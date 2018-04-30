---
title: 'Nasıl yapılır: WorkflowServiceHost ile Kalıcılığı Yapılandırma'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e31cd4df-13a3-4a9a-9be8-5243e0055356
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: de177180dc22fc3236924da691cf9b1f594519ce
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-configure-persistence-with-workflowservicehost"></a><span data-ttu-id="3281e-102">Nasıl yapılır: WorkflowServiceHost ile Kalıcılığı Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="3281e-102">How to: Configure Persistence with WorkflowServiceHost</span></span>
<span data-ttu-id="3281e-103">Bu konu, iş akışları barındırılan için Kalıcılık etkinleştirmek için SQL iş akışı örneği depolama özelliğini yapılandırmak açıklar <xref:System.ServiceModel.Activities.WorkflowServiceHost> bir yapılandırma dosyası kullanarak.</span><span class="sxs-lookup"><span data-stu-id="3281e-103">This topic describes how to configure the SQL Workflow Instance Store feature to enable persistence for workflows hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost> by using a configuration file.</span></span> <span data-ttu-id="3281e-104">SQL iş akışı örneği deposuna özelliği kullanmadan önce iş akışı örnekleri sürdürmek için kullanılan bir SQL veritabanı oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3281e-104">Before using the SQL Workflow Instance Store feature you must create a SQL database that is used to persist workflow instances.</span></span> <span data-ttu-id="3281e-105">Daha fazla bilgi için bkz: [nasıl yapılır: iş akışları ve iş akışı hizmetleri için SQL kalıcılığını etkinleştirmek](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="3281e-105">For more information, see [How to: Enable SQL Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span></span>  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-configuration"></a><span data-ttu-id="3281e-106">Yapılandırmada SQL iş akışı örneği deposunu yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="3281e-106">To Configure the SQL Workflow Instance Store in Configuration</span></span>  
  
1.  <span data-ttu-id="3281e-107">SQL iş akışı örneği deposunun özelliklerini aracılığıyla yapılandırılabilir <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, XML yapılandırma ayarlarıyla değiştirmenize izin verir hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="3281e-107">The properties of the SQL workflow instance store can be configured through the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, a service behavior that allows you to change the settings through XML configuration.</span></span> <span data-ttu-id="3281e-108">Aşağıdaki yapılandırma örneği kullanarak SQL iş akışı örneği deposuna yapılandırmak gösterilmiştir <`sqlWorkflowInstanceStore`> davranışı öğesi bir yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="3281e-108">The following configuration example shows how to configure the SQL workflow instance store by using the <`sqlWorkflowInstanceStore`> behavior element in a configuration file.</span></span>  
  
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
  
     <span data-ttu-id="3281e-109">SQL iş akışı örneği depolama yapılandırma hakkında daha fazla bilgi için bkz: [nasıl yapılır: iş akışları ve iş akışı hizmetleri için SQL kalıcılığını etkinleştirmek](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="3281e-109">For more information about how to configure the SQL workflow instance store, see [How to: Enable SQL Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span></span> <span data-ttu-id="3281e-110">İçin bireysel ayarlar hakkında daha fazla bilgi için <`sqlWorkflowInstanceStore`> davranışı öğesi bkz [SQL iş akışı örneği deposuna](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).</span><span class="sxs-lookup"><span data-stu-id="3281e-110">For more information about the individual settings for the <`sqlWorkflowInstanceStore`> behavior element, see [SQL Workflow Instance Store](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).</span></span> <span data-ttu-id="3281e-111">Windows Server App Fabric kendi Kalıcılık deposuna sağlar.</span><span class="sxs-lookup"><span data-stu-id="3281e-111">Windows Server App Fabric provides its own persistence store.</span></span> <span data-ttu-id="3281e-112">Daha fazla bilgi için bkz: [Windows Server App Fabric kalıcılığı](http://go.microsoft.com/fwlink/?LinkId=193121).</span><span class="sxs-lookup"><span data-stu-id="3281e-112">For more information, see [Windows Server App Fabric Persistence](http://go.microsoft.com/fwlink/?LinkId=193121).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3281e-113">Önceki yapılandırma örneği Basitleştirilmiş yapılandırmasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="3281e-113">The preceding configuration example uses simplified configuration.</span></span> <span data-ttu-id="3281e-114">Daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/simplified-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="3281e-114">For more information, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md)</span></span>  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-code"></a><span data-ttu-id="3281e-115">SQL iş akışı örneği deposu yapılandırma</span><span class="sxs-lookup"><span data-stu-id="3281e-115">To Configure the SQL Workflow Instance Store in Code</span></span>  
  
1.  <span data-ttu-id="3281e-116">SQL iş akışı örneği deposunun özelliklerini aracılığıyla yapılandırılabilir <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, kod aracılığıyla ayarlarını değiştirmenizi sağlar hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="3281e-116">The properties of the SQL workflow instance store can be configured through the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, a service behavior that allows you to change the settings through code.</span></span> <span data-ttu-id="3281e-117">Aşağıdaki örnek SQL iş akışı örneği deposuna kullanarak yapılandırmak nasıl gösterir <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> kodu davranışı öğesi</span><span class="sxs-lookup"><span data-stu-id="3281e-117">The following example shows how to configure the SQL workflow instance store by using the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> behavior element in a code</span></span>  
  
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
  
     <span data-ttu-id="3281e-118">SQL iş akışı örneği depolama yapılandırma hakkında daha fazla bilgi için bkz: [nasıl yapılır: iş akışları ve iş akışı hizmetleri için SQL kalıcılığını etkinleştirmek](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="3281e-118">For more information about how to configure the SQL workflow instance store, see [How to: Enable SQL Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span></span> <span data-ttu-id="3281e-119">İçin bireysel ayarlar hakkında daha fazla bilgi için <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> davranışı öğesi bkz [SQL iş akışı örneği deposuna](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).</span><span class="sxs-lookup"><span data-stu-id="3281e-119">For more information about the individual settings for the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> behavior element, see [SQL Workflow Instance Store](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).</span></span> <span data-ttu-id="3281e-120">Windows Server App Fabric kendi Kalıcılık deposuna sağlar.</span><span class="sxs-lookup"><span data-stu-id="3281e-120">Windows Server App Fabric provides its own persistence store.</span></span> <span data-ttu-id="3281e-121">Daha fazla bilgi için bkz: [Windows Server App Fabric kalıcılığı](http://go.microsoft.com/fwlink/?LinkId=193121).</span><span class="sxs-lookup"><span data-stu-id="3281e-121">For more information, see [Windows Server App Fabric Persistence](http://go.microsoft.com/fwlink/?LinkId=193121).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3281e-122">Önceki yapılandırma örneği Basitleştirilmiş yapılandırmasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="3281e-122">The preceding configuration example uses simplified configuration.</span></span> <span data-ttu-id="3281e-123">Daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/simplified-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="3281e-123">For more information, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md)</span></span>  
  
     <span data-ttu-id="3281e-124">Program aracılığıyla kalıcılığı yapılandırma örneği için bkz: [nasıl yapılır: iş akışları ve iş akışı hizmetleri kalıcılığı etkinleştir](../../../../docs/framework/windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="3281e-124">For an example of how to configure persistence programmatically see [How to: Enable Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3281e-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3281e-125">See Also</span></span>  
 [<span data-ttu-id="3281e-126">İş Akışı Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="3281e-126">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [<span data-ttu-id="3281e-127">İş Akışı Kalıcılığı</span><span class="sxs-lookup"><span data-stu-id="3281e-127">Workflow Persistence</span></span>](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md)  
 [<span data-ttu-id="3281e-128">Windows Server App Fabric kalıcılığı</span><span class="sxs-lookup"><span data-stu-id="3281e-128">Windows Server App Fabric Persistence</span></span>](http://go.microsoft.com/fwlink/?LinkId=193121)
