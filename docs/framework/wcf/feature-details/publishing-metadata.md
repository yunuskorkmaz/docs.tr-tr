---
title: Meta Verileri Yayımlama
description: WCF hizmetlerinin bir veya daha fazla meta veri uç noktası yayımlayarak meta verileri nasıl yayımlacağınızı öğrenin ve meta verileri standart protokoller kullanılarak kullanılabilir hale getirir
ms.date: 03/30/2017
helpviewer_keywords:
- metadata [WCF], publishing
ms.assetid: 3a56831a-cabc-45c0-bd02-12e2e9bd7313
ms.openlocfilehash: 2aa6d877db4e5b09b4c594e6e87b63fb6c04703b
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244965"
---
# <a name="publishing-metadata"></a>Meta Verileri Yayımlama
Windows Communication Foundation (WCF) Hizmetleri bir veya daha fazla meta veri uç noktası yayımlayarak meta verileri yayımlar. Yayımlama hizmeti meta verileri, WS-MetadataExchange (MEX) ve HTTP/GET istekleri gibi standartlaştırılmış protokoller kullanılarak meta verilerin kullanılabilmesini sağlar. Meta veri uç noktaları, bir adrese, bağlamaya ve sözleşmeye sahip oldukları diğer hizmet uç noktalarına benzer ve yapılandırma veya kesinlik temelli kod aracılığıyla bir hizmet ana bilgisayarına eklenebilirler.  
  
## <a name="publishing-metadata-endpoints"></a>Meta Veri Uç Noktalarını Yayımlama  
 Bir WCF hizmeti için meta veri uç noktalarını yayımlamak için, önce hizmet <xref:System.ServiceModel.Description.ServiceMetadataBehavior> davranışını hizmete eklemeniz gerekir. Örnek eklemek, <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> hizmetinizin meta veri uç noktalarını kullanıma almasına izin verir. <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType>Hizmet davranışını ekledikten sonra, MEX protokolünü destekleyen veya http/get isteklerine yanıt veren meta veri uç noktalarını kullanıma sunabilirsiniz.  
  
 , <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> <xref:System.ServiceModel.Description.WsdlExporter> Hizmetinizdeki tüm hizmet uç noktalarına ait meta verileri dışarı aktarmak için bir kullanır. Bir hizmetten meta verileri dışarı aktarma hakkında daha fazla bilgi için bkz. [meta verileri dışarı ve içeri](exporting-and-importing-metadata.md)aktarma.  
  
 , <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> <xref:System.ServiceModel.Description.ServiceMetadataExtension> Hizmet ana bilgisayarınıza uzantı olarak bir örnek ekler. , <xref:System.ServiceModel.Description.ServiceMetadataExtension?displayProperty=nameWithType> Meta veri yayımlama protokolleri için uygulama sağlar. Ayrıca, <xref:System.ServiceModel.Description.ServiceMetadataExtension?displayProperty=nameWithType> özelliğine erişerek hizmetin meta verilerini çalışma zamanında almak için öğesini de kullanabilirsiniz <xref:System.ServiceModel.Description.ServiceMetadataExtension.Metadata%2A?displayProperty=nameWithType> .  
  
### <a name="mex-metadata-endpoints"></a>MEX meta veri uç noktaları  
 MEX protokolünü kullanan meta veri uç noktaları eklemek için hizmet sözleşmesini kullanan hizmet ana bilgisayarınıza hizmet uç noktaları ekleyin `IMetadataExchange` . WCF <xref:System.ServiceModel.Description.IMetadataExchange> , WCF programlama modelinin bir parçası olarak kullanabileceğiniz bu hizmet sözleşmesi adına sahip bir arabirim içerir. WS-MetadataExchange uç noktaları veya MEX uç noktaları, statik fabrika yöntemlerinin, <xref:System.ServiceModel.Description.MetadataExchangeBindings> Svcutil.exe gıbı WCF araçları tarafından kullanılan varsayılan bağlamaları eşleştirmek için sınıfında kullanıma sunabileceğiniz dört varsayılan bağlamalardan birini kullanabilir. Ayrıca, kendi özel bağlamalarınızı kullanarak MEX meta veri uç noktalarını yapılandırabilirsiniz.  
  
### <a name="http-get-metadata-endpoints"></a>HTTP GET meta veri uç noktaları  
 HTTP/GET isteklerine yanıt veren hizmetinize bir meta veri uç noktası eklemek için, <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> özelliğini <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> olarak ayarlayın `true` . Ayrıca <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> , üzerinde özelliğini olarak AYARLAYARAK https kullanan bir meta veri uç noktası da yapılandırabilirsiniz <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> `true` .  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Nasıl yapılır: Yapılandırma Dosyası Kullanarak Bir Hizmet için Meta Verileri Yayımlama](how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 İstemcilerin bir WS-MetadataExchange veya sorgu dizesini kullanarak bir HTTP/GET isteği kullanarak meta verileri alabilmesi için meta verileri yayımlamak üzere bir WCF hizmetinin nasıl yapılandırılacağını gösterir `?wsdl` .  
  
 [Nasıl yapılır: Kod Kullanarak Bir Hizmet için Meta Verileri Yayımlama](how-to-publish-metadata-for-a-service-using-code.md)  
 İstemcilerin bir WS-MetadataExchange veya sorgu dizesini kullanarak bir HTTP/GET isteği kullanarak meta verileri alabilmesi için, koddaki bir WCF hizmeti için meta veri yayımlamanın nasıl etkinleştirileceğini gösterir `?wsdl` .  
  
## <a name="reference"></a>Başvuru  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>  
  
 <xref:System.ServiceModel.Description.IMetadataExchange>  
  
 <xref:System.ServiceModel.Description.ServiceMetadataExtension>  
  
 <xref:System.ServiceModel.Description.MetadataExchangeBindings>  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Verileri Dışarı ve İçeri Aktarma](exporting-and-importing-metadata.md)
