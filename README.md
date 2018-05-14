# CarND-Controls-PID
Self-Driving Car Engineer Nanodegree Program

---

## Dependencies

* cmake >= 3.5
 * All OSes: [click here for installation instructions](https://cmake.org/install/)
* make >= 4.1(mac, linux), 3.81(Windows)
  * Linux: make is installed by default on most Linux distros
  * Mac: [install Xcode command line tools to get make](https://developer.apple.com/xcode/features/)
  * Windows: [Click here for installation instructions](http://gnuwin32.sourceforge.net/packages/make.htm)
* gcc/g++ >= 5.4
  * Linux: gcc / g++ is installed by default on most Linux distros
  * Mac: same deal as make - [install Xcode command line tools]((https://developer.apple.com/xcode/features/)
  * Windows: recommend using [MinGW](http://www.mingw.org/)
* [uWebSockets](https://github.com/uWebSockets/uWebSockets)
  * Run either `./install-mac.sh` or `./install-ubuntu.sh`.
  * If you install from source, checkout to commit `e94b6e1`, i.e.
    ```
    git clone https://github.com/uWebSockets/uWebSockets 
    cd uWebSockets
    git checkout e94b6e1
    ```
    Some function signatures have changed in v0.14.x. See [this PR](https://github.com/udacity/CarND-MPC-Project/pull/3) for more details.
* Simulator. You can download these from the [project intro page](https://github.com/udacity/self-driving-car-sim/releases) in the classroom.

There's an experimental patch for windows in this [PR](https://github.com/udacity/CarND-PID-Control-Project/pull/3)

## Basic Build Instructions

1. Clone this repo.
2. Make a build directory: `mkdir build && cd build`
3. Compile: `cmake .. && make`
4. Run it: `./pid`. 

Tips for setting up your environment can be found [here](https://classroom.udacity.com/nanodegrees/nd013/parts/40f38239-66b6-46ec-ae68-03afd8a601c8/modules/0949fca6-b379-42af-a919-ee50aa304e6a/lessons/f758c44c-5e40-4e01-93b5-1a82aa4e044f/concepts/23d376c7-0195-4276-bdf0-e02f1f3c665d)

## PID Controllers

### Determining the values for P, I, and D.
The final values of the parameters where tuned and decided on by hand.  I have started the coding in the Twiddle Algorithm as provided by the coursework from Udacity.  I have not tested it's implementation as of yet but intened to revisit this project after my completion of the course.

* The Proportional value I decided on is 0.08.  The P value is used in the calculation converting CTE(cross track error) into the actuation command(steering angle).  

* The Integral value I decided on is 0.005. The I value is used for calculating the sum of CTE vs the actuation commands.  The approximate starting I value is 1 / 10 of the P value

* The Derivative value I decided on is 0.885. The D vaue is used for calculating the difference between the last two values.  The approximate starting D value is 10 times that of the P value.

* Methodology:  I started with a fixed ratio of the P-I-D values.  I would only adjust the P value until the simulation could complete a lap to my satisfaction.  During the tuning of the P value I ignored over shooting of the calculated acuation and how long it took to get to a stable state.  Once I was able to complete a lap I started adjusting the inner and outter loops accordingly.  I look forward to coming back to this project and completing the implementation of the twiddle algorithm. 

