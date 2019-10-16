---
title: Windows Communication Foundation Uç Noktaları
ms.date: 03/30/2017
helpviewer_keywords:
- endpoints [WCF]
ms.assetid: bd0c310f-dd9f-4081-9be2-3db5909850b6
ms.openlocfilehash: f11a8198d38a01fe27a84a3e613e1ff066c25b9d
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319908"
---
# <a name="windows-communication-foundation-endpoints"></a><span data-ttu-id="d9f4c-102">Windows Communication Foundation Uç Noktaları</span><span class="sxs-lookup"><span data-stu-id="d9f4c-102">Windows Communication Foundation Endpoints</span></span>
<span data-ttu-id="d9f4c-103">Bir Windows Communication Foundation (WCF) hizmeti olan tüm iletişimler hizmetin *uç noktaları* aracılığıyla oluşur.</span><span class="sxs-lookup"><span data-stu-id="d9f4c-103">All communication with a Windows Communication Foundation (WCF) service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="d9f4c-104">Uç noktalar, istemcilere bir WCF hizmetinin sunduğu işlevlere erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="d9f4c-104">Endpoints provide clients access to the functionality that a WCF service offers.</span></span>  
  
 <span data-ttu-id="d9f4c-105">Uç nokta oluşturma hakkında genel bir bakış için bkz. [Endpoint oluşturmaya genel bakış](endpoint-creation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="d9f4c-105">For an overview about how to create an endpoint, see [Endpoint Creation Overview](endpoint-creation-overview.md).</span></span> <span data-ttu-id="d9f4c-106">Her uç nokta şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="d9f4c-106">Each endpoint contains:</span></span>  
  
- <span data-ttu-id="d9f4c-107">Uç noktanın nerede bulunacağını gösteren bir adres.</span><span class="sxs-lookup"><span data-stu-id="d9f4c-107">An address that indicates where to find the endpoint.</span></span>  
  
- <span data-ttu-id="d9f4c-108">Bir istemcinin bitiş noktasıyla nasıl iletişim kurabildiğini belirten bir bağlama.</span><span class="sxs-lookup"><span data-stu-id="d9f4c-108">A binding that specifies how a client can communicate with the endpoint.</span></span>  
  
- <span data-ttu-id="d9f4c-109">Kullanılabilir yöntemleri tanımlayan bir anlaşma.</span><span class="sxs-lookup"><span data-stu-id="d9f4c-109">A contract that identifies the methods available.</span></span>  
  
 <span data-ttu-id="d9f4c-110">Bir uç noktanın bu tek bölümlerini belirtme hakkında açıklamalar için, bkz:</span><span class="sxs-lookup"><span data-stu-id="d9f4c-110">For descriptions about how to specify these individual parts of an endpoint, see:</span></span>  
  
- [<span data-ttu-id="d9f4c-111">Uç Nokta Adresi Belirtme</span><span class="sxs-lookup"><span data-stu-id="d9f4c-111">Specifying an Endpoint Address</span></span>](specifying-an-endpoint-address.md)  
  
- [<span data-ttu-id="d9f4c-112">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="d9f4c-112">Using Bindings to Configure Services and Clients</span></span>](using-bindings-to-configure-services-and-clients.md)  
  
- [<span data-ttu-id="d9f4c-113">Hizmetleri Tasarlama ve Uygulama</span><span class="sxs-lookup"><span data-stu-id="d9f4c-113">Designing and Implementing Services</span></span>](designing-and-implementing-services.md)  
  
## <a name="in-this-section"></a><span data-ttu-id="d9f4c-114">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="d9f4c-114">In This Section</span></span>  
 [<span data-ttu-id="d9f4c-115">Uç Nokta Oluşturmaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="d9f4c-115">Endpoint Creation Overview</span></span>](endpoint-creation-overview.md)  
 <span data-ttu-id="d9f4c-116">Bir uç noktanın yapısını açıklar ve bir uç noktanın yapılandırma ve kodda nasıl tanımlanacağını, ayrıca çalışma zamanı tarafından belirtilen varsayılan uç noktaların, bağlamaların ve davranışların nasıl kullanılacağı özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="d9f4c-116">Describes the structure of an endpoint and outlines how to define an endpoint in configuration and in code, as well as how to use the default endpoints, bindings, and behaviors provided by the runtime.</span></span>  
  
 [<span data-ttu-id="d9f4c-117">Uç Nokta Adresi Belirtme</span><span class="sxs-lookup"><span data-stu-id="d9f4c-117">Specifying an Endpoint Address</span></span>](specifying-an-endpoint-address.md)  
 <span data-ttu-id="d9f4c-118">Bir WCF hizmeti ile iletişimin uç noktalar aracılığıyla nasıl oluştuğunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="d9f4c-118">Describes how communication with a WCF service occurs through endpoints.</span></span>  
  
 [<span data-ttu-id="d9f4c-119">Nasıl yapılır: Yapılandırma İçinde Hizmet Uç Noktası Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d9f4c-119">How to: Create a Service Endpoint in Configuration</span></span>](./feature-details/how-to-create-a-service-endpoint-in-configuration.md)  
 <span data-ttu-id="d9f4c-120">Yapılandırmada bir hizmet uç noktası oluşturmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="d9f4c-120">Demonstrates how to create a service endpoint in configuration.</span></span>  
  
 [<span data-ttu-id="d9f4c-121">Nasıl yapılır: Kod İçinde Hizmet Uç Noktası Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d9f4c-121">How to: Create a Service Endpoint in Code</span></span>](./feature-details/how-to-create-a-service-endpoint-in-code.md)  
 <span data-ttu-id="d9f4c-122">Kodda bir hizmet uç noktası oluşturmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="d9f4c-122">Demonstrates how to create a service endpoint in code.</span></span>  
  
 [<span data-ttu-id="d9f4c-123">Meta Veri Uç Noktalarını Yayımlama</span><span class="sxs-lookup"><span data-stu-id="d9f4c-123">Publishing Metadata Endpoints</span></span>](publishing-metadata-endpoints.md)  
 <span data-ttu-id="d9f4c-124">Yapılandırmada ve kodunda meta veri uç noktaları yayımlayarak meta verilerin nasıl yayımlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d9f4c-124">Demonstrates how to publish metadata by publishing metadata endpoints in configuration and in code.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="d9f4c-125">Başvuru</span><span class="sxs-lookup"><span data-stu-id="d9f4c-125">Reference</span></span>  
 <xref:System.ServiceModel.EndpointAddress>  
  
## <a name="related-sections"></a><span data-ttu-id="d9f4c-126">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="d9f4c-126">Related Sections</span></span>  
 [<span data-ttu-id="d9f4c-127">Temel Programlama Yaşam Döngüsü</span><span class="sxs-lookup"><span data-stu-id="d9f4c-127">Basic Programming Lifecycle</span></span>](basic-programming-lifecycle.md)
