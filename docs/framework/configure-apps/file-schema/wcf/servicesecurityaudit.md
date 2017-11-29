---
title: '&lt;serviceSecurityAudit&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ba517369-a034-4f8e-a2c4-66517716062b
caps.latest.revision: "17"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: f0c708c19761f6086e1b5c2fdd15904c76fe3de9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltservicesecurityauditgt"></a>&lt;serviceSecurityAudit&gt;
Hizmet işlemleri sırasında güvenlik olaylarının denetlenmesini etkinleştirme ayarlarını belirtir.  
  
 \<Sistem. ServiceModel >  
\<davranışları >  
\<serviceBehaviors >  
\<davranışı >  
\<serviceSecurityAudit >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<serviceSecurityAudit   
   auditLogLocation="Default/Application/Security"  
   messageAuthenticationAuditLevel= None/Success/Failure/SuccessAndFailure"   serviceAuthorizationAuditLevel="None/Success/Failure/SuccessAndFailure"  
   suppressAuditFailure="Boolean"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|auditLogLocation|Denetim günlüğü konumunu belirtir. Geçerli değerler şunlardır:<br /><br /> -Varsayılan: Güvenlik olaylarını uygulama günlüğüne olay günlüğüne ve Windows XP, Windows Server 2003 ve Windows Vista yazılır.<br />-Uygulama: Denetim olayları uygulama olay günlüğüne yazılır.<br />-Güvenlik: Denetim olaylarını güvenlik olay günlüğüne yazılır.<br /><br /> Varsayılan değer varsayılandır. Daha fazla bilgi için bkz. <xref:System.ServiceModel.AuditLogLocation>.|  
|suppressAuditFailure|Denetim günlüğü yazma hataları gizleme için davranışını belirten bir Boole değeri.<br /><br /> Uygulamalar için Denetim günlüğü yazma hataları için bildirilmesi gerekir. Uygulamanızın denetim hataları işlemek üzere tasarlanmamıştır, Denetim günlüğü yazma hataları gizlemek için bu öznitelik kullanmanız gerekir.<br /><br /> Bu öznitelik değilse `true`, denetim olayları yazma girişimlerine karşı neden özel durumları OutOfMemoryException, StackOverFlowException, ThreadAbortException ve ArgumentException dışında sistem tarafından işlenir ve için yayılmaz uygulama. Bu öznitelik değilse `false`, denetim olayları yazmak için denemelerinden kaynaklanan tüm özel durumları uygulamaya geçirilir.<br /><br /> Varsayılan, `true` değeridir.|  
|serviceAuthorizationAuditLevel|Denetim günlüğüne yetkilendirme olayları türlerini belirtir. Geçerli değerler şunlardır:<br /><br /> -Yok: Hiçbir hizmet yetkilendirme olaylarının denetlenmesi gerçekleştirilir.<br />-BAŞARI: Yalnızca başarılı hizmet yetkilendirme olayları denetlenir.<br />-Hata: Yalnızca hatası hizmeti yetkilendirme olayları denetlenir.<br />-SuccessAndFailure: Hem başarı ve başarısızlık hizmeti yetkilendirme olayları denetlenir.<br /><br /> Varsayılan değer, Yok'tur. Daha fazla bilgi için bkz. <xref:System.ServiceModel.AuditLevel>.|  
|messageAuthenticationAuditLevel|İleti kimlik doğrulama denetim olayları günlüğe türünü belirtir. Geçerli değerler şunlardır:<br /><br /> -Hiçbiri: Denetim olayları üretilir.<br />-BAŞARI: Yalnızca başarılı güvenlik (tam doğrulama ileti imzası doğrulama, şifreleme ve belirtecini doğrulama gibi) olaylar günlüğe kaydedilir.<br />-Hata: Yalnızca hatası olaylarının günlüğe kaydedilir.<br />-SuccessAndFailure: Hem başarılı ve başarısız olaylar günlüğe kaydedilir.<br /><br /> Varsayılan değer, Yok'tur. Daha fazla bilgi için bkz. <xref:System.ServiceModel.AuditLevel>.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<davranışı >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Bir davranış öğesi belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yapılandırma öğesi denetlemek için kullanılan [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] kimlik doğrulama olayları. Denetim etkin olduğunda başarılı veya başarısız kimlik doğrulama girişimleri (ya da her ikisi de) denetlenebilir. Üç olay günlüklerini birine yazılır: uygulama, güvenlik veya işletim sistemi sürümü için varsayılan günlük. Olay günlüklerini tüm Windows Olay Görüntüleyicisi'ni kullanarak görüntülenebilir.  
  
 Bu yapılandırma öğesini kullanarak bir ayrıntılı örnek için bkz: [hizmet denetleme davranışı](../../../../../docs/framework/wcf/samples/service-auditing-behavior.md).  
  
 Varsayılan olarak, Windows XP uygulama oturum açma olaylarını denetle görülebilir; Windows Server 2003 ve Windows Vista'te olduğu sırada, denetim olaylarını güvenlik günlüğüne görülebilir. Denetim olaylarının konumu ayarlayarak belirtilebilir `auditLogLocation` özniteliği için 'Uygulama' veya 'Security'. Daha fazla bilgi için bkz: [nasıl yapılır: denetim güvenlik olaylarını](../../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md). Güvenlik günlüğüne yazılır, LocalSecurityPolicy -> Nesne erişimini etkinleştir "Başarılı" ve "Başarısız" olarak ayarlanmalıdır.  
  
 Olay günlüğü bakarken olaylarını denetle "ServiceModel denetim 3.0.0.0" kaynağıdır. Hizmet yetkilendirme denetim kayıtlarının 'ServiceAuthorization' kategorisini bulunurken ileti kimlik doğrulama denetim kayıtlarının "MessageAuthentication" kategorisi vardır.  
  
 İleti, ileti olup süresi doldu ve istemci hizmete olup doğrulanabilir müdahale olup olmadığını ileti kimlik doğrulama denetim olaylarını kapsar. Kimlik doğrulaması başarılı oldu veya istemci kimlik yanı sıra başarısız hakkında bilgi sağlar ve uç nokta ileti ileti ile ilişkili eylem birlikte gönderildi.  
  
 Hizmet yetkilendirme denetim olaylarını hizmet Yetkilendirme Yöneticisi tarafından yapılan yetkilendirme kararı kapsar. Bunlar olup yetkilendirme, istemci kimliği ile birlikte başarısız başarılı hakkında bilgi sağlar, uç nokta ileti, ileti, gelen oluşturulan yetkilendirme Bağlam tanıtıcısı ile ilişkili eylem gönderildi gelen ileti ve erişim kararı Yetkilendirme Yöneticisi'ni türü.  
  
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
 [Güvenlik davranışları](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [Denetleme](../../../../../docs/framework/wcf/feature-details/auditing-security-events.md)  
 [Nasıl yapılır: güvenlik olaylarını denetleme](../../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md)  
 [Hizmet denetleme davranışı](../../../../../docs/framework/wcf/samples/service-auditing-behavior.md)
