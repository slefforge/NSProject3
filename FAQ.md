## Windows Malware:
#### What is the correct format for `stage*-commands.txt`?
The commands should begin with $ and should be written on separate lines. 
The order of the commands does not matter, so
```
$COMMAND1
$COMMAND2
$COMMAND3
```
is equivalent to
```
$COMMAND3
$COMMAND1
$COMMAND2
```
#### Are the commands case sensitive?
Yes, the commands should be written exactly as they are displayed when they are discovered.
#### I know my commands are correct but the malware is still not being downloaded.
You may need to disable or change your home network firewall settings, as the malware can be blocked by some filters.
#### Cuckoo is displaying a score of 0 and no signatures on the "Summary" page.
Those features have been disabled for this project. You can you the other tabs in Cuckoo to gather information.
#### I do not see any information in Cuckoo's Network Analysis tab for Stage 2.
For Stage 2, you may need to use Wireshark to gather information about the Command and Control traffic.
#### I'm getting an error when trying to analyze a malware sample using Cuckoo.
Restart the VM, run ./reset in the ~/tools/networking directory, and rework the steps in the write-up for analyzing the malware sample using Cuckoo. Sometimes just resubmitting the sample for analysis can resolve the error as well.
#### Do I have to use Cuckoo?
No, Cuckoo is not required to complete the project. For observing C2 traffic, Wireshark can be used instead.
#### When I run stage2.exe on the Windows XP VM I get an error.
Make sure that you check the file type of the malware sample using `file stage2.exe` and unzip it accordingly. Even though the filename ends with .exe that doesn't guarantee that it is an executable file.
#### When I run `file stage2.exe` I get an html file.
This means that your commands were correct, but the malware file was not downloaded correctly for some reason. To resolve this restart the VM, run ./reset in the ~/tools/networking directory, and rerun the malware in the Windows VM. 
#### When I open the Windows XP VM a "Hardware Wizard" dialog box keeps opening.
This is normal, if you keep closing it, it will stop opening after you close it a few times.
#### The malware sample was not downloaded to the shared directory.
This is normal, the malware may not download to to the shared directory automatically, you may have to manually move it.
#### Where is the Procmon utility located?
You can find Procmon in the ProcessMonitor directory on the Desktop of the Windows XP VM.
#### Is Stage 1: Question 1 asking for a domain name or a URL?
The first question for Stage 1 in the report is asking for the full URL, not just the domain.

## Linux Malware
#### I'm seeing strange behavior when running payload.exe?
Payload.exe is the zipped version of the malware. You will need to unzip it on the Linux VM in the shared directory in order to complete the remainder of the Linux Malware section.
#### Should I submit payload.exe or payload?
Payload.exe is the zipped version. It's okay if you only submit payload, since that is the actual binary. 
#### I have no idea where to start in questions 2 and 3!!!
Read through the comments on the targs_len_before and opts_len_before functions in linux_sym_exec. They address what registers hold information about the loop. Then, read the example commands in assignment-questionaire.txt for more information on how to set those registers. The angr documentation (https://docs.angr.io/) can also help with formatting these commands. 
#### How do I know if questions 2 and 3 are correct?
Your solutions to questions 2 and 3 are correct if the malware analysis does not timeout when you run linux_sym_exec on the malware sample in question 4. 
#### What target addresses should I use for question 4?
You can refer to slide 44 of cs6262proj2tutorial.pdf for a guide to finding the target addresses.
#### Is it okay that the format of my commands in question 4 is a few characters off from the example format?
The example format is just there to tell you that you're looking for a command in the format of a regex. The regex you find does not have to be in exactly the same format as the example commands. 
#### Why are there two un-completed functions in detect_loop.py?
We give you two functions: dynamic_call_sequence and find_loop. detect_loop.py is split into these two functions to emphasize that preprocessing on the trace is nesecary before you detect the loop. 
#### Do I need to use both functions in detect_loop?
No, we split up the functions to highlight that there are two seperate actions you need to perform here. You're not submitting detect_loop, so you can change the structure of the functions however you choose. 
#### What are the inputs to each function in detect_loop.py?
function_list is a dictionary of functions (and their addresses) that are called somewhere in the trace. dynamic_trace is a list of the addresses called in the trace. This trace includes addresses visited that are not function calls. 
#### What is the desired output from detect_loop.py?
The output is a list of function calls (and only function calls, not other addresses) that are repeated in a loop in a certain order. You can assume this loop contains more than one function call. 
#### Does each function returned by detect_loop.py need to be called the same number of times in the entire trace?
No, some functions may be called outside of the loop. However, for this project, you can assume the function calls in the loop will have a similar (although not nesecarily identical) number of calls. 


## Android Malware
#### Do I need to complete the Windows/Linux malware sections first?
No, the two sections are independent and can be completed separately.
#### The Android emulator is taking a long time to load.
The Android emulator can take a long time to load, especially the first time that you run it. However, if it is taking an extremely long time it may be a memory issue and you may need to increase the RAM available to the virtual machine.
#### How do I send an SMS to the emulated Android phone?
Read through the Android cheat sheet on page 107 of the write-up, it shows you how to send an SMS as well as how to perform other common functions.
#### Does the country code I find need to correspond to a real country code?
No, the project uses simulated country codes. Therefore, the country code you find may or may not correspond to an existing country code.
#### How small of an change is required in the Smali code?
The change you make to the Smali code will be on the scale of a few characters.
