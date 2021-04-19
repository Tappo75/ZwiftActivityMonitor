Zwift Activity Monitor
======================

## The Power is Within You

This application allows Zwift users to monitor their moving average power and FTP in real-time.  It also provides valuable metrics to the rider such as average and normalized power (NP), intensity factor (IF), and total suffer score (TSS).  For the racer and time-trialist, there's also the ability to configure distance based splits with optional goals.  


![main_view](https://github.com/ruffk/ZwiftActivityMonitor/raw/master/ZwiftActivityMonitor/images/MainView.png)
Example of Main View window


![split_view](https://github.com/ruffk/ZwiftActivityMonitor/raw/master/ZwiftActivityMonitor/images/SplitView.png)
Example of Split View window

## How It Works

Zwift Activity Montitor (or ZAM for short), monitors outgoing network packets generated by the Zwift application and
aggregates the data into statistical moving averages.

The network packets that ZAM consumes contain some important statistics.  Some of them are:
<ol>
	<li>Current power output</li>
	<li>Current heartrate (if wearing an HRM)</li>
	<li>Distance travelled</li>
	<li>Time spent riding</li>
</ol>

## Prerequisites

Before you begin, ensure you have met the following requirements:
* You have installed the latest version of Npcap: Packet capture library for Windows. (https://nmap.org/npcap/#download)

## Installing Zwift Activity Monitor (Windows Only)

Note: The Setup-ZAM.exe file is signed by a certificate.

To install Zwift Activity Monitor, follow these steps:

<ol>
	<li>Make sure you've installed the latest version of Npcap from the link above in Prerequisites.</li>
	<li>Download the latest Setup-ZAM.exe release from this GitHub repository.</li>
	<li>Run the installation.  The installation is signed, but you may still receive a popup from Windows SmartScreen.</li>
</ol>

## Using Zwift Activity Monitor

When you launch ZAM for the first time, you will be presented with the configuration window.  The following section describes this important step.

### Configuration

ZAM is easily configured via a set of configuration tab pages in the <b>Analyze->Options</b> dialog.

#### Options -> System Configuration Tab

ZAM first and foremost needs to know what network you use when running Zwift.  It's usually pretty simple as most
computers are either Wi-Fi or direct Ethernet cabled.  Within ZAM there is a packet monitoring system which MUST be started
in order to use ZAM.  This can either be done manually each time you run ZAM (by clicking the Start button), or by checking Auto-Start.

<ol>
	<li>Current User - The user profile that will be used during this ZAM session.  This defaults to the Default User Profile.</li>
	<li>Network - The network in your computer you use when running Zwift.</li>
	<li>Auto-Start - Whether to start the Zwift Packet Monitoring service automatically when ZAM starts.</li>
	<li>Window Position - Once you find where you like the ZAM window to sit, enter those coordinates and it will open there each time.</li>
</ol>

![system_options](https://github.com/ruffk/ZwiftActivityMonitor/raw/master/ZwiftActivityMonitor/images/SystemOptions.png)

#### Options -> User Configuration Tab

Multiple user profiles are ideal for multi-rider households, or if you'd like to be able to quickly select a different collector set. 
A default profile is provided for you, but you should configure it properly before using.

<ol>
	<li>Name - Identifies the rider.</li>
	<li>Weight - In Kilos or Pounds, preferably </li>
	<li>FTP - From your last FTP test or the value that Zwift has.</li>
	<li>Default moving average collector selection</li>
</ol>

The moving average collectors selected will be shown by default for this user.  However, you can select different collectors from the main ZAM window. 

Note: <b>It is VERY important to set the weight and FTP fields properly!</b>  These are used to calculate Watts/Kilo and Intensity Factor.

![user_profiles](https://github.com/ruffk/ZwiftActivityMonitor/raw/master/ZwiftActivityMonitor/images/UserProfiles.png)

#### Options -> Collector Configuration Tab

ZAM uses moving average collectors to present statistics on the screen in real-time.  A collector has the following attributes:

<ol>
	<li>Time Duration - The period for which a collector retains data</li>
	<li>Average Power display format - Moving average for all values currently in the collector.</li>
	<li>Maximum Power display format - The maximum value attained from the moving average.</li>
	<li>FTP display format - Maximum power value * 0.95 (Most applicable to the 20 minute collector).</li>
</ol>

Display Format can be shown in:

<ol>
	<li>Watts - Rounded to nearest whole number.</li>
	<li>Watts/Kilo - Shown as #.##</li>
	<li>Hidden - Not shown.</li>
</ol>

![collectors](https://github.com/ruffk/ZwiftActivityMonitor/raw/master/ZwiftActivityMonitor/images/Collectors.png)

#### Options -> Splits Configuration Tab

ZAM allows you to configure distance based splits to review your progress while riding.  Optionally, you can also configure goals so that you'll know if you're ahead or behind on your split times.  A split has the following attributes:

<ol>
	<li>Show Splits - When checked, the Splits View window will display automatically for 5 seconds when the distance is hit.</li>
	<li>Splits Every - This determines the distance (in km or mi) that splits occur.</li>
	<li>Calculate Goal - When checked, the splits view window will show a +/- indicator of your time vs the split time.</li>
	<li>Goal Time and Goal Distance - Together these are used to automatically calculate the number of splits and the target split times.</li>
</ol>

An example of the Splits View window is shown at the beginning of this readme file.

![splits](https://github.com/ruffk/ZwiftActivityMonitor/raw/master/ZwiftActivityMonitor/images/Splits.png)

### Using While Zwifting

#### Quick Start

**Important Note: The activity monitor can only overlay Zwift if it (Zwift) is configured to run in windowed mode.**

<ol>
	<li>Start the Zwift Packet Monitoring service from the Analyze->Options System Tab by pressing Start.  Maybe while you're there select the Auto-Start option.</li>
	<li>Click Analyze->Start.</li>
	<li>Pedal away!</li>
	<li>Click Analyze->Stop when done.</li>
</ol>

#### Timer Set-Up

If you've ever done a WTRL TTT then you know there's usually a delayed start after the banner drops. Or, maybe you're in an event pen and don't want to worry about clicking Analyze->Start when the banner drops.  We've got you covered! Setting the timer allows you to pre-determine the ZAM start time.  You set it up and a countdown begins.  When the countdown ends, the system "clicks" Start for you.

<ol>
	<li>Click Analyze->Setup Timer.</li>
	<li>Set your delay time.</li>
	<li>Click the Start Timer button.</li>
	<li>When the countdown ends, start pedalling!</li>
	<li>If you change your mind or need to reset the timer, Click Analyze->Stop Timer and repeat the setup process.</li>
</ol>

![setup_timer](https://github.com/ruffk/ZwiftActivityMonitor/raw/master/ZwiftActivityMonitor/images/SetupTimer.png)

## Contributing to Zwift Activity Monitor

See the GitHub documentation on [creating a pull request] (https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/creating-a-pull-request).

## Credits

Brad Walker for development of the ZwiftPacketMonitor library (https://github.com/braddwalker/ZwiftPacketMonitor) and giving me great ideas.

<div>Icons made by <a href="" title="photo3idea_studio">photo3idea_studio</a> from <a href="https://www.flaticon.com/" title="Flaticon">www.flaticon.com</a></div>

## Contact

If you want to contact me you can reach me at <mailto:ruff.kevin@outlook.com>.

## License

This project uses the following license: [MIT License] (https://github.com/ruffk/ZwiftActivityMonitor/blob/master/LICENSE).
