# Python-project
import time
import random
from random import randint

print '\n' * 5
print 'Type "help" if you are stuck'
print '\n\n\n------------------------'
print '    Space Invasion'
print '------------------------'
print '\nstardate 86088.58 : Biocrytic inc.'
time.sleep(1)
print '\nBooting....'
time.sleep(1)
print '\nInitalizing Manual controls....'
time.sleep(1)
print '....'
time.sleep(1)
print '....'
time.sleep(1)
print 'Weapons offline...'
time.sleep(1)
print 'Locator offline...'
time.sleep(1)
print '\nUSP port avaliable...'
time.sleep(1)
print '....'
time.sleep(1)
print '....'
print '\nCyborg018 Online...'
time.sleep(1)
print '''\n\nYou are a Robotics Specialist at Biocrytic HQ. 
A weapons supply spaceship has been boarded by space pirates. 
They are currently attempting to steal the cargo.
You activate Cyborg018 that is on-board to take back the ship.
However the weapons and locators are not active.''' 

def start(inventory):
    print '\n----------' 
    time.sleep(1)
    print '....' 
    time.sleep(1)
    print '\n[-ELEVATOR-]' 
    print '\n1.) deck 1 - Security Room' 
    print '2.) deck 2 - Server Room' 
    print '3.) deck 3 - Weapons Room' 
    print '4.) deck 4 - Supply Hanger' 
    print '5.) deck 5 - Command Room' 
    print '6.) deck 6 - Transporter Room\n' 
    
    cmdlist = ['1', '2', '3', '4', '5', '6',]
    cmd = getcmd(cmdlist)
    
    if cmd == '1':
        security(inventory)
    elif cmd == '2':
        if 'hack' in inventory:
            print '\n- DECK 2 - SERVER ROOM LOCKED -' 
            time.sleep(2)
            start(inventory)
        else:
            server_room(inventory)
    elif cmd == '3':
        weapons_room(inventory)
    elif cmd == '4':
        if 'laser' in inventory:
            print '\n- DECK 4 - SUPPLY HANGAR LOCKED -' 
            time.sleep(2)
            start(inventory)
        else:
            supply_hangar(inventory)
    elif cmd == '5':
        command_room(inventory)
    elif cmd == '6':
        if 'locator' in inventory:
            print '\n- DECK 6 - TRANSPORTER ROOM LOCKED -' 
            time.sleep(2)
            start(inventory)
        else:
            transporter_room(inventory)
	
def server_room(inventory):
    print '\n----------' 
    time.sleep(1)
    print '....' 
    time.sleep(1)
    print '''\nThis is the Server Room and it appears deserted. 
You can see a broken computer system in the corner of the room, it has been smashed beyond recognition.''' 
    print '\n[-SERVER ROOM-]\n' 
    print '1.) Examine broken computer' 
    print '2.) Return to Elevator\n' 
    
    cmdlist = ['1', '2']
    cmd = getcmd(cmdlist)
    if cmd == '1':
        time.sleep(1)
        broken_comp(inventory)
    elif cmd == '2':
        start(inventory)
        
def broken_comp(inventory, items=['hack']):
    print '\n----------' 
    print '''\nAlthough the screen is smashed, the processors are still working.
The broken computer seems to have a USB port. This port will allow you to download a hack 
program into your system.''' 
    if len(items) > 0:
        for item in items:
            print '\n--> %s' % (item) 
            print '*freebie hint: type "USB port"*' 
            print '\n\n1.) Exit.' 
            
    cmdlist = ['USB port', '1']
    cmd = getcmd(cmdlist)
    
    if cmd == 'USB port':
            inventory.append('hack')
            items = ['hack']
            print '\nUSB port connected.' 
            time.sleep(1)
            print 'accessing file..' 
            time.sleep(1)
            print 'downloading..' 
            time.sleep(1)
            print '....'
            time.sleep(1)
            print '\ndownload complete.' 
            print '\nYou have installed the hack program and return' 
            print 'to the Elevator.' 
            time.sleep(2)
            start(inventory)
    elif cmd == '1':
            start(inventory)
    else:
        print '\n error. invalid command-'
    
def weapons_room(inventory):
    print '\n----------' 
    time.sleep(1)
    print '....'
    time.sleep(1)
    print '''\nYou enter the Weapons Room, two enemy pirates fire lasers at you.
They happen to be the best shooters and you take a direct hit.'''
    print '\n[-Weapons Room-]'
    print '....'
    time.sleep(1)
    print '....'
    time.sleep(1)
    print '\nshutting down...'
    time.sleep(1)
    print 'Cyborg018 is offline.'
    time.sleep(1)
    print 'Shipment lost...'
    print 'Your boss is very disappointed with your preformance'
    time.sleep(1)
    print '\nGAME OVER\n'
    exit(0)
	
def supply_hangar(inventory):
    print '\n----------'
    time.sleep(1)
    print '....'
    time.sleep(1)
    print '''\nThe Supply Hanger is filled with rubble. Dead pirates are everywhere.
The automated defence has done their job. At the back of the room, there is a Control panel
for the defence system. You can access the system to re-calibrate your laser but the system requires a 
3 digit access code.\n'''
    print '[-SUPPLY HANGAR-]'
    print '\n1.) Enter the 3 digit code'
    print '2.) Return to Elevator'
    
    cmdlist = ['1', '2']
    cmd = getcmd(cmdlist)
    
    if cmd == '1':
        access_code(inventory)
    elif cmd == '2':
        start(inventory)
        
def access_code(inventory):
    code = '%d%d%d' % (randint(0,9), randint(0,9), randint(0,9))
    guess = raw_input('\n[KEYPAD]> ')
    guesses = 0
    
    while guess != code and guess != 'py27rtq' and guesses <4:
        print('\n* ACCESS - DENIED *')
        guesses += 1
        guess = raw_input('\n[KEYPAD]> ')
        
    if guess == code or guess == 'py27rtq':
        defense_system(inventory)
    else:
        print '\n....'
        time.sleep(1)
        print '\n....'
        time.sleep(1)
        print '\nKEYPAD - LOCKED'
        time.sleep(1)
        print '\ncode randomizing..'
        time.sleep(1)
        print '\nKEYPAD - OPEN'
        time.sleep(1)
        supply_hangar(inventory)
		
def defense_system(inventory, items=['laser']):
    print '\n\n----------'
    print '\nBooting Defense System....'
    time.sleep(1)
    print 'Initalizing Systems....'
    time.sleep(1)
    print '....'
    time.sleep(1)
    print '....'
    time.sleep(1)
    print 'Defense System Active.'
    time.sleep(1)
    print '''\nThe Defense System is now active. You MUST connect to
this control panel with the USB port to re-calibrate your laser.'''
    
    if len(items) > 0:
        for item in items:
            print '\n--> %s' % (item)
    cmdlist = ['USB port']
    cmd = getcmd(cmdlist)
    if 'port' in cmd:
            inventory.append('laser')
            items = ['laser']
            print '\nUSB port connected.'
            time.sleep(1)
            print 'Repairing Laser...'
            time.sleep(1)
            print 'Auto alignment...'
            time.sleep(1)
            print '....'
            time.sleep(1)
            print '\nLASER ONLINE.'
            print '''\nYour laser is now online. 
You return to the Main Elevator.'''
            time.sleep(2)
            start(inventory)
    else:
        print '\n error. invalid command-'
		
def security(inventory):
    print '\n----------'
    time.sleep(1)
    print '....'
    time.sleep(1)
    print '''\nYou are the Security Room. This is where all
surveillance aboard the shuttle is done. Parts of the system have been deactivated 
to protect vital information.You MUST access it to gain special override codes. To do that,
you will have to hack the system.\n'''
    print '[-SECURITY ROOM-]\n'
    print '1.) View Surveillance monitors'
    print '2.) Hack the system'
    print '3.) Return to elevator'
    
    cmdlist =['1', '2', '3']
    cmd = getcmd(cmdlist)
    
    if cmd == '1':
        print '\n----------'
        print '\nBooting Monitors....'
        time.sleep(1)
        print '....'
        time.sleep(1)
        print '...'
        time.sleep(1)
        print 'Monitors active.'
        time.sleep(1)
        print '\n[-SURVEILLANCE FEED-]'
        print '''\n-The Hangar monitor is offline.
    \n-In the Cargo hold there are two pirates patrolling.
    \n-The Maintenance deck looks clear.
    \n-The captain of the pirates is posted on the Shuttle Control deck.
    \n-Observation shows a pirate on the lookout.'''
        time.sleep(2)
        security(inventory)
        
    elif cmd == '2':
        if 'hack' in inventory:
            print '\nloading droid hack....'
            time.sleep(2)
            print '....' 
            time.sleep(2)
            print '10000101010101010101010' * 1000
            time.sleep(1)
            print '....'
            time.sleep(1)
            print 'Accessing encrypted files...'
            time.sleep(2)
            print 'Decrypting....'
            time.sleep(2)
            print '\n\n[-SEN343 LOG-]'
            time.sleep(1)
            print '\n\nDAILY OVER-RIDE CODES- SUPPLY HANGER SYSTEM'
            time.sleep(1)
            print '\n\n-Navigations - szb41ee'
            time.sleep(1)
            print '\n\n-Emergency escape pods - qr66mop'
            time.sleep(1)
            print '\n\n-Hangar defence system - py27rtq'
            time.sleep(1)
            print '\n\nCODES WILL BE RESET EVERY 24 HOURS'
            security(inventory)
        else:
            print '\n- ACCESS TO DATA RECORDER DENIED -'
            time.sleep(2)
            security(inventory)
        
    elif cmd == '3':
        start(inventory)
		
def transporter_room(inventory):
    print '\n----------'
    time.sleep(1)
    print '....'
    time.sleep(1)
    print '''\nYou enter the transporter room. A clumsy pirate
fumbling for his laser gun confronts you. Suddenly, he drops the gun and starts to pick it up.
He is going to shoot any second now...\n'''
    print '[-TRASNPORTER ROOM-]\n'
    print '1.) Shoot the clumsy pirate'
    print '2.) Retreat to the Elevator.'
    
    cmdlist = ['1', '2']
    cmd = getcmd(cmdlist)
    
    if cmd == '1':
        if 'laser' in inventory:
            print '\nlasers activating...'
            time.sleep(1)
            print 'target locked...'
            time.sleep(1)
            print '...'
            time.sleep(1)
            print '\nTARGET TERMINATED\n'
            enemy(inventory)
        else:
            print '\n- WARNING LASER OFFLINE -'
            time.sleep(2)
            print '''\nThe clumsy pirate manages to pick up his laser
He aims his gun at you and shoots....'''
            print '....'
            time.sleep(1)
            print '....'
            time.sleep(1)
            print '\nShutting down...'
            time.sleep(1)
            print 'Cyborg018 offline.'
            time.sleep(1)
            print 'Your boss is disappointed that you lost the shipment'
            print '\nGAME OVER\n'
            exit(0)
            
    elif cmd == '2':
            print '''\nThe clumsy pirate manages to pick up his gun.
He aims his gun as you retreat to the elevator.
The elevator was so close, yet so far...'''
            print '....'
            time.sleep(1)
            print '....'
            time.sleep(1)
            print '\nShutting down...'
            time.sleep(1)
            print 'Cyborg018 offline.'
            time.sleep(1)
            print 'Your boss is diappointed that you lost the weapons'
            time.sleep(1)
            print '\nGAME OVER\n'
            exit(0)
			
def enemy(inventory, items=['locator']):
    print '\n----------'
    time.sleep(1)
    print '''\nThe clumsy pirate falls over and dies. On his belt is a small device 
that has a program installed that will repair your locator. you MUST connect
your USB port to download the program.'''
    if len(items) > 0:
        for item in items:
            print '\n--> %s' % (item)
    cmdlist = ['USB port']
    cmd = getcmd(cmdlist)
    if cmd == 'USB port':
            inventory.append('locator')
            items = ['locator']
            print '\nUSB port connected.'
            time.sleep(1)
            print 'accessing file..'
            time.sleep(1)
            print 'downloading..'
            time.sleep(1)
            print '....'
            time.sleep(1)
            print 'Repairing locator...'
            time.sleep(1)
            print 'Auto alignment...'
            time.sleep(1)
            print '....'
            time.sleep(2)
            print '\nLOCATOR ONLINE.'
            time.sleep(2)
            print('''\nYour Locator is now online.
You return to the elevator''')
            start(inventory)
			
def command_room(inventory):
    print '\n----------'
    time.sleep(1)
    print '....'
    time.sleep(1)
    print '''\nYou enter Command Room where all the navigation takes place.
The Captain of the pirates is trying to steer the ship to his base.
He has a very powerful machine gun and an invisibility cloak.'''
    print '\n[-COMMAND ROOM-]'
    print '\n1.) Attempt to attack the Captain'
    print '2.) Retreat to Main Elevator'
    cmdlist = ['1', '2']
    cmd = getcmd(cmdlist)
    
    if cmd == '1':
        if 'laser' in inventory and 'locator' in inventory and 'hack' in inventory:
            print '\n....'
            time.sleep(1)
            print '\n....'
            captain(inventory)
        else:
            time.sleep(1)
            print '\nCaptain:>'
            print '\nMUHAHAHHAHA ' * 10
            time.sleep(1)
            print '''\nThe Captain laughs as you fall to the ground.
The last thing you see is the Captain revealing himself from the invisibility cloak'''
            print '....'
            time.sleep(1)
            print '....'
            time.sleep(1)
            print '\nShutting down...'
            time.sleep(1)
            print 'Cyborg018 offline.'
            time.sleep(1)
            print 'Your boss is disappointed that you lost the weapons shipment'
            tome.sleep(1)
            print '\nGAME OVER\n'
            exit(0)
    elif cmd == '2':
        start(inventory)
        
def captain(inventory):
    print '\nRunning hack...'
    time.sleep(1)
    print '\nJamming the machine gun...'
    time.sleep(1)
    print '\n......' 
    time.sleep(1)
    print '\nLocator Activating...'
    time.sleep(1)
    print '\nLocating the invisible Captain...'
    time.sleep(1)
    print '\n......' 
    time.sleep(1)
    print '\nLaser active...'
    time.sleep(1)
    print '\nTargeting the Captain...'
    time.sleep(1)
    print '\nTarget Locked...'
    time.sleep(1)
    print '\n......'
    time.sleep(2)
    print '\n\nCAPTAIN TERMINATED \n'
    time.sleep(2)
    print '''\n\nYou have defeated the Captain and taken back control
of the weapons supply ship. The flight path has been corrected and a distress signal has been sent to 
Biocrytic: Department of Defense. Reinforcement troops are being sent.
\n - GAME OVER -\n''' 

def getcmd(cmdlist):
    cmd = raw_input('\nCommand--> ')
    if cmd in cmdlist:
        return cmd
    elif cmd == 'help':
        print '\nTYPE: "inventory" to view items'
        print 'or "quit" to self-destruct'
        return getcmd(cmdlist)
    elif cmd == 'inventory':
        print '\ninventory contains:\n'
        for item in inventory:
            print '-- %s' % (item)
        return getcmd(cmdlist)
    elif cmd == 'secret':
        print '\n........'
        time.sleep(1)
        print 'Written by: Benson Lau'
        print 'A simple game to test my Python skills'
        print '\n........\n' 
        return getcmd(cmdlist)
    elif cmd == 'quit':
        print '\n----------'
        time.sleep(1)
        print '\nself-destruct sequence initiated...'
        time.sleep(1)
        print 'shutting down...'
        time.sleep(1)
        print '\nCyborg018 offline.'
        time.sleep(1)
        print 'Your boss walks towards your desk.'
        time.sleep(1)
        print 'He fires you on the spot for not trying to save the shipment'
        exit(0)
    else:
        print '\n   error. invalid command-\n'
        return getcmd(cmdlist)
    
if __name__ == "__main__":
	inventory = ['USB port']
	start(inventory)
