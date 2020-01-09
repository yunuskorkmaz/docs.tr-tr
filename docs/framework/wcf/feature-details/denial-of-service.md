---
title: Hizmet Reddi
ms.date: 03/30/2017
helpviewer_keywords:
- denial of service [WCF]
ms.assetid: dfb150f3-d598-4697-a5e6-6779e4f9b600
ms.openlocfilehash: 4a9f3a3b7e69d33a8707a4bed5b9bc369c75f601
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346689"
---
# <a name="denial-of-service"></a>Hizmet Reddi
Bir sistem, iletilerin işlenemediği veya çok yavaş işlendiği durumlarda hizmet reddi oluşur.  
  
## <a name="excess-memory-consumption"></a>Aşırı bellek tüketimi  
 Çok sayıda benzersiz yerel ad, ad alanı veya ön ek içeren bir XML belgesi okunurken bir sorun oluşabilir. <xref:System.Xml.XmlReader>türetilen bir sınıf kullanıyorsanız ve her öğe için <xref:System.Xml.XmlReader.LocalName%2A>, <xref:System.Xml.XmlReader.Prefix%2A> ya da <xref:System.Xml.XmlReader.NamespaceURI%2A> özelliğini çağırırsanız, döndürülen dize bir <xref:System.Xml.NameTable>eklenir. <xref:System.Xml.NameTable> tarafından tutulan koleksiyon, dize tanıtıcılarının sanal bir "bellek sızıntısı" oluşturarak boyutu hiçbir şekilde düşürür.  
  
 Azaltmaları şunları içerir:  
  
- <xref:System.Xml.NameTable> sınıfından türetebilir ve en büyük boyut kotasını zorunlu tutun. (Bir <xref:System.Xml.NameTable> kullanımını önleyemez veya <xref:System.Xml.NameTable>, dolduğunda değiştiremezsiniz.)  
  
- Belirtilen özellikleri kullanmaktan kaçının ve bunun yerine mümkün olduğunda <xref:System.Xml.XmlReader.IsStartElement%2A> yöntemi ile <xref:System.Xml.XmlReader.MoveToAttribute%2A> yöntemi kullanın; Bu yöntemler dizeleri döndürmez ve bu nedenle <xref:System.Xml.NameTable> koleksiyonunu fazla doldurma sorununu ortadan kaldırmayın.  
  
## <a name="malicious-client-sends-excessive-license-requests-to-service"></a>Kötü amaçlı Istemci hizmete aşırı lisans Isteği gönderir  
 Kötü amaçlı bir istemci aşırı lisans isteği içeren bir hizmet içeriyorsa, sunucunun aşırı bellek kullanmasına neden olabilir.  
  
 Risk azaltma: <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> sınıfının aşağıdaki özelliklerini kullanın:  
  
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxCachedCookies%2A>: sunucunun `SPNego` veya `SSL` anlaşdıktan sonra önbelleğe aldığı en fazla zaman sınırlı `SecurityContextToken`s sayısını denetler.  
  
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.IssuedCookieLifetime%2A>: `SecurityContextTokens`, sunucunun `SPNego` veya `SSL` anlaşmasına göre verdiği yaşam süresini denetler. Sunucu `SecurityContextToken`s 'yi bu süre için önbelleğe alır.  
  
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxPendingSessions%2A>: sunucuda oluşturulan ancak hiçbir uygulama iletisi işlenen en fazla güvenli konuşma sayısını denetler. Bu kota, istemcilerin hizmette güvenli konuşmalar kurmasını engeller ve böylece hizmetin istemci başına durum korumasını sağlar, ancak hiçbir zaman onları kullanmıyor.  
  
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.InactivityTimeout%2A>: hizmetin istemciden konuşma için bir uygulama iletisi almadan güvenli bir konuşmayı canlı olarak sakladığı en uzun süreyi denetler. Bu kota, istemcilerin hizmette güvenli konuşmalar kurmasını engeller ve böylece hizmetin istemci başına durum korumasını sağlar, ancak hiçbir zaman onları kullanmıyor.  
  
## <a name="wsdualhttpbinding-or-dual-custom-bindings-require-client-authentication"></a>WSDualHttpBinding veya Ikili özel bağlamalar Istemci kimlik doğrulaması gerektirir  
 <xref:System.ServiceModel.WSDualHttpBinding>, varsayılan olarak güvenlik etkinleştirilmiştir. Ancak, <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> özelliği <xref:System.ServiceModel.MessageCredentialType.None>olarak ayarlanarak istemci kimlik doğrulaması devre dışı bırakılmışsa, kötü niyetli bir Kullanıcı üçüncü bir hizmette hizmet reddi saldırısına neden olabilir. Kötü amaçlı bir istemci hizmeti bir üçüncü hizmete ileti akışı göndermek üzere yönlendirebilir, bu durum oluşabilir.  
  
 Bunu azaltmak için özelliği `None`olarak ayarlamayın. Ayrıca, Çift ileti düzenine sahip özel bir bağlama oluştururken bu olasılığa de dikkat edin.  
  
## <a name="auditing-event-log-can-be-filled"></a>Denetim olayı günlüğü doldurulabilir  
 Kötü amaçlı bir kullanıcı denetimin etkinleştirildiğini anladıysa, bu saldırgan denetim girişlerinin yazılmasına neden olan geçersiz iletiler gönderebilir. Denetim günlüğü bu şekilde doldurulmuşsa, denetim sistemi başarısız olur.  
  
 Bunu azaltmak için <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> özelliğini `true` olarak ayarlayın ve Denetim davranışını denetlemek için Olay Görüntüleyicisi özelliklerini kullanın. Olay günlüklerini görüntülemek ve yönetmek için Olay Görüntüleyicisi kullanma hakkında daha fazla bilgi için bkz. [Olay Görüntüleyicisi](https://go.microsoft.com/fwlink/?LinkId=186123). Daha fazla bilgi için bkz. [Denetim](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).  
  
## <a name="invalid-implementations-of-iauthorizationpolicy-can-cause-service-to-become-unresponsive"></a>Geçersiz IAuthorizationPolicy uygulamaları hizmetin yanıt vermemesine neden olabilir  
 <xref:System.IdentityModel.Policy.IAuthorizationPolicy> arabiriminin hatalı bir uygulamasında <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%2A> yönteminin çağrılması hizmetin yanıt vermemesine neden olabilir.  
  
 Risk azaltma: yalnızca güvenilir kodu kullanın. Diğer bir deyişle, yalnızca yazdığınız ve test ettiğiniz veya güvenilir bir sağlayıcıdan gelen kodu kullanın. Güvenilmeyen <xref:System.IdentityModel.Policy.IAuthorizationPolicy> uzantılarının, önemli bir süre olmaksızın kodunuza takılmasına izin vermeyin. Bu, hizmet uygulamasında kullanılan tüm uzantılar için geçerlidir. WCF, uygulama kodu ve genişletilebilirlik noktaları kullanılarak takılan yabancı kod arasında ayrım yapmaz.  
  
## <a name="kerberos-maximum-token-size-may-need-resizing"></a>Kerberos en büyük belirteç boyutu yeniden boyutlandırılmasına gerek olabilir  
 İstemci çok sayıda gruba aitse (yaklaşık 900, ancak gerçek sayı gruplara bağlı olarak farklılık gösterir), bir ileti üstbilgisinin bloğu 64 kilobayt değerini aştığında bir sorun ortaya çıkabilir. Bu durumda,[Internet Explorer Kerberos kimlik doğrulaması, IIS 'e bağlanan yetersiz bir arabellek nedeniyle](https://go.microsoft.com/fwlink/?LinkId=89176)Microsoft desteği makalesinde açıklandığı şekilde, en yüksek Kerberos belirteç boyutunu artırabilirsiniz. Daha büyük Kerberos belirtecine uyum sağlamak için, en büyük WCF ileti boyutunu da artırmanız gerekebilir.  
  
## <a name="autoenrollment-results-in-multiple-certificates-with-same-subject-name-for-machine"></a>Otomatik kayıt, makine için aynı konu adına sahip birden çok sertifika ile sonuçlanır  
 Otomatik *kayıt* , Windows Server 2003 ' in, sertifikaları otomatik olarak kullanıcıları ve bilgisayarları kaydedecek yetenektir. Bir makine, özelliğin etkinleştirildiği bir etki alanında olduğunda, istemci kimlik doğrulamasının amaçlanan amacını taşıyan bir X. 509.440 sertifikası otomatik olarak oluşturulur ve yeni bir makine her katıldığında yerel bilgisayarın kişisel sertifika deposuna eklenir. Network. Ancak otomatik kayıt, önbellekte oluşturduğu tüm sertifikalar için aynı konu adını kullanır.  
  
 Etkisi, WCF hizmetlerinin otomatik kayıt ile etki alanlarında açılmasının başarısız olmasına neden olabilir. Bu durum, makinenin tam etki alanı adı sistemi (DNS) adına sahip birden çok sertifika olduğu için varsayılan Service X. 509.440 kimlik bilgileri arama ölçütleri belirsiz olabileceğinden belirsizdir. Bir sertifika otomatik kaydın kaynağı; diğeri kendisi tarafından verilen bir sertifika olabilir.  
  
 Bunu azaltmak için, [\<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)üzerinde daha kesin bir arama ölçütü kullanarak kullanmak üzere tam sertifikaya başvurun. Örneğin, <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByThumbprint> seçeneğini kullanın ve sertifikayı benzersiz parmak izine (karma) göre belirtin.  
  
 Otomatik kayıt özelliği hakkında daha fazla bilgi için bkz. [Windows Server 'Da sertifika otomatik kaydı 2003](https://go.microsoft.com/fwlink/?LinkId=95166).  
  
## <a name="last-of-multiple-alternative-subject-names-used-for-authorization"></a>Yetkilendirme için kullanılan birden çok alternatif konu adının son sayısı  
 Bir X. 509.440 sertifikası birden çok alternatif konu adı içerdiğinde ve alternatif konu adını kullanarak yetkilendirdiğiniz durumlarda, yetkilendirme başarısız olabilir.  
  
## <a name="protect-configuration-files-with-acls"></a>Yapılandırma dosyalarını ACL 'lerle koruma  
 Gerekli ve isteğe bağlı talepleri, CardSpace tarafından verilen belirteçler için kod ve yapılandırma dosyalarında belirtebilirsiniz. Bu, ilgili öğelerin, güvenlik belirteci hizmetine gönderilen `RequestSecurityToken` iletilerinde yayılmasına neden olur. Saldırgan, gerekli veya isteğe bağlı talepleri kaldırmak için kodu veya yapılandırmayı değiştirebilir, bu da güvenlik belirteci hizmetini hedef hizmete erişime izin verilmeyen bir belirteç verecek şekilde alabilir.  
  
 Azaltmak için: yapılandırma dosyasını değiştirmek üzere bilgisayara erişim gerektir. Yapılandırma dosyalarını güvenli hale getirmek için dosya erişim denetim listelerini (ACL 'Ler) kullanın. WCF, kodun yapılandırmadan yüklenmesine izin vermeden önce kodun uygulama dizininde veya genel derleme önbelleğinde olmasını gerektirir. Dizinlerin güvenliğini sağlamak için Dizin ACL 'Lerini kullanın.  
  
## <a name="maximum-number-of-secure-sessions-for-a-service-is-reached"></a>Bir hizmet için en fazla güvenli oturum sayısına ulaşıldı  
 Bir istemci bir hizmet tarafından başarıyla doğrulandığında ve hizmetle güvenli bir oturum yapıldığında, istemci tarafından iptal edilene veya oturumun süresi dolana kadar, hizmet oturumu izler. Belirlenen her oturum, bir hizmet ile en fazla etkin eşzamanlı oturum sayısı sınırına göre sayılır. Bu sınıra ulaşıldığında, bir veya daha fazla etkin oturumun süresi dolana veya bir istemci tarafından iptal edilene kadar bu hizmetle yeni bir oturum oluşturmayı deneyen istemciler reddedilir. Bir istemcide bir hizmetle birden fazla oturum olabilir ve bu oturumlardan her biri sınıra doğru sayılır.  
  
> [!NOTE]
> Durum bilgisi olan oturumlar kullandığınızda, önceki paragraf uygulanmaz. Durum bilgisi olan oturumlar hakkında daha fazla bilgi için bkz. [nasıl yapılır: güvenli bir oturum Için güvenlik bağlamı belirteci oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).  
  
 Bunu azaltmak için, <xref:System.ServiceModel.Channels.SecurityBindingElement> sınıfının <xref:System.ServiceModel.Channels.SecurityBindingElement> özelliğini ayarlayarak, en fazla etkin oturum sayısı ve bir oturumun maksimum yaşam süresi sınırını ayarlayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenlik Konuları](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)
- [Bilgilerin Açığa Çıkması](../../../../docs/framework/wcf/feature-details/information-disclosure.md)
- [Ayrıcalıkların Yükseltilmesi](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)
- [Hizmet Reddi](../../../../docs/framework/wcf/feature-details/denial-of-service.md)
- [Yeniden Yürütme Saldırıları](../../../../docs/framework/wcf/feature-details/replay-attacks.md)
- [İzinsiz Değişiklik](../../../../docs/framework/wcf/feature-details/tampering.md)
- [Desteklenmeyen Senaryolar](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)
