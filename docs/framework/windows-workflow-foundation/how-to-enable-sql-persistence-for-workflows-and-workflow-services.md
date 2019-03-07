---
title: 'Nasıl yapılır: İş akışları ve iş akışı hizmetleri için SQL kalıcılığını etkinleştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ca7bf77f-3e5d-4b23-b17a-d0b60f46411d
ms.openlocfilehash: 4f4bcd06067775c6f43063ebe5682730deba1d4f
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57498893"
---
# <a name="how-to-enable-sql-persistence-for-workflows-and-workflow-services"></a><span data-ttu-id="b499d-102">Nasıl yapılır: İş akışları ve iş akışı hizmetleri için SQL kalıcılığını etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="b499d-102">How to: Enable SQL Persistence for Workflows and Workflow Services</span></span>

<span data-ttu-id="b499d-103">Bu konu, iş akışlarınızı kalıcılığını etkinleştirmek için SQL iş akışı örneği Store özelliği yapılandırmayı açıklar ve programlı olarak ve bir yapılandırma dosyası kullanarak iş akışı her ikisi de Hizmetleri.</span><span class="sxs-lookup"><span data-stu-id="b499d-103">This topic describes how to configure the SQL Workflow Instance Store feature to enable persistence for your workflows and workflow services both programmatically and by using a configuration file.</span></span>

<span data-ttu-id="b499d-104">Windows Server App Fabric kalıcılığını yapılandırma işlemini basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="b499d-104">Windows Server App Fabric simplifies the process of configuring persistence.</span></span> <span data-ttu-id="b499d-105">Daha fazla bilgi için [App Fabric kalıcılığı yapılandırma](https://go.microsoft.com/fwlink/?LinkId=201204)</span><span class="sxs-lookup"><span data-stu-id="b499d-105">For more information, see [App Fabric Persistence Configuration](https://go.microsoft.com/fwlink/?LinkId=201204)</span></span>

<span data-ttu-id="b499d-106">SQL iş akışı örneği Store özelliği kullanmadan önce iş akışı örneği kalıcı hale getirmek için bu özelliği kullanan bir veritabanı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b499d-106">Before using the SQL Workflow Instance Store feature, create a database that the feature uses to persist workflow instances.</span></span> <span data-ttu-id="b499d-107">[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] Kurulum programı %WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN klasörüne SQL iş akışı örneği Store özelliğiyle ilişkili SQL komut dosyaları kopyalar.</span><span class="sxs-lookup"><span data-stu-id="b499d-107">The [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] set-up program copies SQL script files associated with the SQL Workflow Instance Store feature to the %WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN folder.</span></span> <span data-ttu-id="b499d-108">Bu komut dosyaları, SQL iş akışı örneği Store'nın iş akışı örneği kalıcı hale getirmek için kullanmak istediğiniz bir SQL Server 2005 veya SQL Server 2008 veritabanınızda çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="b499d-108">Run these script files against a SQL Server 2005 or SQL Server 2008 database that you want the SQL Workflow Instance Store to use to persist workflow instances.</span></span> <span data-ttu-id="b499d-109">İlk SqlWorkflowInstanceStoreSchema.sql dosyasını çalıştırın ve SqlWorkflowInstanceStoreLogic.sql dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="b499d-109">Run the SqlWorkflowInstanceStoreSchema.sql file first and then run the SqlWorkflowInstanceStoreLogic.sql file.</span></span>

> [!NOTE]
> <span data-ttu-id="b499d-110">Yeni bir veritabanı için Kalıcılık veritabanını temizlemek için aşağıdaki sırayla %WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN betikleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="b499d-110">To clean up the persistence database to have a fresh database, run the scripts in %WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN in the following order.</span></span>
>
> 1. <span data-ttu-id="b499d-111">SqlWorkflowInstanceStoreSchema.sql</span><span class="sxs-lookup"><span data-stu-id="b499d-111">SqlWorkflowInstanceStoreSchema.sql</span></span>
> 2. <span data-ttu-id="b499d-112">SqlWorkflowInstanceStoreLogic.sql</span><span class="sxs-lookup"><span data-stu-id="b499d-112">SqlWorkflowInstanceStoreLogic.sql</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b499d-113">Kalıcılık veritabanı oluşturmazsanız, bir ana iş akışı persist çalıştığında SQL iş akışı örneği Store özellik aşağıdakine benzer bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b499d-113">If you do not create a persistence database, the SQL Workflow Instance Store feature throws an exception similar to the following one when a host tries to persist workflows.</span></span>
>
> <span data-ttu-id="b499d-114">System.Data.SqlClient.SqlException: Saklı yordam 'System.Activities.DurableInstancing.CreateLockOwner' bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="b499d-114">System.Data.SqlClient.SqlException: Could not find stored procedure 'System.Activities.DurableInstancing.CreateLockOwner'</span></span>

<span data-ttu-id="b499d-115">Aşağıdaki bölümlerde, iş akışları ve SQL iş akışı örneği Store kullanarak iş akışı hizmetleri için kalıcılığı etkinleştirme açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b499d-115">The following sections describe how to enable persistence for workflows and workflow services using the SQL Workflow Instance Store.</span></span> <span data-ttu-id="b499d-116">SQL iş akışı örneği Store özellikleri hakkında daha fazla bilgi için bkz. [özellikleri SQL iş akışı örneği Store](../../../docs/framework/windows-workflow-foundation/properties-of-sql-workflow-instance-store.md).</span><span class="sxs-lookup"><span data-stu-id="b499d-116">For more information about properties of the SQL Workflow Instance Store, see [Properties of SQL Workflow Instance Store](../../../docs/framework/windows-workflow-foundation/properties-of-sql-workflow-instance-store.md).</span></span>

## <a name="enabling-persistence-for-self-hosted-workflows-that-use-workflowapplication"></a><span data-ttu-id="b499d-117">WorkflowApplication şirket içinde barındırılan iş akışı için kalıcılığı etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="b499d-117">Enabling Persistence for Self-Hosted Workflows that use WorkflowApplication</span></span>

<span data-ttu-id="b499d-118">Şirket içinde barındırılan iş akışı için kalıcılığını sağlayabilirsiniz <xref:System.Activities.WorkflowApplication> kullanarak program aracılığıyla <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> nesne modeli.</span><span class="sxs-lookup"><span data-stu-id="b499d-118">You can enable persistence for self-hosted workflows that use <xref:System.Activities.WorkflowApplication> programmatically by using the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> object model.</span></span> <span data-ttu-id="b499d-119">Aşağıdaki yordam, bunu yapmak için adımları içerir.</span><span class="sxs-lookup"><span data-stu-id="b499d-119">The following procedure contains steps to do this.</span></span>

#### <a name="to-enable-persistence-for-self-hosted-workflows"></a><span data-ttu-id="b499d-120">Şirket içinde barındırılan iş akışları için kalıcılığı etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="b499d-120">To enable persistence for self-hosted workflows</span></span>

1. <span data-ttu-id="b499d-121">System.Activities.DurableInstancing.dll bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b499d-121">Add a reference to System.Activities.DurableInstancing.dll.</span></span>

2. <span data-ttu-id="b499d-122">Aşağıdaki deyim, varolan "kullanma" deyimleri sonra kaynak dosyasının en üstüne ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b499d-122">Add the following statement at the top of the source file after the existing "using" statements.</span></span>

    ```csharp
    using System.Activities.DurableInstancing;
    ```

3. <span data-ttu-id="b499d-123">Oluşturmak bir <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> atayabilirsiniz <xref:System.Activities.WorkflowApplication.InstanceStore%2A> , <xref:System.Activities.WorkflowApplication> aşağıdaki kod örneğinde gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="b499d-123">Construct a <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> and assign it to the <xref:System.Activities.WorkflowApplication.InstanceStore%2A> of the <xref:System.Activities.WorkflowApplication> as shown in the following code example.</span></span>

    ```csharp
    SqlWorkflowInstanceStore store =
        new SqlWorkflowInstanceStore("Server=.\\SQLEXPRESS;Initial Catalog=Persistence;Integrated Security=SSPI");

    WorkflowApplication wfApp =
        new WorkflowApplication(new Workflow1());

    wfApp.InstanceStore = store;
    ```

   > [!NOTE]
   > <span data-ttu-id="b499d-124">Bağlantı dizesi sunucu adı SQL Server sürümüne bağlı olarak farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="b499d-124">Depending on your edition of SQL Server, the connection string server name may be different.</span></span>

4. <span data-ttu-id="b499d-125">Çağırma <xref:System.Activities.WorkflowApplication.Persist%2A> metodunda <xref:System.Activities.WorkflowApplication> bir iş akışı persist nesnesine veya <xref:System.Activities.WorkflowApplication.Unload%2A> kalıcı hale getirmek ve bir iş akışı kaldırma yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b499d-125">Invoke the <xref:System.Activities.WorkflowApplication.Persist%2A> method on the <xref:System.Activities.WorkflowApplication> object to persist a workflow, or <xref:System.Activities.WorkflowApplication.Unload%2A> method to persist and unload a workflow.</span></span> <span data-ttu-id="b499d-126">Ayrıca işleyebilir <xref:System.Activities.WorkflowApplication.PersistableIdle%2A> olayı tarafından <xref:System.Activities.WorkflowApplication> nesne ve uygun döndürür (<xref:System.Activities.PersistableIdleAction.Persist> veya <xref:System.Activities.PersistableIdleAction.Unload>) üyesi <xref:System.Activities.PersistableIdleAction>.</span><span class="sxs-lookup"><span data-stu-id="b499d-126">You can also handle the <xref:System.Activities.WorkflowApplication.PersistableIdle%2A> event raised by the <xref:System.Activities.WorkflowApplication> object and return appropriate (<xref:System.Activities.PersistableIdleAction.Persist> or <xref:System.Activities.PersistableIdleAction.Unload>) member of <xref:System.Activities.PersistableIdleAction>.</span></span>

   ```csharp
   wfApp.PersistableIdle = delegate(WorkflowApplicationIdleEventArgs e)
   {
       return PersistableIdleAction.Persist;
   };
   ```

> [!NOTE]
> <span data-ttu-id="b499d-127">Bkz: [nasıl yapılır: Oluşturma ve uzun çalışan iş akışı çalıştırma](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md) adımında [başlangıç Öğreticisi](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md) adım adım yönergeler için.</span><span class="sxs-lookup"><span data-stu-id="b499d-127">See the [How to: Create and Run a Long Running Workflow](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md) step of the [Getting Started Tutorial](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md) for step by step instructions.</span></span>

## <a name="enabling-persistence-for-self-hosted-workflow-services-that-use-the-workflowservicehost"></a><span data-ttu-id="b499d-128">WorkflowServiceHost kullanan şirket içinde barındırılan iş akışı hizmetleri için kalıcılığı etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="b499d-128">Enabling Persistence for Self-Hosted Workflow Services that use the WorkflowServiceHost</span></span>

<span data-ttu-id="b499d-129">Kullanan şirket içinde barındırılan iş akışı hizmetleri için kalıcılığı etkinleştirebilirsiniz <xref:System.ServiceModel.WorkflowServiceHost> kullanarak program aracılığıyla <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> sınıfı veya <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b499d-129">You can enable persistence for self-hosted workflow services that use <xref:System.ServiceModel.WorkflowServiceHost> programmatically by using the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> class or the <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> class.</span></span>

### <a name="using-the-sqlworkflowinstancestorebehavior-class"></a><span data-ttu-id="b499d-130">SqlWorkflowInstanceStoreBehavior sınıfını kullanma</span><span class="sxs-lookup"><span data-stu-id="b499d-130">Using the SqlWorkflowInstanceStoreBehavior Class</span></span>

<span data-ttu-id="b499d-131">Aşağıdaki yordamı kullanmak için adımları içeren <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> şirket içinde barındırılan iş akışı hizmetleri için kalıcılığı etkinleştirme sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b499d-131">The following procedure contains steps to use the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> class to enable persistence for self-hosted workflow services.</span></span>

#### <a name="to-enable-persistence-using-sqlworkflowinstancestorebehavior"></a><span data-ttu-id="b499d-132">Kalıcılık SqlWorkflowInstanceStoreBehavior kullanarak etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="b499d-132">To enable persistence using SqlWorkflowInstanceStoreBehavior</span></span>

1. <span data-ttu-id="b499d-133">System.ServiceModel.dll bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b499d-133">Add a reference to the System.ServiceModel.dll.</span></span>

2. <span data-ttu-id="b499d-134">Aşağıdaki deyim, varolan "kullanma" deyimleri sonra kaynak dosyasının en üstüne ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b499d-134">Add the following statement at the top of the source file after the existing "using" statements.</span></span>

    ```csharp
    using System.ServiceModel.Activities.Description;
    ```

3. <span data-ttu-id="b499d-135">Bir örneğini oluşturmak `WorkflowServiceHost` ve iş akışı hizmeti için uç noktalar ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b499d-135">Create an instance of the `WorkflowServiceHost` and add endpoints for the workflow service.</span></span>

    ```csharp
    WorkflowServiceHost host = new WorkflowServiceHost(new CountingWorkflow(), new Uri(hostBaseAddress));
    host.AddServiceEndpoint("ICountingWorkflow", new BasicHttpBinding(), "");
    ```

4. <span data-ttu-id="b499d-136">Oluşturmak bir `SqlWorkflowInstanceStoreBehavior` nesne ve davranışları nesne özelliklerini ayarlamak için.</span><span class="sxs-lookup"><span data-stu-id="b499d-136">Construct a `SqlWorkflowInstanceStoreBehavior` object and to set properties of the behavior object.</span></span>

    ```csharp
    SqlWorkflowInstanceStoreBehavior instanceStoreBehavior = new SqlWorkflowInstanceStoreBehavior(connectionString);
    instanceStoreBehavior.HostLockRenewalPeriod = new TimeSpan(0, 0, 5);
    instanceStoreBehavior.InstanceCompletionAction = InstanceCompletionAction.DeleteAll;
    instanceStoreBehavior.InstanceLockedExceptionAction = InstanceLockedExceptionAction.AggressiveRetry;
    instanceStoreBehavior.InstanceEncodingOption = InstanceEncodingOption.GZip;
    instanceStoreBehavior.RunnableInstancesDetectionPeriod = new TimeSpan("00:00:02");
    host.Description.Behaviors.Add(instanceStoreBehavior);
    ```

5. <span data-ttu-id="b499d-137">İş akışı hizmeti konağı açın.</span><span class="sxs-lookup"><span data-stu-id="b499d-137">Open the workflow service host.</span></span>

    ```csharp
    host.Open();
    ```

### <a name="using-the-durableinstancingoptions-property"></a><span data-ttu-id="b499d-138">DurableInstancingOptions özelliğini kullanma</span><span class="sxs-lookup"><span data-stu-id="b499d-138">Using the DurableInstancingOptions Property</span></span>

<span data-ttu-id="b499d-139">Zaman `SqlWorkflowInstanceStoreBehavior` uygulanan `DurableInstancingOptions.InstanceStore` üzerinde `WorkflowServiceHost` ayarlanır `SqlWorkflowInstanceStore` yapılandırma değerleri kullanılarak oluşturulan bir nesne.</span><span class="sxs-lookup"><span data-stu-id="b499d-139">When the `SqlWorkflowInstanceStoreBehavior` is applied, the `DurableInstancingOptions.InstanceStore` on the `WorkflowServiceHost` is set to the `SqlWorkflowInstanceStore` object created using the configuration values.</span></span> <span data-ttu-id="b499d-140">Program üzerinden ayarlamak için aynısını yapabilir <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> özelliği `WorkflowServiceHost` kullanmadan `SqlWorkflowInstanceStoreBehavior` aşağıdaki kod örneğinde gösterildiği gibi sınıf.</span><span class="sxs-lookup"><span data-stu-id="b499d-140">You can do the same programmatically to set the <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> property of the `WorkflowServiceHost` without using the `SqlWorkflowInstanceStoreBehavior` class as shown in the following code example.</span></span>

```csharp
workflowServiceHost.DurableInstancingOptions.InstanceStore = sqlInstanceStoreObject;
```

## <a name="enabling-persistence-for-was-hosted-workflow-services-that-use-the-workflowservicehost-using-a-configuration-file"></a><span data-ttu-id="b499d-141">Bir yapılandırma dosyası kullanarak WorkflowServiceHost kullanan WAS-Hosted iş akışı hizmetleri için kalıcılığı etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="b499d-141">Enabling Persistence for WAS-Hosted Workflow Services that use the WorkflowServiceHost using a Configuration File</span></span>

<span data-ttu-id="b499d-142">Şirket içinde barındırılan veya Windows İşlem Etkinleştirme hizmeti WAS barındırılan iş akışı hizmetleri için kalıcılığı yapılandırma dosyası kullanarak etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b499d-142">You can enable persistence for self-hosted or Windows Process Activation Service (WAS)-hosted workflow services by using a configuration file.</span></span> <span data-ttu-id="b499d-143">Şirket içinde barındırılan iş akışı Hizmetleri gibi WorkflowServiceHost WAS barındırılan iş akışı hizmeti kullanır.</span><span class="sxs-lookup"><span data-stu-id="b499d-143">A WAS-hosted workflow service uses the WorkflowServiceHost as the self-hosted workflow services do.</span></span>

<span data-ttu-id="b499d-144">`SqlWorkflowInstanceStoreBehavior`, Uygun şekilde değiştirmenize olanak sağlayan bir hizmet davranışını [SQL iş akışı örneği Store](../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md) özellikleri aracılığıyla XML yapılandırması.</span><span class="sxs-lookup"><span data-stu-id="b499d-144">The `SqlWorkflowInstanceStoreBehavior`, a service behavior that allows you to conveniently change the [SQL Workflow Instance Store](../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md) properties through XML configuration.</span></span> <span data-ttu-id="b499d-145">WAS barındırılan iş akışı hizmetleri için Web.config dosyasını kullanın.</span><span class="sxs-lookup"><span data-stu-id="b499d-145">For WAS-hosted workflow services, use the Web.config file.</span></span> <span data-ttu-id="b499d-146">Aşağıdaki yapılandırma örnek SQL iş akışı örneği Store kullanarak yapılandırmak nasıl gösterir `sqlWorkflowInstanceStore` yapılandırma dosyasında bir davranış öğesi.</span><span class="sxs-lookup"><span data-stu-id="b499d-146">The following configuration example shows how to configure the SQL Workflow Instance Store by using the `sqlWorkflowInstanceStore` behavior element in a configuration file.</span></span>

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

<span data-ttu-id="b499d-147">İçin değerler ayarlamazsanız `connectionString` veya `connectionStringName` özelliği, SQL iş akışı örneği Store kullanan varsayılan bağlantı dizesi adlı `DefaultSqlWorkflowInstanceStoreConnectionString`.</span><span class="sxs-lookup"><span data-stu-id="b499d-147">If you do not set values for the `connectionString` or the `connectionStringName` property, the SQL Workflow Instance Store uses the default named connection string `DefaultSqlWorkflowInstanceStoreConnectionString`.</span></span>

<span data-ttu-id="b499d-148">Zaman `SqlWorkflowInstanceStoreBehavior` uygulanan `DurableInstancingOptions.InstanceStore` üzerinde `WorkflowServiceHost` ayarlanır `SqlWorkflowInstanceStore` yapılandırma değerleri kullanılarak oluşturulan bir nesne.</span><span class="sxs-lookup"><span data-stu-id="b499d-148">When the `SqlWorkflowInstanceStoreBehavior` is applied, the `DurableInstancingOptions.InstanceStore` on the `WorkflowServiceHost` is set to the `SqlWorkflowInstanceStore` object created using the configuration values.</span></span> <span data-ttu-id="b499d-149">Programlı olarak kullanmak için aynısını yapabilir `SqlWorkflowInstanceStore` ile `WorkflowServiceHost` hizmet davranış öğesi kullanmadan.</span><span class="sxs-lookup"><span data-stu-id="b499d-149">You can do the same programmatically to use the `SqlWorkflowInstanceStore` with `WorkflowServiceHost` without using the service behavior element.</span></span>

```csharp
workflowServiceHost.DurableInstancingOptions.InstanceStore = sqlInstanceStoreObject;
```

> [!IMPORTANT]
> <span data-ttu-id="b499d-150">Kullanıcı adları ve parolalar gibi hassas bilgileri Web.config dosyasında depolamaz önerilir.</span><span class="sxs-lookup"><span data-stu-id="b499d-150">It is recommended that you do not store sensitive information such as user names and passwords in the Web.config file.</span></span> <span data-ttu-id="b499d-151">Web.config dosyasındaki hassas bilgileri depolamak, dosya sistemine erişim denetim listeleri (ACL'ler) kullanarak güvenli Web.config dosyasına erişim.</span><span class="sxs-lookup"><span data-stu-id="b499d-151">If you do store sensitive information in the Web.config file, you should secure access to the Web.config file by using file system Access Control Lists (ACLs).</span></span> <span data-ttu-id="b499d-152">Ayrıca, ayrıca yapılandırma değerleri bir yapılandırma dosyasında belirtildiği gibi güvenliğini sağlamak [şifreleme yapılandırma bilgilerini kullanarak korumalı Yapılandırması](https://go.microsoft.com/fwlink/?LinkId=178419).</span><span class="sxs-lookup"><span data-stu-id="b499d-152">In addition, you can also secure the configuration values within a configuration file as mentioned in [Encrypting Configuration Information Using Protected Configuration](https://go.microsoft.com/fwlink/?LinkId=178419).</span></span>

### <a name="machineconfig-elements-related-to-the-sql-workflow-instance-store-feature"></a><span data-ttu-id="b499d-153">SQL iş akışı örneği Store özelliğiyle ilgili Machine.config öğeleri</span><span class="sxs-lookup"><span data-stu-id="b499d-153">Machine.config Elements Related to the SQL Workflow Instance Store Feature</span></span>

<span data-ttu-id="b499d-154">[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] Yükleme Machine.config dosyasının SQL iş akışı örneği Store özellikle ilgili aşağıdaki öğeleri ekler:</span><span class="sxs-lookup"><span data-stu-id="b499d-154">The [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] installation adds the following elements related to the SQL Workflow Instance Store feature to the Machine.config file:</span></span>

- <span data-ttu-id="b499d-155">Aşağıdaki davranışı uzantı öğesi Machine.config dosyasına ekler; böylece kullanabileceğiniz \<sqlWorkflowInstanceStore > hizmetleriniz için kalıcılığı yapılandırma yapılandırma dosyasındaki hizmet davranış öğesi.</span><span class="sxs-lookup"><span data-stu-id="b499d-155">Adds the following behavior extension element to the Machine.config file so that you can use the \<sqlWorkflowInstanceStore> service behavior element in the configuration file to configure persistence for your services.</span></span>

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
