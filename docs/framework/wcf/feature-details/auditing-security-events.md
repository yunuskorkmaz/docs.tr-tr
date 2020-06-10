---
title: Güvenlik Etkinliklerini Denetleme
ms.date: 03/30/2017
helpviewer_keywords:
- auditing security events [WCF]
ms.assetid: 5633f61c-a3c9-40dd-8070-1c373b66a716
ms.openlocfilehash: b130ed57ba086535122c8c8795c42863348870d0
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597663"
---
# <a name="auditing-security-events"></a>Güvenlik Etkinliklerini Denetleme
Windows Communication Foundation (WCF) ile oluşturulan uygulamalar, denetim özelliğiyle güvenlik olaylarını (başarı, hata veya her ikisi de) günlüğe kaydedebilir. Olaylar Windows sistem olay günlüğüne yazılır ve Olay Görüntüleyicisi kullanılarak incelenebilir.  
  
 Denetim, yöneticinin zaten oluşan veya sürmekte olan bir saldırıyı algılaması için bir yol sağlar. Ayrıca Denetim, bir geliştiricinin güvenlikle ilgili sorunları ayıklamasına yardımcı olabilir. Örneğin, yetkilendirme veya denetim ilkesi yapılandırmasındaki bir hata yetkili bir kullanıcıya yanlışlıkla erişimi reddettiğinde, geliştirici olay günlüğünü inceleyerek bu hatanın nedenini hızlıca bulabilir ve yalıtabilir.  
  
 WCF güvenliği hakkında daha fazla bilgi için bkz. [Güvenliğe genel bakış](security-overview.md). WCF programlama hakkında daha fazla bilgi için bkz. [Temel WCF programlama](../basic-wcf-programming.md).  
  
## <a name="audit-level-and-behavior"></a>Denetim düzeyi ve davranışı  
 İki güvenlik denetimi düzeyi vardır:  
  
- Bir arayanın yetkilendirildiği hizmet Yetkilendirme düzeyi.  
  
- İleti düzeyi, WCF 'nin ileti geçerliliğini kontrol ettiğini ve arayanın kimliğini doğrular.  
  
 Denetim *davranışı*olarak bilinen başarı veya başarısızlık için her iki denetim düzeyini de kontrol edebilirsiniz.  
  
## <a name="audit-log-location"></a>Denetim günlüğü konumu  
 Bir denetim düzeyi ve davranışı belirledikten sonra, siz (veya bir yönetici) denetim günlüğü için bir konum belirtebilir. Üç seçenek şunlardır: varsayılan, uygulama ve güvenlik. Varsayılan değeri belirttiğinizde, gerçek günlük kullandığınız sisteme ve sistemin güvenlik günlüğüne yazmayı destekleyip desteklemediğini belirtir. Daha fazla bilgi için bu konunun ilerleyen bölümlerindeki "Işletim sistemi" bölümüne bakın.  
  
 Güvenlik günlüğüne yazmak için için gerekir `SeAuditPrivilege` . Varsayılan olarak, yalnızca yerel sistem ve ağ hizmeti hesaplarında bu ayrıcalık vardır. Güvenlik günlüğü işlevlerini yönetmek ve için `read` `delete` gerekir `SeSecurityPrivilege` . Varsayılan olarak, yalnızca Yöneticiler bu ayrıcalığa sahiptir.  
  
 Buna karşılık, kimliği doğrulanmış kullanıcılar uygulama günlüğünü okuyup yazabilir. Windows XP, denetim olaylarını varsayılan olarak uygulama günlüğüne yazar. Günlük Ayrıca, tüm kimliği doğrulanmış kullanıcılara görünür olan kişisel bilgileri de içerebilir.  
  
## <a name="suppressing-audit-failures"></a>Denetim başarısızlıklarını gizleme  
 Denetim sırasında başka bir seçenek de herhangi bir denetim hatasının engellenip engellenmeyeceğini belirtir. Varsayılan olarak, bir denetim hatası uygulamayı etkilemez. Ancak gerekirse, seçeneğini olarak ayarlayabilirsiniz `false` , bu da bir özel durumun oluşturulmasına neden olur.  
  
## <a name="programming-auditing"></a>Programlama denetimi  
 Denetim davranışını programlı bir şekilde veya yapılandırma aracılığıyla belirtebilirsiniz.  
  
### <a name="auditing-classes"></a>Denetim sınıfları  
 Aşağıdaki tabloda, program denetleme davranışı için kullanılan sınıflar ve özellikler açıklanmaktadır.  
  
|Sınıf|Açıklama|  
|-----------|-----------------|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>|Hizmet davranışı olarak denetim için seçenekleri ayarlamaya izin vermez.|  
|<xref:System.ServiceModel.AuditLogLocation>|Hangi günlüğün yazılacağını belirten sabit listesi. Olası değerler varsayılan, uygulama ve güvenlik ' dir. Varsayılan ' ı seçtiğinizde, işletim sistemi gerçek günlük konumunu belirler. Bu konunun devamındaki "uygulama veya güvenlik olay günlüğü seçimi" bölümüne bakın.|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.MessageAuthenticationAuditLevel%2A>|İleti düzeyinde denetlenecek ileti kimlik doğrulaması olaylarının türünü belirtir. Seçenekler,, `None` ve ' dir `Failure` `Success` `SuccessOrFailure` .|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.ServiceAuthorizationAuditLevel%2A>|Hizmet düzeyinde denetlenecek hizmet Yetkilendirme olaylarının türünü belirtir. Seçenekler,, `None` ve ' dir `Failure` `Success` `SuccessOrFailure` .|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A>|Denetim başarısız olduğunda istemci isteğine ne olacağını belirtir. Örneğin, hizmet güvenlik günlüğüne yazmaya çalıştığında, ancak sahip değildir `SeAuditPrivilege` . Varsayılan değeri, `true` hataların yoksayılacağını ve istemci isteğinin normal olarak işleneceğini gösterir.|  
  
 Denetim olaylarını günlüğe kaydetmek üzere bir uygulama ayarlamaya ilişkin bir örnek için bkz. [nasıl yapılır: güvenlik olaylarını denetleme](how-to-audit-wcf-security-events.md).  
  
### <a name="configuration"></a>Yapılandırma  
 Ayrıca, altına bir ekleyerek denetim davranışını belirtmek için yapılandırma ' yı da kullanabilirsiniz [\<serviceSecurityAudit>](../../configure-apps/file-schema/wcf/servicesecurityaudit.md) [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) . [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)Aşağıdaki kodda gösterildiği gibi öğesini öğesine eklemeniz gerekir.  
  
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
  
 Denetim etkinse ve bir `auditLogLocation` belirtilmemişse, varsayılan günlük adı, güvenlik günlüğüne yazmayı destekleyen platformun "güvenlik" günlüğü olur; aksi takdirde, "uygulama" günlüğü olur. Yalnızca Windows Server 2003 ve Windows Vista işletim sistemleri güvenlik günlüğüne yazmayı destekler. Daha fazla bilgi için bu konunun ilerleyen bölümlerindeki "Işletim sistemi" bölümüne bakın.  
  
## <a name="security-considerations"></a>Güvenlikle İlgili Dikkat Edilmesi Gerekenler  
 Kötü amaçlı bir kullanıcı denetimin etkinleştirildiğini biliyorsa, bu saldırgan denetim girişlerinin yazılmasına neden olan geçersiz iletiler gönderebilir. Denetim günlüğü bu şekilde doldurulmuşsa, denetim sistemi başarısız olur. Bunu azaltmak için <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> özelliğini olarak ayarlayın `true` ve Denetim davranışını denetlemek için Olay Görüntüleyicisi özelliklerini kullanın.  
  
 Windows XP 'de uygulama günlüğüne yazılan denetim olayları, kimliği doğrulanmış herhangi bir kullanıcı tarafından görülebilir.  
  
## <a name="choosing-between-application-and-security-event-logs"></a>Uygulama ve güvenlik olay günlükleri arasında seçim yapma  
 Aşağıdaki tablolar, uygulamada veya güvenlik olay günlüğünde oturum açıp kullanmayacağınızı seçmenize yardımcı olacak bilgiler sağlar.  
  
#### <a name="operating-system"></a>İşletim Sistemi  
  
|Sistem|Uygulama günlüğü|Güvenlik günlüğü|  
|------------|---------------------|------------------|  
|Windows XP SP2 veya üzeri|Destekleniyor|Desteklenmiyor|  
|Windows Server 2003 SP1 ve Windows Vista|Destekleniyor|İş parçacığı bağlamı sahip olmalıdır`SeAuditPrivilege`|  
  
#### <a name="other-factors"></a>Diğer faktörler  
 İşletim sistemine ek olarak, aşağıdaki tabloda günlüğe kaydetme işleminin etkinleştirilmesi kontrol eden diğer ayarlar açıklanmaktadır.  
  
|Çarpan|Uygulama günlüğü|Güvenlik günlüğü|  
|------------|---------------------|------------------|  
|Denetim İlkesi Yönetimi|Geçerli değildir.|Yapılandırma ile birlikte güvenlik günlüğü de yerel güvenlik yetkilisi (LSA) ilkesi tarafından denetlenir. "Nesne erişimini denetle" kategorisinin de etkinleştirilmesi gerekir.|  
|Varsayılan Kullanıcı deneyimi|Tüm kimliği doğrulanmış kullanıcılar uygulama günlüğüne yazabilir, bu nedenle uygulama işlemlerine yönelik ek izin adımı gerekmez.|Uygulama işlemi (bağlam) olmalıdır `SeAuditPrivilege` .|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
- <xref:System.ServiceModel.AuditLogLocation>
- [Güvenliğe genel bakış](security-overview.md)
- [Temel WCF Programlama](../basic-wcf-programming.md)
- [Nasıl yapılır: Güvenlik Olaylarını Denetleme](how-to-audit-wcf-security-events.md)
- [\<serviceSecurityAudit>](../../configure-apps/file-schema/wcf/servicesecurityaudit.md)
- [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md)
- [Windows Server App Fabric için güvenlik modeli](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
