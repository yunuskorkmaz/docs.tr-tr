---
title: '&lt;serviceSecurityAudit&gt;'
ms.date: 03/30/2017
ms.assetid: ba517369-a034-4f8e-a2c4-66517716062b
ms.openlocfilehash: 36215709f0ede32c25739ea47f2f285e4122f098
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53144447"
---
# <a name="ltservicesecurityauditgt"></a>&lt;serviceSecurityAudit&gt;
Hizmet işlemleri sırasında güvenlik olaylarının denetlenmesini etkinleştirme ayarlarını belirtir.  
  
 \<system.ServiceModel>  
\<davranışlar >  
\<serviceBehaviors>  
\<davranışı >  
\<serviceSecurityAudit >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<serviceSecurityAudit   
   auditLogLocation="Default/Application/Security"  
   messageAuthenticationAuditLevel= None/Success/Failure/SuccessOrFailure"   serviceAuthorizationAuditLevel="None/Success/Failure/SuccessOrFailure"  
   suppressAuditFailure="Boolean"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|auditLogLocation|Denetim günlüğünün konumunu belirtir. Geçerli değerler şunlardır:<br /><br /> -Varsayılan: Güvenlik olayları uygulama günlüğüne olay günlüğüne ve Windows XP, Windows Server 2003 ve Windows Vista yazılır.<br />-Uygulama: Denetim olayları uygulama olay günlüğüne yazılır.<br />-Güvenlik: Denetim olaylarını güvenlik olay günlüğüne yazılır.<br /><br /> Varsayılan, varsayılan değerdir. Daha fazla bilgi için bkz. <xref:System.ServiceModel.AuditLogLocation>.|  
|suppressAuditFailure|Denetim günlüğüne yazma başarısızlıklarını gösterme/gizleme davranışını belirten bir Boole değeri.<br /><br /> Uygulamalar için Denetim günlüğüne yazma hataları açamayacakları bildirilmelidir. Uygulamanızın denetim hatalarını işlemek üzere tasarlanmamıştır, Denetim günlüğüne yazma hatalarını engellemek için bu öznitelik kullanmanız gerekir.<br /><br /> Bu öznitelik ise `true`, denetim olayları yazması denemelerinden kaynaklanan özel durumları dışında OutOfMemoryException, StackOverFlowException ThreadAbortException ve ArgumentException sistem tarafından işlenir ve için yayılmaz uygulama. Bu öznitelik ise `false`, denetim olayları yazması denemelerinden kaynaklanan tüm özel durumları uygulamaya geçirilir.<br /><br /> Varsayılan, `true` değeridir.|  
|serviceAuthorizationAuditLevel|Denetim günlüğüne kaydedilen yetkilendirme olay türlerini belirtir. Geçerli değerler şunlardır:<br /><br /> -Yok: Hiçbir hizmet yetkilendirme olaylarının denetlenmesini gerçekleştirilir.<br />-BAŞARI: Yalnızca başarılı hizmet yetkilendirme olaylar denetlenir.<br />-Hata: Yalnızca hata hizmet yetkilendirme olaylar denetlenir.<br />-SuccessOrFailure: Başarı ve başarısızlık hem hizmet yetkilendirme olaylar denetlenir.<br /><br /> Varsayılan değer, Yok'tur. Daha fazla bilgi için bkz. <xref:System.ServiceModel.AuditLevel>.|  
|messageAuthenticationAuditLevel|Günlüğe ileti kimlik doğrulaması olaylarının türünü belirtir. Geçerli değerler şunlardır:<br /><br /> -Yok: Denetim olayları üretilir.<br />-BAŞARI: Yalnızca başarılı güvenlik (tam doğrulama ileti imzası doğrulama, şifreleme ve belirteç doğrulama gibi) olayları günlüğe kaydedilir.<br />-Hata: Yalnızca hata olaylarını günlüğe kaydedilir.<br />-SuccessOrFailure: Hem başarılı hem de hata olayları günlüğe kaydedilir.<br /><br /> Varsayılan değer, Yok'tur. Daha fazla bilgi için bkz. <xref:System.ServiceModel.AuditLevel>.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<davranışı >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Bir davranış öğesi belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yapılandırma öğesi, Windows Communication Foundation (WCF) kimlik doğrulama olayları denetlemek için kullanılır. Denetimi etkinleştirildiğinde, başarılı veya başarısız kimlik doğrulama girişimleri (veya her ikisi de) denetlenebilir. Olayları üç olay günlüklerini birine yazılır: uygulama, güvenlik veya varsayılan günlük işletim sistemi sürümü. Olay günlüklerini tüm Windows Olay Görüntüleyicisi kullanılarak görüntülenebilir.  
  
 Bu yapılandırma öğesini kullanarak bir ayrıntılı örnek için bkz: [hizmet denetleme davranışı](../../../../../docs/framework/wcf/samples/service-auditing-behavior.md).  
  
 Varsayılan olarak, Windows XP'de uygulama oturum açma olaylarını denetle görülebilir; Windows Server 2003 ve Windows Vista'te olduğu sırada, denetim olayları güvenlik günlüğünde görülebilir. Denetim olayları konumunu ayarlayarak belirtilebilir `auditLogLocation` özniteliği için 'Uygulama' veya 'Güvenlik'. Daha fazla bilgi için [nasıl yapılır: Güvenlik olaylarını denetleme](../../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md). Olayları güvenlik günlüğünde yazılır, LocalSecurityPolicy -> Nesne erişimini etkinleştirmek için "Başarılı" ve "Başarısız" olarak ayarlanmalıdır.  
  
 Olay günlüğüne baktığımda denetim olayları "ServiceModel denetim 3.0.0.0" kaynağıdır. Hizmet yetkilendirme Denetim kayıtlarını 'ServiceAuthorization' kategorisi ileti kimlik doğrulama Denetim kayıtlarını "MessageAuthentication" kategorisi bulunur.  
  
 İleti, ileti olup süresi doldu ve istemci hizmeti için olup olmadığını doğrulanabilir oynanmış olmadığını ileti kimlik doğrulaması olaylarının kapsar. Bunlar kimlik doğrulaması başarılı oldu veya istemci kimliği ile birlikte başarısız hakkında bilgi sağlar ve uç nokta ileti birlikte iletiyle ilişkili eylemi için gönderildi.  
  
 Hizmet yetkilendirme denetim olaylarını hizmet Yetkilendirme Yöneticisi tarafından yapılan yetkilendirme kararı kapsar. Yetkilendirme başarılı olup olmadığını hakkında bilgi sağladıkları veya istemci kimliği ile birlikte başarısız oldu, uç nokta ileti, ileti öğesinden oluşturulan yetkilendirme Bağlam tanıtıcısı ile ilişkili eylem gönderildi gelen ileti ve erişim kararı Yetkilendirme Yöneticisi türünü.  
  
## <a name="example"></a>Örnek  
  
```xml  
<system.serviceModel>  
   <serviceBehaviors>  
      <behavior name="NewBehavior">  
         <serviceSecurityAudit auditLogLocation="Application"   
             suppressAuditFailure="true"  
             serviceAuthorizationAuditLevel="Success"   
             messageAuthenticationAuditLevel="Success" />  
      </behavior>  
   </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.ServiceSecurityAuditElement>  
 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>  
 [Güvenlik Davranışları](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [Denetim](../../../../../docs/framework/wcf/feature-details/auditing-security-events.md)  
 [Nasıl Yapılır: Güvenlik olaylarını denetleme](../../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md)  
 [Hizmet Denetleme Davranışı](../../../../../docs/framework/wcf/samples/service-auditing-behavior.md)
