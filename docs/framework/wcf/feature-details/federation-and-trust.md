---
title: Federasyon ve Güven
ms.date: 03/30/2017
helpviewer_keywords:
- federation [WCF], and trust
ms.assetid: 4bdec4f2-f8a2-4512-bdcf-14ef54b5877a
ms.openlocfilehash: 1f0872c9aea11a54860fe3075d2756691590e0d4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54532428"
---
# <a name="federation-and-trust"></a>Federasyon ve Güven
Bu konu, Federasyon uygulamalarına, güven sınırları ve yapılandırma ve verilen belirteçler Windows Communication Foundation (WCF) kullanımı ile ilgili çeşitli yönlerini kapsar.  
  
## <a name="services-security-token-services-and-trust"></a>Hizmetleri, güvenlik belirteci hizmetlerine ve güven  
 İstemcilerin belirli bir veren tarafından sağlanan bir belirteci kullanarak kimlik doğrulaması için Federasyon uç noktaları genellikle açığa çıkaran hizmetler bekler. Hizmet veren için doğru kimlik bilgileriyle yapılandırılmış önemlidir; Aksi takdirde, verilen belirteçler imzaları doğrulamak mümkün olmayacaktır ve istemci hizmetiyle iletişim kuramadı. Verici kimlik bilgileri hizmetini yapılandırma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Federe bir hizmette kimlik bilgilerini yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).  
  
 Hedef hizmet için doğru kimlik bilgileriyle güvenlik belirteci hizmeti yapılandırmak için benzer şekilde, simetrik anahtarlar kullanılırken anahtarları hedef hizmet için şifrelenir; Aksi takdirde, hedef hizmet anahtarı şifrelemek mümkün olmayacaktır ve yeniden istemci hizmetiyle iletişim kurmak mümkün olmayacaktır.  
  
 WCF hizmetleri kullanma değerini <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxClockSkew%2A> özelliği [SecurityBindingElement](../../../../docs/framework/wcf/diagnostics/wmi/securitybindingelement.md) saati istemci ve hizmet arasında eğriltme izin vermek için. Federasyon içinde `MaxClockSkew` ayarı uygulanır saat Eğer hem istemci hem de burada verilen belirteç istemci elde gelen güvenlik belirteci hizmeti arasında. Bu nedenle, güvenlik belirteci hizmetlerine saat eğriltme izinler verilen belirtecin geçerlilik tarihi ve bitiş zamanları ayarlarken yapmamanız.  
  
> [!NOTE]
>  Verilen belirteç ömrünü kısaltır saat eğriltme önemini artar. Belirteç süresini 30 dakika veya daha fazla olduğunda, çoğu durumda, saat eğriltme önemli bir sorun değildir. Daha kısa veya belirtecin tam geçerlilik süresinin önemli olduğu senaryolar saat eğriltme dikkate şekilde tasarlanmalıdır.  
  
## <a name="federated-endpoints-and-time-outs"></a>Federasyon uç noktaları ve zaman aşımları  
 Bir istemci bir Federasyon uç noktası ile iletişim kurduğunda, öncelikle uygun bir güvenlik belirteci hizmeti belirtecinden edinmeniz gerekir. Güvenlik belirteci hizmeti bir Federasyon uç noktası sunarsa, istemci için bu endpoint verenden önce bir belirteç almanız gerekir. Her belirteç edinme işlemi zaman alır ve bu süre, son uç noktaya gerçek ileti göndermek için genel zaman aşımı tabidir.  
  
 Örneğin, istemci tarafı kanalı zaman aşımı süresini 30 saniye olarak ayarlanır. Her bir belirteç vermek üzere 15 saniye sürer ve son uç noktaya iletiyi göndermeden önce belirteçlerini almak için çağrılacak iki belirteç verenler gerekir. Bu durumda, denemesi başarısız olur ve bir <xref:System.TimeoutException> oluşturulur. Bu nedenle, ayarlanacak ihtiyacınız <xref:System.ServiceModel.IContextChannel.OperationTimeout%2A> değeri almak için geçen süre dahil etmek için büyük bir değere istemci kanalındaki tüm verilen belirteçleri. Burada bir değer belirtilmemişse için durumda <xref:System.ServiceModel.IContextChannel.OperationTimeout%2A> özelliği <xref:System.ServiceModel.Channels.Binding.OpenTimeout%2A> özelliği veya <xref:System.ServiceModel.Channels.Binding.SendTimeout%2A> özelliği (veya her ikisi) tüm verilen belirteçleri almak için geçen süre dahil etmek için büyük bir değere ayarlanmış olması gerekir.  
  
## <a name="token-lifetime-and-renewal"></a>Belirteç ömrü ve yenileme  
 WCF istemcileri, hizmet için bir ilk isteği yaparken, verilen belirteç denetlemez.  Bunun yerine, WCF uygun başlangıç ve bitiş zamanları ile bir belirteç vermek için güvenlik belirteci hizmeti güvenir. Belirteç istemci tarafından önbelleğe alınan ve yeniden, belirteç ömrü sonraki isteklerde authenticateasync denetlenir ve istemci otomatik olarak gerekirse belirtecini yeniler. Belirteç önbelleğe alma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Federe istemci oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md).  
  
 Belirteçleri veya güvenlik bağlamı belirteçler veren, anlaşması zaman aşımı veya diğer özel durumlar isteme verilen belirteçler, WCF istemcileri tarafından oluşturulan neden olabilir veya anlaşması veya güvenlik yenileme kısa ömre, 30 saniye bazında ya da daha az belirleme bağlam belirteci.  
  
## <a name="issued-tokens-and-inclusionmode"></a>Verilen belirteçler ve InclusionMode  
 Verilen bir belirteç bir istemciden bir Federasyon uç noktası için gönderilen bir iletinin serileştirildiği veya ayarı denetlenen <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.InclusionMode%2A> özelliği <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters> sınıfı. Bu özellik, birine ayarlanabilir <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode> numaralandırma değerlerinin, ancak en federe senaryolarda yararlı değildir. `SecurityTokenInclusionMode.Never` Ve `SecurityTokenInclusionMode.AlwaysToInitiator` değerler için bağlı olan taraf güvenlik belirteci hizmeti tarafından verilen belirtecin bir başvuru göndermek istemci neden olur. Bağlı olan taraf verilen belirteç kimlik doğrulaması bir kopyasını sahip olduğu sürece, belirteç başvurusu çözümlenebilir olmadığı için başarısız olur. WCF işler `SecurityTokenInclusionMode.Once` eşdeğer olarak `SecurityTokenInclusionMode.AlwaysToRecipient`.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>
- [Nasıl yapılır: Federe istemci oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [Nasıl yapılır: Federe bir hizmette kimlik bilgilerini yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [Nasıl yapılır: WSFederationHttpBinding oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
