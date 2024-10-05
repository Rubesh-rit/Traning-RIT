class FigoFSM:
    # Define binary states for the FSM
    STATE_IDLE = '000'
    STATE_MOVE_FORWARD = '001'
    STATE_TURN_LEFT = '010'
    STATE_TURN_RIGHT = '011'
    STATE_STOP = '100'

    def __init__(self):
        # Initially the rover is idle
        self.state = self.STATE_IDLE

    def change_state(self, new_state):
        print(f"Transitioning from {self.state} to {new_state}")
        self.state = new_state
        self.perform_action()

    def perform_action(self):
        if self.state == self.STATE_IDLE:
            self.idle()
        elif self.state == self.STATE_MOVE_FORWARD:
            self.move_forward()
        elif self.state == self.STATE_TURN_LEFT:
            self.turn_left()
        elif self.state == self.STATE_TURN_RIGHT:
            self.turn_right()
        elif self.state == self.STATE_STOP:
            self.stop()

    def idle(self):
        print("Rover is idle, waiting for next command.")

    def move_forward(self):
        print("Rover is moving forward.")
        # Implement the logic to move the rover forward here (e.g., motor control)

    def turn_left(self):
        print("Rover is turning left.")
        # Implement the logic to turn the rover left here

    def turn_right(self):
        print("Rover is turning right.")
        # Implement the logic to turn the rover right here

    def stop(self):
        print("Rover has stopped.")
        # Implement the logic to stop the rover here

    # Example method to simulate sensor input for navigation
    def navigate(self, sensor_input):
        if sensor_input == 'obstacle_left':
            self.change_state(self.STATE_TURN_RIGHT)
        elif sensor_input == 'obstacle_right':
            self.change_state(self.STATE_TURN_LEFT)
        elif sensor_input == 'clear_path':
            self.change_state(self.STATE_MOVE_FORWARD)
        elif sensor_input == 'stop':
            self.change_state(self.STATE_STOP)
        else:
            self.change_state(self.STATE_IDLE)


# Example usage of the FSM
if __name__ == "__main__":
    figo_rover = FigoFSM()

    # Simulate navigation inputs
    inputs = ['clear_path', 'obstacle_left', 'clear_path', 'obstacle_right', 'stop']
    
    for input_signal in inputs:
        print(f"Sensor Input: {input_signal}")
        figo_rover.navigate(input_signal)
