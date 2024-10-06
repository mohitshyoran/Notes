## 1. Selective Amendment
### OverviewAn web application, user can register and can start from creating a draft proposal, add sites, add products.
Quatation will be given and after validation of data and some sort of approval from both the sides it will be signed and wil be converted in a agreement.
Now to do any modification in agrement replace/delete/add/modify previosly a process was there.
which will copy complete data, do modification and merge, which is called full agreement.
This was coping unneccesarily all the data even if it was not needed, hence increasing time complexity of all the process througout the flow.
Hence selective amendment came in picture, now instead of copying data of all the sites, just copy sites on which modification will be done.
do the changes and merge then. hence less data will be processed and process will be faster.

### Challenges-
* Since many flows were uncovered in past from a long time after creation so product also missed few of the scenerios, which i got to know througout the process of development and while discussing with all the stakeholders.
* And I was new to the system and this was touching all the major services, some of them were out of my teams scope, so had to learn about them as well.
* Lot of ambiguity for me because for some cases it was left to developer to understand system behaviour and do things accordingly.

### Action-
* Figured out most of the thing myself and kept all the owners in loop that i am doing these changes, Found many gaps in the system as well.
* Connected to service owners to understand the working of service, review the changes, if it can break anything. 
* Connected with product and architect wherever I suspected gaps to get confirmation from them.
* Some time where I could not connect with some one, I raised this to my manager and got some time scheduled with them.

### Result-
* I was able to deliver it with slight delay.
* Boosted my confidence.
* Good boding with other team members.
* High level understanding of all major service which later helped me solving in production bugs.

## 2. One Identity
EG is group of brands, previously diffent identity on diffent stack for every brand.
Company wanted to have a unfied identity across all the brands so that can give common feature like reward points.

Design was done and implementation was just started.
I got chance to work on it.

Challenges:
* Multiple brands(diff working of old stack), two type of accounts, and different kind  of login mechanism(password, opt, social) -> So many combinations of scenerios and using common code.
* Maintain data in sync in old stack(foreward sync) and in new system as well(Backward sync)

Action: 
* With learning kotlin and onboarding I quickly made a good understaing of business.
* which helped me to contribute in more better way, for which later i got appreciation as well from my seniot team members.

Result:
* Boosted confidence, and contributed in successful delivry within timelines.

## 3. lock-unlock capability
* High level design
* UniverasalAuthenticationService -> UniversalCredentitalService.
* According to requirement -> lastFailedTime and failedAttempts.
