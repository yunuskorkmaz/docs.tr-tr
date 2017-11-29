---
title: "Meta Veri Uç Noktalarını Yayımlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 29cd8a60-dfb7-460c-bf5a-c2b31b782671
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0f3f134526fd24a724ba593302ba2bf1f27fa3e2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="publishing-metadata-endpoints"></a><span data-ttu-id="7ae35-102">Meta Veri Uç Noktalarını Yayımlama</span><span class="sxs-lookup"><span data-stu-id="7ae35-102">Publishing Metadata Endpoints</span></span>
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)]<span data-ttu-id="7ae35-103">Hizmetleri, bir veya daha fazla meta veri uç noktalarını yayımlayarak meta veri yayımlama.</span><span class="sxs-lookup"><span data-stu-id="7ae35-103"> services publish metadata by publishing one or more metadata endpoints.</span></span> <span data-ttu-id="7ae35-104">Hizmet meta veri yayımlama meta verileri WS-MetadataExchange (MEX) ve HTTP/GET istekleri gibi standart protokoller kullanılarak kullanılabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="7ae35-104">Publishing service metadata makes the metadata available using standardized protocols, such as WS-MetadataExchange (MEX) and HTTP/GET requests.</span></span> <span data-ttu-id="7ae35-105">Meta veri uç noktalarını bir adresi, bağlama ve bir sözleşme sahip ve bir hizmet ana yapılandırma yoluyla ya da koddaki eklenebilir, diğer hizmet uç noktaları benzerdir.</span><span class="sxs-lookup"><span data-stu-id="7ae35-105">Metadata endpoints are similar to other service endpoints in that they have an address, a binding, and a contract, and they can be added to a service host through configuration or in code.</span></span> <span data-ttu-id="7ae35-106">Yayımlama meta veri uç noktalarını etkinleştirmek için eklemelisiniz <xref:System.ServiceModel.Description.ServiceMetadataBehavior> hizmet hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="7ae35-106">To enable publishing metadata endpoints, you must add the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> service behavior to the service.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7ae35-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="7ae35-107">In This Section</span></span>  
 [<span data-ttu-id="7ae35-108">Nasıl yapılır: bir yapılandırma dosyası kullanarak bir hizmet için meta verileri yayımlama</span><span class="sxs-lookup"><span data-stu-id="7ae35-108">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 <span data-ttu-id="7ae35-109">Nasıl yapılandırılacağını göstermektedir bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] istemcileri WS-MetadataExchange ya da bir HTTP/GET isteği kullanarak kullanarak meta verilerini alabilmesi meta veri yayımlama için hizmet `?wsdl` sorgu dizesi.</span><span class="sxs-lookup"><span data-stu-id="7ae35-109">Demonstrates how to configure a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service to publish metadata so that clients can retrieve the metadata using a WS-MetadataExchange or an HTTP/GET request using the `?wsdl` query string.</span></span>  
  
 [<span data-ttu-id="7ae35-110">Nasıl yapılır: kod kullanarak bir hizmet için meta verileri yayımlama</span><span class="sxs-lookup"><span data-stu-id="7ae35-110">How to: Publish Metadata for a Service Using Code</span></span>](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)  
 <span data-ttu-id="7ae35-111">Meta veri yayımlama için etkinleştirme gösteren bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] istemcileri WS-MetadataExchange ya da bir HTTP/GET isteği kullanarak kullanarak meta verilerini alabilmesi kod içinde hizmet `?wsdl` sorgu dizesi.</span><span class="sxs-lookup"><span data-stu-id="7ae35-111">Demonstrates how to enable metadata publishing for a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service in code so that clients can retrieve the metadata using a WS-MetadataExchange or an HTTP/GET request using the `?wsdl` query string.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ae35-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7ae35-112">See Also</span></span>  
 [<span data-ttu-id="7ae35-113">Meta veri yayımlama</span><span class="sxs-lookup"><span data-stu-id="7ae35-113">Publishing Metadata</span></span>](../../../docs/framework/wcf/feature-details/publishing-metadata.md)
