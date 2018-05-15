---
title: Windows Communication Foundation Uç Noktaları
ms.date: 03/30/2017
helpviewer_keywords:
- endpoints [WCF]
ms.assetid: bd0c310f-dd9f-4081-9be2-3db5909850b6
ms.openlocfilehash: b55abe937701f8708643efa2ea4cb62514b3521b
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
---
# <a name="windows-communication-foundation-endpoints"></a><span data-ttu-id="33d17-102">Windows Communication Foundation Uç Noktaları</span><span class="sxs-lookup"><span data-stu-id="33d17-102">Windows Communication Foundation Endpoints</span></span>
<span data-ttu-id="33d17-103">Tüm Windows Communication Foundation (WCF) hizmetiyle aracılığıyla iletişimin *uç noktaları* hizmetinin.</span><span class="sxs-lookup"><span data-stu-id="33d17-103">All communication with a Windows Communication Foundation (WCF) service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="33d17-104">Uç noktaları istemciler için bir WCF hizmeti sunan işlevlere erişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="33d17-104">Endpoints provide clients access to the functionality that a WCF service offers.</span></span>  
  
 <span data-ttu-id="33d17-105">Bir uç nokta oluşturma hakkında bir genel bakış için bkz: [uç noktası oluşturma genel bakış](../../../docs/framework/wcf/endpoint-creation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="33d17-105">For an overview about how to create an endpoint, see [Endpoint Creation Overview](../../../docs/framework/wcf/endpoint-creation-overview.md).</span></span> <span data-ttu-id="33d17-106">Her uç nokta içerir:</span><span class="sxs-lookup"><span data-stu-id="33d17-106">Each endpoint contains:</span></span>  
  
-   <span data-ttu-id="33d17-107">Uç nokta nerede bulacağını gösteren bir adres.</span><span class="sxs-lookup"><span data-stu-id="33d17-107">An address that indicates where to find the endpoint.</span></span>  
  
-   <span data-ttu-id="33d17-108">Bir bağlama istemci uç noktasıyla nasıl iletişim kurabilir belirtir.</span><span class="sxs-lookup"><span data-stu-id="33d17-108">A binding that specifies how a client can communicate with the endpoint.</span></span>  
  
-   <span data-ttu-id="33d17-109">Kullanılabilir yöntemleri tanımlayan bir sözleşme.</span><span class="sxs-lookup"><span data-stu-id="33d17-109">A contract that identifies the methods available.</span></span>  
  
 <span data-ttu-id="33d17-110">Bu tek tek bir uç nokta bölümlerini belirtme hakkında daha fazla açıklamaları için bkz:</span><span class="sxs-lookup"><span data-stu-id="33d17-110">For descriptions about how to specify these individual parts of an endpoint, see:</span></span>  
  
-   [<span data-ttu-id="33d17-111">Uç Nokta Adresi Belirtme</span><span class="sxs-lookup"><span data-stu-id="33d17-111">Specifying an Endpoint Address</span></span>](../../../docs/framework/wcf/specifying-an-endpoint-address.md)  
  
-   [<span data-ttu-id="33d17-112">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="33d17-112">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
  
-   [<span data-ttu-id="33d17-113">Hizmetleri Tasarlama ve Uygulama</span><span class="sxs-lookup"><span data-stu-id="33d17-113">Designing and Implementing Services</span></span>](../../../docs/framework/wcf/designing-and-implementing-services.md)  
  
## <a name="in-this-section"></a><span data-ttu-id="33d17-114">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="33d17-114">In This Section</span></span>  
 [<span data-ttu-id="33d17-115">Uç Nokta Oluşturmaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="33d17-115">Endpoint Creation Overview</span></span>](../../../docs/framework/wcf/endpoint-creation-overview.md)  
 <span data-ttu-id="33d17-116">Bir uç nokta yapısını tanımlar ve varsayılan uç noktalar, bağlamaları ve davranışları kullanmak için çalışma zamanı tarafından sağlanan nasıl bir uç nokta yapılandırması ve kodda, nasıl tanımlanacağı de özetler.</span><span class="sxs-lookup"><span data-stu-id="33d17-116">Describes the structure of an endpoint and outlines how to define an endpoint in configuration and in code, as well as how to use the default endpoints, bindings, and behaviors provided by the runtime.</span></span>  
  
 [<span data-ttu-id="33d17-117">Uç Nokta Adresi Belirtme</span><span class="sxs-lookup"><span data-stu-id="33d17-117">Specifying an Endpoint Address</span></span>](../../../docs/framework/wcf/specifying-an-endpoint-address.md)  
 <span data-ttu-id="33d17-118">Bir WCF Hizmeti ile iletişim uç noktaları yoluyla nasıl gerçekleştiğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="33d17-118">Describes how communication with a WCF service occurs through endpoints.</span></span>  
  
 [<span data-ttu-id="33d17-119">Nasıl yapılır: Yapılandırma İçinde Hizmet Uç Noktası Oluşturma</span><span class="sxs-lookup"><span data-stu-id="33d17-119">How to: Create a Service Endpoint in Configuration</span></span>](../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)  
 <span data-ttu-id="33d17-120">Hizmet uç noktası yapılandırması oluşturmak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="33d17-120">Demonstrates how to create a service endpoint in configuration.</span></span>  
  
 [<span data-ttu-id="33d17-121">Nasıl yapılır: Kod İçinde Hizmet Uç Noktası Oluşturma</span><span class="sxs-lookup"><span data-stu-id="33d17-121">How to: Create a Service Endpoint in Code</span></span>](../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)  
 <span data-ttu-id="33d17-122">Kod içinde hizmet uç noktası oluşturma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="33d17-122">Demonstrates how to create a service endpoint in code.</span></span>  
  
 [<span data-ttu-id="33d17-123">Meta Veri Uç Noktalarını Yayımlama</span><span class="sxs-lookup"><span data-stu-id="33d17-123">Publishing Metadata Endpoints</span></span>](../../../docs/framework/wcf/publishing-metadata-endpoints.md)  
 <span data-ttu-id="33d17-124">Meta veri meta veri uç noktalarını yapılandırma ve kodun yayımlayarak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="33d17-124">Demonstrates how to publish metadata by publishing metadata endpoints in configuration and in code.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="33d17-125">Başvuru</span><span class="sxs-lookup"><span data-stu-id="33d17-125">Reference</span></span>  
 <xref:System.ServiceModel.EndpointAddress>  
  
## <a name="related-sections"></a><span data-ttu-id="33d17-126">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="33d17-126">Related Sections</span></span>  
 [<span data-ttu-id="33d17-127">Temel Programlama Yaşam Döngüsü</span><span class="sxs-lookup"><span data-stu-id="33d17-127">Basic Programming Lifecycle</span></span>](../../../docs/framework/wcf/basic-programming-lifecycle.md)
