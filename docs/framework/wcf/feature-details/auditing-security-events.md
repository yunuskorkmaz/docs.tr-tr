---
title: Güvenlik Etkinliklerini Denetleme
ms.date: 03/30/2017
helpviewer_keywords:
- auditing security events [WCF]
ms.assetid: 5633f61c-a3c9-40dd-8070-1c373b66a716
ms.openlocfilehash: 535f19741ff26e9472ce56ff06b670f7d0523be8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185462"
---
# <a name="auditing-security-events"></a>Güvenlik Etkinliklerini Denetleme
Windows Communication Foundation (WCF) ile oluşturulan uygulamalar, denetim özelliğiyle güvenlik olaylarını (başarı, başarısızlık veya her ikisi) günlüğe kaydedebilir. Olaylar Windows sistemi olay günlüğüne yazılır ve Olay Görüntüleyicisi kullanılarak incelenebilir.  
  
 Denetim, yöneticinin zaten meydana gelen veya devam etmekte olan bir saldırıyı algılaması için bir yol sağlar. Ayrıca, denetim, bir geliştiricinin güvenlikle ilgili sorunları hata ayıklamasına yardımcı olabilir. Örneğin, yetkilendirme veya denetleme ilkesinin yapılandırmasındaki bir hata yanlışlıkla yetkili bir kullanıcıya erişimi reddederse, geliştirici olay günlüğünü inceleyerek bu hatanın nedenini hızlı bir şekilde keşfedebilir ve yalıtabilir.  
  
 WCF güvenliği hakkında daha fazla bilgi için [Güvenlik genel bakışı'na](../../../../docs/framework/wcf/feature-details/security-overview.md)bakın. WCF programlama hakkında daha fazla bilgi için [Temel WCF Programlama'ya](../../../../docs/framework/wcf/basic-wcf-programming.md)bakın.  
  
## <a name="audit-level-and-behavior"></a>Denetim Düzeyi ve Davranışı  
 İki güvenlik denetimi düzeyi vardır:  
  
- Arayanın yetkili olduğu hizmet yetkilendirme düzeyi.  
  
- WCF'nin ileti geçerliliğini denetlediği ve arayanın kimliğini doğruladığı ileti düzeyi.  
  
 Denetim *davranışı*olarak bilinen başarı veya başarısızlık için her iki denetim düzeylerini de denetleyebilirsiniz.  
  
## <a name="audit-log-location"></a>Denetim Günlüğü Konumu  
 Bir denetim düzeyi ve davranışı belirledikten sonra, siz (veya yönetici) denetim günlüğü için bir konum belirtebilirsiniz. Üç seçenek şunlardır: Varsayılan, Uygulama ve Güvenlik. Varsayılan olarak belirttiğiniz zaman, gerçek günlük kullandığınız sisteme ve sistemin güvenlik günlüğüne yazmayı destekleyip desteklemediğine bağlıdır. Daha fazla bilgi için bu konunun ilerleyen bölümlerinde "İşletim Sistemi" bölümüne bakın.  
  
 Güvenlik günlüğüne yazmak için `SeAuditPrivilege`. Varsayılan olarak, yalnızca Yerel Sistem ve Ağ Hizmeti hesapları bu ayrıcalığa sahiptir. Güvenlik günlüğü işlevlerini `read` `delete` yönetmek `SeSecurityPrivilege`için ve . Varsayılan olarak, yalnızca yöneticiler bu ayrıcalığa sahiptir.  
  
 Bunun aksine, kimlik doğrulaması yapılan kullanıcılar Uygulama günlüğüne okuma ve yazma yazabilir. Windows XP varsayılan olarak Uygulama günlüğüne denetim olayları yazar. Günlük, kimlik doğrulaması yapılan tüm kullanıcılar tarafından görülebilen kişisel bilgiler de içerebilir.  
  
## <a name="suppressing-audit-failures"></a>Denetim Hatalarını Bastırma  
 Denetim sırasında başka bir seçenek herhangi bir denetim hatası bastırmak için olup olmadığıdır. Varsayılan olarak, denetim hatası bir uygulamayı etkilemez. Gerekirse, ancak, bir özel durum `false`atılmasına neden olan seçeneği ayarlayabilirsiniz.  
  
## <a name="programming-auditing"></a>Programlama Denetimi  
 Denetim davranışını programlı veya yapılandırma yoluyla belirtebilirsiniz.  
  
### <a name="auditing-classes"></a>Denetim Sınıfları  
 Aşağıdaki tabloda, denetim davranışını programlamak için kullanılan sınıflar ve özellikler açıklanmaktadır.  
  
|Sınıf|Açıklama|  
|-----------|-----------------|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>|Bir hizmet davranışı olarak denetim seçenekleri ayarlamasağlar.|  
|<xref:System.ServiceModel.AuditLogLocation>|Hangi günlüğe yazılmayı belirtecek numaralandırma. Olası değerler Varsayılan, Uygulama ve Güvenlik'tir. Varsayılan'ı seçtiğinizde, işletim sistemi gerçek günlük konumunu belirler. Bu konunun ilerleyen bölümlerinde "Uygulama veya Güvenlik Olayı Günlük Seçimi" bölümüne bakın.|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.MessageAuthenticationAuditLevel%2A>|İleti kimlik doğrulama olaylarının hangi türlerinin ileti düzeyinde denetlendiği belirtilir. Seçenekler `None`, `Failure`, `Success`, `SuccessOrFailure`ve .|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.ServiceAuthorizationAuditLevel%2A>|Hizmet düzeyinde hangi hizmet yetkilendirme olaylarının denetlendiği belirtilir. Seçenekler `None`, `Failure`, `Success`, `SuccessOrFailure`ve .|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A>|Denetim başarısız olduğunda istemci isteğine ne olacağını belirtir. Örneğin, hizmet güvenlik günlüğüne yazmayı denediğinde, ancak `SeAuditPrivilege`. Varsayılan değeri `true` hataları niçin yoksaydığını ve istemci isteğinin normal olarak işlendiğini gösterir.|  
  
 Denetim olaylarını günlüğe kaydetmek için bir uygulama ayarlama örneği için [bkz.](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md)  
  
### <a name="configuration"></a>Yapılandırma  
 Ayrıca, [ \<>davranışları ](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)altında bir [ \<serviceSecurityAudit>](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md) ekleyerek denetim davranışını belirtmek için yapılandırmayı kullanabilirsiniz. Aşağıdaki kodda gösterildiği gibi [ \<bir davranış>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) altında öğe eklemeniz gerekir.  
  
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
  
 Denetim etkinse ve `auditLogLocation` bir belirtilmemişse, varsayılan günlük adı Güvenlik günlüğüne yazmayı destekleyen platform için "Güvenlik" günlüğüdür; aksi takdirde, "Uygulama" günlüğüdür. Yalnızca Windows Server 2003 ve Windows Vista işletim sistemleri Güvenlik günlüğüne yazmayı destekler. Daha fazla bilgi için bu konunun ilerleyen bölümlerinde "İşletim Sistemi" bölümüne bakın.  
  
## <a name="security-considerations"></a>Güvenlikle İlgili Dikkat Edilmesi Gerekenler  
 Kötü amaçlı bir kullanıcı denetimin etkin olduğunu biliyorsa, bu saldırgan denetim girişlerinin yazılmasına neden olan geçersiz iletiler gönderebilir. Denetim günlüğü bu şekilde doldurulursa, denetim sistemi başarısız olur. Bunu azaltmak için özelliği, <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> denetim `true` davranışını denetlemek için Olay Görüntüleyicisi'nin özelliklerini belirleyin ve kullanın.  
  
 Windows XP'deki Uygulama Günlüğü'ne yazılan denetim olayları, kimlik doğrulaması yapılan tüm kullanıcı tarafından görülebilir.  
  
## <a name="choosing-between-application-and-security-event-logs"></a>Uygulama ve Güvenlik Etkinlik Günlükleri Arasında Seçim  
 Aşağıdaki tablolar, Uygulama'da mı yoksa Güvenlik olay günlüğüne mi giriş yapacaklarını seçmenize yardımcı olacak bilgiler sağlar.  
  
#### <a name="operating-system"></a>İşletim Sistemi  
  
|Sistem|Uygulama günlüğü|Güvenlik günlüğü|  
|------------|---------------------|------------------|  
|Windows XP SP2 veya sonrası|Destekleniyor|Desteklenmiyor|  
|Windows Server 2003 SP1 ve Windows Vista|Destekleniyor|İş parçacığı bağlamı sahip olmalıdır`SeAuditPrivilege`|  
  
#### <a name="other-factors"></a>Diğer Faktörler  
 İşletim sistemine ek olarak, aşağıdaki tabloda günlüğe kaydetme olanağını kontrol eden diğer ayarlar açıklanmaktadır.  
  
|Faktörü|Uygulama günlüğü|Güvenlik günlüğü|  
|------------|---------------------|------------------|  
|Denetim ilkesi yönetimi|Geçerli değildir.|Yapılandırmanın yanı sıra, Güvenlik günlüğü yerel güvenlik yetkilisi (LSA) ilkesi tarafından da denetlenir. "Denetim nesneerişimi" kategorisi de etkinleştirilmelidir.|  
|Varsayılan kullanıcı deneyimi|Tüm kimlik doğrulaması yapılan kullanıcılar Uygulama günlüğüne yazabilir, bu nedenle uygulama işlemleri için ek izin adımı gerekmez.|Başvuru süreci (bağlam) `SeAuditPrivilege`olmalıdır.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
- <xref:System.ServiceModel.AuditLogLocation>
- [Güvenliğe Genel Bakış](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [Temel WCF Programlama](../../../../docs/framework/wcf/basic-wcf-programming.md)
- [Nasıl yapılır: Güvenlik Olaylarını Denetleme](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md)
- [\<serviceSecurityAudit>](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md)
- [\<davranışlar>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)
- [Windows Server App Fabric için Güvenlik Modeli](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
