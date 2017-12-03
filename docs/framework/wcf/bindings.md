---
title: "Windows Communication Foundation Bağlamaları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: bindings [WCF]
ms.assetid: 845df323-be53-4848-92ef-ba67a406484d
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 36924bdc79a9789a991befb53c0025b7ea1fd601
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="windows-communication-foundation-bindings"></a><span data-ttu-id="a4f8f-102">Windows Communication Foundation Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="a4f8f-102">Windows Communication Foundation Bindings</span></span>
<span data-ttu-id="a4f8f-103">Bağlamaları belirtin nasıl bir [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] Hizmeti uç noktası diğer uç ile iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="a4f8f-103">Bindings specify how a [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] service endpoint communicates with other endpoints.</span></span> <span data-ttu-id="a4f8f-104">Kendi en temel sırasında bir bağlama kullanılacak Aktarım (örneğin, HTTP veya TCP) belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a4f8f-104">At its most basic, a binding must specify the transport (for example, HTTP or TCP) to use.</span></span> <span data-ttu-id="a4f8f-105">Güvenlik ve işlem, bağlamaları desteği gibi diğer özellikleri de ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a4f8f-105">You can also set other characteristics, such as security and transaction support, through bindings.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a4f8f-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="a4f8f-106">In This Section</span></span>  
 [<span data-ttu-id="a4f8f-107">WCF bağlamaları genel bakış</span><span class="sxs-lookup"><span data-stu-id="a4f8f-107">WCF Bindings Overview</span></span>](../../../docs/framework/wcf/bindings-overview.md)  
 <span data-ttu-id="a4f8f-108">Ne genel bakış [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] do bağlamaları, hangi bağlamaları sistemi sağlar ve nasıl tanımlamak veya bunları değiştirmek.</span><span class="sxs-lookup"><span data-stu-id="a4f8f-108">Overview of what [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] bindings do, what bindings the system provides, and how you can define or modify them.</span></span>  
  
 [<span data-ttu-id="a4f8f-109">Sistem tarafından sağlanan bağlamalar</span><span class="sxs-lookup"><span data-stu-id="a4f8f-109">System-Provided Bindings</span></span>](../../../docs/framework/wcf/system-provided-bindings.md)  
 <span data-ttu-id="a4f8f-110">İle birlikte gelen bağlamaları listesini [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a4f8f-110">A list of bindings included with [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="a4f8f-111">Bu bağlamaların güvenlik ve ileti düzeni gereksinimleri çoğunu kapsar.</span><span class="sxs-lookup"><span data-stu-id="a4f8f-111">These bindings cover the majority of security and message pattern requirements.</span></span>  
  
 [<span data-ttu-id="a4f8f-112">Hizmetler ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="a4f8f-112">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 <span data-ttu-id="a4f8f-113">A [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] bağlama istemciler hizmet uç noktalarına bağlanmak için kullanması gereken önemli bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="a4f8f-113">A [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] binding contains important information that clients must use to connect to service endpoints.</span></span>  
  
 [<span data-ttu-id="a4f8f-114">Hizmetler için bağlamaları yapılandırma</span><span class="sxs-lookup"><span data-stu-id="a4f8f-114">Configuring Bindings for Services</span></span>](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md)  
 <span data-ttu-id="a4f8f-115">Yapılandırma Yöneticiler ve yükleyicileri hizmet uç noktaları için olan bağlamaları özelleştirmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="a4f8f-115">Configuration enables administrators and installers to customize the bindings for service endpoints.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="a4f8f-116">Başvuru</span><span class="sxs-lookup"><span data-stu-id="a4f8f-116">Reference</span></span>  
 <xref:System.ServiceModel.Channels>  
  
## <a name="related-sections"></a><span data-ttu-id="a4f8f-117">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="a4f8f-117">Related Sections</span></span>  
 [<span data-ttu-id="a4f8f-118">Uç noktalar: Adresler, bağlamalar ve sözleşmeler</span><span class="sxs-lookup"><span data-stu-id="a4f8f-118">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)  
  
 [<span data-ttu-id="a4f8f-119">Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="a4f8f-119">Bindings</span></span>](../../../docs/framework/wcf/feature-details/bindings.md)  
  
## <a name="see-also"></a><span data-ttu-id="a4f8f-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a4f8f-120">See Also</span></span>  
 [<span data-ttu-id="a4f8f-121">Özel bağlamalar</span><span class="sxs-lookup"><span data-stu-id="a4f8f-121">Custom Bindings</span></span>](../../../docs/framework/wcf/extending/custom-bindings.md)
