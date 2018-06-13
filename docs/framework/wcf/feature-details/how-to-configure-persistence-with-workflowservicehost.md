---
title: 'Nasıl yapılır: WorkflowServiceHost ile Kalıcılığı Yapılandırma'
ms.date: 03/30/2017
ms.assetid: e31cd4df-13a3-4a9a-9be8-5243e0055356
ms.openlocfilehash: 9035ded1ca533d9b2107d90f605e15c9ce915965
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33493214"
---
# <a name="how-to-configure-persistence-with-workflowservicehost"></a>Nasıl yapılır: WorkflowServiceHost ile Kalıcılığı Yapılandırma
Bu konu, iş akışları barındırılan için Kalıcılık etkinleştirmek için SQL iş akışı örneği depolama özelliğini yapılandırmak açıklar <xref:System.ServiceModel.Activities.WorkflowServiceHost> bir yapılandırma dosyası kullanarak. SQL iş akışı örneği deposuna özelliği kullanmadan önce iş akışı örnekleri sürdürmek için kullanılan bir SQL veritabanı oluşturmanız gerekir. Daha fazla bilgi için bkz: [nasıl yapılır: iş akışları ve iş akışı hizmetleri için SQL kalıcılığını etkinleştirmek](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-configuration"></a>Yapılandırmada SQL iş akışı örneği deposunu yapılandırmak için  
  
1.  SQL iş akışı örneği deposunun özelliklerini aracılığıyla yapılandırılabilir <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, XML yapılandırma ayarlarıyla değiştirmenize izin verir hizmet davranışı. Aşağıdaki yapılandırma örneği kullanarak SQL iş akışı örneği deposuna yapılandırmak gösterilmiştir <`sqlWorkflowInstanceStore`> davranışı öğesi bir yapılandırma dosyası.  
  
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
  
     SQL iş akışı örneği depolama yapılandırma hakkında daha fazla bilgi için bkz: [nasıl yapılır: iş akışları ve iş akışı hizmetleri için SQL kalıcılığını etkinleştirmek](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md). İçin bireysel ayarlar hakkında daha fazla bilgi için <`sqlWorkflowInstanceStore`> davranışı öğesi bkz [SQL iş akışı örneği deposuna](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md). Windows Server App Fabric kendi Kalıcılık deposuna sağlar. Daha fazla bilgi için bkz: [Windows Server App Fabric kalıcılığı](http://go.microsoft.com/fwlink/?LinkId=193121).  
  
    > [!NOTE]
    >  Önceki yapılandırma örneği Basitleştirilmiş yapılandırmasını kullanır. Daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/simplified-configuration.md)  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-code"></a>SQL iş akışı örneği deposu yapılandırma  
  
1.  SQL iş akışı örneği deposunun özelliklerini aracılığıyla yapılandırılabilir <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, kod aracılığıyla ayarlarını değiştirmenizi sağlar hizmet davranışı. Aşağıdaki örnek SQL iş akışı örneği deposuna kullanarak yapılandırmak nasıl gösterir <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> kodu davranışı öğesi  
  
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
  
     SQL iş akışı örneği depolama yapılandırma hakkında daha fazla bilgi için bkz: [nasıl yapılır: iş akışları ve iş akışı hizmetleri için SQL kalıcılığını etkinleştirmek](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md). İçin bireysel ayarlar hakkında daha fazla bilgi için <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> davranışı öğesi bkz [SQL iş akışı örneği deposuna](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md). Windows Server App Fabric kendi Kalıcılık deposuna sağlar. Daha fazla bilgi için bkz: [Windows Server App Fabric kalıcılığı](http://go.microsoft.com/fwlink/?LinkId=193121).  
  
    > [!NOTE]
    >  Önceki yapılandırma örneği Basitleştirilmiş yapılandırmasını kullanır. Daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/simplified-configuration.md)  
  
     Program aracılığıyla kalıcılığı yapılandırma örneği için bkz: [nasıl yapılır: iş akışları ve iş akışı hizmetleri kalıcılığı etkinleştir](../../../../docs/framework/windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İş Akışı Hizmetleri](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [İş Akışı Kalıcılığı](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md)  
 [Windows Server App Fabric kalıcılığı](http://go.microsoft.com/fwlink/?LinkId=193121)
