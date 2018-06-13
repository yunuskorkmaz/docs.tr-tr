---
title: Hizmet Reddi
ms.date: 03/30/2017
helpviewer_keywords:
- denial of service [WCF]
ms.assetid: dfb150f3-d598-4697-a5e6-6779e4f9b600
ms.openlocfilehash: 52a22d96e981ff10d444569465d8e74ddf890836
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33496119"
---
# <a name="denial-of-service"></a>Hizmet Reddi
Hizmet reddi oluşur. bir sistem iletileri işlenemiyor veya çok yavaş işlenene bir şekilde doludur.  
  
## <a name="excess-memory-consumption"></a>Aşırı bellek tüketimi  
 Çok sayıda benzersiz yerel adları, ad alanlarını ve önekleri XML belgesiyle okunurken bir sorun oluşabilir. Öğesinden türeyen bir sınıf kullanıyorsanız <xref:System.Xml.XmlReader>, ve ya da çağırın <xref:System.Xml.XmlReader.LocalName%2A>, <xref:System.Xml.XmlReader.Prefix%2A> veya <xref:System.Xml.XmlReader.NamespaceURI%2A> her öğe için özelliği, döndürülen dize eklenen bir <xref:System.Xml.NameTable>. Tutulan koleksiyonu <xref:System.Xml.NameTable> hiçbir zaman bir sanal oluşturma boyutunda azaltır, dize tanıtıcısı "bellek sızıntısı".  
  
 Azaltıcı Etkenler şunlardır:  
  
-   Öğesinden türetilen <xref:System.Xml.NameTable> sınıfı ve en büyük boyutu kotası zorlayın. (Kullanımını engelleyemez bir <xref:System.Xml.NameTable> veya geçiş <xref:System.Xml.NameTable> olduğu zaman tam.)  
  
-   Belirtilen özellikleri kullanmaktan kaçının ve bunun yerine kullanın <xref:System.Xml.XmlReader.MoveToAttribute%2A> yöntemiyle <xref:System.Xml.XmlReader.IsStartElement%2A> yöntemi mümkün olduğunca; bu yöntemleri değil dönün dizeler ve böylece overfilling, bir sorunu önlemenize <xref:System.Xml.NameTable> koleksiyonu.  
  
## <a name="malicious-client-sends-excessive-license-requests-to-service"></a>Kötü amaçlı istemci aşırı lisans istekleri hizmetine gönderir.  
 Kötü amaçlı bir istemci aşırı lisans istekleri hizmetiyle bombards, aşırı bellek kullanmak sunucunun neden olabilir.  
  
 Azaltma: aşağıdaki özelliklerini kullanmak <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> sınıfı:  
  
-   <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxCachedCookies%2A>: saat ilişkisindeki, maksimum sayısını kontrol `SecurityContextToken`sonra sunucu önbelleğe s `SPNego` veya `SSL` anlaşma.  
  
-   <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.IssuedCookieLifetime%2A>: ömrü denetimleri `SecurityContextTokens` , aşağıdaki sunucu sorunları `SPNego` veya `SSL` anlaşma. Sunucu önbelleklerini `SecurityContextToken`s Bu süre.  
  
-   <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxPendingSessions%2A>: sunucuda ancak hiçbir uygulama ileti işlendikten için kurulmuş güvenli konuşmaları en fazla sayısını denetler. Bu kota istemcilerin konuşması güvenli konuşmaları oluşturma, böylece istemci başına durumunu korumak üzere bir hizmetin neden, ancak hiçbir zaman kullanmadan önler.  
  
-   <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.InactivityTimeout%2A>: hizmet tutar güvenli bir konuşma Canlı istemcisinden konuşma için bir uygulama iletisi almadan en fazla süreyi denetler. Bu kota istemcilerin konuşması güvenli konuşmaları oluşturma, böylece istemci başına durumunu korumak üzere bir hizmetin neden, ancak hiçbir zaman kullanmadan önler.  
  
## <a name="wsdualhttpbinding-or-dual-custom-bindings-require-client-authentication"></a>WSDualHttpBinding veya özel çift bağlamalarını istemci kimlik doğrulaması gerektirir  
 Varsayılan olarak, <xref:System.ServiceModel.WSDualHttpBinding> sahip güvenliği etkinleştirilmiş. Mümkündür, ancak, bu istemci kimlik doğrulaması tarafından devre dışı ayarı <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> özelliğine <xref:System.ServiceModel.MessageCredentialType.None>, kötü niyetli bir kullanıcı bir hizmet reddi saldırısına üçüncü bir hizmete neden olabilir. Kötü amaçlı bir istemci bir akış üçüncü hizmet iletilerinin göndermek üzere hizmetini yönlendirebilirsiniz olduğundan bu durum oluşabilir.  
  
 Bunu azaltmak için özellik ayarlanmamışsa `None`. Özel bağlama oluşturma bir ikili ileti deseni sahip olduğunda bu olasılığını unutmayın.  
  
## <a name="auditing-event-log-can-be-filled"></a>Olay günlüğü denetleme doldurulabilir  
 Kötü niyetli bir kullanıcı denetimi etkinleştirildiğini bilirse, bu saldırgan denetim girişlerini yazılmasına neden geçersiz iletileri gönderebilir. Bu şekilde denetim günlüğü dolu denetim sistemi başarısız olur.  
  
 Bu durumu iyileştirmek için ayarlanmış <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> özelliğine `true` ve Denetim davranışını denetlemek için Olay Görüntüleyicisi'ni özelliklerini kullanın. Olay günlükleri görüntüleme ve yönetme için Olay Görüntüleyicisi'ni kullanma hakkında daha fazla bilgi için bkz: [Olay Görüntüleyicisi'ni](http://go.microsoft.com/fwlink/?LinkId=186123). Daha fazla bilgi için bkz: [denetim](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).  
  
## <a name="invalid-implementations-of-iauthorizationpolicy-can-cause-service-hangs"></a>Geçersiz uygulamaları IAuthorizationPolicy Can neden Hizmeti kilitleniyor  
 Çağırma <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%2A> hatalı uyarlamasını yöntemi <xref:System.IdentityModel.Policy.IAuthorizationPolicy> arabirimi hizmet askıda kalmasına neden olabilir.  
  
 Azaltma: yalnızca güvenilir kodunu kullanın. Diğer bir deyişle, kullanan yazılmış ve test kod veya güvenilen bir sağlayıcı gelir. Güvenilmeyen uzantılarını izin verme <xref:System.IdentityModel.Policy.IAuthorizationPolicy> kodunuzu son olmadan takılı için göz önünde bulundurarak. Bu, bir hizmet uygulamasında kullanılan tüm uzantıları uygular. WCF, genişletilebilirlik noktaları kullanarak uygulama kodu ve takılı yabancı kodu arasında hiçbir ayrım yapmaz.  
  
## <a name="kerberos-maximum-token-size-may-need-resizing"></a>Yeniden boyutlandırma Kerberos en büyük simge boyutu gerekebilir  
 Bir istemci çok sayıda grupları ait olup olmadığını (yaklaşık 900 gerçek sayı grupları bağlı olarak değişir rağmen), ileti üst bilginin blok 64 kilobayt aştığında bir sorun ortaya çıkabilir. Bu durumda, Microsoft Support makalesini içinde açıklandığı gibi en yüksek Kerberos belirteci boyutunu artırabilirsiniz "[Internet Explorer Kerberos kimlik doğrulaması için IIS bağlanan bir yetersiz arabellek nedeniyle çalışmıyor](http://go.microsoft.com/fwlink/?LinkId=89176)." Büyük Kerberos belirteci uyum sağlamak için WCF ileti sınırını artırmak gerekebilir.  
  
## <a name="autoenrollment-results-in-multiple-certificates-with-same-subject-name-for-machine"></a>Makine için aynı konu adına sahip birden çok sertifika otomatik kaydını sonuçları  
 *Otomatik kayıt* yeteneğini olduğu [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] kullanıcıları ve bilgisayarları sertifikalar için otomatik olarak kaydedilecek. Bir makine özelliği etkinleştirilmiş bir etki alanında olduğunda, istemci kimlik doğrulaması hedeflenen amacı olan bir X.509 sertifikası otomatik olarak oluşturulur ve yeni bir makine katıldığı her yerel bilgisayarın kişisel sertifika deposuna eklendi Ağ. Ancak, otomatik kayıt önbellekte oluşturduğu tüm sertifikalar aynı konu adı kullanır.  
  
 WCF hizmetleri autoenrollment etki alanlarıyla açmak başlatılamayabilir etkisidir. Bu durum, makine tam olarak nitelenmiş etki alanı adı sistemi (DNS) adıyla birden fazla sertifika var olduğundan varsayılan hizmet X.509 kimlik bilgisi arama ölçütlerini belirsiz olabilir kaynaklanır. Bir sertifika otomatik kaydını kaynaklanan; diğer bir kendi kendine sertifikayı olabilir.  
  
 Bunu azaltmak için üzerinde daha kesin bir arama ölçütü kullanarak tam sertifika başvuru [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md). Örneğin, <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByThumbprint> seçeneği ve kendi benzersiz parmak izi tarafından (karma) sertifikasını belirtin.  
  
 Otomatik kayıt özelliği hakkında daha fazla bilgi için bkz: [Windows Server 2003'te sertifika otomatik kaydını](http://go.microsoft.com/fwlink/?LinkId=95166).  
  
## <a name="last-of-multiple-alternative-subject-names-used-for-authorization"></a>Son yetkilendirme için kullanılan birden fazla alternatif konu adları  
 Birden çok alternatif konu adı, bir X.509 sertifikası içerir ve alternatif konu adı kullanarak yetkilendirmek, yetkilendirme başarısız olabileceği ender durumda.  
  
## <a name="protect-configuration-files-with-acls"></a>ACL'ler ile yapılandırma dosyalarını koruyun  
 Kod ve yapılandırma dosyaları için gerekli ve isteğe bağlı talep belirtebilirsiniz [!INCLUDE[infocard](../../../../includes/infocard-md.md)] verilen belirteçler. Bu ilgili öğeleri de gösterilmesini sonuçlanır `RequestSecurityToken` güvenlik gönderilen iletileri hizmet belirteci. Bir saldırgan kod veya yapılandırma gerekli veya isteğe bağlı talep kaldırmak için potansiyel olarak hedef hizmete erişim izni olmayan bir belirteç vermek için güvenlik belirteci hizmeti alma değişiklik yapabilirsiniz.  
  
 Azaltmak için: yapılandırma dosyasını değiştirmek için bilgisayara erişimi gerektirir. Dosya erişimi denetimi kullan yapılandırma dosyalarını güvenli hale getirmek için listeleri (ACL'ler). WCF yapılandırmasından yüklenmesi gibi kodu sağlayacak önce kodu uygulama dizini veya genel derleme önbelleği olmasını gerektirir. Dizin ACL dizinleri güvenliğini sağlamak için kullanın.  
  
## <a name="maximum-number-of-secure-sessions-for-a-service-is-reached"></a>Bir hizmet için güvenli oturumlar sayısı üst sınırına  
 Bir istemci bir hizmet tarafından başarıyla doğrulandıktan ve güvenli bir oturum hizmetiyle kurulan hizmeti istemci iptal eder veya oturum süresinin sona kadar oturum izler. Her kurulan oturum sınırınızı için en fazla bir hizmetle etkin eşzamanlı oturum sayısını sayar. Bu sınıra ulaşıldığında, yeni bir oturum hizmetle oluşturma denemesi istemcileri kadar reddedilir veya fazla etkin oturum sona veya istemci tarafından iptal edildi. Bir istemci bir hizmet ile birden çok oturumu olabilir ve her biri bu oturumlar, sınırında sayılır.  
  
> [!NOTE]
>  Durum bilgisi olan oturumlar kullandığınızda, önceki paragrafta geçerli değildir. Durum bilgisi olan oturumlar hakkında daha fazla bilgi için bkz: [nasıl yapılır: güvenli oturum açmak için bir güvenlik bağlamı belirteci oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).  
  
 Bunu azaltmak için bir oturum için en uzun kullanım ömrünü ve en fazla etkin oturum sayısı sınırı ayarlamak için <xref:System.ServiceModel.Channels.SecurityBindingElement> özelliği <xref:System.ServiceModel.Channels.SecurityBindingElement> sınıfı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Güvenlik Konuları](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)  
 [Bilgilerin Açığa Çıkması](../../../../docs/framework/wcf/feature-details/information-disclosure.md)  
 [Ayrıcalıkların Yükseltilmesi](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)  
 [Hizmet Reddi](../../../../docs/framework/wcf/feature-details/denial-of-service.md)  
 [Yeniden Yürütme Saldırıları](../../../../docs/framework/wcf/feature-details/replay-attacks.md)  
 [İzinsiz Değişiklik](../../../../docs/framework/wcf/feature-details/tampering.md)  
 [Desteklenmeyen Senaryolar](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)
