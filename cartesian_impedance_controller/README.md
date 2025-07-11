# Catesian Impedance Controller

This controller implements a catesian impedance controller which take a desired pose and a desired force in the cartesian frame.

## Example Configuration
Below is an example `controller_manager.yaml` for a controller specific configuration.
```yaml
controller_manager:
  ros__parameters:
    update_rate: 500  # Hz

    cartesian_impedance_controller:
      type: cartesian_impedance_controller/CartesianImpedanceController

    # More controller instances here
    # ...

cartesian_impedance_controller:
  ros__parameters:
    end_effector_link: "tool0"
    robot_base_link: "base_link"
    ft_sensor_ref_link: "sensor_link"
    command_current_configuration: false # for KUKA set this to true, for other robots set to false
    max_impedance_force: 10.0 # (N) maximum task force
    delta_tau_max: 1.0 # (Nm) maximum torque increment in one control cycle
    joints:
      - joint1
      - joint2
      - joint3
      - joint4
      - joint5
      - joint6
      - joint7
      
    command_interfaces:
      - effort
    
    state_interfaces:
      - position
      - velocity

    stiffness:
        trans_x: 500
        trans_y: 500
        trans_z: 500
        rot_x: 50
        rot_y: 50
        rot_z: 50

    nullspace_stiffness: 1.0
    nullspace_configuration:
      - 0.0
      - 0.0
      - 0.0
      - 1.57
      - 0.0
      - 0.0
      - 0.0
    compensate_gravity: false
    compensate_coriolis: false
    compensate_dJdq: false


# More controller specifications here
# ...

```

