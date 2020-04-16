---
title: 'Nasıl yapılır: WorkflowServiceHost ile Kalıcılığı Yapılandırma'
ms.date: 03/30/2017
ms.assetid: e31cd4df-13a3-4a9a-9be8-5243e0055356
ms.openlocfilehash: 4bfa66a895ae9af9cb87ff110dc82c8a8a922b49
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463845"
---
# <a name="how-to-configure-persistence-with-workflowservicehost"></a>Nasıl yapılır: WorkflowServiceHost ile Kalıcılığı Yapılandırma
Bu konu, bir yapılandırma dosyası kullanarak barındırılan <xref:System.ServiceModel.Activities.WorkflowServiceHost> iş akışları için kalıcılığı etkinleştirmek için SQL İş Akışı Örneği Deposu özelliğini nasıl yapılandırıştırılabildiğini açıklar. SQL İş Akışı Örneği Deposu özelliğini kullanmadan önce, iş akışı örneklerini kalıcı olarak sürdürmek için kullanılan bir SQL veritabanı oluşturmanız gerekir. Daha fazla bilgi için [bkz: İş Akışları ve İş Akışı Hizmetleri için SQL Kalıcılığını etkinleştirin.](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md)  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-configuration"></a>Sql İş Akışı Örnek Mağazasını Yapılandırmada Yapılandırmada Yapılandırmak için  
  
1. SQL iş akışı örneği deposunun <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>özellikleri, XML yapılandırması ile ayarları değiştirmenize olanak tanıyan bir hizmet davranışı aracılığıyla yapılandırılabilir. Aşağıdaki yapılandırma örneği, yapılandırma dosyasındaki <`sqlWorkflowInstanceStore`> davranış öğesini kullanarak SQL iş akışı örnek deposunun nasıl yapılandırılabildiğini gösterir.  
  
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
            </sqlWorkflowInstanceStore>  
        </behavior>  
    </serviceBehaviors>  
    ```  
  
     SQL iş akışı örneği deposunun nasıl yapılandırılabildiğini hakkında daha fazla bilgi için [bkz.](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md) <`sqlWorkflowInstanceStore`> davranış öğesinin tek tek ayarları hakkında daha fazla bilgi için [SQL İş Akışı Örneği Deposu'na](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md)bakın. Windows Server App Fabric kendi kalıcılık deposu sağlar. Daha fazla bilgi için [Windows Server App Kumaş Kalıcılığı'na](https://docs.microsoft.com/previous-versions/appfabric/ee677272(v=azure.10))bakın.  
  
    > [!NOTE]
    > Önceki yapılandırma örneği basitleştirilmiş yapılandırma kullanır. Daha fazla bilgi için [bkz.](../../../../docs/framework/wcf/simplified-configuration.md)  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-code"></a>Koddaki SQL İş Akışı Örnek Deposunu Yapılandırmak için  
  
1. SQL iş akışı örneği deposunun <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>özellikleri, kodları aracılığıyla ayarları değiştirmenize olanak sağlayan bir hizmet davranışı aracılığıyla yapılandırılabilir. Aşağıdaki örnek, bir koddaki davranış öğesini kullanarak <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> SQL iş akışı örnek deposunun nasıl yapılandırılabildiğini gösterir  
  
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
  
     SQL iş akışı örneği deposunun nasıl yapılandırılabildiğini hakkında daha fazla bilgi için [bkz.](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md) Davranış öğesiiçin tek tek ayarlar hakkında daha fazla bilgi için [SQL İş Akışı Örneği Deposu'na](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md)bakın. <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> Windows Server App Fabric kendi kalıcılık deposu sağlar. Daha fazla bilgi için [Windows Server App Kumaş Kalıcılığı'na](https://docs.microsoft.com/previous-versions/appfabric/ee677272(v=azure.10))bakın.  
  
    > [!NOTE]
    > Önceki yapılandırma örneği basitleştirilmiş yapılandırma kullanır. Daha fazla bilgi için [bkz.](../../../../docs/framework/wcf/simplified-configuration.md)  
  
     Kalıcılığı programlı olarak yapılandırmaya yönelik bir örnek için [bkz.](../../../../docs/framework/windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İş Akışı Hizmetleri](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [İş Akışı Kalıcılığı](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md)
- [Windows Server App Kumaş Kalıcılığı](https://docs.microsoft.com/previous-versions/appfabric/ee677272(v=azure.10))
