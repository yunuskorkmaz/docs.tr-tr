---
title: Meta Veri Uç Noktalarını Yayımlama
ms.date: 03/30/2017
ms.assetid: 29cd8a60-dfb7-460c-bf5a-c2b31b782671
ms.openlocfilehash: 4c6ac81f0c97415dc21ff3346178dd1e9936b7a5
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319904"
---
# <a name="publishing-metadata-endpoints"></a>Meta Veri Uç Noktalarını Yayımlama
Windows Communication Foundation (WCF) Hizmetleri bir veya daha fazla meta veri uç noktası yayımlayarak meta verileri yayımlar. Yayımlama hizmeti meta verileri, WS-MetadataExchange (MEX) ve HTTP/GET istekleri gibi standartlaştırılmış protokoller kullanılarak meta verilerin kullanılabilmesini sağlar. Meta veri uç noktaları, bir adrese, bağlamaya ve sözleşmeye sahip oldukları diğer hizmet uç noktalarına benzer ve yapılandırma veya kod aracılığıyla bir hizmet ana bilgisayarına eklenebilirler. Meta veri uç noktalarını yayımlamayı etkinleştirmek için, hizmete <xref:System.ServiceModel.Description.ServiceMetadataBehavior> hizmet davranışını eklemeniz gerekir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Nasıl yapılır: Yapılandırma Dosyası Kullanarak Bir Hizmet için Meta Verileri Yayımlama](./feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 İstemcilerin bir WS-MetadataExchange veya bir HTTP/GET isteği kullanarak `?wsdl` sorgu dizesini kullanarak meta verileri alabilmesi için bir WCF hizmetinin meta verileri yayımlaması için nasıl yapılandırılacağını gösterir.  
  
 [Nasıl yapılır: Kod Kullanarak Bir Hizmet için Meta Verileri Yayımlama](./feature-details/how-to-publish-metadata-for-a-service-using-code.md)  
 İstemcilerin bir WS-MetadataExchange veya `?wsdl` sorgu dizesini kullanarak bir HTTP/GET isteği kullanarak meta verileri alabilmesi için, koddaki bir WCF hizmeti için meta veri yayımlamanın nasıl etkinleştirileceğini gösterir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Verileri Yayımlama](./feature-details/publishing-metadata.md)
