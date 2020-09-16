---
title: 'Nasıl yapılır: WorkflowServiceHost ile Kalıcılığı Yapılandırma'
ms.date: 03/30/2017
ms.assetid: e31cd4df-13a3-4a9a-9be8-5243e0055356
ms.openlocfilehash: 93397923154d780ed3b714bf0bb95c15bc71bbfb
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556316"
---
# <a name="how-to-configure-persistence-with-workflowservicehost"></a>Nasıl yapılır: WorkflowServiceHost ile Kalıcılığı Yapılandırma
Bu konuda, <xref:System.ServiceModel.Activities.WorkflowServiceHost> bir yapılandırma dosyası kullanılarak içinde barındırılan iş akışları için kalıcılığı etkinleştirmek üzere SQL Iş akışı örnek deposu özelliğinin nasıl yapılandırılacağı açıklanmaktadır. SQL Iş akışı örnek deposu özelliğini kullanmadan önce, iş akışı örneklerini kalıcı hale getirmek için kullanılan bir SQL veritabanı oluşturmanız gerekir. Daha fazla bilgi için bkz. [nasıl yapılır: Iş akışları ve Iş akışı hizmetleri IÇIN SQL kalıcılığını etkinleştirme](../../windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-configuration"></a>Yapılandırmada SQL Iş akışı örnek deposunu yapılandırmak için  
  
1. SQL iş akışı örnek deposunun özellikleri, <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> ayarları XML yapılandırması aracılığıyla değiştirmenize olanak tanıyan bir hizmet davranışı aracılığıyla yapılandırılabilir. Aşağıdaki yapılandırma örneği, `sqlWorkflowInstanceStore` bir yapılandırma dosyasında <> Behavior öğesi KULLANıLARAK SQL iş akışı örnek deposunun nasıl yapılandırılacağını gösterir.  
  
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
  
     SQL iş akışı örnek deposunun nasıl yapılandırılacağı hakkında daha fazla bilgi için bkz. [nasıl yapılır: Iş akışları ve Iş akışı hizmetleri IÇIN SQL kalıcılığını etkinleştirme](../../windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md). <> davranış öğesinin bireysel ayarları hakkında daha fazla bilgi için `sqlWorkflowInstanceStore` bkz. [SQL Workflow örnek deposu](../../windows-workflow-foundation/sql-workflow-instance-store.md). Windows Server App Fabric kendi Kalıcılık mağazasını sağlar. Daha fazla bilgi için bkz. [Windows Server App Fabric kalıcılığı](/previous-versions/appfabric/ee677272(v=azure.10)).  
  
    > [!NOTE]
    > Önceki yapılandırma örneği Basitleştirilmiş yapılandırma kullanır. Daha fazla bilgi için bkz. [Basitleştirilmiş yapılandırma](../simplified-configuration.md)  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-code"></a>SQL Iş akışı örnek deposunu kodda yapılandırmak için  
  
1. SQL iş akışı örnek deposunun özellikleri, <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> ayarları kod aracılığıyla değiştirmenize olanak tanıyan bir hizmet davranışı aracılığıyla yapılandırılabilir. Aşağıdaki örnek, <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> bir koddaki davranış öğesi KULLANıLARAK SQL iş akışı örnek deposunun nasıl yapılandırılacağını gösterir  
  
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
  
     SQL iş akışı örnek deposunun nasıl yapılandırılacağı hakkında daha fazla bilgi için bkz. [nasıl yapılır: Iş akışları ve Iş akışı hizmetleri IÇIN SQL kalıcılığını etkinleştirme](../../windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md). Davranış öğesinin bireysel ayarları hakkında daha fazla bilgi için <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> bkz. [SQL Workflow örnek deposu](../../windows-workflow-foundation/sql-workflow-instance-store.md). Windows Server App Fabric kendi Kalıcılık mağazasını sağlar. Daha fazla bilgi için bkz. [Windows Server App Fabric kalıcılığı](/previous-versions/appfabric/ee677272(v=azure.10)).  
  
    > [!NOTE]
    > Önceki yapılandırma örneği Basitleştirilmiş yapılandırma kullanır. Daha fazla bilgi için bkz. [Basitleştirilmiş yapılandırma](../simplified-configuration.md)  
  
     Kalıcılığın nasıl yapılandırılacağı hakkında bir örnek için bkz. [nasıl yapılır: Iş akışları ve Iş akışı hizmetleri Için kalıcılığı etkinleştirme](../../windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İş Akışı Hizmetleri](workflow-services.md)
- [İş Akışı Kalıcılığı](../../windows-workflow-foundation/workflow-persistence.md)
- [Windows Server App Fabric kalıcılığı](/previous-versions/appfabric/ee677272(v=azure.10))
