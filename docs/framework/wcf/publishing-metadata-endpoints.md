---
title: Meta Veri Uç Noktalarını Yayımlama
ms.date: 03/30/2017
ms.assetid: 29cd8a60-dfb7-460c-bf5a-c2b31b782671
ms.openlocfilehash: 6060850b78c890e043dfaf6f242460bc6e0ef627
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="publishing-metadata-endpoints"></a>Meta Veri Uç Noktalarını Yayımlama
Windows Communication Foundation (WCF) hizmetlerini, bir veya daha fazla meta veri uç noktalarını yayımlayarak meta veri yayımlama. Hizmet meta veri yayımlama meta verileri WS-MetadataExchange (MEX) ve HTTP/GET istekleri gibi standart protokoller kullanılarak kullanılabilir hale getirir. Meta veri uç noktalarını bir adresi, bağlama ve bir sözleşme sahip ve bir hizmet ana yapılandırma yoluyla ya da koddaki eklenebilir, diğer hizmet uç noktaları benzerdir. Yayımlama meta veri uç noktalarını etkinleştirmek için eklemelisiniz <xref:System.ServiceModel.Description.ServiceMetadataBehavior> hizmet hizmet davranışı.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Nasıl yapılır: Yapılandırma Dosyası Kullanarak Bir Hizmet için Meta Verileri Yayımlama](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 Nasıl yapılandırılacağını göstermektedir bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] istemcileri WS-MetadataExchange ya da bir HTTP/GET isteği kullanarak kullanarak meta verilerini alabilmesi meta veri yayımlama için hizmet `?wsdl` sorgu dizesi.  
  
 [Nasıl yapılır: Kod Kullanarak Bir Hizmet için Meta Verileri Yayımlama](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)  
 Meta veri yayımlama için etkinleştirme gösteren bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] istemcileri WS-MetadataExchange ya da bir HTTP/GET isteği kullanarak kullanarak meta verilerini alabilmesi kod içinde hizmet `?wsdl` sorgu dizesi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Meta Verileri Yayımlama](../../../docs/framework/wcf/feature-details/publishing-metadata.md)
