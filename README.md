# Energy-Tracker
Write automated tests that track energy usage over time.

## Philosophy
The Earth isn't doing great. More attention needs to be paid to software energy usage. Industrial coders rarely have the opportunity (much less the incentive) to put effort into finding a more energy efficient language or framework. It's about optimizing what you got. Energy Tracker is a free, low barrier tool that helps identify energy hogging code.

*If this isn't the right tool for you, please consider how else you can reduce your organization's impact on our Environment.*

## Methodology
Reliably measuring the energy consumption of a fragment of code is hard. There's more nuance here than we will cover, but it's often inaccurate because of...
* **variable hardware** - Software often runs on different harware with different efficiencies.
* **variable load** - The computational load of test machines may not be static.
* **simultaneous computation** - It's troublesome to isolate what processes used what amount of power.

A reasonable coder could assert that time complexity (Big O) is a suitable proxy for energy usage, but regrettably, that's not always the case. This [article](https://thenewstack.io/which-programming-languages-use-the-least-electricity/) is a good read on the subject.

What's more, many hardware components (processors included) do not report their actual energy usage. But let's say they did, we still couldn't apply that measurement to a specific piece of code. It would be system wide.

So let's look at the process specific power metrics we **do** have access to. **Top** is a harware monitoring utility that's installed by default on many machines and provides a process specific metric called **Time**. This is the total CPU time used by the process since it started, precise to the hundredths of a second. Measured on the same hardware, this metric should at least provide a trend as to how much energy a fragment of code is using. We will focus on the processor time for now as it is typically the most energy intensive hardware component.
