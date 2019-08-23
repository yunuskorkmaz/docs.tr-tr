---
title: 'Nasıl yapılır: WorkflowServiceHost ile İş Akışı Tarafından İşlenmeyen Özel Durum Davranışını Yapılandırma'
ms.date: 03/30/2017
ms.assetid: 51b25c86-292c-43e4-8d13-273d2badc8ad
ms.openlocfilehash: aec2fd80e10ae1959b29c0883d51c4045517d792
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957253"
---
# <a name="how-to-configure-workflow-unhandled-exception-behavior-with-workflowservicehost"></a>Nasıl yapılır: WorkflowServiceHost ile İş Akışı Tarafından İşlenmeyen Özel Durum Davranışını Yapılandırma
, <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> İçinde<xref:System.ServiceModel.Activities.WorkflowServiceHost>barındırılan bir iş akışında işlenmeyen bir özel durum oluşursa gerçekleştirilecek eylemi belirtmenizi sağlayan bir davranıştır. Bu konu, bir yapılandırma dosyasında bu davranışın nasıl yapılandırılacağını gösterir.  
  
### <a name="to-configure-workflowunhandledexceptionbehavior"></a>WorkflowUnhandledExceptionBehavior 'ı yapılandırmak için  
  
1. Aşağıdaki örnekte gösterildiği`workflowUnhandledException`gibi işlenmeyen bir özel durum`behavior`oluştuğunda gerçekleştirilecek eylemi belirtmek için`serviceBehaviors` `action` özniteliğini kullanarak bir < > öğesi içindeki bir < > öğesine bir < > öğesi ekleyin.  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <workflowUnhandledException action="abandonAndSuspend"/>   
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
    > [!NOTE]
    > Önceki yapılandırma örneği Basitleştirilmiş yapılandırma kullanıyor. Daha fazla bilgi için bkz. [Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/simplified-configuration.md).  
  
     Bu davranış, aşağıdaki örnekte gösterildiği gibi, kodda yapılandırılabilir.  
  
    ```csharp  
    host.Description.Behaviors.Add(new WorkflowUnhandledExceptionBehavior { Action = WorkflowUnhandledExceptionAction.AbandonAndSuspend });  
    ```  
  
     `action` <`workflowUnhandledException`> Öğesinin özniteliği aşağıdaki değerlerden birine ayarlanabilir:  
  
     **iptal**  
     Kalıcı örnek durumuna dokunmadan bellekteki örneği iptal eder (diğer bir deyişle, son kalıcı noktaya geri dön).  
  
     **Terk Andsusbeklet**  
     Bellekte örneği iptal eder ve kalıcı örneği askıya alınmış olarak güncelleştirir.  
  
     **İptal**  
     Örnek için iptal işleyicileri çağırır ve sonra örnek deposundan da kaldırabilen örneği bellekte tamamlar  
  
     **sonlandırmayı**  
     Örneği bellekte tamamlar ve örnek deposundan kaldırır.  
  
     Hakkında <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>daha fazla bilgi için bkz. [iş akışı hizmeti konak genişletilebilirliği](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İş Akışı Hizmeti Konak Genişletilebilirliği](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)
- [İş Akışı Hizmetleri](../../../../docs/framework/wcf/feature-details/workflow-services.md)
