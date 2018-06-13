---
title: Meta Veri Uç Noktalarını Yayımlama
ms.date: 03/30/2017
ms.assetid: 29cd8a60-dfb7-460c-bf5a-c2b31b782671
ms.openlocfilehash: 42e0f82ca2c669bbde444cf6aac9ce8f0266f783
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33807085"
---
# <a name="publishing-metadata-endpoints"></a>Meta Veri Uç Noktalarını Yayımlama
Windows Communication Foundation (WCF) hizmetlerini, bir veya daha fazla meta veri uç noktalarını yayımlayarak meta veri yayımlama. Hizmet meta veri yayımlama meta verileri WS-MetadataExchange (MEX) ve HTTP/GET istekleri gibi standart protokoller kullanılarak kullanılabilir hale getirir. Meta veri uç noktalarını bir adresi, bağlama ve bir sözleşme sahip ve bir hizmet ana yapılandırma yoluyla ya da koddaki eklenebilir, diğer hizmet uç noktaları benzerdir. Yayımlama meta veri uç noktalarını etkinleştirmek için eklemelisiniz <xref:System.ServiceModel.Description.ServiceMetadataBehavior> hizmet hizmet davranışı.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Nasıl yapılır: Yapılandırma Dosyası Kullanarak Bir Hizmet için Meta Verileri Yayımlama](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 İstemciler bir WS-MetadataExchange ya da bir HTTP/GET isteği kullanarak kullanarak meta verilerini alabilmesi meta veri yayımlamak için bir WCF hizmeti yapılandırmak gösterilmiştir `?wsdl` sorgu dizesi.  
  
 [Nasıl yapılır: Kod Kullanarak Bir Hizmet için Meta Verileri Yayımlama](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)  
 İstemciler bir WS-MetadataExchange ya da bir HTTP/GET isteği kullanarak kullanarak meta verilerini alabilmesi meta veri yayımlama için kod bir WCF hizmeti etkinleştirmek gösterilmiştir `?wsdl` sorgu dizesi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Meta Verileri Yayımlama](../../../docs/framework/wcf/feature-details/publishing-metadata.md)
