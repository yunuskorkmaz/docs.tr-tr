---
title: Özel Bağlama Üzerinden Meta Veri Yayımlama ve Alma
ms.date: 03/30/2017
ms.assetid: 904e11b4-d90e-45c6-9ee5-c3472c90008c
ms.openlocfilehash: 850f341e933e44d92f130dae90aff5b5c1a882b5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54639555"
---
# <a name="publishing-and-retrieving-metadata-over-a-custom-binding"></a>Özel Bağlama Üzerinden Meta Veri Yayımlama ve Alma
<xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> Meta veri uç noktası için bir hizmet eklemek için destek sağlar. Bu meta veri uç noktalarını bir URL, HTTP GET isteklerine yanıt verebilir bir `?wsdl` querystring ve WS-MetadataExchange (MEX) belirtiminde tanımlanan WS aktarım GET istekleri. MEX uç noktaları uygulayan <xref:System.ServiceModel.Description.IMetadataExchange?displayProperty=nameWithType> sözleşme.  
  
## <a name="publishing-metadata-over-a-custom-binding"></a>Özel bağlama üzerinden meta verileri yayımlama  
 Meta veri uç noktalarını HTTPS GET ve HTTP GET meta veri uç noktalarını ayarlayarak etkinleştirilen <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A?displayProperty=nameWithType> veya <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A?displayProperty=nameWithType> özelliklerine `true`. Bu uç noktalar için olan bağlamaları yapılandırılamaz.  
  
 <xref:System.ServiceModel.Description.IMetadataExchange> Sözleşmesi, ancak kullanılabilir özel bağlamalar kullananlar çünkü dahil olmak üzere, herhangi bir noktayla <xref:System.ServiceModel.Description.IMetadataExchange> uç noktaları için başka bir Windows Communication Foundation (WCF) Hizmeti uç aynıdır. Sistem tarafından sağlanan bir bağlamayı yapılandırmasını değiştirmek nasıl biliyorsanız, veya nasıl yapılandırılacağını bildiğiniz bir <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>, bağlama ile kullanmak için yapılandırabilirsiniz. ardından bir <xref:System.ServiceModel.Description.IMetadataExchange> uç noktası.  
  
## <a name="retrieving-metadata-over-a-custom-binding"></a>Özel bağlama üzerinden meta verileri alma  
 Standart HTTP veya HTTPS GET istekleri kullanarak HTTP Get ve HTTPS Get meta veri uç noktalarından meta verileri alınabilir.  
  
 Bir MEX meta veri uç noktasından meta verilerini almak için genel olarak WCF tarafından desteklenen standart MEX bağlamaları birini kullanabilirsiniz. Daha fazla bilgi için bkz. <xref:System.ServiceModel.Description.MetadataExchangeBindings?displayProperty=nameWithType>. <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> Türünü ve Svcutil.exe aracını otomatik olarak seçin belirtilen meta veri uç noktası adresini temel alan bu standart MEX bağlamaların bir tanesini.  
  
 MEX meta veri uç noktasının standart MEX bağlamaları olandan farklı bir bağlama kullanıyorsa, tarafından kullanılan bağlama yapılandırabileceğiniz <xref:System.ServiceModel.Description.MetadataExchangeClient> göre sağlama veya kod kullanarak bir <xref:System.ServiceModel.Description.IMetadataExchange> istemcisi bitiş noktası yapılandırması. Svcutil.exe aracını, yapılandırma dosyasından otomatik olarak yükleyen bir <xref:System.ServiceModel.Description.IMetadataExchange> URI şeması meta veri uç noktası adresi için aynı ada sahip istemci uç noktası yapılandırması.  
  
## <a name="security"></a>Güvenlik  
 Özel bağlama üzerinden meta veri yayımlama sırasında bağlama gerektirir meta verileriniz güvenlik desteği sağladığını emin olun. Örneğin, istemci meta verilerini almak için sağ sahip olduğundan emin olun ve bilgilerin açığa çıkmasını önlemek için meta verilerinizi ve uygulamanızı daha güvenli yapılandırarak yapabileceğiniz, <xref:System.ServiceModel.Description.IMetadataExchange> uç nokta kimlik doğrulaması ve şifreleme gerektirecek şekilde. Örnek [özel güvenli meta veri uç noktası](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) bu senaryo gösterir.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Hizmetleri Güvenli Hale Getirme](../../../../docs/framework/wcf/securing-services.md)
- [WS-MetadataExchange Bağlamaları](../../../../docs/framework/wcf/extending/ws-metadataexchange-bindings.md)
- [Nasıl yapılır: Yapılandırma özel bir WS-Metadata değişimi bağlaması](../../../../docs/framework/wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md)
- [Nasıl yapılır: Bağlama üzerinden meta verileri bir olmayan - MEX alma](../../../../docs/framework/wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)
