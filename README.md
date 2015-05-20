# A guide to using ROS on the IFC6410

This hopes to be a quick practical guide to getting ROS Indigo running on the IFC6410 runing Ubuntu Trusty, from the Linary 14.05 build.

This is a GitBook the source is hosted on GitHub. If you'd like to make a contribution please visit: https://github.com/tfoote/ros_ifc6410_guide

The book is registered to be automatically built and made available at: http://tfoote.gitbooks.io/a-guide-to-using-ros-on-the-ifc6410/

The current build status is: [![Build Status](https://www.gitbook.io/button/status/book/tfoote/a-guide-to-using-ros-on-the-ifc6410)](https://www.gitbook.io/book/tfoote/a-guide-to-using-ros-on-the-ifc6410/activity)

## Other resources

This is designed as a basic tutorial on how to get going with ROS on the IFC6410. It draws from various other resources.
If you want to do more complicated things we will do our best to link to the upstream resources we used to generate this guide.
However if you are interested in doing more than is exactly outlined here we suggest that you peruse some of these resources.

 * [MyDragonBoard Forums](http://mydragonboard.org/?s=ifc6410)
 * Linaro builds [14.05](http://releases.linaro.org/14.05/ubuntu/ifc6410) [14.10](http://releases.linaro.org/14.10/ubuntu/ifc6410)
  * Open source builds (still requires binary drivers see Techweb below)
  * 14.05 currently recommended due to SD card issues in 14.10.
 * [Inforce Computing product page](http://www.inforcecomputing.com/products/moreinfo/inforce6410.html)
 * [inforce Computing Techweb](http://www.inforcecomputing.com/techweb/index.php) Registration requried.
  * The source for binary hardware drivers.
  * Also redistributes full images from Linaro with the binary releases built in.



### TurtleBot

Install turtlebot from binaries
install ftdi rules
export kinect sensor
