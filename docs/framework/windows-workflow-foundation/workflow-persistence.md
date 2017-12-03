---
title: "İş akışı kalıcılığı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: programming [WF], persistence
ms.assetid: 39e69d1f-b771-4c16-9e18-696fa43b65b2
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 769197b3f59c68c79f94c71c49ba4b1f4f98da2c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="workflow-persistence"></a><span data-ttu-id="d5186-102">İş akışı kalıcılığı</span><span class="sxs-lookup"><span data-stu-id="d5186-102">Workflow Persistence</span></span>
<span data-ttu-id="d5186-103">İş akışı Kalıcılık dayanıklı yakalama bir iş akışı örneğinin durumu, işlem veya bilgisayar bilgilerinin bağımsız olur.</span><span class="sxs-lookup"><span data-stu-id="d5186-103">Workflow persistence is the durable capture of a workflow instance's state, independent of process or computer information.</span></span> <span data-ttu-id="d5186-104">Bu sistem hatası durumunda iş akışı örneği için iyi bilinen bir kurtarma noktası sağlamak üzere veya etkin olarak iş yapmamanın kaldırma iş akışı örnekleri tarafından bellek korumak için ya da iş akışı örneği çalışma durumu bir düğümden diğerine taşımak için gerçekleştirilir bir sunucu grubundaki düğümü.</span><span class="sxs-lookup"><span data-stu-id="d5186-104">This is done to provide a well-known point of recovery for the workflow instance in the event of system failure, or to preserve memory by unloading workflow instances that are not actively doing work, or to move the state of the workflow instance from one node to another node in a server farm.</span></span>  
  
 <span data-ttu-id="d5186-105">İşlem çeviklik, ölçeklenebilirlik, Kurtarma hatası karşısında ve bellek daha verimli bir şekilde yönetme becerisini kalıcılığını etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="d5186-105">Persistence enables process agility, scalability, recovery in the face of failure, and the ability to manage memory more efficiently.</span></span> <span data-ttu-id="d5186-106">Kalıcılık işlemi Kalıcılık noktasını, kaydedilecek veri toplama ve son olarak verilerin kalıcı bir sağlayıcı için gerçek depolama temsilci kimliğini içerir.</span><span class="sxs-lookup"><span data-stu-id="d5186-106">The persistence process includes the identification of a persistence point, the gathering of the data to be saved, and finally the delegation of the actual storage of the data to a persistence provider.</span></span>  
  
 <span data-ttu-id="d5186-107">Bir iş akışı kalıcılığını etkinleştirmek için bir örnek depolama ile ilişkilendirmeniz gerekir **WorkflowApplication** veya **WorkflowServiceHost** bölümünde belirtildiği gibi [nasıl yapılır: kalıcılığı etkinleştir İş akışları ve iş akışı Hizmetleri](../../../docs/framework/windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="d5186-107">To enable persistence for a workflow, you need to associate an instance store with the **WorkflowApplication** or **WorkflowServiceHost** as mentioned in [How to: Enable Persistence for Workflows and Workflow Services](../../../docs/framework/windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md).</span></span> <span data-ttu-id="d5186-108">**WorkflowApplication** ve **WorkflowServiceHost** Kalıcılık deposu ve iş akışı örneği yükleniyor kalıcı iş akışı örneği etkinleştirmek için onlarla ilişkili örnek deposuna kullanın Kalıcılık store içinde depolanan iş akışı örneği verileri temel bellek.</span><span class="sxs-lookup"><span data-stu-id="d5186-108">The **WorkflowApplication** and **WorkflowServiceHost** use the instance store associated with them to enable persisting workflow instances into a persistence store and loading workflow instances into memory based on the workflow instance data stored in the persistence store.</span></span>  
  
 <span data-ttu-id="d5186-109">[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] Birlikte **SqlWorkflowInstanceStore** verileri ve iş akışı örneği bir SQL Server 2005 veya SQL Server 2008 veritabanı içine hakkındaki meta verileri kalıcılığı sağlayan sınıf.</span><span class="sxs-lookup"><span data-stu-id="d5186-109">The [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] ships with the **SqlWorkflowInstanceStore** class, which allows persistence of data and metadata about workflow instances into a SQL Server 2005 or SQL Server 2008 database.</span></span> <span data-ttu-id="d5186-110">Bkz: [SQL iş akışı örneği deposuna](../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md) daha fazla ayrıntı için.</span><span class="sxs-lookup"><span data-stu-id="d5186-110">See [SQL Workflow Instance Store](../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md) for more details.</span></span>  
  
 <span data-ttu-id="d5186-111">Depolamak ve iş akışı örneği ile ilgili bilgilerin yanı sıra, uygulamaya özgü verileri yüklemek için genişletme Kalıcılık katılımcıları oluşturabilirsiniz <xref:System.Activities.Persistence.PersistenceParticipant> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d5186-111">To store and load your application-specific data along with the workflow instance-related information, you can create persistence participants that extend the <xref:System.Activities.Persistence.PersistenceParticipant> class.</span></span> <span data-ttu-id="d5186-112">Kalıcı depoya belleğe örneği Mağazası'ndan veri yüklemeye ve ilave bir mantık Kalıcılık işlem altında gerçekleştirmek için özel seri hale getirilebilir veri kaydetmek için Kalıcılık işlemindeki Kalıcılık katılımcı katılır.</span><span class="sxs-lookup"><span data-stu-id="d5186-112">A persistence participant participates in the persistence process to save custom serializable data into the persistence store, to load the data from the instance store into memory, and to perform any additional logic under a persistence transaction.</span></span> <span data-ttu-id="d5186-113">Daha fazla bilgi için bkz: [Kalıcılık katılımcıları](../../../docs/framework/windows-workflow-foundation/persistence-participants.md).</span><span class="sxs-lookup"><span data-stu-id="d5186-113">For more information, see [Persistence Participants](../../../docs/framework/windows-workflow-foundation/persistence-participants.md).</span></span>  
  
 <span data-ttu-id="d5186-114">Windows Server App Fabric kalıcılığı yapılandırma işlemini basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="d5186-114">Windows Server App Fabric simplifies the process of configuring persistence.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="d5186-115">[Windows Server App Fabric ile kalıcılığı kavramları](http://go.microsoft.com/fwlink/?LinkId=201200)</span><span class="sxs-lookup"><span data-stu-id="d5186-115"> [Persistence Concepts with Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkId=201200)</span></span>  
  
## <a name="implicit-persistence-points"></a><span data-ttu-id="d5186-116">Örtük Kalıcılık noktaları</span><span class="sxs-lookup"><span data-stu-id="d5186-116">Implicit Persistence Points</span></span>  
 <span data-ttu-id="d5186-117">Aşağıdaki listeden bir örnek deposuna bir iş akışı ile ilişkili olduğunda bağlı bir iş akışı kalıcı koşulları örnekleri içerir.</span><span class="sxs-lookup"><span data-stu-id="d5186-117">The following list contains examples of the conditions upon which a workflow is persisted when an instance store is associated with a workflow.</span></span>  
  
-   <span data-ttu-id="d5186-118">Zaman bir **TransactionScope** etkinlik tamamlandıktan veya **TransactedReceiveScope** etkinliği tamamlar.</span><span class="sxs-lookup"><span data-stu-id="d5186-118">When a **TransactionScope** activity completes or a **TransactedReceiveScope** activity completes.</span></span>  
  
-   <span data-ttu-id="d5186-119">Bir iş akışı örneği olduğunda boşta ve **WorkflowIdleBehavior** iş akışı ana bilgisayarında ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d5186-119">When a workflow instance becomes idle and the **WorkflowIdleBehavior** is set on workflow host.</span></span> <span data-ttu-id="d5186-120">Bu, örneğin, Mesajlaşma etkinlikleri kullanın veya bir oluşur **gecikme** etkinlik.</span><span class="sxs-lookup"><span data-stu-id="d5186-120">This occurs, for example, when you use messaging activities or a **Delay** activity.</span></span>  
  
-   <span data-ttu-id="d5186-121">Bir WorkflowApplication olduğunda boşta ve **PersistableIdle** uygulamanın özelliği ayarlanmış **PersistableIdleAction.Persist**.</span><span class="sxs-lookup"><span data-stu-id="d5186-121">When a WorkflowApplication becomes idle and the **PersistableIdle** property of the application is set to **PersistableIdleAction.Persist**.</span></span>  
  
-   <span data-ttu-id="d5186-122">Ne zaman bir ana bilgisayar uygulaması devam veya bir iş akışı örneği unload talimatı verilir.</span><span class="sxs-lookup"><span data-stu-id="d5186-122">When a host application is instructed to persist or unload a workflow instance.</span></span>  
  
-   <span data-ttu-id="d5186-123">Ne zaman bir iş akışı örneği sonlandırıldı veya tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="d5186-123">When a workflow instance is terminated or finishes.</span></span>  
  
-   <span data-ttu-id="d5186-124">Zaman bir **devam ettir** etkinlik yürütür.</span><span class="sxs-lookup"><span data-stu-id="d5186-124">When a **Persist** activity executes.</span></span>  
  
-   <span data-ttu-id="d5186-125">Windows Workflow Foundation'ın önceki bir sürümü kullanılarak geliştirilen bir iş akışı örneği Kalıcılık noktası birlikte çalışabilir yürütme sırasında karşılaştığında.</span><span class="sxs-lookup"><span data-stu-id="d5186-125">When an instance of a workflow developed using a previous version of Windows Workflow Foundation encounters a persistence point during interoperable execution.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d5186-126">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="d5186-126">In This Section</span></span>  
  
-   [<span data-ttu-id="d5186-127">SQL iş akışı örneği deposu</span><span class="sxs-lookup"><span data-stu-id="d5186-127">SQL Workflow Instance Store</span></span>](../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md)  
  
-   [<span data-ttu-id="d5186-128">Örnek depolar</span><span class="sxs-lookup"><span data-stu-id="d5186-128">Instance Stores</span></span>](../../../docs/framework/windows-workflow-foundation/instance-stores.md)  
  
-   [<span data-ttu-id="d5186-129">Kalıcılık katılımcıları</span><span class="sxs-lookup"><span data-stu-id="d5186-129">Persistence Participants</span></span>](../../../docs/framework/windows-workflow-foundation/persistence-participants.md)  
  
-   [<span data-ttu-id="d5186-130">Kalıcılık en iyi uygulamalar</span><span class="sxs-lookup"><span data-stu-id="d5186-130">Persistence Best Practices</span></span>](../../../docs/framework/windows-workflow-foundation/persistence-best-practices.md)  
  
-   [<span data-ttu-id="d5186-131">Kalıcı olmayan iş akışı örnekleri</span><span class="sxs-lookup"><span data-stu-id="d5186-131">Non-Persisted Workflow Instances</span></span>](../../../docs/framework/windows-workflow-foundation/non-persisted-workflow-instances.md)  
  
-   [<span data-ttu-id="d5186-132">Duraklatma ve sürdürme bir iş akışı</span><span class="sxs-lookup"><span data-stu-id="d5186-132">Pausing and Resuming a Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/pausing-and-resuming-a-workflow.md)
