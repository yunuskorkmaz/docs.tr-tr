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
# <a name="how-to-enable-sql-persistence-for-workflows-and-workflow-services"></a>Nasıl yapılır: iş akışları ve iş akışı hizmetleri için SQL kalıcılığı etkinleştir
Bu konuda, iş akışlarınızı kalıcılığını etkinleştirmek için SQL iş akışı örneği deposuna özelliği yapılandırmayı açıklar ve iş akışı her ikisi de program aracılığıyla bir yapılandırma dosyası kullanarak hizmetleri ve.  
  
 Windows Server App Fabric kalıcılığı yapılandırma işlemini basitleştirir. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][App Fabric kalıcılığı yapılandırma](http://go.microsoft.com/fwlink/?LinkId=201204)  
  
 SQL iş akışı örneği depolama özelliğini kullanmadan önce iş akışı örnekleri kalıcı hale getirmek için özelliğini kullanan bir veritabanı oluşturun. [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] Kurulum programı %WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN klasörüne SQL iş akışı örneği deposuna özelliğiyle ilişkili SQL komut dosyalarını kopyalar. Bu komut dosyaları, iş akışı örnekleri kalıcı hale getirmek için kullanılacak SQL iş akışı örneği deposu istediğiniz SQL Server 2005 veya SQL Server 2008 veritabanına karşı çalışırlar. İlk SqlWorkflowInstanceStoreSchema.sql dosyasını çalıştırın ve sonra SqlWorkflowInstanceStoreLogic.sql dosyasını çalıştırın.  
  
> [!NOTE]
>  Yeni bir veritabanı için Kalıcılık veritabanını temizlemek için aşağıdaki sırayla %WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN betikleri çalıştırın.  
>   
>  1.  SqlWorkflowInstanceStoreSchema.sql  
> 2.  SqlWorkflowInstanceStoreLogic.sql  
  
> [!IMPORTANT]
>  Kalıcılık veritabanı oluşturmazsanız, bir ana iş akışları kalıcı hale getirmek çalıştığında SQL iş akışı örneği depolama özelliğini aşağıdakine benzer bir özel durum oluşturur.  
>   
>  System.Data.SqlClient.SqlException: saklı yordam 'System.Activities.DurableInstancing.CreateLockOwner' bulunamadı.  
  
 Aşağıdaki bölümlerde, iş akışları ve iş akışı hizmetleri SQL iş akışı örneği deposunu kullanan kalıcılığını etkinleştirmek açıklar. [!INCLUDE[crabout](../../../includes/crabout-md.md)]SQL iş akışı örneği deposuna özelliklerini görmek [özellikleri SQL iş akışı örneği deposuna](../../../docs/framework/windows-workflow-foundation/properties-of-sql-workflow-instance-store.md).  
  
## <a name="enabling-persistence-for-self-hosted-workflows-that-use-workflowapplication"></a>Kalıcılığı Self-Hosted WorkflowApplication kullanan iş akışları için etkinleştirme  
 Kalıcılık kullanan kendi kendini barındıran iş akışları için etkinleştirebilirsiniz <xref:System.Activities.WorkflowApplication> kullanarak program aracılığıyla <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> nesne modeli. Aşağıdaki yordam, bunu yapmak için adımları içerir.  
  
#### <a name="to-enable-persistence-for-self-hosted-workflows"></a>Kendini barındıran iş akışları kalıcılığını etkinleştirmek için  
  
1.  System.Activites.DurableInstancing.dll bir başvuru ekleyin.  
  
2.  Aşağıdaki deyim kaynak dosyasının en üstte varolan "kullanarak" ifadeleri sonra ekleyin.  
  
    ```csharp  
    using System.Activities.DurableInstancing;  
    ```  
  
3.  Oluşturmak bir <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> ve atayın <xref:System.Activities.WorkflowApplication.InstanceStore%2A> , <xref:System.Activities.WorkflowApplication> aşağıdaki kod örneğinde gösterildiği gibi.  
  
    ```csharp  
    SqlWorkflowInstanceStore store =   
        new SqlWorkflowInstanceStore("Server=.\\SQLEXPRESS;Initial Catalog=Persistence;Integrated Security=SSPI");  
  
    WorkflowApplication wfApp =  
        new WorkflowApplication(new Workflow1());  
  
    wfApp.InstanceStore = store;  
    ```  
  
    > [!NOTE]
    >  Bağlantı dizesi sunucu adı SQL Server sürümüne bağlı olarak farklı olabilir.  
  
4.  Çağırma <xref:System.Activities.WorkflowApplication.Persist%2A> yöntemi <xref:System.Activities.WorkflowApplication> bir iş akışını sürdürmek için nesne veya <xref:System.Activities.WorkflowApplication.Unload%2A> kalıcı hale getirmek ve bir iş akışı kaldırma için yöntem. Ayrıca işleyebilir <xref:System.Activities.WorkflowApplication.PersistableIdle%2A> olayı tarafından <xref:System.Activities.WorkflowApplication> nesne ve uygun döndürür (<xref:System.Activities.PersistableIdleAction.Persist> veya <xref:System.Activities.PersistableIdleAction.Unload>) üyesi <xref:System.Activities.PersistableIdleAction>.  
  
    ```csharp  
    wfApp.PersistableIdle = delegate(WorkflowApplicationIdleEventArgs e)  
    {  
        return PersistableIdleAction.Persist;  
    };  
    ```  
  
> [!NOTE]
>  Bkz [bir iş akışı uygulaması kalıcı](../../../docs/framework/windows-workflow-foundation/samples/persisting-a-workflow-application.md) adresindeki örnek [kalıcılığı](../../../docs/framework/windows-workflow-foundation/samples/persistence.md) bir örneğini kullanarak da iş akışları kalıcılığını etkinleştirmek için <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>ve [nasıl yapılır: oluşturma ve uzun çalıştırma İş akışını çalıştıran](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md) adımında [başlangıç Öğreticisi](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md) adım adım yönergeler için.  
  
## <a name="enabling-persistence-for-self-hosted-workflow-services-that-use-the-workflowservicehost"></a>WorkflowServiceHost kullanan Self-Hosted iş akışı hizmetleri kalıcılığını etkinleştirme  
 Kullanan kendi kendini barındıran iş akışı hizmetleri kalıcılığını etkinleştirebilirsiniz <xref:System.ServiceModel.WorkflowServiceHost> kullanarak program aracılığıyla <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> sınıfı veya <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> sınıfı.  
  
### <a name="using-the-sqlworkflowinstancestorebehavior-class"></a>SqlWorkflowInstanceStoreBehavior sınıfını kullanma  
 Aşağıdaki yordamı kullanmak için adımları içerir <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> kendini barındıran iş akışı hizmetleri kalıcılığını etkinleştirmek için sınıf.  
  
##### <a name="to-enable-persistence-using-sqlworkflowinstancestorebehavior"></a>Kalıcılığı SqlWorkflowInstanceStoreBehavior kullanarak etkinleştirmek için  
  
1.  System.ServiceModel.dll bir başvuru ekleyin.  
  
2.  Aşağıdaki deyim kaynak dosyasının en üstte varolan "kullanarak" ifadeleri sonra ekleyin.  
  
    ```csharp  
    using System.ServiceModel.Activities.Description;  
    ```  
  
3.  Bir örneğini oluşturmak `WorkflowServiceHost` ve iş akışı hizmeti için uç nokta ekleyin.  
  
    ```  
    WorkflowServiceHost host = new WorkflowServiceHost(new CountingWorkflow(), new Uri(hostBaseAddress));  
    host.AddServiceEndpoint("ICountingWorkflow", new BasicHttpBinding(), "");  
    ```  
  
4.  Oluşturmak bir `SqlWorkflowInstanceStoreBehavior` nesne ve davranış nesnesinin özelliklerini ayarlamak için.  
  
    ```csharp  
    SqlWorkflowInstanceStoreBehavior instanceStoreBehavior = new SqlWorkflowInstanceStoreBehavior(connectionString);  
    instanceStoreBehavior.HostLockRenewalPeriod = new TimeSpan(0, 0, 5);  
    instanceStoreBehavior.InstanceCompletionAction = InstanceCompletionAction.DeleteAll;  
    instanceStoreBehavior.InstanceLockedExceptionAction = InstanceLockedExceptionAction.AggressiveRetry;  
    instanceStoreBehavior.InstanceEncodingOption = InstanceEncodingOption.GZip;  
    instanceStoreBehavior.RunnableInstancesDetectionPeriod = new TimeSpan("00:00:02");  
    host.Description.Behaviors.Add(instanceStoreBehavior);  
    ```  
  
5.  İş akışı hizmeti ana bilgisayarı açın.  
  
    ```vb  
    host.Open();  
    ```  
  
> [!IMPORTANT]
>  Bkz: [yerleşik yapılandırma](../../../docs/framework/windows-workflow-foundation/samples/built-in-configuration.md) adresindeki örnek [kalıcılığı](../../../docs/framework/windows-workflow-foundation/samples/persistence.md) bir örneğini kullanarak iş akışı hizmetleri kalıcılığını etkinleştirmek için `SqlWorkflowInstanceStoreBehavior` sınıfı.  
  
### <a name="using-the-durableinstancingoptions-property"></a>DurableInstancingOptions özelliğini kullanma  
 Zaman `SqlWorkflowInstanceStoreBehavior` uygulanan `DurableInstancingOptions.InstanceStore` üzerinde `WorkflowServiceHost` ayarlanır `SqlWorkflowInstanceStore` yapılandırma değerlerini kullanılarak oluşturulan nesne. Program aracılığıyla ayarlamak için aynısını yapabilir <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> özelliği `WorkflowServiceHost` kullanmadan `SqlWorkflowInstanceStoreBehavior` sınıfı aşağıdaki kod örneğinde gösterildiği gibi.  
  
```  
workflowServiceHost.DurableInstancingOptions.InstanceStore = sqlInstanceStoreObject;  
```  
  
## <a name="enabling-persistence-for-was-hosted-workflow-services-that-use-the-workflowservicehost-using-a-configuration-file"></a>Bir yapılandırma dosyası kullanarak WorkflowServiceHost kullanan WAS-Hosted iş akışı hizmetleri kalıcılığını etkinleştirme  
 Bir yapılandırma dosyası kullanarak kendini barındıran veya Windows İşlem Etkinleştirme hizmeti WAS barındırılan iş akışı hizmetleri kalıcılığını etkinleştirebilirsiniz. Kendini barındıran iş akışı Hizmetleri gibi bir iş akışı WAS barındırılan hizmet WorkflowServiceHost kullanır.  
  
 `SqlWorkflowInstanceStoreBehavior`, Uygun şekilde değiştirmenize olanak verir hizmet davranışı [SQL iş akışı örneği deposuna](../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md) XML yapılandırma yoluyla özellikleri. İş akışı WAS barındırılan hizmetler için Web.config dosyasını kullanın. Aşağıdaki yapılandırma örneği kullanarak SQL iş akışı örneği deposuna yapılandırmak gösterilmiştir `sqlWorkflowInstanceStore` davranışı öğesi bir yapılandırma dosyası.  
  
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
  
 İçin değerler ayarlamazsanız `connectionString` veya `connectionStringName` özelliği, SQL iş akışı örneği deposuna kullanan varsayılan bağlantı dizesi adlı `DefaultSqlWorkflowInstanceStoreConnectionString`.  
  
 Zaman `SqlWorkflowInstanceStoreBehavior` uygulanan `DurableInstancingOptions.InstanceStore` üzerinde `WorkflowServiceHost` ayarlanır `SqlWorkflowInstanceStore` yapılandırma değerlerini kullanılarak oluşturulan nesne. Program aracılığıyla kullanmak için aynısını yapabilir `SqlWorkflowInstanceStore` ile `WorkflowServiceHost` hizmet davranışı öğesinin kullanmadan.  
  
```  
workflowServiceHost.DurableInstancingOptions.InstanceStore = sqlInstanceStoreObject;  
```  
  
> [!IMPORTANT]
>  Kullanıcı adları ve parolalar gibi hassas bilgileri Web.config dosyasında depolamaz önerilir. Web.config dosyasında gizli bilgileri depoluyorsa, dosya sistemi erişim denetim listeleri (ACL'ler) kullanılarak güvenli Web.config dosyasına erişimi. Ayrıca, ayrıca yapılandırma dosyasının içinde yapılandırma değerlerini bölümünde belirtildiği gibi güvenli hale getirebilirsiniz [şifreleme yapılandırma bilgilerini kullanarak korumalı Yapılandırması](http://go.microsoft.com/fwlink/?LinkId=178419).  
  
### <a name="machineconfig-elements-related-to-the-sql-workflow-instance-store-feature"></a>SQL iş akışı örneği deposuna özelliğiyle ilgili Machine.config öğeleri  
 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] Yükleme Machine.config dosyasının SQL iş akışı örneği deposuna özellikle ilgili aşağıdaki öğeleri ekler:  
  
-   Aşağıdaki davranışı uzantı öğesi, Machine.config dosyasının ekler, böylece kullanabileceğiniz <`sqlWorkflowInstanceStore`> hizmet davranışı yapılandırma dosyasına hizmetleriniz için kalıcılığı yapılandırma öğesinde.  
  
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
