# cayoperico_ct-gtav

How to use:
You need to install Cheat Engine.
1. Open GTA 5 first.
2. Open Cheat Engine.
3. Load CayoPerico-CT.ct -- or just open the file.
4. Tick 'Activate Table' -- Cheat Engine will automatically attach to GTA5.exe process.
5. Have fun!

Hotkeys:
- Numpad plus (+) : Teleport to Waypoint
- Numpad dot (.) : Teleport to Objective
- Numpad minus (-) : Toggle Godmode
(You can change this and set other hotkey by right-clicking in Cheat Engine!)


tutorial

<b> use the bunker </b>

1. Go to your bunker and open the computer
2. Look at Bunker Products and remember that!
3. Sell your products and wait for Agent call
4. Open Lua Engine
5. Type and replace 'money here' with money you want (ex. 20000000) and 'bunker value' to your bunker product value (ex. 7000)
Code:
deliverBunker(money here , bunker value)
For Epic Games:
deliverBunker(money here)
6. Click 'Execute' and Profit!

<b> unlimited ammo </b> prolly crash

1. Double-click on <script> beside Unlimited Ammo
Copy this code:
[ENABLE]
{$lua}
function f_infAmmo(act)
  local CPlayer = readPointer(readPointer(getAddress("WorldPTR")) + pCPed)
  local CInventory  = readPointer(CPlayer + 0x10D0)
  local f_based = readPointer(getAddress(CInventory + 0x48))
  local inventory = readSmallInteger(CInventory + 0x50)
  local solut = inventory - 1;
  for i = 0,solut,1 do
  local inf_ammo = readPointer(f_based + 0x8 * i)
  if inventory==0 then break end
  writeBytes(inf_ammo + 0x24, act)
  end
end
f_infAmmo(1)
[DISABLE]
{$lua}
f_infAmmo(0)
3. Press 'OK'
  

<b> teleport menu </b>

1. Right-click your Cheat Engine
2. Select 'Open File Location'
3. Make a text file with name "Teleport Locations.txt"

<b> add custom tp </b>
A. Using teleport menu
1. Go to your Cheat Engine directory and open "Teleport Locations.txt"
Use this format to add location:

~location name~ x:~x coord~, y:~y coord~, z:~z coord~
Ex. Shoe Store x:135.2539, y:-1307.2087, z:28.6759)


B. Manually
1. Tick 'Teleport', and tick 'Manual'
2. Open Auto Assembler by pressing Ctrl + Alt + A
3. Copy this code, and replace x,y,z with the coords found on 'Manual':


Use this format to add location:
[ENABLE]
{$lua}
teleport('c',x,y,z)
 
[DISABLE]
{$lua}
teleport('c',x,y,z)



4. Press 'File' on top, and press 'Assign to current cheat table'
5. Now scroll to the bottom of your table you will see Auto Assemble script, you can name it with your location and move it.
- 6. If you already made a custom location, you can copy-paste it, and double-click on <script> to change your coordinates

