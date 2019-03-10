---
title: İş akışı kalıcılığı
ms.date: 03/30/2017
helpviewer_keywords:
- programming [WF], persistence
ms.assetid: 39e69d1f-b771-4c16-9e18-696fa43b65b2
ms.openlocfilehash: db0e4acc76f758004948857fc0b23a9cbc62f244
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57715548"
---
# <a name="workflow-persistence"></a><span data-ttu-id="17494-102">İş akışı kalıcılığı</span><span class="sxs-lookup"><span data-stu-id="17494-102">Workflow Persistence</span></span>
<span data-ttu-id="17494-103">İş akışı kalıcılığı dayanıklı yakalama bir iş akışı örneği durumu, işlem veya bilgisayar bilgilerinin bağımsız olur.</span><span class="sxs-lookup"><span data-stu-id="17494-103">Workflow persistence is the durable capture of a workflow instance's state, independent of process or computer information.</span></span> <span data-ttu-id="17494-104">Bu sistem hatası durumunda iş akışı örneği için bilinen bir kurtarma noktası sağlamak veya etkin bir şekilde iş yapmamanın kaldırma iş akışı örnekleri tarafından bellek korumak için veya iş akışı örneği durumu bir düğümden diğerine taşımak için gerçekleştirilir bir sunucu grubundaki düğümü.</span><span class="sxs-lookup"><span data-stu-id="17494-104">This is done to provide a well-known point of recovery for the workflow instance in the event of system failure, or to preserve memory by unloading workflow instances that are not actively doing work, or to move the state of the workflow instance from one node to another node in a server farm.</span></span>  
  
 <span data-ttu-id="17494-105">Kalıcılık işlemin çeviklik, ölçeklenebilirlik, Kurtarma hata ile karşılaşıldığında ve belleği daha verimli bir şekilde yönetme olanağı sağlar.</span><span class="sxs-lookup"><span data-stu-id="17494-105">Persistence enables process agility, scalability, recovery in the face of failure, and the ability to manage memory more efficiently.</span></span> <span data-ttu-id="17494-106">Kalıcılık işlem Kalıcılık noktası, veri toplamayı ve son olarak verilerin kalıcı bir sağlayıcı gerçek depolama alanlarının kimliğini içerir.</span><span class="sxs-lookup"><span data-stu-id="17494-106">The persistence process includes the identification of a persistence point, the gathering of the data to be saved, and finally the delegation of the actual storage of the data to a persistence provider.</span></span>  
  
 <span data-ttu-id="17494-107">Bir iş akışı kalıcılığını etkinleştirmek için bir örnek deposuna ile ilişkilendirmeniz gerekir **WorkflowApplication** veya **WorkflowServiceHost** belirtildiği gibi [nasıl yapılır: İş akışları ve iş akışı hizmetleri için kalıcılığı etkinleştir](how-to-enable-persistence-for-workflows-and-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="17494-107">To enable persistence for a workflow, you need to associate an instance store with the **WorkflowApplication** or **WorkflowServiceHost** as mentioned in [How to: Enable Persistence for Workflows and Workflow Services](how-to-enable-persistence-for-workflows-and-workflow-services.md).</span></span> <span data-ttu-id="17494-108">**WorkflowApplication** ve **WorkflowServiceHost** ilişkili örnek deposuna sürdürme deposundan ve iş akışı örneği yükleniyor kalıcı hale getirme iş akışı örnekleri etkinleştirmek için kullanın İş akışı örneği verileri sürdürme deposunda saklanan bağlı bellek.</span><span class="sxs-lookup"><span data-stu-id="17494-108">The **WorkflowApplication** and **WorkflowServiceHost** use the instance store associated with them to enable persisting workflow instances into a persistence store and loading workflow instances into memory based on the workflow instance data stored in the persistence store.</span></span>  
  
 <span data-ttu-id="17494-109">[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] Birlikte **SqlWorkflowInstanceStore** Kalıcılık verileri ve SQL Server 2005 veya SQL Server 2008 veritabanına iş akışı örnekleri hakkında meta veriler sağlayan sınıf.</span><span class="sxs-lookup"><span data-stu-id="17494-109">The [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] ships with the **SqlWorkflowInstanceStore** class, which allows persistence of data and metadata about workflow instances into a SQL Server 2005 or SQL Server 2008 database.</span></span> <span data-ttu-id="17494-110">Bkz: [SQL iş akışı örneği Store](sql-workflow-instance-store.md) daha fazla ayrıntı için.</span><span class="sxs-lookup"><span data-stu-id="17494-110">See [SQL Workflow Instance Store](sql-workflow-instance-store.md) for more details.</span></span>  
  
 <span data-ttu-id="17494-111">Depolayın ve iş akışı örneği ile ilgili bilgilerin yanı sıra, uygulamaya özgü verileri yüklemek için genişletme Kalıcılık katılımcıları oluşturabilirsiniz <xref:System.Activities.Persistence.PersistenceParticipant> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="17494-111">To store and load your application-specific data along with the workflow instance-related information, you can create persistence participants that extend the <xref:System.Activities.Persistence.PersistenceParticipant> class.</span></span> <span data-ttu-id="17494-112">Kalıcı depoya belleğe örneği Mağazası'ndan veri yüklemeye ve herhangi ek bir mantık Kalıcılık işlem altında gerçekleştirmek için özel seri hale getirilebilir veri kaydetmek için Kalıcılık işleminde bir Kalıcılık Katılımcısı katılır.</span><span class="sxs-lookup"><span data-stu-id="17494-112">A persistence participant participates in the persistence process to save custom serializable data into the persistence store, to load the data from the instance store into memory, and to perform any additional logic under a persistence transaction.</span></span> <span data-ttu-id="17494-113">Daha fazla bilgi için [Kalıcılık katılımcıları](persistence-participants.md).</span><span class="sxs-lookup"><span data-stu-id="17494-113">For more information, see [Persistence Participants](persistence-participants.md).</span></span>  
  
 <span data-ttu-id="17494-114">Windows Server App Fabric kalıcılığını yapılandırma işlemini basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="17494-114">Windows Server App Fabric simplifies the process of configuring persistence.</span></span> <span data-ttu-id="17494-115">Daha fazla bilgi için [Windows Server App Fabric ile Kalıcılık kavramları](https://go.microsoft.com/fwlink/?LinkId=201200)</span><span class="sxs-lookup"><span data-stu-id="17494-115">For more information, see [Persistence Concepts with Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkId=201200)</span></span>  
  
## <a name="implicit-persistence-points"></a><span data-ttu-id="17494-116">Örtük Kalıcılık noktaları</span><span class="sxs-lookup"><span data-stu-id="17494-116">Implicit Persistence Points</span></span>  
 <span data-ttu-id="17494-117">Aşağıdaki liste, bir örnek deposuna bir iş akışı ile ilişkili olduğunda, bir akışı kalıcı koşullar örnekleri içerir.</span><span class="sxs-lookup"><span data-stu-id="17494-117">The following list contains examples of the conditions upon which a workflow is persisted when an instance store is associated with a workflow.</span></span>  
  
-   <span data-ttu-id="17494-118">Olduğunda bir **TransactionScope** etkinliği tamamlandıktan veya **TransactedReceiveScope** etkinliği tamamlar.</span><span class="sxs-lookup"><span data-stu-id="17494-118">When a **TransactionScope** activity completes or a **TransactedReceiveScope** activity completes.</span></span>  
  
-   <span data-ttu-id="17494-119">Bir iş akışı örneği olduğunda boşta ve **WorkflowIdleBehavior** iş akışı konakta ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="17494-119">When a workflow instance becomes idle and the **WorkflowIdleBehavior** is set on workflow host.</span></span> <span data-ttu-id="17494-120">Bu, örneğin, Mesajlaşma etkinlikleri kullandığınızda veya oluşur **gecikme** etkinlik.</span><span class="sxs-lookup"><span data-stu-id="17494-120">This occurs, for example, when you use messaging activities or a **Delay** activity.</span></span>  
  
-   <span data-ttu-id="17494-121">Bir WorkflowApplication olduğunda boşta ve **PersistableIdle** uygulamanın özelliği **PersistableIdleAction.Persist**.</span><span class="sxs-lookup"><span data-stu-id="17494-121">When a WorkflowApplication becomes idle and the **PersistableIdle** property of the application is set to **PersistableIdleAction.Persist**.</span></span>  
  
-   <span data-ttu-id="17494-122">Ne zaman bir ana bilgisayar uygulaması kalıcı veya bir iş akışı örneği kaldırmak için talimat verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="17494-122">When a host application is instructed to persist or unload a workflow instance.</span></span>  
  
-   <span data-ttu-id="17494-123">Ne zaman bir iş akışı örneği sonlandırıldı veya tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="17494-123">When a workflow instance is terminated or finishes.</span></span>  
  
-   <span data-ttu-id="17494-124">Olduğunda bir **kalan** etkinliği yürütür.</span><span class="sxs-lookup"><span data-stu-id="17494-124">When a **Persist** activity executes.</span></span>  
  
-   <span data-ttu-id="17494-125">Ne zaman Windows Workflow Foundation'ın önceki bir sürümü kullanılarak geliştirilen bir iş akışı örneği birlikte çalışabilen yürütme sırasında bir Kalıcılık noktası karşılaşır.</span><span class="sxs-lookup"><span data-stu-id="17494-125">When an instance of a workflow developed using a previous version of Windows Workflow Foundation encounters a persistence point during interoperable execution.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="17494-126">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="17494-126">In This Section</span></span>  
  
-   [<span data-ttu-id="17494-127">SQL İş Akışı Örnek Deposu</span><span class="sxs-lookup"><span data-stu-id="17494-127">SQL Workflow Instance Store</span></span>](sql-workflow-instance-store.md)  
  
-   [<span data-ttu-id="17494-128">Örnek Depoları</span><span class="sxs-lookup"><span data-stu-id="17494-128">Instance Stores</span></span>](instance-stores.md)  
  
-   [<span data-ttu-id="17494-129">Kalıcılık Katılımcıları</span><span class="sxs-lookup"><span data-stu-id="17494-129">Persistence Participants</span></span>](persistence-participants.md)  
  
-   [<span data-ttu-id="17494-130">Kalıcılık En İyi Uygulamaları</span><span class="sxs-lookup"><span data-stu-id="17494-130">Persistence Best Practices</span></span>](persistence-best-practices.md)  
  
-   [<span data-ttu-id="17494-131">Kalıcı Olmayan İş Akışı Örnekleri</span><span class="sxs-lookup"><span data-stu-id="17494-131">Non-Persisted Workflow Instances</span></span>](non-persisted-workflow-instances.md)  
  
-   [<span data-ttu-id="17494-132">İş Akışını Duraklatma ve Sürdürme</span><span class="sxs-lookup"><span data-stu-id="17494-132">Pausing and Resuming a Workflow</span></span>](pausing-and-resuming-a-workflow.md)
