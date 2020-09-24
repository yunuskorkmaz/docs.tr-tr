---
title: <serviceSecurityAudit>
ms.date: 03/30/2017
ms.assetid: ba517369-a034-4f8e-a2c4-66517716062b
ms.openlocfilehash: 6cec3373dae3127f16bb8a418a91a684554f2b0c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153670"
---
# \<serviceSecurityAudit>

Hizmet işlemleri sırasında güvenlik olaylarının denetlenmesini etkinleştiren ayarları belirtir.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceSecurityAudit>**  
  
## <a name="syntax"></a>Syntax  
  
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
|auditLogLocation|Denetim günlüğünün konumunu belirtir. Geçerli değerler şunlardır:<br /><br /> -Varsayılan: güvenlik olayları Windows XP 'de uygulama günlüğüne ve Windows Server 2003 ve Windows Vista 'daki olay günlüğüne yazılır.<br />-Uygulama: denetim olayları, uygulama olay günlüğüne yazılır.<br />-Güvenlik: denetim olayları güvenlik olay günlüğüne yazılır.<br /><br /> Varsayılan değer varsayılandır. Daha fazla bilgi için bkz. <xref:System.ServiceModel.AuditLogLocation>.|  
|suppressAuditFailure|Denetim günlüğüne yazma başarısızlıklarını gizleme davranışını belirleyen bir Boolean değer.<br /><br /> Uygulamalar, denetim günlüğüne yazma hatalarıyla ilgili bilgilendirmelidir. Uygulamanız denetim başarısızlıklarını işleyecek şekilde tasarlanmamışsa, denetim günlüğüne yazarken oluşan hataların görüntülenmesini engellemek için bu özniteliği kullanmanız gerekir.<br /><br /> Bu öznitelik ise, `true` OutOfMemoryException, StackOverflowException, Threalebortexception, ve denetim olaylarını yazma girişimlerinin sonucu olan özel durumlar sistem tarafından işlenir ve uygulamaya yayılmaz. Bu öznitelik ise `false` , denetim olaylarını yazma denemesinden kaynaklanan tüm özel durumlar uygulamaya geçirilir.<br /><br /> Varsayılan değer: `true`.|  
|serviceAuthorizationAuditLevel|Denetim günlüğüne kaydedilen yetkilendirme olaylarının türlerini belirtir. Geçerli değerler şunlardır:<br /><br /> -None: hizmet Yetkilendirme olaylarının denetlenmesi yapılmaz.<br />-Başarılı: yalnızca başarılı hizmet yetkilendirme olayları denetlenir.<br />-Hata: yalnızca başarısız hizmet yetkilendirme olayları denetlenir.<br />-Başarılı Sorfailure: hem başarı hem de başarısızlık Hizmeti yetkilendirme olayları denetlenir.<br /><br /> Varsayılan değer, Yok'tur. Daha fazla bilgi için bkz. <xref:System.ServiceModel.AuditLevel>.|  
|messageAuthenticationAuditLevel|Günlüğe kaydedilen ileti kimlik doğrulaması denetim olaylarının türünü belirtir. Geçerli değerler şunlardır:<br /><br /> -None: hiçbir denetim olayı oluşturulmaz.<br />-Success: yalnızca başarılı bir güvenlik (ileti imzası doğrulama, şifre ve belirteç doğrulama dahil tam doğrulama) olayları günlüğe kaydedilir.<br />-Hata: yalnızca hata olayları günlüğe kaydedilir.<br />-Başarılı Sorfailure: hem başarı hem de hata olayları günlüğe kaydedilir.<br /><br /> Varsayılan değer, Yok'tur. Daha fazla bilgi için bkz. <xref:System.ServiceModel.AuditLevel>.|  
  
### <a name="child-elements"></a>Alt Öğeler  

 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|Bir davranış öğesi belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  

 Bu yapılandırma öğesi Windows Communication Foundation (WCF) kimlik doğrulama olaylarını denetlemek için kullanılır. Denetim etkinleştirildiğinde, başarılı veya başarısız kimlik doğrulama denemeleri (ya da her ikisi) denetlenebilir. Olaylar üç olay günlüğünden birine yazılır: işletim sistemi sürümü için uygulama, güvenlik veya varsayılan günlük. Olay günlüklerinin hepsi Windows Olay Görüntüleyicisi kullanılarak görüntülenebilir.  
  
 Bu yapılandırma öğesinin kullanımına ilişkin ayrıntılı bir örnek için bkz. [hizmet denetimi davranışı](../../../wcf/samples/service-auditing-behavior.md).  
  
 Varsayılan olarak, Windows XP 'de, denetim olayları uygulama günlüğünde görülebilir; Windows Server 2003 ve Windows Vista 'da, denetim olayları güvenlik günlüğünde görünebilirler. `auditLogLocation`' Application ' veya ' Security ' özniteliği ayarlanarak denetim olaylarının konumu belirtilebilir. Daha fazla bilgi için bkz. [nasıl yapılır: güvenlik olaylarını denetleme](../../../wcf/feature-details/how-to-audit-wcf-security-events.md). Olaylar güvenlik günlüğünde yazılmışsa, LocalSecurityPolicy-> nesne erişimini etkinleştir ' in "başarılı" ve "başarısızlık" için ayarlanmış olması gerekir.  
  
 Olay günlüğüne baktığınızda, denetim olaylarının kaynağı "ServiceModel Audit 3.0.0.0" olur. İleti kimlik doğrulaması denetim kayıtları, hizmet yetkilendirme denetim kayıtları bir ' ServiceAuthorization ' kategorisine sahip iken "MessageAuthentication" kategorisine sahiptir.  
  
 İleti kimlik doğrulaması denetim olayları, iletinin zaman aşımına uğradığını ve istemcinin hizmette kimlik doğrulaması yapıp yapamadığını içeren iletinin ile değiştirilip değiştirilmediğini kapsar. Kimlik doğrulamanın, istemcinin kimliğiyle birlikte başarılı veya başarısız olup olmadığı hakkında bilgi sağlar ve ileti ile ilişkili eylemle birlikte iletinin gönderildiği bitiş noktasıdır.  
  
 Hizmet yetkilendirme denetim olayları, bir hizmet Yetkilendirme Yöneticisi tarafından yapılan yetkilendirme kararlarını kapsar. Kimlik doğrulama başarılı veya başarısız olsun, istemcinin kimliği, iletinin gönderildiği bitiş noktası, iletiyle ilişkili eylem, gelen iletiden oluşturulan yetkilendirme bağlamının tanımlayıcısı ve erişim kararı veren Yetkilendirme Yöneticisi türü hakkında bilgi sağlar.  
  
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
- [Nasıl yapılır: Güvenlik Olaylarını Denetleme](../../../wcf/feature-details/how-to-audit-wcf-security-events.md)
- [Hizmet Denetleme Davranışı](../../../wcf/samples/service-auditing-behavior.md)
