---
title: 'Nasıl yapılır: WorkflowServiceHost ile Kalıcılığı Yapılandırma'
ms.date: 03/30/2017
ms.assetid: e31cd4df-13a3-4a9a-9be8-5243e0055356
ms.openlocfilehash: 93397923154d780ed3b714bf0bb95c15bc71bbfb
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556316"
---
# <a name="how-to-configure-persistence-with-workflowservicehost"></a><span data-ttu-id="f564b-102">Nasıl yapılır: WorkflowServiceHost ile Kalıcılığı Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="f564b-102">How to: Configure Persistence with WorkflowServiceHost</span></span>
<span data-ttu-id="f564b-103">Bu konuda, <xref:System.ServiceModel.Activities.WorkflowServiceHost> bir yapılandırma dosyası kullanılarak içinde barındırılan iş akışları için kalıcılığı etkinleştirmek üzere SQL Iş akışı örnek deposu özelliğinin nasıl yapılandırılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f564b-103">This topic describes how to configure the SQL Workflow Instance Store feature to enable persistence for workflows hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost> by using a configuration file.</span></span> <span data-ttu-id="f564b-104">SQL Iş akışı örnek deposu özelliğini kullanmadan önce, iş akışı örneklerini kalıcı hale getirmek için kullanılan bir SQL veritabanı oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f564b-104">Before using the SQL Workflow Instance Store feature you must create a SQL database that is used to persist workflow instances.</span></span> <span data-ttu-id="f564b-105">Daha fazla bilgi için bkz. [nasıl yapılır: Iş akışları ve Iş akışı hizmetleri IÇIN SQL kalıcılığını etkinleştirme](../../windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="f564b-105">For more information, see [How to: Enable SQL Persistence for Workflows and Workflow Services](../../windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span></span>  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-configuration"></a><span data-ttu-id="f564b-106">Yapılandırmada SQL Iş akışı örnek deposunu yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="f564b-106">To Configure the SQL Workflow Instance Store in Configuration</span></span>  
  
1. <span data-ttu-id="f564b-107">SQL iş akışı örnek deposunun özellikleri, <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> ayarları XML yapılandırması aracılığıyla değiştirmenize olanak tanıyan bir hizmet davranışı aracılığıyla yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="f564b-107">The properties of the SQL workflow instance store can be configured through the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, a service behavior that allows you to change the settings through XML configuration.</span></span> <span data-ttu-id="f564b-108">Aşağıdaki yapılandırma örneği, `sqlWorkflowInstanceStore` bir yapılandırma dosyasında <> Behavior öğesi KULLANıLARAK SQL iş akışı örnek deposunun nasıl yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f564b-108">The following configuration example shows how to configure the SQL workflow instance store by using the <`sqlWorkflowInstanceStore`> behavior element in a configuration file.</span></span>  
  
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
  
     <span data-ttu-id="f564b-109">SQL iş akışı örnek deposunun nasıl yapılandırılacağı hakkında daha fazla bilgi için bkz. [nasıl yapılır: Iş akışları ve Iş akışı hizmetleri IÇIN SQL kalıcılığını etkinleştirme](../../windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="f564b-109">For more information about how to configure the SQL workflow instance store, see [How to: Enable SQL Persistence for Workflows and Workflow Services](../../windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span></span> <span data-ttu-id="f564b-110"><> davranış öğesinin bireysel ayarları hakkında daha fazla bilgi için `sqlWorkflowInstanceStore` bkz. [SQL Workflow örnek deposu](../../windows-workflow-foundation/sql-workflow-instance-store.md).</span><span class="sxs-lookup"><span data-stu-id="f564b-110">For more information about the individual settings for the <`sqlWorkflowInstanceStore`> behavior element, see [SQL Workflow Instance Store](../../windows-workflow-foundation/sql-workflow-instance-store.md).</span></span> <span data-ttu-id="f564b-111">Windows Server App Fabric kendi Kalıcılık mağazasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="f564b-111">Windows Server App Fabric provides its own persistence store.</span></span> <span data-ttu-id="f564b-112">Daha fazla bilgi için bkz. [Windows Server App Fabric kalıcılığı](/previous-versions/appfabric/ee677272(v=azure.10)).</span><span class="sxs-lookup"><span data-stu-id="f564b-112">For more information, see [Windows Server App Fabric Persistence](/previous-versions/appfabric/ee677272(v=azure.10)).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="f564b-113">Önceki yapılandırma örneği Basitleştirilmiş yapılandırma kullanır.</span><span class="sxs-lookup"><span data-stu-id="f564b-113">The preceding configuration example uses simplified configuration.</span></span> <span data-ttu-id="f564b-114">Daha fazla bilgi için bkz. [Basitleştirilmiş yapılandırma](../simplified-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="f564b-114">For more information, see [Simplified Configuration](../simplified-configuration.md)</span></span>  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-code"></a><span data-ttu-id="f564b-115">SQL Iş akışı örnek deposunu kodda yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="f564b-115">To Configure the SQL Workflow Instance Store in Code</span></span>  
  
1. <span data-ttu-id="f564b-116">SQL iş akışı örnek deposunun özellikleri, <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> ayarları kod aracılığıyla değiştirmenize olanak tanıyan bir hizmet davranışı aracılığıyla yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="f564b-116">The properties of the SQL workflow instance store can be configured through the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, a service behavior that allows you to change the settings through code.</span></span> <span data-ttu-id="f564b-117">Aşağıdaki örnek, <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> bir koddaki davranış öğesi KULLANıLARAK SQL iş akışı örnek deposunun nasıl yapılandırılacağını gösterir</span><span class="sxs-lookup"><span data-stu-id="f564b-117">The following example shows how to configure the SQL workflow instance store by using the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> behavior element in a code</span></span>  
  
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
  
     <span data-ttu-id="f564b-118">SQL iş akışı örnek deposunun nasıl yapılandırılacağı hakkında daha fazla bilgi için bkz. [nasıl yapılır: Iş akışları ve Iş akışı hizmetleri IÇIN SQL kalıcılığını etkinleştirme](../../windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="f564b-118">For more information about how to configure the SQL workflow instance store, see [How to: Enable SQL Persistence for Workflows and Workflow Services](../../windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span></span> <span data-ttu-id="f564b-119">Davranış öğesinin bireysel ayarları hakkında daha fazla bilgi için <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> bkz. [SQL Workflow örnek deposu](../../windows-workflow-foundation/sql-workflow-instance-store.md).</span><span class="sxs-lookup"><span data-stu-id="f564b-119">For more information about the individual settings for the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> behavior element, see [SQL Workflow Instance Store](../../windows-workflow-foundation/sql-workflow-instance-store.md).</span></span> <span data-ttu-id="f564b-120">Windows Server App Fabric kendi Kalıcılık mağazasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="f564b-120">Windows Server App Fabric provides its own persistence store.</span></span> <span data-ttu-id="f564b-121">Daha fazla bilgi için bkz. [Windows Server App Fabric kalıcılığı](/previous-versions/appfabric/ee677272(v=azure.10)).</span><span class="sxs-lookup"><span data-stu-id="f564b-121">For more information, see [Windows Server App Fabric Persistence](/previous-versions/appfabric/ee677272(v=azure.10)).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="f564b-122">Önceki yapılandırma örneği Basitleştirilmiş yapılandırma kullanır.</span><span class="sxs-lookup"><span data-stu-id="f564b-122">The preceding configuration example uses simplified configuration.</span></span> <span data-ttu-id="f564b-123">Daha fazla bilgi için bkz. [Basitleştirilmiş yapılandırma](../simplified-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="f564b-123">For more information, see [Simplified Configuration](../simplified-configuration.md)</span></span>  
  
     <span data-ttu-id="f564b-124">Kalıcılığın nasıl yapılandırılacağı hakkında bir örnek için bkz. [nasıl yapılır: Iş akışları ve Iş akışı hizmetleri Için kalıcılığı etkinleştirme](../../windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="f564b-124">For an example of how to configure persistence programmatically see [How to: Enable Persistence for Workflows and Workflow Services](../../windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f564b-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f564b-125">See also</span></span>

- [<span data-ttu-id="f564b-126">İş Akışı Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="f564b-126">Workflow Services</span></span>](workflow-services.md)
- [<span data-ttu-id="f564b-127">İş Akışı Kalıcılığı</span><span class="sxs-lookup"><span data-stu-id="f564b-127">Workflow Persistence</span></span>](../../windows-workflow-foundation/workflow-persistence.md)
- <span data-ttu-id="f564b-128">[Windows Server App Fabric kalıcılığı](/previous-versions/appfabric/ee677272(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="f564b-128">[Windows Server App Fabric Persistence](/previous-versions/appfabric/ee677272(v=azure.10))</span></span>
