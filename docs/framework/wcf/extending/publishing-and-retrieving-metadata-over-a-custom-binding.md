---
title: Özel Bağlama Üzerinden Meta Veri Yayımlama ve Alma
ms.date: 03/30/2017
ms.assetid: 904e11b4-d90e-45c6-9ee5-c3472c90008c
ms.openlocfilehash: 329daa39a14ed4c839ecbaa6cf9df036ceabee34
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795508"
---
# <a name="publishing-and-retrieving-metadata-over-a-custom-binding"></a>Özel Bağlama Üzerinden Meta Veri Yayımlama ve Alma
, <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> Bir hizmete meta veri uç noktası ekleme desteği sağlar. Bu meta veri uç noktaları, bir `?wsdl` QueryString ve WS-MetadataExchange (MEX) belirtiminde tanımlandığı şekilde ws-Transfer get istekleri olan bir URL 'de http get isteklerine yanıt verebilir. MEX uç noktaları <xref:System.ServiceModel.Description.IMetadataExchange?displayProperty=nameWithType> sözleşmeyi uygular.  
  
## <a name="publishing-metadata-over-a-custom-binding"></a>Özel bağlama üzerinden meta verileri yayımlama  
 HTTP get meta veri uç noktaları ve https veri al uç noktaları, <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A?displayProperty=nameWithType> veya <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A?displayProperty=nameWithType> özellikleri olarak `true`ayarlanarak etkinleştirilir. Bu uç noktaların bağlamaları yapılandırılamaz.  
  
 Ancak, diğer tüm Windows Communication Foundation (WCF) hizmet uç noktası ile aynı olduğundan <xref:System.ServiceModel.Description.IMetadataExchange> , sözleşme,ÖzelBağlamalarkullananlardahilolmaküzereherhangibiruçnoktailekullanılabilir.<xref:System.ServiceModel.Description.IMetadataExchange> Sistem tarafından sağlanmış bir bağlamanın yapılandırmasını nasıl değiştireceğiniz veya uygulamasının nasıl yapılandırılacağını <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>bildiğiniz durumlarda, bir bağlamayı bir <xref:System.ServiceModel.Description.IMetadataExchange> uç nokta ile kullanmak üzere yapılandırabilirsiniz.  
  
## <a name="retrieving-metadata-over-a-custom-binding"></a>Özel bağlama üzerinden meta verileri alma  
 Meta veriler, standart HTTP veya HTTPS GET istekleri kullanılarak HTTP GET ve HTTPS Get meta veri uç noktalarından alınabilir.  
  
 Bir MEX meta veri uç noktasından meta verileri almak için genellikle WCF tarafından desteklenen standart MEX bağlamalarından birini kullanabilirsiniz. Daha fazla bilgi için bkz. <xref:System.ServiceModel.Description.MetadataExchangeBindings?displayProperty=nameWithType>. <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> Type ve Svcutil. exe aracı, belirtilen meta veri uç noktasının adresini temel alarak bu standart MEX bağlamalarından birini otomatik olarak seçer.  
  
 Bir MEX meta veri uç noktası standart MEX bağlamalarından birinin farklı bir bağlamasını kullanıyorsa, <xref:System.ServiceModel.Description.MetadataExchangeClient> using kodu tarafından kullanılan bağlamayı yapılandırabilir veya bir <xref:System.ServiceModel.Description.IMetadataExchange> istemci uç noktası yapılandırması sağlayabilirsiniz. Svcutil. exe aracı, yapılandırma dosyasından, meta veri uç noktası <xref:System.ServiceModel.Description.IMetadataExchange> adresinin URI şeması ile aynı ada sahip bir istemci uç noktası yapılandırması otomatik olarak yüklenir.  
  
## <a name="security"></a>Güvenlik  
 Özel bir bağlama üzerinden meta veriler yayımlarken, bağlamanın meta verilerinizin gerektirdiği güvenlik desteğini sağladığından emin olun. Örneğin, bilgilerin açığa çıkmasına engel olmak ve istemcinizin meta verileri elde etmek için doğru olduğundan emin olmak için, <xref:System.ServiceModel.Description.IMetadataExchange> uç noktanızı kimlik doğrulama ve şifreleme gerektirecek şekilde yapılandırarak meta verilerinizi ve uygulamanızı daha güvenli hale getirebilirsiniz. Örnek [özel güvenli meta veri uç noktası](../samples/custom-secure-metadata-endpoint.md) bu senaryoyu gösterir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hizmetleri Güvenli Hale Getirme](../securing-services.md)
- [WS-MetadataExchange Bağlamaları](ws-metadataexchange-bindings.md)
- [Nasıl yapılır: Özel WS-Metadata Exchange bağlamasını yapılandırma](how-to-configure-a-custom-ws-metadata-exchange-binding.md)
- [Nasıl yapılır: MEX olmayan bağlama üzerinden meta verileri alma](how-to-retrieve-metadata-over-a-non-mex-binding.md)
