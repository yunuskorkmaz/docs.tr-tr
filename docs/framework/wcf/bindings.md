---
description: 'Daha fazla bilgi edinin: Windows Communication Foundation Bağlamaları'
title: Windows Communication Foundation Bağlamaları
ms.date: 03/30/2017
helpviewer_keywords:
- bindings [WCF]
ms.assetid: 845df323-be53-4848-92ef-ba67a406484d
ms.openlocfilehash: 1d21fb9593917b50a22bd0b0bf0f4506fd99b8df
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781174"
---
# <a name="windows-communication-foundation-bindings"></a><span data-ttu-id="cb7c2-103">Windows Communication Foundation Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="cb7c2-103">Windows Communication Foundation Bindings</span></span>

<span data-ttu-id="cb7c2-104">Bağlamalar Windows Communication Foundation (WCF) hizmet uç noktasının diğer uç noktalarla nasıl iletişim kuracağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="cb7c2-104">Bindings specify how a Windows Communication Foundation (WCF) service endpoint communicates with other endpoints.</span></span> <span data-ttu-id="cb7c2-105">En temel tarafında, bir bağlama kullanılacak taşıma (örneğin, HTTP veya TCP) belirtmelidir.</span><span class="sxs-lookup"><span data-stu-id="cb7c2-105">At its most basic, a binding must specify the transport (for example, HTTP or TCP) to use.</span></span> <span data-ttu-id="cb7c2-106">Ayrıca, güvenlik ve işlem desteği gibi diğer özellikleri bağlamalar aracılığıyla da ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cb7c2-106">You can also set other characteristics, such as security and transaction support, through bindings.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cb7c2-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="cb7c2-107">In This Section</span></span>  

 [<span data-ttu-id="cb7c2-108">WCF Bağlamalarına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="cb7c2-108">WCF Bindings Overview</span></span>](bindings-overview.md)  
 <span data-ttu-id="cb7c2-109">WCF bağlamalarının ne yaptığını, sistemin sağladığı bağlamaları ve bunları nasıl tanımlayacağınızı veya değiştirebileceğinize genel bakış.</span><span class="sxs-lookup"><span data-stu-id="cb7c2-109">Overview of what WCF bindings do, what bindings the system provides, and how you can define or modify them.</span></span>  
  
 [<span data-ttu-id="cb7c2-110">Sistem Tarafından Sağlanan Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="cb7c2-110">System-Provided Bindings</span></span>](system-provided-bindings.md)  
 <span data-ttu-id="cb7c2-111">WCF 'ye eklenen bağlamaların listesi.</span><span class="sxs-lookup"><span data-stu-id="cb7c2-111">A list of bindings included with WCF.</span></span> <span data-ttu-id="cb7c2-112">Bu bağlamalar, güvenlik ve ileti örüntülerinin çoğunluğunun çoğunu kapsar.</span><span class="sxs-lookup"><span data-stu-id="cb7c2-112">These bindings cover the majority of security and message pattern requirements.</span></span>  
  
 [<span data-ttu-id="cb7c2-113">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="cb7c2-113">Using Bindings to Configure Services and Clients</span></span>](using-bindings-to-configure-services-and-clients.md)  
 <span data-ttu-id="cb7c2-114">WCF bağlaması, istemcilerin hizmet uç noktalarına bağlanmak için kullanması gereken önemli bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="cb7c2-114">A WCF binding contains important information that clients must use to connect to service endpoints.</span></span>  
  
 [<span data-ttu-id="cb7c2-115">Hizmetler için Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="cb7c2-115">Configuring Bindings for Services</span></span>](configuring-bindings-for-wcf-services.md)  
 <span data-ttu-id="cb7c2-116">Yapılandırma, yöneticilerin ve yükleyicilerin hizmet uç noktaları bağlamalarını özelleştirmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="cb7c2-116">Configuration enables administrators and installers to customize the bindings for service endpoints.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="cb7c2-117">Başvuru</span><span class="sxs-lookup"><span data-stu-id="cb7c2-117">Reference</span></span>  

 <xref:System.ServiceModel.Channels>  
  
## <a name="related-sections"></a><span data-ttu-id="cb7c2-118">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="cb7c2-118">Related Sections</span></span>  

 [<span data-ttu-id="cb7c2-119">Uç Noktalar: Adresler, Bağlamalar ve Sözleşmeler</span><span class="sxs-lookup"><span data-stu-id="cb7c2-119">Endpoints: Addresses, Bindings, and Contracts</span></span>](./feature-details/endpoints-addresses-bindings-and-contracts.md)  
  
 [<span data-ttu-id="cb7c2-120">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="cb7c2-120">Bindings</span></span>](./feature-details/bindings.md)  
  
## <a name="see-also"></a><span data-ttu-id="cb7c2-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cb7c2-121">See also</span></span>

- [<span data-ttu-id="cb7c2-122">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="cb7c2-122">Custom Bindings</span></span>](./extending/custom-bindings.md)
