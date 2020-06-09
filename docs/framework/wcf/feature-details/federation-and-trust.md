---
title: Federasyon ve Güven
ms.date: 03/30/2017
helpviewer_keywords:
- federation [WCF], and trust
ms.assetid: 4bdec4f2-f8a2-4512-bdcf-14ef54b5877a
ms.openlocfilehash: 8b924a4aeb9c667592e99d65666cd8f048d34c22
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595485"
---
# <a name="federation-and-trust"></a>Federasyon ve Güven
Bu konu, Federasyon uygulamaları, güven sınırları ve yapılandırma ve Windows Communication Foundation (WCF) ' de verilen belirteçlerin kullanımı ile ilgili çeşitli konuları ele almaktadır.  
  
## <a name="services-security-token-services-and-trust"></a>Hizmetler, güvenlik belirteci Hizmetleri ve güven  
 Federasyon uç noktalarını açığa çıkaran hizmetler, genellikle istemcilerin belirli bir veren tarafından sunulan bir belirteci kullanarak kimlik doğrulaması yapmasını bekler. Hizmetin veren için doğru kimlik bilgileriyle yapılandırılması önemlidir; Aksi takdirde, verilen belirteçler üzerinde imzaları doğrulayamayacak ve istemci hizmetle iletişim kuramayacak. Hizmette verenin kimlik bilgilerini yapılandırma hakkında daha fazla bilgi için bkz. [nasıl yapılır: kimlik bilgilerini yapılandırma Federasyon Hizmeti](how-to-configure-credentials-on-a-federation-service.md).  
  
 Benzer şekilde, simetrik anahtarlar kullanılırken anahtarlar hedef hizmet için şifrelenir, bu nedenle güvenlik belirteci hizmetini hedef hizmet için doğru kimlik bilgileriyle yapılandırmanız gerekir; Aksi takdirde, hedef hizmetin anahtarını şifreleyemez ve yeniden, istemci hizmetle iletişim kuramamayacak.  
  
 WCF Hizmetleri, <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxClockSkew%2A> istemci ve hizmet arasında saat çarpıklığı sağlamak Için [SecurityBindingElement](../diagnostics/wmi/securitybindingelement.md) üzerinde özelliğin değerini kullanır. Federasyon ' da, bu `MaxClockSkew` ayar istemcinin verilen belirteci aldığı istemci ve güvenlik belirteci hizmeti arasındaki saat eğillerinin geçerli olması için geçerlidir. Bu nedenle, güvenlik belirteci Hizmetleri, verilen belirtecin etkin ve sona erme zamanlarını ayarlarken saat eğriltmek zorunda kalmaz.  
  
> [!NOTE]
> Saatin eğmesinin önemi, verilen belirtecin kısa ömürlü olduğu kadar artar. Çoğu durumda, belirteç ömrü 30 dakika veya daha fazla olduğunda saat eğriltme önemli bir sorun değildir. Daha kısa ömürleri olan veya belirtecin tam geçerlilik süresinin önemli olduğu senaryolar, saat çarpıklığı alacak şekilde tasarlanmalıdır.  
  
## <a name="federated-endpoints-and-time-outs"></a>Federasyon uç noktaları ve zaman aşımları  
 İstemci federe bir uç noktayla iletişim kurduğunda, önce bir güvenlik belirteci hizmetinden uygun bir belirteç almalıdır. Güvenlik belirteci hizmeti bir Federasyon uç noktası kullanıma sunarsa, istemci öncelikle bu uç nokta için verenin bir belirtecini almalıdır. Her bir belirteç alımı zaman alır ve bu süre, gerçek iletinin son bitiş noktasına gönderilmesi için genel zaman aşımına tabidir.  
  
 Örneğin, istemci tarafı kanaldaki zaman aşımı 30 saniyeye ayarlanır. İletiyi son uç noktaya göndermeden önce belirteçleri almak için iki belirteç veren çağrılmalıdır ve her birinin bir belirteç vermesi 15 saniye sürer. Bu durumda, deneme başarısız olur ve bir oluşturulur <xref:System.TimeoutException> . Bu nedenle, <xref:System.ServiceModel.IContextChannel.OperationTimeout%2A> istemci kanalında değeri, tüm verilen belirteçleri almak için geçen süreyi kapsayacak büyüklükte bir değere ayarlamanız gerekir. Özelliği için bir değer belirtilmediğinde <xref:System.ServiceModel.IContextChannel.OperationTimeout%2A> , <xref:System.ServiceModel.Channels.Binding.OpenTimeout%2A> özelliğin veya <xref:System.ServiceModel.Channels.Binding.SendTimeout%2A> özelliğin (ya da her ikisinin), verilen tüm belirteçleri almak için geçen süreyi kapsayacak büyüklükte bir değere ayarlanması gerekir.  
  
## <a name="token-lifetime-and-renewal"></a>Belirteç ömrü ve yenileme  
 WCF istemcileri bir hizmete ilk istek yaparken verilen belirteci denetlemez.  Bunun yerine, WCF uygun etkin ve sona erme zamanları ile belirteç vermek için güvenlik belirteci hizmetine güvenir. Belirteç istemci tarafından önbelleğe alınmışsa ve yeniden kullanılırsa, belirteç ömrü sonraki isteklere karşı denetlenir ve istemci gerekirse belirteci otomatik olarak yeniler. Belirteç önbelleğe alma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Federasyon Istemcisi oluşturma](how-to-create-a-federated-client.md).  
  
 Verilen belirteçler veya güvenlik bağlamı belirteçleri için 30 saniyelik veya daha az sırada olan kısa yaşam sürelerinin belirtilmesi, verilen belirteçleri veya güvenlik bağlamı belirteçlerini anlaşarak veya yenilemede WCF istemcileri tarafından yapılan anlaşma zaman aşımları veya diğer özel durumlar ile sonuçlanmasına neden olabilir.  
  
## <a name="issued-tokens-and-inclusionmode"></a>Verilen belirteçler ve yani ıonmode  
 Verilen belirtecin istemciden federe uç noktaya gönderilen bir ileti içinde serileştirilip serileştirilmediği veya sınıfın özelliği ayarlanarak denetlenmediği <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.InclusionMode%2A> <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters> . Bu özellik, <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode> sabit listesi değerlerinden birine ayarlanabilir, ancak çoğu Federasyon senaryosunda yararlı değildir. `SecurityTokenInclusionMode.Never`Ve `SecurityTokenInclusionMode.AlwaysToInitiator` değerleri istemcinin bağlı olan tarafa güvenlik belirteci hizmeti tarafından verilen belirtece bir başvuru göndermesini sağlar. Bağlı olan taraf verilen belirtecin bir kopyasına sahip olmadığı için, belirteç başvurusu çözümlenemediği için kimlik doğrulaması başarısız olur. WCF `SecurityTokenInclusionMode.Once` ile eşdeğer olarak davranır `SecurityTokenInclusionMode.AlwaysToRecipient` .  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>
- [Nasıl yapılır: Federe İstemci Oluşturma](how-to-create-a-federated-client.md)
- [Nasıl yapılır: Federe Bir Hizmette Kimlik Bilgilerini Yapılandırma](how-to-configure-credentials-on-a-federation-service.md)
- [Nasıl yapılır: WSFederationHttpBinding Oluşturma](how-to-create-a-wsfederationhttpbinding.md)
