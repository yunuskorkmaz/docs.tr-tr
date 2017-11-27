---
title: "Eş Kanalı Uygulamalarını Güvenli Hale Getirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d4a0311d-3f78-4525-9c4b-5c93c4492f28
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 02bad6b5c7460655f4d3a5851e4e74d7de12111f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="securing-peer-channel-applications"></a>Eş Kanalı Uygulamalarını Güvenli Hale Getirme
Gibi diğer bağlamaları altında [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)], `NetPeerTcpBinding` sahip güvenlik varsayılan olarak etkindir ve her ikisi de taşıma ve ileti tabanlı güvenlik (veya) sunar. Bu konuda, bu iki güvenlik türleri açıklanmaktadır. Güvenlik türü bağlama belirtimi güvenlik modu etiketinde belirtilir (<xref:System.ServiceModel.NetPeerTcpBinding.Security%2A>`Mode`).  
  
## <a name="transport-based-security"></a>Aktarım tabanlı güvenlik  
 Eş kanal taşıma, her ikisi de gerektiren ayarını WMI'ya güvenliğini sağlamak için iki tür kimlik doğrulama bilgilerini destekleyen `ClientCredentialSettings.Peer` ilişkili özellikte `ChannelFactory`:  
  
-   Parola. İstemciler bir gizli parolası hakkında bilgi sahibi bağlantılarının kimliğini doğrulamak için kullanır. Bu kimlik bilgisi türü kullanıldığında, `ClientCredentialSettings.Peer.MeshPassword` geçerli bir parola taşımalıdır ve isteğe bağlı olarak bir `X509Certificate2` örneği.  
  
-   Sertifika. Belirli bir uygulama kimlik doğrulaması kullanılır. Bu kimlik bilgisi türü kullanıldığında, somut bir uygulama kullanması gerekir <xref:System.IdentityModel.Selectors.X509CertificateValidator> içinde `ClientCredentialSettings.Peer.PeerAuthentication`.  
  
## <a name="message-based-security"></a>İleti tabanlı güvenlik  
 İleti güvenliği kullanarak, tüm alıcı taraflar tarafından güvenilen bir taraf iletiyi gönderen doğrulayabilir uygulama giden iletiler kaydolabilirsiniz ve ileti olmadığını değiştirilmiş. Şu anda yalnızca X.509 kimlik bilgisi ileti imzalama eş kanalı destekler.  
  
## <a name="best-practices"></a>En İyi Yöntemler  
  
-   Bu bölüm, eş kanalı uygulamalarını güvenli hale getirmek için en iyi uygulamaları açıklar.  
  
### <a name="enable-security-with-peer-channel-applications"></a>Eş kanal uygulamalarla güvenliğini etkinleştir  
 Eş kanal protokoller dağıtılmış yapısı nedeniyle, kafes üyeliği, gizlilik ve güvenli bir kafes gizlilik zorlamak zordur. İstemcileri ve çözümleyicisini arasındaki iletişimin güvenliğini sağlamak önemlidir. Eş Adı Çözümleme Protokolü (PNRP) altında kimlik sahtekarlığı önlemek için güvenli adları ve diğer ortak saldırılara kullanın. Özel çözümleyicisini bağlantı istemcilerin kullandığı her iki ileti ve aktarım tabanlı güvenlik dahil olmak üzere çözümleyici hizmetiyle iletişim güvenliği etkinleştirerek güvenli hale getirin.  
  
### <a name="use-the-strongest-possible-security-model"></a>En güçlü olası güvenlik modelini kullanın  
 Örneğin, her bir üyesi kafes ayrı olarak tanımlanması gerekirse, sertifika tabanlı kimlik doğrulama modeli kullanır. Bu mümkün değilse, aşağıdaki geçerli önerileri parola tabanlı kimlik doğrulaması güvenli tutmak için kullanın. Bu parolalar yalnızca parolaları güvenli bir ortam kullanarak iletmek güvenilen taraflarla parolaları sık değişen ve parolaları güçlü sağlayarak paylaşımı içerir (en az sekiz karakter uzunluğunda, en az bir harf bir rakam, her iki çalışmalarından içerir ve bir özel karakter).  
  
### <a name="never-accept-self-signed-certificates"></a>Hiçbir zaman otomatik olarak imzalanan sertifikalar kabul et  
 Hiçbir zaman konu adlarına göre bir sertifika kimlik bilgileri kabul edin. Herhangi bir sertifika oluşturabilir ve herkesin doğrulama bir ad seçebilirsiniz unutmayın. Kimlik sahtekarlığı olasılığını önlemek için (güvenilir bir veren veya bir kök sertifika yetkilisi) yetkilisi kimlik bilgilerini veren temel alarak sertifikaları doğrulayın.  
  
### <a name="use-message-authentication"></a>İleti kimlik doğrulamasını kullan  
 İleti kimlik doğrulama ileti güvenilir bir kaynaktan geldiğini ve hiç kimse iletiyle iletim sırasında değişiklik yaptığını doğrulamak için kullanın. İleti kimlik doğrulaması aldatma veya kafes iletilerinde değiştirmesine kötü amaçlı bir istemci için kolaydır.  
  
## <a name="peer-channel-code-examples"></a>Eş kanal kod örnekleri  
 [Eş kanal senaryoları](../../../../docs/framework/wcf/feature-details/peer-channel-scenarios.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Eş kanalı güvenliği](../../../../docs/framework/wcf/feature-details/peer-channel-security.md)  
 [Eş kanal uygulaması oluşturma](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
