---
title: 'Nasıl yapılır: iş akışları ve iş akışı hizmetleri için SQL kalıcılığını etkinleştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ca7bf77f-3e5d-4b23-b17a-d0b60f46411d
ms.openlocfilehash: d79c8fc364d13c00049523f7788ada258af6ec98
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/08/2018
ms.locfileid: "48873235"
---
# <a name="how-to-enable-sql-persistence-for-workflows-and-workflow-services"></a>Nasıl yapılır: iş akışları ve iş akışı hizmetleri için SQL kalıcılığını etkinleştirme

Bu konu, iş akışlarınızı kalıcılığını etkinleştirmek için SQL iş akışı örneği Store özelliği yapılandırmayı açıklar ve programlı olarak ve bir yapılandırma dosyası kullanarak iş akışı her ikisi de Hizmetleri.  
  
Windows Server App Fabric kalıcılığını yapılandırma işlemini basitleştirir. Daha fazla bilgi için [App Fabric kalıcılığı yapılandırma](https://go.microsoft.com/fwlink/?LinkId=201204)  
  
SQL iş akışı örneği Store özelliği kullanmadan önce iş akışı örneği kalıcı hale getirmek için bu özelliği kullanan bir veritabanı oluşturun. [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] Kurulum programı %WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN klasörüne SQL iş akışı örneği Store özelliğiyle ilişkili SQL komut dosyaları kopyalar. Bu komut dosyaları, SQL iş akışı örneği Store'nın iş akışı örneği kalıcı hale getirmek için kullanmak istediğiniz bir SQL Server 2005 veya SQL Server 2008 veritabanınızda çalıştırın. İlk SqlWorkflowInstanceStoreSchema.sql dosyasını çalıştırın ve SqlWorkflowInstanceStoreLogic.sql dosyasını çalıştırın.

> [!NOTE]
> Yeni bir veritabanı için Kalıcılık veritabanını temizlemek için aşağıdaki sırayla %WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN betikleri çalıştırın.  
>
> 1. SqlWorkflowInstanceStoreSchema.sql
> 2. SqlWorkflowInstanceStoreLogic.sql

> [!IMPORTANT]
> Kalıcılık veritabanı oluşturmazsanız, bir ana iş akışı persist çalıştığında SQL iş akışı örneği Store özellik aşağıdakine benzer bir özel durum oluşturur.  
> 
> System.Data.SqlClient.SqlException: 'System.Activities.DurableInstancing.CreateLockOwner' saklı yordamı bulunamadı.  

Aşağıdaki bölümlerde, iş akışları ve SQL iş akışı örneği Store kullanarak iş akışı hizmetleri için kalıcılığı etkinleştirme açıklanmaktadır. SQL iş akışı örneği Store özellikleri hakkında daha fazla bilgi için bkz. [özellikleri SQL iş akışı örneği Store](../../../docs/framework/windows-workflow-foundation/properties-of-sql-workflow-instance-store.md).  

## <a name="enabling-persistence-for-self-hosted-workflows-that-use-workflowapplication"></a>WorkflowApplication şirket içinde barındırılan iş akışı için kalıcılığı etkinleştirme

Şirket içinde barındırılan iş akışı için kalıcılığını sağlayabilirsiniz <xref:System.Activities.WorkflowApplication> kullanarak program aracılığıyla <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> nesne modeli. Aşağıdaki yordam, bunu yapmak için adımları içerir.  

#### <a name="to-enable-persistence-for-self-hosted-workflows"></a>Şirket içinde barındırılan iş akışları için kalıcılığı etkinleştirme

1.  System.Activites.DurableInstancing.dll bir başvuru ekleyin.  
  
2.  Aşağıdaki deyim, varolan "kullanma" deyimleri sonra kaynak dosyasının en üstüne ekleyin.  
  
    ```csharp  
    using System.Activities.DurableInstancing;  
    ```  
  
3.  Oluşturmak bir <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> atayabilirsiniz <xref:System.Activities.WorkflowApplication.InstanceStore%2A> , <xref:System.Activities.WorkflowApplication> aşağıdaki kod örneğinde gösterildiği gibi.
  
    ```csharp
    SqlWorkflowInstanceStore store =
        new SqlWorkflowInstanceStore("Server=.\\SQLEXPRESS;Initial Catalog=Persistence;Integrated Security=SSPI");

    WorkflowApplication wfApp =
        new WorkflowApplication(new Workflow1());

    wfApp.InstanceStore = store;
    ```
  
   > [!NOTE]
   > Bağlantı dizesi sunucu adı SQL Server sürümüne bağlı olarak farklı olabilir.  
  
4. Çağırma <xref:System.Activities.WorkflowApplication.Persist%2A> metodunda <xref:System.Activities.WorkflowApplication> bir iş akışı persist nesnesine veya <xref:System.Activities.WorkflowApplication.Unload%2A> kalıcı hale getirmek ve bir iş akışı kaldırma yöntemi. Ayrıca işleyebilir <xref:System.Activities.WorkflowApplication.PersistableIdle%2A> olayı tarafından <xref:System.Activities.WorkflowApplication> nesne ve uygun döndürür (<xref:System.Activities.PersistableIdleAction.Persist> veya <xref:System.Activities.PersistableIdleAction.Unload>) üyesi <xref:System.Activities.PersistableIdleAction>.  
  
   ```csharp
   wfApp.PersistableIdle = delegate(WorkflowApplicationIdleEventArgs e)
   {
       return PersistableIdleAction.Persist;
   };
   ```

> [!NOTE]
> Bkz: [nasıl yapılır: oluşturma ve uzun çalışan iş akışı çalıştırma](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md) adımında [başlangıç Öğreticisi](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md) adım adım yönergeler için.  

## <a name="enabling-persistence-for-self-hosted-workflow-services-that-use-the-workflowservicehost"></a>WorkflowServiceHost kullanan şirket içinde barındırılan iş akışı hizmetleri için kalıcılığı etkinleştirme

Kullanan şirket içinde barındırılan iş akışı hizmetleri için kalıcılığı etkinleştirebilirsiniz <xref:System.ServiceModel.WorkflowServiceHost> kullanarak program aracılığıyla <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> sınıfı veya <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> sınıfı.  

### <a name="using-the-sqlworkflowinstancestorebehavior-class"></a>SqlWorkflowInstanceStoreBehavior sınıfını kullanma  

Aşağıdaki yordamı kullanmak için adımları içeren <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> şirket içinde barındırılan iş akışı hizmetleri için kalıcılığı etkinleştirme sınıfı.  

#### <a name="to-enable-persistence-using-sqlworkflowinstancestorebehavior"></a>Kalıcılık SqlWorkflowInstanceStoreBehavior kullanarak etkinleştirmek için

1.  System.ServiceModel.dll bir başvuru ekleyin.  
  
2.  Aşağıdaki deyim, varolan "kullanma" deyimleri sonra kaynak dosyasının en üstüne ekleyin.  
  
    ```csharp
    using System.ServiceModel.Activities.Description;
    ```

3.  Bir örneğini oluşturmak `WorkflowServiceHost` ve iş akışı hizmeti için uç noktalar ekleyin.  
  
    ```csharp
    WorkflowServiceHost host = new WorkflowServiceHost(new CountingWorkflow(), new Uri(hostBaseAddress));  
    host.AddServiceEndpoint("ICountingWorkflow", new BasicHttpBinding(), "");  
    ``` 

4.  Oluşturmak bir `SqlWorkflowInstanceStoreBehavior` nesne ve davranışları nesne özelliklerini ayarlamak için.  
  
    ```csharp
    SqlWorkflowInstanceStoreBehavior instanceStoreBehavior = new SqlWorkflowInstanceStoreBehavior(connectionString);
    instanceStoreBehavior.HostLockRenewalPeriod = new TimeSpan(0, 0, 5);
    instanceStoreBehavior.InstanceCompletionAction = InstanceCompletionAction.DeleteAll;
    instanceStoreBehavior.InstanceLockedExceptionAction = InstanceLockedExceptionAction.AggressiveRetry;
    instanceStoreBehavior.InstanceEncodingOption = InstanceEncodingOption.GZip;
    instanceStoreBehavior.RunnableInstancesDetectionPeriod = new TimeSpan("00:00:02");
    host.Description.Behaviors.Add(instanceStoreBehavior);
    ```

5.  İş akışı hizmeti konağı açın.

    ```csharp
    host.Open();
    ```

### <a name="using-the-durableinstancingoptions-property"></a>DurableInstancingOptions özelliğini kullanma

Zaman `SqlWorkflowInstanceStoreBehavior` uygulanan `DurableInstancingOptions.InstanceStore` üzerinde `WorkflowServiceHost` ayarlanır `SqlWorkflowInstanceStore` yapılandırma değerleri kullanılarak oluşturulan bir nesne. Program üzerinden ayarlamak için aynısını yapabilir <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> özelliği `WorkflowServiceHost` kullanmadan `SqlWorkflowInstanceStoreBehavior` aşağıdaki kod örneğinde gösterildiği gibi sınıf.  

```csharp
workflowServiceHost.DurableInstancingOptions.InstanceStore = sqlInstanceStoreObject;  
```

## <a name="enabling-persistence-for-was-hosted-workflow-services-that-use-the-workflowservicehost-using-a-configuration-file"></a>Bir yapılandırma dosyası kullanarak WorkflowServiceHost kullanan WAS-Hosted iş akışı hizmetleri için kalıcılığı etkinleştirme

Şirket içinde barındırılan veya Windows İşlem Etkinleştirme hizmeti WAS barındırılan iş akışı hizmetleri için kalıcılığı yapılandırma dosyası kullanarak etkinleştirebilirsiniz. Şirket içinde barındırılan iş akışı Hizmetleri gibi WorkflowServiceHost WAS barındırılan iş akışı hizmeti kullanır.  
  
`SqlWorkflowInstanceStoreBehavior`, Uygun şekilde değiştirmenize olanak sağlayan bir hizmet davranışını [SQL iş akışı örneği Store](../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md) özellikleri aracılığıyla XML yapılandırması. WAS barındırılan iş akışı hizmetleri için Web.config dosyasını kullanın. Aşağıdaki yapılandırma örnek SQL iş akışı örneği Store kullanarak yapılandırmak nasıl gösterir `sqlWorkflowInstanceStore` yapılandırma dosyasında bir davranış öğesi.  
  
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
  
İçin değerler ayarlamazsanız `connectionString` veya `connectionStringName` özelliği, SQL iş akışı örneği Store kullanan varsayılan bağlantı dizesi adlı `DefaultSqlWorkflowInstanceStoreConnectionString`.  
  
Zaman `SqlWorkflowInstanceStoreBehavior` uygulanan `DurableInstancingOptions.InstanceStore` üzerinde `WorkflowServiceHost` ayarlanır `SqlWorkflowInstanceStore` yapılandırma değerleri kullanılarak oluşturulan bir nesne. Programlı olarak kullanmak için aynısını yapabilir `SqlWorkflowInstanceStore` ile `WorkflowServiceHost` hizmet davranış öğesi kullanmadan.  
  
```csharp
workflowServiceHost.DurableInstancingOptions.InstanceStore = sqlInstanceStoreObject;
```
  
> [!IMPORTANT]
> Kullanıcı adları ve parolalar gibi hassas bilgileri Web.config dosyasında depolamaz önerilir. Web.config dosyasındaki hassas bilgileri depolamak, dosya sistemine erişim denetim listeleri (ACL'ler) kullanarak güvenli Web.config dosyasına erişim. Ayrıca, ayrıca yapılandırma değerleri bir yapılandırma dosyasında belirtildiği gibi güvenliğini sağlamak [şifreleme yapılandırma bilgilerini kullanarak korumalı Yapılandırması](https://go.microsoft.com/fwlink/?LinkId=178419).

### <a name="machineconfig-elements-related-to-the-sql-workflow-instance-store-feature"></a>SQL iş akışı örneği Store özelliğiyle ilgili Machine.config öğeleri

[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] Yükleme Machine.config dosyasının SQL iş akışı örneği Store özellikle ilgili aşağıdaki öğeleri ekler:  

-   Aşağıdaki davranışı uzantı öğesi Machine.config dosyasına ekler; böylece kullanabileceğiniz <`sqlWorkflowInstanceStore`> hizmetleriniz için kalıcılığı yapılandırma yapılandırma dosyasındaki hizmet davranış öğesi.

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
