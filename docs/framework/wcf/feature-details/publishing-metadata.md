---
title: Meta Verileri Yayımlama
ms.date: 03/30/2017
helpviewer_keywords:
- meatadata [WCF], publishing
ms.assetid: 3a56831a-cabc-45c0-bd02-12e2e9bd7313
ms.openlocfilehash: 97836cef12cd1f220e97d2c38d2dca1b878d7484
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59183091"
---
# <a name="publishing-metadata"></a>Meta Verileri Yayımlama
Windows Communication Foundation (WCF) Hizmetleri, bir veya daha fazla meta veri uç noktalarını yayımlayarak meta verileri yayımlama. Hizmet meta verileri yayımlama meta verileri, WS-MetadataExchange (MEX) ve HTTP/GET istekleri gibi standart protokolleri kullanarak kullanılabilir hale getirir. Meta veri uç noktalarını, adres, bağlama ve bir sözleşme sahip ve bir hizmet ana yapılandırma veya kesinlik temelli kod aracılığıyla eklenebilir, diğer hizmet uç noktaları için benzerdir.  
  
## <a name="publishing-metadata-endpoints"></a>Meta Veri Uç Noktalarını Yayımlama  
 Bir WCF hizmeti için meta veri uç noktalarını yayımlamak için önce eklemelisiniz <xref:System.ServiceModel.Description.ServiceMetadataBehavior> hizmet hizmet davranışı. Ekleme bir <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> örnek meta veri uç noktalarını kullanıma sunmak, hizmeti sağlar. Eklediğiniz sonra <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> hizmet davranışı MEX protokolü destekleyen veya HTTP/GET istekleri için yanıt meta veri uç noktalarını ardından koyabileceğiniz.  
  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> Kullanan bir <xref:System.ServiceModel.Description.WsdlExporter> hizmetinizi tüm hizmet uç noktalarına meta verileri dışarı aktarmak için. Bir hizmet meta verileri dışarı aktarma hakkında daha fazla bilgi için bkz. [aktarma ve içeri aktarma meta verileri](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md).  
  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> Ekler bir <xref:System.ServiceModel.Description.ServiceMetadataExtension> örneği, hizmet ana bilgisayarı için bir genişletme olarak. <xref:System.ServiceModel.Description.ServiceMetadataExtension?displayProperty=nameWithType> Protokolleri yayımlama meta verileri uygulamasını sağlar. Ayrıca <xref:System.ServiceModel.Description.ServiceMetadataExtension?displayProperty=nameWithType> erişerek çalışma zamanında hizmet meta verileri alınacak <xref:System.ServiceModel.Description.ServiceMetadataExtension.Metadata%2A?displayProperty=nameWithType> özelliği.  
  
### <a name="mex-metadata-endpoints"></a>MEX meta veri uç noktaları  
 MEX protokolünü kullanan bir meta veri uç noktalarını eklemek için kullanın, hizmet konağı için hizmet uç noktaları Ekle `IMetadataExchange` hizmet sözleşmesi. WCF içeren bir <xref:System.ServiceModel.Description.IMetadataExchange> arabirimi ile WCF programlama modelinin bir parçası kullanabilirsiniz. Bu hizmet sözleşmesi adı. WS-MetadataExchange uç noktalarına veya MEX uç noktaları, birini kullanabilirsiniz statik Fabrika yöntemleri ortaya dört varsayılan bağlamaları <xref:System.ServiceModel.Description.MetadataExchangeBindings> Svcutil.exe gibi WCF araçları tarafından kullanılan varsayılan bağlamaları eşleştirilecek sınıfı. Ayrıca, kendi özel bağlama kullanma MEX meta veri uç noktalarını yapılandırabilirsiniz.  
  
### <a name="http-get-metadata-endpoints"></a>HTTP GET meta veri uç noktaları  
 HTTP/GET isteklerine yanıt verip hizmetinize bir meta veri uç noktası eklemek için ayarlanmış <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> özelliği <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> için `true`. Ayrıca ayarlayarak HTTPS kullanan bir meta veri uç noktası yapılandırabilirsiniz <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> özelliği <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> için `true`.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Nasıl yapılır: Yapılandırma Dosyası Kullanarak Bir Hizmet için Meta Verileri Yayımlama](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 İstemciler bir WS-MetadataExchange ya da bir HTTP/GET isteği kullanılarak kullanarak meta verileri alabilir. böylece, meta verileri yayımlamak için bir WCF hizmetini yapılandırma gösterilmektedir `?wsdl` sorgu dizesi.  
  
 [Nasıl yapılır: Kod Kullanarak Bir Hizmet için Meta Verileri Yayımlama](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)  
 İstemciler bir WS-MetadataExchange ya da bir HTTP/GET isteği kullanılarak kullanarak meta verileri alabilir. böylece kodda bir WCF hizmeti için meta veri yayımlamayı etkinleştirme gösterilmektedir `?wsdl` sorgu dizesi.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>  
  
 <xref:System.ServiceModel.Description.IMetadataExchange>  
  
 <xref:System.ServiceModel.Description.ServiceMetadataExtension>  
  
 <xref:System.ServiceModel.Description.MetadataExchangeBindings>  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Verileri Dışarı ve İçeri Aktarma](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md)
