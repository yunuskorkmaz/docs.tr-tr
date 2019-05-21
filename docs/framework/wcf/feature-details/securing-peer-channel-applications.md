---
title: Eş Kanalı Uygulamalarını Güvenli Hale Getirme
ms.date: 03/30/2017
ms.assetid: d4a0311d-3f78-4525-9c4b-5c93c4492f28
ms.openlocfilehash: 4b52e0476ce6ac54a2e4a3a8cfceb112d662186b
ms.sourcegitcommit: ffd7dd79468a81bbb0d6449f6d65513e050c04c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2019
ms.locfileid: "65959880"
---
# <a name="securing-peer-channel-applications"></a>Eş Kanalı Uygulamalarını Güvenli Hale Getirme
Gibi diğer bağlamalar WinFX altında `NetPeerTcpBinding` güvenlik varsayılan olarak etkin olan ve her ikisi de taşıma ve ileti tabanlı güvenlik (veya) sunar. Bu konuda, bu iki tür güvenlik anlatılmaktadır. Bağlama belirtimi güvenlik modu etiketinde tarafından belirtilen güvenlik türünü (<xref:System.ServiceModel.NetPeerTcpBinding.Security%2A>`Mode`).  
  
## <a name="transport-based-security"></a>Aktarım tabanlı güvenlik  
 Eş kanal taşıma, ikisi de ayarını WMI'ya gerektiren güvenliğini sağlamak için iki tür kimlik doğrulama bilgilerini destekler `ClientCredentialSettings.Peer` özelliği ilişkili `ChannelFactory`:  
  
- Parola. İstemciler, bağlantıların kimliğini doğrulamak için gizli bir parola bilgisini kullanır. Bu kimlik bilgisi türü kullanıldığında `ClientCredentialSettings.Peer.MeshPassword` geçerli bir parola taşımalıdır ve isteğe bağlı olarak bir `X509Certificate2` örneği.  
  
- Sertifika. Belirli uygulama kimlik doğrulaması kullanılır. Bu kimlik bilgisi türü kullanıldığında, somut bir uygulama kullanmalısınız <xref:System.IdentityModel.Selectors.X509CertificateValidator> içinde `ClientCredentialSettings.Peer.PeerAuthentication`.  
  
## <a name="message-based-security"></a>İleti tabanlı güvenlik  
 İleti güveliği kullanarak, böylece tüm alıcı taraf tarafından güvenilen bir taraf gönderilen ileti doğrulayabilirsiniz giden iletiler uygulamada oturum ve ileti olmadığını değiştirilmiş. Şu anda yalnızca X.509 kimlik bilgisi ileti imzalama eş kanalı destekler.  
  
## <a name="best-practices"></a>En İyi Yöntemler  
  
- Bu bölümde, eş kanalı uygulamalarını güvenli hale getirmek için en iyi uygulamalar ele alınmaktadır.  
  
### <a name="enable-security-with-peer-channel-applications"></a>Eş kanalı uygulamalarını ile güvenliği etkinleştirme  
 Eş kanal protokoller dağıtılmış doğası nedeniyle kafes üyelik, gizlilik ve güvenli olmayan bir ağ gizlilik zorlamak güçtür. İstemcilerle çözümleyicisini arasındaki iletişimin güvenliğini sağlamak unutmamak önemlidir. Eş Adı Çözümleme Protokolü (PNRP) altında kimlik sahtekarlığı önlemek için güvenli adları ve diğer yaygın saldırılardan kullanın. Bir özel Çözücü hizmet bağlantısı istemcilerin kullandığı her iki ileti ve aktarım tabanlı güvenlik dahil olmak üzere çözümleyici hizmetiyle bağlantı güvenliği etkinleştirerek güvenli hale getirin.  
  
### <a name="use-the-strongest-possible-security-model"></a>En güçlü olası bir güvenlik modeli kullanır  
 Kafes her üyesi ayrı ayrı tanımlanması gerekir, örneğin, sertifika tabanlı kimlik doğrulama modeli kullanın. Bu mümkün değilse, bunları güvenli tutmak için parola tabanlı kimlik doğrulaması aşağıdaki geçerli önerileri kullanın. Bu parola yalnızca güvenilir kişilere güvenli bir ortam kullanarak parolaları iletmesini durdurabilirsiniz, parolaları sık değişen ve parolaları güçlü olmalarını sağlamaya paylaşım içerir (en az sekiz karakter uzunluğunda olmalı, her iki durumda da bir rakam, en az bir harf içerir ve özel karakter).  
  
### <a name="never-accept-self-signed-certificates"></a>Hiçbir zaman otomatik olarak imzalanan sertifikaları kabul et  
 Hiçbir zaman bir sertifika konu adlarına göre kimlik bilgilerini kabul edin. Herhangi bir sertifika oluşturabilir ve herkesin doğrulamakta olduğunuz bir ad seçin unutmayın. Kimlik sahtekarlığı olasılığını önlemek için veren yetkili kimlik bilgileri (güvenilir verene veya bir kök sertifika yetkilisi) üzerinde temel alarak sertifikaları doğrulayın.  
  
### <a name="use-message-authentication"></a>İleti kimlik doğrulaması kullan  
 İleti kimlik doğrulaması, bir ileti güvenilir bir kaynaktan geldiğini ve hiç ileti aktarım sırasında değişiklik yapmadığından doğrulamak için kullanın. İleti kimlik doğrulaması olmadan, sızmasını veya kafes iletilerinde değiştirmesine kötü amaçlı bir istemci için kolaydır.  
  
## <a name="peer-channel-code-examples"></a>Eş kanal kod örnekleri  
 [Eş Kanal Senaryoları](../../../../docs/framework/wcf/feature-details/peer-channel-scenarios.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Eş Kanalı Güvenliği](../../../../docs/framework/wcf/feature-details/peer-channel-security.md)
- [Eş Kanal Uygulaması Oluşturma](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
