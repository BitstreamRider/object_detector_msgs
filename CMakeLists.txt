cmake_minimum_required(VERSION 3.8)
project(object_detector_msgs)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# find dependencies
find_package(ament_cmake REQUIRED)
# uncomment the following section in order to fill in
# further dependencies manually.
find_package(rosidl_default_generators REQUIRED)
find_package(std_msgs REQUIRED)
find_package(sensor_msgs REQUIRED)
find_package(vision_msgs REQUIRED)
find_package(action_msgs REQUIRED)


# Generate messages, services, and actions
rosidl_generate_interfaces(${PROJECT_NAME}
  msg/BoundingBox.msg
  msg/Detection.msg
  msg/Detections.msg
  msg/PoseWithConfidence.msg
  msg/Pose3DBBoxWithConfidence.msg
  msg/PoseStWithConfidence.msg
  msg/Plane.msg

  srv/Start.srv
  srv/Stop.srv
  srv/Detectron2ServiceServer.srv
  srv/EstimatePoses.srv
  srv/EstimatePoses3DBBox.srv
  srv/EstimatePointingGesture.srv
  srv/RefinePoses.srv
  srv/GetPoses.srv
  srv/EstimatePosesSt.srv
  srv/RefinePosesSt.srv
  srv/GetPosesSt.srv
  srv/AddBoxes.srv
  srv/VisualizePoseEstimation.srv

  action/CheckForDetections.action
  action/GenericImgProcAnnotator.action

  DEPENDENCIES
    std_msgs
    sensor_msgs
    vision_msgs
    action_msgs
)

ament_export_dependencies(rosidl_default_runtime)
ament_export_include_directories(include)

ament_package()
