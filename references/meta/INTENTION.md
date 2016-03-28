#LibBWT

Named after the abbreviation for the *theoretical* [Java API
for Bluetooth Wireless Technology (JABWT)](https://en.wikipedia.org/wiki/Java_APIs_for_Bluetooth).

Other possible names include...

+ LibBTLEZ
+ LibWireless (ideally this would also implement netlike - yuck!)
+ LibBlue
+ BluetoothWT.framework / libBluetoothWT / WTBluetooth.framework ...
+ LibBLEWireless / BLEWireless.framework
+ LibBTWireless / BTWireless.framework

##Basic Plans

This project was created as part of the larger Pfing application project.
While Pfing really only ***needs*** to have range finding support, it would
be good for it to have general support for the [Bluetooth Protocol Stack](https://en.wikipedia.org/wiki/List_of_Bluetooth_protocols)
as well. This library attempts to offer that support in a standardized interface.

##Joining the Bluetooth Special Interest Group

Upon consideration and study I conclude that I am permitted, as an individual, to
join the [Bluetooth Special Interest Group](https://www.bluetooth.com/). In the
Bluetooth SIG [Membership Agreement](https://www.bluetooth.org/login/register/agreement.html)
there is provided a clear definition of who may become an "Adopter Member" of the
Bluetooth SIG.

>   <strong>Adopter Membership</strong> is open to any firm, corporation or other legal entity. Adopter Members
    have no right to participate in or chair any working groups of <em>Bluetooth</em> SIG. Adopter Members have no voting
    rights in regard to corporation level matters.

The question, then, is whether I as an individual am a "legal entity". According
to [businessdictionary.com](http://www.businessdictionary.com/definition/legal-entity.html)
the answer seems to be yes. The following is their definition of legal entity.

>   <dl>
        <dt>legal entity</dt>
        <dd>An association, corporation, partnership, proprietorship, trust, or individual that has legal standing in the eyes of law. A legal entity has legal capacity to enter into agreements or contracts, assume obligations, incur and pay debts, sue and be sued in its own right, and to be held responsible for its actions.</dd>
    </dl>

To reinforce this position, [thelawdictionary.com](http://thelawdictionary.org/legal-entity/)
provides a very similar definition.

>   <dl>
        <dt>What is LEGAL ENTITY?</dt>
        <dd>
            <p>A lawful or legally standing <a href="http://thelawdictionary.org/association/" title="The act of a number of persons who unite or join together for some special purpose or business. The union of a company of persons [...]">association</a>, <a href="http://thelawdictionary.org/corporation/" title="An artificial person or legal entity created by or under the authority of the laws of a state or nation, composed, in some rare instances, [...]">corporation</a>, <a href="http://thelawdictionary.org/partnership/" title="A voluntary contract between two or more competent persons to place their money, effects, labor, and skill, or some or all of them, in lawful [...]">partnership</a>, <a href="http://thelawdictionary.org/proprietorship/" title="1. Thisoccurs when a businesses or company is owned by one person or one family. It is not owned by several people or a group [...]">proprietorship</a>, trust, or <a href="http://thelawdictionary.org/individual/" title="As a noun, this term denotes a single person as distinguished from a group or class, and also, very commonly, a private or natural person [...]">individual</a>. Has <a href="http://thelawdictionary.org/legal-capacity/" title="Lawful capacity for an entity in its own name to enter into binding contracts, to sue and to be sued.">legal capacity</a> to (1) enter into agreements or contracts, (2) assume obligations, (3) incur and pay debts, (4) sue and be sued in its own right, and (5) to be <a href="http://thelawdictionary.org/accountable/" title="This party is assigned responsibilities and is in charge of the account in question.
            ">accountable</a> for illegal activities.</p>
        </dd>
    </dl>

##Language Support

The default implementation language will be Objective-C, and all initial
builds (except maybe for windows?) will be in the Objective-C language.
However it seems to me that once this standard Objective-C library is build,
it will not be difficult to add a C++ wrapper to it. Once the C++ wrapper is
built the implementation can really be ported to any other language based on
the demand that I realistically do not doubt will follow a successful
implementation of this library.

It would be very exciting to eventually provide a [JSR-82](https://jcp.org/ja/jsr/detail?id=82)
implementation that doesn't [provide L2CAP support exclusively on Windows](http://bluecove.org/).

##Library Model

The model - both objective and functional - of this library must be carefully
planned and considered. It is what will set this library apart from the other,
inaccessible, user-unfriendly Bluetooth frameworks such as [IOBluetooth](https://developer.apple.com/library/mac/documentation/DeviceDrivers/Reference/IOBluetooth/index.html#//apple_ref/doc/uid/TP30000814),
[BlueZ](http://www.bluez.org/), and even to some extent [CoreBluetooth](https://developer.apple.com/library/ios/documentation/CoreBluetooth/Reference/CoreBluetooth_Framework/).

Rather, this framework will be modeled on a much more user friendly paradigm such as
that of the JABWT API and high level HTTP(S) interfaces. The following are resources that
may provide helpful insights into how BlueTooth could be made user-friendly and,
most importantly, useful for a developer unfamiliar with the Bluetooth Protocol Stack.

<table border="1">
    <caption>
        <strong>Useful Resources Demonstrating an Intuitive Model</strong>
    </caption>
    <thead>
        <tr>
            <th>Resource</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>
                <a href="https://docs.oracle.com/javame/config/cldc/opt-pkgs/api/bluetooth/jsr082/">JSR-82 Spec</a>
            </td>
            <td>
                The Java interface can be expected to be both comprehensive and easy to use. It can also be expected to be thoroughly object oriented.
            </td>
        </tr>
        <tr>
            <td>
                <a href="http://htmlpreview.github.io/?https://github.com/karulis/pybluez/blob/master/docs/index.html">PyBluez</a>
            </td>
            <td>The (apparently) well liked PyBluez Python implementation of the Bluetooth Stack.</td>
        </tr>
        <tr>
            <td>
                <a href="http://developer.android.com/guide/topics/connectivity/bluetooth.html">Android Bluetooth API</a>
            </td>
            <td>The Android implementation of the Bluetooth Stack is also in Java, and therefore is likely very good.</td>
        </tr>
        <tr>
            <td>
                <a href="file:///Users/williamrosenbloom/Desktop/private_projects/pfing/frameworks/BTWireless/references/meta/blejs-docs/index.html">ble.js</a>
            </td>
            <td>Low-energy-only GATT implementation reduced to a more palatable <a href="https://github.com/evothings/cordova-ble">JavaScript API</a>.</td>
        </tr>
    </tbody>
</table>

##Functionality Goals

While the actual model of LibBWT is yet to be determined, the functionality is
something I have considered very much. The following is a ***preliminary*** overview
of what BLEWireless should facilitate for programmers.

+ Provide Bluetooth related graphical resources in *somewhat* the manner of IOBluetoothUI.framework.
+ Provide Bluetooth specification standard attributes and information, and an interface for
crreating UUID's that do not conflict with standards.
+ Provide a general, object-oriented Bluetooth socket for reading and writing - including with only ATT support.
+ Provide a metadata monitoring interface similar to RTCP.
+ Provide an error handling interface universal to all functionality of the library.
+ Provide an installer capable of downloading and rectifying missing dependencies.
+ Provide an interface to determine system Bluetooth capabilities/permissions.
+ Provide special, prebuilt, and simplified procedures for common Bluetooth tasks. These might include but
are not limited to the following.
    + AV Streaming (AVDTP) and Control (AVCTP).
    + Reading/Monitoring a Characteristic (ATT).
    + OBEX File/Blob Transfer (OBEX).
    + Network Proxying - HTTP Stream Style (BNEP).
    + SDP Device Discovery (SDP/HCI) and Analysis (ATT).
    + SDP Server/Daemon Setup (SDP/HCI).
    + Broadcast/Receive Telephony (TCS and MIDI).
+ Invisible and Automatic but Configurable Encryption (SMP).

####Blue SDK Support Graphic - Something to which to Aspire

![Blue SDK Supported Functionality](file:///Users/williamrosenbloom/Desktop/private_projects/pfing/frameworks/BTWireless/references/meta/BlueSDKDiagram.png)

##Platform Dependencies

Distributing for three (and maybe more) separate platforms, BTWireless will be based on different libraries for each
platform. There is the option of eventually using the non-free but official Bluetooth SIG [Blue SDK](http://www.opensynergy.com/en/products/blue-sdk/)
by OpenSynergy. However GNU has inspired me to hate non-free software. The following is a list of the open-source
libraries that may be used to implement the Bluetooth Protocol Stack on the target operating systems.

<table>
    <caption><strong>Libraries for Target Systems</caption>
    <thead>
        <tr>
            <th>System</th>
            <th>Library</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Darwin</td>
            <td>
                <a href="https://developer.apple.com/library/mac/documentation/DeviceDrivers/Reference/IOBluetooth/">IOBluetooth</a>
                and
                <a href="https://developer.apple.com/library/ios/documentation/CoreBluetooth/Reference/CoreBluetooth_Framework/">CoreBluetooth</a>
                and
                <a href="">CoreMidi</a>
                and maybe
                <a href="https://developer.apple.com/library/mac/documentation/DeviceDrivers/Reference/IOBluetoothUI/">IOBluetoothUI</a>
            </td>
        </tr>
        <tr>
            <td>Linux and GNU</td>
            <td>
                <a href="http://www.bluez.org/">BlueZ</a>
            </td>
        </tr>
        <tr>
            <td>Android</td>
            <td>
                <a href="https://android.googlesource.com/platform/external/bluetooth/bluedroid/">BlueDroid</a>
            </td>
        </tr>
        <tr>
            <td>BSD Systems</td>
            <td>
                <a href="http://gentoobrowse.randomdan.homeip.net/package/net-libs/libpcap">libpcap</a>
                <em>- This library may actually be useful on several systems</em>
            </td>
        </tr>
        <tr>
            <td>Windows and Cygwin</td>
            <td>
                Literally they just call it
                <a href="https://msdn.microsoft.com/en-us/library/windows/desktop/aa362932(v=vs.85).aspx">Bluetooth</a>
            </td>
        </tr>
    </tbody>
</table>

##Thread-Pooling

####In General - C++ on Linux and Windows

Servers will require thread-pooling to implement this app effectively. Therefore
**I need to use a solution for thread-pooling that can be ported to Windows**.
This means I will likely be using the [C++ `std` namespace threading library](http://en.cppreference.com/w/cpp/thread)
, or the [Boost threading library](http://www.boost.org/doc/libs/1_60_0/doc/html/thread.html)
for which a portable and open-source [C++ thread-pooling library](http://threadpool.sourceforge.net/)
already exists - though it is admittedly not near as customizable as I would like.

####In Particular - ObjC and GCD for Darwin and GNUstep

For Darwin and [GNUstep](http://www.gnu.org/software/gnustep/) enabled GNU machines
the answer to thread pooling is actually much simpler - use the embedded [GCD](https://developer.apple.com/library/ios/documentation/Performance/Reference/GCD_libdispatch_Ref/) and [NSOperation](https://developer.apple.com/library/ios/documentation/Cocoa/Reference/NSOperation_class/index.html#//apple_ref/occ/cl/NSOperation)
interfaces to handle asynchronous tasks. This saves a lot of coding time but also
**constitutes a huge sacrifice in customization of the thread-pool**. However
that sacrifice may well be worth it, considering it is the opinion of this statement from
Apple Developer's [Concurrency Programming Guide](https://developer.apple.com/library/ios/documentation/General/Conceptual/ConcurrencyProgrammingGuide/Introduction/Introduction.html#//apple_ref/doc/uid/TP40008091-CH1-SW1)
manual that thread programming can waste resources and may soon be a thing of
the past. In their [Concurrency and Application Design section](https://developer.apple.com/library/ios/documentation/General/Conceptual/ConcurrencyProgrammingGuide/ConcurrencyandApplicationDesign/ConcurrencyandApplicationDesign.html#//apple_ref/doc/uid/TP40008091-CH100-SW1)
they state the following.

>   <h3><strong>The Move Away from Threads</strong></h3>
>
>   Although threads have been around for many years and continue to have their uses, they do not solve the general problem of executing multiple tasks in a scalable way. With threads, the burden of creating a scalable solution rests squarely on the shoulders of you, the developer. You have to decide how many threads to create and adjust that number dynamically as system conditions change. Another problem is that your application assumes most of the costs associated with creating and maintaining any threads it uses.

##IPC Integration

For servers that listen for BlueTooth connections, it is advisable that some IPC
support be added directly into this library to make the lives of users easier. I
genuinely have no idea how IPC works on Windows, but there seems to be a portable
solution on GitHub.

The [libipc](https://github.com/kralf/libipc) library is portable to UNIX, Cygwn, MAC OS,
and Windows operatings systems according to its README.md file. It seems to offer
comprehensive IPC functions including the native creation of daemons. This option
is likely a necessity for Linux and Windows. However it is worth noting that **libipc
has a CMake based build system**.

#####Note Regarding `pthread_detatch`:

It is tempting to use the `pthread_detatch` function provided by the pthread API to
produce daemons, however this is not possible. The following is a quote from [the man7.org
Linux `pthread_detatch` man page](http://man7.org/linux/man-pages/man3/pthread_detach.3.html).

>   The detached attribute merely determines the behavior of the system
           when the thread terminates; it does not prevent the thread from being
           terminated if the process terminates using [exit(3)](http://man7.org/linux/man-pages/man3/exit.3.html) (or equivalently,
           if the main thread returns).

