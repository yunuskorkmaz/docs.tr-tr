---
title: <serviceSecurityAudit>
ms.date: 03/30/2017
ms.assetid: ba517369-a034-4f8e-a2c4-66517716062b
ms.openlocfilehash: a1fcc59550904a34eced8e87fa9bc54a334acd03
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937171"
---
# <a name="servicesecurityaudit"></a>\<Servicesecurityauıdıt >
Hizmet işlemleri sırasında güvenlik olaylarının denetlenmesini etkinleştiren ayarları belirtir.  
  
 \<system.ServiceModel>  
\<davranışlar >  
\<serviceBehaviors>  
\<davranış >  
\<Servicesecurityauıdıt >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<serviceSecurityAudit auditLogLocation="Default/Application/Security"
                      messageAuthenticationAuditLevel="None/Success/Failure/SuccessOrFailure"
                      serviceAuthorizationAuditLevel="None/Success/Failure/SuccessOrFailure"
                      suppressAuditFailure="Boolean" />
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|auditLogLocation|Denetim günlüğünün konumunu belirtir. Geçerli değerler şunlardır:<br /><br /> Varsayılanını Güvenlik olayları Windows XP 'de uygulama günlüğüne ve Windows Server 2003 ve Windows Vista 'daki olay günlüğüne yazılır.<br />Uygulamanızı Denetim olayları, uygulama olay günlüğüne yazılır.<br />Güven Denetim olayları güvenlik olay günlüğüne yazılır.<br /><br /> Varsayılan değer varsayılandır. Daha fazla bilgi için bkz. <xref:System.ServiceModel.AuditLogLocation>.|  
|suppressAuditFailure|Denetim günlüğüne yazma başarısızlıklarını gizleme davranışını belirleyen bir Boolean değer.<br /><br /> Uygulamalar, denetim günlüğüne yazma hatalarıyla ilgili bilgilendirmelidir. Uygulamanız denetim başarısızlıklarını işleyecek şekilde tasarlanmamışsa, denetim günlüğüne yazarken oluşan hataların görüntülenmesini engellemek için bu özniteliği kullanmanız gerekir.<br /><br /> Bu öznitelik ise `true`, OutOfMemoryException, StackOverflowException, threalebortexception, ve denetim olaylarını yazma girişimlerinin sonucu olan özel durumlar sistem tarafından işlenir ve şuna yayılmaz Uygulamanızı. Bu öznitelik ise `false`, denetim olaylarını yazma denemesinden kaynaklanan tüm özel durumlar uygulamaya geçirilir.<br /><br /> Varsayılan, `true` değeridir.|  
|serviceAuthorizationAuditLevel|Denetim günlüğüne kaydedilen yetkilendirme olaylarının türlerini belirtir. Geçerli değerler şunlardır:<br /><br /> Seçim Hizmet Yetkilendirme olaylarının denetlenmesi yapılmaz.<br />Başarılı Yalnızca başarılı hizmet yetkilendirme olayları denetlenir.<br />Hataları Yalnızca başarısız hizmet yetkilendirme olayları denetlenir.<br />-Başarılı Sorfailure: Başarı ve başarısızlık Hizmeti yetkilendirme olaylarının her ikisi de denetlenir.<br /><br /> Varsayılan değer, Yok'tur. Daha fazla bilgi için bkz. <xref:System.ServiceModel.AuditLevel>.|  
|messageAuthenticationAuditLevel|Günlüğe kaydedilen ileti kimlik doğrulaması denetim olaylarının türünü belirtir. Geçerli değerler şunlardır:<br /><br /> Seçim Hiçbir denetim olayı oluşturulmaz.<br />Başarılı Yalnızca başarılı güvenlik (ileti imzası doğrulama, şifre ve belirteç doğrulama dahil tam doğrulama) olayları günlüğe kaydedilir.<br />Hataları Yalnızca hata olayları günlüğe kaydedilir.<br />-Başarılı Sorfailure: Hem başarı hem de hata olayları günlüğe kaydedilir.<br /><br /> Varsayılan değer, Yok'tur. Daha fazla bilgi için bkz. <xref:System.ServiceModel.AuditLevel>.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<davranış >](behavior-of-endpointbehaviors.md)|Bir davranış öğesi belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yapılandırma öğesi Windows Communication Foundation (WCF) kimlik doğrulama olaylarını denetlemek için kullanılır. Denetim etkinleştirildiğinde, başarılı veya başarısız kimlik doğrulama denemeleri (ya da her ikisi) denetlenebilir. Olaylar üç olay günlüğünden birine yazılır: işletim sistemi sürümü için uygulama, güvenlik veya varsayılan günlük. Olay günlüklerinin hepsi Windows Olay Görüntüleyicisi kullanılarak görüntülenebilir.  
  
 Bu yapılandırma öğesinin kullanımına ilişkin ayrıntılı bir örnek için bkz. [hizmet denetimi davranışı](../../../wcf/samples/service-auditing-behavior.md).  
  
 Varsayılan olarak, Windows XP 'de, denetim olayları uygulama günlüğünde görülebilir; Windows Server 2003 ve Windows Vista 'da, denetim olayları güvenlik günlüğünde görünebilirler. ' Application ' veya ' Security ' `auditLogLocation` özniteliği ayarlanarak denetim olaylarının konumu belirtilebilir. Daha fazla bilgi için [nasıl yapılır: Güvenlik olaylarını](../../../wcf/feature-details/how-to-audit-wcf-security-events.md)denetleyin. Olaylar güvenlik günlüğünde yazılmışsa, LocalSecurityPolicy-> Nesne erişimini etkinleştir ' in "başarılı" ve "başarısızlık" için ayarlanmış olması gerekir.  
  
 Olay günlüğüne baktığınızda, denetim olaylarının kaynağı "ServiceModel Audit 3.0.0.0" olur. İleti kimlik doğrulaması denetim kayıtları, hizmet yetkilendirme denetim kayıtları bir ' ServiceAuthorization ' kategorisine sahip iken "MessageAuthentication" kategorisine sahiptir.  
  
 İleti kimlik doğrulaması denetim olayları, iletinin zaman aşımına uğradığını ve istemcinin hizmette kimlik doğrulaması yapıp yapamadığını içeren iletinin ile değiştirilip değiştirilmediğini kapsar. Kimlik doğrulamanın, istemcinin kimliğiyle birlikte başarılı veya başarısız olup olmadığı hakkında bilgi sağlar ve ileti ile ilişkili eylemle birlikte iletinin gönderildiği bitiş noktasıdır.  
  
 Hizmet yetkilendirme denetim olayları, bir hizmet Yetkilendirme Yöneticisi tarafından yapılan yetkilendirme kararlarını kapsar. Bunlar, Yetkilendirme başarılı veya başarısız olsun, istemcinin kimliği, iletinin gönderildiği bitiş noktası, iletiyle ilişkili eylem, ileti ile ilişkili eylem, ile oluşturulan yetkilendirme bağlamının tanımlayıcısı gelen ileti ve erişim kararı veren Yetkilendirme Yöneticisi türü.  
  
## <a name="example"></a>Örnek  
  
```xml  
<system.serviceModel>
  <behaviors>
    <serviceBehaviors>
      <behavior name="NewBehavior">
        <serviceSecurityAudit auditLogLocation="Application"
                              suppressAuditFailure="true"
                              serviceAuthorizationAuditLevel="Success"
                              messageAuthenticationAuditLevel="Success" />
      </behavior>
    </serviceBehaviors>
  </behaviors>
</system.serviceModel>
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.ServiceSecurityAuditElement>
- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
- [Güvenlik Davranışları](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [Denetim](../../../wcf/feature-details/auditing-security-events.md)
- [Nasıl yapılır: Güvenlik olaylarını denetleme](../../../wcf/feature-details/how-to-audit-wcf-security-events.md)
- [Hizmet Denetleme Davranışı](../../../wcf/samples/service-auditing-behavior.md)
