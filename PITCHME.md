---?image=assets/images/gitpitch-audience.jpg
@title[Platform Build Lab]
<br><br><br><br><br>
## <span class="gold"   >UEFI & EDK II Training</span>

#### UEFI Shell Lab w/ Windows Emulation

<br>
<span style="font-size:0.75em" ><a href='http://www.tianocore.org'>tianocore.org</a></span>
Note:
  PITCHME.md for UEFI / EDK II Training  UEFI Shell Windows Lab

  Copyright (c) 2020, Intel Corporation. All rights reserved.<BR>

  Redistribution and use in source (original document form) and 'compiled'
  forms (converted to PDF, epub, HTML and other formats) with or without
  modification, are permitted provided that the following conditions are met:

  1) Redistributions of source code (original document form) must retain the
     above copyright notice, this list of conditions and the following
     disclaimer as the first lines of this file unmodified.

  2) Redistributions in compiled form (transformed to other DTDs, converted to
     PDF, epub, HTML and other formats) must reproduce the above copyright
     notice, this list of conditions and the following disclaimer in the
     documentation and/or other materials provided with the distribution.

  THIS DOCUMENTATION IS PROVIDED BY TIANOCORE PROJECT "AS IS" AND ANY EXPRESS OR
  IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF
  MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO
  EVENT SHALL TIANOCORE PROJECT  BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL,
  SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO,
  PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS;
  OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY,
  WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR
  OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS DOCUMENTATION, EVEN IF
  ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.



---  
@title[Lesson Objective]
<BR>
### <p align="center"<span class="gold"   >Lesson Objective </span></p><br>

<!---  Add bullets using https://fontawesome.com/cheatsheet certificate
-->

 @fa[certificate gp-bullet-green]<span style="font-size:0.9em">&nbsp;&nbsp;Run UEFI Shell  (Windows Emulation)</span><br><br>
 @fa[certificate gp-bullet-cyan]<span style="font-size:0.9em">&nbsp;&nbsp;Run UEFI Shell Commands</span><br><br>
 @fa[certificate gp-bullet-yellow]<span style="font-size:0.9em">&nbsp;&nbsp;Run UEFI Shell Scripts</span> <br>
 

---?image=assets/images/binary-strings-black2.jpg
@title[UEFI Shell Lab with Win Emulation Section]
<br><br><br><br><br>
### <span class="gold"  >&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;UEFI Shell Lab with Win Emulation</span>
<span style="font-size:0.9em" > &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span>



---?image=/assets/images/slides/Slide4.JPG
@title[Invoke Win Emulation ]
<p align="right"><span class="gold" ><b>Invoke Win Emulation</b></span></p>
@snap[north-west span-53 ]
<br>
<br>
<br>
<br>
<br>
@box[bg-black text-white rounded my-box-pad2  ](<p style="line-height:60% "><span style="font-size:0.9em;" ><br><br><br><br><br><br><br><br>&nbsp;</span></p>)
@snapend

<span style="font-size:0.9em" >From the VS command Prompt</span>


@snap[north-west span-54 ]
<br>
<br>
<br>
<br>
<p style="line-height:40%" align="left" ><span style="font-size:0.4em; font-family:Consolas;"><br>&nbsp;&nbsp;
 &gt; CD C:\FW\edk2-ws<br>&nbsp;&nbsp;
 <font color="#A8ff60"> &num; set up PACKAGES_PATH </font><br>&nbsp;&nbsp;
 &gt; set WORKSPACE=%CD% <br>&nbsp;&nbsp;
 &gt; @size[.8em](set PACKAGES_PATH=%WORKSPACE%\edk2;%WORKSPACE%\edk2-libc )<br>&nbsp;&nbsp;
 &gt; cd edk2 <br>&nbsp;&nbsp;
 &gt; edksetup Rebuild <br>&nbsp;&nbsp;
 &gt; Build -a X64 <br>&nbsp;&nbsp;
 &gt; RunEmulator.bat <br>&nbsp;&nbsp;
</span></p>
@snapend



Note:
- From the VS  command prompt
<pre>
CD C:\FW\edk2-ws
# set up PACKAGES_PATH 
$> set WORKSPACE=%CD%
$> set PACKAGES_PATH=%WORKSPACE%\edk2;%WORKSPACE%\edk2-libc
$> cd edk2
$> edksetup Rebuild
$> Build -a X64
$> RunEmulator.bat
</pre>





---?image=assets/images/binary-strings-black2.jpg
@title[UEFI Shell Lab Commands Section]
<br><br><br><br><br>
## <span class="gold"  >&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;UEFI Shell Commands </span>
<span style="font-size:0.9em" > &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Commands from the Command Line Interface</span>


---
@title[Common Shell Commands ]
<p align="right"><span class="gold" >@size[1.1em](<b>Common Shell Commands For Debugging  </b>)</span><br>
<span style="font-size:0.75em;" >  </span></p>

@snap[west span-30]
<br>
<br>
@box[bg-grey-05 text-white  rounded  my-box-pad2](<p align="left" style="line-height:80%"><span style="font-size:0.8em; font-family:Consolas;" >&nbsp; help<br>&nbsp;  mm<br>&nbsp; mem<br>&nbsp; memmap<br>&nbsp; drivers<br>&nbsp; devices<br>&nbsp; devtree<br>&nbsp; dh<br>&nbsp; Load<br>&nbsp; dmpstore<br>&nbsp; stall<br>&nbsp;</span></p>)
@snapend

@snap[east span-65]
@box[bg-royal text-white  rounded](<b>"-b" is the command line parameter for breaking after each page.</b><br>)
@snapend

Note:

Next for this lab there are a few shell commands that will help us with debugging. For example if you are writing a driver, you would want to get familiar with these shell commands. Each of these commands will have a help option to give you further information about these commands.

We are not going to go all were these in detail but just to make you aware of the shell commands.



---?image=/assets/images/slides/Slide7.JPG
@title[Shell Help Command ]
<p align="right"><span class="gold" >@size[1.1em](<b>Shell Help  </b>)</span><br>
<span style="font-size:0.75em;" >  </span></p>

@snap[north-west span-33]
<br>
<br>
@box[bg-black text-white  rounded  my-box-pad2 ](<p align="left" style="line-height:20%"><span style="font-size:0.56em; font-family:Consolas;" >&nbsp;&nbsp;<font color="yellow">Shell&gt;&nbsp;</font>help -b<br>&nbsp;</span></p>)
@snapend




Note:

Next let’s just try the help shell command. So once you reach the shell go ahead and type: “help –b”
And what you will see is the list of all the shell commands built into this platform followed by a one liner information about each command.
To exit, this emulation simply type: “reset”


---?image=/assets/images/slides/Slide8.JPG
@title[Shell MemMap Command help ]
<p align="right"><span class="gold" >@size[1.1em](<b>Shell "`Memmap`"  </b>)</span><br>
<span style="font-size:0.75em;" >  </span></p>


@snap[north-west span-33]
<br>
<br>
@box[bg-black text-white  rounded  my-box-pad2 ](<p align="left" style="line-height:20%"><span style="font-size:0.56em; font-family:Consolas;" >&nbsp;&nbsp;<font color="yellow">Shell&gt;&nbsp;</font>memmap<br>&nbsp;</span></p>)
@snapend

@snap[north-west span-99]
<br>
<br>
<p style="line-height:80%" align="left" ><span style="font-size:0.8em;" ><br>&nbsp;
Displays the memory map maintained by the UEFI environment</span></p>
@snapend


Note:


---?image=/assets/images/slides/Slide9.JPG
@title[Shell mm -?  Command ]
<p align="right"><span class="gold" >@size[1.1em](<b>Shell "`mm`"  </b>)</span><br>
<span style="font-size:0.75em;" >  </span></p>

@snap[north-west span-33]
<br>
<br>
@box[bg-black text-white  rounded  my-box-pad2 ](<p align="left" style="line-height:20%"><span style="font-size:0.56em; font-family:Consolas;" >&nbsp;&nbsp;<font color="yellow">Shell&gt;&nbsp;</font>mm -? -b<br>&nbsp;</span></p>)
@snapend

@snap[north-west span-40]
<br>
<br>
<p style="line-height:80%" align="left" ><span style="font-size:0.8em;" ><br><br>
Help for "mm" command shows options for different types of memory and I/O that can be modified
</span></p>
@snapend


Note:


---?image=/assets/images/slides/Slide10.JPG
@title[Shell mm   Command ]


<p align="right"><span class="gold" >@size[1.1em](<b>Shell "`mm`"  </b>)</span><br>
<span style="font-size:0.75em;" >  </span></p>

@snap[north-west span-33]
<br>
<br>
@box[bg-black text-white  rounded  my-box-pad2 ](<p align="left" style="line-height:20%"><span style="font-size:0.56em; font-family:Consolas;" >&nbsp;&nbsp;<font color="yellow">Shell&gt;&nbsp;</font>mm **<br>&nbsp;</span></p>)
@snapend

@snap[north-east span-50]
<br>
<br>
<p style="line-height:67%" align="left" ><span style="font-size:0.7em;" ><br><br>&nbsp;
&ast;&ast;Pick a location from the MemMap command on Previous slide<br><br>
<span style="background-color: #000000">
&nbsp;&nbsp;<font face="Consolas">@size[.4em]( BS_Data    <font color="cyan">00000117FC9F5000</font>-00000117FCA1CFFF 0000000000000028 . . .)</font> &nbsp;&nbsp; </span><br>
MM can display / modify any location <br><br>
Do <font color="red"><b>not</b></font> try (below) in Win Emulator. Because the emulator will crash.<br><br>
<span style="background-color: #000000"><font face="Consolas">@size[.7em](<font color="yellow">&nbsp;&nbsp;Shell&gt;</font> mm 0000)  </font>&nbsp;&nbsp; </span>
<br><br>"q" to quit
</span></p>
@snapend

@snap[south-east span-30]
<p align="left"><span style="font-size:01.5em;" ><font color="red"><b>&#9747;</b></font></span></p>
<p style="line-height:10%" align="left" ><span style="font-size:0.7em;" >
<br><br><br><br><br><br>
</span></p>
<br>
@snapend

Note:

Why doesn’t it work on windows emulator mm 0?

Because the Emulator is a Windows Application and trying to access location 00 will force the Windows app to not allow your application to access location 0



---?image=/assets/images/slides/Slide11.JPG
@title[Shell mem Command ]
<p align="right"><span class="gold" >@size[1.1em](<b>Shell "`Mem`"  </b>)</span><br>
<span style="font-size:0.75em;" >  </span></p>

@snap[north-west span-33]
<br>
<br>
@box[bg-black text-white  rounded  my-box-pad2 ](<p align="left" style="line-height:20%"><span style="font-size:0.56em; font-family:Consolas;" >&nbsp;&nbsp;<font color="yellow">Shell&gt;&nbsp;</font>mem <br>&nbsp;</span></p>)
@snapend

@snap[north-west span-99]
<br>
<br>
<p style="line-height:80%" align="left" ><span style="font-size:0.8em;" ><br>
Displays the contents of the system or device memory without arguments, displays the system memory configuration.
</span></p>
@snapend


@snap[east span-28]
<p style="line-height:65%" align="left" ><span style="font-size:0.7em;" ><br>
<font color="yellow">UEFI System<br>  Table Pointer</font>
</span></p>
@snapend

Note:


---?image=/assets/images/slides/Slide12.JPG
@title[Shell drivers Command ]
<p align="right"><span class="gold" >@size[1.1em](<b>Shell "`Drivers`"  </b>)</span><br>
<span style="font-size:0.75em;" >  </span></p>

@snap[north-west span-33]
<br>
<br>
@box[bg-black text-white  rounded  my-box-pad2 ](<p align="left" style="line-height:20%"><span style="font-size:0.56em; font-family:Consolas;" >&nbsp;&nbsp;<font color="yellow">Shell&gt;&nbsp;</font>drivers -b <br>&nbsp;</span></p>)
@snapend

@snap[north-east span-33]
<br>
<br>
<p style="line-height:67%" align="left" ><span style="font-size:0.7em;" ><br><br>
Displays the UEFI driver list.
<br><br>
@size[.8em](To get a description of teach section in the list, Use:)<br>
<span style="background-color: #000000"><font face="Consolas">@size[.67em](<font color="yellow">&nbsp;&nbsp;Shell&gt;</font> drivers -?)  </font>&nbsp;&nbsp; </span>
<br><br>"`q`" to quit
</span></p>
@snapend


Note:



---?image=/assets/images/slides/Slide13.JPG
@title[Shell devices Command ]
<p align="right"><span class="gold" >@size[1.1em](<b>Shell "`Devices`"  </b>)</span><br>
<span style="font-size:0.75em;" >  </span></p>

@snap[north-west span-33]
<br>
<br>
@box[bg-black text-white  rounded  my-box-pad2 ](<p align="left" style="line-height:20%"><span style="font-size:0.56em; font-family:Consolas;" >&nbsp;&nbsp;<font color="yellow">Shell&gt;&nbsp;</font>devices -b <br>&nbsp;</span></p>)
@snapend

@snap[north-west span-100]
<br>
<br>
<p style="line-height:80%" align="left" ><span style="font-size:0.8em;" ><br>
Displays a list of devices that UEFI drivers manage.
</span></p>
@snapend

@snap[south-west span-100]
<p style="line-height:80%" align="left" ><span style="font-size:0.78em;" ><br>
For the Windows Emulation there is not that many devices
</span></p>
@snapend

Note:


---?image=/assets/images/slides/Slide14.JPG
@title[Shell devtree Command ]
<p align="right"><span class="gold" >@size[1.1em](<b>Shell "`Devtree`"  </b>)</span><br>
<span style="font-size:0.75em;" >  </span></p>

@snap[north-west span-33]
<br>
<br>
@box[bg-black text-white  rounded  my-box-pad2 ](<p align="left" style="line-height:20%"><span style="font-size:0.56em; font-family:Consolas;" >&nbsp;&nbsp;<font color="yellow">Shell&gt;&nbsp;</font>devtree -b <br>&nbsp;</span></p>)
@snapend

@snap[north-west span-100]
<br>
<br>
<p style="line-height:80%" align="left" ><span style="font-size:0.8em;" ><br>
Displays tree of devices currently managed by UEFI drivers.
</span></p>
@snapend


Note:


---?image=/assets/images/slides/Slide15.JPG
@title[Shell handle Database Command ]
<p align="right"><span class="gold" >@size[1.1em](<b>Shell "`Devtree`"  </b>)</span><br>
<span style="font-size:0.75em;" >  </span></p>

@snap[north-west span-33]
<br>
<br>
@box[bg-black text-white  rounded  my-box-pad2 ](<p align="left" style="line-height:20%"><span style="font-size:0.56em; font-family:Consolas;" >&nbsp;&nbsp;<font color="yellow">Shell&gt;&nbsp;</font>dh -b <br>&nbsp;</span></p>)
@snapend

@snap[north-west span-100]
<br>
<br>
<p style="line-height:70%" align="left" ><span style="font-size:0.75em;" ><br>
Dump Handle - Displays the device handles associated with UEFI drivers
</span></p>
@snapend


@snap[north-east span-43]
<br>
<br>
<br>
<br>
<br>
<p style="line-height:67%" align="left" ><span style="font-size:0.67em;" ><br><br>
Also try "` dh -d`" with handle number to get more information on that handle.
</span></p>
@snapend


Note:

Also try dh -d with handle number to get more information on that handle.

---?image=/assets/images/slides/Slide16.JPG
@title[Shell Load Command ]

<p align="right"><span class="gold" >@size[1.1em](<b>Shell "`Load`"  </b>)</span><br>
<span style="font-size:0.75em;" >  </span></p>

@snap[north-west span-33]
<br>
<br>
@box[bg-black text-white  rounded  my-box-pad2 ](<p align="left" style="line-height:20%"><span style="font-size:0.56em; font-family:Consolas;" >&nbsp;&nbsp;<font color="yellow">Shell&gt;&nbsp;</font>load -? -b <br>&nbsp;</span></p>)
@snapend

@snap[north-west span-100]
<br>
<br>
<p style="line-height:80%" align="left" ><span style="font-size:0.8em;" ><br>
Loads a UEFI driver into memory
</span></p>
@snapend




Note:


---?image=/assets/images/slides/Slide17.JPG
@title[Shell Load Command ]

<p align="right"><span class="gold" >@size[1.1em](<b>Shell "`Dmpstore`"  </b>)</span><br>
<span style="font-size:0.75em;" >  </span></p>

@snap[north-west span-35]
<br>
<br>
@box[bg-black text-white  rounded  my-box-pad2 ](<p align="left" style="line-height:20%"><span style="font-size:0.56em; font-family:Consolas;" >&nbsp;&nbsp;<font color="yellow">Shell&gt;&nbsp;</font>dmpstore -all -b <br>&nbsp;</span></p>)
@snapend

@snap[north-west span-100]
<br>
<br>
<p style="line-height:80%" align="left" ><span style="font-size:0.8em;" ><br>
Display the contents of the NVRAM variables
</span></p>
@snapend




Note:

---
@title[Shell Stall Command ]
<p align="right"><span class="gold" >@size[1.1em](<b>Shell "`Stall`"  </b>)</span><br>
<span style="font-size:0.75em;" >  </span></p>

@snap[north-west span-33]
<br>
<br>
@box[bg-black text-white  rounded  my-box-pad2 ](<p align="left" style="line-height:20%"><span style="font-size:0.56em; font-family:Consolas;" >&nbsp;&nbsp;<font color="yellow">Shell&gt;&nbsp;</font>stall 10000000<br>&nbsp;</span></p>)
@snapend

@snap[north-west span-100]
<br>
<br>
<p style="line-height:80%" align="left" ><span style="font-size:0.8em;" ><br>
Stalls the operation for a specified number of microseconds
</span></p>
@snapend

@snap[north span-35]
<br>
<br>
<br>
<br>
<br>
<br>
@box[bg-grey-05 text-white  rounded  my-box-pad2 ](<p align="left" style="line-height:35%"><span style="font-size:0.40em; font-family:Consolas;" >&nbsp;&nbsp;<font color="yellow">Shell&gt;&nbsp;</font><font color="gray">stall 10000000</font><br>&nbsp;&nbsp;<font color="yellow">Shell&gt;&nbsp;</font>_<br>&nbsp;</span></p>)

@snapend
Note:



---?image=assets/images/binary-strings-black2.jpg
@title[UEFI Shell Lab Scripts Section]
<br><br><br><br><br>
## <span class="gold"  >&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;UEFI Shell Scripts</span>
<span style="font-size:0.9em" > &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Use Scripting with UEFI Shell</span>

---
@title[UEFI Shell Scripts ]
<p align="right"><span class="gold" >@size[1.1em](<b>UEFI Shell Scripts  </b>)</span><br>
<span style="font-size:0.75em;" >  </span></p>
<br>
<span style="font-size:0.9em" >The UEFI Shell can execute commands from a file, which is called a batch script file (<font face="Consolas" color="yellow"><b>.nsh</b></font> files). </span>
<br>
<br>
<span style="font-size:0.8em" ><font color="cyan"><b>Benefits:</b></font> These files allow users to simplify routine or repetitive tasks. <br>
- <span style="font-size:0.7em" >Perform basic flow control. </span>
- <span style="font-size:0.7em" >Allow branching and looping in a script. </span>
- <span style="font-size:0.7em" >Allow users to control input and output and call other batch programs (known as script nesting). </span>

Note:
The UEFI Shell can execute commands from a file, which is called a batch script file (.nsh files). 
<br>
Benefits: These files allow users to simplify routine or repetitive tasks. <br>
- Perform basic flow control. 
- Allow branching and looping in a script. 
- Allow users to control input and output and call other batch programs (known as script nesting). 

---?image=/assets/images/slides/Slide21.JPG
@title[Writing UEFI Shell Scripts]
<p align="right"><span class="gold" >@size[1.1em](<b>Writing UEFI Shell Scripts  </b>)</span><br>
<span style="font-size:0.75em;" >  </span></p>


@snap[north-west span-55]
<br>
<br>
<p style="line-height:67%" align="left" ><span style="font-size:0.67em;" ><br><br>
At the shell prompt, type "`fs0:`"
</span></p>
@box[bg-black text-white  rounded  my-box-pad2 ](<p align="left" style="line-height:42%"><span style="font-size:0.46em; font-family:Consolas;" >&nbsp;&nbsp;<font color="yellow">Shell&gt;&nbsp;</font>fs0:<br><font color="yellow">&nbsp;&nbsp;FS0:/&gt;&nbsp;</font><br>&nbsp;</span></p>)
<p style="line-height:67%" align="left" ><span style="font-size:0.67em;" >
<b>Type :</b>
<span style="background-color: #000000"><font face="Consolas">@size[.67em](&nbsp;echo Hello World)  </font>&nbsp;&nbsp; </span>
</span></p>
<br>
<p style="line-height:67%" align="left" ><span style="font-size:0.67em;" ><br><br>
<font color="#A8ff60"><br>
Press "F2"<br>
Enter<br>
Press "F3" to exit<br>
</span></p>
@snapend


Note:

With the UEFI shell There is an editor included. This is a very simple editor but can help if running on the target system without an OS "Nice" editor available.

SHell editor help  menu - Cnt W

At the shell prompt

Shell> fs0:

FS0:\> edit HelloScript.nsh 

Type : echo “Hello World“



Press “F2”- Enter Press “F3” to exit

---
@title[Hello World Script]
<p align="right"><span class="gold" >@size[1.1em](<b>Hello World Script </b>)</span><br>
<span style="font-size:0.75em;" >  </span></p>

@snap[north-west span-100]
<br>
<br>
<p style="line-height:80%" align="left" ><span style="font-size:0.8em;" ><br>
In the shell, type HelloScript for the following result:
</span></p>
@snapend




@snap[north span-33]
<br>
<br>
<br>
<br>
<br>
<br>
@box[bg-black text-white  rounded  my-box-pad2 ](<p align="left" style="line-height:42%"><span style="font-size:0.46em; font-family:Consolas;" >&nbsp;&nbsp;<font color="yellow">FS0:/&gt;&nbsp;</font>helloscript.nsh<br><font color="yellow">&nbsp;&nbsp;FS0:/&gt;&nbsp;</font>echo Hello World<br>&nbsp;&nbsp;Hello World<br>&nbsp;&nbsp;<font color="yellow">FS0:/&gt;&nbsp;</font>_<br>&nbsp;</span></p>)
@snapend

@snap[south-west span-100]
<br>
<p style="line-height:70%" align="left" ><span style="font-size:0.7em;" ><br>
Close the Win emulation, type: "reset"<br><br>
<span style="background-color: #000000"><font face="Consolas">@size[.67em](<font color="yellow">FS0:/&gt;&nbsp;</font> reset)  </font>&nbsp;&nbsp; </span>
</span></p>
<br>
<br>
@snapend



Note:

In the shell, type HelloScript for the following result:

```
HelloScript.nsh
```

Close - at the shell prompt type : reset

---?image=/assets/images/slides/Slide23.JPG
@title[UEFI Shell Nested Scripts ]
<p align="right"><span class="gold" >@size[1.1em](<b>UEFI Shell Nested Scripts </b>)</span><br>
<span style="font-size:0.75em;" >  </span></p>

@snap[north-west span-100]
<br>
<br>
<p style="line-height:70%" align="left" ><span style="font-size:0.7em;" ><br>
Copy the Scripts from the <font face="Consolas">/FW/LabSampleCode/ShellScripts</font> to the runtime directory @size[.8em](<font face="Consolas">C:/FW/edk2-ws/Build/EmulatorX64/DEBUG_VS20<font color="yellow"><i>nn</i>x86</font></font>/X64)
</span></p>
@snapend




Note:

Copy the Scripts from the `/FW/LabSampleCode/ShellScripts` to the Nt32 runtime directory  `C:/FW/edk2/Build/NT32IA32/DEBUG_VS201nx86/IA32`

---
@title[UEFI Shell Script Example]
<br>
<p align="center"><span class="gold" >UEFI Shell Script Example</span></p>

<span style="font-size:0.8em"><font color="yellow">Script1.nsh</font></span>
```shell
# Simple UEFI Shell script file
echo  -off
script2.nsh
if exist %cwd%Mytime.log then
     type Mytime.log
endif
echo "%HThank you.” “%VByeBye:) %N"
```
<span style="font-size:0.8em"><font color="yellow">Script2.nsh</font></span>
```shell
# Show nested scripts
time > Mytime.log
for %a run (3 1 -1)
    echo %a counting down
endfor
```

Note:
walk through the script calling the second script
- if
- for loop
  - %a counting down...
  
---?image=/assets/images/slides/Slide25.JPG
@title[Run UEFI Shell Scripts ]
<p align="right"><span class="gold" >@size[1.1em](<b>Run UEFI Shell Scripts </b>)</span><br>
<span style="font-size:0.75em;" >  </span></p>

@snap[north-west span-55]
<br>
<br>
<p style="line-height:80%" align="left" ><span style="font-size:0.8em;" ><br>
From the VS command Prompt<br>
<span style="background-color: #000000"><font face="Consolas">@size[.67em](C:\\FW\\edk2&gt;&nbsp;RunEmulator.bat)  </font>&nbsp;&nbsp; </span>
<br>
<br>
At the Shell prompt Type:
</span></p>
@box[bg-black text-white  rounded  my-box-pad2 ](<p align="left" style="line-height:42%"><span style="font-size:0.46em; font-family:Consolas;" >&nbsp;&nbsp;<font color="yellow">Shell&gt;&nbsp;</font>fs0:<br><font color="yellow">&nbsp;&nbsp;FS0:\\&gt;&nbsp;</font>Script1<br><font color="yellow">&nbsp;&nbsp;FS0:\\&gt;&nbsp;</font><br><font color="yellow">&nbsp;&nbsp;FS0:\\&gt;&nbsp;</font>Edit Script1.nsh<br><br>&nbsp;</span></p>)
@snapend


Note:
From the VS command Prompt
   `C:\FW\edk2> Build Run`


 At the Shell prompt Type  
```
Shell> fs0:
FS0:\> Script1

FS0:\> Edit Script1.nsh
```


 
---?image=/assets/images/slides/Slide26.JPG
@title[Run UEFI Shell Scripts cont ]
<p align="right"><span class="gold" >@size[1.1em](<b>Run UEFI Shell Scripts </b>)</span><br>
<span style="font-size:0.75em;" >  </span></p>

@snap[north-west span-100]
<br>
<br>
<p style="line-height:70%" align="left" ><span style="font-size:0.7em;" ><br>
Remove the "&num;" on the first line<br>
<br>
<br>
<b>Press "F2"<br>
Enter<br>
Press "F3" to exit</b><br><br>
Type<br> 
<span style="background-color: #000000"><font face="Consolas">@size[.67em](<font color="yellow">FS0:\\&gt;&nbsp;</font> Script1)  </font>&nbsp;&nbsp; </span>
</span></p>
@snapend


Note:
- Remove the “#” on the first line


- Press “F2”
- Enter
- Press “F3” to exit
- Type 
- FS0:\> Script1


---  
@title[Summary]
<BR>
### <p align="center"><span class="gold"   >Summary </span></p><br>

 @fa[certificate gp-bullet-green]<span style="font-size:0.9em">&nbsp;&nbsp;Run UEFI Shell  (Windows Emulation)</span><br><br>
 @fa[certificate gp-bullet-cyan]<span style="font-size:0.9em">&nbsp;&nbsp;Run UEFI Shell Commands</span><br><br>
 @fa[certificate gp-bullet-yellow]<span style="font-size:0.9em">&nbsp;&nbsp;Run UEFI Shell Scripts</span> <br>
 

 

---?image=assets/images/gitpitch-audience.jpg
@title[Questions]
<br>
![Questions](/assets/images/questions.JPG =10x) 


---?image=assets/images/gitpitch-audience.jpg
@title[Logo Slide]
<br><br><br>
![Logo Slide](/assets/images/TianocoreLogo.png =10x)


---
@title[Acknowledgements]
#### <p align="center"><span class="gold"   >Acknowledgements</span></p>

```c++
/**
Redistribution and use in source (original document form) and 'compiled' forms (converted
to PDF, epub, HTML and other formats) with or without modification, are permitted provided
that the following conditions are met:

Redistributions of source code (original document form) must retain the above copyright 
notice, this list of conditions and the following disclaimer as the first lines of this 
file unmodified.

Redistributions in compiled form (transformed to other DTDs, converted to PDF, epub, HTML
and other formats) must reproduce the above copyright notice, this list of conditions and 
the following disclaimer in the documentation and/or other materials provided with the 
distribution.

THIS DOCUMENTATION IS PROVIDED BY TIANOCORE PROJECT "AS IS" AND ANY EXPRESS OR IMPLIED 
WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND 
FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL TIANOCORE PROJECT BE 
LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES 
(INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, 
DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, 
WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) 
ARISING IN ANY WAY OUT OF THE USE OF THIS DOCUMENTATION, EVEN IF ADVISED OF THE POSSIBILITY 
OF SUCH DAMAGE.

Copyright (c) 2020, Intel Corporation. All rights reserved.
**/

```
