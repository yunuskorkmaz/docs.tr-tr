---
title: 'Nasıl yapılır: Iş akışları ve Iş akışı hizmetleri için SQL kalıcılığını etkinleştirme'
ms.date: 03/30/2017
ms.assetid: ca7bf77f-3e5d-4b23-b17a-d0b60f46411d
ms.openlocfilehash: bef95dbeaaa96678a66ba94494a0207c7314c326
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802589"
---
# <a name="how-to-enable-sql-persistence-for-workflows-and-workflow-services"></a><span data-ttu-id="8395a-102">Nasıl yapılır: Iş akışları ve Iş akışı hizmetleri için SQL kalıcılığını etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="8395a-102">How to: Enable SQL Persistence for Workflows and Workflow Services</span></span>

<span data-ttu-id="8395a-103">Bu konuda, hem programlama yoluyla hem de bir yapılandırma dosyası kullanarak, iş akışlarınız ve iş akışı hizmetlerinize yönelik kalıcılığı etkinleştirmek için SQL Iş akışı örnek deposu özelliğinin nasıl yapılandırılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8395a-103">This topic describes how to configure the SQL Workflow Instance Store feature to enable persistence for your workflows and workflow services both programmatically and by using a configuration file.</span></span>

<span data-ttu-id="8395a-104">Windows Server App Fabric, kalıcılığı yapılandırma sürecini basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="8395a-104">Windows Server App Fabric simplifies the process of configuring persistence.</span></span> <span data-ttu-id="8395a-105">Daha fazla bilgi için bkz. [App Fabric Kalıcılık Yapılandırması](https://docs.microsoft.com/previous-versions/appfabric/ee790848(v=azure.10)).</span><span class="sxs-lookup"><span data-stu-id="8395a-105">For more information, see [App Fabric Persistence Configuration](https://docs.microsoft.com/previous-versions/appfabric/ee790848(v=azure.10)).</span></span>

<span data-ttu-id="8395a-106">SQL Iş akışı örneği deposu özelliğini kullanmadan önce, özelliğin iş akışı örneklerini kalıcı hale getirmek için kullandığı bir veritabanı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="8395a-106">Before using the SQL Workflow Instance Store feature, create a database that the feature uses to persist workflow instances.</span></span> <span data-ttu-id="8395a-107">[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] Kurulum programı SQL Iş akışı örneği deposu özelliğiyle ilişkili SQL komut dosyalarını%WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN klasörüne kopyalar.</span><span class="sxs-lookup"><span data-stu-id="8395a-107">The [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] set-up program copies SQL script files associated with the SQL Workflow Instance Store feature to the %WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN folder.</span></span> <span data-ttu-id="8395a-108">Bu betik dosyalarını, SQL Workflow örnek deposunun iş akışı örneklerini kalıcı hale getirmek için kullanmasını istediğiniz bir SQL Server 2005 veya SQL Server 2008 veritabanında çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="8395a-108">Run these script files against a SQL Server 2005 or SQL Server 2008 database that you want the SQL Workflow Instance Store to use to persist workflow instances.</span></span> <span data-ttu-id="8395a-109">Önce SqlWorkflowInstanceStoreSchema. SQL dosyasını çalıştırın ve ardından Sqlworkflowcestorelogic. SQL dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="8395a-109">Run the SqlWorkflowInstanceStoreSchema.sql file first and then run the SqlWorkflowInstanceStoreLogic.sql file.</span></span>

> [!NOTE]
> <span data-ttu-id="8395a-110">Kalıcı veritabanını yeni bir veritabanına sahip olacak şekilde temizlemek için,%WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN içindeki betikleri aşağıdaki sırayla çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="8395a-110">To clean up the persistence database to have a fresh database, run the scripts in %WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN in the following order.</span></span>
>
> 1. <span data-ttu-id="8395a-111">SqlWorkflowInstanceStoreSchema. SQL</span><span class="sxs-lookup"><span data-stu-id="8395a-111">SqlWorkflowInstanceStoreSchema.sql</span></span>
> 2. <span data-ttu-id="8395a-112">Sqlworkflowcestorelogic. SQL</span><span class="sxs-lookup"><span data-stu-id="8395a-112">SqlWorkflowInstanceStoreLogic.sql</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8395a-113">Bir Kalıcılık veritabanı oluşturmayın, SQL Iş akışı örneği deposu özelliği, bir konak iş akışlarını kalıcı yapmayı denediğinde aşağıdakine benzer bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8395a-113">If you do not create a persistence database, the SQL Workflow Instance Store feature throws an exception similar to the following one when a host tries to persist workflows.</span></span>
>
> <span data-ttu-id="8395a-114">System. Data. SqlClient. SqlException: ' System. Activities. Durableörnekno. CreateLockOwner ' saklı yordamı bulunamadı</span><span class="sxs-lookup"><span data-stu-id="8395a-114">System.Data.SqlClient.SqlException: Could not find stored procedure 'System.Activities.DurableInstancing.CreateLockOwner'</span></span>

<span data-ttu-id="8395a-115">Aşağıdaki bölümlerde, SQL Iş akışı örnek deposu kullanılarak iş akışları ve iş akışı hizmetleri için kalıcılığın nasıl etkinleştirileceği açıklanır.</span><span class="sxs-lookup"><span data-stu-id="8395a-115">The following sections describe how to enable persistence for workflows and workflow services using the SQL Workflow Instance Store.</span></span> <span data-ttu-id="8395a-116">SQL Iş akışı örnek deposunun özellikleri hakkında daha fazla bilgi için bkz. [SQL Workflow örnek deposunun özellikleri](properties-of-sql-workflow-instance-store.md).</span><span class="sxs-lookup"><span data-stu-id="8395a-116">For more information about properties of the SQL Workflow Instance Store, see [Properties of SQL Workflow Instance Store](properties-of-sql-workflow-instance-store.md).</span></span>

## <a name="enabling-persistence-for-self-hosted-workflows-that-use-workflowapplication"></a><span data-ttu-id="8395a-117">WorkflowApplication kullanan kendi kendine barındırılan Iş akışları için kalıcılığı etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="8395a-117">Enabling Persistence for Self-Hosted Workflows that use WorkflowApplication</span></span>

<span data-ttu-id="8395a-118"><xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> nesne modelini kullanarak program aracılığıyla <xref:System.Activities.WorkflowApplication> kullanan, kendi kendine barındırılan iş akışları için kalıcılığı etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8395a-118">You can enable persistence for self-hosted workflows that use <xref:System.Activities.WorkflowApplication> programmatically by using the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> object model.</span></span> <span data-ttu-id="8395a-119">Aşağıdaki yordam bunu yapmak için gereken adımları içerir.</span><span class="sxs-lookup"><span data-stu-id="8395a-119">The following procedure contains steps to do this.</span></span>

#### <a name="to-enable-persistence-for-self-hosted-workflows"></a><span data-ttu-id="8395a-120">Şirket içinde barındırılan iş akışlarıyla kalıcılığı etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="8395a-120">To enable persistence for self-hosted workflows</span></span>

1. <span data-ttu-id="8395a-121">System. Activities. Durableörnekbir. dll dosyasına bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8395a-121">Add a reference to System.Activities.DurableInstancing.dll.</span></span>

2. <span data-ttu-id="8395a-122">Mevcut "Using" deyimlerinin ardından kaynak dosyanın en üstüne aşağıdaki deyimi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8395a-122">Add the following statement at the top of the source file after the existing "using" statements.</span></span>

    ```csharp
    using System.Activities.DurableInstancing;
    ```

3. <span data-ttu-id="8395a-123">Aşağıdaki kod örneğinde gösterildiği gibi bir <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> oluşturun ve bunu <xref:System.Activities.WorkflowApplication> <xref:System.Activities.WorkflowApplication.InstanceStore%2A> atayın.</span><span class="sxs-lookup"><span data-stu-id="8395a-123">Construct a <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> and assign it to the <xref:System.Activities.WorkflowApplication.InstanceStore%2A> of the <xref:System.Activities.WorkflowApplication> as shown in the following code example.</span></span>

    ```csharp
    SqlWorkflowInstanceStore store =
        new SqlWorkflowInstanceStore("Server=.\\SQLEXPRESS;Initial Catalog=Persistence;Integrated Security=SSPI");

    WorkflowApplication wfApp =
        new WorkflowApplication(new Workflow1());

    wfApp.InstanceStore = store;
    ```

   > [!NOTE]
   > <span data-ttu-id="8395a-124">SQL Server sürümüne bağlı olarak, bağlantı dizesi sunucu adı farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="8395a-124">Depending on your edition of SQL Server, the connection string server name may be different.</span></span>

4. <span data-ttu-id="8395a-125">Bir iş akışını sürdürmek için <xref:System.Activities.WorkflowApplication> nesnesi üzerinde <xref:System.Activities.WorkflowApplication.Persist%2A> yöntemi çağırın veya bir iş akışını kalıcı hale getirmek ve kaldırmak için <xref:System.Activities.WorkflowApplication.Unload%2A> yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="8395a-125">Invoke the <xref:System.Activities.WorkflowApplication.Persist%2A> method on the <xref:System.Activities.WorkflowApplication> object to persist a workflow, or <xref:System.Activities.WorkflowApplication.Unload%2A> method to persist and unload a workflow.</span></span> <span data-ttu-id="8395a-126">Ayrıca, <xref:System.Activities.WorkflowApplication> nesnesi tarafından oluşturulan <xref:System.Activities.WorkflowApplication.PersistableIdle%2A> olayını işleyebilir ve <xref:System.Activities.PersistableIdleAction>uygun (<xref:System.Activities.PersistableIdleAction.Persist> ya da <xref:System.Activities.PersistableIdleAction.Unload>) üyesini döndürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8395a-126">You can also handle the <xref:System.Activities.WorkflowApplication.PersistableIdle%2A> event raised by the <xref:System.Activities.WorkflowApplication> object and return appropriate (<xref:System.Activities.PersistableIdleAction.Persist> or <xref:System.Activities.PersistableIdleAction.Unload>) member of <xref:System.Activities.PersistableIdleAction>.</span></span>

   ```csharp
   wfApp.PersistableIdle = delegate(WorkflowApplicationIdleEventArgs e)
   {
       return PersistableIdleAction.Persist;
   };
   ```

> [!NOTE]
> <span data-ttu-id="8395a-127">Adım adım yönergeler için bkz. Başlangıç [öğreticisinin](getting-started-tutorial.md) [uzun süre çalışan iş akışı oluşturma ve çalıştırma](how-to-create-and-run-a-long-running-workflow.md) adımı.</span><span class="sxs-lookup"><span data-stu-id="8395a-127">See the [How to: Create and Run a Long Running Workflow](how-to-create-and-run-a-long-running-workflow.md) step of the [Getting Started Tutorial](getting-started-tutorial.md) for step by step instructions.</span></span>

## <a name="enabling-persistence-for-self-hosted-workflow-services-that-use-the-workflowservicehost"></a><span data-ttu-id="8395a-128">WorkflowServiceHost kullanan kendi kendine barındırılan Iş akışı hizmetleri için kalıcılığı etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="8395a-128">Enabling Persistence for Self-Hosted Workflow Services that use the WorkflowServiceHost</span></span>

<span data-ttu-id="8395a-129"><xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> sınıfını veya <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> sınıfını kullanarak program aracılığıyla <xref:System.ServiceModel.WorkflowServiceHost> kullanan şirket içinde barındırılan iş akışı hizmetleri için kalıcılığı etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8395a-129">You can enable persistence for self-hosted workflow services that use <xref:System.ServiceModel.WorkflowServiceHost> programmatically by using the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> class or the <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> class.</span></span>

### <a name="using-the-sqlworkflowinstancestorebehavior-class"></a><span data-ttu-id="8395a-130">Sqlworkflowcestorebehavior sınıfını kullanma</span><span class="sxs-lookup"><span data-stu-id="8395a-130">Using the SqlWorkflowInstanceStoreBehavior Class</span></span>

<span data-ttu-id="8395a-131">Aşağıdaki yordam, kendi kendine barındırılan iş akışı hizmetleri için kalıcılığı etkinleştirmek üzere <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> sınıfını kullanma adımları içerir.</span><span class="sxs-lookup"><span data-stu-id="8395a-131">The following procedure contains steps to use the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> class to enable persistence for self-hosted workflow services.</span></span>

#### <a name="to-enable-persistence-using-sqlworkflowinstancestorebehavior"></a><span data-ttu-id="8395a-132">Sqlworkflowcestorebehavior kullanarak kalıcılığı etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="8395a-132">To enable persistence using SqlWorkflowInstanceStoreBehavior</span></span>

1. <span data-ttu-id="8395a-133">System. ServiceModel. dll dosyasına bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8395a-133">Add a reference to the System.ServiceModel.dll.</span></span>

2. <span data-ttu-id="8395a-134">Mevcut "Using" deyimlerinin ardından kaynak dosyanın en üstüne aşağıdaki deyimi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8395a-134">Add the following statement at the top of the source file after the existing "using" statements.</span></span>

    ```csharp
    using System.ServiceModel.Activities.Description;
    ```

3. <span data-ttu-id="8395a-135">`WorkflowServiceHost` bir örneğini oluşturun ve iş akışı hizmeti için uç noktalar ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8395a-135">Create an instance of the `WorkflowServiceHost` and add endpoints for the workflow service.</span></span>

    ```csharp
    WorkflowServiceHost host = new WorkflowServiceHost(new CountingWorkflow(), new Uri(hostBaseAddress));
    host.AddServiceEndpoint("ICountingWorkflow", new BasicHttpBinding(), "");
    ```

4. <span data-ttu-id="8395a-136">`SqlWorkflowInstanceStoreBehavior` nesnesi oluşturun ve davranış nesnesinin özelliklerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="8395a-136">Construct a `SqlWorkflowInstanceStoreBehavior` object and to set properties of the behavior object.</span></span>

    ```csharp
    SqlWorkflowInstanceStoreBehavior instanceStoreBehavior = new SqlWorkflowInstanceStoreBehavior(connectionString);
    instanceStoreBehavior.HostLockRenewalPeriod = new TimeSpan(0, 0, 5);
    instanceStoreBehavior.InstanceCompletionAction = InstanceCompletionAction.DeleteAll;
    instanceStoreBehavior.InstanceLockedExceptionAction = InstanceLockedExceptionAction.AggressiveRetry;
    instanceStoreBehavior.InstanceEncodingOption = InstanceEncodingOption.GZip;
    instanceStoreBehavior.RunnableInstancesDetectionPeriod = new TimeSpan("00:00:02");
    host.Description.Behaviors.Add(instanceStoreBehavior);
    ```

5. <span data-ttu-id="8395a-137">İş akışı hizmet konağını açın.</span><span class="sxs-lookup"><span data-stu-id="8395a-137">Open the workflow service host.</span></span>

    ```csharp
    host.Open();
    ```

### <a name="using-the-durableinstancingoptions-property"></a><span data-ttu-id="8395a-138">DurableInstancingOptions özelliğini kullanma</span><span class="sxs-lookup"><span data-stu-id="8395a-138">Using the DurableInstancingOptions Property</span></span>

<span data-ttu-id="8395a-139">`SqlWorkflowInstanceStoreBehavior` uygulandığında, `WorkflowServiceHost` `DurableInstancingOptions.InstanceStore` yapılandırma değerleri kullanılarak oluşturulan `SqlWorkflowInstanceStore` nesnesine ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="8395a-139">When the `SqlWorkflowInstanceStoreBehavior` is applied, the `DurableInstancingOptions.InstanceStore` on the `WorkflowServiceHost` is set to the `SqlWorkflowInstanceStore` object created using the configuration values.</span></span> <span data-ttu-id="8395a-140">Aşağıdaki kod örneğinde gösterildiği gibi `SqlWorkflowInstanceStoreBehavior` sınıfını kullanmadan `WorkflowServiceHost` <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> özelliğini ayarlamak için programlama yoluyla aynı şekilde yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8395a-140">You can do the same programmatically to set the <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> property of the `WorkflowServiceHost` without using the `SqlWorkflowInstanceStoreBehavior` class as shown in the following code example.</span></span>

```csharp
workflowServiceHost.DurableInstancingOptions.InstanceStore = sqlInstanceStoreObject;
```

## <a name="enabling-persistence-for-was-hosted-workflow-services-that-use-the-workflowservicehost-using-a-configuration-file"></a><span data-ttu-id="8395a-141">Yapılandırma dosyası kullanarak WorkflowServiceHost kullanan, WAS tarafından barındırılan Iş akışı hizmetleri için kalıcılık etkinleştiriliyor</span><span class="sxs-lookup"><span data-stu-id="8395a-141">Enabling Persistence for WAS-Hosted Workflow Services that use the WorkflowServiceHost using a Configuration File</span></span>

<span data-ttu-id="8395a-142">Kendi kendine barındırılan veya Windows Işlem etkinleştirme hizmeti (WAS) tarafından barındırılan iş akışı hizmetleri için bir yapılandırma dosyası kullanarak kalıcılığı etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8395a-142">You can enable persistence for self-hosted or Windows Process Activation Service (WAS)-hosted workflow services by using a configuration file.</span></span> <span data-ttu-id="8395a-143">Bir barındırılan iş akışı hizmeti, otomatik olarak barındırılan iş akışı hizmetleri olarak WorkflowServiceHost kullanır.</span><span class="sxs-lookup"><span data-stu-id="8395a-143">A WAS-hosted workflow service uses the WorkflowServiceHost as the self-hosted workflow services do.</span></span>

<span data-ttu-id="8395a-144">`SqlWorkflowInstanceStoreBehavior`, [SQL Iş akışı örnek deposu](sql-workflow-instance-store.md) özelliklerini XML yapılandırması aracılığıyla kolayca değiştirmenize olanak tanıyan bir hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="8395a-144">The `SqlWorkflowInstanceStoreBehavior`, a service behavior that allows you to conveniently change the [SQL Workflow Instance Store](sql-workflow-instance-store.md) properties through XML configuration.</span></span> <span data-ttu-id="8395a-145">WAS tarafından barındırılan iş akışı hizmetleri için Web. config dosyasını kullanın.</span><span class="sxs-lookup"><span data-stu-id="8395a-145">For WAS-hosted workflow services, use the Web.config file.</span></span> <span data-ttu-id="8395a-146">Aşağıdaki yapılandırma örneği, bir yapılandırma dosyasında `sqlWorkflowInstanceStore` Behavior öğesi kullanılarak SQL Iş akışı örnek deposunun nasıl yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8395a-146">The following configuration example shows how to configure the SQL Workflow Instance Store by using the `sqlWorkflowInstanceStore` behavior element in a configuration file.</span></span>

```xml
<serviceBehaviors>
    <behavior name="">
        <sqlWorkflowInstanceStore
                    connectionString="Data Source=(local);Initial Catalog=DefaultPersistenceProviderDb;Integrated Security=True;Async=true"
                    instanceEncodingOption="GZip | None"
                    instanceCompletionAction="DeleteAll | DeleteNothing"
                    instanceLockedExceptionAction="NoRetry | BasicRetry |AggressiveRetry"
                    hostLockRenewalPeriod="00:00:30"
                    runnableInstancesDetectionPeriod="00:00:05" />

    </behavior>
</serviceBehaviors>
```

<span data-ttu-id="8395a-147">`connectionString` veya `connectionStringName` özelliği için değer ayarlanmamışsa SQL Iş akışı örneği deposu, varsayılan olarak adlandırılan `DefaultSqlWorkflowInstanceStoreConnectionString`bağlantı dizesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="8395a-147">If you do not set values for the `connectionString` or the `connectionStringName` property, the SQL Workflow Instance Store uses the default named connection string `DefaultSqlWorkflowInstanceStoreConnectionString`.</span></span>

<span data-ttu-id="8395a-148">`SqlWorkflowInstanceStoreBehavior` uygulandığında, `WorkflowServiceHost` `DurableInstancingOptions.InstanceStore` yapılandırma değerleri kullanılarak oluşturulan `SqlWorkflowInstanceStore` nesnesine ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="8395a-148">When the `SqlWorkflowInstanceStoreBehavior` is applied, the `DurableInstancingOptions.InstanceStore` on the `WorkflowServiceHost` is set to the `SqlWorkflowInstanceStore` object created using the configuration values.</span></span> <span data-ttu-id="8395a-149">Hizmet davranışı öğesini kullanmadan `WorkflowServiceHost` ile `SqlWorkflowInstanceStore` kullanmak için aynı programlama yoluyla aynı şekilde yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8395a-149">You can do the same programmatically to use the `SqlWorkflowInstanceStore` with `WorkflowServiceHost` without using the service behavior element.</span></span>

```csharp
workflowServiceHost.DurableInstancingOptions.InstanceStore = sqlInstanceStoreObject;
```

> [!IMPORTANT]
> <span data-ttu-id="8395a-150">Web. config dosyasında kullanıcı adları ve parolalar gibi hassas bilgileri saklamayın olmanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="8395a-150">It is recommended that you do not store sensitive information such as user names and passwords in the Web.config file.</span></span> <span data-ttu-id="8395a-151">Gizli bilgileri Web. config dosyasında depolarsanız, dosya sistemi Access Control listeleri (ACL 'Ler) kullanarak Web. config dosyasına erişimi güvenli hale getirin.</span><span class="sxs-lookup"><span data-stu-id="8395a-151">If you do store sensitive information in the Web.config file, you should secure access to the Web.config file by using file system Access Control Lists (ACLs).</span></span> <span data-ttu-id="8395a-152">Ayrıca, bir yapılandırma dosyası içindeki yapılandırma değerlerini, [korunan yapılandırma kullanarak yapılandırma bilgilerini şifreleme](https://docs.microsoft.com/en-us/previous-versions/aspnet/53tyfkaw(v=vs.100))bölümünde belirtildiği gibi da güvenli hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8395a-152">In addition, you can also secure the configuration values within a configuration file as mentioned in [Encrypting Configuration Information Using Protected Configuration](https://docs.microsoft.com/en-us/previous-versions/aspnet/53tyfkaw(v=vs.100)).</span></span>

### <a name="machineconfig-elements-related-to-the-sql-workflow-instance-store-feature"></a><span data-ttu-id="8395a-153">SQL Iş akışı örnek deposu özelliğiyle Ilgili Machine. config öğeleri</span><span class="sxs-lookup"><span data-stu-id="8395a-153">Machine.config Elements Related to the SQL Workflow Instance Store Feature</span></span>

<span data-ttu-id="8395a-154">[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] yükleme SQL Iş akışı örneği deposu özelliğiyle ilgili aşağıdaki öğeleri Machine. config dosyasına ekler:</span><span class="sxs-lookup"><span data-stu-id="8395a-154">The [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] installation adds the following elements related to the SQL Workflow Instance Store feature to the Machine.config file:</span></span>

- <span data-ttu-id="8395a-155">Hizmetlerinizin kalıcılığını yapılandırmak için yapılandırma dosyasında \<SqlWorkflowInstanceStore > hizmet davranışı öğesini kullanabilmeniz için, aşağıdaki davranış uzantısı öğesini Machine. config dosyasına ekler.</span><span class="sxs-lookup"><span data-stu-id="8395a-155">Adds the following behavior extension element to the Machine.config file so that you can use the \<sqlWorkflowInstanceStore> service behavior element in the configuration file to configure persistence for your services.</span></span>

    ```xml
    <configuration>
        <system.serviceModel>
            <extensions>
                <behaviorExtensions>
                    <add name="sqlWorkflowInstanceStore" type="System.Activities.DurableInstancing.SqlWorkflowInstanceStoreElement, System.Activities.DurableInstancing, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" />
                </behaviorExtensions>
            </extensions>
        </system.serviceModel>
    </configuration>
    ```
