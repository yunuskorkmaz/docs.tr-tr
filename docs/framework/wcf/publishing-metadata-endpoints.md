---
description: 'Hakkında daha fazla bilgi edinin: meta veri uç noktaları yayımlama'
title: Meta Veri Uç Noktalarını Yayımlama
ms.date: 03/30/2017
ms.assetid: 29cd8a60-dfb7-460c-bf5a-c2b31b782671
ms.openlocfilehash: 8204a62413e09c0fbc6effaae1fd752aee397147
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99726682"
---
# <a name="publishing-metadata-endpoints"></a><span data-ttu-id="ad7d2-103">Meta Veri Uç Noktalarını Yayımlama</span><span class="sxs-lookup"><span data-stu-id="ad7d2-103">Publishing Metadata Endpoints</span></span>

<span data-ttu-id="ad7d2-104">Windows Communication Foundation (WCF) Hizmetleri bir veya daha fazla meta veri uç noktası yayımlayarak meta verileri yayımlar.</span><span class="sxs-lookup"><span data-stu-id="ad7d2-104">Windows Communication Foundation (WCF) services publish metadata by publishing one or more metadata endpoints.</span></span> <span data-ttu-id="ad7d2-105">Yayımlama hizmeti meta verileri, WS-MetadataExchange (MEX) ve HTTP/GET istekleri gibi standartlaştırılmış protokoller kullanılarak meta verilerin kullanılabilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="ad7d2-105">Publishing service metadata makes the metadata available using standardized protocols, such as WS-MetadataExchange (MEX) and HTTP/GET requests.</span></span> <span data-ttu-id="ad7d2-106">Meta veri uç noktaları, bir adrese, bağlamaya ve sözleşmeye sahip oldukları diğer hizmet uç noktalarına benzer ve yapılandırma veya kod aracılığıyla bir hizmet ana bilgisayarına eklenebilirler.</span><span class="sxs-lookup"><span data-stu-id="ad7d2-106">Metadata endpoints are similar to other service endpoints in that they have an address, a binding, and a contract, and they can be added to a service host through configuration or in code.</span></span> <span data-ttu-id="ad7d2-107">Meta veri uç noktalarını yayımlamayı etkinleştirmek için hizmet <xref:System.ServiceModel.Description.ServiceMetadataBehavior> davranışını hizmete eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ad7d2-107">To enable publishing metadata endpoints, you must add the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> service behavior to the service.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ad7d2-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="ad7d2-108">In This Section</span></span>  

 [<span data-ttu-id="ad7d2-109">Nasıl yapılır: Yapılandırma Dosyası Kullanarak Bir Hizmet için Meta Verileri Yayımlama</span><span class="sxs-lookup"><span data-stu-id="ad7d2-109">How to: Publish Metadata for a Service Using a Configuration File</span></span>](./feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 <span data-ttu-id="ad7d2-110">İstemcilerin, sorgu dizesini kullanarak bir WS-MetadataExchange veya HTTP/GET isteği kullanarak meta verileri alabilmesi için meta verileri yayınlamak üzere bir WCF hizmetinin nasıl yapılandırılacağını gösterir `?wsdl` .</span><span class="sxs-lookup"><span data-stu-id="ad7d2-110">Demonstrates how to configure a WCF service to publish metadata so that clients can retrieve the metadata using a WS-MetadataExchange or an HTTP/GET request using the `?wsdl` query string.</span></span>  
  
 [<span data-ttu-id="ad7d2-111">Nasıl yapılır: Kod Kullanarak Bir Hizmet için Meta Verileri Yayımlama</span><span class="sxs-lookup"><span data-stu-id="ad7d2-111">How to: Publish Metadata for a Service Using Code</span></span>](./feature-details/how-to-publish-metadata-for-a-service-using-code.md)  
 <span data-ttu-id="ad7d2-112">İstemcilerin bir WS-MetadataExchange veya sorgu dizesini kullanarak bir HTTP/GET isteği kullanarak meta verileri alabilmesi için kodda bir WCF hizmeti için meta veri yayımlamanın nasıl etkinleştirileceğini gösterir `?wsdl` .</span><span class="sxs-lookup"><span data-stu-id="ad7d2-112">Demonstrates how to enable metadata publishing for a WCF service in code so that clients can retrieve the metadata using a WS-MetadataExchange or an HTTP/GET request using the `?wsdl` query string.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad7d2-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ad7d2-113">See also</span></span>

- [<span data-ttu-id="ad7d2-114">Meta Verileri Yayımlama</span><span class="sxs-lookup"><span data-stu-id="ad7d2-114">Publishing Metadata</span></span>](./feature-details/publishing-metadata.md)
