---
title: 'Nasıl yapılır: İş Akışları ve İş Akışı Hizmetleri için SQL Kalıcılığını Etkinleştirme'
ms.date: 03/30/2017
ms.assetid: ca7bf77f-3e5d-4b23-b17a-d0b60f46411d
ms.openlocfilehash: 5bcd37a654db35ba6e8af1b15d6c132a090b0579
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90547759"
---
# <a name="how-to-enable-sql-persistence-for-workflows-and-workflow-services"></a>Nasıl yapılır: İş Akışları ve İş Akışı Hizmetleri için SQL Kalıcılığını Etkinleştirme

Bu konuda, hem programlama yoluyla hem de bir yapılandırma dosyası kullanarak, iş akışlarınız ve iş akışı hizmetlerinize yönelik kalıcılığı etkinleştirmek için SQL Iş akışı örnek deposu özelliğinin nasıl yapılandırılacağı açıklanmaktadır.

Windows Server App Fabric, kalıcılığı yapılandırma sürecini basitleştirir. Daha fazla bilgi için bkz. [App Fabric Kalıcılık Yapılandırması](/previous-versions/appfabric/ee790848(v=azure.10)).

SQL Iş akışı örneği deposu özelliğini kullanmadan önce, özelliğin iş akışı örneklerini kalıcı hale getirmek için kullandığı bir veritabanı oluşturun. Kurulum [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] programı SQL Iş akışı örneği deposu özelliğiyle ILIŞKILI SQL komut dosyalarını%WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN klasörüne kopyalar. Bu betik dosyalarını, SQL Workflow örnek deposunun iş akışı örneklerini kalıcı hale getirmek için kullanmasını istediğiniz bir SQL Server 2005 veya SQL Server 2008 veritabanında çalıştırın. Önce SqlWorkflowInstanceStoreSchema. SQL dosyasını çalıştırın ve ardından Sqlworkflowcestorelogic. SQL dosyasını çalıştırın.

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

<xref:System.Activities.WorkflowApplication>Nesne modelini kullanarak programlı olarak kullanan kendi kendine barındırılan iş akışları için kalıcılığı etkinleştirebilirsiniz <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> . Aşağıdaki yordam bunu yapmak için gereken adımları içerir.

#### <a name="to-enable-persistence-for-self-hosted-workflows"></a>Şirket içinde barındırılan iş akışlarıyla kalıcılığı etkinleştirmek için

1. System.Activities.DurableInstancing.dll bir başvuru ekleyin.

2. Mevcut "Using" deyimlerinin ardından kaynak dosyanın en üstüne aşağıdaki deyimi ekleyin.

    ```csharp
    using System.Activities.DurableInstancing;
    ```

3. Oluşturun <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> ve <xref:System.Activities.WorkflowApplication.InstanceStore%2A> <xref:System.Activities.WorkflowApplication> Aşağıdaki kod örneğinde gösterildiği gibi öğesine atayın.

    ```csharp
    SqlWorkflowInstanceStore store =
        new SqlWorkflowInstanceStore("Server=.\\SQLEXPRESS;Initial Catalog=Persistence;Integrated Security=SSPI");

    WorkflowApplication wfApp =
        new WorkflowApplication(new Workflow1());

    wfApp.InstanceStore = store;
    ```

   > [!NOTE]
   > SQL Server sürümüne bağlı olarak, bağlantı dizesi sunucu adı farklı olabilir.

4. Bir iş akışını kalıcı hale getirmek <xref:System.Activities.WorkflowApplication.Persist%2A> için nesne üzerinde yöntemi çağırın <xref:System.Activities.WorkflowApplication> veya <xref:System.Activities.WorkflowApplication.Unload%2A> bir iş akışını kalıcı hale getirme ve kaldırma yöntemi. Ayrıca, <xref:System.Activities.WorkflowApplication.PersistableIdle%2A> nesne tarafından oluşturulan olayı işleyebilir <xref:System.Activities.WorkflowApplication> ve öğesinin uygun ( <xref:System.Activities.PersistableIdleAction.Persist> veya <xref:System.Activities.PersistableIdleAction.Unload> ) üyesini döndürebilirsiniz <xref:System.Activities.PersistableIdleAction> .

   ```csharp
   wfApp.PersistableIdle = delegate(WorkflowApplicationIdleEventArgs e)
   {
       return PersistableIdleAction.Persist;
   };
   ```

> [!NOTE]
> Adım adım yönergeler için bkz. Başlangıç [öğreticisinin](getting-started-tutorial.md) [uzun süre çalışan iş akışı oluşturma ve çalıştırma](how-to-create-and-run-a-long-running-workflow.md) adımı.

## <a name="enabling-persistence-for-self-hosted-workflow-services-that-use-the-workflowservicehost"></a>WorkflowServiceHost kullanan kendi kendine barındırılan Iş akışı hizmetleri için kalıcılığı etkinleştirme

<xref:System.ServiceModel.WorkflowServiceHost>Sınıfını veya sınıfını kullanarak programlı olarak kullanan şirket içinde barındırılan iş akışı hizmetleri için kalıcılığın etkin olmasını sağlayabilirsiniz <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> .

### <a name="using-the-sqlworkflowinstancestorebehavior-class"></a>Sqlworkflowcestorebehavior sınıfını kullanma

Aşağıdaki yordam, <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> kendi kendine barındırılan iş akışı hizmetleri için kalıcılığı etkinleştirmek üzere sınıfını kullanma adımları içerir.

#### <a name="to-enable-persistence-using-sqlworkflowinstancestorebehavior"></a>Sqlworkflowcestorebehavior kullanarak kalıcılığı etkinleştirmek için

1. System.ServiceModel.dll bir başvuru ekleyin.

2. Mevcut "Using" deyimlerinin ardından kaynak dosyanın en üstüne aşağıdaki deyimi ekleyin.

    ```csharp
    using System.ServiceModel.Activities.Description;
    ```

3. Bir örneği oluşturun `WorkflowServiceHost` ve iş akışı hizmeti için uç noktalar ekleyin.

    ```csharp
    WorkflowServiceHost host = new WorkflowServiceHost(new CountingWorkflow(), new Uri(hostBaseAddress));
    host.AddServiceEndpoint("ICountingWorkflow", new BasicHttpBinding(), "");
    ```

4. Bir `SqlWorkflowInstanceStoreBehavior` nesne oluşturun ve davranış nesnesinin özelliklerini ayarlayın.

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

Uygulandığında, `SqlWorkflowInstanceStoreBehavior` `DurableInstancingOptions.InstanceStore` üzerinde, `WorkflowServiceHost` `SqlWorkflowInstanceStore` yapılandırma değerleri kullanılarak oluşturulan nesnesine ayarlanır. <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> `WorkflowServiceHost` `SqlWorkflowInstanceStoreBehavior` Aşağıdaki kod örneğinde gösterildiği gibi sınıfını kullanmadan özelliğini ayarlamak için programlama yoluyla aynı şekilde yapabilirsiniz.

```csharp
workflowServiceHost.DurableInstancingOptions.InstanceStore = sqlInstanceStoreObject;
```

## <a name="enabling-persistence-for-was-hosted-workflow-services-that-use-the-workflowservicehost-using-a-configuration-file"></a>Yapılandırma dosyası kullanarak WorkflowServiceHost kullanan, WAS tarafından barındırılan Iş akışı hizmetleri için kalıcılık etkinleştiriliyor

Kendi kendine barındırılan veya Windows Işlem etkinleştirme hizmeti (WAS) tarafından barındırılan iş akışı hizmetleri için bir yapılandırma dosyası kullanarak kalıcılığı etkinleştirebilirsiniz. Bir barındırılan iş akışı hizmeti, otomatik olarak barındırılan iş akışı hizmetleri olarak WorkflowServiceHost kullanır.

`SqlWorkflowInstanceStoreBehavior`, [SQL Iş akışı örnek deposu](sql-workflow-instance-store.md) özelliklerini XML yapılandırması aracılığıyla kolayca değiştirmenize olanak tanıyan bir hizmet davranışı. WAS tarafından barındırılan iş akışı hizmetleri için Web.config dosyasını kullanın. Aşağıdaki yapılandırma örneği, `sqlWorkflowInstanceStore` bir yapılandırma dosyasındaki davranış öğesi KULLANıLARAK SQL Iş akışı örnek deposunun nasıl yapılandırılacağını gösterir.

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

Veya özelliği için değer ayarlanmamışsa `connectionString` `connectionStringName` , SQL Iş akışı örneği deposu varsayılan adlı bağlantı dizesini kullanır `DefaultSqlWorkflowInstanceStoreConnectionString` .

Uygulandığında, `SqlWorkflowInstanceStoreBehavior` `DurableInstancingOptions.InstanceStore` üzerinde, `WorkflowServiceHost` `SqlWorkflowInstanceStore` yapılandırma değerleri kullanılarak oluşturulan nesnesine ayarlanır. `SqlWorkflowInstanceStore`Hizmet davranışı öğesini kullanmadan ile kullanmak için aynısını kullanabilirsiniz `WorkflowServiceHost` .

```csharp
workflowServiceHost.DurableInstancingOptions.InstanceStore = sqlInstanceStoreObject;
```

> [!IMPORTANT]
> Web.config dosyasında kullanıcı adları ve parolalar gibi hassas bilgileri saklamayın olmanız önerilir. Web.config dosyasında hassas bilgileri depolarsanız dosya sistemi Access Control listeleri (ACL 'Ler) kullanarak Web.config dosyasına erişmeniz gerekir. Ayrıca, bir yapılandırma dosyası içindeki yapılandırma değerlerini, [korunan yapılandırma kullanarak yapılandırma bilgilerini şifreleme](/previous-versions/aspnet/53tyfkaw(v=vs.100))bölümünde belirtildiği gibi da güvenli hale getirebilirsiniz.

### <a name="machineconfig-elements-related-to-the-sql-workflow-instance-store-feature"></a>SQL Iş akışı örneği deposu özelliğiyle Ilgili öğeleri Machine.config

[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]Yükleme, Machine.config DOSYASıNA SQL Workflow örnek deposu özelliğiyle ilgili aşağıdaki öğeleri ekler:

- \<sqlWorkflowInstanceStore>Hizmetlerinizin kalıcılığını yapılandırmak için yapılandırma dosyasındaki hizmet davranışı öğesini kullanabilmeniz için, aşağıdaki davranış uzantısı öğesini Machine.config dosyasına ekler.

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
