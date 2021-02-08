---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: Iş akışları ve Iş akışı hizmetleri için SQL kalıcılığı etkinleştirme'
title: 'Nasıl yapılır: İş Akışları ve İş Akışı Hizmetleri için SQL Kalıcılığını Etkinleştirme'
ms.date: 03/30/2017
ms.assetid: ca7bf77f-3e5d-4b23-b17a-d0b60f46411d
ms.openlocfilehash: 5c124c4ec1d75d4b3b24468c04a4fb82236aa29a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99777729"
---
# <a name="how-to-enable-sql-persistence-for-workflows-and-workflow-services"></a><span data-ttu-id="92039-103">Nasıl yapılır: İş Akışları ve İş Akışı Hizmetleri için SQL Kalıcılığını Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="92039-103">How to: Enable SQL Persistence for Workflows and Workflow Services</span></span>

<span data-ttu-id="92039-104">Bu konuda, hem programlama yoluyla hem de bir yapılandırma dosyası kullanarak, iş akışlarınız ve iş akışı hizmetlerinize yönelik kalıcılığı etkinleştirmek için SQL Iş akışı örnek deposu özelliğinin nasıl yapılandırılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="92039-104">This topic describes how to configure the SQL Workflow Instance Store feature to enable persistence for your workflows and workflow services both programmatically and by using a configuration file.</span></span>

<span data-ttu-id="92039-105">Windows Server App Fabric, kalıcılığı yapılandırma sürecini basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="92039-105">Windows Server App Fabric simplifies the process of configuring persistence.</span></span> <span data-ttu-id="92039-106">Daha fazla bilgi için bkz. [App Fabric Kalıcılık Yapılandırması](/previous-versions/appfabric/ee790848(v=azure.10)).</span><span class="sxs-lookup"><span data-stu-id="92039-106">For more information, see [App Fabric Persistence Configuration](/previous-versions/appfabric/ee790848(v=azure.10)).</span></span>

<span data-ttu-id="92039-107">SQL Iş akışı örneği deposu özelliğini kullanmadan önce, özelliğin iş akışı örneklerini kalıcı hale getirmek için kullandığı bir veritabanı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="92039-107">Before using the SQL Workflow Instance Store feature, create a database that the feature uses to persist workflow instances.</span></span> <span data-ttu-id="92039-108">Kurulum [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] programı SQL Iş akışı örneği deposu özelliğiyle ILIŞKILI SQL komut dosyalarını%WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN klasörüne kopyalar.</span><span class="sxs-lookup"><span data-stu-id="92039-108">The [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] set-up program copies SQL script files associated with the SQL Workflow Instance Store feature to the %WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN folder.</span></span> <span data-ttu-id="92039-109">Bu betik dosyalarını, SQL Workflow örnek deposunun iş akışı örneklerini kalıcı hale getirmek için kullanmasını istediğiniz bir SQL Server 2005 veya SQL Server 2008 veritabanında çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="92039-109">Run these script files against a SQL Server 2005 or SQL Server 2008 database that you want the SQL Workflow Instance Store to use to persist workflow instances.</span></span> <span data-ttu-id="92039-110">Önce SqlWorkflowInstanceStoreSchema. SQL dosyasını çalıştırın ve ardından Sqlworkflowcestorelogic. SQL dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="92039-110">Run the SqlWorkflowInstanceStoreSchema.sql file first and then run the SqlWorkflowInstanceStoreLogic.sql file.</span></span>

> [!NOTE]
> <span data-ttu-id="92039-111">Kalıcı veritabanını yeni bir veritabanına sahip olacak şekilde temizlemek için,%WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN içindeki betikleri aşağıdaki sırayla çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="92039-111">To clean up the persistence database to have a fresh database, run the scripts in %WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN in the following order.</span></span>
>
> 1. <span data-ttu-id="92039-112">SqlWorkflowInstanceStoreSchema. SQL</span><span class="sxs-lookup"><span data-stu-id="92039-112">SqlWorkflowInstanceStoreSchema.sql</span></span>
> 2. <span data-ttu-id="92039-113">Sqlworkflowcestorelogic. SQL</span><span class="sxs-lookup"><span data-stu-id="92039-113">SqlWorkflowInstanceStoreLogic.sql</span></span>

> [!IMPORTANT]
> <span data-ttu-id="92039-114">Bir Kalıcılık veritabanı oluşturmayın, SQL Iş akışı örneği deposu özelliği, bir konak iş akışlarını kalıcı yapmayı denediğinde aşağıdakine benzer bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="92039-114">If you do not create a persistence database, the SQL Workflow Instance Store feature throws an exception similar to the following one when a host tries to persist workflows.</span></span>
>
> <span data-ttu-id="92039-115">System. Data. SqlClient. SqlException: ' System. Activities. Durableörnekno. CreateLockOwner ' saklı yordamı bulunamadı</span><span class="sxs-lookup"><span data-stu-id="92039-115">System.Data.SqlClient.SqlException: Could not find stored procedure 'System.Activities.DurableInstancing.CreateLockOwner'</span></span>

<span data-ttu-id="92039-116">Aşağıdaki bölümlerde, SQL Iş akışı örnek deposu kullanılarak iş akışları ve iş akışı hizmetleri için kalıcılığın nasıl etkinleştirileceği açıklanır.</span><span class="sxs-lookup"><span data-stu-id="92039-116">The following sections describe how to enable persistence for workflows and workflow services using the SQL Workflow Instance Store.</span></span> <span data-ttu-id="92039-117">SQL Iş akışı örnek deposunun özellikleri hakkında daha fazla bilgi için bkz. [SQL Workflow örnek deposunun özellikleri](properties-of-sql-workflow-instance-store.md).</span><span class="sxs-lookup"><span data-stu-id="92039-117">For more information about properties of the SQL Workflow Instance Store, see [Properties of SQL Workflow Instance Store](properties-of-sql-workflow-instance-store.md).</span></span>

## <a name="enabling-persistence-for-self-hosted-workflows-that-use-workflowapplication"></a><span data-ttu-id="92039-118">WorkflowApplication kullanan Self-Hosted Iş akışları için kalıcılığın etkinleştirilmesi</span><span class="sxs-lookup"><span data-stu-id="92039-118">Enabling Persistence for Self-Hosted Workflows that use WorkflowApplication</span></span>

<span data-ttu-id="92039-119"><xref:System.Activities.WorkflowApplication>Nesne modelini kullanarak programlı olarak kullanan kendi kendine barındırılan iş akışları için kalıcılığı etkinleştirebilirsiniz <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> .</span><span class="sxs-lookup"><span data-stu-id="92039-119">You can enable persistence for self-hosted workflows that use <xref:System.Activities.WorkflowApplication> programmatically by using the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> object model.</span></span> <span data-ttu-id="92039-120">Aşağıdaki yordam bunu yapmak için gereken adımları içerir.</span><span class="sxs-lookup"><span data-stu-id="92039-120">The following procedure contains steps to do this.</span></span>

#### <a name="to-enable-persistence-for-self-hosted-workflows"></a><span data-ttu-id="92039-121">Şirket içinde barındırılan iş akışlarıyla kalıcılığı etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="92039-121">To enable persistence for self-hosted workflows</span></span>

1. <span data-ttu-id="92039-122">System.Activities.DurableInstancing.dll bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="92039-122">Add a reference to System.Activities.DurableInstancing.dll.</span></span>

2. <span data-ttu-id="92039-123">Mevcut "Using" deyimlerinin ardından kaynak dosyanın en üstüne aşağıdaki deyimi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="92039-123">Add the following statement at the top of the source file after the existing "using" statements.</span></span>

    ```csharp
    using System.Activities.DurableInstancing;
    ```

3. <span data-ttu-id="92039-124">Oluşturun <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> ve <xref:System.Activities.WorkflowApplication.InstanceStore%2A> <xref:System.Activities.WorkflowApplication> Aşağıdaki kod örneğinde gösterildiği gibi öğesine atayın.</span><span class="sxs-lookup"><span data-stu-id="92039-124">Construct a <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> and assign it to the <xref:System.Activities.WorkflowApplication.InstanceStore%2A> of the <xref:System.Activities.WorkflowApplication> as shown in the following code example.</span></span>

    ```csharp
    SqlWorkflowInstanceStore store =
        new SqlWorkflowInstanceStore("Server=.\\SQLEXPRESS;Initial Catalog=Persistence;Integrated Security=SSPI");

    WorkflowApplication wfApp =
        new WorkflowApplication(new Workflow1());

    wfApp.InstanceStore = store;
    ```

   > [!NOTE]
   > <span data-ttu-id="92039-125">SQL Server sürümüne bağlı olarak, bağlantı dizesi sunucu adı farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="92039-125">Depending on your edition of SQL Server, the connection string server name may be different.</span></span>

4. <span data-ttu-id="92039-126">Bir iş akışını kalıcı hale getirmek <xref:System.Activities.WorkflowApplication.Persist%2A> için nesne üzerinde yöntemi çağırın <xref:System.Activities.WorkflowApplication> veya <xref:System.Activities.WorkflowApplication.Unload%2A> bir iş akışını kalıcı hale getirme ve kaldırma yöntemi.</span><span class="sxs-lookup"><span data-stu-id="92039-126">Invoke the <xref:System.Activities.WorkflowApplication.Persist%2A> method on the <xref:System.Activities.WorkflowApplication> object to persist a workflow, or <xref:System.Activities.WorkflowApplication.Unload%2A> method to persist and unload a workflow.</span></span> <span data-ttu-id="92039-127">Ayrıca, <xref:System.Activities.WorkflowApplication.PersistableIdle%2A> nesne tarafından oluşturulan olayı işleyebilir <xref:System.Activities.WorkflowApplication> ve öğesinin uygun ( <xref:System.Activities.PersistableIdleAction.Persist> veya <xref:System.Activities.PersistableIdleAction.Unload> ) üyesini döndürebilirsiniz <xref:System.Activities.PersistableIdleAction> .</span><span class="sxs-lookup"><span data-stu-id="92039-127">You can also handle the <xref:System.Activities.WorkflowApplication.PersistableIdle%2A> event raised by the <xref:System.Activities.WorkflowApplication> object and return appropriate (<xref:System.Activities.PersistableIdleAction.Persist> or <xref:System.Activities.PersistableIdleAction.Unload>) member of <xref:System.Activities.PersistableIdleAction>.</span></span>

   ```csharp
   wfApp.PersistableIdle = delegate(WorkflowApplicationIdleEventArgs e)
   {
       return PersistableIdleAction.Persist;
   };
   ```

> [!NOTE]
> <span data-ttu-id="92039-128">Adım adım yönergeler için bkz. Başlangıç [öğreticisinin](getting-started-tutorial.md) [uzun süre çalışan iş akışı oluşturma ve çalıştırma](how-to-create-and-run-a-long-running-workflow.md) adımı.</span><span class="sxs-lookup"><span data-stu-id="92039-128">See the [How to: Create and Run a Long Running Workflow](how-to-create-and-run-a-long-running-workflow.md) step of the [Getting Started Tutorial](getting-started-tutorial.md) for step by step instructions.</span></span>

## <a name="enabling-persistence-for-self-hosted-workflow-services-that-use-the-workflowservicehost"></a><span data-ttu-id="92039-129">WorkflowServiceHost kullanan Self-Hosted Iş akışı hizmetleri için kalıcılığın etkinleştirilmesi</span><span class="sxs-lookup"><span data-stu-id="92039-129">Enabling Persistence for Self-Hosted Workflow Services that use the WorkflowServiceHost</span></span>

<span data-ttu-id="92039-130"><xref:System.ServiceModel.WorkflowServiceHost>Sınıfını veya sınıfını kullanarak programlı olarak kullanan şirket içinde barındırılan iş akışı hizmetleri için kalıcılığın etkin olmasını sağlayabilirsiniz <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> .</span><span class="sxs-lookup"><span data-stu-id="92039-130">You can enable persistence for self-hosted workflow services that use <xref:System.ServiceModel.WorkflowServiceHost> programmatically by using the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> class or the <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> class.</span></span>

### <a name="using-the-sqlworkflowinstancestorebehavior-class"></a><span data-ttu-id="92039-131">Sqlworkflowcestorebehavior sınıfını kullanma</span><span class="sxs-lookup"><span data-stu-id="92039-131">Using the SqlWorkflowInstanceStoreBehavior Class</span></span>

<span data-ttu-id="92039-132">Aşağıdaki yordam, <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> kendi kendine barındırılan iş akışı hizmetleri için kalıcılığı etkinleştirmek üzere sınıfını kullanma adımları içerir.</span><span class="sxs-lookup"><span data-stu-id="92039-132">The following procedure contains steps to use the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> class to enable persistence for self-hosted workflow services.</span></span>

#### <a name="to-enable-persistence-using-sqlworkflowinstancestorebehavior"></a><span data-ttu-id="92039-133">Sqlworkflowcestorebehavior kullanarak kalıcılığı etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="92039-133">To enable persistence using SqlWorkflowInstanceStoreBehavior</span></span>

1. <span data-ttu-id="92039-134">System.ServiceModel.dll bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="92039-134">Add a reference to the System.ServiceModel.dll.</span></span>

2. <span data-ttu-id="92039-135">Mevcut "Using" deyimlerinin ardından kaynak dosyanın en üstüne aşağıdaki deyimi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="92039-135">Add the following statement at the top of the source file after the existing "using" statements.</span></span>

    ```csharp
    using System.ServiceModel.Activities.Description;
    ```

3. <span data-ttu-id="92039-136">Bir örneği oluşturun `WorkflowServiceHost` ve iş akışı hizmeti için uç noktalar ekleyin.</span><span class="sxs-lookup"><span data-stu-id="92039-136">Create an instance of the `WorkflowServiceHost` and add endpoints for the workflow service.</span></span>

    ```csharp
    WorkflowServiceHost host = new WorkflowServiceHost(new CountingWorkflow(), new Uri(hostBaseAddress));
    host.AddServiceEndpoint("ICountingWorkflow", new BasicHttpBinding(), "");
    ```

4. <span data-ttu-id="92039-137">Bir `SqlWorkflowInstanceStoreBehavior` nesne oluşturun ve davranış nesnesinin özelliklerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="92039-137">Construct a `SqlWorkflowInstanceStoreBehavior` object and to set properties of the behavior object.</span></span>

    ```csharp
    SqlWorkflowInstanceStoreBehavior instanceStoreBehavior = new SqlWorkflowInstanceStoreBehavior(connectionString);
    instanceStoreBehavior.HostLockRenewalPeriod = new TimeSpan(0, 0, 5);
    instanceStoreBehavior.InstanceCompletionAction = InstanceCompletionAction.DeleteAll;
    instanceStoreBehavior.InstanceLockedExceptionAction = InstanceLockedExceptionAction.AggressiveRetry;
    instanceStoreBehavior.InstanceEncodingOption = InstanceEncodingOption.GZip;
    instanceStoreBehavior.RunnableInstancesDetectionPeriod = new TimeSpan("00:00:02");
    host.Description.Behaviors.Add(instanceStoreBehavior);
    ```

5. <span data-ttu-id="92039-138">İş akışı hizmet konağını açın.</span><span class="sxs-lookup"><span data-stu-id="92039-138">Open the workflow service host.</span></span>

    ```csharp
    host.Open();
    ```

### <a name="using-the-durableinstancingoptions-property"></a><span data-ttu-id="92039-139">DurableInstancingOptions özelliğini kullanma</span><span class="sxs-lookup"><span data-stu-id="92039-139">Using the DurableInstancingOptions Property</span></span>

<span data-ttu-id="92039-140">Uygulandığında, `SqlWorkflowInstanceStoreBehavior` `DurableInstancingOptions.InstanceStore` üzerinde, `WorkflowServiceHost` `SqlWorkflowInstanceStore` yapılandırma değerleri kullanılarak oluşturulan nesnesine ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="92039-140">When the `SqlWorkflowInstanceStoreBehavior` is applied, the `DurableInstancingOptions.InstanceStore` on the `WorkflowServiceHost` is set to the `SqlWorkflowInstanceStore` object created using the configuration values.</span></span> <span data-ttu-id="92039-141"><xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> `WorkflowServiceHost` `SqlWorkflowInstanceStoreBehavior` Aşağıdaki kod örneğinde gösterildiği gibi sınıfını kullanmadan özelliğini ayarlamak için programlama yoluyla aynı şekilde yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="92039-141">You can do the same programmatically to set the <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> property of the `WorkflowServiceHost` without using the `SqlWorkflowInstanceStoreBehavior` class as shown in the following code example.</span></span>

```csharp
workflowServiceHost.DurableInstancingOptions.InstanceStore = sqlInstanceStoreObject;
```

## <a name="enabling-persistence-for-was-hosted-workflow-services-that-use-the-workflowservicehost-using-a-configuration-file"></a><span data-ttu-id="92039-142">Yapılandırma dosyası kullanarak WorkflowServiceHost kullanan WAS-Hosted Iş akışı hizmetleri için kalıcılığın etkinleştirilmesi</span><span class="sxs-lookup"><span data-stu-id="92039-142">Enabling Persistence for WAS-Hosted Workflow Services that use the WorkflowServiceHost using a Configuration File</span></span>

<span data-ttu-id="92039-143">Kendi kendine barındırılan veya Windows Işlem etkinleştirme hizmeti (WAS) tarafından barındırılan iş akışı hizmetleri için bir yapılandırma dosyası kullanarak kalıcılığı etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="92039-143">You can enable persistence for self-hosted or Windows Process Activation Service (WAS)-hosted workflow services by using a configuration file.</span></span> <span data-ttu-id="92039-144">Bir barındırılan iş akışı hizmeti, otomatik olarak barındırılan iş akışı hizmetleri olarak WorkflowServiceHost kullanır.</span><span class="sxs-lookup"><span data-stu-id="92039-144">A WAS-hosted workflow service uses the WorkflowServiceHost as the self-hosted workflow services do.</span></span>

<span data-ttu-id="92039-145">`SqlWorkflowInstanceStoreBehavior`, [SQL Iş akışı örnek deposu](sql-workflow-instance-store.md) özelliklerini XML yapılandırması aracılığıyla kolayca değiştirmenize olanak tanıyan bir hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="92039-145">The `SqlWorkflowInstanceStoreBehavior`, a service behavior that allows you to conveniently change the [SQL Workflow Instance Store](sql-workflow-instance-store.md) properties through XML configuration.</span></span> <span data-ttu-id="92039-146">WAS tarafından barındırılan iş akışı hizmetleri için Web.config dosyasını kullanın.</span><span class="sxs-lookup"><span data-stu-id="92039-146">For WAS-hosted workflow services, use the Web.config file.</span></span> <span data-ttu-id="92039-147">Aşağıdaki yapılandırma örneği, `sqlWorkflowInstanceStore` bir yapılandırma dosyasındaki davranış öğesi KULLANıLARAK SQL Iş akışı örnek deposunun nasıl yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="92039-147">The following configuration example shows how to configure the SQL Workflow Instance Store by using the `sqlWorkflowInstanceStore` behavior element in a configuration file.</span></span>

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

<span data-ttu-id="92039-148">Veya özelliği için değer ayarlanmamışsa `connectionString` `connectionStringName` , SQL Iş akışı örneği deposu varsayılan adlı bağlantı dizesini kullanır `DefaultSqlWorkflowInstanceStoreConnectionString` .</span><span class="sxs-lookup"><span data-stu-id="92039-148">If you do not set values for the `connectionString` or the `connectionStringName` property, the SQL Workflow Instance Store uses the default named connection string `DefaultSqlWorkflowInstanceStoreConnectionString`.</span></span>

<span data-ttu-id="92039-149">Uygulandığında, `SqlWorkflowInstanceStoreBehavior` `DurableInstancingOptions.InstanceStore` üzerinde, `WorkflowServiceHost` `SqlWorkflowInstanceStore` yapılandırma değerleri kullanılarak oluşturulan nesnesine ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="92039-149">When the `SqlWorkflowInstanceStoreBehavior` is applied, the `DurableInstancingOptions.InstanceStore` on the `WorkflowServiceHost` is set to the `SqlWorkflowInstanceStore` object created using the configuration values.</span></span> <span data-ttu-id="92039-150">`SqlWorkflowInstanceStore`Hizmet davranışı öğesini kullanmadan ile kullanmak için aynısını kullanabilirsiniz `WorkflowServiceHost` .</span><span class="sxs-lookup"><span data-stu-id="92039-150">You can do the same programmatically to use the `SqlWorkflowInstanceStore` with `WorkflowServiceHost` without using the service behavior element.</span></span>

```csharp
workflowServiceHost.DurableInstancingOptions.InstanceStore = sqlInstanceStoreObject;
```

> [!IMPORTANT]
> <span data-ttu-id="92039-151">Web.config dosyasında kullanıcı adları ve parolalar gibi hassas bilgileri saklamayın olmanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="92039-151">It is recommended that you do not store sensitive information such as user names and passwords in the Web.config file.</span></span> <span data-ttu-id="92039-152">Web.config dosyasında hassas bilgileri depolarsanız dosya sistemi Access Control listeleri (ACL 'Ler) kullanarak Web.config dosyasına erişmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="92039-152">If you do store sensitive information in the Web.config file, you should secure access to the Web.config file by using file system Access Control Lists (ACLs).</span></span> <span data-ttu-id="92039-153">Ayrıca, bir yapılandırma dosyası içindeki yapılandırma değerlerini, [korunan yapılandırma kullanarak yapılandırma bilgilerini şifreleme](/previous-versions/aspnet/53tyfkaw(v=vs.100))bölümünde belirtildiği gibi da güvenli hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="92039-153">In addition, you can also secure the configuration values within a configuration file as mentioned in [Encrypting Configuration Information Using Protected Configuration](/previous-versions/aspnet/53tyfkaw(v=vs.100)).</span></span>

### <a name="machineconfig-elements-related-to-the-sql-workflow-instance-store-feature"></a><span data-ttu-id="92039-154">SQL Iş akışı örneği deposu özelliğiyle Ilgili öğeleri Machine.config</span><span class="sxs-lookup"><span data-stu-id="92039-154">Machine.config Elements Related to the SQL Workflow Instance Store Feature</span></span>

<span data-ttu-id="92039-155">[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]Yükleme, Machine.config DOSYASıNA SQL Workflow örnek deposu özelliğiyle ilgili aşağıdaki öğeleri ekler:</span><span class="sxs-lookup"><span data-stu-id="92039-155">The [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] installation adds the following elements related to the SQL Workflow Instance Store feature to the Machine.config file:</span></span>

- <span data-ttu-id="92039-156">\<sqlWorkflowInstanceStore>Hizmetlerinizin kalıcılığını yapılandırmak için yapılandırma dosyasındaki hizmet davranışı öğesini kullanabilmeniz için, aşağıdaki davranış uzantısı öğesini Machine.config dosyasına ekler.</span><span class="sxs-lookup"><span data-stu-id="92039-156">Adds the following behavior extension element to the Machine.config file so that you can use the \<sqlWorkflowInstanceStore> service behavior element in the configuration file to configure persistence for your services.</span></span>

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
