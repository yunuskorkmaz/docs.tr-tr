---
title: "Windows Communication Foundation Uç Noktaları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: endpoints [WCF]
ms.assetid: bd0c310f-dd9f-4081-9be2-3db5909850b6
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4ac3d1f16d860ea01217d0d1d35d0588da0c8d87
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="windows-communication-foundation-endpoints"></a><span data-ttu-id="f8746-102">Windows Communication Foundation Uç Noktaları</span><span class="sxs-lookup"><span data-stu-id="f8746-102">Windows Communication Foundation Endpoints</span></span>
<span data-ttu-id="f8746-103">İle tüm iletişimin bir [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] servis oluşur aracılığıyla *uç noktaları* hizmetinin.</span><span class="sxs-lookup"><span data-stu-id="f8746-103">All communication with a [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="f8746-104">Uç noktaları, istemcilerin erişim işlevine sağlar bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmet sunar.</span><span class="sxs-lookup"><span data-stu-id="f8746-104">Endpoints provide clients access to the functionality that a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service offers.</span></span>  
  
 <span data-ttu-id="f8746-105">Bir uç nokta oluşturma hakkında bir genel bakış için bkz: [uç noktası oluşturma genel bakış](../../../docs/framework/wcf/endpoint-creation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="f8746-105">For an overview about how to create an endpoint, see [Endpoint Creation Overview](../../../docs/framework/wcf/endpoint-creation-overview.md).</span></span> <span data-ttu-id="f8746-106">Her uç nokta içerir:</span><span class="sxs-lookup"><span data-stu-id="f8746-106">Each endpoint contains:</span></span>  
  
-   <span data-ttu-id="f8746-107">Uç nokta nerede bulacağını gösteren bir adres.</span><span class="sxs-lookup"><span data-stu-id="f8746-107">An address that indicates where to find the endpoint.</span></span>  
  
-   <span data-ttu-id="f8746-108">Bir bağlama istemci uç noktasıyla nasıl iletişim kurabilir belirtir.</span><span class="sxs-lookup"><span data-stu-id="f8746-108">A binding that specifies how a client can communicate with the endpoint.</span></span>  
  
-   <span data-ttu-id="f8746-109">Kullanılabilir yöntemleri tanımlayan bir sözleşme.</span><span class="sxs-lookup"><span data-stu-id="f8746-109">A contract that identifies the methods available.</span></span>  
  
 <span data-ttu-id="f8746-110">Bu tek tek bir uç nokta bölümlerini belirtme hakkında daha fazla açıklamaları için bkz:</span><span class="sxs-lookup"><span data-stu-id="f8746-110">For descriptions about how to specify these individual parts of an endpoint, see:</span></span>  
  
-   [<span data-ttu-id="f8746-111">Bir uç noktası adresi belirtme</span><span class="sxs-lookup"><span data-stu-id="f8746-111">Specifying an Endpoint Address</span></span>](../../../docs/framework/wcf/specifying-an-endpoint-address.md)  
  
-   [<span data-ttu-id="f8746-112">Hizmetler ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="f8746-112">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
  
-   [<span data-ttu-id="f8746-113">Hizmetleri Tasarlama ve uygulama</span><span class="sxs-lookup"><span data-stu-id="f8746-113">Designing and Implementing Services</span></span>](../../../docs/framework/wcf/designing-and-implementing-services.md)  
  
## <a name="in-this-section"></a><span data-ttu-id="f8746-114">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="f8746-114">In This Section</span></span>  
 [<span data-ttu-id="f8746-115">Uç noktası oluşturma genel bakış</span><span class="sxs-lookup"><span data-stu-id="f8746-115">Endpoint Creation Overview</span></span>](../../../docs/framework/wcf/endpoint-creation-overview.md)  
 <span data-ttu-id="f8746-116">Bir uç nokta yapısını tanımlar ve varsayılan uç noktalar, bağlamaları ve davranışları kullanmak için çalışma zamanı tarafından sağlanan nasıl bir uç nokta yapılandırması ve kodda, nasıl tanımlanacağı de özetler.</span><span class="sxs-lookup"><span data-stu-id="f8746-116">Describes the structure of an endpoint and outlines how to define an endpoint in configuration and in code, as well as how to use the default endpoints, bindings, and behaviors provided by the runtime.</span></span>  
  
 [<span data-ttu-id="f8746-117">Bir uç noktası adresi belirtme</span><span class="sxs-lookup"><span data-stu-id="f8746-117">Specifying an Endpoint Address</span></span>](../../../docs/framework/wcf/specifying-an-endpoint-address.md)  
 <span data-ttu-id="f8746-118">Açıklar nasıl ile iletişim bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmet bitiş noktalarından oluşur.</span><span class="sxs-lookup"><span data-stu-id="f8746-118">Describes how communication with a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service occurs through endpoints.</span></span>  
  
 [<span data-ttu-id="f8746-119">Nasıl yapılır: yapılandırmada hizmet uç noktası oluşturma</span><span class="sxs-lookup"><span data-stu-id="f8746-119">How to: Create a Service Endpoint in Configuration</span></span>](../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)  
 <span data-ttu-id="f8746-120">Hizmet uç noktası yapılandırması oluşturmak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f8746-120">Demonstrates how to create a service endpoint in configuration.</span></span>  
  
 [<span data-ttu-id="f8746-121">Nasıl yapılır: kod içinde hizmet uç noktası oluşturma</span><span class="sxs-lookup"><span data-stu-id="f8746-121">How to: Create a Service Endpoint in Code</span></span>](../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)  
 <span data-ttu-id="f8746-122">Kod içinde hizmet uç noktası oluşturma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f8746-122">Demonstrates how to create a service endpoint in code.</span></span>  
  
 [<span data-ttu-id="f8746-123">Yayımlama meta veri uç noktaları</span><span class="sxs-lookup"><span data-stu-id="f8746-123">Publishing Metadata Endpoints</span></span>](../../../docs/framework/wcf/publishing-metadata-endpoints.md)  
 <span data-ttu-id="f8746-124">Meta veri meta veri uç noktalarını yapılandırma ve kodun yayımlayarak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f8746-124">Demonstrates how to publish metadata by publishing metadata endpoints in configuration and in code.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="f8746-125">Başvuru</span><span class="sxs-lookup"><span data-stu-id="f8746-125">Reference</span></span>  
 <xref:System.ServiceModel.EndpointAddress>  
  
## <a name="related-sections"></a><span data-ttu-id="f8746-126">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="f8746-126">Related Sections</span></span>  
 [<span data-ttu-id="f8746-127">Temel programlama yaşam döngüsü</span><span class="sxs-lookup"><span data-stu-id="f8746-127">Basic Programming Lifecycle</span></span>](../../../docs/framework/wcf/basic-programming-lifecycle.md)
