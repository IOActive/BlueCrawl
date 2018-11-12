# BlueCrawl

Bluetooth meta-data collector for Android (using Frida JS). BlueCrawl serves to aid any bluetooth based research folks seek to do on android.
As with any other protocol, reverse engineering it requires seeing how it is interpreted from different view points; here I present the viewpoint of the
java layer in the application. Having this info can also aid a variety of activities involving spoofing bluetooth information and checking whether apps are stealing
or maliciously scanning for bluetooth objects. 

## Example

```
> frida -U -l bluecrawl-1.0.0.js com.android.bluetooth
     ____
    / _  |   Frida 12.2.15 - A world-class dynamic instrumentation toolkit
   | (_| |
    > _  |   Commands:
   /_/ |_|       help      -> Displays the help system
   . . . .       object?   -> Display information about 'object'
   . . . .       exit/quit -> Exit
   . . . .
   . . . .   More info at http://www.frida.re/docs/home/
                                   
[LGE Nexus 5X::com.android.bluetooth]-> 
 ---------- BlueCrawl : Bluetooth Metadata collector
 v1.0.0

 finding loaded bluetooth classes
[->]	android.bluetooth.IBluetoothManagerCallback$Stub
[->]	android.bluetooth.IBluetoothHeadset$Stub
[->]	android.bluetooth.IBluetoothProfileServiceConnection$Stub
[->]	android.bluetooth.BluetoothProfile$ServiceListener
[->]	android.bluetooth.IBluetoothHeadset
[->]	android.bluetooth.BluetoothGattServerCallback
...
[*] -----

 searching loaded classes for 'android.bluetooth.BluetoothSocket'...
[*] 'android.bluetooth.BluetoothSocket' instance found 'android.bluetooth.BluetoothSocket@c445cb2'
[*]	getting info for 'android.bluetooth.BluetoothSocket@c445cb2'
[*]	- isConnected          :false
[*]	- connection type    :(1) L2CAP
[x]	- conneted device   : device details not available
[*]	- InputStream        :android.bluetooth.BluetoothInputStream@ceae875
[*]	- OutputStream        :android.bluetooth.BluetoothOutputStream@256d00a

[*] 'android.bluetooth.BluetoothSocket' instance found 'android.bluetooth.BluetoothSocket@5f8bd5f'
[*]	getting info for 'android.bluetooth.BluetoothSocket@5f8bd5f'
[*]	- isConnected          :false
[*]	- connection type    :(3) SCO
[x]	- conneted device   : device details not available
[*]	- InputStream        :android.bluetooth.BluetoothInputStream@3b7d3f3
[*]	- OutputStream        :android.bluetooth.BluetoothOutputStream@8cb78b0

[*] -----

 searching loaded classes for 'android.bluetooth.BluetoothServerSocket'...
[*]  'android.bluetooth.BluetoothServerSocket' instance found 'ServerSocket: Type: TYPE_RFCOMM Channel: 5'
[*]  'android.bluetooth.BluetoothServerSocket' instance found 'ServerSocket: Type: TYPE_RFCOMM Channel: 4'
[*]  'android.bluetooth.BluetoothServerSocket' instance found 'ServerSocket: Type: TYPE_L2CAP Channel: 4097'
[*]  'android.bluetooth.BluetoothServerSocket' instance found 'ServerSocket: Type: TYPE_RFCOMM Channel: 6'
[*]  'android.bluetooth.BluetoothServerSocket' instance found 'ServerSocket: Type: TYPE_L2CAP Channel: 4099'
[*]  'android.bluetooth.BluetoothServerSocket' instance found 'ServerSocket: Type: TYPE_L2CAP Channel: 4101'
[*]  'android.bluetooth.BluetoothServerSocket' instance found 'ServerSocket: Type: TYPE_RFCOMM Channel: 7'
[*] -----

 searching loaded classes for 'android.bluetooth.BluetoothDevice'...
[*]  android.bluetooth.BluetoothDevice instance found :=> 'FF:FF:FF:BE:EE:EF'
[*]	Bluetooth device ['FF:FF:FF:BE:EE:EF']
[*]	- Name           :Nexus 5
[*]	- Address        :FF:FF:FF:BE:EE:EF
[*]	- Type           :(1) Classic
[*]	- Device Class   :5a020c
[*]		-- Class Major  : (512)  Phone
[*]	- Bond State     :(12) Bonded
```
*Disclaimer : MAC addresses shown here are fabricated entirely.
Prints in color too!
