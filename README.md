# project_simulation_script
Repository holds all the necessary files which are needed to recreate the results of the simulation. Read the README file for instructions on running and plotting the code.

---Introduction-------------------------------------------------------------------------------------------------

This README shows you how to run the simulation script in ns-3 as well as plotting the results in the same way as was done for the study.

Before you run the script make sure you download the project.zip and unzip it, move the folder to the scratch directory in your ns-3 folder. Make sure that the third.cc and fifth.cc files are not in the same scratch directory as this can cause problems with the build.

----------------------------------------------------------------------------------------------------------------

---Running the script with ns-3---------------------------------------------------------------------------------

After copying the project folder to your scratch directory run the following commands to run the script:

1. First run the ns-3 configure command: ./ns3 configure

2. The use the ns-3 build command: ./ns3 build

(Note: if the build stops before reaching a 100% without giving an error message run the following command te clear the cmake cache: rm -rf cmake-cache
Then run the configure command again and after that run the build command again)

3. And finally run the following command to run the script and write it's output to a .dat file: ./ns3 run scratch/project/ProjectSimulation.cc > filename.dat 2>&1

If no error messages are displayed then the script is running succesfully, it will take a around 10 minutes to complete.

The script will run using TCP Hybala. If you want to use the other algoritms you will have to go into the script and change the following line which is located near the top of the main function:

Config::SetDefault("ns3::TcpL4Protocol::SocketType", StringValue("ns3::TcpHybala"));

Simply change TcpHybala to TcpVegas or TcpVeno and save the script, then reconfigure and rebuild ns3 and run the script again

----------------------------------------------------------------------------------------------------------------

---plotting the results with gnuplot----------------------------------------------------------------------------

For the presentation of the output the tool gnuplot is used. Startup gnuplot and run the follwing commands to create a graph of the output:

1. Set the file type and the size (feel free to use different sizes) for the image: set terminal png size 800,640
   
2. Set the name of the file to be written to: set output "tcpname.png"
   
3. Set a name for the x-axis: set xlabel "Seconds"
   
4. Set a name for the y-axis: set ylabel "Congestion Window Size"
   
5. Set a titel for the graph: set titel "tcpname Congestion Window Size over Time"
    
6. Add a grid to the graph: set grid
    
7. And now plot the results into the png file that you created: plot "tcpname.dat" using 1:2 title 'congestion window' with linespoints linecolor '#ff0000'
   (feel free to change the linecolor with another rgb value)

Now a .png file is created wich shows of graph of the data from the .dat file you used in the plot command

----------------------------------------------------------------------------------------------------------------
