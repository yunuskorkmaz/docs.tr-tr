---
description: 'Şu konuda daha fazla bilgi edinin: nasıl yapılır: WorkflowServiceHost ile Kalıcılığı Yapılandırma'
title: 'Nasıl yapılır: WorkflowServiceHost ile Kalıcılığı Yapılandırma'
ms.date: 03/30/2017
ms.assetid: e31cd4df-13a3-4a9a-9be8-5243e0055356
ms.openlocfilehash: 79945fb791cc25bdf362302fa884636942fb5692
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99780043"
---
# <a name="how-to-configure-persistence-with-workflowservicehost"></a><span data-ttu-id="2228d-103">Nasıl yapılır: WorkflowServiceHost ile Kalıcılığı Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="2228d-103">How to: Configure Persistence with WorkflowServiceHost</span></span>

<span data-ttu-id="2228d-104">Bu konuda, <xref:System.ServiceModel.Activities.WorkflowServiceHost> bir yapılandırma dosyası kullanılarak içinde barındırılan iş akışları için kalıcılığı etkinleştirmek üzere SQL Iş akışı örnek deposu özelliğinin nasıl yapılandırılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2228d-104">This topic describes how to configure the SQL Workflow Instance Store feature to enable persistence for workflows hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost> by using a configuration file.</span></span> <span data-ttu-id="2228d-105">SQL Iş akışı örnek deposu özelliğini kullanmadan önce, iş akışı örneklerini kalıcı hale getirmek için kullanılan bir SQL veritabanı oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2228d-105">Before using the SQL Workflow Instance Store feature you must create a SQL database that is used to persist workflow instances.</span></span> <span data-ttu-id="2228d-106">Daha fazla bilgi için bkz. [nasıl yapılır: Iş akışları ve Iş akışı hizmetleri IÇIN SQL kalıcılığını etkinleştirme](../../windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="2228d-106">For more information, see [How to: Enable SQL Persistence for Workflows and Workflow Services](../../windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span></span>  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-configuration"></a><span data-ttu-id="2228d-107">Yapılandırmada SQL Iş akışı örnek deposunu yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="2228d-107">To Configure the SQL Workflow Instance Store in Configuration</span></span>  
  
1. <span data-ttu-id="2228d-108">SQL iş akışı örnek deposunun özellikleri, <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> ayarları XML yapılandırması aracılığıyla değiştirmenize olanak tanıyan bir hizmet davranışı aracılığıyla yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="2228d-108">The properties of the SQL workflow instance store can be configured through the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, a service behavior that allows you to change the settings through XML configuration.</span></span> <span data-ttu-id="2228d-109">Aşağıdaki yapılandırma örneği, `sqlWorkflowInstanceStore` bir yapılandırma dosyasında <> Behavior öğesi KULLANıLARAK SQL iş akışı örnek deposunun nasıl yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2228d-109">The following configuration example shows how to configure the SQL workflow instance store by using the <`sqlWorkflowInstanceStore`> behavior element in a configuration file.</span></span>  
  
    ```xml  
    <serviceBehaviors>  
        <behavior name="">  
            <sqlWorkflowInstanceStore
                 connectionString="provider=System.Data.SqlClient;Data Source=(local);Initial Catalog=DefaultPersistenceProviderDb;Integrated Security=True;Async=true"  
                 instanceEncodingOption="GZip | None"  
                 instanceCompletionAction="DeleteAll | DeleteNothing"  
                 instanceLockedExceptionAction="NoRetry | SimpleRetry | AggressiveRetry"  
                 hostLockRenewalPeriod="00:00:30"
                 runnableInstancesDetectionPeriod="00:00:05">  
            </sqlWorkflowInstanceStore>  
        </behavior>  
    </serviceBehaviors>  
    ```  
  
     <span data-ttu-id="2228d-110">SQL iş akışı örnek deposunun nasıl yapılandırılacağı hakkında daha fazla bilgi için bkz. [nasıl yapılır: Iş akışları ve Iş akışı hizmetleri IÇIN SQL kalıcılığını etkinleştirme](../../windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="2228d-110">For more information about how to configure the SQL workflow instance store, see [How to: Enable SQL Persistence for Workflows and Workflow Services](../../windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span></span> <span data-ttu-id="2228d-111"><> davranış öğesinin bireysel ayarları hakkında daha fazla bilgi için `sqlWorkflowInstanceStore` bkz. [SQL Workflow örnek deposu](../../windows-workflow-foundation/sql-workflow-instance-store.md).</span><span class="sxs-lookup"><span data-stu-id="2228d-111">For more information about the individual settings for the <`sqlWorkflowInstanceStore`> behavior element, see [SQL Workflow Instance Store](../../windows-workflow-foundation/sql-workflow-instance-store.md).</span></span> <span data-ttu-id="2228d-112">Windows Server App Fabric kendi Kalıcılık mağazasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="2228d-112">Windows Server App Fabric provides its own persistence store.</span></span> <span data-ttu-id="2228d-113">Daha fazla bilgi için bkz. [Windows Server App Fabric kalıcılığı](/previous-versions/appfabric/ee677272(v=azure.10)).</span><span class="sxs-lookup"><span data-stu-id="2228d-113">For more information, see [Windows Server App Fabric Persistence](/previous-versions/appfabric/ee677272(v=azure.10)).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="2228d-114">Önceki yapılandırma örneği Basitleştirilmiş yapılandırma kullanır.</span><span class="sxs-lookup"><span data-stu-id="2228d-114">The preceding configuration example uses simplified configuration.</span></span> <span data-ttu-id="2228d-115">Daha fazla bilgi için bkz. [Basitleştirilmiş yapılandırma](../simplified-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="2228d-115">For more information, see [Simplified Configuration](../simplified-configuration.md)</span></span>  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-code"></a><span data-ttu-id="2228d-116">SQL Iş akışı örnek deposunu kodda yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="2228d-116">To Configure the SQL Workflow Instance Store in Code</span></span>  
  
1. <span data-ttu-id="2228d-117">SQL iş akışı örnek deposunun özellikleri, <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> ayarları kod aracılığıyla değiştirmenize olanak tanıyan bir hizmet davranışı aracılığıyla yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="2228d-117">The properties of the SQL workflow instance store can be configured through the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, a service behavior that allows you to change the settings through code.</span></span> <span data-ttu-id="2228d-118">Aşağıdaki örnek, <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> bir koddaki davranış öğesi KULLANıLARAK SQL iş akışı örnek deposunun nasıl yapılandırılacağını gösterir</span><span class="sxs-lookup"><span data-stu-id="2228d-118">The following example shows how to configure the SQL workflow instance store by using the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> behavior element in a code</span></span>  
  
    ```csharp  
    host.Description.Behaviors.Add(new SqlWorkflowInstanceStoreBehavior  
    {  
       ConnectionString = "provider=System.Data.SqlClient;Data Source=(local);Initial Catalog=DefaultPersistenceProviderDb;Integrated Security=True;Async=true",  
       InstanceEncodingOption = "GZip | None",  
       InstanceCompletionAction = "DeleteAll | DeleteNothing",  
       InstanceLockedExceptionAction = "NoRetry | SimpleRetry | AggressiveRetry",  
       HostLockRenewalPeriod = new TimeSpan(00, 00, 30),  
       RunnableInstancesDetectionPeriod = new TimeSpan(00, 00, 05)  
    });  
    ```  
  
     <span data-ttu-id="2228d-119">SQL iş akışı örnek deposunun nasıl yapılandırılacağı hakkında daha fazla bilgi için bkz. [nasıl yapılır: Iş akışları ve Iş akışı hizmetleri IÇIN SQL kalıcılığını etkinleştirme](../../windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="2228d-119">For more information about how to configure the SQL workflow instance store, see [How to: Enable SQL Persistence for Workflows and Workflow Services](../../windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span></span> <span data-ttu-id="2228d-120">Davranış öğesinin bireysel ayarları hakkında daha fazla bilgi için <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> bkz. [SQL Workflow örnek deposu](../../windows-workflow-foundation/sql-workflow-instance-store.md).</span><span class="sxs-lookup"><span data-stu-id="2228d-120">For more information about the individual settings for the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> behavior element, see [SQL Workflow Instance Store](../../windows-workflow-foundation/sql-workflow-instance-store.md).</span></span> <span data-ttu-id="2228d-121">Windows Server App Fabric kendi Kalıcılık mağazasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="2228d-121">Windows Server App Fabric provides its own persistence store.</span></span> <span data-ttu-id="2228d-122">Daha fazla bilgi için bkz. [Windows Server App Fabric kalıcılığı](/previous-versions/appfabric/ee677272(v=azure.10)).</span><span class="sxs-lookup"><span data-stu-id="2228d-122">For more information, see [Windows Server App Fabric Persistence](/previous-versions/appfabric/ee677272(v=azure.10)).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="2228d-123">Önceki yapılandırma örneği Basitleştirilmiş yapılandırma kullanır.</span><span class="sxs-lookup"><span data-stu-id="2228d-123">The preceding configuration example uses simplified configuration.</span></span> <span data-ttu-id="2228d-124">Daha fazla bilgi için bkz. [Basitleştirilmiş yapılandırma](../simplified-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="2228d-124">For more information, see [Simplified Configuration](../simplified-configuration.md)</span></span>  
  
     <span data-ttu-id="2228d-125">Kalıcılığın nasıl yapılandırılacağı hakkında bir örnek için bkz. [nasıl yapılır: Iş akışları ve Iş akışı hizmetleri Için kalıcılığı etkinleştirme](../../windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="2228d-125">For an example of how to configure persistence programmatically see [How to: Enable Persistence for Workflows and Workflow Services](../../windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2228d-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2228d-126">See also</span></span>

- [<span data-ttu-id="2228d-127">İş Akışı Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="2228d-127">Workflow Services</span></span>](workflow-services.md)
- [<span data-ttu-id="2228d-128">İş Akışı Kalıcılığı</span><span class="sxs-lookup"><span data-stu-id="2228d-128">Workflow Persistence</span></span>](../../windows-workflow-foundation/workflow-persistence.md)
- <span data-ttu-id="2228d-129">[Windows Server App Fabric kalıcılığı](/previous-versions/appfabric/ee677272(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="2228d-129">[Windows Server App Fabric Persistence](/previous-versions/appfabric/ee677272(v=azure.10))</span></span>
