---
title: Federasyon ve Güven
ms.date: 03/30/2017
helpviewer_keywords:
- federation [WCF], and trust
ms.assetid: 4bdec4f2-f8a2-4512-bdcf-14ef54b5877a
ms.openlocfilehash: fc6a14ed825fa447e80a8389684d10ed07a00815
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="federation-and-trust"></a>Federasyon ve Güven
Bu konu, Federasyon uygulamalarına, güven sınırları ve yapılandırma ve verilen belirteçleri Windows Communication Foundation (WCF) kullanımıyla ilgili çeşitli konuları kapsar.  
  
## <a name="services-security-token-services-and-trust"></a>Hizmetleri, güvenlik belirteci Hizmetleri ve güven  
 Federasyon uç noktaları genellikle kullanıma Hizmetleri istemcilerin belirli bir gönderici tarafından sağlanan bir belirteci kullanarak kimlik doğrulaması için bekler. Hizmet veren için doğru kimlik bilgileri ile yapılandırılan önemlidir; Aksi takdirde verilen belirteçler imzaları doğrulamak mümkün olmaz ve istemci hizmeti ile iletişim kuramayacaktır. Verici kimlik bilgileri hizmetini yapılandırma hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir Federasyon Hizmeti kimlik bilgilerini yapılandırmak](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).  
  
 Hedef hizmet için doğru kimlik bilgileriyle güvenlik belirteci hizmeti yapılandırmak için benzer şekilde, simetrik anahtarlar kullanırken, anahtarları hedef hizmet için şifrelenir; Aksi takdirde, hedef hizmet için anahtarı şifrelemek mümkün olmayacaktır ve yeniden istemci hizmeti ile iletişim kuramayacaktır.  
  
 WCF hizmetleri değerini kullanması <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxClockSkew%2A> özelliği [SecurityBindingElement](../../../../docs/framework/wcf/diagnostics/wmi/securitybindingelement.md) saati istemci ile hizmet arasında eğme izin vermek için. Federasyon içinde `MaxClockSkew` ayarı uygulanır saati Eğer hem istemci hem de istemci burada verilen belirteç elde gelen güvenlik belirteci hizmeti arasında. Bu nedenle, güvenlik belirteci Hizmetleri saat eğriltme kesintileri verilen belirtecin geçerlilik tarihi ve bitiş zamanları ayarlarken yapmamanız.  
  
> [!NOTE]
>  Verilen belirteç ömrü kısaltır saat eğriltme önemini artar. Belirteç ömrü 30 dakika veya daha fazla olduğunda, çoğu durumda, saat eğriltme önemli bir sorun değildir. Daha kısa yaşam süresi veya belirteç tam geçerlilik süresini önemli olduğu senaryolar saat eğriltme dikkate tasarlanmalıdır.  
  
## <a name="federated-endpoints-and-time-outs"></a>Federasyon uç noktaları ve zaman aşımları  
 Bir istemci federe bir uç noktasıyla iletişim kurduğunda, öncelikle bir güvenlik belirteci hizmeti uygun bir belirtecinden edinmeniz gerekir. Güvenlik belirteci hizmeti federe bir uç noktasını kullanıma sunar, istemci o uç noktası için verenden önce bir belirteç edinmeniz gerekir. Her belirteç edinme zaman alır ve son uç noktasına gerçek iletisi göndermek için genel zaman aşımı saat tabidir.  
  
 Örneğin, istemci tarafı kanal zaman aşımı süresini 30 saniye olarak ayarlanır. Her bir belirteç vermek üzere 15 saniye sürer ve iki belirteci verenler son uç noktasına iletiyi göndermeden önce belirteçleri almak için çağrılması gerekir. Bu durumda, denemesi başarısız olur ve bir <xref:System.TimeoutException> oluşturulur. Bu nedenle, ayarlamanız gerekir <xref:System.ServiceModel.IContextChannel.OperationTimeout%2A> değer almak için geçen süre dahil etmek için büyük bir değere istemci kanalındaki tüm verilen belirteçleri. Burada bir değer belirtilmemişse için durumda <xref:System.ServiceModel.IContextChannel.OperationTimeout%2A> özelliği, <xref:System.ServiceModel.Channels.Binding.OpenTimeout%2A> özelliği veya <xref:System.ServiceModel.Channels.Binding.SendTimeout%2A> özelliği (veya her ikisi de) tüm verilen belirteçleri almak için geçen süre dahil etmek için büyük bir değere ayarlanması gerekir.  
  
## <a name="token-lifetime-and-renewal"></a>Belirteç ömrü ve yenileme  
 WCF istemcileri, bir hizmete ilk isteği yaparken, verilen belirteç denetlemez.  Bunun yerine, WCF uygun geçerlilik tarihi ve bitiş zamanları ile bir belirteç vermek için güvenlik belirteci hizmeti güvenir. Belirteç istemci tarafından önbelleğe alınmış ve yeniden, belirteç ömrü sonraki isteklerde denetlenir ve istemci otomatik olarak gerekirse belirteci yeniler. Belirteç önbelleğe alma hakkında daha fazla bilgi için bkz: [nasıl yapılır: federe istemci oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md).  
  
 Verilen belirteçleri veya güvenlik bağlamı belirteçleri, anlaşma zaman aşımlarını veya belirteçlerin verildiği isteyen WCF istemcileri tarafından oluşturulan diğer özel durumlar neden veya anlaşması veya güvenlik yenilenirken terabayt 30 saniye veya daha az kısa yaşam süresi belirtme bağlam belirteçleri.  
  
## <a name="issued-tokens-and-inclusionmode"></a>Verilen belirteçler ve InclusionMode  
 Verilen bir belirteç federe bir uç noktası için bir istemciden gönderilen bir ileti serileştirilmiş veya ayarlayarak denetlenmeyen <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.InclusionMode%2A> özelliği <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters> sınıfı. Bu özellik, birine ayarlanabilir <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode> numaralandırma değerlerinin, ancak en federe senaryolarda yararlı değildir. `SecurityTokenInclusionMode.Never` Ve `SecurityTokenInclusionMode.AlwaysToInitiator` değerler bağlı olan taraf için güvenlik belirteci hizmeti tarafından verilen belirteç başvuru göndermek istemci neden olur. Bağlı olan taraf verilen belirteç, kimlik doğrulama kopyasını sahip olduğu sürece, belirteç başvurusu çözümlenebilir olmadığı için başarısız olur. WCF değerlendirir `SecurityTokenInclusionMode.Once` eşdeğer olarak `SecurityTokenInclusionMode.AlwaysToRecipient`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>  
 [Nasıl yapılır: Federe İstemci Oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [Nasıl yapılır: Federe Bir Hizmette Kimlik Bilgilerini Yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)  
 [Nasıl yapılır: WSFederationHttpBinding Oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
