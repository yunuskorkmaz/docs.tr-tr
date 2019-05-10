---
title: Windows Communication Foundation Uç Noktaları
ms.date: 03/30/2017
helpviewer_keywords:
- endpoints [WCF]
ms.assetid: bd0c310f-dd9f-4081-9be2-3db5909850b6
ms.openlocfilehash: 1a18e2ab31998b7759803e023151892694757119
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64613391"
---
# <a name="windows-communication-foundation-endpoints"></a><span data-ttu-id="6db47-102">Windows Communication Foundation Uç Noktaları</span><span class="sxs-lookup"><span data-stu-id="6db47-102">Windows Communication Foundation Endpoints</span></span>
<span data-ttu-id="6db47-103">Bir Windows Communication Foundation (WCF) hizmetiyle kurulan tüm iletişimlerde üzerinden gerçekleşir *uç noktaları* hizmeti.</span><span class="sxs-lookup"><span data-stu-id="6db47-103">All communication with a Windows Communication Foundation (WCF) service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="6db47-104">Uç noktaları, istemcilerin bir WCF hizmeti sunan işlevine erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="6db47-104">Endpoints provide clients access to the functionality that a WCF service offers.</span></span>  
  
 <span data-ttu-id="6db47-105">Bir uç nokta oluşturma hakkında genel bir bakış için bkz. [uç nokta oluşturmaya genel bakış](../../../docs/framework/wcf/endpoint-creation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="6db47-105">For an overview about how to create an endpoint, see [Endpoint Creation Overview](../../../docs/framework/wcf/endpoint-creation-overview.md).</span></span> <span data-ttu-id="6db47-106">Her uç nokta içerir:</span><span class="sxs-lookup"><span data-stu-id="6db47-106">Each endpoint contains:</span></span>  
  
- <span data-ttu-id="6db47-107">Uç nokta yeri belirten bir adres.</span><span class="sxs-lookup"><span data-stu-id="6db47-107">An address that indicates where to find the endpoint.</span></span>  
  
- <span data-ttu-id="6db47-108">Bir bağlama için bir istemci uç noktasıyla nasıl iletişim kurabilir belirtir.</span><span class="sxs-lookup"><span data-stu-id="6db47-108">A binding that specifies how a client can communicate with the endpoint.</span></span>  
  
- <span data-ttu-id="6db47-109">Kullanılabilir yöntemleri tanımlayan bir sözleşme.</span><span class="sxs-lookup"><span data-stu-id="6db47-109">A contract that identifies the methods available.</span></span>  
  
 <span data-ttu-id="6db47-110">Bu ayrı bir uç nokta bölümlerini belirtme hakkında daha fazla açıklamaları için bkz:</span><span class="sxs-lookup"><span data-stu-id="6db47-110">For descriptions about how to specify these individual parts of an endpoint, see:</span></span>  
  
- [<span data-ttu-id="6db47-111">Uç Nokta Adresi Belirtme</span><span class="sxs-lookup"><span data-stu-id="6db47-111">Specifying an Endpoint Address</span></span>](../../../docs/framework/wcf/specifying-an-endpoint-address.md)  
  
- [<span data-ttu-id="6db47-112">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="6db47-112">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
  
- [<span data-ttu-id="6db47-113">Hizmetleri Tasarlama ve Uygulama</span><span class="sxs-lookup"><span data-stu-id="6db47-113">Designing and Implementing Services</span></span>](../../../docs/framework/wcf/designing-and-implementing-services.md)  
  
## <a name="in-this-section"></a><span data-ttu-id="6db47-114">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="6db47-114">In This Section</span></span>  
 [<span data-ttu-id="6db47-115">Uç Nokta Oluşturmaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="6db47-115">Endpoint Creation Overview</span></span>](../../../docs/framework/wcf/endpoint-creation-overview.md)  
 <span data-ttu-id="6db47-116">Bir uç nokta yapısını açıklar ve varsayılan uç noktaları, bağlamalar ve davranışları kullanmak için çalışma zamanı tarafından sağlanan nasıl bir uç nokta yapılandırması ve kodda nasıl tanımlanacağını de açıklar.</span><span class="sxs-lookup"><span data-stu-id="6db47-116">Describes the structure of an endpoint and outlines how to define an endpoint in configuration and in code, as well as how to use the default endpoints, bindings, and behaviors provided by the runtime.</span></span>  
  
 [<span data-ttu-id="6db47-117">Uç Nokta Adresi Belirtme</span><span class="sxs-lookup"><span data-stu-id="6db47-117">Specifying an Endpoint Address</span></span>](../../../docs/framework/wcf/specifying-an-endpoint-address.md)  
 <span data-ttu-id="6db47-118">Bir WCF Hizmeti ile iletişimi uç noktaları yoluyla ne olacağı açıklanır.</span><span class="sxs-lookup"><span data-stu-id="6db47-118">Describes how communication with a WCF service occurs through endpoints.</span></span>  
  
 [<span data-ttu-id="6db47-119">Nasıl yapılır: Yapılandırma içinde hizmet uç noktası oluşturma</span><span class="sxs-lookup"><span data-stu-id="6db47-119">How to: Create a Service Endpoint in Configuration</span></span>](../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)  
 <span data-ttu-id="6db47-120">Yapılandırma içinde hizmet uç noktası oluşturma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6db47-120">Demonstrates how to create a service endpoint in configuration.</span></span>  
  
 [<span data-ttu-id="6db47-121">Nasıl yapılır: Kod içinde hizmet uç noktası oluşturma</span><span class="sxs-lookup"><span data-stu-id="6db47-121">How to: Create a Service Endpoint in Code</span></span>](../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)  
 <span data-ttu-id="6db47-122">Kod içinde hizmet uç noktası oluşturma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6db47-122">Demonstrates how to create a service endpoint in code.</span></span>  
  
 [<span data-ttu-id="6db47-123">Meta Veri Uç Noktalarını Yayımlama</span><span class="sxs-lookup"><span data-stu-id="6db47-123">Publishing Metadata Endpoints</span></span>](../../../docs/framework/wcf/publishing-metadata-endpoints.md)  
 <span data-ttu-id="6db47-124">Yapılandırma ve kod meta veri uç noktalarını yayımlama meta veri yayımlama işlemini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="6db47-124">Demonstrates how to publish metadata by publishing metadata endpoints in configuration and in code.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="6db47-125">Başvuru</span><span class="sxs-lookup"><span data-stu-id="6db47-125">Reference</span></span>  
 <xref:System.ServiceModel.EndpointAddress>  
  
## <a name="related-sections"></a><span data-ttu-id="6db47-126">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="6db47-126">Related Sections</span></span>  
 [<span data-ttu-id="6db47-127">Temel Programlama Yaşam Döngüsü</span><span class="sxs-lookup"><span data-stu-id="6db47-127">Basic Programming Lifecycle</span></span>](../../../docs/framework/wcf/basic-programming-lifecycle.md)
