---
title: Kalıcı Olmayan İş Akışı Örnekleri
ms.date: 03/30/2017
ms.assetid: 5e01af77-6b14-4964-91a5-7dfd143449c0
ms.openlocfilehash: 410451f0dfeb91111e77634245aa786c4afc5b04
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61644271"
---
# <a name="non-persisted-workflow-instances"></a><span data-ttu-id="23e7e-102">Kalıcı Olmayan İş Akışı Örnekleri</span><span class="sxs-lookup"><span data-stu-id="23e7e-102">Non-Persisted Workflow Instances</span></span>
<span data-ttu-id="23e7e-103">Bir iş akışının yeni bir örneği oluşturulduğunda, durumunda kalıcı <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, hizmet ana bilgisayarı örnek deposunda bu hizmet için bir giriş oluşturur.</span><span class="sxs-lookup"><span data-stu-id="23e7e-103">When a new instance of a workflow is created that persists its state in the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, the service host creates an entry for that service in the instance store.</span></span> <span data-ttu-id="23e7e-104">Sonuç olarak, ne zaman iş akışı örneği kalıcıdır ilk kez <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> geçerli örneğin durumunu depolar.</span><span class="sxs-lookup"><span data-stu-id="23e7e-104">Subsequently, when the workflow instance is persisted for the first time, the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> stores the current instance state.</span></span> <span data-ttu-id="23e7e-105">İş akışı Windows İşlem Etkinleştirme hizmetinde barındırılıyorsa, bu ilk kez örneği kalıcıdır hizmet dağıtım verileri de örnek deposuna yazılır.</span><span class="sxs-lookup"><span data-stu-id="23e7e-105">If the workflow is hosted in the Windows Process Activation Service, the service deployment data is also written to the instance store when the instance is persisted for the first time.</span></span>  
  
 <span data-ttu-id="23e7e-106">İş akışı örneği kalıcı değil sürece olduğu bir **kalıcı olmayan** durumu.</span><span class="sxs-lookup"><span data-stu-id="23e7e-106">As long as the workflow instance has not been persisted, it is in a **non-persisted** state.</span></span> <span data-ttu-id="23e7e-107">Bu durumdayken, iş akışı örneği bir uygulama etki alanı geri dönüşümü, ana bilgisayar hatası veya bilgisayar hatasından sonra kurtarılamaz.</span><span class="sxs-lookup"><span data-stu-id="23e7e-107">While in this state, the workflow instance cannot be recovered after an application domain recycle, host failure, or computer failure.</span></span>  
  
## <a name="the-non-persisted-state"></a><span data-ttu-id="23e7e-108">Kalıcı olmayan durumu</span><span class="sxs-lookup"><span data-stu-id="23e7e-108">The Non-Persisted State</span></span>  
 <span data-ttu-id="23e7e-109">Kalıcı dayanıklı iş akışı örnekleri aşağıdaki durumlarda kalıcı olmayan bir durumda kalır:</span><span class="sxs-lookup"><span data-stu-id="23e7e-109">Durable workflow instances that have not been persisted remain in a non-persisted state in the following cases:</span></span>  
  
- <span data-ttu-id="23e7e-110">İlk kez iş akışı örneği kalıcıdır önce hizmet ana bilgisayarı kilitleniyor.</span><span class="sxs-lookup"><span data-stu-id="23e7e-110">The service host crashes before the workflow instance is persisted for the first time.</span></span> <span data-ttu-id="23e7e-111">İş akışı örneği, örnek deposunda kalır ve kurtarılmamış.</span><span class="sxs-lookup"><span data-stu-id="23e7e-111">The workflow instance remains in the instance store and is not recovered.</span></span> <span data-ttu-id="23e7e-112">İlişkili bir ileti geldiğinde, iş akışı örneği tekrar etkin hale gelir.</span><span class="sxs-lookup"><span data-stu-id="23e7e-112">If a correlated message arrives, the workflow instance becomes active again.</span></span>  
  
- <span data-ttu-id="23e7e-113">İş akışı örneği bir özel durum karşılaştığında, önce ilk kez kalıcı hale getirilir.</span><span class="sxs-lookup"><span data-stu-id="23e7e-113">The workflow instance experiences an exception before it is persisted for the first time.</span></span> <span data-ttu-id="23e7e-114">Yapılandırmanıza bağlı olarak <xref:System.Activities.UnhandledExceptionAction> döndürülen, aşağıdaki senaryolarda oluşur:</span><span class="sxs-lookup"><span data-stu-id="23e7e-114">Depending on the <xref:System.Activities.UnhandledExceptionAction> returned, the following scenarios occur:</span></span>  
  
    - <span data-ttu-id="23e7e-115"><xref:System.Activities.UnhandledExceptionAction> ayarlanır <xref:System.Activities.UnhandledExceptionAction.Abort>: Bir özel durum oluştuğunda, hizmet dağıtım bilgileri için örnek deposuna yazılır ve bellekten iş akışı örneği kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="23e7e-115"><xref:System.Activities.UnhandledExceptionAction> is set to <xref:System.Activities.UnhandledExceptionAction.Abort>: When an exception occurs, service deployment information is written to the instance store, and the workflow instance is unloaded from memory.</span></span> <span data-ttu-id="23e7e-116">İş akışı örneği kalıcı olmayan bir durumda kalır ve yeniden yüklenemiyor.</span><span class="sxs-lookup"><span data-stu-id="23e7e-116">The workflow instance remains in a non-persisted state and cannot be reloaded.</span></span>  
  
    - <span data-ttu-id="23e7e-117"><xref:System.Activities.UnhandledExceptionAction> ayarlanır <xref:System.Activities.UnhandledExceptionAction.Cancel> veya <xref:System.Activities.UnhandledExceptionAction.Terminate>: Özel bir durum oluştuğunda, hizmet dağıtım bilgileri, örnek deposuna yazılır ve etkinlik örneğinin durumunu ayarlamak <xref:System.Activities.ActivityInstanceState.Closed>.</span><span class="sxs-lookup"><span data-stu-id="23e7e-117"><xref:System.Activities.UnhandledExceptionAction> is set to <xref:System.Activities.UnhandledExceptionAction.Cancel> or <xref:System.Activities.UnhandledExceptionAction.Terminate>: When an exception occurs, service deployment information is written to the instance store, and the activity instance state is set to <xref:System.Activities.ActivityInstanceState.Closed>.</span></span>  
  
 <span data-ttu-id="23e7e-118">Kaldırılan kalıcı olmayan iş akışı örnekleri karşılaşıldığında riskini en aza indirmek için erken yaşam döngüsü içinde iş akışını sürdürmek öneririz.</span><span class="sxs-lookup"><span data-stu-id="23e7e-118">To minimize the risk of encountering unloaded non-persisted workflow instances, we recommend persisting the workflow early in its life cycle.</span></span>  
  
## <a name="detection-and-removal-of-non-persisted-instances"></a><span data-ttu-id="23e7e-119">Algılama ve kaldırma kalıcı olmayan örnekleri</span><span class="sxs-lookup"><span data-stu-id="23e7e-119">Detection and Removal of Non-Persisted Instances</span></span>  
 <span data-ttu-id="23e7e-120"><xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> Herhangi kalıcı olmayan iş akışı örnekleri örnek deposundan kaldırmaz.</span><span class="sxs-lookup"><span data-stu-id="23e7e-120">The <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> does not remove any non-persisted workflow instances from the instance store.</span></span> <span data-ttu-id="23e7e-121">Kalıcı olmayan iş akışı örneği ile ilişkili tüm süresi dolan kilit sahiplerinin ayrıca kaldırmaz.</span><span class="sxs-lookup"><span data-stu-id="23e7e-121">It also does not remove any expired lock owners that have non-persisted workflow instances associated with them.</span></span>  
  
 <span data-ttu-id="23e7e-122">Yönetici kalıcı olmayan örnekleri için örnek deposuna düzenli aralıklarla denetleyen öneririz.</span><span class="sxs-lookup"><span data-stu-id="23e7e-122">We recommend that the administrator periodically checks the instance store for non-persisted instances.</span></span> <span data-ttu-id="23e7e-123">Bu iş akışı bağıntılı iletilerin almaz alışık oldukları sürece Yöneticiler bu örnekleri örnek deposundan kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="23e7e-123">Administrators can remove those instances from the instance store as long as they know that this workflow will not receive correlated messages.</span></span> <span data-ttu-id="23e7e-124">Örneğin, örnek veritabanında birkaç ay boyunca yapıldı ve iş akışı genellikle birkaç gün ömrü olduğunu bilinir, kilitlenen başlatılmış örneği olduğunu varsayın güvenli olurdu.</span><span class="sxs-lookup"><span data-stu-id="23e7e-124">For example, if the instance has been in the database for several months and it is known that the workflow typically has a lifetime of several days, it would be safe to assume that this was an initialized instance that had crashed.</span></span>  
  
 <span data-ttu-id="23e7e-125">SQL iş akışı örneği Store içinde kalıcı olmayan örnekleri bulmak için aşağıdaki SQL sorgularını kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="23e7e-125">To find non-persisted instances in the SQL Workflow Instance Store you can use the following SQL queries:</span></span>  
  
- <span data-ttu-id="23e7e-126">Bu sorgu, kalıcı ve (UTC saatiyle depolanır) kimliği ve oluşturma zamanı için bunları döndüren tüm örneklerini bulur.</span><span class="sxs-lookup"><span data-stu-id="23e7e-126">This query finds all instances that have not been persisted, and returns the ID and creation time (stored in UTC time) for them.</span></span>  
  
    ```sql  
    select InstanceId, CreationTime   
        from [System.Activities.DurableInstancing].[Instances]   
        where IsInitialized = 0  
    ```  
  
- <span data-ttu-id="23e7e-127">Bu sorgu değil yerleştirildi ve yüklü değildir ve döndürür (UTC saatiyle depolanır) kimliği ve oluşturma zamanı bunları için tüm örneklerini bulur.</span><span class="sxs-lookup"><span data-stu-id="23e7e-127">This query finds all instances that have not been persisted, and that are not loaded, and returns the ID and creation time (stored in UTC time) for them.</span></span>  
  
    ```sql  
    select InstanceId, CreationTime   
        from [System.Activities.DurableInstancing].[Instances]   
        where IsInitialized = 0   
            and CurrentMachine is NULL  
    ```  
  
- <span data-ttu-id="23e7e-128">Bu sorgu kalıcı ve döndüren kimliği, oluşturma zamanı (UTC saatiyle depolanır), askıya alınmış tüm örneklerini bulur askıya alma nedeni ve bunlar için özel durum adı.</span><span class="sxs-lookup"><span data-stu-id="23e7e-128">This query finds all suspended instances that have not been persisted, and returns the ID, creation time (stored in UTC time), suspension reason, and exception name for them.</span></span>  
  
    ```sql  
    select InstanceId, CreationTime, SuspensionReason, SuspensionExceptionName   
        from [System.Activities.DurableInstancing].[Instances]   
        where IsInitialized = 0   
            and IsSuspended = 1  
    ```  
  
 <span data-ttu-id="23e7e-129">Kalıcı olmayan örnekleri silerken dikkatli olun.</span><span class="sxs-lookup"><span data-stu-id="23e7e-129">Use care when you are deleting non-persisted instances.</span></span> <span data-ttu-id="23e7e-130">Genel olarak, kalıcı olmayan örnekleri tarafından oluşturulan kaldırmanın güvenli olduğunu <xref:System.ServiceModel.Activities.WorkflowServiceHost> askıya alınmış durumda veya yüklü değil.</span><span class="sxs-lookup"><span data-stu-id="23e7e-130">In general, it is safe to remove non-persisted instances created by <xref:System.ServiceModel.Activities.WorkflowServiceHost> that are suspended or are not loaded.</span></span> <span data-ttu-id="23e7e-131">Bunları silerek, bu belirli örneklere Mağaza'dan silinebilir `[System.Activities.DurableInstancing].[Instances]` doğru örneği kimliğini değiştirerek aşağıdaki SQL komutunu kullanarak görünümü</span><span class="sxs-lookup"><span data-stu-id="23e7e-131">Those specific instances can be deleted from the store by deleting them from the `[System.Activities.DurableInstancing].[Instances]` view by using the following SQL command, substituting the correct instance ID.</span></span>  
  
```sql  
delete [System.Activities.DurableInstancing].[Instances]   
    where InstanceId=’078a9bc4-ada5-4f9e-8cce-b0eb0009995f’  
```  
  
> [!WARNING]
>  <span data-ttu-id="23e7e-132">Bu, az önce oluşturduğunuz ve henüz kalıcı örnekleri içerdiğinden tüm kalıcı olmayan örnekleri kaldırma önermiyoruz.</span><span class="sxs-lookup"><span data-stu-id="23e7e-132">We do not recommend removing all non-persisted instances because this includes instances that have just been created and have not yet been persisted.</span></span>
