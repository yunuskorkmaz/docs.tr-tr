---
title: 'Nasıl yapılır: WorkflowServiceHost ile Kalıcılığı Yapılandırma'
ms.date: 03/30/2017
ms.assetid: e31cd4df-13a3-4a9a-9be8-5243e0055356
ms.openlocfilehash: b8839f42a9b8b5f4da0a1a8364c7eac5a4c06d4e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61699779"
---
# <a name="how-to-configure-persistence-with-workflowservicehost"></a><span data-ttu-id="614d0-102">Nasıl yapılır: WorkflowServiceHost ile Kalıcılığı Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="614d0-102">How to: Configure Persistence with WorkflowServiceHost</span></span>
<span data-ttu-id="614d0-103">Bu konu, barındırılan iş akışları için kalıcılığını sağlamak için SQL iş akışı örneği Store özelliği yapılandırmayı açıklar <xref:System.ServiceModel.Activities.WorkflowServiceHost> bir yapılandırma dosyası kullanarak.</span><span class="sxs-lookup"><span data-stu-id="614d0-103">This topic describes how to configure the SQL Workflow Instance Store feature to enable persistence for workflows hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost> by using a configuration file.</span></span> <span data-ttu-id="614d0-104">SQL iş akışı örneği Store özelliği kullanmadan önce iş akışı örneği kalıcı hale getirmek için kullanılan bir SQL veritabanı oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="614d0-104">Before using the SQL Workflow Instance Store feature you must create a SQL database that is used to persist workflow instances.</span></span> <span data-ttu-id="614d0-105">Daha fazla bilgi için [nasıl yapılır: İş akışları ve iş akışı hizmetleri için SQL kalıcılığını](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="614d0-105">For more information, see [How to: Enable SQL Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span></span>  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-configuration"></a><span data-ttu-id="614d0-106">SQL iş akışı örneği Store yapılandırmasında yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="614d0-106">To Configure the SQL Workflow Instance Store in Configuration</span></span>  
  
1. <span data-ttu-id="614d0-107">SQL iş akışı örnek deposunun özellikleri aracılığıyla yapılandırılabilir <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, bir hizmet davranışını ayarlar XML yapılandırması üzerinden değiştirilmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="614d0-107">The properties of the SQL workflow instance store can be configured through the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, a service behavior that allows you to change the settings through XML configuration.</span></span> <span data-ttu-id="614d0-108">Aşağıdaki yapılandırma örnek kullanan SQL iş akışı örnek deposu yapılandırma işlemi gösterilmektedir <`sqlWorkflowInstanceStore`> yapılandırma dosyasında bir davranış öğesi.</span><span class="sxs-lookup"><span data-stu-id="614d0-108">The following configuration example shows how to configure the SQL workflow instance store by using the <`sqlWorkflowInstanceStore`> behavior element in a configuration file.</span></span>  
  
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
  
     <span data-ttu-id="614d0-109">SQL iş akışı örnek deposu yapılandırma hakkında daha fazla bilgi için bkz. [nasıl yapılır: İş akışları ve iş akışı hizmetleri için SQL kalıcılığını](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="614d0-109">For more information about how to configure the SQL workflow instance store, see [How to: Enable SQL Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span></span> <span data-ttu-id="614d0-110">İçin bireysel ayarlar hakkında daha fazla bilgi için <`sqlWorkflowInstanceStore`> davranış öğesi bkz [SQL iş akışı örneği Store](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).</span><span class="sxs-lookup"><span data-stu-id="614d0-110">For more information about the individual settings for the <`sqlWorkflowInstanceStore`> behavior element, see [SQL Workflow Instance Store](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).</span></span> <span data-ttu-id="614d0-111">Windows Server App Fabric kendi sürdürme deposundan sağlar.</span><span class="sxs-lookup"><span data-stu-id="614d0-111">Windows Server App Fabric provides its own persistence store.</span></span> <span data-ttu-id="614d0-112">Daha fazla bilgi için [Windows Server App Fabric Kalıcılık](https://go.microsoft.com/fwlink/?LinkId=193121).</span><span class="sxs-lookup"><span data-stu-id="614d0-112">For more information, see [Windows Server App Fabric Persistence](https://go.microsoft.com/fwlink/?LinkId=193121).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="614d0-113">Basitleştirilmiş yapılandırma önceki yapılandırma örneği kullanır.</span><span class="sxs-lookup"><span data-stu-id="614d0-113">The preceding configuration example uses simplified configuration.</span></span> <span data-ttu-id="614d0-114">Daha fazla bilgi için [Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/simplified-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="614d0-114">For more information, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md)</span></span>  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-code"></a><span data-ttu-id="614d0-115">SQL iş akışı örneği Store kodda yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="614d0-115">To Configure the SQL Workflow Instance Store in Code</span></span>  
  
1. <span data-ttu-id="614d0-116">SQL iş akışı örnek deposunun özellikleri aracılığıyla yapılandırılabilir <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, kod aracılığıyla ayarlarını değiştirmenize olanak sağlayan bir hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="614d0-116">The properties of the SQL workflow instance store can be configured through the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, a service behavior that allows you to change the settings through code.</span></span> <span data-ttu-id="614d0-117">Aşağıdaki örnek, SQL iş akışı örnek deposu kullanarak yapılandırma işlemi gösterilmektedir <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> kodu davranış öğesi</span><span class="sxs-lookup"><span data-stu-id="614d0-117">The following example shows how to configure the SQL workflow instance store by using the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> behavior element in a code</span></span>  
  
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
  
     <span data-ttu-id="614d0-118">SQL iş akışı örnek deposu yapılandırma hakkında daha fazla bilgi için bkz. [nasıl yapılır: İş akışları ve iş akışı hizmetleri için SQL kalıcılığını](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="614d0-118">For more information about how to configure the SQL workflow instance store, see [How to: Enable SQL Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span></span> <span data-ttu-id="614d0-119">İçin bireysel ayarlar hakkında daha fazla bilgi için <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> davranış öğesi bkz [SQL iş akışı örneği Store](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).</span><span class="sxs-lookup"><span data-stu-id="614d0-119">For more information about the individual settings for the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> behavior element, see [SQL Workflow Instance Store](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).</span></span> <span data-ttu-id="614d0-120">Windows Server App Fabric kendi sürdürme deposundan sağlar.</span><span class="sxs-lookup"><span data-stu-id="614d0-120">Windows Server App Fabric provides its own persistence store.</span></span> <span data-ttu-id="614d0-121">Daha fazla bilgi için [Windows Server App Fabric Kalıcılık](https://go.microsoft.com/fwlink/?LinkId=193121).</span><span class="sxs-lookup"><span data-stu-id="614d0-121">For more information, see [Windows Server App Fabric Persistence](https://go.microsoft.com/fwlink/?LinkId=193121).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="614d0-122">Basitleştirilmiş yapılandırma önceki yapılandırma örneği kullanır.</span><span class="sxs-lookup"><span data-stu-id="614d0-122">The preceding configuration example uses simplified configuration.</span></span> <span data-ttu-id="614d0-123">Daha fazla bilgi için [Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/simplified-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="614d0-123">For more information, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md)</span></span>  
  
     <span data-ttu-id="614d0-124">Program aracılığıyla kalıcılığı yapılandırma örneği için bkz. [nasıl yapılır: İş akışları ve iş akışı hizmetleri için kalıcılığı etkinleştir](../../../../docs/framework/windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="614d0-124">For an example of how to configure persistence programmatically see [How to: Enable Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="614d0-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="614d0-125">See also</span></span>

- [<span data-ttu-id="614d0-126">İş Akışı Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="614d0-126">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [<span data-ttu-id="614d0-127">İş Akışı Kalıcılığı</span><span class="sxs-lookup"><span data-stu-id="614d0-127">Workflow Persistence</span></span>](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md)
- [<span data-ttu-id="614d0-128">Windows Server AppFabric kalıcılığı</span><span class="sxs-lookup"><span data-stu-id="614d0-128">Windows Server App Fabric Persistence</span></span>](https://go.microsoft.com/fwlink/?LinkId=193121)
