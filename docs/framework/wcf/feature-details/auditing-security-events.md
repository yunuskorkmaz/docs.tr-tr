---
title: Güvenlik Etkinliklerini Denetleme
ms.date: 03/30/2017
helpviewer_keywords:
- auditing security events [WCF]
ms.assetid: 5633f61c-a3c9-40dd-8070-1c373b66a716
ms.openlocfilehash: 7d19c32994fdfc5587c06b979886f20ab2a04508
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62048280"
---
# <a name="auditing-security-events"></a>Güvenlik Etkinliklerini Denetleme
Windows Communication Foundation (WCF) ile oluşturulan uygulamalar (başarı, başarısızlık veya her ikisi de) güvenlik olaylarını denetleme özelliği ile oturum açabilirsiniz. Olayları Windows sistem olay günlüğüne yazılır ve Olay Görüntüleyicisi'ni kullanarak incelenebilir.  
  
 Denetim, bir yöneticinin devam ediyor veya zaten bir saldırı algılamak bir yol sağlar. Ayrıca, Denetim güvenlikle ilgili sorunların hatalarını ayıklamak için geliştirici olmanıza yardımcı olabilir. Örneğin, yetkilendirme ve Denetim İlkesi yapılandırmasında bir hata için yetkili bir kullanıcı yanlışlıkla erişimi reddederse, bir geliştirici hızlı bir şekilde bulmak ve olay günlüğünü inceleyerek bu hatanın nedenini ayırmak.  
  
 WCF güvenlik hakkında daha fazla bilgi için bkz: [güvenliğine genel bakış](../../../../docs/framework/wcf/feature-details/security-overview.md). WCF programlama hakkında daha fazla bilgi için bkz. [temel WCF programlama](../../../../docs/framework/wcf/basic-wcf-programming.md).  
  
## <a name="audit-level-and-behavior"></a>Denetim düzeyi ve davranışı  
 İki düzeyde güvenlik denetimleri mevcuttur:  
  
- Hizmet, bir çağıranın yetkili yetkilendirme düzeyi.  
  
- İleti düzeyi, WCF ileti geçerliliğini denetler ve arayan kimliğini doğrular.  
  
 Her ikisi de başarılı veya başarısız olarak da bilinen düzeylerini denetim denetleyebilirsiniz *davranışını denetleme*.  
  
## <a name="audit-log-location"></a>Denetim günlüğü konumu  
 Bir denetim düzeyi ve davranış belirledikten sonra (veya yönetici) denetim günlüğü için bir konum belirtebilirsiniz. Üç seçenek içerir: Varsayılan, uygulama ve güvenlik. Varsayılan belirttiğinizde, hangi sistemde kullandığınız gerçek günlük bağlıdır ve sistem güvenlik günlüğüne yazma destekleyip desteklemediğini. Daha fazla bilgi için bu konunun ilerleyen bölümlerindeki "İşletim sistemi" bölümüne bakın.  
  
 Güvenlik günlüğüne yazmak için gerekli `SeAuditPrivilege`. Varsayılan olarak, yalnızca yerel sistem ve ağ hizmeti hesapları, bu ayrıcalığına sahip. Güvenlik günlüğü işlevlerini yönetmek için `read` ve `delete` gerektirir `SeSecurityPrivilege`. Varsayılan olarak, yalnızca Yöneticiler bu ayrıcalığına sahip.  
  
 Buna karşılık, kimliği doğrulanmış kullanıcılar okuyabilir ve uygulama günlüğüne yazma. [!INCLUDE[wxp](../../../../includes/wxp-md.md)] yazma, varsayılan olarak uygulama günlüğü olaylarını denetleyin. Günlük, ayrıca tüm kimliği doğrulanmış kullanıcılar için görünür olan kişisel bilgiler içerebilir.  
  
## <a name="suppressing-audit-failures"></a>Denetim başarısızlıklarını gösterme/gizleme  
 Denetim sırasında başka bir seçenek herhangi bir denetim hatası engellenip engellenmeyeceğini olur. Varsayılan olarak, bir uygulama bir denetim hatası etkilemez. Zorunlu kılınırsa, ancak seçeneği ayarlayabilirsiniz `false`, bir özel durum oluşturulmasına neden olur.  
  
## <a name="programming-auditing"></a>Programlama denetleme  
 Program aracılığıyla veya yapılandırma yoluyla denetim davranış belirtebilirsiniz.  
  
### <a name="auditing-classes"></a>Denetim sınıfları  
 Aşağıdaki tabloda, sınıflar ve denetim davranışı programlamak için kullanılan özellikleri açıklanmaktadır.  
  
|örneği|Açıklama|  
|-----------|-----------------|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>|Bir hizmet davranışı denetleme seçeneklerini ayarlama sağlar.|  
|<xref:System.ServiceModel.AuditLogLocation>|Yazma oturum belirtmek için sabit listesi. Olası değerler şunlardır: varsayılan, uygulama ve güvenlik. Varsayılan seçtiğinizde, işletim sistemini gerçek günlük konumunu belirler. Bu konunun devamındaki "Uygulama veya güvenlik olay günlüğü seçim" bölümüne bakın.|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.MessageAuthenticationAuditLevel%2A>|İleti kimlik doğrulama olaylarını hangi tür ileti düzeyinde denetleneceğini belirler. Seçimler `None`, `Failure`, `Success`, ve `SuccessOrFailure`.|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.ServiceAuthorizationAuditLevel%2A>|Hizmet yetkilendirme olay türlerini hizmet düzeyinde denetlenir belirtir. Seçimler `None`, `Failure`, `Success`, ve `SuccessOrFailure`.|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A>|İstemci isteği denetim başarısız olacağını belirtir. Örneğin, zaman hizmeti güvenlik günlüğüne yazmayı dener, ancak sahip değil `SeAuditPrivilege`. Varsayılan değer olan `true` hataları dikkate alınmaz ve istemci isteğinin normal olarak işlenen gösterir.|  
  
 Bir uygulama denetim olaylarını günlüğe kaydedecek şekilde ayarlama örneği için bkz. [nasıl yapılır: Güvenlik olaylarını denetleme](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md).  
  
### <a name="configuration"></a>Yapılandırma  
 Yapılandırma ekleyerek Denetim davranışını belirtmek için de kullanabilirsiniz bir [ \<serviceSecurityAudit >](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md) altında [ \<davranışları >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md). Öğesi altında eklemelisiniz bir [ \<davranışı >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) aşağıdaki kodda gösterildiği gibi.  
  
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
  
 Denetimi etkinse ve bir `auditLogLocation` değil belirtilmezse, varsayılan günlük güvenlik günlüğüne yazmayı destekleyen bir platform için "Güvenlik" günlük adıdır; Aksi takdirde, "Uygulama" günlük bir değer. Yalnızca [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ve [!INCLUDE[wv](../../../../includes/wv-md.md)] güvenlik günlüğüne yazma işletim sistemlerini destekler. Daha fazla bilgi için bu konunun ilerleyen bölümlerindeki "İşletim sistemi" bölümüne bakın.  
  
## <a name="security-considerations"></a>Güvenlik Değerlendirmeleri  
 Kötü niyetli bir kullanıcı denetiminin etkin olduğundan biliyorsa, bu saldırgan denetim girişleri yazılmasına neden geçersiz iletileri gönderebilir. Denetim günlüğü bu şekilde doldurulur denetim sistemi başarısız olur. Bunu azaltmak için ayarlanmış <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> özelliğini `true` ve Denetim davranışını denetlemek için Olay Görüntüleyicisi'ni özelliklerini kullanın. Daha fazla bilgi için Microsoft Support makalesini görüntüleme ve Windows XP'de kullanılabilir Olay Görüntüleyicisi'ni kullanarak olay günlüklerini yönetme bakın [görüntülemek ve olay günlüklerini Olay Görüntüleyicisi'nde Windows XP yönetmek nasıl](https://go.microsoft.com/fwlink/?LinkId=89150).  
  
 Uygulama günlüğüne yazılan iş olaylarını denetleme [!INCLUDE[wxp](../../../../includes/wxp-md.md)] herhangi bir kimliği doğrulanmış kullanıcı tarafından görülebilir.  
  
## <a name="choosing-between-application-and-security-event-logs"></a>Uygulama ve güvenlik olayı günlükleri arasında seçim yapma  
 Aşağıdaki tablolarda, uygulama ya da güvenlik olay günlüğü kaydedilip edilmeyeceğini seçmenize yardımcı olacak bilgiler verilmektedir.  
  
#### <a name="operating-system"></a>İşletim sistemi  
  
|Sistem|Uygulama günlüğü|Güvenlik günlüğü|  
|------------|---------------------|------------------|  
|[!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)] veya üzeri|Desteklenir|Desteklenmez|  
|[!INCLUDE[ws2003sp1](../../../../includes/ws2003sp1-md.md)] ve [!INCLUDE[wv](../../../../includes/wv-md.md)]|Desteklenir|İş parçacığı bağlamı sahip olması gerekir `SeAuditPrivilege`|  
  
#### <a name="other-factors"></a>Diğer faktörler  
 Ek olarak işletim sistemi, aşağıdaki tabloda günlük etkinleştirme denetleyen diğer ayarlar açıklanmaktadır.  
  
|faktörü|Uygulama günlüğü|Güvenlik günlüğü|  
|------------|---------------------|------------------|  
|Denetim İlkesi Yönetimi|Geçerli değildir.|Yapılandırması ile birlikte, güvenlik günlüğü ayrıca yerel güvenlik yetkilisi (LSA) ilkesi tarafından kontrol edilir. "Nesne erişimini denetle" kategorisi de etkinleştirilmesi gerekir.|  
|Varsayılan kullanıcı deneyimi|Uygulama işlemleri için hiçbir ek adım gerekmez, tüm kimliği doğrulanmış kullanıcılara uygulama günlüğüne yazabilirsiniz.|(Bağlam) uygulama işlemi olmalıdır `SeAuditPrivilege`.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
- <xref:System.ServiceModel.AuditLogLocation>
- [Güvenliğe Genel Bakış](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [Temel WCF Programlama](../../../../docs/framework/wcf/basic-wcf-programming.md)
- [Nasıl yapılır: Güvenlik olaylarını denetleme](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md)
- [\<serviceSecurityAudit >](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md)
- [\<davranışlar >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)
- [Windows Server AppFabric için güvenlik modeli](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
