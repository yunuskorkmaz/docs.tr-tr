---
title: HTTP Taşıma Güvenliği
ms.date: 03/30/2017
ms.assetid: d3439262-c58e-4d30-9f2b-a160170582bb
ms.openlocfilehash: 4bd3fbfd39538eee4344ef0a8ca4fe61b372ab70
ms.sourcegitcommit: 09b4090b78f52fd09b0e430cd4b26576f1fdf96e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76212141"
---
# <a name="http-transport-security"></a>HTTP Taşıma Güvenliği
Aktarım olarak HTTP kullanırken güvenlik, bir Güvenli Yuva Katmanı (SSL) uygulamasıyla sağlanır. SSL, bir istemcide bir hizmetin kimliğini doğrulamak ve ardından kanala Gizlilik (şifreleme) sağlamak için Internet 'te yaygın olarak kullanılır. Bu konuda, SSL 'nin nasıl çalıştığı ve Windows Communication Foundation (WCF) ' de nasıl uygulandığı açıklanmaktadır.  
  
## <a name="basic-ssl"></a>Temel SSL  
 SSL 'nin nasıl çalıştığı, bu örnekte bir bankanın web sitesi olan tipik bir senaryo aracılığıyla en iyi şekilde açıklanmıştır. Site bir müşterinin Kullanıcı adı ve parolayla oturum açmasına olanak tanır. Kimlik doğrulaması yapıldıktan sonra, Kullanıcı hesap bakiyelerini görüntüleme, faturaları ödeme ve bir hesaptan diğerine para taşıma gibi işlemleri gerçekleştirebilir.  
  
 Bir kullanıcı siteyi ilk kez ziyaret ettiğinde, SSL mekanizması kullanıcının istemcisiyle (Bu durumda, Internet Explorer) *el sıkışma*olarak adlandırılan bir dizi anlaşmaya başlar. Önce SSL, müşterinin banka sitesinin kimliğini doğrular. Bu önemli bir adımdır çünkü müşterilerin, Kullanıcı adı ve parolasına yazmaya çalışan bir sızma değil, gerçek siteyle iletişim kurdıklarından haberdar olması gerekir. SSL, VeriSign gibi güvenilir bir yetkili tarafından sağlanmış bir SSL sertifikası kullanarak bu kimlik doğrulamasını yapar. Mantık şu şekilde gider: banka sitesinin kimliği için VeriSign voular. Internet Explorer VeriSign güvendiğinden, site güvenilir. VeriSign ile kontrol yapmak istiyorsanız, bunu da VeriSign logosu ' na tıklayarak yapabilirsiniz. Bu, sona erme tarihi ve kim tarafından verildiği (banka sitesi) için bir özgünlük listesi sunar.  
  
 Güvenli bir oturum başlatmak için, istemci bir "Hello" öğesinin eşdeğerini, imzalamak, karmaları oluşturmak ve ile şifrelemek ve şifrelerini çözmek için kullanabileceği bir şifreleme algoritmaları listesiyle birlikte sunucuya gönderir. Yanıt olarak, site bir bildirim ve bir algoritma paketlerinden birinin seçimini geri gönderir. Bu ilk anlaşma sırasında, her iki taraf da nonce alıp alır. *Nonce* , bir karma oluşturmak için sitenin ortak anahtarı ile birlikte kullanılan rastgele oluşturulmuş bir veri parçasıdır. *Karma* , SHA1 gibi standart bir algoritma kullanılarak iki sayıdan türetilmiş yeni bir sayıdır. (İstemci ve site ayrıca hangi karma algoritmanın kullanılacağını kabul etmek için iletiler de değiş tokuş ediyor.) Karma benzersizdir ve iletileri şifrelemek ve şifrelerini çözmek için istemci ile site arasındaki oturum için kullanılır. Hem istemci hem de hizmetin özgün nonce ve sertifikanın ortak anahtarı vardır; bu nedenle her iki taraf da aynı karma değeri oluşturabilir. Bu nedenle, istemci, verileri karmayı hesaplamak için kabul edilen algoritmayı kullanarak (a) hizmet tarafından gönderilen karmayı doğrular ve (b) onu hizmet tarafından gönderilen karmayla karşılaştırır; iki eşleşme varsa, istemci karmaya müdahale yapılmadığını güvence altına aldı. İstemci daha sonra bu karmayı bir anahtar olarak kullanabilir, ancak başka bir yeni karma içeren bir iletiyi şifreleyebilir. Hizmet, karmayı kullanarak iletinin şifresini çözebilir ve bu ikinci-son karmayı kurtarabilir. Birikmiş bilgiler (nonce, ortak anahtar ve diğer veriler) artık her iki taraf tarafından da biliniyor ve bir son karma (veya ana anahtar) oluşturulabilir. Bu son anahtar, bir sonraki son karma kullanılarak şifreli olarak gönderilir. Ana anahtar daha sonra, oturumun geri kalanı için iletileri şifrelemek ve şifrelerini çözmek için kullanılır. Hem istemci hem de hizmet aynı anahtarı kullandığından, buna bir *oturum anahtarı*da denir.  
  
 Oturum anahtarı ayrıca bir simetrik anahtar veya "paylaşılan gizlilik" olarak da belirlenir. Bir simetrik anahtar olması, işlemin her iki tarafında da gereken hesaplamayı azalttığından önemlidir. Her ileti, yeni bir CES ve karma değer alışverişi talep altına alıyorsa, performans, performansı ortadan kaldırmaya başlar. Bu nedenle, SSL 'nin nihai hedefi, iletilerin iki tarafla daha fazla güvenlik ve verimlilik arasında serbestçe akmasını sağlayan bir simetrik anahtar kullanmaktır.  
  
 Protokol siteden siteye değişebildiğinden, önceki açıklama ne olduğunu basitleştirilmiş bir sürümdür. Ayrıca, hem istemci hem de site, el sıkışma sırasında, veri alışverişi sırasında daha fazla karmaşıklık ve bu nedenle koruma eklemek için algorithmically birleştirilmiş olmayan her ikisi de mümkündür.  
  
### <a name="certificates-and-public-key-infrastructure"></a>Sertifikalar ve ortak anahtar altyapısı  
 El sıkışma sırasında hizmet, SSL sertifikasını istemciye de gönderir. Sertifika, son kullanma tarihi, veren yetkilisi ve sitenin Tekdüzen Kaynak tanımlayıcısı (URI) gibi bilgileri içerir. İstemci, bir eşleşme sağlamak için URI 'yi ilk olarak iletişim kuruyordu URI ile karşılaştırır ve ayrıca tarihi ve verme yetkilisini denetler.  
  
 Her sertifika iki anahtara, özel bir anahtara ve ortak anahtara sahiptir ve ikisi de *Exchange anahtar çifti*olarak bilinir. Kısaca, ortak anahtar sertifikadan okunurken özel anahtar yalnızca sertifikanın sahibi olarak bilinir. Her iki anahtar de bir Özet, karma veya başka bir anahtarı şifrelemek veya şifresini çözmek için kullanılabilir, ancak yalnızca tersine işlem olarak. Örneğin, istemci ortak anahtarla şifrelediği takdirde, yalnızca site özel anahtarı kullanarak iletinin şifresini çözebilir. Benzer şekilde, site özel anahtarla şifrelediği takdirde, istemci ortak anahtarla şifresini çözebilir. Bu, yalnızca özel anahtarla şifrelenen iletilerin ortak anahtarla şifresi çözülebildiğinden, istemcinin yalnızca özel anahtarla birlikte alınıp değiştirildiğini istemciye güvence sağlar. Site, ortak anahtar kullanılarak şifrelenmiş bir istemciyle ileti alışverişi olduğundan emin olur. Bu değişim yalnızca bir başlangıç anlaşması için güvenlidir, ancak gerçek simetrik anahtarı oluşturmak için çok daha fazla şey yapılır. Bununla birlikte, tüm iletişimler geçerli bir SSL sertifikasına sahip hizmete bağımlıdır.  
  
## <a name="implementing-ssl-with-wcf"></a>WCF ile SSL uygulama  
 HTTP aktarım güvenliği (veya SSL), WCF 'ye dışarıdan sağlanır. SSL 'yi iki şekilde uygulayabilirsiniz; karar verme faktörü uygulamanızın barındırıldığı bir uygulamadır:  
  
- WCF ana bilgisayarınız olarak Internet Information Services (IIS) kullanıyorsanız, bir SSL hizmeti ayarlamak için IIS altyapısını kullanın.  
  
- Şirket içinde barındırılan bir WCF uygulaması oluşturuyorsanız, HttpCfg. exe aracını kullanarak adrese bir SSL sertifikası bağlayabilirsiniz.  
  
### <a name="using-iis-for-transport-security"></a>Taşıma güvenliği için IIS kullanma  
  
#### <a name="iis-70"></a>IIS 7.0  
 IIS 7,0 ' ü güvenli bir ana bilgisayar (SSL kullanarak) olarak ayarlamak için bkz. [ııs 7,0 ' de güvenli yuva katmanı yapılandırma](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc771438(v=ws.10)).  
  
Sertifikaları IIS 7,0 ile kullanmak üzere yapılandırmak için bkz. [ııs 7,0 ' de sunucu sertifikalarını yapılandırma](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732230(v=ws.10)).  
  
#### <a name="iis-60"></a>IIS 6.0  
 IIS 6,0 ' ü güvenli bir ana bilgisayar (SSL kullanarak) olarak ayarlamak için bkz. [yapılandırma güvenli yuva katmanı](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc736992(v=ws.10)).  
  
 Sertifikaları IIS 6,0 ile kullanmak üzere yapılandırmak için, bkz. [Certificates_IIS_SP1_Ops](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc757474(v=ws.10)).  
  
### <a name="using-httpcfg-for-ssl"></a>SSL için HttpCfg kullanma  

 Kendi kendine barındırılan bir WCF uygulaması oluşturuyorsanız, [Httpcfg. exe](/windows/win32/http/httpcfg-exe) aracını kullanın.
  
 X. 509.952 sertifikasıyla bir bağlantı noktası ayarlamak için HttpCfg. exe aracını kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: SSL sertifikası Ile bağlantı noktası yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Aktarım Güvenliği](../../../../docs/framework/wcf/feature-details/transport-security.md)
- [İleti Güvenliği](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)
