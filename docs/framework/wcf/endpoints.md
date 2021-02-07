---
description: 'Hakkında daha fazla bilgi edinin: Windows Communication Foundation uç noktaları'
title: Windows Communication Foundation Uç Noktaları
ms.date: 03/30/2017
helpviewer_keywords:
- endpoints [WCF]
ms.assetid: bd0c310f-dd9f-4081-9be2-3db5909850b6
ms.openlocfilehash: caa918f2dd7ca7b0289cc1faf6d189270596808b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99756779"
---
# <a name="windows-communication-foundation-endpoints"></a><span data-ttu-id="1c2dc-103">Windows Communication Foundation Uç Noktaları</span><span class="sxs-lookup"><span data-stu-id="1c2dc-103">Windows Communication Foundation Endpoints</span></span>

<span data-ttu-id="1c2dc-104">Bir Windows Communication Foundation (WCF) hizmeti olan tüm iletişimler hizmetin *uç noktaları* aracılığıyla oluşur.</span><span class="sxs-lookup"><span data-stu-id="1c2dc-104">All communication with a Windows Communication Foundation (WCF) service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="1c2dc-105">Uç noktalar, istemcilere bir WCF hizmetinin sunduğu işlevlere erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="1c2dc-105">Endpoints provide clients access to the functionality that a WCF service offers.</span></span>  
  
 <span data-ttu-id="1c2dc-106">Uç nokta oluşturma hakkında genel bir bakış için bkz. [Endpoint oluşturmaya genel bakış](endpoint-creation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1c2dc-106">For an overview about how to create an endpoint, see [Endpoint Creation Overview](endpoint-creation-overview.md).</span></span> <span data-ttu-id="1c2dc-107">Her uç nokta şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="1c2dc-107">Each endpoint contains:</span></span>  
  
- <span data-ttu-id="1c2dc-108">Uç noktanın nerede bulunacağını gösteren bir adres.</span><span class="sxs-lookup"><span data-stu-id="1c2dc-108">An address that indicates where to find the endpoint.</span></span>  
  
- <span data-ttu-id="1c2dc-109">Bir istemcinin bitiş noktasıyla nasıl iletişim kurabildiğini belirten bir bağlama.</span><span class="sxs-lookup"><span data-stu-id="1c2dc-109">A binding that specifies how a client can communicate with the endpoint.</span></span>  
  
- <span data-ttu-id="1c2dc-110">Kullanılabilir yöntemleri tanımlayan bir anlaşma.</span><span class="sxs-lookup"><span data-stu-id="1c2dc-110">A contract that identifies the methods available.</span></span>  
  
 <span data-ttu-id="1c2dc-111">Bir uç noktanın bu tek bölümlerini belirtme hakkında açıklamalar için, bkz:</span><span class="sxs-lookup"><span data-stu-id="1c2dc-111">For descriptions about how to specify these individual parts of an endpoint, see:</span></span>  
  
- [<span data-ttu-id="1c2dc-112">Bir Uç Noktası Adresi Belirtme</span><span class="sxs-lookup"><span data-stu-id="1c2dc-112">Specifying an Endpoint Address</span></span>](specifying-an-endpoint-address.md)  
  
- [<span data-ttu-id="1c2dc-113">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="1c2dc-113">Using Bindings to Configure Services and Clients</span></span>](using-bindings-to-configure-services-and-clients.md)  
  
- [<span data-ttu-id="1c2dc-114">Hizmetleri Tasarlama ve Uygulama</span><span class="sxs-lookup"><span data-stu-id="1c2dc-114">Designing and Implementing Services</span></span>](designing-and-implementing-services.md)  
  
## <a name="in-this-section"></a><span data-ttu-id="1c2dc-115">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="1c2dc-115">In This Section</span></span>  

 [<span data-ttu-id="1c2dc-116">Uç Noktası Oluşturma Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="1c2dc-116">Endpoint Creation Overview</span></span>](endpoint-creation-overview.md)  
 <span data-ttu-id="1c2dc-117">Bir uç noktanın yapısını açıklar ve bir uç noktanın yapılandırma ve kodda nasıl tanımlanacağını, ayrıca çalışma zamanı tarafından belirtilen varsayılan uç noktaların, bağlamaların ve davranışların nasıl kullanılacağı özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="1c2dc-117">Describes the structure of an endpoint and outlines how to define an endpoint in configuration and in code, as well as how to use the default endpoints, bindings, and behaviors provided by the runtime.</span></span>  
  
 [<span data-ttu-id="1c2dc-118">Bir Uç Noktası Adresi Belirtme</span><span class="sxs-lookup"><span data-stu-id="1c2dc-118">Specifying an Endpoint Address</span></span>](specifying-an-endpoint-address.md)  
 <span data-ttu-id="1c2dc-119">Bir WCF hizmeti ile iletişimin uç noktalar aracılığıyla nasıl oluştuğunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="1c2dc-119">Describes how communication with a WCF service occurs through endpoints.</span></span>  
  
 [<span data-ttu-id="1c2dc-120">Nasıl yapılır: Yapılandırma İçinde Hizmet Uç Noktası Oluşturma</span><span class="sxs-lookup"><span data-stu-id="1c2dc-120">How to: Create a Service Endpoint in Configuration</span></span>](./feature-details/how-to-create-a-service-endpoint-in-configuration.md)  
 <span data-ttu-id="1c2dc-121">Yapılandırmada bir hizmet uç noktası oluşturmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="1c2dc-121">Demonstrates how to create a service endpoint in configuration.</span></span>  
  
 [<span data-ttu-id="1c2dc-122">Nasıl yapılır: Kod İçinde Hizmet Uç Noktası Oluşturma</span><span class="sxs-lookup"><span data-stu-id="1c2dc-122">How to: Create a Service Endpoint in Code</span></span>](./feature-details/how-to-create-a-service-endpoint-in-code.md)  
 <span data-ttu-id="1c2dc-123">Kodda bir hizmet uç noktası oluşturmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="1c2dc-123">Demonstrates how to create a service endpoint in code.</span></span>  
  
 [<span data-ttu-id="1c2dc-124">Meta Veri Uç Noktalarını Yayımlama</span><span class="sxs-lookup"><span data-stu-id="1c2dc-124">Publishing Metadata Endpoints</span></span>](publishing-metadata-endpoints.md)  
 <span data-ttu-id="1c2dc-125">Yapılandırmada ve kodunda meta veri uç noktaları yayımlayarak meta verilerin nasıl yayımlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1c2dc-125">Demonstrates how to publish metadata by publishing metadata endpoints in configuration and in code.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="1c2dc-126">Başvuru</span><span class="sxs-lookup"><span data-stu-id="1c2dc-126">Reference</span></span>  

 <xref:System.ServiceModel.EndpointAddress>  
  
## <a name="related-sections"></a><span data-ttu-id="1c2dc-127">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="1c2dc-127">Related Sections</span></span>  

 [<span data-ttu-id="1c2dc-128">Temel Programlama Yaşam Döngüsü</span><span class="sxs-lookup"><span data-stu-id="1c2dc-128">Basic Programming Lifecycle</span></span>](basic-programming-lifecycle.md)
