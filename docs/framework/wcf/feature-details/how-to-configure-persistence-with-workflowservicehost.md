---
title: 'Nasıl yapılır: WorkflowServiceHost ile Kalıcılığı Yapılandırma'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e31cd4df-13a3-4a9a-9be8-5243e0055356
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8a11ab534cbb643d17985670e202954313f5a068
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
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
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)] SQL iş akışı örneği depolama yapılandırma hakkında [nasıl yapılır: iş akışları ve iş akışı hizmetleri için SQL kalıcılığını etkinleştirmek](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)] için bireysel ayarlar <`sqlWorkflowInstanceStore`> davranışı öğesi bkz [SQL iş akışı örneği deposuna](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md). Windows Server App Fabric kendi Kalıcılık deposuna sağlar. Daha fazla bilgi için bkz: [Windows Server App Fabric kalıcılığı](http://go.microsoft.com/fwlink/?LinkId=193121).  
  
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
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)] SQL iş akışı örneği depolama yapılandırma hakkında [nasıl yapılır: iş akışları ve iş akışı hizmetleri için SQL kalıcılığını etkinleştirmek](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)] için bireysel ayarlar <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> davranışı öğesi bkz [SQL iş akışı örneği deposuna](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md). Windows Server App Fabric kendi Kalıcılık deposuna sağlar. Daha fazla bilgi için bkz: [Windows Server App Fabric kalıcılığı](http://go.microsoft.com/fwlink/?LinkId=193121).  
  
    > [!NOTE]
    >  Önceki yapılandırma örneği Basitleştirilmiş yapılandırmasını kullanır. Daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/simplified-configuration.md)  
  
     Program aracılığıyla kalıcılığı yapılandırma örneği için bkz: [nasıl yapılır: iş akışları ve iş akışı hizmetleri kalıcılığı etkinleştir](../../../../docs/framework/windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İş Akışı Hizmetleri](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [İş Akışı Kalıcılığı](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md)  
 [Windows Server App Fabric kalıcılığı](http://go.microsoft.com/fwlink/?LinkId=193121)
