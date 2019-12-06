---
title: Güvenlik Etkinliklerini Denetleme
ms.date: 03/30/2017
helpviewer_keywords:
- auditing security events [WCF]
ms.assetid: 5633f61c-a3c9-40dd-8070-1c373b66a716
ms.openlocfilehash: fec23439236fccb23964c0feb22691a973c787b1
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74838097"
---
# <a name="auditing-security-events"></a>Güvenlik Etkinliklerini Denetleme
Windows Communication Foundation (WCF) ile oluşturulan uygulamalar, denetim özelliğiyle güvenlik olaylarını (başarı, hata veya her ikisi de) günlüğe kaydedebilir. Olaylar Windows sistem olay günlüğüne yazılır ve Olay Görüntüleyicisi kullanılarak incelenebilir.  
  
 Denetim, yöneticinin zaten oluşan veya sürmekte olan bir saldırıyı algılaması için bir yol sağlar. Ayrıca Denetim, bir geliştiricinin güvenlikle ilgili sorunları ayıklamasına yardımcı olabilir. Örneğin, yetkilendirme veya denetim ilkesi yapılandırmasındaki bir hata yetkili bir kullanıcıya yanlışlıkla erişimi reddettiğinde, geliştirici olay günlüğünü inceleyerek bu hatanın nedenini hızlıca bulabilir ve yalıtabilir.  
  
 WCF güvenliği hakkında daha fazla bilgi için bkz. [Güvenliğe genel bakış](../../../../docs/framework/wcf/feature-details/security-overview.md). WCF programlama hakkında daha fazla bilgi için bkz. [Temel WCF programlama](../../../../docs/framework/wcf/basic-wcf-programming.md).  
  
## <a name="audit-level-and-behavior"></a>Denetim düzeyi ve davranışı  
 İki güvenlik denetimi düzeyi vardır:  
  
- Bir arayanın yetkilendirildiği hizmet Yetkilendirme düzeyi.  
  
- İleti düzeyi, WCF 'nin ileti geçerliliğini kontrol ettiğini ve arayanın kimliğini doğrular.  
  
 Denetim *davranışı*olarak bilinen başarı veya başarısızlık için her iki denetim düzeyini de kontrol edebilirsiniz.  
  
## <a name="audit-log-location"></a>Denetim günlüğü konumu  
 Bir denetim düzeyi ve davranışı belirledikten sonra, siz (veya bir yönetici) denetim günlüğü için bir konum belirtebilir. Üç seçenek şunlardır: varsayılan, uygulama ve güvenlik. Varsayılan değeri belirttiğinizde, gerçek günlük kullandığınız sisteme ve sistemin güvenlik günlüğüne yazmayı destekleyip desteklemediğini belirtir. Daha fazla bilgi için bu konunun ilerleyen bölümlerindeki "Işletim sistemi" bölümüne bakın.  
  
 Güvenlik günlüğüne yazmak için `SeAuditPrivilege`gerekir. Varsayılan olarak, yalnızca yerel sistem ve ağ hizmeti hesaplarında bu ayrıcalık vardır. Güvenlik günlüğü işlevlerini yönetmek için `read` ve `delete` `SeSecurityPrivilege`gerekir. Varsayılan olarak, yalnızca Yöneticiler bu ayrıcalığa sahiptir.  
  
 Buna karşılık, kimliği doğrulanmış kullanıcılar uygulama günlüğünü okuyup yazabilir. [!INCLUDE[wxp](../../../../includes/wxp-md.md)], varsayılan olarak, denetim olaylarını uygulama günlüğüne yazar. Günlük Ayrıca, tüm kimliği doğrulanmış kullanıcılara görünür olan kişisel bilgileri de içerebilir.  
  
## <a name="suppressing-audit-failures"></a>Denetim başarısızlıklarını gizleme  
 Denetim sırasında başka bir seçenek de herhangi bir denetim hatasının engellenip engellenmeyeceğini belirtir. Varsayılan olarak, bir denetim hatası uygulamayı etkilemez. Ancak gerekirse, seçeneğini `false`olarak ayarlayabilirsiniz. Bu, bir özel durumun oluşturulmasına neden olur.  
  
## <a name="programming-auditing"></a>Programlama denetimi  
 Denetim davranışını programlı bir şekilde veya yapılandırma aracılığıyla belirtebilirsiniz.  
  
### <a name="auditing-classes"></a>Denetim sınıfları  
 Aşağıdaki tabloda, program denetleme davranışı için kullanılan sınıflar ve özellikler açıklanmaktadır.  
  
|Sınıf|Açıklama|  
|-----------|-----------------|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>|Hizmet davranışı olarak denetim için seçenekleri ayarlamaya izin vermez.|  
|<xref:System.ServiceModel.AuditLogLocation>|Hangi günlüğün yazılacağını belirten sabit listesi. Olası değerler varsayılan, uygulama ve güvenlik ' dir. Varsayılan ' ı seçtiğinizde, işletim sistemi gerçek günlük konumunu belirler. Bu konunun devamındaki "uygulama veya güvenlik olay günlüğü seçimi" bölümüne bakın.|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.MessageAuthenticationAuditLevel%2A>|İleti düzeyinde denetlenecek ileti kimlik doğrulaması olaylarının türünü belirtir. Seçenekler `None`, `Failure`, `Success`ve `SuccessOrFailure`.|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.ServiceAuthorizationAuditLevel%2A>|Hizmet düzeyinde denetlenecek hizmet Yetkilendirme olaylarının türünü belirtir. Seçenekler `None`, `Failure`, `Success`ve `SuccessOrFailure`.|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A>|Denetim başarısız olduğunda istemci isteğine ne olacağını belirtir. Örneğin, hizmet güvenlik günlüğüne yazmaya çalıştığında, ancak `SeAuditPrivilege`sahip değildir. `true` varsayılan değeri, hataların yoksayılacağını ve istemci isteğinin normal olarak işleneceğini belirtir.|  
  
 Denetim olaylarını günlüğe kaydetmek üzere bir uygulama ayarlamaya ilişkin bir örnek için bkz. [nasıl yapılır: güvenlik olaylarını denetleme](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md).  
  
### <a name="configuration"></a>Yapılandırma  
 Ayrıca, [\<davranışları >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)altına bir [\<Servicesecurityaudıt >](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md) ekleyerek denetim davranışını belirtmek için yapılandırmayı kullanabilirsiniz. Aşağıdaki kodda gösterildiği gibi, öğeyi bir [\<davranış >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) altına eklemeniz gerekir.  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <behavior>  
        <!-- auditLogLocation="Application" or "Security" -->  
        <serviceSecurityAudit  
                  auditLogLocation="Application"  
                  suppressAuditFailure="true"  
                  serviceAuthorizationAuditLevel="Failure"  
                  messageAuthenticationAuditLevel="SuccessOrFailure" />   
      </behavior>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
 Denetim etkinse ve bir `auditLogLocation` belirtilmemişse, varsayılan günlük adı, güvenlik günlüğüne yazmayı destekleyen platformun "güvenlik" günlüğü olur; Aksi halde, "uygulama" günlüğü. Yalnızca [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ve Windows Vista işletim sistemleri güvenlik günlüğüne yazmayı destekler. Daha fazla bilgi için bu konunun ilerleyen bölümlerindeki "Işletim sistemi" bölümüne bakın.  
  
## <a name="security-considerations"></a>Güvenlik Konuları  
 Kötü amaçlı bir kullanıcı denetimin etkinleştirildiğini biliyorsa, bu saldırgan denetim girişlerinin yazılmasına neden olan geçersiz iletiler gönderebilir. Denetim günlüğü bu şekilde doldurulmuşsa, denetim sistemi başarısız olur. Bunu azaltmak için <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> özelliğini `true` olarak ayarlayın ve Denetim davranışını denetlemek için Olay Görüntüleyicisi özelliklerini kullanın. Daha fazla bilgi için, [WINDOWS XP 'de Olay Görüntüleyicisi olay günlüklerini görüntüleme ve yönetme konusunda](https://go.microsoft.com/fwlink/?LinkId=89150)bulunan Windows xp 'de Olay Görüntüleyicisi kullanarak olay günlüklerini görüntüleme ve yönetme hakkında Microsoft desteği makalesine bakın.  
  
 [!INCLUDE[wxp](../../../../includes/wxp-md.md)] uygulama günlüğüne yazılan denetim olayları, kimliği doğrulanmış herhangi bir kullanıcı tarafından görülebilir.  
  
## <a name="choosing-between-application-and-security-event-logs"></a>Uygulama ve güvenlik olay günlükleri arasında seçim yapma  
 Aşağıdaki tablolar, uygulamada veya güvenlik olay günlüğünde oturum açıp kullanmayacağınızı seçmenize yardımcı olacak bilgiler sağlar.  
  
#### <a name="operating-system"></a>İşletim sistemi  
  
|Sistem|Uygulama günlüğü|Güvenlik günlüğü|  
|------------|---------------------|------------------|  
|[!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)] veya üzeri|Desteklenir|Desteklenmez|  
|[!INCLUDE[ws2003sp1](../../../../includes/ws2003sp1-md.md)] ve Windows Vista|Desteklenir|İş parçacığı bağlamı `SeAuditPrivilege` sahip olmalıdır|  
  
#### <a name="other-factors"></a>Diğer faktörler  
 İşletim sistemine ek olarak, aşağıdaki tabloda günlüğe kaydetme işleminin etkinleştirilmesi kontrol eden diğer ayarlar açıklanmaktadır.  
  
|faktörü|Uygulama günlüğü|Güvenlik günlüğü|  
|------------|---------------------|------------------|  
|Denetim İlkesi Yönetimi|Yok.|Yapılandırma ile birlikte güvenlik günlüğü de yerel güvenlik yetkilisi (LSA) ilkesi tarafından denetlenir. "Nesne erişimini denetle" kategorisinin de etkinleştirilmesi gerekir.|  
|Varsayılan Kullanıcı deneyimi|Tüm kimliği doğrulanmış kullanıcılar uygulama günlüğüne yazabilir, bu nedenle uygulama işlemlerine yönelik ek izin adımı gerekmez.|Uygulama işlemi (bağlam) `SeAuditPrivilege`sahip olmalıdır.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
- <xref:System.ServiceModel.AuditLogLocation>
- [Güvenliğe Genel Bakış](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [Temel WCF Programlama](../../../../docs/framework/wcf/basic-wcf-programming.md)
- [Nasıl yapılır: Güvenlik Olaylarını Denetleme](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md)
- [\<Servicesecurityauıdıt >](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md)
- [\<davranışlar >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)
- [Windows Server App Fabric için güvenlik modeli](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
