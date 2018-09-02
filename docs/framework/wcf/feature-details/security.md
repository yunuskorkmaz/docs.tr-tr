---
title: Windows Communication Foundation Güvenliği
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, programming
- security [WCF]
- Windows Communication Foundation, security
ms.assetid: 7ea87fcb-dcfb-4a4a-8b03-6b954575d45b
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: a070800ea15c5a7f16b52ca69c7e454c92618e1a
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43384934"
---
# <a name="windows-communication-foundation-security"></a><span data-ttu-id="56538-102">Windows Communication Foundation Güvenliği</span><span class="sxs-lookup"><span data-stu-id="56538-102">Windows Communication Foundation Security</span></span>
<span data-ttu-id="56538-103">Bu bölümdeki konularda, Windows Communication Foundation (WCF) güvenlik özellikleri ve bunları güvenli iletiler yardımcı olmak için nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="56538-103">The topics in this section describe Windows Communication Foundation (WCF) security features and how to use them to help secure messages.</span></span>  
  
 <span data-ttu-id="56538-104">Windows Server AppFabric ve güvenlik hakkında daha fazla bilgi için bkz. [Windows Server AppFabric güvenlik modeli](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)</span><span class="sxs-lookup"><span data-stu-id="56538-104">For more information about Windows Server AppFabric and security, see [Security Model for Windows Server AppFabric](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="56538-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="56538-105">In This Section</span></span>  
 [<span data-ttu-id="56538-106">Güvenliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="56538-106">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 <span data-ttu-id="56538-107">Wcf'de güvenlik özelliklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="56538-107">Describes the security features in WCF.</span></span>  
  
 [<span data-ttu-id="56538-108">Güvenlik Kavramları</span><span class="sxs-lookup"><span data-stu-id="56538-108">Security Concepts</span></span>](../../../../docs/framework/wcf/feature-details/security-concepts.md)  
 <span data-ttu-id="56538-109">Temel terminoloji ve WCF güvenliğinde kullanılan kavramları açıklar.</span><span class="sxs-lookup"><span data-stu-id="56538-109">Describes the basic terminology and concepts used in WCF security.</span></span>  
  
 [<span data-ttu-id="56538-110">Ortak Güvenlik Senaryoları</span><span class="sxs-lookup"><span data-stu-id="56538-110">Common Security Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
 <span data-ttu-id="56538-111">Senaryo ve Topolojilerde WCF ile yapılandırabileceğiniz açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="56538-111">Describes scenarios and topologies you can configure with WCF.</span></span>  
  
 [<span data-ttu-id="56538-112">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="56538-112">Security Behaviors</span></span>](../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 <span data-ttu-id="56538-113">Güvenlik, kimlik bilgilerini ayarlama gibi etkileyen WCF davranışları genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="56538-113">Provides an overview of WCF behaviors that affect security, such as setting credentials.</span></span>  
  
 [<span data-ttu-id="56538-114">Bağlamalar ve Güvenlik</span><span class="sxs-lookup"><span data-stu-id="56538-114">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
 <span data-ttu-id="56538-115">Özel güvenlik bağlamaları oluşturmak nasıl gösteren konular da dahil olmak üzere bağlamaları, güvenlik odaklı görünümünü.</span><span class="sxs-lookup"><span data-stu-id="56538-115">A security-oriented view of the bindings, including topics that demonstrate how to create custom security bindings.</span></span>  
  
 [<span data-ttu-id="56538-116">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="56538-116">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 <span data-ttu-id="56538-117">WCF güvenlik özellikleri kullanarak iletileri güvenli hale getirmek açıklar.</span><span class="sxs-lookup"><span data-stu-id="56538-117">Describes how to secure messages using WCF security features.</span></span>  
  
 [<span data-ttu-id="56538-118">Kimlik Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="56538-118">Authentication</span></span>](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
 <span data-ttu-id="56538-119">Genel kimlik doğrulama görevlerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="56538-119">Demonstrates common authentication tasks.</span></span>  
  
 [<span data-ttu-id="56538-120">Yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="56538-120">Authorization</span></span>](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
 <span data-ttu-id="56538-121">Güvenlik uygulamaları ile yetkilendirme senaryoları açıklar.</span><span class="sxs-lookup"><span data-stu-id="56538-121">Describes common authorization scenarios with security implementations.</span></span>  
  
 [<span data-ttu-id="56538-122">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="56538-122">Federation and Issued Tokens</span></span>](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 <span data-ttu-id="56538-123">Federasyon ve Federasyon sunucuları ile iletişim kuran istemciler oluşturma hakkındaki temel bilgileri açıklar.</span><span class="sxs-lookup"><span data-stu-id="56538-123">Describes the basics of federation and how to create clients that communicate with federated servers.</span></span>  
  
 [<span data-ttu-id="56538-124">Kısmi Güven</span><span class="sxs-lookup"><span data-stu-id="56538-124">Partial Trust</span></span>](../../../../docs/framework/wcf/feature-details/partial-trust.md)  
 <span data-ttu-id="56538-125">Kısmen güvenilen senaryoları ve WCF sınırlamalar kısmen güvenilen çalıştırırken çalıştırma işlemi açıklanır.</span><span class="sxs-lookup"><span data-stu-id="56538-125">Describes how to run partially-trusted scenarios and WCF limitations when running partially trusted.</span></span>  
  
 [<span data-ttu-id="56538-126">Denetim</span><span class="sxs-lookup"><span data-stu-id="56538-126">Auditing</span></span>](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)  
 <span data-ttu-id="56538-127">Güvenlik olaylarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="56538-127">Describes how to audit security events.</span></span>  
  
 [<span data-ttu-id="56538-128">Güvenlik Kılavuzu ve En İyi Uygulamalar</span><span class="sxs-lookup"><span data-stu-id="56538-128">Security Guidance and Best Practices</span></span>](../../../../docs/framework/wcf/feature-details/security-guidance-and-best-practices.md)  
 <span data-ttu-id="56538-129">Güvenli WCF uygulamaları oluşturmaya yönelik yönergeler.</span><span class="sxs-lookup"><span data-stu-id="56538-129">Guidelines for creating secure WCF applications.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="56538-130">Başvuru</span><span class="sxs-lookup"><span data-stu-id="56538-130">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Security>  
  
## <a name="related-sections"></a><span data-ttu-id="56538-131">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="56538-131">Related Sections</span></span>  
 [<span data-ttu-id="56538-132">WCF Özellik Ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="56538-132">WCF Feature Details</span></span>](../../../../docs/framework/wcf/feature-details/index.md)  
  
 [<span data-ttu-id="56538-133">Temel WCF Programlama</span><span class="sxs-lookup"><span data-stu-id="56538-133">Basic WCF Programming</span></span>](../../../../docs/framework/wcf/basic-wcf-programming.md)  
  
 [<span data-ttu-id="56538-134">Başlangıç Öğreticisi</span><span class="sxs-lookup"><span data-stu-id="56538-134">Getting Started Tutorial</span></span>](../../../../docs/framework/wcf/getting-started-tutorial.md)  
  
 [<span data-ttu-id="56538-135">Kavramsal Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="56538-135">Conceptual Overview</span></span>](../../../../docs/framework/wcf/conceptual-overview.md)  
  
## <a name="see-also"></a><span data-ttu-id="56538-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="56538-136">See Also</span></span>  
 [<span data-ttu-id="56538-137">Uygulamanızı Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="56538-137">Configuring Your Application</span></span>](../../../../docs/framework/wcf/diagnostics/configuring-your-application.md)
