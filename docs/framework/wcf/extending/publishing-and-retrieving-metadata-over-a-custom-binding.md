---
title: "Özel Bağlama Üzerinden Meta Veri Yayımlama ve Alma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 904e11b4-d90e-45c6-9ee5-c3472c90008c
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4f66821f38e8915ee93cf5b1b77dd75e32662121
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="publishing-and-retrieving-metadata-over-a-custom-binding"></a>Özel Bağlama Üzerinden Meta Veri Yayımlama ve Alma
<xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> Bir hizmet için meta veri uç noktası eklemek için destek sağlar. Bu meta veri uç noktalarını bir URL HTTP GET isteklerine yanıt vermesini sağlayabilirsiniz bir `?wsdl` querystring ve WS-MetadataExchange (MEX) belirtiminde tanımlanan WS aktarma GET istekleri. MEX uç noktaları uygulamak <xref:System.ServiceModel.Description.IMetadataExchange?displayProperty=nameWithType> sözleşme.  
  
## <a name="publishing-metadata-over-a-custom-binding"></a>Özel bağlama üzerinden meta verileri yayımlama  
 Meta veri uç noktalarını alma HTTPS ve HTTP GET meta veri uç noktaları ayarlanarak etkinleştirilir <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A?displayProperty=nameWithType> veya <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A?displayProperty=nameWithType> özelliklerine `true`. Bu uç noktalar için olan bağlamaları yapılandırılamaz.  
  
 <xref:System.ServiceModel.Description.IMetadataExchange> Sözleşme, ancak kullanılabilir özel bağlamalar kullanan çünkü dahil olmak üzere herhangi bir uç nokta ile <xref:System.ServiceModel.Description.IMetadataExchange> noktalarıdır diğer aynı [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Hizmeti uç noktası. Sistem tarafından sağlanan bir bağlamayı yapılandırmasını değiştirmek nasıl bilmiyorsanız veya nasıl yapılandırılacağı bildiğiniz bir <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>, bağlama ile kullanmak için yapılandırabilirsiniz sonra bir <xref:System.ServiceModel.Description.IMetadataExchange> uç noktası.  
  
## <a name="retrieving-metadata-over-a-custom-binding"></a>Özel bağlama üzerinden meta verileri alma  
 Standart HTTP veya HTTPS GET isteklerini kullanarak HTTP Get hem de HTTPS alma meta veri uç noktalarından meta verileri alınabilir.  
  
 MEX meta veri uç noktasından meta verilerini almak için genellikle tarafından desteklenen standart MEX bağlamaları birini kullanabilirsiniz [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] <xref:System.ServiceModel.Description.MetadataExchangeBindings?displayProperty=nameWithType>. <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> Türü ve Svcutil.exe Aracı'nı otomatik olarak aşağıdakilerden birini seçin belirtilen meta veri uç noktasının adresini temel alan bu standart MEX bağlar.  
  
 MEX meta veri uç noktasının standart MEX bağlamaları olandan farklı bir bağlama kullanıyorsa, bağlama tarafından kullanılan yapılandırabilirsiniz <xref:System.ServiceModel.Description.MetadataExchangeClient> kod kullanarak veya göre sağlayan bir <xref:System.ServiceModel.Description.IMetadataExchange> istemci uç nokta yapılandırması. Svcutil.exe Aracı'nı otomatik olarak yükler, yapılandırma dosyasından bir <xref:System.ServiceModel.Description.IMetadataExchange> URI düzeni meta veri uç noktası adresi için aynı ada sahip istemci uç nokta yapılandırması.  
  
## <a name="security"></a>Güvenlik  
 Özel bağlama üzerinden meta veri yayımlama sırasında bağlama meta verileriniz gerektiren güvenlik desteği sağladığından emin olun. Örneğin, istemci meta verileri elde hakkına sahip olduğundan emin olun ve bilgilerin açığa çıkmasını önlemek için meta verilerinizin ve uygulamanızı daha güvenli yapılandırarak yapabilirsiniz, <xref:System.ServiceModel.Description.IMetadataExchange> kimlik doğrulama ve şifreleme gerektirecek şekilde uç noktası. Örnek [özel güvenli meta veri uç noktasının](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) bu senaryo gösterir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hizmetleri güvenli hale getirme](../../../../docs/framework/wcf/securing-services.md)  
 [WS-MetadataExchange bağlamaları](../../../../docs/framework/wcf/extending/ws-metadataexchange-bindings.md)  
 [Nasıl yapılır: yapılandırma özel bir WS-Metadata değişimi bağlaması](../../../../docs/framework/wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md)  
 [Nasıl yapılır: meta verileri üzerinden alma bir MEX olmayan bağlama](../../../../docs/framework/wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)
