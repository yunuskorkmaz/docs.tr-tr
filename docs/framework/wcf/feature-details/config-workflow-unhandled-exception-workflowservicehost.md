---
title: 'Nasıl yapılır: WorkflowServiceHost ile İş Akışı Tarafından İşlenmeyen Özel Durum Davranışını Yapılandırma'
ms.date: 03/30/2017
ms.assetid: 51b25c86-292c-43e4-8d13-273d2badc8ad
ms.openlocfilehash: 8f7fe203a4198aa98e8aee1be3a12e4d72a066f8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59175415"
---
# <a name="how-to-configure-workflow-unhandled-exception-behavior-with-workflowservicehost"></a>Nasıl yapılır: WorkflowServiceHost ile İş Akışı Tarafından İşlenmeyen Özel Durum Davranışını Yapılandırma
<xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> Barındırılan iş akışı içinde işlenmeyen bir özel durum oluşursa yapılacak eylem belirtmenize olanak tanıyan bir davranış <xref:System.ServiceModel.Activities.WorkflowServiceHost>. Bu konuda, bir yapılandırma dosyasında bu davranışı yapılandırma gösterilmektedir.  
  
### <a name="to-configure-workflowunhandledexceptionbehavior"></a>WorkflowUnhandledExceptionBehavior yapılandırmak için  
  
1.  Ekleme bir <`workflowUnhandledException`> öğesinde bir <`behavior`> öğesi içinde bir <`serviceBehaviors`> öğesini kullanarak `action` aşağıdaki örnekte gösterildiği gibi işlenmeyen bir özel durum ortaya çıktığında gerçekleştirilecek eylemi belirtmek için özniteliği.  
  
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
    >  Önceki yapılandırma örneği Basitleştirilmiş yapılandırma kullanıyor. Daha fazla bilgi için [Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/simplified-configuration.md).  
  
     Bu davranış, aşağıdaki örnekte gösterildiği gibi kodda yapılandırılabilir.  
  
    ```csharp  
    host.Description.Behaviors.Add(new WorkflowUnhandledExceptionBehavior { Action = WorkflowUnhandledExceptionAction.AbandonAndSuspend });  
    ```  
  
     `action` Özniteliği <`workflowUnhandledException`> öğesi aşağıdaki değerlerden birine ayarlanabilir:  
  
     **İptal Et**  
     (Son kalan noktasına geri olduğu gibi) kalıcı örneği durumu dokunmadan bellekte örneği durdurur.  
  
     **abandonAndSuspend**  
     Bellekte bir örneği durdurur ve yakında askıya alınacak kalıcı örneğini güncelleştirir.  
  
     **İptal**  
     Örneğinin iptal işleyicisi çağırır ve ardından örneğinde bellek, ayrıca örnek Mağazası'ndan kaldırabilir tamamlar  
  
     **terminate**  
     Bellek örneğinde tamamlanır ve örnek deposundan kaldırır.  
  
     Hakkında daha fazla bilgi için <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>, bkz: [iş akışı hizmeti konak genişletilebilirliği](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İş Akışı Hizmeti Ana Bilgisayar Genişletilebilirliği](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)
- [İş Akışı Hizmetleri](../../../../docs/framework/wcf/feature-details/workflow-services.md)
