---
title: 'Nasıl yapılır: WorkflowServiceHost ile Kalıcılığı Yapılandırma'
ms.date: 03/30/2017
ms.assetid: e31cd4df-13a3-4a9a-9be8-5243e0055356
ms.openlocfilehash: 8485cfdfb3a8f62f04fc488ad28df86e609e17ad
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59086669"
---
# <a name="how-to-configure-persistence-with-workflowservicehost"></a>Nasıl yapılır: WorkflowServiceHost ile Kalıcılığı Yapılandırma
Bu konu, barındırılan iş akışları için kalıcılığını sağlamak için SQL iş akışı örneği Store özelliği yapılandırmayı açıklar <xref:System.ServiceModel.Activities.WorkflowServiceHost> bir yapılandırma dosyası kullanarak. SQL iş akışı örneği Store özelliği kullanmadan önce iş akışı örneği kalıcı hale getirmek için kullanılan bir SQL veritabanı oluşturmanız gerekir. Daha fazla bilgi için [nasıl yapılır: İş akışları ve iş akışı hizmetleri için SQL kalıcılığını](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-configuration"></a>SQL iş akışı örneği Store yapılandırmasında yapılandırmak için  
  
1.  SQL iş akışı örnek deposunun özellikleri aracılığıyla yapılandırılabilir <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, bir hizmet davranışını ayarlar XML yapılandırması üzerinden değiştirilmesine izin verir. Aşağıdaki yapılandırma örnek kullanan SQL iş akışı örnek deposu yapılandırma işlemi gösterilmektedir <`sqlWorkflowInstanceStore`> yapılandırma dosyasında bir davranış öğesi.  
  
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
  
     SQL iş akışı örnek deposu yapılandırma hakkında daha fazla bilgi için bkz. [nasıl yapılır: İş akışları ve iş akışı hizmetleri için SQL kalıcılığını](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md). İçin bireysel ayarlar hakkında daha fazla bilgi için <`sqlWorkflowInstanceStore`> davranış öğesi bkz [SQL iş akışı örneği Store](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md). Windows Server App Fabric kendi sürdürme deposundan sağlar. Daha fazla bilgi için [Windows Server App Fabric Kalıcılık](https://go.microsoft.com/fwlink/?LinkId=193121).  
  
    > [!NOTE]
    >  Basitleştirilmiş yapılandırma önceki yapılandırma örneği kullanır. Daha fazla bilgi için [Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/simplified-configuration.md)  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-code"></a>SQL iş akışı örneği Store kodda yapılandırmak için  
  
1.  SQL iş akışı örnek deposunun özellikleri aracılığıyla yapılandırılabilir <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, kod aracılığıyla ayarlarını değiştirmenize olanak sağlayan bir hizmet davranışı. Aşağıdaki örnek, SQL iş akışı örnek deposu kullanarak yapılandırma işlemi gösterilmektedir <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> kodu davranış öğesi  
  
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
  
     SQL iş akışı örnek deposu yapılandırma hakkında daha fazla bilgi için bkz. [nasıl yapılır: İş akışları ve iş akışı hizmetleri için SQL kalıcılığını](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md). İçin bireysel ayarlar hakkında daha fazla bilgi için <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> davranış öğesi bkz [SQL iş akışı örneği Store](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md). Windows Server App Fabric kendi sürdürme deposundan sağlar. Daha fazla bilgi için [Windows Server App Fabric Kalıcılık](https://go.microsoft.com/fwlink/?LinkId=193121).  
  
    > [!NOTE]
    >  Basitleştirilmiş yapılandırma önceki yapılandırma örneği kullanır. Daha fazla bilgi için [Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/simplified-configuration.md)  
  
     Program aracılığıyla kalıcılığı yapılandırma örneği için bkz. [nasıl yapılır: İş akışları ve iş akışı hizmetleri için kalıcılığı etkinleştir](../../../../docs/framework/windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İş Akışı Hizmetleri](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [İş Akışı Kalıcılığı](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md)
- [Windows Server AppFabric kalıcılığı](https://go.microsoft.com/fwlink/?LinkId=193121)
