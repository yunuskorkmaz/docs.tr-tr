---
description: 'Daha fazla bilgi edinin: özel bir bağlama üzerinden meta veri yayımlama ve alma'
title: Özel Bağlama Üzerinden Meta Veri Yayımlama ve Alma
ms.date: 03/30/2017
ms.assetid: 904e11b4-d90e-45c6-9ee5-c3472c90008c
ms.openlocfilehash: 26532c3478d8250e9f6ec7dbb9431be5052239b4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99644131"
---
# <a name="publishing-and-retrieving-metadata-over-a-custom-binding"></a>Özel Bağlama Üzerinden Meta Veri Yayımlama ve Alma

, <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> Bir hizmete meta veri uç noktası ekleme desteği sağlar. Bu meta veri uç noktaları, bir QueryString içeren bir URL 'de HTTP GET isteklerine yanıt verebilir `?wsdl` ve WS-MetadataExchange (MEX) belirtiminde tanımlanan ISTEKLERI al WS-Transfer. MEX uç noktaları <xref:System.ServiceModel.Description.IMetadataExchange?displayProperty=nameWithType> sözleşmeyi uygular.  
  
## <a name="publishing-metadata-over-a-custom-binding"></a>Özel bağlama üzerinden meta verileri yayımlama  

 HTTP GET meta veri uç noktaları ve HTTPS veri al uç noktaları, <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A?displayProperty=nameWithType> veya <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A?displayProperty=nameWithType> özellikleri olarak ayarlanarak etkinleştirilir `true` . Bu uç noktaların bağlamaları yapılandırılamaz.  
  
 <xref:System.ServiceModel.Description.IMetadataExchange>Ancak, <xref:System.ServiceModel.Description.IMetadataExchange> diğer tüm WINDOWS COMMUNICATION FOUNDATION (WCF) hizmet uç noktası ile aynı olduğundan, sözleşme, Özel Bağlamalar kullananlar dahil olmak üzere herhangi bir uç nokta ile kullanılabilir. Sistem tarafından sağlanmış bir bağlamanın yapılandırmasını nasıl değiştireceğiniz veya uygulamasının nasıl yapılandırılacağını bildiğiniz durumlarda <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> , bir bağlamayı bir uç nokta ile kullanmak üzere yapılandırabilirsiniz <xref:System.ServiceModel.Description.IMetadataExchange> .  
  
## <a name="retrieving-metadata-over-a-custom-binding"></a>Özel bağlama üzerinden meta verileri alma  

 Meta veriler, standart HTTP veya HTTPS GET istekleri kullanılarak HTTP GET ve HTTPS Get meta veri uç noktalarından alınabilir.  
  
 Bir MEX meta veri uç noktasından meta verileri almak için genellikle WCF tarafından desteklenen standart MEX bağlamalarından birini kullanabilirsiniz. Daha fazla bilgi için bkz. <xref:System.ServiceModel.Description.MetadataExchangeBindings?displayProperty=nameWithType>. <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType>Türü ve Svcutil.exe Aracı, belirtilen meta veri uç noktasının adresini temel alarak bu standart MEX bağlamalarından birini otomatik olarak seçer.  
  
 Bir MEX meta veri uç noktası standart MEX bağlamalarından birinin farklı bir bağlamasını kullanıyorsa, using kodu tarafından kullanılan bağlamayı yapılandırabilir <xref:System.ServiceModel.Description.MetadataExchangeClient> veya bir <xref:System.ServiceModel.Description.IMetadataExchange> istemci uç noktası yapılandırması sağlayabilirsiniz. Svcutil.exe Aracı, <xref:System.ServiceModel.Description.IMetadataExchange> meta veri uç noktası ADRESININ URI şeması ile aynı ada sahip bir istemci uç noktası yapılandırması olan yapılandırma dosyasından otomatik olarak yüklenir.  
  
## <a name="security"></a>Güvenlik  

 Özel bir bağlama üzerinden meta veriler yayımlarken, bağlamanın meta verilerinizin gerektirdiği güvenlik desteğini sağladığından emin olun. Örneğin, bilgilerin açığa çıkmasına engel olmak ve istemcinizin meta verileri elde etmek için doğru olduğundan emin olmak için, <xref:System.ServiceModel.Description.IMetadataExchange> uç noktanızı kimlik doğrulama ve şifreleme gerektirecek şekilde yapılandırarak meta verilerinizi ve uygulamanızı daha güvenli hale getirebilirsiniz. Örnek [özel güvenli meta veri uç noktası](../samples/custom-secure-metadata-endpoint.md) bu senaryoyu gösterir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hizmetleri Güvenli Hale Getirme](../securing-services.md)
- [WS-MetadataExchange Bağlamaları](ws-metadataexchange-bindings.md)
- [Nasıl yapılır: Özel Bir WS-Metadata Değişimi Bağlaması Yapılandırma](how-to-configure-a-custom-ws-metadata-exchange-binding.md)
- [Nasıl yapılır: MEX Olmayan Bağlama Üzerinden Meta Verileri Alma](how-to-retrieve-metadata-over-a-non-mex-binding.md)
