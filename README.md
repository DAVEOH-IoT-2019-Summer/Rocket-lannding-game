# Rocket-lannding-game

import time

old_position = 100                                                                    # This is inital value
old_velocity = 0
old_fuel = 100
gravity_init = -10
gravity = 0
thrusters = 0
acceleration = 0
new_fuel = 0
new_position = 100
new_velocity = 0


while True:
    # formulas for calculate.
    new_fuel = old_fuel - int(thrusters)
    acceleration = gravity + int(thrusters)
    new_position = old_position + old_velocity + acceleration * 0.5
    new_velocity = old_velocity + acceleration
    print "P:{0}    V:{1}    F:{2}".format(new_position, new_velocity, new_fuel)       # Monitoring current situation.
    
    if new_fuel <= 0:                                                                  # Rocket Crashed problem case.
        thrusters = 4
        print "{0}".format(thrusters)
        
        while True:
            acceleration = gravity + int(thrusters)                                    # This is formulas for calculate.
            new_position = old_position + old_velocity + acceleration * 0.5
            new_velocity = old_velocity + acceleration
            old_velocity = new_velocity
            old_position = new_position
            if old_position <= 0:
                print "P:0    V:{0}    F: 0\n Rocket crashed! Velocity was {1} m/s".format(new_velocity, new_velocity)
                while True:
                    continue
            print "P:{0}    V:{1}    F: 0 \n No fuel --rocket is in free-fall!!".format(new_position, new_velocity)
            thrusters=0
            time.sleep(1)
            
    if new_position <= 0 :                                                          # Success Landing case
        print "P:0    V:{0}    F:{1}".format(new_velocity, new_fuel)
        print "Landing Successful!!"
        while True:
            continue

    thrusters = raw_input("Set thrusters(0-20) : ")                                 # input the thrusters value.
    thrusters = int(thrusters)

    if thrusters > 20:                                                              # if thrusters value is over provied,
        print "Thrusters at max(20)!"                                               # adjust thrusters value to max(20)
        thrusters = 20
        #print "Thrusters {0}\n".format(thrusters)
    elif thrusters < 0:                                                             # if thrusters value less than 0,
        print "NO Thrusters(0)!"                                                    # adjust thrusters value to min(0)
        thrusters = 0
        print "Thrusters {0}\n".format(thrusters)"
    else:                                                                           # Not change value,
        print "Thrusters {0}\n".format(thrusters)ew

    old_fuel = new_fuel                                                 
    gravity = gravity_init
    old_velocity = new_velocity
    old_position = new_position
