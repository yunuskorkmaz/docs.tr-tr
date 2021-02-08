---
description: 'Daha fazla bilgi edinin: kalıcı olmayan Iş akışı örnekleri'
title: Kalıcı Olmayan İş Akışı Örnekleri
ms.date: 03/30/2017
ms.assetid: 5e01af77-6b14-4964-91a5-7dfd143449c0
ms.openlocfilehash: 0ee5968426a6bb800b9e70ac592c6da191c22511
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787909"
---
# <a name="non-persisted-workflow-instances"></a><span data-ttu-id="e016a-103">Kalıcı Olmayan İş Akışı Örnekleri</span><span class="sxs-lookup"><span data-stu-id="e016a-103">Non-Persisted Workflow Instances</span></span>

<span data-ttu-id="e016a-104">İçinde durumunu devam eden yeni bir iş akışı örneği oluşturulduğunda <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> , hizmet ana bilgisayarı örnek deposunda bu hizmet için bir giriş oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e016a-104">When a new instance of a workflow is created that persists its state in the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, the service host creates an entry for that service in the instance store.</span></span> <span data-ttu-id="e016a-105">Daha sonra, iş akışı örneği ilk kez kalıcı olduğunda, <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> geçerli örnek durumunu depolar.</span><span class="sxs-lookup"><span data-stu-id="e016a-105">Subsequently, when the workflow instance is persisted for the first time, the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> stores the current instance state.</span></span> <span data-ttu-id="e016a-106">İş akışı Windows Işlem etkinleştirme hizmetinde barındırılıyorsa, örnek ilk kez kalıcı olduğunda hizmet dağıtım verileri de örnek deposuna yazılır.</span><span class="sxs-lookup"><span data-stu-id="e016a-106">If the workflow is hosted in the Windows Process Activation Service, the service deployment data is also written to the instance store when the instance is persisted for the first time.</span></span>

<span data-ttu-id="e016a-107">İş akışı örneği kalıcı olmadığı sürece **kalıcı olmayan** bir durumda.</span><span class="sxs-lookup"><span data-stu-id="e016a-107">As long as the workflow instance has not been persisted, it is in a **non-persisted** state.</span></span> <span data-ttu-id="e016a-108">Bu durumda, bir uygulama etki alanı geri dönüştürme, ana bilgisayar arızası veya bilgisayar hatasından sonra iş akışı örneği kurtarılamaz.</span><span class="sxs-lookup"><span data-stu-id="e016a-108">While in this state, the workflow instance cannot be recovered after an application domain recycle, host failure, or computer failure.</span></span>

## <a name="the-non-persisted-state"></a><span data-ttu-id="e016a-109">Kalıcı olmayan durum</span><span class="sxs-lookup"><span data-stu-id="e016a-109">The Non-Persisted State</span></span>

<span data-ttu-id="e016a-110">Kalıcı olmayan dayanıklı iş akışı örnekleri aşağıdaki durumlarda kalıcı olmayan bir durumda kalır:</span><span class="sxs-lookup"><span data-stu-id="e016a-110">Durable workflow instances that have not been persisted remain in a non-persisted state in the following cases:</span></span>

- <span data-ttu-id="e016a-111">Hizmet ana bilgisayarı, iş akışı örneği ilk kez kalıcı hale gelmeden önce çöker.</span><span class="sxs-lookup"><span data-stu-id="e016a-111">The service host crashes before the workflow instance is persisted for the first time.</span></span> <span data-ttu-id="e016a-112">İş akışı örneği örnek deposunda kalır ve kurtarılmaz.</span><span class="sxs-lookup"><span data-stu-id="e016a-112">The workflow instance remains in the instance store and is not recovered.</span></span> <span data-ttu-id="e016a-113">Bağıntılı bir ileti alınırsa, iş akışı örneği tekrar etkin hale gelir.</span><span class="sxs-lookup"><span data-stu-id="e016a-113">If a correlated message arrives, the workflow instance becomes active again.</span></span>

- <span data-ttu-id="e016a-114">İş akışı örneği, ilk kez kalıcı hale gelmeden önce bir özel durum yaşanır.</span><span class="sxs-lookup"><span data-stu-id="e016a-114">The workflow instance experiences an exception before it is persisted for the first time.</span></span> <span data-ttu-id="e016a-115">Döndürülen öğesine bağlı olarak <xref:System.Activities.UnhandledExceptionAction> , aşağıdaki senaryolar oluşur:</span><span class="sxs-lookup"><span data-stu-id="e016a-115">Depending on the <xref:System.Activities.UnhandledExceptionAction> returned, the following scenarios occur:</span></span>

  - <span data-ttu-id="e016a-116"><xref:System.Activities.UnhandledExceptionAction> Şu şekilde ayarlanır <xref:System.Activities.UnhandledExceptionAction.Abort> : bir özel durum oluştuğunda, hizmet dağıtım bilgileri örnek deposuna yazılır ve iş akışı örneği bellekten kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="e016a-116"><xref:System.Activities.UnhandledExceptionAction> is set to <xref:System.Activities.UnhandledExceptionAction.Abort>: When an exception occurs, service deployment information is written to the instance store, and the workflow instance is unloaded from memory.</span></span> <span data-ttu-id="e016a-117">İş akışı örneği kalıcı olmayan bir durumda kalır ve yeniden yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="e016a-117">The workflow instance remains in a non-persisted state and cannot be reloaded.</span></span>

  - <span data-ttu-id="e016a-118"><xref:System.Activities.UnhandledExceptionAction> veya olarak ayarlanır <xref:System.Activities.UnhandledExceptionAction.Cancel> <xref:System.Activities.UnhandledExceptionAction.Terminate> : bir özel durum oluştuğunda, hizmet dağıtım bilgileri örnek deposuna yazılır ve etkinlik örneği durumu olarak ayarlanır <xref:System.Activities.ActivityInstanceState.Closed> .</span><span class="sxs-lookup"><span data-stu-id="e016a-118"><xref:System.Activities.UnhandledExceptionAction> is set to <xref:System.Activities.UnhandledExceptionAction.Cancel> or <xref:System.Activities.UnhandledExceptionAction.Terminate>: When an exception occurs, service deployment information is written to the instance store, and the activity instance state is set to <xref:System.Activities.ActivityInstanceState.Closed>.</span></span>

<span data-ttu-id="e016a-119">Kaldırılmış kalıcı olmayan iş akışı örneklerinin denenmesinin riskini en aza indirmek için iş akışının yaşam döngüsünün başlarında kalıcı olmasını öneririz.</span><span class="sxs-lookup"><span data-stu-id="e016a-119">To minimize the risk of encountering unloaded non-persisted workflow instances, we recommend persisting the workflow early in its life cycle.</span></span>

## <a name="detection-and-removal-of-non-persisted-instances"></a><span data-ttu-id="e016a-120">Kalıcı olmayan örneklerin algılanması ve kaldırılması</span><span class="sxs-lookup"><span data-stu-id="e016a-120">Detection and Removal of Non-Persisted Instances</span></span>

<span data-ttu-id="e016a-121">, <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> Hiçbir kalıcı olmayan iş akışı örneğini örnek deposundan kaldırmaz.</span><span class="sxs-lookup"><span data-stu-id="e016a-121">The <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> does not remove any non-persisted workflow instances from the instance store.</span></span> <span data-ttu-id="e016a-122">Ayrıca bunlarla ilişkili kalıcı olmayan iş akışı örneklerine sahip olan süre dolmayan kilit sahiplerini kaldırmaz.</span><span class="sxs-lookup"><span data-stu-id="e016a-122">It also does not remove any expired lock owners that have non-persisted workflow instances associated with them.</span></span>

<span data-ttu-id="e016a-123">Yöneticinin örnek deposunu kalıcı olmayan örnekler için düzenli olarak denetlemesini öneririz.</span><span class="sxs-lookup"><span data-stu-id="e016a-123">We recommend that the administrator periodically checks the instance store for non-persisted instances.</span></span> <span data-ttu-id="e016a-124">Yöneticiler, bu iş akışının bağıntılı iletileri almadıkları sürece bu örnekleri örnek deposundan kaldırabilir.</span><span class="sxs-lookup"><span data-stu-id="e016a-124">Administrators can remove those instances from the instance store as long as they know that this workflow will not receive correlated messages.</span></span> <span data-ttu-id="e016a-125">Örneğin, örnek veritabanında birkaç ay boyunca bulunuyorsa ve iş akışının genellikle birkaç güne sahip olduğu bilinmektedir, bu da kilitlenen başlatılmış bir örnek olduğunu varsaymak güvenli olacaktır.</span><span class="sxs-lookup"><span data-stu-id="e016a-125">For example, if the instance has been in the database for several months and it is known that the workflow typically has a lifetime of several days, it would be safe to assume that this was an initialized instance that had crashed.</span></span>

<span data-ttu-id="e016a-126">SQL Iş akışı örneği deposundaki kalıcı olmayan örnekleri bulmak için aşağıdaki SQL sorgularını kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e016a-126">To find non-persisted instances in the SQL Workflow Instance Store you can use the following SQL queries:</span></span>

- <span data-ttu-id="e016a-127">Bu sorgu kalıcı olmayan tüm örnekleri bulur ve bunlar için KIMLIK ve oluşturma saati (UTC saat olarak saklanır) döndürür.</span><span class="sxs-lookup"><span data-stu-id="e016a-127">This query finds all instances that have not been persisted, and returns the ID and creation time (stored in UTC time) for them.</span></span>

  ```sql
  select InstanceId, CreationTime
      from [System.Activities.DurableInstancing].[Instances]
      where IsInitialized = 0
  ```

- <span data-ttu-id="e016a-128">Bu sorgu kalıcı olmayan ve yüklenmeyen tüm örnekleri bulur ve bunlar için KIMLIK ve oluşturma saati (UTC saat olarak saklanır) döndürür.</span><span class="sxs-lookup"><span data-stu-id="e016a-128">This query finds all instances that have not been persisted, and that are not loaded, and returns the ID and creation time (stored in UTC time) for them.</span></span>

  ```sql
  select InstanceId, CreationTime
      from [System.Activities.DurableInstancing].[Instances]
      where IsInitialized = 0
          and CurrentMachine is NULL
  ```

- <span data-ttu-id="e016a-129">Bu sorgu kalıcı olmayan tüm askıya alınmış örnekleri bulur ve KIMLIK, oluşturma saati (UTC zaman içinde depolanan), askıya alma nedeni ve bunlar için özel durum adı döndürür.</span><span class="sxs-lookup"><span data-stu-id="e016a-129">This query finds all suspended instances that have not been persisted, and returns the ID, creation time (stored in UTC time), suspension reason, and exception name for them.</span></span>

  ```sql
  select InstanceId, CreationTime, SuspensionReason, SuspensionExceptionName
      from [System.Activities.DurableInstancing].[Instances]
      where IsInitialized = 0
          and IsSuspended = 1
  ```

<span data-ttu-id="e016a-130">Kalıcı olmayan örnekleri silerken dikkatli kullanın.</span><span class="sxs-lookup"><span data-stu-id="e016a-130">Use care when you are deleting non-persisted instances.</span></span> <span data-ttu-id="e016a-131">Genel olarak, tarafından oluşturulan veya yüklenmeyen kalıcı olmayan örneklerin kaldırılması güvenlidir <xref:System.ServiceModel.Activities.WorkflowServiceHost> .</span><span class="sxs-lookup"><span data-stu-id="e016a-131">In general, it is safe to remove non-persisted instances created by <xref:System.ServiceModel.Activities.WorkflowServiceHost> that are suspended or are not loaded.</span></span> <span data-ttu-id="e016a-132">Bu belirli örnekler, `[System.Activities.DurableInstancing].[Instances]` doğru örnek kimliği yerine, AŞAĞıDAKI SQL komutu kullanılarak görünümden silinerek depolamadan silinebilir.</span><span class="sxs-lookup"><span data-stu-id="e016a-132">Those specific instances can be deleted from the store by deleting them from the `[System.Activities.DurableInstancing].[Instances]` view by using the following SQL command, substituting the correct instance ID.</span></span>

```sql
delete [System.Activities.DurableInstancing].[Instances]
    where InstanceId=’078a9bc4-ada5-4f9e-8cce-b0eb0009995f’
```

> [!WARNING]
> <span data-ttu-id="e016a-133">Kalıcı olmayan tüm örnekleri kaldırmanızı önermeyiz çünkü bu, az önce oluşturulmuş ve henüz kalıcı olmayan örnekler içeriyor.</span><span class="sxs-lookup"><span data-stu-id="e016a-133">We do not recommend removing all non-persisted instances because this includes instances that have just been created and have not yet been persisted.</span></span>
