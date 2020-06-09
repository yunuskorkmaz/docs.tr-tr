---
title: Eş Kanalı Uygulamalarını Güvenli Hale Getirme
ms.date: 03/30/2017
ms.assetid: d4a0311d-3f78-4525-9c4b-5c93c4492f28
ms.openlocfilehash: a77449710e9093bc8ea2d5446e6359c26a3d1c1e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84589883"
---
# <a name="securing-peer-channel-applications"></a>Eş Kanalı Uygulamalarını Güvenli Hale Getirme
WinFX 'in altındaki diğer bağlamalar gibi, `NetPeerTcpBinding` Varsayılan olarak güvenlik etkinleştirilmiştir ve hem aktarım hem de ileti tabanlı güvenlik (veya her ikisi de) sağlar. Bu konu, bu iki güvenlik türünü açıklamaktadır. Güvenlik türü, bağlama belirtiminde () güvenlik modu etiketiyle belirtilir <xref:System.ServiceModel.NetPeerTcpBinding.Security%2A> `Mode` .  
  
## <a name="transport-based-security"></a>Aktarım tabanlı güvenlik  
 Eş kanal, aktarım güvenliğini sağlamak için iki tür kimlik doğrulama kimlik bilgisini destekler, her ikisi de `ClientCredentialSettings.Peer` ilişkili özelliği ayarlamayı gerektirir `ChannelFactory` :  
  
- Parolayı. İstemciler, bağlantıların kimliğini doğrulamak için gizli bir parola bilgisi kullanır. Bu kimlik bilgisi türü kullanıldığında, `ClientCredentialSettings.Peer.MeshPassword` geçerli bir parola ve isteğe bağlı olarak bir örnek taşıması gerekir `X509Certificate2` .  
  
- Sertifika. Belirli uygulama kimlik doğrulaması kullanılır. Bu kimlik bilgisi türü kullanıldığında, içinde somut bir uygulama kullanmanız gerekir <xref:System.IdentityModel.Selectors.X509CertificateValidator> `ClientCredentialSettings.Peer.PeerAuthentication` .  
  
## <a name="message-based-security"></a>İleti tabanlı güvenlik  
 İleti güvenliğini kullanarak, bir uygulama giden iletileri imzalayabilir ve böylece tüm alıcı taraflar iletinin güvenilen bir taraf tarafından gönderildiğini ve iletinin kurcalanmadığını doğrulayabilirler. Şu anda, eş kanal yalnızca X. 509.440 kimlik bilgisi ileti imzasını destekler.  
  
## <a name="best-practices"></a>En İyi Uygulamalar  
  
- Bu bölümde, eş kanal uygulamalarının güvenliğini sağlamaya yönelik en iyi yöntemler açıklanmaktadır.  
  
### <a name="enable-security-with-peer-channel-applications"></a>Eş kanal uygulamalarıyla güvenliği etkinleştirme  
 Eş kanal protokollerinin dağıtılmış doğası nedeniyle, güvenli olmayan bir kafeste ağ üyeliğini, gizliliği ve gizliliği zorlamak zordur. İstemciler ve çözümleyici Hizmeti arasındaki iletişimin güvenliğini sağlamak için de önemlidir. Eş adı çözümleme Protokolü (PNRP) altında, kimlik sahtekarlığı ve diğer yaygın saldırıları önlemek için güvenli adlar kullanın. İstemci, hem ileti hem de aktarım tabanlı güvenlik dahil olmak üzere çözümleyici hizmetiyle iletişim kurmak için kullandığı bağlantının güvenliğini etkinleştirerek özel bir çözümleyici hizmetini güvenli hale getirin.  
  
### <a name="use-the-strongest-possible-security-model"></a>Olası en güçlü güvenlik modelini kullanın  
 Örneğin, her bir ağ üyesinin ayrı ayrı tanımlanması gerekiyorsa sertifika tabanlı kimlik doğrulama modeli kullanın. Bu mümkün değilse, geçerli önerilerden sonra parola tabanlı kimlik doğrulaması kullanarak bunları güvende tutun. Bu, parolaların yalnızca güvenilir taraflara paylaşılması, güvenli bir ortam kullanarak parola iletme, parolaları sıklıkla değiştirme ve parolaların güçlü olmasını sağlama (en az sekiz karakter uzunluğunda olmak üzere, her iki durumda da, bir rakam ve özel karakter içeren en az bir harf içermelidir) içerir.  
  
### <a name="never-accept-self-signed-certificates"></a>Otomatik olarak Imzalanan sertifikaları kabul etme  
 Konu adlarını temel alan sertifika kimlik bilgilerini hiçbir şekilde kabul etmez. Herkesin bir sertifika oluşturmadığını ve herkesin doğruladığını bir ad seçebileceğini unutmayın. Sızdırma olasılığını önlemek için, sertifika verme yetkilisi kimlik bilgilerine (güvenilir veren veya kök sertifika yetkilisi) göre sertifikaları doğrulayın.  
  
### <a name="use-message-authentication"></a>Ileti kimlik doğrulamasını kullan  
 İletinin güvenilen bir kaynaktan geldiğini ve iletim sırasında iletiyi hiç kimse kurmadığını doğrulamak için ileti kimlik doğrulamasını kullanın. İleti kimlik doğrulaması olmadan, kötü amaçlı bir istemcinin kafesdeki iletilerle sızması veya sızması oldukça kolaydır.  
  
## <a name="peer-channel-code-examples"></a>Eş kanal kodu örnekleri  
 [Eş Kanal Senaryoları](peer-channel-scenarios.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Eş Kanalı Güvenliği](peer-channel-security.md)
- [Eş Kanal Uygulaması Oluşturma](building-a-peer-channel-application.md)
