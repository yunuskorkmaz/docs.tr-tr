---
title: "Kalıcı olmayan iş akışı örnekleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5e01af77-6b14-4964-91a5-7dfd143449c0
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 54ed92ee666a55b52db22abbbe46922189b3f8fb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="non-persisted-workflow-instances"></a><span data-ttu-id="74db9-102">Kalıcı olmayan iş akışı örnekleri</span><span class="sxs-lookup"><span data-stu-id="74db9-102">Non-Persisted Workflow Instances</span></span>
<span data-ttu-id="74db9-103">Bir iş akışı yeni bir örneğini oluşturulduğunda durumundayken kalıcı <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, hizmet ana bilgisayarı örnek deposunda bu hizmet için bir giriş oluşturur.</span><span class="sxs-lookup"><span data-stu-id="74db9-103">When a new instance of a workflow is created that persists its state in the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, the service host creates an entry for that service in the instance store.</span></span> <span data-ttu-id="74db9-104">Sonuç olarak, ne zaman iş akışı örneği kalıcıdır ilk kez <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> geçerli örnek durum depolar.</span><span class="sxs-lookup"><span data-stu-id="74db9-104">Subsequently, when the workflow instance is persisted for the first time, the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> stores the current instance state.</span></span> <span data-ttu-id="74db9-105">İş akışı Windows İşlem Etkinleştirme hizmeti barındırılıyorsa örneği ilk kez kalıcı veri hizmeti dağıtımı da örnek deposuna yazılır.</span><span class="sxs-lookup"><span data-stu-id="74db9-105">If the workflow is hosted in the Windows Process Activation Service, the service deployment data is also written to the instance store when the instance is persisted for the first time.</span></span>  
  
 <span data-ttu-id="74db9-106">İş akışı örneği kalıcı olmayan sürece olan bir **kalıcı olmayan** durumu.</span><span class="sxs-lookup"><span data-stu-id="74db9-106">As long as the workflow instance has not been persisted, it is in a **non-persisted** state.</span></span> <span data-ttu-id="74db9-107">Bu durumundayken, iş akışı örneği bir uygulama etki alanı geri dönüşümü, ana bilgisayar hatası veya bilgisayar hatasından sonra kurtarılamaz.</span><span class="sxs-lookup"><span data-stu-id="74db9-107">While in this state, the workflow instance cannot be recovered after an application domain recycle, host failure, or computer failure.</span></span>  
  
## <a name="the-non-persisted-state"></a><span data-ttu-id="74db9-108">Kalıcı olmayan durumu</span><span class="sxs-lookup"><span data-stu-id="74db9-108">The Non-Persisted State</span></span>  
 <span data-ttu-id="74db9-109">Aşağıdaki durumlarda kalıcı olmayan bir durumda değil kalıcı dayanıklı iş akışı örnekleri kalır:</span><span class="sxs-lookup"><span data-stu-id="74db9-109">Durable workflow instances that have not been persisted remain in a non-persisted state in the following cases:</span></span>  
  
-   <span data-ttu-id="74db9-110">İş akışı örneği ilk kez kalıcı önce Hizmet Konağı çöküyor.</span><span class="sxs-lookup"><span data-stu-id="74db9-110">The service host crashes before the workflow instance is persisted for the first time.</span></span> <span data-ttu-id="74db9-111">İş akışı örneği örnek deposunda kalır ve kurtarılmamış.</span><span class="sxs-lookup"><span data-stu-id="74db9-111">The workflow instance remains in the instance store and is not recovered.</span></span> <span data-ttu-id="74db9-112">Bağlantılı bir ileti alınırsa, iş akışı örneği yeniden etkin hale gelir.</span><span class="sxs-lookup"><span data-stu-id="74db9-112">If a correlated message arrives, the workflow instance becomes active again.</span></span>  
  
-   <span data-ttu-id="74db9-113">İlk kez kalıcı önce iş akışı örneği bir özel durum karşılaşır.</span><span class="sxs-lookup"><span data-stu-id="74db9-113">The workflow instance experiences an exception before it is persisted for the first time.</span></span> <span data-ttu-id="74db9-114">Bağlı olarak <xref:System.Activities.UnhandledExceptionAction> döndürülen, aşağıdaki senaryolarda oluşur:</span><span class="sxs-lookup"><span data-stu-id="74db9-114">Depending on the <xref:System.Activities.UnhandledExceptionAction> returned, the following scenarios occur:</span></span>  
  
    -   <span data-ttu-id="74db9-115"><xref:System.Activities.UnhandledExceptionAction>ayarlanmış <xref:System.Activities.UnhandledExceptionAction.Abort>: bir özel durum oluştu, hizmet dağıtım bilgileri için örnek deposuna yazılır ve iş akışı örneği bellekten olduğunda.</span><span class="sxs-lookup"><span data-stu-id="74db9-115"><xref:System.Activities.UnhandledExceptionAction> is set to <xref:System.Activities.UnhandledExceptionAction.Abort>: When an exception occurs, service deployment information is written to the instance store, and the workflow instance is unloaded from memory.</span></span> <span data-ttu-id="74db9-116">İş akışı örneği kalıcı olmayan bir durumda kalır ve yeniden yüklenemiyor.</span><span class="sxs-lookup"><span data-stu-id="74db9-116">The workflow instance remains in a non-persisted state and cannot be reloaded.</span></span>  
  
    -   <span data-ttu-id="74db9-117"><xref:System.Activities.UnhandledExceptionAction>ayarlanmış <xref:System.Activities.UnhandledExceptionAction.Cancel> veya <xref:System.Activities.UnhandledExceptionAction.Terminate>: bir özel durum oluştu, hizmet dağıtım bilgileri için örnek deposuna yazılır ve etkinlik örnek durum kümesine <xref:System.Activities.ActivityInstanceState.Closed>.</span><span class="sxs-lookup"><span data-stu-id="74db9-117"><xref:System.Activities.UnhandledExceptionAction> is set to <xref:System.Activities.UnhandledExceptionAction.Cancel> or <xref:System.Activities.UnhandledExceptionAction.Terminate>: When an exception occurs, service deployment information is written to the instance store, and the activity instance state is set to <xref:System.Activities.ActivityInstanceState.Closed>.</span></span>  
  
 <span data-ttu-id="74db9-118">Kalıcı olmayan bellekten iş akışı örnekleri karşılaşmadan riskini en aza indirmek için erken yaşam döngüsü iş akışını sürdürmek öneririz.</span><span class="sxs-lookup"><span data-stu-id="74db9-118">To minimize the risk of encountering unloaded non-persisted workflow instances, we recommend persisting the workflow early in its life cycle.</span></span>  
  
## <a name="detection-and-removal-of-non-persisted-instances"></a><span data-ttu-id="74db9-119">Algılama ve temizleme kalıcı olmayan örnekleri</span><span class="sxs-lookup"><span data-stu-id="74db9-119">Detection and Removal of Non-Persisted Instances</span></span>  
 <span data-ttu-id="74db9-120"><xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> Hiç kalıcı olmayan iş akışı örneği örnek deposundan kaldırmaz.</span><span class="sxs-lookup"><span data-stu-id="74db9-120">The <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> does not remove any non-persisted workflow instances from the instance store.</span></span> <span data-ttu-id="74db9-121">Kalıcı olmayan iş akışı örneği ilişkili tüm süresi dolan kilit sahiplerinin ayrıca kaldırmaz.</span><span class="sxs-lookup"><span data-stu-id="74db9-121">It also does not remove any expired lock owners that have non-persisted workflow instances associated with them.</span></span>  
  
 <span data-ttu-id="74db9-122">Yönetici kalıcı olmayan örnekleri için örnek deposuna düzenli olarak denetler öneririz.</span><span class="sxs-lookup"><span data-stu-id="74db9-122">We recommend that the administrator periodically checks the instance store for non-persisted instances.</span></span> <span data-ttu-id="74db9-123">Yöneticiler bu iş akışı bağıntılı iletileri almaz bilmeniz sürece bu örneklerde örneği Mağazası'ndan kaldırabilir.</span><span class="sxs-lookup"><span data-stu-id="74db9-123">Administrators can remove those instances from the instance store as long as they know that this workflow will not receive correlated messages.</span></span> <span data-ttu-id="74db9-124">Örneğin, örnek veritabanında birkaç ay olmuştur ve iş akışı genellikle birkaç gün ömrü olduğunu biliniyorsa ise, onu bu çöken örneği başlatılmış olduğunu varsaymak güvenli olabilir.</span><span class="sxs-lookup"><span data-stu-id="74db9-124">For example, if the instance has been in the database for several months and it is known that the workflow typically has a lifetime of several days, it would be safe to assume that this was an initialized instance that had crashed.</span></span>  
  
 <span data-ttu-id="74db9-125">SQL iş akışı örneği Mağazası'nda kalıcı olmayan örneklerini bulmak için aşağıdaki SQL sorgularını kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="74db9-125">To find non-persisted instances in the SQL Workflow Instance Store you can use the following SQL queries:</span></span>  
  
-   <span data-ttu-id="74db9-126">Bu sorgu kalıcı ve (UTC saatiyle depolanır) kimliği ve oluşturulması zaman bunları döndüren tüm örneklerini bulur.</span><span class="sxs-lookup"><span data-stu-id="74db9-126">This query finds all instances that have not been persisted, and returns the ID and creation time (stored in UTC time) for them.</span></span>  
  
    ```sql  
    select InstanceId, CreationTime   
        from [System.Activities.DurableInstancing].[Instances]   
        where IsInitialized = 0  
    ```  
  
-   <span data-ttu-id="74db9-127">Bu sorgu, değil devam ediyor ve yüklü değil ve (UTC saatiyle depolanır) kimliği ve oluşturulması zaman bunları döndürür tüm örneklerini bulur.</span><span class="sxs-lookup"><span data-stu-id="74db9-127">This query finds all instances that have not been persisted, and that are not loaded, and returns the ID and creation time (stored in UTC time) for them.</span></span>  
  
    ```sql  
    select InstanceId, CreationTime   
        from [System.Activities.DurableInstancing].[Instances]   
        where IsInitialized = 0   
            and CurrentMachine is NULL  
    ```  
  
-   <span data-ttu-id="74db9-128">Bu sorgu kalıcı ve döndüren kimliği, oluşturma zamanı (UTC saatiyle depolanır), askıya alınmış tüm örneklerini bulur askıya neden ve bunlar için özel durum adı.</span><span class="sxs-lookup"><span data-stu-id="74db9-128">This query finds all suspended instances that have not been persisted, and returns the ID, creation time (stored in UTC time), suspension reason, and exception name for them.</span></span>  
  
    ```sql  
    select InstanceId, CreationTime, SuspensionReason, SuspensionExceptionName   
        from [System.Activities.DurableInstancing].[Instances]   
        where IsInitialized = 0   
            and IsSuspended = 1  
    ```  
  
 <span data-ttu-id="74db9-129">Kalıcı olmayan örnekleri silerken dikkatli olun.</span><span class="sxs-lookup"><span data-stu-id="74db9-129">Use care when you are deleting non-persisted instances.</span></span> <span data-ttu-id="74db9-130">Genel olarak, kalıcı olmayan örnekleri tarafından oluşturulan kaldırmak güvenli <xref:System.ServiceModel.Activities.WorkflowServiceHost> , askıya alınmış durumda veya yüklü değil.</span><span class="sxs-lookup"><span data-stu-id="74db9-130">In general, it is safe to remove non-persisted instances created by <xref:System.ServiceModel.Activities.WorkflowServiceHost> that are suspended or are not loaded.</span></span> <span data-ttu-id="74db9-131">Bu belirli örnekleri onlardan silerek depolama alanından silinebilir `[System.Activities.DurableInstancing].[Instances]` doğru örneği kimlik değiştirerek aşağıdaki SQL komutunu kullanarak görünümü</span><span class="sxs-lookup"><span data-stu-id="74db9-131">Those specific instances can be deleted from the store by deleting them from the `[System.Activities.DurableInstancing].[Instances]` view by using the following SQL command, substituting the correct instance ID.</span></span>  
  
```sql  
delete [System.Activities.DurableInstancing].[Instances]   
    where InstanceId=’078a9bc4-ada5-4f9e-8cce-b0eb0009995f’  
```  
  
> [!WARNING]
>  <span data-ttu-id="74db9-132">Bu yeni oluşturduğunuz ve henüz kalıcı örnekleri içerdiğinden kalıcı olmayan tüm örneklerini kaldırma önermiyoruz.</span><span class="sxs-lookup"><span data-stu-id="74db9-132">We do not recommend removing all non-persisted instances because this includes instances that have just been created and have not yet been persisted.</span></span>
