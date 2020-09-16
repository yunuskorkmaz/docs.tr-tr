---
title: Denial of Service (Hizmet Reddi)
ms.date: 03/30/2017
helpviewer_keywords:
- denial of service [WCF]
ms.assetid: dfb150f3-d598-4697-a5e6-6779e4f9b600
ms.openlocfilehash: 29798a73ec69b7f695068343d9c7b5593eeba4fa
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557586"
---
# <a name="denial-of-service"></a>Denial of Service (Hizmet Reddi)
Bir sistem, iletilerin işlenemediği veya çok yavaş işlendiği durumlarda hizmet reddi oluşur.  
  
## <a name="excess-memory-consumption"></a>Aşırı bellek tüketimi  
 Çok sayıda benzersiz yerel ad, ad alanı veya ön ek içeren bir XML belgesi okunurken bir sorun oluşabilir. Öğesinden türetilen bir sınıf kullanıyorsanız <xref:System.Xml.XmlReader> ve <xref:System.Xml.XmlReader.LocalName%2A> <xref:System.Xml.XmlReader.Prefix%2A> <xref:System.Xml.XmlReader.NamespaceURI%2A> her öğe için ya da özelliğini çağırdığınızda döndürülen dize bir öğesine eklenir <xref:System.Xml.NameTable> . Tarafından tutulan koleksiyon, <xref:System.Xml.NameTable> dize tanıtıcılarının sanal bir "bellek sızıntısı" oluşturma, hiçbir şekilde boyut azaltmaktadır.  
  
 Azaltmaları şunları içerir:  
  
- Sınıfından türeten <xref:System.Xml.NameTable> en büyük boyut kotasını zorunlu tutun. (Bir veya ' ın <xref:System.Xml.NameTable> dolu olduğu zaman, ' ın kullanımını engellemez <xref:System.Xml.NameTable> .)  
  
- Belirtilen özellikleri kullanmaktan kaçının ve bunun yerine <xref:System.Xml.XmlReader.MoveToAttribute%2A> yöntemi <xref:System.Xml.XmlReader.IsStartElement%2A> mümkün olduğunda kullanın; Bu yöntemler dizeleri döndürmez ve bu nedenle koleksiyonun üzerine gelme sorununu önleyin <xref:System.Xml.NameTable> .  
  
## <a name="malicious-client-sends-excessive-license-requests-to-service"></a>Kötü amaçlı Istemci hizmete aşırı lisans Isteği gönderir  
 Kötü amaçlı bir istemci aşırı lisans isteği içeren bir hizmet içeriyorsa, sunucunun aşırı bellek kullanmasına neden olabilir.  
  
 Risk azaltma: sınıfının aşağıdaki özelliklerini kullanın <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> :  
  
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxCachedCookies%2A>: `SecurityContextToken` sunucunun, `SPNego` veya anlaşmasına göre önbelleğe aldığı en fazla zaman sınırlı sayısını denetler `SSL` .  
  
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.IssuedCookieLifetime%2A>: `SecurityContextTokens` sunucunun, takip eden `SPNego` veya anlaşmasına verdiği kullanım ömrünü denetler `SSL` . Sunucu, `SecurityContextToken` s 'yi bu süre için önbelleğe alır.  
  
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxPendingSessions%2A>: sunucuda oluşturulan ancak hiçbir uygulama iletisi işlenen en fazla güvenli konuşma sayısını denetler. Bu kota, istemcilerin hizmette güvenli konuşmalar kurmasını engeller ve böylece hizmetin istemci başına durum korumasını sağlar, ancak hiçbir zaman onları kullanmıyor.  
  
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.InactivityTimeout%2A>: hizmetin istemciden konuşma için bir uygulama iletisi almadan güvenli bir konuşmayı canlı olarak sakladığı en uzun süreyi denetler. Bu kota, istemcilerin hizmette güvenli konuşmalar kurmasını engeller ve böylece hizmetin istemci başına durum korumasını sağlar, ancak hiçbir zaman onları kullanmıyor.  
  
## <a name="wsdualhttpbinding-or-dual-custom-bindings-require-client-authentication"></a>WSDualHttpBinding veya Ikili özel bağlamalar Istemci kimlik doğrulaması gerektirir  
 Varsayılan olarak, <xref:System.ServiceModel.WSDualHttpBinding> güvenlik etkindir. Ancak, istemci kimlik doğrulaması özelliği olarak ayarlanarak devre dışı bırakılmışsa <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> <xref:System.ServiceModel.MessageCredentialType.None> , kötü niyetli bir Kullanıcı üçüncü bir hizmette hizmet reddi saldırısına neden olabilir. Kötü amaçlı bir istemci hizmeti bir üçüncü hizmete ileti akışı göndermek üzere yönlendirebilir, bu durum oluşabilir.  
  
 Bunu azaltmak için özelliğini olarak ayarlamayın `None` . Ayrıca, Çift ileti düzenine sahip özel bir bağlama oluştururken bu olasılığa de dikkat edin.  
  
## <a name="auditing-event-log-can-be-filled"></a>Denetim olayı günlüğü doldurulabilir  
 Kötü amaçlı bir kullanıcı denetimin etkinleştirildiğini anladıysa, bu saldırgan denetim girişlerinin yazılmasına neden olan geçersiz iletiler gönderebilir. Denetim günlüğü bu şekilde doldurulmuşsa, denetim sistemi başarısız olur.  
  
 Bunu azaltmak için <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> özelliğini olarak ayarlayın `true` ve Denetim davranışını denetlemek için Olay Görüntüleyicisi özelliklerini kullanın. Olay günlüklerini görüntülemek ve yönetmek için Olay Görüntüleyicisi kullanma hakkında daha fazla bilgi için bkz. [Olay Görüntüleyicisi](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc766042(v=ws.11)). Daha fazla bilgi için bkz. [Denetim](auditing-security-events.md).  
  
## <a name="invalid-implementations-of-iauthorizationpolicy-can-cause-service-to-become-unresponsive"></a>Geçersiz IAuthorizationPolicy uygulamaları hizmetin yanıt vermemesine neden olabilir  
 Yöntemi, <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%2A> arabirimin hatalı bir uygulamasında çağırmak <xref:System.IdentityModel.Policy.IAuthorizationPolicy> hizmetin yanıt vermemesine neden olabilir.  
  
 Risk azaltma: yalnızca güvenilir kodu kullanın. Diğer bir deyişle, yalnızca yazdığınız ve test ettiğiniz veya güvenilir bir sağlayıcıdan gelen kodu kullanın. Güvenilmeyen uzantıların <xref:System.IdentityModel.Policy.IAuthorizationPolicy> kodunuza hiçbir süre olmaksızın takılmasına izin vermeyin. Bu, hizmet uygulamasında kullanılan tüm uzantılar için geçerlidir. WCF, uygulama kodu ve genişletilebilirlik noktaları kullanılarak takılan yabancı kod arasında ayrım yapmaz.  
  
## <a name="kerberos-maximum-token-size-may-need-resizing"></a>Kerberos en büyük belirteç boyutu yeniden boyutlandırılmasına gerek olabilir  
 İstemci çok sayıda gruba aitse (yaklaşık 900, ancak gerçek sayı gruplara bağlı olarak farklılık gösterir), bir ileti üstbilgisinin bloğu 64 kilobayt değerini aştığında bir sorun ortaya çıkabilir. Bu durumda, en fazla Kerberos belirteç boyutunu artırabilirsiniz. Daha büyük Kerberos belirtecine uyum sağlamak için, en büyük WCF ileti boyutunu da artırmanız gerekebilir.  
  
## <a name="autoenrollment-results-in-multiple-certificates-with-same-subject-name-for-machine"></a>Otomatik kayıt, makine için aynı konu adına sahip birden çok sertifika ile sonuçlanır  
 Otomatik *kayıt* , Windows Server 2003 ' in, sertifikaları otomatik olarak kullanıcıları ve bilgisayarları kaydedecek yetenektir. Bir makine, özelliğin etkinleştirildiği bir etki alanında olduğunda, ağa her yeni makine katıldığında, istemci kimlik doğrulamasının amaçlanan amacını taşıyan bir X. 509.440 sertifikası otomatik olarak oluşturulur ve yerel bilgisayarın kişisel sertifika deposuna eklenir. Ancak otomatik kayıt, önbellekte oluşturduğu tüm sertifikalar için aynı konu adını kullanır.  
  
 Etkisi, WCF hizmetlerinin otomatik kayıt ile etki alanlarında açılmasının başarısız olmasına neden olabilir. Bu durum, makinenin tam etki alanı adı sistemi (DNS) adına sahip birden çok sertifika olduğu için varsayılan Service X. 509.440 kimlik bilgileri arama ölçütleri belirsiz olabileceğinden belirsizdir. Bir sertifika otomatik kaydın kaynağı; diğeri kendisi tarafından verilen bir sertifika olabilir.  
  
 Bunu azaltmak için, üzerinde daha kesin bir arama ölçütü kullanarak kullanmak üzere tam sertifikaya başvurun [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) . Örneğin, <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByThumbprint> seçeneğini kullanın ve sertifikayı benzersiz parmak izine (karma) göre belirtin.  
  
 Otomatik kayıt özelliği hakkında daha fazla bilgi için bkz. [Windows Server 'Da sertifika otomatik kaydı 2003](/previous-versions/windows/it-pro/windows-server-2003/cc778954(v=ws.10)).  
  
## <a name="last-of-multiple-alternative-subject-names-used-for-authorization"></a>Yetkilendirme için kullanılan birden çok alternatif konu adının son sayısı  
 Bir X. 509.440 sertifikası birden çok alternatif konu adı içerdiğinde ve alternatif konu adını kullanarak yetkilendirdiğiniz durumlarda, yetkilendirme başarısız olabilir.  
  
## <a name="protect-configuration-files-with-acls"></a>Yapılandırma dosyalarını ACL 'lerle koruma  
 Gerekli ve isteğe bağlı talepleri, CardSpace tarafından verilen belirteçler için kod ve yapılandırma dosyalarında belirtebilirsiniz. Bu, ilgili öğelerin `RequestSecurityToken` güvenlik belirteci hizmetine gönderilen iletilerde yayılmasına neden olur. Saldırgan, gerekli veya isteğe bağlı talepleri kaldırmak için kodu veya yapılandırmayı değiştirebilir, bu da güvenlik belirteci hizmetini hedef hizmete erişime izin verilmeyen bir belirteç verecek şekilde alabilir.  
  
 Azaltmak için: yapılandırma dosyasını değiştirmek üzere bilgisayara erişim gerektir. Yapılandırma dosyalarını güvenli hale getirmek için dosya erişim denetim listelerini (ACL 'Ler) kullanın. WCF, kodun yapılandırmadan yüklenmesine izin vermeden önce kodun uygulama dizininde veya genel derleme önbelleğinde olmasını gerektirir. Dizinlerin güvenliğini sağlamak için Dizin ACL 'Lerini kullanın.  
  
## <a name="maximum-number-of-secure-sessions-for-a-service-is-reached"></a>Bir hizmet için en fazla güvenli oturum sayısına ulaşıldı  
 Bir istemci bir hizmet tarafından başarıyla doğrulandığında ve hizmetle güvenli bir oturum yapıldığında, istemci tarafından iptal edilene veya oturumun süresi dolana kadar, hizmet oturumu izler. Belirlenen her oturum, bir hizmet ile en fazla etkin eşzamanlı oturum sayısı sınırına göre sayılır. Bu sınıra ulaşıldığında, bir veya daha fazla etkin oturumun süresi dolana veya bir istemci tarafından iptal edilene kadar bu hizmetle yeni bir oturum oluşturmayı deneyen istemciler reddedilir. Bir istemcide bir hizmetle birden fazla oturum olabilir ve bu oturumlardan her biri sınıra doğru sayılır.  
  
> [!NOTE]
> Durum bilgisi olan oturumlar kullandığınızda, önceki paragraf uygulanmaz. Durum bilgisi olan oturumlar hakkında daha fazla bilgi için bkz. [nasıl yapılır: güvenli bir oturum Için güvenlik bağlamı belirteci oluşturma](how-to-create-a-security-context-token-for-a-secure-session.md).  
  
 Bunu azaltmak için, sınıfının özelliğini ayarlayarak, en fazla etkin oturum sayısı ve bir oturumun maksimum yaşam süresi sınırını ayarlayın <xref:System.ServiceModel.Channels.SecurityBindingElement> <xref:System.ServiceModel.Channels.SecurityBindingElement> .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenlik konuları](security-considerations-in-wcf.md)
- [Bilgilerin Açığa Çıkması](information-disclosure.md)
- [Ayrıcalık Yükseltme](elevation-of-privilege.md)
- [Hizmet Reddi](denial-of-service.md)
- [Yeniden Yürütme Saldırıları](replay-attacks.md)
- [Kurcalama](tampering.md)
- [Desteklenmeyen Senaryolar](unsupported-scenarios.md)
