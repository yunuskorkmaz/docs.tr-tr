---
description: 'Şu konuda daha fazla bilgi edinin: nasıl yapılır: kalıcı olmayan örnekler için sorgulama'
title: 'Nasıl yapılır: Kalıcı Olmayan Örnekleri Sorgulama'
ms.date: 03/30/2017
ms.assetid: 294019b1-c1a7-4b81-a14f-b47c106cd723
ms.openlocfilehash: 2cef64f97b32c5f1d31fa078200bc2fe15179485
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99777664"
---
# <a name="how-to-query-for-non-persisted-instances"></a><span data-ttu-id="70d0e-103">Nasıl yapılır: Kalıcı Olmayan Örnekleri Sorgulama</span><span class="sxs-lookup"><span data-stu-id="70d0e-103">How to: Query for Non-persisted Instances</span></span>

<span data-ttu-id="70d0e-104">Bir hizmetin yeni bir örneği oluşturulduğunda ve hizmet SQL Iş akışı örnek deposu davranışını tanımlıysa, hizmet ana bilgisayarı örnek deposundaki bu hizmet örneği için bir başlangıç girişi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="70d0e-104">When a new instance of a service is created and the service has the SQL Workflow Instance Store behavior defined, the service host creates a initial entry for that service instance in the instance store.</span></span> <span data-ttu-id="70d0e-105">Daha sonra hizmet örneği ilk kez devam ederse, SQL Iş akışı örnek deposu davranışı, geçerli örnek durumunu etkinleştirme, kurtarma ve denetim için gereken ek verilerle birlikte depolar.</span><span class="sxs-lookup"><span data-stu-id="70d0e-105">Subsequently when the service instance persists for the first time, the SQL Workflow Instance Store behavior stores the current instance state together with additional data that is required for activation, recovery, and control.</span></span>

<span data-ttu-id="70d0e-106">Örnek için ilk giriş oluşturulduktan sonra bir örnek kalıcı değilse, hizmet örneği kalıcı olmayan durumda olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="70d0e-106">If an instance is not persisted after the initial entry for the instance is created, the service instance is said to be in the non-persisted state.</span></span> <span data-ttu-id="70d0e-107">Tüm kalıcı hizmet örnekleri sorgulanabilir ve denetlenebilir.</span><span class="sxs-lookup"><span data-stu-id="70d0e-107">All the persisted service instances can be queried and controlled.</span></span> <span data-ttu-id="70d0e-108">Kalıcı olmayan hizmet örnekleri, hiçbir şekilde sorgulanamaz ve denetlenemez.</span><span class="sxs-lookup"><span data-stu-id="70d0e-108">Non-persisted service instances can neither be queried nor controlled.</span></span> <span data-ttu-id="70d0e-109">Kalıcı olmayan bir örnek işlenmeyen bir özel durum nedeniyle askıya alınırsa, sorgulanabilir ancak denetlenemez.</span><span class="sxs-lookup"><span data-stu-id="70d0e-109">If a non-persisted instance is suspended due to an unhandled exception it can be queried but not controlled.</span></span>

<span data-ttu-id="70d0e-110">Henüz kalıcı olmayan dayanıklı hizmet örnekleri, aşağıdaki senaryolarda kalıcı olmayan bir durumda kalır:</span><span class="sxs-lookup"><span data-stu-id="70d0e-110">Durable service instances that are not yet persisted remain in a non-persisted state in the following scenarios:</span></span>

- <span data-ttu-id="70d0e-111">Hizmet ana bilgisayarı, örnek ilk kez kalıcı hale gelmeden önce kilitleniyor.</span><span class="sxs-lookup"><span data-stu-id="70d0e-111">The service host crashes before the instance persisted for the first time.</span></span> <span data-ttu-id="70d0e-112">Örnek için başlangıç girdisi örnek deposunda kalır.</span><span class="sxs-lookup"><span data-stu-id="70d0e-112">The initial entry for the instance remains in the instance store.</span></span> <span data-ttu-id="70d0e-113">Örnek kurtarılabilir değil.</span><span class="sxs-lookup"><span data-stu-id="70d0e-113">The instance is not recoverable.</span></span> <span data-ttu-id="70d0e-114">Bağıntılı bir ileti alınırsa, örnek tekrar etkin hale gelir.</span><span class="sxs-lookup"><span data-stu-id="70d0e-114">If a correlated message arrives, the instance becomes active again.</span></span>

- <span data-ttu-id="70d0e-115">Örnek, ilk kez kalıcı yapmadan önce işlenmemiş bir özel durumla karşılaşır.</span><span class="sxs-lookup"><span data-stu-id="70d0e-115">The instance experiences an unhandled exception before it persisted for the first time.</span></span> <span data-ttu-id="70d0e-116">Aşağıdaki senaryolar ortaya çıkar</span><span class="sxs-lookup"><span data-stu-id="70d0e-116">The following scenarios arise</span></span>

  - <span data-ttu-id="70d0e-117">**UnhandledExceptionAction** özelliğinin değeri **Abandon** olarak ayarlandıysa, hizmet dağıtım bilgileri örnek deposuna yazılır ve örnek bellekten kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="70d0e-117">If the value of the **UnhandledExceptionAction** property is set to **Abandon**, the service deployment information is written to the instance store and the instance is unloaded from memory.</span></span> <span data-ttu-id="70d0e-118">Örnek, kalıcılık veritabanında kalıcı olmayan durumda kalır.</span><span class="sxs-lookup"><span data-stu-id="70d0e-118">The instance remains in non-persisted state in the persistence database.</span></span>

  - <span data-ttu-id="70d0e-119">**UnhandledExceptionAction** özelliğinin değeri, **Andsusbekleto bırakma** olarak ayarlandıysa, hizmet dağıtım bilgileri kalıcılık veritabanına yazılır ve örnek durumu **askıya alındı** olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="70d0e-119">If the value of the **UnhandledExceptionAction** property is set to **AbandonAndSuspend**, the service deployment information is written to the persistence database and the instance state is set to **Suspended**.</span></span> <span data-ttu-id="70d0e-120">Örnek devam ettirilemez, iptal edilemez veya sonlandırılamıyor.</span><span class="sxs-lookup"><span data-stu-id="70d0e-120">The instance cannot be resumed, canceled, or terminated.</span></span> <span data-ttu-id="70d0e-121">Örnek henüz kalıcı olmadığı için hizmet ana bilgisayarı örneği yükleyemiyor, bu nedenle örnek için veritabanı girişi tamamlanmadı.</span><span class="sxs-lookup"><span data-stu-id="70d0e-121">The service host cannot load the instance because the instance hasn't persisted yet and, hence the database entry for the instance is not complete.</span></span>

  - <span data-ttu-id="70d0e-122">**UnhandledExceptionAction** özelliğinin değeri **Cancel** veya **Terminate** olarak ayarlandıysa, hizmet dağıtım bilgileri örnek deposuna yazılır ve örnek durumu **tamamlandı** olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="70d0e-122">If the value of the **UnhandledExceptionAction** property is set to **Cancel** or **Terminate**, the service deployment information is written to the instance store and the instance state is set to **Completed**.</span></span>

<span data-ttu-id="70d0e-123">Aşağıdaki bölümlerde, SQL kalıcılık veritabanında kalıcı olmayan örnekleri bulacak ve bu örnekleri veritabanından silecek örnek sorgular sağlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="70d0e-123">The following sections provide sample queries to find non-persisted instances in the SQL persistence database and to delete these instances from the database.</span></span>

## <a name="to-find-all-instances-not-persisted-yet"></a><span data-ttu-id="70d0e-124">Henüz kalıcı olmayan tüm örnekleri bulmak için</span><span class="sxs-lookup"><span data-stu-id="70d0e-124">To find all instances not persisted yet</span></span>

<span data-ttu-id="70d0e-125">Aşağıdaki SQL sorgusu, kalıcılık veritabanında kalıcı olmayan tüm örneklerin KIMLIĞINI ve oluşturulma zamanını döndürür.</span><span class="sxs-lookup"><span data-stu-id="70d0e-125">The following SQL query returns the ID and creation time for all instances that are not persisted in to the persistence database yet.</span></span>

```sql
select InstanceId, CreationTime from [System.Activities.DurableInstancing].[Instances] where IsInitialized = 0;
```

## <a name="to-find-all-instances-not-persisted-yet-and-also-not-loaded"></a><span data-ttu-id="70d0e-126">Henüz kalıcı olmayan ve yüklenmeyen tüm örnekleri bulmak için</span><span class="sxs-lookup"><span data-stu-id="70d0e-126">To find all instances not persisted yet and also not loaded</span></span>

 <span data-ttu-id="70d0e-127">Aşağıdaki SQL sorgusu, kalıcı olmayan ve ayrıca yüklenmeyen tüm örnekler için KIMLIK ve oluşturma saati döndürür.</span><span class="sxs-lookup"><span data-stu-id="70d0e-127">The following SQL query returns ID and creation time for all instances that are not persisted and also are not loaded.</span></span>

```sql
select InstanceId, CreationTime from [System.Activities.DurableInstancing].[Instances] where IsInitialized = 0 and CurrentMachine is NULL;
```

## <a name="to-find-all-suspended-instances-not-persisted-yet"></a><span data-ttu-id="70d0e-128">Henüz kalıcı olmayan tüm askıya alınmış örnekleri bulmak için</span><span class="sxs-lookup"><span data-stu-id="70d0e-128">To find all suspended instances not persisted yet</span></span>

<span data-ttu-id="70d0e-129">Aşağıdaki SQL sorgusu, kalıcı olmayan ve ayrıca askıya alınmış durumda olan tüm örnekler için KIMLIK, oluşturma saati, askıya alma nedeni ve askıya alma özel durum adını döndürür.</span><span class="sxs-lookup"><span data-stu-id="70d0e-129">The following SQL query returns ID, creation time, suspension reason, and suspension exception name for all instances that are not persisted and also in a suspended state.</span></span>

```sql
select InstanceId, CreationTime, SuspensionReason, SuspensionExceptionName from [System.Activities.DurableInstancing].[Instances] where IsInitialized = 0 and IsSuspended = 1;
```

## <a name="to-delete-non-persisted-instances-from-the-persistence-database"></a><span data-ttu-id="70d0e-130">Kalıcı olmayan örnekleri kalıcılık veritabanından silmek için</span><span class="sxs-lookup"><span data-stu-id="70d0e-130">To delete non-persisted instances from the persistence database</span></span>

<span data-ttu-id="70d0e-131">Örnek depolama alanını kalıcı olmayan örnekler için düzenli olarak denetlemeniz ve örneğin bağıntılı bir ileti almadığınızdan emin olmanız durumunda örnek deposundan örnekleri kaldırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="70d0e-131">You should periodically check the instance store for non-persisted instances and remove instances from the instance store if you are sure that the instance will not receive a correlated message.</span></span> <span data-ttu-id="70d0e-132">Örneğin, örnek veritabanında birkaç ay boyunca bulunuyorsa ve iş akışının genellikle birkaç günün ömrü olduğunu biliyorsanız, bu, kilitlenen başlatılmamış bir örnek olduğunu varsaymak güvenli olacaktır.</span><span class="sxs-lookup"><span data-stu-id="70d0e-132">For example, if the instance has been in the database for several months and you know that the workflow typically has a lifetime of a few days, it would be safe to assume that this is an uninitialized instance that had crashed.</span></span>

<span data-ttu-id="70d0e-133">Genel olarak, askıya alınmamış veya yüklenmeyen kalıcı olmayan örnekleri silmek güvenlidir.</span><span class="sxs-lookup"><span data-stu-id="70d0e-133">In general, it is safe to delete non-persisted instances that are not suspended or not loaded.</span></span> <span data-ttu-id="70d0e-134">Bu örnek kümesi yeni oluşturulan ancak henüz kalıcı olmayan örnekleri içerdiğinden, kalıcı olmayan **Tüm** örnekleri silmemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="70d0e-134">You should not delete **all** the non-persisted instances because this instance set includes instances that are just created but are not persisted yet.</span></span> <span data-ttu-id="70d0e-135">Yalnızca yüklü olan kalıcı olmayan örnekleri silmeniz gerekir, çünkü yüklenen örnek olan iş akışı hizmeti ana bilgisayarı bir özel duruma neden oldu veya örnek bir özel duruma neden oldu.</span><span class="sxs-lookup"><span data-stu-id="70d0e-135">You should only delete non-persisted instances that are left over because the workflow service host that had the instance loaded caused an exception or the instance itself caused an exception.</span></span>

> [!WARNING]
> <span data-ttu-id="70d0e-136">Örnek deposundan kalıcı olmayan örneklerin silinmesi deponun boyutunu düşürür ve mağaza işlemlerinin performansını iyileştirebilir.</span><span class="sxs-lookup"><span data-stu-id="70d0e-136">Deleting non-persisted instances from the instance store decreases the size of the store and may improve the performance of store operations.</span></span>
