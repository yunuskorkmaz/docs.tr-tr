---
title: Hizmet Denetleme Davranışı
ms.date: 03/30/2017
ms.assetid: 59bf0cda-e496-4418-a3a1-2f0f6e85f8ce
ms.openlocfilehash: bfe13146a7f7cdec648a82a34c34077ec5466809
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599938"
---
# <a name="service-auditing-behavior"></a>Hizmet Denetleme Davranışı
Bu örnek, <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> hizmet işlemleri sırasında güvenlik olaylarının denetlenmesini etkinleştirmek için öğesinin nasıl kullanılacağını gösterir. Bu örnek, [Başlarken](getting-started-sample.md)' i temel alır. Hizmeti ve istemcisi kullanılarak yapılandırıldı [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) . `mode`Öğesinin özniteliği [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) olarak ayarlanmıştır `Message` ve `clientCredentialType` olarak ayarlanmıştır `Windows` . Bu örnekte, istemci bir konsol uygulaması (. exe) ve hizmet Internet Information Services (IIS) tarafından barındırılır.  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
 Hizmet yapılandırma dosyası, `serviceSecurityAudit` denetimi yapılandırmak için öğesini kullanır.  
  
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
  
 Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir. İstemcisini kapatmak için konsol penceresinde ENTER tuşuna basın.  
  
 Elde edilen denetim günlükleri Olay Görüntüleyicisi çalıştırılarak görülebilir. Varsayılan olarak, Windows XP 'de, Windows Server 2003 ve Windows Vista 'da denetim olayları uygulama günlüğünde görülebilir, bu da denetim olayları güvenlik günlüğünde görülebilir. Windows Server 2008 ve Windows 7 ' de, denetim olayları uygulamalar ve hizmetler günlüklerinde görülebilir. `auditLogLocation`"Application" veya "Security" özniteliği ayarlanarak denetim olaylarının konumu belirtilebilir. Daha fazla bilgi için bkz. [nasıl yapılır: güvenlik olaylarını denetleme](../feature-details/how-to-audit-wcf-security-events.md). Olaylar güvenlik günlüğünde yazılmışsa, LocalSecurityPolicy-> nesne erişimini etkinleştir "başarı" ve "başarısızlık" için ayarlanmalıdır.  
  
 Olay günlüğüne baktığınızda, denetim olaylarının kaynağı "ServiceModel Audit 3.0.0.0" olur. İleti kimlik doğrulaması denetim kayıtları, hizmet yetkilendirme denetim kayıtları "ServiceAuthorization" kategorisine sahip olsa da "MessageAuthentication" kategorisine sahiptir.  
  
 İleti kimlik doğrulaması denetim olayları iletinin değiştirilip değiştirilmediğini, iletinin süresi dolmadığını ve istemcinin hizmette kimlik doğrulaması yapıp yapamadığını kapsar. Kimlik doğrulamanın, istemcinin kimliğiyle birlikte başarılı mı yoksa başarısız mı olduğunu ve iletinin iletiyle ilişkili eylem ile birlikte gönderildiği bitiş noktasını sağlar.  
  
 Hizmet yetkilendirme denetim olayları, bir hizmet Yetkilendirme Yöneticisi tarafından yapılan yetkilendirme kararlarını kapsar. Bunlar, Yetkilendirme başarılı veya başarısız olsun, istemcinin kimliği, iletinin gönderildiği bitiş noktası, iletiyle ilişkili eylem, gelen iletiden oluşturulan yetkilendirme bağlamının tanımlayıcısı ve erişim kararı veren Yetkilendirme Yöneticisi türü hakkında bilgi sağlar.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.  
  
3. Örneği tek veya bir çoklu bilgisayar yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Denetim](../feature-details/auditing-security-events.md)
- [Nasıl yapılır: Güvenlik Olaylarını Denetleme](../feature-details/how-to-audit-wcf-security-events.md)
