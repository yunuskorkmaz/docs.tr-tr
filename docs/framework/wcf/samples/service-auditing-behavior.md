---
title: "Hizmet Denetleme Davranışı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59bf0cda-e496-4418-a3a1-2f0f6e85f8ce
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f84bff892a35288a75738d9cfa326ffc4119b433
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="service-auditing-behavior"></a>Hizmet Denetleme Davranışı
Bu örnek nasıl kullanılacağı ortaya <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> hizmet işlemleri sırasında güvenlik olaylarının denetimini etkinleştirmek için. Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md). İstemci ve hizmet kullanılarak yapılandırılmış [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md). `mode` Özniteliği [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) ayarlandığından `Message` ve `clientCredentialType` ayarlandığından `Windows`. Bu örnekte, istemci bir konsol uygulaması (.exe) ve Internet Information Services (IIS) tarafından barındırılan hizmetindeki.  
  
> [!NOTE]
>  Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.  
  
 Hizmet yapılandırma dosyası kullanan `serviceSecurityAudit` denetimi yapılandırmak amacıyla öğesi.  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      ...  
<!-- serviceSecurityAudit allows specification of audit location   
     and whether to audit success, failure or both. This service   
     logs success and failure of messageAuthentication   
     to the default location -->  
     <serviceSecurityAudit auditLogLocation ="Default" messageAuthenticationAuditLevel = "SuccessOrFailure" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir. Konsol penceresinde istemciyi aşağı kapatmak için ENTER tuşuna basın.  
  
 Sonuçta elde edilen denetim günlüklerini Olay Görüntüleyicisi'ni çalıştırarak görülebilir. Varsayılan olarak, Windows XP Windows Server 2003 ve Windows Vista üzerinde uygulama günlüğünde denetim olaylarını görülebilir denetim olaylarını güvenlik günlüğüne görülebilir. Windows Server 2008 ve Windows 7 üzerinde denetim olayları uygulamaları ve Hizmetleri günlüklerinde görülebilir. Denetim olaylarının konumu ayarlayarak belirtilebilir `auditLogLocation` özniteliği için "Uygulama" veya "Güvenlik". Daha fazla bilgi için bkz: [nasıl yapılır: denetim güvenlik olaylarını](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md). Nesne erişimi etkinleştir "Başarılı" ve "Başarısız" için ayarlanmalıdır LocalSecurityPolicy -> güvenlik günlüğüne yazılan olaylar durumunda.  
  
 Olay günlüğü bakarken olaylarını denetle "ServiceModel denetim 3.0.0.0" kaynağıdır. Hizmet yetkilendirme denetim kayıtlarının "ServiceAuthorization" kategorisi bulunurken ileti kimlik doğrulama denetim kayıtlarının "MessageAuthentication" kategorisi vardır.  
  
 İleti, ileti olup süresi doldu ve istemci hizmete olup doğrulanabilir müdahale olup olmadığını ileti kimlik doğrulama denetim olaylarını kapsar. Kimlik doğrulaması başarılı oldu veya istemci kimlikle birlikte başarısız hakkında bilgi sağlar ve uç nokta ileti ileti ile ilişkili eylem birlikte gönderildi.  
  
 Hizmet yetkilendirme denetim olaylarını hizmet Yetkilendirme Yöneticisi tarafından yapılan yetkilendirme kararı kapsar. Olup Yetkilendirme başarılı hakkında bilgi sağlamak veya istemci kimlikle birlikte başarısız oldu, uç nokta ileti, ileti, gelen oluşturulan yetkilendirme Bağlam tanıtıcısı ile ilişkili eylem gönderildi gelen ileti ve erişim kararı Yetkilendirme Yöneticisi'ni türü.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çapraz bilgisayar yapılandırmasında örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Denetleme](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)  
 [Nasıl yapılır: güvenlik olaylarını denetleme](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md)
