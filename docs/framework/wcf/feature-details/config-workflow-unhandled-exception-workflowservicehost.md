---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: Iş akışı Işlenmeyen özel durum davranışını WorkflowServiceHost ile yapılandırma'
title: 'Nasıl yapılır: WorkflowServiceHost ile İş Akışı Tarafından İşlenmeyen Özel Durum Davranışını Yapılandırma'
ms.date: 03/30/2017
ms.assetid: 51b25c86-292c-43e4-8d13-273d2badc8ad
ms.openlocfilehash: 7d32ccf1262895d948cae26f0922adf3003664ba
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99743388"
---
# <a name="how-to-configure-workflow-unhandled-exception-behavior-with-workflowservicehost"></a>Nasıl yapılır: WorkflowServiceHost ile İş Akışı Tarafından İşlenmeyen Özel Durum Davranışını Yapılandırma

, <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> İçinde barındırılan bir iş akışında işlenmeyen bir özel durum oluşursa gerçekleştirilecek eylemi belirtmenizi sağlayan bir davranıştır <xref:System.ServiceModel.Activities.WorkflowServiceHost> . Bu konu, bir yapılandırma dosyasında bu davranışın nasıl yapılandırılacağını gösterir.  
  
### <a name="to-configure-workflowunhandledexceptionbehavior"></a>WorkflowUnhandledExceptionBehavior 'ı yapılandırmak için  
  
1. `workflowUnhandledException` `behavior` `serviceBehaviors` `action` Aşağıdaki örnekte gösterildiği gibi işlenmeyen bir özel durum oluştuğunda gerçekleştirilecek eylemi belirtmek için özniteliğini kullanarak bir <> öğesi içindeki bir <> öğesine bir <> öğesi ekleyin.  
  
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
    > Önceki yapılandırma örneği Basitleştirilmiş yapılandırma kullanıyor. Daha fazla bilgi için bkz. [Basitleştirilmiş yapılandırma](../simplified-configuration.md).  
  
     Bu davranış, aşağıdaki örnekte gösterildiği gibi, kodda yapılandırılabilir.  
  
    ```csharp  
    host.Description.Behaviors.Add(new WorkflowUnhandledExceptionBehavior { Action = WorkflowUnhandledExceptionAction.AbandonAndSuspend });  
    ```  
  
     `action`<`workflowUnhandledException`> öğesinin özniteliği aşağıdaki değerlerden birine ayarlanabilir:  
  
     **iptal**  
     Kalıcı örnek durumuna dokunmadan bellekteki örneği iptal eder (diğer bir deyişle, son kalıcı noktaya geri dön).  
  
     **Terk Andsusbeklet**  
     Bellekte örneği iptal eder ve kalıcı örneği askıya alınmış olarak güncelleştirir.  
  
     **İptal**  
     Örnek için iptal işleyicileri çağırır ve sonra örnek deposundan da kaldırabilen örneği bellekte tamamlar  
  
     **sonlandırmayı**  
     Örneği bellekte tamamlar ve örnek deposundan kaldırır.  
  
     Hakkında daha fazla bilgi için <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> bkz. [Iş akışı hizmeti konak genişletilebilirliği](workflow-service-host-extensibility.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İş Akışı Hizmeti Ana Bilgisayar Genişletilebilirliği](workflow-service-host-extensibility.md)
- [İş Akışı Hizmetleri](workflow-services.md)
