---
title: Hizmet Reddi
ms.date: 03/30/2017
helpviewer_keywords:
- denial of service [WCF]
ms.assetid: dfb150f3-d598-4697-a5e6-6779e4f9b600
ms.openlocfilehash: 4c49e721ce4934c041b6636776c72db7839a1b1b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61857096"
---
# <a name="denial-of-service"></a>Hizmet Reddi
Hizmet reddi bir sistemde iletilerin işleneceğini veya oldukça yavaş işlenir şekilde doludur oluşur.  
  
## <a name="excess-memory-consumption"></a>Aşırı bellek tüketimi  
 Çok sayıda benzersiz yerel ad, ad alanları veya ön ekleri bir XML belgesi okunurken bir sorun oluşabilir. Türetilen bir sınıf kullanıyorsa <xref:System.Xml.XmlReader>, ve çağırın ya da <xref:System.Xml.XmlReader.LocalName%2A>, <xref:System.Xml.XmlReader.Prefix%2A> veya <xref:System.Xml.XmlReader.NamespaceURI%2A> özelliği her öğe için döndürülen dizeyi eklenen bir <xref:System.Xml.NameTable>. Tutulan koleksiyonun <xref:System.Xml.NameTable> hiçbir zaman boyutu oluşturma bir sanal azaltır "bellek sızıntısı" dize işler.  
  
 Risk azaltma işlemleri şunlardır:  
  
- Öğesinden türetilen <xref:System.Xml.NameTable> sınıfı ve en fazla boyut kotasını zorlayın. (Kullanımını önleyemez bir <xref:System.Xml.NameTable> veya geçiş <xref:System.Xml.NameTable> tam olduğunda.)  
  
- Belirtilen özellikleri kullanmaktan kaçının ve bunun yerine kullanın <xref:System.Xml.XmlReader.MoveToAttribute%2A> yöntemiyle <xref:System.Xml.XmlReader.IsStartElement%2A> yöntemi mümkün olduğunda; bu yöntemleri değil dönün dizeleri ve bu nedenle overfilling sorununu önlemek <xref:System.Xml.NameTable> koleksiyonu.  
  
## <a name="malicious-client-sends-excessive-license-requests-to-service"></a>Kötü amaçlı bir istemci aşırı lisans istekleri hizmetine gönderir.  
 Kötü amaçlı bir istemci aşırı lisans istekleri hizmetiyle bombards, aşırı bellek kullanılacak sunucuyu neden olabilir.  
  
 Azaltma: Aşağıdaki özellikleri kullanın <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> sınıfı:  
  
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxCachedCookies%2A>: zaman sınırlı maksimum sayısını kontrol `SecurityContextToken`sonra sunucunun önbelleğe alan s `SPNego` veya `SSL` anlaşması.  
  
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.IssuedCookieLifetime%2A>: ömrünü denetimleri `SecurityContextTokens` , aşağıdaki sunucu sorunlarını `SPNego` veya `SSL` anlaşması. Sunucu önbelleklerini `SecurityContextToken`bu süre boyunca s.  
  
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxPendingSessions%2A>: sunucuda ancak herhangi bir uygulama iletisi işlendi için oluşturulan güvenli konuşma en fazla sayısını denetler. Bu kota, hizmetine güvenli konuşma oluşturma, böylece istemci başına durumunu korumak üzere bir hizmetin neden, ancak hiçbir zaman kullanarak istemcilerin önler.  
  
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.InactivityTimeout%2A>: hizmet tutan bir güvenli konuşma Canlı konuşma için istemcideki bir uygulama iletisi almadan en uzun süreyi denetler. Bu kota, hizmetine güvenli konuşma oluşturma, böylece istemci başına durumunu korumak üzere bir hizmetin neden, ancak hiçbir zaman kullanarak istemcilerin önler.  
  
## <a name="wsdualhttpbinding-or-dual-custom-bindings-require-client-authentication"></a>WSDualHttpBinding veya çift özel bağlamalar istemci kimlik doğrulaması gerektir  
 Varsayılan olarak, <xref:System.ServiceModel.WSDualHttpBinding> sahip güvenlik etkin. Mümkündür, ancak olması durumunda istemci kimlik doğrulaması tarafından devre dışı ayarı <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> özelliğini <xref:System.ServiceModel.MessageCredentialType.None>, kötü niyetli bir kullanıcı bir hizmet reddi saldırısı üçüncü bir hizmet üzerinde neden olabilir. Kötü amaçlı bir istemci bir akışı üçüncü hizmet vermek için ileti göndermek için yönlendirebilirsiniz çünkü bu durum oluşabilir.  
  
 Bunu azaltmak için özellik ayarlanmamışsa `None`. Özel bağlamayı oluşturmak için bir ikili ileti deseni sahip olduğunda bu olasılığını unutmayın.  
  
## <a name="auditing-event-log-can-be-filled"></a>Olay günlüğü denetim doldurulur  
 Kötü niyetli bir kullanıcı denetiminin etkin olduğundan bilirse, bu saldırgan denetim girişleri yazılmasına neden geçersiz iletileri gönderebilir. Denetim günlüğü bu şekilde doldurulur denetim sistemi başarısız olur.  
  
 Bunu azaltmak için ayarlanmış <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> özelliğini `true` ve Denetim davranışını denetlemek için Olay Görüntüleyicisi'ni özelliklerini kullanın. Olay günlükleri görüntüleme ve yönetme için Olay Görüntüleyicisi'ni kullanma hakkında daha fazla bilgi için bkz. [Olay Görüntüleyicisi'ni](https://go.microsoft.com/fwlink/?LinkId=186123). Daha fazla bilgi için [denetim](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).  
  
## <a name="invalid-implementations-of-iauthorizationpolicy-can-cause-service-hangs"></a>Geçersiz uygulamaları IAuthorizationPolicy Can nedeni hizmet kilitleniyor  
 Çağırma <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%2A> hatalı bir uygulaması metodunda <xref:System.IdentityModel.Policy.IAuthorizationPolicy> arabirimi hizmet kilitlenmesine neden olabilir.  
  
 Azaltma: Yalnızca güvenilen kod kullanın. Güvenilen bir sağlayıcısından gelen veya diğer bir deyişle, yazılan ve test edilen kodu kullanın. Güvenilmeyen uzantılar, izin verme <xref:System.IdentityModel.Policy.IAuthorizationPolicy> kodunuzla son olmadan takılı için göz önünde bulundurarak. Bu, bir hizmet uygulaması içinde kullanılan tüm uzantılar için geçerlidir. WCF genişletilebilirlik noktaları kullanarak uygulama kodu ve takılı olduğundan yabancı kodu arasında hiçbir ayrım yapmaz.  
  
## <a name="kerberos-maximum-token-size-may-need-resizing"></a>Kerberos en büyük simge boyutu yeniden boyutlandırma gerekebilir  
 Bir istemci çok sayıda gruplarına ait olup olmadığını (yaklaşık 900 gerçek sayı gruplara bağlı olarak farklılık gösterir ancak), ileti üst bilginin blok 64 KB'ı aştığında bir sorun ortaya çıkabilir. Bu durumda, Microsoft Support makalesini içinde anlatıldığı gibi Kerberos belirteci boyut sınırını artırabilirsiniz "[Internet Explorer Kerberos kimlik doğrulaması, IIS bağlama bir yetersiz arabellek nedeniyle çalışmıyor](https://go.microsoft.com/fwlink/?LinkId=89176)." Büyük Kerberos belirteci uyum sağlamak için WCF ileti boyutunu artırmanız gerekebilir.  
  
## <a name="autoenrollment-results-in-multiple-certificates-with-same-subject-name-for-machine"></a>Makine için aynı konu adına sahip birden çok sertifika otomatik kaydını sonuçları  
 *Autoenrollment* yeteneğini olan [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] kullanıcılar ve bilgisayarlar için sertifikaları otomatik olarak kaydedilecek. Bir makine özelliği etkin bir etki alanında olduğunda, hedeflenen amacı, istemci kimlik doğrulaması ile bir X.509 sertifikası otomatik olarak oluşturulur ve yeni bir makine katıldığından her yerel bilgisayarın kişisel sertifika deposuna eklendi. Ağ. Ancak, otomatik kayıt, önbellekte oluşturduğu tüm sertifikalar aynı konu adı kullanır.  
  
 Autoenrollment etki alanlarıyla açmak WCF hizmetleri başarısız olabileceği etkisidir. Bu durum, mevcut makinenin tam etki alanı adı sistemi (DNS) ada sahip birden fazla sertifika olduğundan varsayılan hizmet X.509 kimlik bilgisi arama ölçütlerini belirsiz olabilir kaynaklanır. Bir sertifika otomatik kaydını kaynaklanan; diğer Self verilen bir sertifika olabilir.  
  
 Bunu azaltmak için üzerinde daha kesin bir arama ölçütü'ı kullanarak tam sertifika başvuru [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md). Örneğin, <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByThumbprint> seçenek ve sertifikayı benzersiz parmak izi (karma) belirtin.  
  
 Otomatik özelliği hakkında daha fazla bilgi için bkz. [Windows Server 2003'te Autoenrollment sertifikasını](https://go.microsoft.com/fwlink/?LinkId=95166).  
  
## <a name="last-of-multiple-alternative-subject-names-used-for-authorization"></a>Son yetkilendirme için kullanılan birden fazla alternatif konu adları  
 X.509 sertifikası birden fazla alternatif konu adı içerir ve alternatif konu adı kullanarak Yetkilendirme, yetkilendirme başarısız olabilir, nadir durumda.  
  
## <a name="protect-configuration-files-with-acls"></a>ACL'ler ile yapılandırma dosyaları koruma  
 Kod ve yapılandırma dosyalarında gerekli ve isteğe bağlı taleplerin belirtebilirsiniz [!INCLUDE[infocard](../../../../includes/infocard-md.md)] verilen belirteçler. İçinde yayılan karşılık gelen öğelerle sonuçlanır `RequestSecurityToken` Security'ye gönderilen iletileri belirteç hizmeti. Bir saldırganın kod veya yapılandırma gerekli veya isteğe bağlı taleplerin kaldırmak için potansiyel olarak hedef hizmete erişmesine izin vermeyen bir belirteç vermek için güvenlik belirteci hizmeti başlama değiştirebilirsiniz.  
  
 Azaltmak için: Yapılandırma dosyasını değiştirme bilgisayara erişim gerektirir. Yapılandırma dosyaları güvenli hale getirmek için listeleri (ACL'ler) dosya erişimi denetimi kullan. WCF kodların yapılandırmasından yüklenmesine izin verir önce kod uygulama dizini veya genel derleme önbelleği içinde olmasını gerektirir. Dizin ACL dizinleri güvenliğini sağlamak için kullanın.  
  
## <a name="maximum-number-of-secure-sessions-for-a-service-is-reached"></a>Güvenli oturumlar için bir hizmet sayısı üst sınırına  
 Bir istemci bir hizmet tarafından başarıyla doğrulandıktan ve güvenli bir oturum hizmetiyle kurulur, hizmet istemci iptal eder ya da oturum süresinin sona kadar oturum izler. Belirlenen her oturum için en fazla bir hizmetle etkin eşzamanlı oturum sayısını sınırından düşülür. Bu sınıra ulaşıldığında, hizmetle yeni bir oturum oluşturmayı denerseniz istemciler kadar reddedilir veya daha fazla etkin oturumlar sona veya bir istemci tarafından iptal edildi. Bir istemci bir hizmeti ile birden çok oturumu olabilir ve bu oturumları her biri sınırında sayılır.  
  
> [!NOTE]
>  Durum bilgisi olan oturumlar kullandığınızda, önceki paragrafta geçerli değildir. Durum bilgisi olan oturumlar hakkında daha fazla bilgi için bkz. [nasıl yapılır: Bir güvenlik bağlamı oluşturmak için güvenli bir oturum belirteci](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).  
  
 Bunu azaltmak için etkin oturumlar sayısı sınırı ve en fazla ömrü boyunca oturum ayarlayarak <xref:System.ServiceModel.Channels.SecurityBindingElement> özelliği <xref:System.ServiceModel.Channels.SecurityBindingElement> sınıfı.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenlik Konuları](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)
- [Bilgilerin Açığa Çıkması](../../../../docs/framework/wcf/feature-details/information-disclosure.md)
- [Ayrıcalıkların Yükseltilmesi](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)
- [Hizmet Reddi](../../../../docs/framework/wcf/feature-details/denial-of-service.md)
- [Yeniden Yürütme Saldırıları](../../../../docs/framework/wcf/feature-details/replay-attacks.md)
- [İzinsiz Değişiklik](../../../../docs/framework/wcf/feature-details/tampering.md)
- [Desteklenmeyen Senaryolar](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)
