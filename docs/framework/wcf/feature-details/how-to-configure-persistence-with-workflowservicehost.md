---
title: 'Nasıl yapılır: WorkflowServiceHost ile Kalıcılığı Yapılandırma'
ms.date: 03/30/2017
ms.assetid: e31cd4df-13a3-4a9a-9be8-5243e0055356
ms.openlocfilehash: 7b65b89db674a624f7dfbf8ca816e0f0c2d2ff80
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/15/2020
ms.locfileid: "75963475"
---
# <a name="how-to-configure-persistence-with-workflowservicehost"></a><span data-ttu-id="b24ce-102">Nasıl yapılır: WorkflowServiceHost ile Kalıcılığı Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b24ce-102">How to: Configure Persistence with WorkflowServiceHost</span></span>
<span data-ttu-id="b24ce-103">Bu konuda, bir yapılandırma dosyası kullanarak <xref:System.ServiceModel.Activities.WorkflowServiceHost> içinde barındırılan iş akışları için kalıcılığı etkinleştirmek üzere SQL Workflow örnek deposu özelliğinin nasıl yapılandırılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b24ce-103">This topic describes how to configure the SQL Workflow Instance Store feature to enable persistence for workflows hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost> by using a configuration file.</span></span> <span data-ttu-id="b24ce-104">SQL Iş akışı örnek deposu özelliğini kullanmadan önce, iş akışı örneklerini kalıcı hale getirmek için kullanılan bir SQL veritabanı oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b24ce-104">Before using the SQL Workflow Instance Store feature you must create a SQL database that is used to persist workflow instances.</span></span> <span data-ttu-id="b24ce-105">Daha fazla bilgi için bkz. [nasıl yapılır: Iş akışları ve Iş akışı hizmetleri IÇIN SQL kalıcılığını etkinleştirme](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="b24ce-105">For more information, see [How to: Enable SQL Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span></span>  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-configuration"></a><span data-ttu-id="b24ce-106">Yapılandırmada SQL Iş akışı örnek deposunu yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="b24ce-106">To Configure the SQL Workflow Instance Store in Configuration</span></span>  
  
1. <span data-ttu-id="b24ce-107">SQL iş akışı örneği deposunun özellikleri, ayarları XML yapılandırması aracılığıyla değiştirmenize olanak tanıyan bir hizmet davranışı olan <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>aracılığıyla yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="b24ce-107">The properties of the SQL workflow instance store can be configured through the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, a service behavior that allows you to change the settings through XML configuration.</span></span> <span data-ttu-id="b24ce-108">Aşağıdaki yapılandırma örneği, bir yapılandırma dosyasında <`sqlWorkflowInstanceStore`> davranış öğesi kullanılarak SQL iş akışı örnek deposunun nasıl yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b24ce-108">The following configuration example shows how to configure the SQL workflow instance store by using the <`sqlWorkflowInstanceStore`> behavior element in a configuration file.</span></span>  
  
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
            <sqlWorkflowInstanceStore/>  
        </behavior>  
    </serviceBehaviors>  
    ```  
  
     <span data-ttu-id="b24ce-109">SQL iş akışı örnek deposunun nasıl yapılandırılacağı hakkında daha fazla bilgi için bkz. [nasıl yapılır: Iş akışları ve Iş akışı hizmetleri IÇIN SQL kalıcılığını etkinleştirme](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="b24ce-109">For more information about how to configure the SQL workflow instance store, see [How to: Enable SQL Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span></span> <span data-ttu-id="b24ce-110">`sqlWorkflowInstanceStore`> davranış öğesi için bireysel ayarlar hakkında daha fazla bilgi için bkz. [SQL Workflow örnek deposu](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).</span><span class="sxs-lookup"><span data-stu-id="b24ce-110">For more information about the individual settings for the <`sqlWorkflowInstanceStore`> behavior element, see [SQL Workflow Instance Store](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).</span></span> <span data-ttu-id="b24ce-111">Windows Server App Fabric kendi Kalıcılık mağazasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="b24ce-111">Windows Server App Fabric provides its own persistence store.</span></span> <span data-ttu-id="b24ce-112">Daha fazla bilgi için bkz. [Windows Server App Fabric kalıcılığı](https://docs.microsoft.com/previous-versions/appfabric/ee677272(v=azure.10)).</span><span class="sxs-lookup"><span data-stu-id="b24ce-112">For more information, see [Windows Server App Fabric Persistence](https://docs.microsoft.com/previous-versions/appfabric/ee677272(v=azure.10)).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="b24ce-113">Önceki yapılandırma örneği Basitleştirilmiş yapılandırma kullanır.</span><span class="sxs-lookup"><span data-stu-id="b24ce-113">The preceding configuration example uses simplified configuration.</span></span> <span data-ttu-id="b24ce-114">Daha fazla bilgi için bkz. [Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/simplified-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="b24ce-114">For more information, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md)</span></span>  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-code"></a><span data-ttu-id="b24ce-115">SQL Iş akışı örnek deposunu kodda yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="b24ce-115">To Configure the SQL Workflow Instance Store in Code</span></span>  
  
1. <span data-ttu-id="b24ce-116">SQL iş akışı örneği deposunun özellikleri, ayarları kod aracılığıyla değiştirmenize olanak tanıyan bir hizmet davranışı olan <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>aracılığıyla yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="b24ce-116">The properties of the SQL workflow instance store can be configured through the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, a service behavior that allows you to change the settings through code.</span></span> <span data-ttu-id="b24ce-117">Aşağıdaki örnek, bir koddaki <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> Behavior öğesi kullanılarak SQL iş akışı örnek deposunun nasıl yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b24ce-117">The following example shows how to configure the SQL workflow instance store by using the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> behavior element in a code</span></span>  
  
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
  
     <span data-ttu-id="b24ce-118">SQL iş akışı örnek deposunun nasıl yapılandırılacağı hakkında daha fazla bilgi için bkz. [nasıl yapılır: Iş akışları ve Iş akışı hizmetleri IÇIN SQL kalıcılığını etkinleştirme](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="b24ce-118">For more information about how to configure the SQL workflow instance store, see [How to: Enable SQL Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span></span> <span data-ttu-id="b24ce-119"><xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> davranış öğesinin bireysel ayarları hakkında daha fazla bilgi için bkz. [SQL Workflow örnek deposu](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).</span><span class="sxs-lookup"><span data-stu-id="b24ce-119">For more information about the individual settings for the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> behavior element, see [SQL Workflow Instance Store](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).</span></span> <span data-ttu-id="b24ce-120">Windows Server App Fabric kendi Kalıcılık mağazasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="b24ce-120">Windows Server App Fabric provides its own persistence store.</span></span> <span data-ttu-id="b24ce-121">Daha fazla bilgi için bkz. [Windows Server App Fabric kalıcılığı](https://docs.microsoft.com/previous-versions/appfabric/ee677272(v=azure.10)).</span><span class="sxs-lookup"><span data-stu-id="b24ce-121">For more information, see [Windows Server App Fabric Persistence](https://docs.microsoft.com/previous-versions/appfabric/ee677272(v=azure.10)).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="b24ce-122">Önceki yapılandırma örneği Basitleştirilmiş yapılandırma kullanır.</span><span class="sxs-lookup"><span data-stu-id="b24ce-122">The preceding configuration example uses simplified configuration.</span></span> <span data-ttu-id="b24ce-123">Daha fazla bilgi için bkz. [Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/simplified-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="b24ce-123">For more information, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md)</span></span>  
  
     <span data-ttu-id="b24ce-124">Kalıcılığın nasıl yapılandırılacağı hakkında bir örnek için bkz. [nasıl yapılır: Iş akışları ve Iş akışı hizmetleri Için kalıcılığı etkinleştirme](../../../../docs/framework/windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="b24ce-124">For an example of how to configure persistence programmatically see [How to: Enable Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b24ce-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b24ce-125">See also</span></span>

- [<span data-ttu-id="b24ce-126">İş Akışı Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="b24ce-126">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [<span data-ttu-id="b24ce-127">İş Akışı Kalıcılığı</span><span class="sxs-lookup"><span data-stu-id="b24ce-127">Workflow Persistence</span></span>](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md)
- <span data-ttu-id="b24ce-128">[Windows Server App Fabric kalıcılığı](https://docs.microsoft.com/previous-versions/appfabric/ee677272(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="b24ce-128">[Windows Server App Fabric Persistence](https://docs.microsoft.com/previous-versions/appfabric/ee677272(v=azure.10))</span></span>
