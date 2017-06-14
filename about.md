---
title: What is 'Border Patrol'?
...

*Border Patrol* is a research project [funded by EPSRC](http://gow.epsrc.ac.uk/NGBOViewGrant.aspx?GrantRef=EP/N028201/1) as part of the [TIPS](https://www.epsrc.ac.uk/funding/calls/trustidentityprivacysecurity/) call (Trust, Identity, Privacy and Security in the Digital Economy).
It aims to make the design of hardware systems, in particular smart devices, proof against hidden malicious functionality.
It is an ambitious project combining very advanced type theory and compiler technology to hardware design.
Here, [Dr. Wim Vanderbauwhede](http://www.dcs.gla.ac.uk/~wim/) describes how the idea behind Border Patrol came about.

<div class="well">
 Some time ago I was contacted by EDF (a large utility provider) to conduct an analysis of the cybersecurity issues regarding FPGA-based smart SCADA controllers.
 I used to work as a chip designer and in CMOS technology qualification and I am an expert in FPGA (Field Programmable Gate Array) design so I am familiar with the entire process of creating such devices.

 I analysed the complete supply chain of such controllers for possible attack vectors.
 While doing this it became clear that there is a strong notion of trust involved in the design of integrated circuits in general and FPGA-based smart controllers in particular: the industry relies heavily on “IP” (Intellectual Property) cores.
 These are third-party functional units that are usually not transparent as to their inner workings, so the user must put complete trust in the provider.
 Furthermore the system design process is distributed over several different actors:

 The *utility* buys a new smart controller, typically requiring that it adheres to a number of international standards.
 They buy it as part of a system provided by a *systems integrator*. The systems integrator will decide on the architecture of the board, but typically subcontracts both the design of the board to a fabless design house and the manufacturing to a semiconductor fab.
 In the same way the systems integrator will also subcontract the design of the FPGA functionality, both hardware and software.
 In principle, any of the participants in the complete design process could attempt to insert malicious functionality in the system.
 In other words the trust put into each of the participants is very high.

 Insertion of malicious functionality means of course not adhering to the specification, in other words at some point in the chain some actor is *lying* about the functionality. As it is not possible to prevent lying, what we need to do is to mitigate the effect.
 The question is: how can we make sure that, when a functional unit is lying about its functionality, it will not do any damage to the entire system?

 So I thought, why don’t we use some of the most recent advances in theoretical computing science to make the design process a lot harder to subvert?
 Effectively, what we propose is that the architectural specification (i.e. the specification of all the blocks and their connections) is expressed through a formal mechanism that allows it to be entwined with the actual system design code.
 In this way, when using our proposed design flow it is simply not possible to design functionality that does not conform to the architectural specification.

 This approach mitigates agains insertion of unwanted functionality in new designs.
 However, what about IP cores? We cannot prevent the IP core provider from lying about the functionality – most likely they are not actively lying but simply unaware of the hidden functionality.
 But what we can do is demand that the IP core adheres to our formal specification, and crucially, we can check this when the chip is running.
 In this way, any attempt of any unit in the system to communicate with any other unit in a way that does not follow the formal specification will be caught, and no damage will be done.

 The beauty of this mechanism is that it also works agains intrusion: essentially, the Border Patrol units will limit what the intruder can do: any attempt to make the system behave against its specification will be intercepted.

 To achieve this goal a lot of work is required.
 The current type systems do not have all the functionality we need, so a lot of theoretical research work is required. Furthermore, we need to develop a formal specification language and a mechanism to translate formal specifications into types.
 Our type system needs to be integrated into the hardware design language so that designs can be checked.
 And we need to create the actual Border Patrol functionality that will check the communication at run time.

 Our work will focus on FPGA-based smart devices and we will work closely with Xilinx, one of the main FPGA vendors, to integrate our approach into their toolchain. We will also work closely with our other partners, EDF and ABB, on requirements capture and standardisation.

 This is a very exciting project and we believe that it will lead to greatly improved security of smart devices, and in fact to improved productivity and increased reliability in hardware design in general.
</div>
