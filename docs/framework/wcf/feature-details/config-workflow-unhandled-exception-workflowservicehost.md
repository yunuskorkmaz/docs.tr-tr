---
title: 'Nasıl yapılır: WorkflowServiceHost ile İş Akışı Tarafından İşlenmeyen Özel Durum Davranışını Yapılandırma'
ms.date: 03/30/2017
ms.assetid: 51b25c86-292c-43e4-8d13-273d2badc8ad
ms.openlocfilehash: 69c6b1ce11d735181390a0c67df2f8dbea4f906c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185318"
---
# <a name="how-to-configure-workflow-unhandled-exception-behavior-with-workflowservicehost"></a>Nasıl yapılır: WorkflowServiceHost ile İş Akışı Tarafından İşlenmeyen Özel Durum Davranışını Yapılandırma
Bu <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> davranış, 'de barındırılan bir iş akışı içinde işlenmemiş bir özel <xref:System.ServiceModel.Activities.WorkflowServiceHost>durum oluşursa yapılacak eylemi belirtmenizi sağlayan bir davranıştır. Bu konu, yapılandırma dosyasında bu davranışın nasıl yapılandırılabildiğini gösterir.  
  
### <a name="to-configure-workflowunhandledexceptionbehavior"></a>İş Akışını yapılandırmak içinUnhandledExceptionBehavior  
  
1. <`serviceBehaviors`> `workflowUnhandledException` öğesi içindeki `behavior` <> öğesine, işlenmemiş `action` bir özel durum aşağıdaki örnekte gösterildiği gibi meydana geldiğinde yapılacak eylemi belirtmek için özniteliği kullanarak <bir> öğesi ekleyin.  
  
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
    > Önceki yapılandırma örneği basitleştirilmiş yapılandırma kullanıyor. Daha fazla bilgi için Bkz. [Basitleştirilmiş Yapılandırma.](../../../../docs/framework/wcf/simplified-configuration.md)  
  
     Bu davranış, aşağıdaki örnekte gösterildiği gibi kod olarak yapılandırılabilir.  
  
    ```csharp  
    host.Description.Behaviors.Add(new WorkflowUnhandledExceptionBehavior { Action = WorkflowUnhandledExceptionAction.AbandonAndSuspend });  
    ```  
  
     <`action` `workflowUnhandledException`> öğesinin özniteliği aşağıdaki değerlerden birine ayarlanabilir:  
  
     **Terk**  
     Kalıcı örnek durumuna dokunmadan bellekteki örneği iptal eder (diğer bir deyişle, son kalıcı noktaya geri dön).  
  
     **abandonAndSuspend**  
     Bellekteki örneği iptal eder ve askıya alınması için kalıcı örneği güncelleştirir.  
  
     **İptal**  
     Örnek için iptal işleyicilerini çağırır ve ardından örnek mağazadan kaldırabilecek şekilde bellekteki örneği tamamlar  
  
     **Sonlandır**  
     Bellekteki örneği tamamlar ve örnek deposundan kaldırır.  
  
     Hakkında <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>daha fazla bilgi için Bkz. [İş Akışı Hizmeti Ana Bilgisayar Genişletilebilirliği.](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İş Akışı Hizmeti Ana Bilgisayar Genişletilebilirliği](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)
- [İş Akışı Hizmetleri](../../../../docs/framework/wcf/feature-details/workflow-services.md)
