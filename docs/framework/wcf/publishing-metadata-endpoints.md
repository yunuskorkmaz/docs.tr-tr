---
title: Meta Veri Uç Noktalarını Yayımlama
ms.date: 03/30/2017
ms.assetid: 29cd8a60-dfb7-460c-bf5a-c2b31b782671
ms.openlocfilehash: 5be27a72c87d95e36a5b283e7930ba0a5191a5a1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96249767"
---
# <a name="publishing-metadata-endpoints"></a>Meta Veri Uç Noktalarını Yayımlama

Windows Communication Foundation (WCF) Hizmetleri bir veya daha fazla meta veri uç noktası yayımlayarak meta verileri yayımlar. Yayımlama hizmeti meta verileri, WS-MetadataExchange (MEX) ve HTTP/GET istekleri gibi standartlaştırılmış protokoller kullanılarak meta verilerin kullanılabilmesini sağlar. Meta veri uç noktaları, bir adrese, bağlamaya ve sözleşmeye sahip oldukları diğer hizmet uç noktalarına benzer ve yapılandırma veya kod aracılığıyla bir hizmet ana bilgisayarına eklenebilirler. Meta veri uç noktalarını yayımlamayı etkinleştirmek için hizmet <xref:System.ServiceModel.Description.ServiceMetadataBehavior> davranışını hizmete eklemeniz gerekir.  
  
## <a name="in-this-section"></a>Bu Bölümde  

 [Nasıl yapılır: Yapılandırma Dosyası Kullanarak Bir Hizmet için Meta Verileri Yayımlama](./feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 İstemcilerin, sorgu dizesini kullanarak bir WS-MetadataExchange veya HTTP/GET isteği kullanarak meta verileri alabilmesi için meta verileri yayınlamak üzere bir WCF hizmetinin nasıl yapılandırılacağını gösterir `?wsdl` .  
  
 [Nasıl yapılır: Kod Kullanarak Bir Hizmet için Meta Verileri Yayımlama](./feature-details/how-to-publish-metadata-for-a-service-using-code.md)  
 İstemcilerin bir WS-MetadataExchange veya sorgu dizesini kullanarak bir HTTP/GET isteği kullanarak meta verileri alabilmesi için kodda bir WCF hizmeti için meta veri yayımlamanın nasıl etkinleştirileceğini gösterir `?wsdl` .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Verileri Yayımlama](./feature-details/publishing-metadata.md)
