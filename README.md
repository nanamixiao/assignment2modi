# assignment2modi

``` python

import os
import time
import random


class Car():
    def __init__(self, name, finsh_lane_distance):
        self.position = 0
        self.name = name
        self.finsh_lane_distance = finsh_lane_distance

    def move(self):
        self.position += self.update()
        return self.position

    def update(self):
        return random.randint(1, 5)

    def getName(self):
        return self.name

    def check_win(self):
        return self.position >= self.finsh_lane_distance

    def getPosition(self):
        return self.position



class Race():
    def __init__(self, car_obj):
        self.car_obj = car_obj

    def display_race(self):
        while True:
            time.sleep(0.5)
            if self.run():
                break

    def run(self):
        os.system('cls' if os.name == 'nt' else 'clear')
        print("Car race simulation:")

        for car1 in self.car_obj:
            car1.move()
            print(f"{car1.getName()}: {'-' * car1.getPosition()} ({car1.getPosition()})")

            if car1.check_win():
                print(f"   {car1.getName()} wins the race!")
                return True

        return False



if __name__ == '__main__':
    num_of_car = 5
    finish_line_distance = 50
    car_Obj = []

    for i in range(num_of_car):
        car = Car("Car " + str(i + 1), finish_line_distance)
        car_Obj.append(car)

    race = Race(car_Obj)
    race.display_race()
```
