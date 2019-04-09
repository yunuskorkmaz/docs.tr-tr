---
title: Meta Veri Uç Noktalarını Yayımlama
ms.date: 03/30/2017
ms.assetid: 29cd8a60-dfb7-460c-bf5a-c2b31b782671
ms.openlocfilehash: 143a46ce18a0d9dee89bbbffac9be9a467e951df
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59121738"
---
# <a name="publishing-metadata-endpoints"></a><span data-ttu-id="ce095-102">Meta Veri Uç Noktalarını Yayımlama</span><span class="sxs-lookup"><span data-stu-id="ce095-102">Publishing Metadata Endpoints</span></span>
<span data-ttu-id="ce095-103">Windows Communication Foundation (WCF) Hizmetleri, bir veya daha fazla meta veri uç noktalarını yayımlayarak meta verileri yayımlama.</span><span class="sxs-lookup"><span data-stu-id="ce095-103">Windows Communication Foundation (WCF) services publish metadata by publishing one or more metadata endpoints.</span></span> <span data-ttu-id="ce095-104">Hizmet meta verileri yayımlama meta verileri, WS-MetadataExchange (MEX) ve HTTP/GET istekleri gibi standart protokolleri kullanarak kullanılabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="ce095-104">Publishing service metadata makes the metadata available using standardized protocols, such as WS-MetadataExchange (MEX) and HTTP/GET requests.</span></span> <span data-ttu-id="ce095-105">Meta veri uç noktalarını, adres, bağlama ve bir sözleşme sahip ve bir hizmet konağı yapılandırma veya kod için eklenebilir, diğer hizmet uç noktaları için benzerdir.</span><span class="sxs-lookup"><span data-stu-id="ce095-105">Metadata endpoints are similar to other service endpoints in that they have an address, a binding, and a contract, and they can be added to a service host through configuration or in code.</span></span> <span data-ttu-id="ce095-106">Meta veri uç noktalarını yayımlama etkinleştirmek için eklemelisiniz <xref:System.ServiceModel.Description.ServiceMetadataBehavior> hizmet hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="ce095-106">To enable publishing metadata endpoints, you must add the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> service behavior to the service.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ce095-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="ce095-107">In This Section</span></span>  
 [<span data-ttu-id="ce095-108">Nasıl yapılır: Yapılandırma Dosyası Kullanarak Bir Hizmet için Meta Verileri Yayımlama</span><span class="sxs-lookup"><span data-stu-id="ce095-108">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 <span data-ttu-id="ce095-109">İstemciler bir WS-MetadataExchange ya da bir HTTP/GET isteği kullanılarak kullanarak meta verileri alabilir. böylece, meta verileri yayımlamak için bir WCF hizmetini yapılandırma gösterilmektedir `?wsdl` sorgu dizesi.</span><span class="sxs-lookup"><span data-stu-id="ce095-109">Demonstrates how to configure a WCF service to publish metadata so that clients can retrieve the metadata using a WS-MetadataExchange or an HTTP/GET request using the `?wsdl` query string.</span></span>  
  
 [<span data-ttu-id="ce095-110">Nasıl yapılır: Kod Kullanarak Bir Hizmet için Meta Verileri Yayımlama</span><span class="sxs-lookup"><span data-stu-id="ce095-110">How to: Publish Metadata for a Service Using Code</span></span>](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)  
 <span data-ttu-id="ce095-111">İstemciler bir WS-MetadataExchange ya da bir HTTP/GET isteği kullanılarak kullanarak meta verileri alabilir. böylece kodda bir WCF hizmeti için meta veri yayımlamayı etkinleştirme gösterilmektedir `?wsdl` sorgu dizesi.</span><span class="sxs-lookup"><span data-stu-id="ce095-111">Demonstrates how to enable metadata publishing for a WCF service in code so that clients can retrieve the metadata using a WS-MetadataExchange or an HTTP/GET request using the `?wsdl` query string.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce095-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ce095-112">See also</span></span>

- [<span data-ttu-id="ce095-113">Meta Verileri Yayımlama</span><span class="sxs-lookup"><span data-stu-id="ce095-113">Publishing Metadata</span></span>](../../../docs/framework/wcf/feature-details/publishing-metadata.md)
