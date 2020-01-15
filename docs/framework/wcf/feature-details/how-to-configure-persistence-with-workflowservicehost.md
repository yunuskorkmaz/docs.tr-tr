---
title: 'Nasıl yapılır: WorkflowServiceHost ile Kalıcılığı Yapılandırma'
ms.date: 03/30/2017
ms.assetid: e31cd4df-13a3-4a9a-9be8-5243e0055356
ms.openlocfilehash: 7b65b89db674a624f7dfbf8ca816e0f0c2d2ff80
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/15/2020
ms.locfileid: "75963475"
---
# <a name="how-to-configure-persistence-with-workflowservicehost"></a>Nasıl yapılır: WorkflowServiceHost ile Kalıcılığı Yapılandırma
Bu konuda, bir yapılandırma dosyası kullanarak <xref:System.ServiceModel.Activities.WorkflowServiceHost> içinde barındırılan iş akışları için kalıcılığı etkinleştirmek üzere SQL Workflow örnek deposu özelliğinin nasıl yapılandırılacağı açıklanmaktadır. SQL Iş akışı örnek deposu özelliğini kullanmadan önce, iş akışı örneklerini kalıcı hale getirmek için kullanılan bir SQL veritabanı oluşturmanız gerekir. Daha fazla bilgi için bkz. [nasıl yapılır: Iş akışları ve Iş akışı hizmetleri IÇIN SQL kalıcılığını etkinleştirme](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-configuration"></a>Yapılandırmada SQL Iş akışı örnek deposunu yapılandırmak için  
  
1. SQL iş akışı örneği deposunun özellikleri, ayarları XML yapılandırması aracılığıyla değiştirmenize olanak tanıyan bir hizmet davranışı olan <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>aracılığıyla yapılandırılabilir. Aşağıdaki yapılandırma örneği, bir yapılandırma dosyasında <`sqlWorkflowInstanceStore`> davranış öğesi kullanılarak SQL iş akışı örnek deposunun nasıl yapılandırılacağını gösterir.  
  
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
  
     SQL iş akışı örnek deposunun nasıl yapılandırılacağı hakkında daha fazla bilgi için bkz. [nasıl yapılır: Iş akışları ve Iş akışı hizmetleri IÇIN SQL kalıcılığını etkinleştirme](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md). `sqlWorkflowInstanceStore`> davranış öğesi için bireysel ayarlar hakkında daha fazla bilgi için bkz. [SQL Workflow örnek deposu](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md). Windows Server App Fabric kendi Kalıcılık mağazasını sağlar. Daha fazla bilgi için bkz. [Windows Server App Fabric kalıcılığı](https://docs.microsoft.com/previous-versions/appfabric/ee677272(v=azure.10)).  
  
    > [!NOTE]
    > Önceki yapılandırma örneği Basitleştirilmiş yapılandırma kullanır. Daha fazla bilgi için bkz. [Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/simplified-configuration.md)  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-code"></a>SQL Iş akışı örnek deposunu kodda yapılandırmak için  
  
1. SQL iş akışı örneği deposunun özellikleri, ayarları kod aracılığıyla değiştirmenize olanak tanıyan bir hizmet davranışı olan <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>aracılığıyla yapılandırılabilir. Aşağıdaki örnek, bir koddaki <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> Behavior öğesi kullanılarak SQL iş akışı örnek deposunun nasıl yapılandırılacağını gösterir.  
  
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
  
     SQL iş akışı örnek deposunun nasıl yapılandırılacağı hakkında daha fazla bilgi için bkz. [nasıl yapılır: Iş akışları ve Iş akışı hizmetleri IÇIN SQL kalıcılığını etkinleştirme](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md). <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> davranış öğesinin bireysel ayarları hakkında daha fazla bilgi için bkz. [SQL Workflow örnek deposu](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md). Windows Server App Fabric kendi Kalıcılık mağazasını sağlar. Daha fazla bilgi için bkz. [Windows Server App Fabric kalıcılığı](https://docs.microsoft.com/previous-versions/appfabric/ee677272(v=azure.10)).  
  
    > [!NOTE]
    > Önceki yapılandırma örneği Basitleştirilmiş yapılandırma kullanır. Daha fazla bilgi için bkz. [Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/simplified-configuration.md)  
  
     Kalıcılığın nasıl yapılandırılacağı hakkında bir örnek için bkz. [nasıl yapılır: Iş akışları ve Iş akışı hizmetleri Için kalıcılığı etkinleştirme](../../../../docs/framework/windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İş Akışı Hizmetleri](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [İş Akışı Kalıcılığı](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md)
- [Windows Server App Fabric kalıcılığı](https://docs.microsoft.com/previous-versions/appfabric/ee677272(v=azure.10))
