---
title: 'Nasıl yapılır: WorkflowServiceHost ile Kalıcılığı Yapılandırma'
ms.date: 03/30/2017
ms.assetid: e31cd4df-13a3-4a9a-9be8-5243e0055356
ms.openlocfilehash: 2cae73bd503afec6ddd1faf435645ebc21f4fc76
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968479"
---
# <a name="how-to-configure-persistence-with-workflowservicehost"></a>Nasıl yapılır: WorkflowServiceHost ile Kalıcılığı Yapılandırma
Bu konuda, bir yapılandırma dosyası kullanılarak içinde <xref:System.ServiceModel.Activities.WorkflowServiceHost> barındırılan iş akışları için kalıcılığı etkinleştirmek üzere SQL iş akışı örnek deposu özelliğinin nasıl yapılandırılacağı açıklanmaktadır. SQL Iş akışı örnek deposu özelliğini kullanmadan önce, iş akışı örneklerini kalıcı hale getirmek için kullanılan bir SQL veritabanı oluşturmanız gerekir. Daha fazla bilgi için [nasıl yapılır: Iş akışları ve Iş akışı Hizmetleri](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md)için SQL kalıcılığı etkinleştirin.  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-configuration"></a>Yapılandırmada SQL Iş akışı örnek deposunu yapılandırmak için  
  
1. SQL iş akışı örnek deposunun özellikleri, ayarları XML yapılandırması aracılığıyla değiştirmenize olanak <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>tanıyan bir hizmet davranışı aracılığıyla yapılandırılabilir. Aşağıdaki yapılandırma örneği, bir yapılandırma dosyasında <`sqlWorkflowInstanceStore`> Behavior öğesi kullanılarak SQL iş akışı örnek deposunun nasıl yapılandırılacağını gösterir.  
  
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
  
     SQL iş akışı örnek deposunun nasıl yapılandırılacağı hakkında daha fazla bilgi için bkz [. nasıl yapılır: Iş akışları ve Iş akışı Hizmetleri](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md)için SQL kalıcılığı etkinleştirin. <`sqlWorkflowInstanceStore`> Davranış öğesinin bireysel ayarları hakkında daha fazla bilgi için bkz. [SQL Workflow örnek deposu](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md). Windows Server App Fabric kendi Kalıcılık mağazasını sağlar. Daha fazla bilgi için bkz. [Windows Server App Fabric kalıcılığı](https://go.microsoft.com/fwlink/?LinkId=193121).  
  
    > [!NOTE]
    > Önceki yapılandırma örneği Basitleştirilmiş yapılandırma kullanır. Daha fazla bilgi için bkz. [Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/simplified-configuration.md)  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-code"></a>SQL Iş akışı örnek deposunu kodda yapılandırmak için  
  
1. SQL iş akışı örnek deposunun özellikleri, ayarları kod aracılığıyla değiştirmenize olanak tanıyan <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>bir hizmet davranışı aracılığıyla yapılandırılabilir. Aşağıdaki örnek, bir koddaki <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> davranış öğesi kullanılarak SQL iş akışı örnek deposunun nasıl yapılandırılacağını gösterir  
  
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
  
     SQL iş akışı örnek deposunun nasıl yapılandırılacağı hakkında daha fazla bilgi için bkz [. nasıl yapılır: Iş akışları ve Iş akışı Hizmetleri](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md)için SQL kalıcılığı etkinleştirin. <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> Davranış öğesinin bireysel ayarları hakkında daha fazla bilgi için bkz. [SQL Workflow örnek deposu](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md). Windows Server App Fabric kendi Kalıcılık mağazasını sağlar. Daha fazla bilgi için bkz. [Windows Server App Fabric kalıcılığı](https://go.microsoft.com/fwlink/?LinkId=193121).  
  
    > [!NOTE]
    > Önceki yapılandırma örneği Basitleştirilmiş yapılandırma kullanır. Daha fazla bilgi için bkz. [Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/simplified-configuration.md)  
  
     Kalıcılığı programsal olarak yapılandırma hakkında bir örnek için bkz [. nasıl yapılır: Iş akışları ve Iş akışı Hizmetleri](../../../../docs/framework/windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md)için kalıcılığı etkinleştirin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İş Akışı Hizmetleri](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [İş Akışı Kalıcılığı](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md)
- [Windows Server App Fabric kalıcılığı](https://go.microsoft.com/fwlink/?LinkId=193121)
