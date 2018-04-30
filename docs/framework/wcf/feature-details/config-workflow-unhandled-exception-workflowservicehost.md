---
title: 'Nasıl yapılır: WorkflowServiceHost ile İş Akışı Tarafından İşlenmeyen Özel Durum Davranışını Yapılandırma'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 51b25c86-292c-43e4-8d13-273d2badc8ad
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a49b3d42e51ed7a0a57deb392f5728f407909b00
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-configure-workflow-unhandled-exception-behavior-with-workflowservicehost"></a>Nasıl yapılır: WorkflowServiceHost ile İş Akışı Tarafından İşlenmeyen Özel Durum Davranışını Yapılandırma
<xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> Barındırılan bir iş akışı içinde işlenmeyen bir özel durum oluşursa, gerçekleştirilecek eylemi belirtmenize olanak tanıyan bir davranıştır <xref:System.ServiceModel.Activities.WorkflowServiceHost>. Bu konuda, bir yapılandırma dosyasında bu davranışı yapılandırmak gösterilmiştir.  
  
### <a name="to-configure-workflowunhandledexceptionbehavior"></a>WorkflowUnhandledExceptionBehavior yapılandırmak için  
  
1.  Ekleme bir <`workflowUnhandledException`> öğesinde bir <`behavior`> öğesi içinde bir <`serviceBehaviors`> öğesini kullanarak `action` özniteliği aşağıdaki örnekte gösterildiği gibi işlenmeyen bir özel durum meydana geldiğinde eylemi belirtin.  
  
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
    >  Önceki yapılandırma örneği Basitleştirilmiş yapılandırma kullanıyor. Daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/simplified-configuration.md).  
  
     Bu davranış, aşağıdaki örnekte gösterildiği gibi kodda yapılandırılabilir.  
  
    ```csharp  
    host.Description.Behaviors.Add(new WorkflowUnhandledExceptionBehavior { Action = WorkflowUnhandledExceptionAction.AbandonAndSuspend });  
    ```  
  
     `action` Özniteliği <`workflowUnhandledException`> öğesi aşağıdaki değerlerden birine ayarlanabilir:  
  
     **İptal Et**  
     (Bu son kalan noktasına geri olan) kalıcı örneği durumu dokunmadan bellek örneğinde durdurur.  
  
     **abandonAndSuspend**  
     Bellek örneğinde durdurur ve askıya alınmasına kalıcı örneğini güncelleştirir.  
  
     **İptal**  
     İptal işleyicileri için örneği çağırır ve ayrıca örneği Mağazası'ndan kaldırabilir bellek örneğinde tamamlar  
  
     **Sonlandırma**  
     Bellek örneğinde tamamlanır ve örnek deposundan kaldırır.  
  
     Hakkında daha fazla bilgi için <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>, bkz: [iş akışı hizmeti konak genişletilebilirliği](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İş Akışı Hizmeti Konak Genişletilebilirliği](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)  
 [İş Akışı Hizmetleri](../../../../docs/framework/wcf/feature-details/workflow-services.md)
