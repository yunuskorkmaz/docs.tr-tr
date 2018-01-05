---
title: "Nasıl yapılır: iş akışları ve iş akışı hizmetleri için SQL kalıcılığı etkinleştir"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: ca7bf77f-3e5d-4b23-b17a-d0b60f46411d
caps.latest.revision: "36"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 60fac3cba4da35b5146f777abd912ad15f0f29eb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-enable-sql-persistence-for-workflows-and-workflow-services"></a><span data-ttu-id="dadd3-102">Nasıl yapılır: iş akışları ve iş akışı hizmetleri için SQL kalıcılığı etkinleştir</span><span class="sxs-lookup"><span data-stu-id="dadd3-102">How to: Enable SQL Persistence for Workflows and Workflow Services</span></span>
<span data-ttu-id="dadd3-103">Bu konuda, iş akışlarınızı kalıcılığını etkinleştirmek için SQL iş akışı örneği deposuna özelliği yapılandırmayı açıklar ve iş akışı her ikisi de program aracılığıyla bir yapılandırma dosyası kullanarak hizmetleri ve.</span><span class="sxs-lookup"><span data-stu-id="dadd3-103">This topic describes how to configure the SQL Workflow Instance Store feature to enable persistence for your workflows and workflow services both programmatically and by using a configuration file.</span></span>  
  
 <span data-ttu-id="dadd3-104">Windows Server App Fabric kalıcılığı yapılandırma işlemini basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="dadd3-104">Windows Server App Fabric simplifies the process of configuring persistence.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="dadd3-105">[App Fabric kalıcılığı yapılandırma](http://go.microsoft.com/fwlink/?LinkId=201204)</span><span class="sxs-lookup"><span data-stu-id="dadd3-105"> [App Fabric Persistence Configuration](http://go.microsoft.com/fwlink/?LinkId=201204)</span></span>  
  
 <span data-ttu-id="dadd3-106">SQL iş akışı örneği depolama özelliğini kullanmadan önce iş akışı örnekleri kalıcı hale getirmek için özelliğini kullanan bir veritabanı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="dadd3-106">Before using the SQL Workflow Instance Store feature, create a database that the feature uses to persist workflow instances.</span></span> <span data-ttu-id="dadd3-107">[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] Kurulum programı %WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN klasörüne SQL iş akışı örneği deposuna özelliğiyle ilişkili SQL komut dosyalarını kopyalar.</span><span class="sxs-lookup"><span data-stu-id="dadd3-107">The [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] set-up program copies SQL script files associated with the SQL Workflow Instance Store feature to the %WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN folder.</span></span> <span data-ttu-id="dadd3-108">Bu komut dosyaları, iş akışı örnekleri kalıcı hale getirmek için kullanılacak SQL iş akışı örneği deposu istediğiniz SQL Server 2005 veya SQL Server 2008 veritabanına karşı çalışırlar.</span><span class="sxs-lookup"><span data-stu-id="dadd3-108">Run these script files against a SQL Server 2005 or SQL Server 2008 database that you want the SQL Workflow Instance Store to use to persist workflow instances.</span></span> <span data-ttu-id="dadd3-109">İlk SqlWorkflowInstanceStoreSchema.sql dosyasını çalıştırın ve sonra SqlWorkflowInstanceStoreLogic.sql dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="dadd3-109">Run the SqlWorkflowInstanceStoreSchema.sql file first and then run the SqlWorkflowInstanceStoreLogic.sql file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dadd3-110">Yeni bir veritabanı için Kalıcılık veritabanını temizlemek için aşağıdaki sırayla %WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN betikleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="dadd3-110">To clean up the persistence database to have a fresh database, run the scripts in %WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN in the following order.</span></span>  
>   
>  1.  <span data-ttu-id="dadd3-111">SqlWorkflowInstanceStoreSchema.sql</span><span class="sxs-lookup"><span data-stu-id="dadd3-111">SqlWorkflowInstanceStoreSchema.sql</span></span>  
> 2.  <span data-ttu-id="dadd3-112">SqlWorkflowInstanceStoreLogic.sql</span><span class="sxs-lookup"><span data-stu-id="dadd3-112">SqlWorkflowInstanceStoreLogic.sql</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="dadd3-113">Kalıcılık veritabanı oluşturmazsanız, bir ana iş akışları kalıcı hale getirmek çalıştığında SQL iş akışı örneği depolama özelliğini aşağıdakine benzer bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="dadd3-113">If you do not create a persistence database, the SQL Workflow Instance Store feature throws an exception similar to the following one when a host tries to persist workflows.</span></span>  
>   
>  <span data-ttu-id="dadd3-114">System.Data.SqlClient.SqlException: saklı yordam 'System.Activities.DurableInstancing.CreateLockOwner' bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="dadd3-114">System.Data.SqlClient.SqlException: Could not find stored procedure 'System.Activities.DurableInstancing.CreateLockOwner'</span></span>  
  
 <span data-ttu-id="dadd3-115">Aşağıdaki bölümlerde, iş akışları ve iş akışı hizmetleri SQL iş akışı örneği deposunu kullanan kalıcılığını etkinleştirmek açıklar.</span><span class="sxs-lookup"><span data-stu-id="dadd3-115">The following sections describe how to enable persistence for workflows and workflow services using the SQL Workflow Instance Store.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="dadd3-116">SQL iş akışı örneği deposuna özelliklerini görmek [özellikleri SQL iş akışı örneği deposuna](../../../docs/framework/windows-workflow-foundation/properties-of-sql-workflow-instance-store.md).</span><span class="sxs-lookup"><span data-stu-id="dadd3-116"> properties of the SQL Workflow Instance Store, see [Properties of SQL Workflow Instance Store](../../../docs/framework/windows-workflow-foundation/properties-of-sql-workflow-instance-store.md).</span></span>  
  
## <a name="enabling-persistence-for-self-hosted-workflows-that-use-workflowapplication"></a><span data-ttu-id="dadd3-117">Kalıcılığı Self-Hosted WorkflowApplication kullanan iş akışları için etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="dadd3-117">Enabling Persistence for Self-Hosted Workflows that use WorkflowApplication</span></span>  
 <span data-ttu-id="dadd3-118">Kalıcılık kullanan kendi kendini barındıran iş akışları için etkinleştirebilirsiniz <xref:System.Activities.WorkflowApplication> kullanarak program aracılığıyla <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> nesne modeli.</span><span class="sxs-lookup"><span data-stu-id="dadd3-118">You can enable persistence for self-hosted workflows that use <xref:System.Activities.WorkflowApplication> programmatically by using the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> object model.</span></span> <span data-ttu-id="dadd3-119">Aşağıdaki yordam, bunu yapmak için adımları içerir.</span><span class="sxs-lookup"><span data-stu-id="dadd3-119">The following procedure contains steps to do this.</span></span>  
  
#### <a name="to-enable-persistence-for-self-hosted-workflows"></a><span data-ttu-id="dadd3-120">Kendini barındıran iş akışları kalıcılığını etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="dadd3-120">To enable persistence for self-hosted workflows</span></span>  
  
1.  <span data-ttu-id="dadd3-121">System.Activites.DurableInstancing.dll bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="dadd3-121">Add a reference to System.Activites.DurableInstancing.dll.</span></span>  
  
2.  <span data-ttu-id="dadd3-122">Aşağıdaki deyim kaynak dosyasının en üstte varolan "kullanarak" ifadeleri sonra ekleyin.</span><span class="sxs-lookup"><span data-stu-id="dadd3-122">Add the following statement at the top of the source file after the existing "using" statements.</span></span>  
  
    ```csharp  
    using System.Activities.DurableInstancing;  
    ```  
  
3.  <span data-ttu-id="dadd3-123">Oluşturmak bir <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> ve atayın <xref:System.Activities.WorkflowApplication.InstanceStore%2A> , <xref:System.Activities.WorkflowApplication> aşağıdaki kod örneğinde gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="dadd3-123">Construct a <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> and assign it to the <xref:System.Activities.WorkflowApplication.InstanceStore%2A> of the <xref:System.Activities.WorkflowApplication> as shown in the following code example.</span></span>  
  
    ```csharp  
    SqlWorkflowInstanceStore store =   
        new SqlWorkflowInstanceStore("Server=.\\SQLEXPRESS;Initial Catalog=Persistence;Integrated Security=SSPI");  
  
    WorkflowApplication wfApp =  
        new WorkflowApplication(new Workflow1());  
  
    wfApp.InstanceStore = store;  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="dadd3-124">Bağlantı dizesi sunucu adı SQL Server sürümüne bağlı olarak farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="dadd3-124">Depending on your edition of SQL Server, the connection string server name may be different.</span></span>  
  
4.  <span data-ttu-id="dadd3-125">Çağırma <xref:System.Activities.WorkflowApplication.Persist%2A> yöntemi <xref:System.Activities.WorkflowApplication> bir iş akışını sürdürmek için nesne veya <xref:System.Activities.WorkflowApplication.Unload%2A> kalıcı hale getirmek ve bir iş akışı kaldırma için yöntem.</span><span class="sxs-lookup"><span data-stu-id="dadd3-125">Invoke the <xref:System.Activities.WorkflowApplication.Persist%2A> method on the <xref:System.Activities.WorkflowApplication> object to persist a workflow, or <xref:System.Activities.WorkflowApplication.Unload%2A> method to persist and unload a workflow.</span></span> <span data-ttu-id="dadd3-126">Ayrıca işleyebilir <xref:System.Activities.WorkflowApplication.PersistableIdle%2A> olayı tarafından <xref:System.Activities.WorkflowApplication> nesne ve uygun döndürür (<xref:System.Activities.PersistableIdleAction.Persist> veya <xref:System.Activities.PersistableIdleAction.Unload>) üyesi <xref:System.Activities.PersistableIdleAction>.</span><span class="sxs-lookup"><span data-stu-id="dadd3-126">You can also handle the <xref:System.Activities.WorkflowApplication.PersistableIdle%2A> event raised by the <xref:System.Activities.WorkflowApplication> object and return appropriate (<xref:System.Activities.PersistableIdleAction.Persist> or <xref:System.Activities.PersistableIdleAction.Unload>) member of <xref:System.Activities.PersistableIdleAction>.</span></span>  
  
    ```csharp  
    wfApp.PersistableIdle = delegate(WorkflowApplicationIdleEventArgs e)  
    {  
        return PersistableIdleAction.Persist;  
    };  
    ```  
  
> [!NOTE]
>  <span data-ttu-id="dadd3-127">Bkz [bir iş akışı uygulaması kalıcı](../../../docs/framework/windows-workflow-foundation/samples/persisting-a-workflow-application.md) adresindeki örnek [kalıcılığı](../../../docs/framework/windows-workflow-foundation/samples/persistence.md) bir örneğini kullanarak da iş akışları kalıcılığını etkinleştirmek için <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>ve [nasıl yapılır: oluşturma ve uzun çalıştırma İş akışını çalıştıran](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md) adımında [başlangıç Öğreticisi](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md) adım adım yönergeler için.</span><span class="sxs-lookup"><span data-stu-id="dadd3-127">See the [Persisting a Workflow Application](../../../docs/framework/windows-workflow-foundation/samples/persisting-a-workflow-application.md) sample at [Persistence](../../../docs/framework/windows-workflow-foundation/samples/persistence.md) for an example of enabling persistence for workflows using the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, and the [How to: Create and Run a Long Running Workflow](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md) step of the [Getting Started Tutorial](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md) for step by step instructions.</span></span>  
  
## <a name="enabling-persistence-for-self-hosted-workflow-services-that-use-the-workflowservicehost"></a><span data-ttu-id="dadd3-128">WorkflowServiceHost kullanan Self-Hosted iş akışı hizmetleri kalıcılığını etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="dadd3-128">Enabling Persistence for Self-Hosted Workflow Services that use the WorkflowServiceHost</span></span>  
 <span data-ttu-id="dadd3-129">Kullanan kendi kendini barındıran iş akışı hizmetleri kalıcılığını etkinleştirebilirsiniz <xref:System.ServiceModel.WorkflowServiceHost> kullanarak program aracılığıyla <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> sınıfı veya <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="dadd3-129">You can enable persistence for self-hosted workflow services that use <xref:System.ServiceModel.WorkflowServiceHost> programmatically by using the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> class or the <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> class.</span></span>  
  
### <a name="using-the-sqlworkflowinstancestorebehavior-class"></a><span data-ttu-id="dadd3-130">SqlWorkflowInstanceStoreBehavior sınıfını kullanma</span><span class="sxs-lookup"><span data-stu-id="dadd3-130">Using the SqlWorkflowInstanceStoreBehavior Class</span></span>  
 <span data-ttu-id="dadd3-131">Aşağıdaki yordamı kullanmak için adımları içerir <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> kendini barındıran iş akışı hizmetleri kalıcılığını etkinleştirmek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="dadd3-131">The following procedure contains steps to use the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> class to enable persistence for self-hosted workflow services.</span></span>  
  
##### <a name="to-enable-persistence-using-sqlworkflowinstancestorebehavior"></a><span data-ttu-id="dadd3-132">Kalıcılığı SqlWorkflowInstanceStoreBehavior kullanarak etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="dadd3-132">To enable persistence using SqlWorkflowInstanceStoreBehavior</span></span>  
  
1.  <span data-ttu-id="dadd3-133">System.ServiceModel.dll bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="dadd3-133">Add a reference to the System.ServiceModel.dll.</span></span>  
  
2.  <span data-ttu-id="dadd3-134">Aşağıdaki deyim kaynak dosyasının en üstte varolan "kullanarak" ifadeleri sonra ekleyin.</span><span class="sxs-lookup"><span data-stu-id="dadd3-134">Add the following statement at the top of the source file after the existing "using" statements.</span></span>  
  
    ```csharp  
    using System.ServiceModel.Activities.Description;  
    ```  
  
3.  <span data-ttu-id="dadd3-135">Bir örneğini oluşturmak `WorkflowServiceHost` ve iş akışı hizmeti için uç nokta ekleyin.</span><span class="sxs-lookup"><span data-stu-id="dadd3-135">Create an instance of the `WorkflowServiceHost` and add endpoints for the workflow service.</span></span>  
  
    ```  
    WorkflowServiceHost host = new WorkflowServiceHost(new CountingWorkflow(), new Uri(hostBaseAddress));  
    host.AddServiceEndpoint("ICountingWorkflow", new BasicHttpBinding(), "");  
    ```  
  
4.  <span data-ttu-id="dadd3-136">Oluşturmak bir `SqlWorkflowInstanceStoreBehavior` nesne ve davranış nesnesinin özelliklerini ayarlamak için.</span><span class="sxs-lookup"><span data-stu-id="dadd3-136">Construct a `SqlWorkflowInstanceStoreBehavior` object and to set properties of the behavior object.</span></span>  
  
    ```csharp  
    SqlWorkflowInstanceStoreBehavior instanceStoreBehavior = new SqlWorkflowInstanceStoreBehavior(connectionString);  
    instanceStoreBehavior.HostLockRenewalPeriod = new TimeSpan(0, 0, 5);  
    instanceStoreBehavior.InstanceCompletionAction = InstanceCompletionAction.DeleteAll;  
    instanceStoreBehavior.InstanceLockedExceptionAction = InstanceLockedExceptionAction.AggressiveRetry;  
    instanceStoreBehavior.InstanceEncodingOption = InstanceEncodingOption.GZip;  
    instanceStoreBehavior.RunnableInstancesDetectionPeriod = new TimeSpan("00:00:02");  
    host.Description.Behaviors.Add(instanceStoreBehavior);  
    ```  
  
5.  <span data-ttu-id="dadd3-137">İş akışı hizmeti ana bilgisayarı açın.</span><span class="sxs-lookup"><span data-stu-id="dadd3-137">Open the workflow service host.</span></span>  
  
    ```vb  
    host.Open();  
    ```  
  
> [!IMPORTANT]
>  <span data-ttu-id="dadd3-138">Bkz: [yerleşik yapılandırma](../../../docs/framework/windows-workflow-foundation/samples/built-in-configuration.md) adresindeki örnek [kalıcılığı](../../../docs/framework/windows-workflow-foundation/samples/persistence.md) bir örneğini kullanarak iş akışı hizmetleri kalıcılığını etkinleştirmek için `SqlWorkflowInstanceStoreBehavior` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="dadd3-138">See the [Built-in Configuration](../../../docs/framework/windows-workflow-foundation/samples/built-in-configuration.md) sample at [Persistence](../../../docs/framework/windows-workflow-foundation/samples/persistence.md) for an example of enabling persistence for workflow services using the `SqlWorkflowInstanceStoreBehavior` class.</span></span>  
  
### <a name="using-the-durableinstancingoptions-property"></a><span data-ttu-id="dadd3-139">DurableInstancingOptions özelliğini kullanma</span><span class="sxs-lookup"><span data-stu-id="dadd3-139">Using the DurableInstancingOptions Property</span></span>  
 <span data-ttu-id="dadd3-140">Zaman `SqlWorkflowInstanceStoreBehavior` uygulanan `DurableInstancingOptions.InstanceStore` üzerinde `WorkflowServiceHost` ayarlanır `SqlWorkflowInstanceStore` yapılandırma değerlerini kullanılarak oluşturulan nesne.</span><span class="sxs-lookup"><span data-stu-id="dadd3-140">When the `SqlWorkflowInstanceStoreBehavior` is applied, the `DurableInstancingOptions.InstanceStore` on the `WorkflowServiceHost` is set to the `SqlWorkflowInstanceStore` object created using the configuration values.</span></span> <span data-ttu-id="dadd3-141">Program aracılığıyla ayarlamak için aynısını yapabilir <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> özelliği `WorkflowServiceHost` kullanmadan `SqlWorkflowInstanceStoreBehavior` sınıfı aşağıdaki kod örneğinde gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="dadd3-141">You can do the same programmatically to set the <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> property of the `WorkflowServiceHost` without using the `SqlWorkflowInstanceStoreBehavior` class as shown in the following code example.</span></span>  
  
```  
workflowServiceHost.DurableInstancingOptions.InstanceStore = sqlInstanceStoreObject;  
```  
  
## <a name="enabling-persistence-for-was-hosted-workflow-services-that-use-the-workflowservicehost-using-a-configuration-file"></a><span data-ttu-id="dadd3-142">Bir yapılandırma dosyası kullanarak WorkflowServiceHost kullanan WAS-Hosted iş akışı hizmetleri kalıcılığını etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="dadd3-142">Enabling Persistence for WAS-Hosted Workflow Services that use the WorkflowServiceHost using a Configuration File</span></span>  
 <span data-ttu-id="dadd3-143">Bir yapılandırma dosyası kullanarak kendini barındıran veya Windows İşlem Etkinleştirme hizmeti WAS barındırılan iş akışı hizmetleri kalıcılığını etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dadd3-143">You can enable persistence for self-hosted or Windows Process Activation Service (WAS)-hosted workflow services by using a configuration file.</span></span> <span data-ttu-id="dadd3-144">Kendini barındıran iş akışı Hizmetleri gibi bir iş akışı WAS barındırılan hizmet WorkflowServiceHost kullanır.</span><span class="sxs-lookup"><span data-stu-id="dadd3-144">A WAS-hosted workflow service uses the WorkflowServiceHost as the self-hosted workflow services do.</span></span>  
  
 <span data-ttu-id="dadd3-145">`SqlWorkflowInstanceStoreBehavior`, Uygun şekilde değiştirmenize olanak verir hizmet davranışı [SQL iş akışı örneği deposuna](../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md) XML yapılandırma yoluyla özellikleri.</span><span class="sxs-lookup"><span data-stu-id="dadd3-145">The `SqlWorkflowInstanceStoreBehavior`, a service behavior that allows you to conveniently change the [SQL Workflow Instance Store](../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md) properties through XML configuration.</span></span> <span data-ttu-id="dadd3-146">İş akışı WAS barındırılan hizmetler için Web.config dosyasını kullanın.</span><span class="sxs-lookup"><span data-stu-id="dadd3-146">For WAS-hosted workflow services, use the Web.config file.</span></span> <span data-ttu-id="dadd3-147">Aşağıdaki yapılandırma örneği kullanarak SQL iş akışı örneği deposuna yapılandırmak gösterilmiştir `sqlWorkflowInstanceStore` davranışı öğesi bir yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="dadd3-147">The following configuration example shows how to configure the SQL Workflow Instance Store by using the `sqlWorkflowInstanceStore` behavior element in a configuration file.</span></span>  
  
```xml  
<serviceBehaviors>  
    <behavior name="">  
        <sqlWorkflowInstanceStore   
                    connectionString="Data Source=(local);Initial Catalog=DefaultPersistenceProviderDb;Integrated Security=True;Async=true"  
                    instanceEncodingOption="GZip | None"  
                    instanceCompletionAction="DeleteAll | DeleteNothing"  
                    instanceLockedExceptionAction="NoRetry | BasicRetry |AggressiveRetry"  
                    hostLockRenewalPeriod="00:00:30"   
                    runnableInstancesDetectionPeriod="00:00:05">  
  
        <sqlWorkflowInstanceStore/>  
    </behavior>  
</serviceBehaviors>  
```  
  
 <span data-ttu-id="dadd3-148">İçin değerler ayarlamazsanız `connectionString` veya `connectionStringName` özelliği, SQL iş akışı örneği deposuna kullanan varsayılan bağlantı dizesi adlı `DefaultSqlWorkflowInstanceStoreConnectionString`.</span><span class="sxs-lookup"><span data-stu-id="dadd3-148">If you do not set values for the `connectionString` or the `connectionStringName` property, the SQL Workflow Instance Store uses the default named connection string `DefaultSqlWorkflowInstanceStoreConnectionString`.</span></span>  
  
 <span data-ttu-id="dadd3-149">Zaman `SqlWorkflowInstanceStoreBehavior` uygulanan `DurableInstancingOptions.InstanceStore` üzerinde `WorkflowServiceHost` ayarlanır `SqlWorkflowInstanceStore` yapılandırma değerlerini kullanılarak oluşturulan nesne.</span><span class="sxs-lookup"><span data-stu-id="dadd3-149">When the `SqlWorkflowInstanceStoreBehavior` is applied, the `DurableInstancingOptions.InstanceStore` on the `WorkflowServiceHost` is set to the `SqlWorkflowInstanceStore` object created using the configuration values.</span></span> <span data-ttu-id="dadd3-150">Program aracılığıyla kullanmak için aynısını yapabilir `SqlWorkflowInstanceStore` ile `WorkflowServiceHost` hizmet davranışı öğesinin kullanmadan.</span><span class="sxs-lookup"><span data-stu-id="dadd3-150">You can do the same programmatically to use the `SqlWorkflowInstanceStore` with `WorkflowServiceHost` without using the service behavior element.</span></span>  
  
```  
workflowServiceHost.DurableInstancingOptions.InstanceStore = sqlInstanceStoreObject;  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="dadd3-151">Kullanıcı adları ve parolalar gibi hassas bilgileri Web.config dosyasında depolamaz önerilir.</span><span class="sxs-lookup"><span data-stu-id="dadd3-151">It is recommended that you do not store sensitive information such as user names and passwords in the Web.config file.</span></span> <span data-ttu-id="dadd3-152">Web.config dosyasında gizli bilgileri depoluyorsa, dosya sistemi erişim denetim listeleri (ACL'ler) kullanılarak güvenli Web.config dosyasına erişimi.</span><span class="sxs-lookup"><span data-stu-id="dadd3-152">If you do store sensitive information in the Web.config file, you should secure access to the Web.config file by using file system Access Control Lists (ACLs).</span></span> <span data-ttu-id="dadd3-153">Ayrıca, ayrıca yapılandırma dosyasının içinde yapılandırma değerlerini bölümünde belirtildiği gibi güvenli hale getirebilirsiniz [şifreleme yapılandırma bilgilerini kullanarak korumalı Yapılandırması](http://go.microsoft.com/fwlink/?LinkId=178419).</span><span class="sxs-lookup"><span data-stu-id="dadd3-153">In addition, you can also secure the configuration values within a configuration file as mentioned in [Encrypting Configuration Information Using Protected Configuration](http://go.microsoft.com/fwlink/?LinkId=178419).</span></span>  
  
### <a name="machineconfig-elements-related-to-the-sql-workflow-instance-store-feature"></a><span data-ttu-id="dadd3-154">SQL iş akışı örneği deposuna özelliğiyle ilgili Machine.config öğeleri</span><span class="sxs-lookup"><span data-stu-id="dadd3-154">Machine.config Elements Related to the SQL Workflow Instance Store Feature</span></span>  
 <span data-ttu-id="dadd3-155">[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] Yükleme Machine.config dosyasının SQL iş akışı örneği deposuna özellikle ilgili aşağıdaki öğeleri ekler:</span><span class="sxs-lookup"><span data-stu-id="dadd3-155">The [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] installation adds the following elements related to the SQL Workflow Instance Store feature to the Machine.config file:</span></span>  
  
-   <span data-ttu-id="dadd3-156">Aşağıdaki davranışı uzantı öğesi, Machine.config dosyasının ekler, böylece kullanabileceğiniz <`sqlWorkflowInstanceStore`> hizmet davranışı yapılandırma dosyasına hizmetleriniz için kalıcılığı yapılandırma öğesinde.</span><span class="sxs-lookup"><span data-stu-id="dadd3-156">Adds the following behavior extension element to the Machine.config file so that you can use the <`sqlWorkflowInstanceStore`> service behavior element in the configuration file to configure persistence for your services.</span></span>  
  
    ```xml  
    <configuration>  
        <system.serviceModel>  
            <extensions>  
                <behaviorExtensions>  
                    <add name="sqlWorkflowInstanceStore" type="System.Activities.DurableInstancing.SqlWorkflowInstanceStoreElement, System.Activities.DurableInstancing, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" />  
                </behaviorExtensions>  
            </extensions>  
        <system.serviceModel>  
    <configuration>  
    ```
