---
title: Windows Communication Foundation Güvenliği
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, programming
- security [WCF]
- Windows Communication Foundation, security
ms.assetid: 7ea87fcb-dcfb-4a4a-8b03-6b954575d45b
ms.openlocfilehash: 58bec40f197dd1f2b104607a65c3ad456b95f69d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59118202"
---
# <a name="windows-communication-foundation-security"></a><span data-ttu-id="0bcb0-102">Windows Communication Foundation Güvenliği</span><span class="sxs-lookup"><span data-stu-id="0bcb0-102">Windows Communication Foundation Security</span></span>
<span data-ttu-id="0bcb0-103">Bu bölümdeki konularda, Windows Communication Foundation (WCF) güvenlik özellikleri ve bunları güvenli iletiler yardımcı olmak için nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="0bcb0-103">The topics in this section describe Windows Communication Foundation (WCF) security features and how to use them to help secure messages.</span></span>  
  
 <span data-ttu-id="0bcb0-104">Windows Server AppFabric ve güvenlik hakkında daha fazla bilgi için bkz. [Windows Server AppFabric güvenlik modeli](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)</span><span class="sxs-lookup"><span data-stu-id="0bcb0-104">For more information about Windows Server AppFabric and security, see [Security Model for Windows Server AppFabric](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0bcb0-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="0bcb0-105">In This Section</span></span>  
 [<span data-ttu-id="0bcb0-106">Güvenlik Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="0bcb0-106">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 <span data-ttu-id="0bcb0-107">Wcf'de güvenlik özelliklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="0bcb0-107">Describes the security features in WCF.</span></span>  
  
 [<span data-ttu-id="0bcb0-108">Güvenlik Kavramları</span><span class="sxs-lookup"><span data-stu-id="0bcb0-108">Security Concepts</span></span>](../../../../docs/framework/wcf/feature-details/security-concepts.md)  
 <span data-ttu-id="0bcb0-109">Temel terminoloji ve WCF güvenliğinde kullanılan kavramları açıklar.</span><span class="sxs-lookup"><span data-stu-id="0bcb0-109">Describes the basic terminology and concepts used in WCF security.</span></span>  
  
 [<span data-ttu-id="0bcb0-110">Ortak Güvenlik Senaryoları</span><span class="sxs-lookup"><span data-stu-id="0bcb0-110">Common Security Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
 <span data-ttu-id="0bcb0-111">Senaryo ve Topolojilerde WCF ile yapılandırabileceğiniz açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0bcb0-111">Describes scenarios and topologies you can configure with WCF.</span></span>  
  
 [<span data-ttu-id="0bcb0-112">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="0bcb0-112">Security Behaviors</span></span>](../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 <span data-ttu-id="0bcb0-113">Güvenlik, kimlik bilgilerini ayarlama gibi etkileyen WCF davranışları genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="0bcb0-113">Provides an overview of WCF behaviors that affect security, such as setting credentials.</span></span>  
  
 [<span data-ttu-id="0bcb0-114">Bağlamalar ve Güvenlik</span><span class="sxs-lookup"><span data-stu-id="0bcb0-114">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
 <span data-ttu-id="0bcb0-115">Özel güvenlik bağlamaları oluşturmak nasıl gösteren konular da dahil olmak üzere bağlamaları, güvenlik odaklı görünümünü.</span><span class="sxs-lookup"><span data-stu-id="0bcb0-115">A security-oriented view of the bindings, including topics that demonstrate how to create custom security bindings.</span></span>  
  
 [<span data-ttu-id="0bcb0-116">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="0bcb0-116">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 <span data-ttu-id="0bcb0-117">WCF güvenlik özellikleri kullanarak iletileri güvenli hale getirmek açıklar.</span><span class="sxs-lookup"><span data-stu-id="0bcb0-117">Describes how to secure messages using WCF security features.</span></span>  
  
 [<span data-ttu-id="0bcb0-118">Kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="0bcb0-118">Authentication</span></span>](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
 <span data-ttu-id="0bcb0-119">Genel kimlik doğrulama görevlerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0bcb0-119">Demonstrates common authentication tasks.</span></span>  
  
 [<span data-ttu-id="0bcb0-120">Yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="0bcb0-120">Authorization</span></span>](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
 <span data-ttu-id="0bcb0-121">Güvenlik uygulamaları ile yetkilendirme senaryoları açıklar.</span><span class="sxs-lookup"><span data-stu-id="0bcb0-121">Describes common authorization scenarios with security implementations.</span></span>  
  
 [<span data-ttu-id="0bcb0-122">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="0bcb0-122">Federation and Issued Tokens</span></span>](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 <span data-ttu-id="0bcb0-123">Federasyon ve Federasyon sunucuları ile iletişim kuran istemciler oluşturma hakkındaki temel bilgileri açıklar.</span><span class="sxs-lookup"><span data-stu-id="0bcb0-123">Describes the basics of federation and how to create clients that communicate with federated servers.</span></span>  
  
 [<span data-ttu-id="0bcb0-124">Kısmi Güven</span><span class="sxs-lookup"><span data-stu-id="0bcb0-124">Partial Trust</span></span>](../../../../docs/framework/wcf/feature-details/partial-trust.md)  
 <span data-ttu-id="0bcb0-125">Kısmen güvenilen senaryoları ve WCF sınırlamalar kısmen güvenilen çalıştırırken çalıştırma işlemi açıklanır.</span><span class="sxs-lookup"><span data-stu-id="0bcb0-125">Describes how to run partially-trusted scenarios and WCF limitations when running partially trusted.</span></span>  
  
 [<span data-ttu-id="0bcb0-126">Denetim</span><span class="sxs-lookup"><span data-stu-id="0bcb0-126">Auditing</span></span>](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)  
 <span data-ttu-id="0bcb0-127">Güvenlik olaylarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="0bcb0-127">Describes how to audit security events.</span></span>  
  
 [<span data-ttu-id="0bcb0-128">Güvenlik Kılavuzu ve En İyi Uygulamalar</span><span class="sxs-lookup"><span data-stu-id="0bcb0-128">Security Guidance and Best Practices</span></span>](../../../../docs/framework/wcf/feature-details/security-guidance-and-best-practices.md)  
 <span data-ttu-id="0bcb0-129">Güvenli WCF uygulamaları oluşturmaya yönelik yönergeler.</span><span class="sxs-lookup"><span data-stu-id="0bcb0-129">Guidelines for creating secure WCF applications.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="0bcb0-130">Başvuru</span><span class="sxs-lookup"><span data-stu-id="0bcb0-130">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Security>  
  
## <a name="related-sections"></a><span data-ttu-id="0bcb0-131">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="0bcb0-131">Related Sections</span></span>  
 [<span data-ttu-id="0bcb0-132">WCF Özellik Ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="0bcb0-132">WCF Feature Details</span></span>](../../../../docs/framework/wcf/feature-details/index.md)  
  
 [<span data-ttu-id="0bcb0-133">Temel WCF Programlama</span><span class="sxs-lookup"><span data-stu-id="0bcb0-133">Basic WCF Programming</span></span>](../../../../docs/framework/wcf/basic-wcf-programming.md)  
  
 [<span data-ttu-id="0bcb0-134">Başlangıç Öğreticisi</span><span class="sxs-lookup"><span data-stu-id="0bcb0-134">Getting Started Tutorial</span></span>](../../../../docs/framework/wcf/getting-started-tutorial.md)  
  
 [<span data-ttu-id="0bcb0-135">Kavramsal Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="0bcb0-135">Conceptual Overview</span></span>](../../../../docs/framework/wcf/conceptual-overview.md)  
  
## <a name="see-also"></a><span data-ttu-id="0bcb0-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0bcb0-136">See also</span></span>

- [<span data-ttu-id="0bcb0-137">Uygulamanızı Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="0bcb0-137">Configuring Your Application</span></span>](../../../../docs/framework/wcf/diagnostics/configuring-your-application.md)
