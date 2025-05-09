# Reliability

In short, the application should be working correctly at the desired performance even if it is facing **adversity (\*1)**.

Some points then can be inlcuded in order to think about a system as a reliable:

- Application can perform the function that users expect.
- It can tolerate the user made mistakes or using the software in unexpected ways.
- Its performance is good enough for the required use case, under the expected data volume and load.
- The system prevents any unauthorized access and abuse.

Things that can go wrong in a software world are called fault.
Systems that can deal with those faults are called fault-tolerant or resilient (even tho the author do not like to call such systems resilient. (imagine a black hole right next to your Data Centers))

Fault does not equal to failure.

Fault is usually defined as one component of the system **deviating (\*2)** from its specification.
Failure is when the system as a whole stops providing the required service to the user/client.

#### Netflix Chaos Monkey (TODO: learn about similar toolings, and history of development of such tools.)

Is an internal tool developed by Netflix which randomly causes failures in the prod env during BUSINESS HOURS (xD)
It is randomly turning off VM's, sending corrupted packages to see how the system will response to that (in that way its collecting response and as I understand they are collecting some metrics.)

Because author mentioned that he mainly discuss cases which should prevent unrevertable (uncurable) things like CPI (customer personal information) leaks, here are a set of books which may bring light on topics what to do when those unrevertable things happened:

1. Cybersecurity Incident Response - A lot of stuff like how to behave/react when shit things happened.
2. Disaster Recovery (DR) and Business Continuity (BC) - Broader than the first book this one not just about security but rather how to revert systems back online.
3. Digital Forensics - This books delve into investigating what happened during a security incident, collecting evidence etc.
4. Data Breach Management - More specific books which focus on the legal regulatory (GDPR or other data protection laws), communication, and customer notification aspects that are mandatory after a data leak.

#### Common fault reasons:

1. Hardware faults
2. Software errors
3. Human errors

## Hardware faults:

Today hardware issues are a rare issues since a lot of people using Cloud Providers.
But still there is often situation when a worker can unplug a power cable and similar things.
For such scenarios hardware or rather the data should be replicated (not only this solution but for ex the HDDs can work in RAID mode) and so there are a lot of techniques which prevents or decrease the downtime of the systerms due to hardware faults.

## Software errors:

This is a more common reason of faults and failures.
There is no quick solution to this problem.

But a lot of things can help to prevent a lot of software errors:

- Carefully think about assumptions and interactions between the systems and inside the app.
- Thorough testing
- Proces isolation
- Allowing processes to crash and restart
- Measuring, monitoring, analyzing system behavior in PROD.

## Human errors:

Humans even with good intentions are known to be unreliable.

How can we make our systems reliable in **spite (\*3)** of unreliable humans?

Things we can do:

- Making our systems in a way to minimize opportunities for error. Writing adapters, well designed abstractions and APIs, making it easy to do the "right thing". Even tho all these should be balanced because in case of rough flexibility people will tend to write workarounds.
- Decouple the places where peoples can make most mistakes from places where those issues can lead to failures. (also have staging and test environemnts)
- Testing at ALL levels.
- Allowing quick and easy recovery from human errors. (make it fast to roll back configuration changes, rolling deployments)
- Detailed and clear monitoring of system components and general situation.
- Implement good management practices and TRAINING. beyond the scope of this book.

## Terms:

1. **Adversity** - In the context above it refers to difficulties, challenges, or unfavourable conditions that the application might encounter.
2. **Deviation** - In the context above it means departure or misfunction from the standart which is considered normal/acceptable.
3. **In spite of/Despite** - Such phrases means that (with the context above): Regardless of the unreliable humans... (so regardless of some reason ....)
