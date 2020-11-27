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
# <a name="publishing-metadata-endpoints"></a><span data-ttu-id="46a12-102">Meta Veri Uç Noktalarını Yayımlama</span><span class="sxs-lookup"><span data-stu-id="46a12-102">Publishing Metadata Endpoints</span></span>

<span data-ttu-id="46a12-103">Windows Communication Foundation (WCF) Hizmetleri bir veya daha fazla meta veri uç noktası yayımlayarak meta verileri yayımlar.</span><span class="sxs-lookup"><span data-stu-id="46a12-103">Windows Communication Foundation (WCF) services publish metadata by publishing one or more metadata endpoints.</span></span> <span data-ttu-id="46a12-104">Yayımlama hizmeti meta verileri, WS-MetadataExchange (MEX) ve HTTP/GET istekleri gibi standartlaştırılmış protokoller kullanılarak meta verilerin kullanılabilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="46a12-104">Publishing service metadata makes the metadata available using standardized protocols, such as WS-MetadataExchange (MEX) and HTTP/GET requests.</span></span> <span data-ttu-id="46a12-105">Meta veri uç noktaları, bir adrese, bağlamaya ve sözleşmeye sahip oldukları diğer hizmet uç noktalarına benzer ve yapılandırma veya kod aracılığıyla bir hizmet ana bilgisayarına eklenebilirler.</span><span class="sxs-lookup"><span data-stu-id="46a12-105">Metadata endpoints are similar to other service endpoints in that they have an address, a binding, and a contract, and they can be added to a service host through configuration or in code.</span></span> <span data-ttu-id="46a12-106">Meta veri uç noktalarını yayımlamayı etkinleştirmek için hizmet <xref:System.ServiceModel.Description.ServiceMetadataBehavior> davranışını hizmete eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="46a12-106">To enable publishing metadata endpoints, you must add the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> service behavior to the service.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="46a12-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="46a12-107">In This Section</span></span>  

 [<span data-ttu-id="46a12-108">Nasıl yapılır: Yapılandırma Dosyası Kullanarak Bir Hizmet için Meta Verileri Yayımlama</span><span class="sxs-lookup"><span data-stu-id="46a12-108">How to: Publish Metadata for a Service Using a Configuration File</span></span>](./feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 <span data-ttu-id="46a12-109">İstemcilerin, sorgu dizesini kullanarak bir WS-MetadataExchange veya HTTP/GET isteği kullanarak meta verileri alabilmesi için meta verileri yayınlamak üzere bir WCF hizmetinin nasıl yapılandırılacağını gösterir `?wsdl` .</span><span class="sxs-lookup"><span data-stu-id="46a12-109">Demonstrates how to configure a WCF service to publish metadata so that clients can retrieve the metadata using a WS-MetadataExchange or an HTTP/GET request using the `?wsdl` query string.</span></span>  
  
 [<span data-ttu-id="46a12-110">Nasıl yapılır: Kod Kullanarak Bir Hizmet için Meta Verileri Yayımlama</span><span class="sxs-lookup"><span data-stu-id="46a12-110">How to: Publish Metadata for a Service Using Code</span></span>](./feature-details/how-to-publish-metadata-for-a-service-using-code.md)  
 <span data-ttu-id="46a12-111">İstemcilerin bir WS-MetadataExchange veya sorgu dizesini kullanarak bir HTTP/GET isteği kullanarak meta verileri alabilmesi için kodda bir WCF hizmeti için meta veri yayımlamanın nasıl etkinleştirileceğini gösterir `?wsdl` .</span><span class="sxs-lookup"><span data-stu-id="46a12-111">Demonstrates how to enable metadata publishing for a WCF service in code so that clients can retrieve the metadata using a WS-MetadataExchange or an HTTP/GET request using the `?wsdl` query string.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46a12-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="46a12-112">See also</span></span>

- [<span data-ttu-id="46a12-113">Meta Verileri Yayımlama</span><span class="sxs-lookup"><span data-stu-id="46a12-113">Publishing Metadata</span></span>](./feature-details/publishing-metadata.md)
