---
title: Meta Verileri Yayımlama
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- meatadata [WCF], publishing
ms.assetid: 3a56831a-cabc-45c0-bd02-12e2e9bd7313
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 031a80c52c194f300d7785f05e73eabeebb296b7
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="publishing-metadata"></a>Meta Verileri Yayımlama
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Hizmetleri, bir veya daha fazla meta veri uç noktalarını yayımlayarak meta veri yayımlama. Hizmet meta veri yayımlama meta verileri WS-MetadataExchange (MEX) ve HTTP/GET istekleri gibi standart protokoller kullanılarak kullanılabilir hale getirir. Meta veri uç noktalarını, sahip oldukları bir adresi, bağlama ve bir sözleşme ve hizmet ana bilgisayar yapılandırması veya kesinlik temelli kodu üzerinden için eklenebilir, diğer hizmet uç noktaları benzerdir.  
  
## <a name="publishing-metadata-endpoints"></a>Meta Veri Uç Noktalarını Yayımlama  
 Meta veri uç noktaları için yayımlamak için bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmeti, ilk eklemelisiniz <xref:System.ServiceModel.Description.ServiceMetadataBehavior> hizmet hizmet davranışı. Ekleme bir <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> örneği meta veri uç noktalarını kullanıma sunmak hizmet sağlar. Eklediğiniz sonra <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> hizmet davranışı MEX protokolü destekleyen veya HTTP/GET isteklerine yanıt meta veri uç noktalarını sonra sunabilir.  
  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> Kullanan bir <xref:System.ServiceModel.Description.WsdlExporter> hizmetinizde tüm hizmet uç noktalarına meta verilerini dışa aktarmak için. Meta veri alanından bir hizmet verme hakkında daha fazla bilgi için bkz: [aktarma ve içeri aktarma meta verileri](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md).  
  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> Ekler bir <xref:System.ServiceModel.Description.ServiceMetadataExtension> örneği, hizmet ana bilgisayarı için bir uzantı olarak. <xref:System.ServiceModel.Description.ServiceMetadataExtension?displayProperty=nameWithType> Meta veri protokolleri yayımlama uygulamasını sağlar. Aynı zamanda <xref:System.ServiceModel.Description.ServiceMetadataExtension?displayProperty=nameWithType> erişerek çalışma zamanında hizmetin meta verileri almak için <xref:System.ServiceModel.Description.ServiceMetadataExtension.Metadata%2A?displayProperty=nameWithType> özelliği.  
  
### <a name="mex-metadata-endpoints"></a>MEX meta veri uç noktaları  
 MEX protokolünü kullanan meta veri uç noktalarını eklemek için kullanın, hizmet ana bilgisayarı hizmet uç noktaları ekleme `IMetadataExchange` hizmet sözleşme. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] içeren bir <xref:System.ServiceModel.Description.IMetadataExchange> parçası olarak kullanabileceğiniz bu hizmet sözleşmesi adı arabirimiyle [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] programlama modeli. WS-MetadataExchange uç noktaları veya MEX uç birini kullanabilirsiniz üzerinde statik Fabrika yöntemleri kullanıma dört varsayılan bağlamaları <xref:System.ServiceModel.Description.MetadataExchangeBindings> sınıfı tarafından kullanılan varsayılan bağlamaları eşleşecek şekilde [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Svcutil.exe gibi araçları. Kendi özel bağlama kullanma MEX meta veri uç noktalarını da yapılandırabilirsiniz.  
  
### <a name="http-get-metadata-endpoints"></a>HTTP GET meta veri uç noktaları  
 HTTP/GET isteklerine yanıt hizmetiniz için bir meta veri uç noktası eklemek için ayarlayın <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> özelliği <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> için `true`. Ayarlayarak HTTPS kullanan bir meta veri uç noktası da yapılandırabilirsiniz <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> özelliği <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> için `true`.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Nasıl yapılır: Yapılandırma Dosyası Kullanarak Bir Hizmet için Meta Verileri Yayımlama](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 Nasıl yapılandırılacağını göstermektedir bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemcileri WS-MetadataExchange ya da bir HTTP/GET isteği kullanarak kullanarak meta verilerini alabilmesi meta veri yayımlama için hizmet `?wsdl` sorgu dizesi.  
  
 [Nasıl yapılır: Kod Kullanarak Bir Hizmet için Meta Verileri Yayımlama](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)  
 Meta veri yayımlama için etkinleştirme gösteren bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemcileri WS-MetadataExchange ya da bir HTTP/GET isteği kullanarak kullanarak meta verilerini alabilmesi kod içinde hizmet `?wsdl` sorgu dizesi.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>  
  
 <xref:System.ServiceModel.Description.IMetadataExchange>  
  
 <xref:System.ServiceModel.Description.ServiceMetadataExtension>  
  
 <xref:System.ServiceModel.Description.MetadataExchangeBindings>  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Meta Verileri Dışarı ve İçeri Aktarma](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md)
