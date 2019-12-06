---
title: 'Nasıl yapılır: Iş akışları ve Iş akışı hizmetleri için SQL kalıcılığını etkinleştirme'
ms.date: 03/30/2017
ms.assetid: ca7bf77f-3e5d-4b23-b17a-d0b60f46411d
ms.openlocfilehash: bbbd2e6a5eb3babeb1a4d06976fdefd621581766
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837694"
---
# <a name="how-to-enable-sql-persistence-for-workflows-and-workflow-services"></a>Nasıl yapılır: Iş akışları ve Iş akışı hizmetleri için SQL kalıcılığını etkinleştirme

Bu konuda, hem programlama yoluyla hem de bir yapılandırma dosyası kullanarak, iş akışlarınız ve iş akışı hizmetlerinize yönelik kalıcılığı etkinleştirmek için SQL Iş akışı örnek deposu özelliğinin nasıl yapılandırılacağı açıklanmaktadır.

Windows Server App Fabric, kalıcılığı yapılandırma sürecini basitleştirir. Daha fazla bilgi için bkz. [App Fabric Kalıcılık Yapılandırması](https://docs.microsoft.com/previous-versions/appfabric/ee790848(v=azure.10)).

SQL Iş akışı örneği deposu özelliğini kullanmadan önce, özelliğin iş akışı örneklerini kalıcı hale getirmek için kullandığı bir veritabanı oluşturun. [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] Kurulum programı SQL Iş akışı örneği deposu özelliğiyle ilişkili SQL komut dosyalarını%WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN klasörüne kopyalar. Bu betik dosyalarını, SQL Workflow örnek deposunun iş akışı örneklerini kalıcı hale getirmek için kullanmasını istediğiniz bir SQL Server 2005 veya SQL Server 2008 veritabanında çalıştırın. Önce SqlWorkflowInstanceStoreSchema. SQL dosyasını çalıştırın ve ardından Sqlworkflowcestorelogic. SQL dosyasını çalıştırın.

> [!NOTE]
> Kalıcı veritabanını yeni bir veritabanına sahip olacak şekilde temizlemek için,%WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN içindeki betikleri aşağıdaki sırayla çalıştırın.
>
> 1. SqlWorkflowInstanceStoreSchema. SQL
> 2. Sqlworkflowcestorelogic. SQL

> [!IMPORTANT]
> Bir Kalıcılık veritabanı oluşturmayın, SQL Iş akışı örneği deposu özelliği, bir konak iş akışlarını kalıcı yapmayı denediğinde aşağıdakine benzer bir özel durum oluşturur.
>
> System. Data. SqlClient. SqlException: ' System. Activities. Durableörnekno. CreateLockOwner ' saklı yordamı bulunamadı

Aşağıdaki bölümlerde, SQL Iş akışı örnek deposu kullanılarak iş akışları ve iş akışı hizmetleri için kalıcılığın nasıl etkinleştirileceği açıklanır. SQL Iş akışı örnek deposunun özellikleri hakkında daha fazla bilgi için bkz. [SQL Workflow örnek deposunun özellikleri](properties-of-sql-workflow-instance-store.md).

## <a name="enabling-persistence-for-self-hosted-workflows-that-use-workflowapplication"></a>WorkflowApplication kullanan kendi kendine barındırılan Iş akışları için kalıcılığı etkinleştirme

<xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> nesne modelini kullanarak program aracılığıyla <xref:System.Activities.WorkflowApplication> kullanan, kendi kendine barındırılan iş akışları için kalıcılığı etkinleştirebilirsiniz. Aşağıdaki yordam bunu yapmak için gereken adımları içerir.

#### <a name="to-enable-persistence-for-self-hosted-workflows"></a>Şirket içinde barındırılan iş akışlarıyla kalıcılığı etkinleştirmek için

1. System. Activities. Durableörnekbir. dll dosyasına bir başvuru ekleyin.

2. Mevcut "Using" deyimlerinin ardından kaynak dosyanın en üstüne aşağıdaki deyimi ekleyin.

    ```csharp
    using System.Activities.DurableInstancing;
    ```

3. Aşağıdaki kod örneğinde gösterildiği gibi bir <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> oluşturun ve bunu <xref:System.Activities.WorkflowApplication> <xref:System.Activities.WorkflowApplication.InstanceStore%2A> atayın.

    ```csharp
    SqlWorkflowInstanceStore store =
        new SqlWorkflowInstanceStore("Server=.\\SQLEXPRESS;Initial Catalog=Persistence;Integrated Security=SSPI");

    WorkflowApplication wfApp =
        new WorkflowApplication(new Workflow1());

    wfApp.InstanceStore = store;
    ```

   > [!NOTE]
   > SQL Server sürümüne bağlı olarak, bağlantı dizesi sunucu adı farklı olabilir.

4. Bir iş akışını sürdürmek için <xref:System.Activities.WorkflowApplication> nesnesi üzerinde <xref:System.Activities.WorkflowApplication.Persist%2A> yöntemi çağırın veya bir iş akışını kalıcı hale getirmek ve kaldırmak için <xref:System.Activities.WorkflowApplication.Unload%2A> yöntemi çağırın. Ayrıca, <xref:System.Activities.WorkflowApplication> nesnesi tarafından oluşturulan <xref:System.Activities.WorkflowApplication.PersistableIdle%2A> olayını işleyebilir ve <xref:System.Activities.PersistableIdleAction>uygun (<xref:System.Activities.PersistableIdleAction.Persist> ya da <xref:System.Activities.PersistableIdleAction.Unload>) üyesini döndürebilirsiniz.

   ```csharp
   wfApp.PersistableIdle = delegate(WorkflowApplicationIdleEventArgs e)
   {
       return PersistableIdleAction.Persist;
   };
   ```

> [!NOTE]
> Adım adım yönergeler için bkz. Başlangıç [öğreticisinin](getting-started-tutorial.md) [uzun süre çalışan iş akışı oluşturma ve çalıştırma](how-to-create-and-run-a-long-running-workflow.md) adımı.

## <a name="enabling-persistence-for-self-hosted-workflow-services-that-use-the-workflowservicehost"></a>WorkflowServiceHost kullanan kendi kendine barındırılan Iş akışı hizmetleri için kalıcılığı etkinleştirme

<xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> sınıfını veya <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> sınıfını kullanarak program aracılığıyla <xref:System.ServiceModel.WorkflowServiceHost> kullanan şirket içinde barındırılan iş akışı hizmetleri için kalıcılığı etkinleştirebilirsiniz.

### <a name="using-the-sqlworkflowinstancestorebehavior-class"></a>Sqlworkflowcestorebehavior sınıfını kullanma

Aşağıdaki yordam, kendi kendine barındırılan iş akışı hizmetleri için kalıcılığı etkinleştirmek üzere <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> sınıfını kullanma adımları içerir.

#### <a name="to-enable-persistence-using-sqlworkflowinstancestorebehavior"></a>Sqlworkflowcestorebehavior kullanarak kalıcılığı etkinleştirmek için

1. System. ServiceModel. dll dosyasına bir başvuru ekleyin.

2. Mevcut "Using" deyimlerinin ardından kaynak dosyanın en üstüne aşağıdaki deyimi ekleyin.

    ```csharp
    using System.ServiceModel.Activities.Description;
    ```

3. `WorkflowServiceHost` bir örneğini oluşturun ve iş akışı hizmeti için uç noktalar ekleyin.

    ```csharp
    WorkflowServiceHost host = new WorkflowServiceHost(new CountingWorkflow(), new Uri(hostBaseAddress));
    host.AddServiceEndpoint("ICountingWorkflow", new BasicHttpBinding(), "");
    ```

4. `SqlWorkflowInstanceStoreBehavior` nesnesi oluşturun ve davranış nesnesinin özelliklerini ayarlayın.

    ```csharp
    SqlWorkflowInstanceStoreBehavior instanceStoreBehavior = new SqlWorkflowInstanceStoreBehavior(connectionString);
    instanceStoreBehavior.HostLockRenewalPeriod = new TimeSpan(0, 0, 5);
    instanceStoreBehavior.InstanceCompletionAction = InstanceCompletionAction.DeleteAll;
    instanceStoreBehavior.InstanceLockedExceptionAction = InstanceLockedExceptionAction.AggressiveRetry;
    instanceStoreBehavior.InstanceEncodingOption = InstanceEncodingOption.GZip;
    instanceStoreBehavior.RunnableInstancesDetectionPeriod = new TimeSpan("00:00:02");
    host.Description.Behaviors.Add(instanceStoreBehavior);
    ```

5. İş akışı hizmet konağını açın.

    ```csharp
    host.Open();
    ```

### <a name="using-the-durableinstancingoptions-property"></a>DurableInstancingOptions özelliğini kullanma

`SqlWorkflowInstanceStoreBehavior` uygulandığında, `WorkflowServiceHost` `DurableInstancingOptions.InstanceStore` yapılandırma değerleri kullanılarak oluşturulan `SqlWorkflowInstanceStore` nesnesine ayarlanır. Aşağıdaki kod örneğinde gösterildiği gibi `SqlWorkflowInstanceStoreBehavior` sınıfını kullanmadan `WorkflowServiceHost` <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> özelliğini ayarlamak için programlama yoluyla aynı şekilde yapabilirsiniz.

```csharp
workflowServiceHost.DurableInstancingOptions.InstanceStore = sqlInstanceStoreObject;
```

## <a name="enabling-persistence-for-was-hosted-workflow-services-that-use-the-workflowservicehost-using-a-configuration-file"></a>Yapılandırma dosyası kullanarak WorkflowServiceHost kullanan, WAS tarafından barındırılan Iş akışı hizmetleri için kalıcılık etkinleştiriliyor

Kendi kendine barındırılan veya Windows Işlem etkinleştirme hizmeti (WAS) tarafından barındırılan iş akışı hizmetleri için bir yapılandırma dosyası kullanarak kalıcılığı etkinleştirebilirsiniz. Bir barındırılan iş akışı hizmeti, otomatik olarak barındırılan iş akışı hizmetleri olarak WorkflowServiceHost kullanır.

`SqlWorkflowInstanceStoreBehavior`, [SQL Iş akışı örnek deposu](sql-workflow-instance-store.md) özelliklerini XML yapılandırması aracılığıyla kolayca değiştirmenize olanak tanıyan bir hizmet davranışı. WAS tarafından barındırılan iş akışı hizmetleri için Web. config dosyasını kullanın. Aşağıdaki yapılandırma örneği, bir yapılandırma dosyasında `sqlWorkflowInstanceStore` Behavior öğesi kullanılarak SQL Iş akışı örnek deposunun nasıl yapılandırılacağını gösterir.

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

`connectionString` veya `connectionStringName` özelliği için değer ayarlanmamışsa SQL Iş akışı örneği deposu, varsayılan olarak adlandırılan `DefaultSqlWorkflowInstanceStoreConnectionString`bağlantı dizesini kullanır.

`SqlWorkflowInstanceStoreBehavior` uygulandığında, `WorkflowServiceHost` `DurableInstancingOptions.InstanceStore` yapılandırma değerleri kullanılarak oluşturulan `SqlWorkflowInstanceStore` nesnesine ayarlanır. Hizmet davranışı öğesini kullanmadan `WorkflowServiceHost` ile `SqlWorkflowInstanceStore` kullanmak için aynı programlama yoluyla aynı şekilde yapabilirsiniz.

```csharp
workflowServiceHost.DurableInstancingOptions.InstanceStore = sqlInstanceStoreObject;
```

> [!IMPORTANT]
> Web. config dosyasında kullanıcı adları ve parolalar gibi hassas bilgileri saklamayın olmanız önerilir. Gizli bilgileri Web. config dosyasında depolarsanız, dosya sistemi Access Control listeleri (ACL 'Ler) kullanarak Web. config dosyasına erişimi güvenli hale getirin. Ayrıca, bir yapılandırma dosyası içindeki yapılandırma değerlerini, [korunan yapılandırma kullanarak yapılandırma bilgilerini şifreleme](https://docs.microsoft.com/previous-versions/aspnet/53tyfkaw(v=vs.100))bölümünde belirtildiği gibi da güvenli hale getirebilirsiniz.

### <a name="machineconfig-elements-related-to-the-sql-workflow-instance-store-feature"></a>SQL Iş akışı örnek deposu özelliğiyle Ilgili Machine. config öğeleri

[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] yükleme SQL Iş akışı örneği deposu özelliğiyle ilgili aşağıdaki öğeleri Machine. config dosyasına ekler:

- Hizmetlerinizin kalıcılığını yapılandırmak için yapılandırma dosyasında \<SqlWorkflowInstanceStore > hizmet davranışı öğesini kullanabilmeniz için, aşağıdaki davranış uzantısı öğesini Machine. config dosyasına ekler.

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
