# pr2_robot_calibration

Package for calibrating the PR2 using the `robot_calibration` package.

**Note:** This package is experimental.
It is based off the `fetch_calibration` package, with some small modifications.
It was used to calibrate a PR2 robot using the 5x4 checkerboard from the PR2 accessories box.

## Tutorial
- [ ] Make sure you have clear space around the robot for it to move its arms
- [ ] Run `robot start`
- [ ] Run the Kinect, which should publish to `/head_mount_kinect/depth_registered/points` and `/head_mount_kinect/depth_registered/camera_info`
  - [ ] If the topics are different, modify `capture_[left,right]_checkerboards.launch` and `capture_[left,right]_checkerboards.yaml` as needed.
- [ ] Grasp the checkerboard with the right gripper
      - For both arms, the gripper holds the checkerboard upright, with the LED facing *inward*, i.e., the right gripper's LED faces left and the left gripper's LED faces right.
- [ ] `roslaunch pr2_robot_calibration capture_right_checkerboards.launch`
- [ ] (Recommended) Make adjustments to robot.xml and then restart the robot
      - Release the checkerboard
      - Disable all breakers
      - Enable all breakers
      - `robot start -f`
- [ ] Move the checkerboard to the left gripper
- [ ] `roslaunch pr2_robot_calibration capture_left_checkerboards.launch`

In both cases, you should see the offsets you need to make to the robot.xml on your robot.
We only calibrate the head/camera poses when calibrating the right arm.
Then, we recommend restarting your robot with the new calibration and then doing a separate calibration for just the left arm joints.
