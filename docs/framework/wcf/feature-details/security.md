---
title: Windows Communication Foundation Güvenliği
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, programming
- security [WCF]
- Windows Communication Foundation, security
ms.assetid: 7ea87fcb-dcfb-4a4a-8b03-6b954575d45b
ms.openlocfilehash: 0f79ac28af45e8c05922373955c5317095d2c682
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744639"
---
# <a name="windows-communication-foundation-security"></a><span data-ttu-id="b43ed-102">Windows Communication Foundation Güvenliği</span><span class="sxs-lookup"><span data-stu-id="b43ed-102">Windows Communication Foundation Security</span></span>
<span data-ttu-id="b43ed-103">Bu bölümdeki konularda, iletilerin güvenli hale getirilmesine yardımcı olmak için Windows Communication Foundation (WCF) güvenlik özellikleri ve bunların nasıl kullanılacağı açıklanır.</span><span class="sxs-lookup"><span data-stu-id="b43ed-103">The topics in this section describe Windows Communication Foundation (WCF) security features and how to use them to help secure messages.</span></span>  
  
 <span data-ttu-id="b43ed-104">Windows Server AppFabric ve Security hakkında daha fazla bilgi için bkz. [Windows Server Için güvenlik modeli AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="b43ed-104">For more information about Windows Server AppFabric and security, see [Security Model for Windows Server AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b43ed-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="b43ed-105">In This Section</span></span>  
 [<span data-ttu-id="b43ed-106">Güvenliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b43ed-106">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 <span data-ttu-id="b43ed-107">WCF 'deki güvenlik özelliklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="b43ed-107">Describes the security features in WCF.</span></span>  
  
 [<span data-ttu-id="b43ed-108">Güvenlik Kavramları</span><span class="sxs-lookup"><span data-stu-id="b43ed-108">Security Concepts</span></span>](../../../../docs/framework/wcf/feature-details/security-concepts.md)  
 <span data-ttu-id="b43ed-109">WCF güvenliği içinde kullanılan temel terminolojiyi ve kavramları açıklar.</span><span class="sxs-lookup"><span data-stu-id="b43ed-109">Describes the basic terminology and concepts used in WCF security.</span></span>  
  
 [<span data-ttu-id="b43ed-110">Ortak Güvenlik Senaryoları</span><span class="sxs-lookup"><span data-stu-id="b43ed-110">Common Security Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
 <span data-ttu-id="b43ed-111">WCF ile yapılandırabileceğiniz senaryoları ve topolojileri açıklar.</span><span class="sxs-lookup"><span data-stu-id="b43ed-111">Describes scenarios and topologies you can configure with WCF.</span></span>  
  
 [<span data-ttu-id="b43ed-112">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="b43ed-112">Security Behaviors</span></span>](../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 <span data-ttu-id="b43ed-113">Kimlik bilgilerini ayarlama gibi güvenliği etkileyen WCF davranışlarına genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="b43ed-113">Provides an overview of WCF behaviors that affect security, such as setting credentials.</span></span>  
  
 [<span data-ttu-id="b43ed-114">Bağlamalar ve Güvenlik</span><span class="sxs-lookup"><span data-stu-id="b43ed-114">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
 <span data-ttu-id="b43ed-115">Özel güvenlik bağlamaları oluşturmayı gösteren konular da dahil olmak üzere bağlamaların güvenlik odaklı bir görünümü.</span><span class="sxs-lookup"><span data-stu-id="b43ed-115">A security-oriented view of the bindings, including topics that demonstrate how to create custom security bindings.</span></span>  
  
 [<span data-ttu-id="b43ed-116">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="b43ed-116">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 <span data-ttu-id="b43ed-117">WCF güvenlik özellikleri kullanılarak iletilerin nasıl güvenli hale alınacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="b43ed-117">Describes how to secure messages using WCF security features.</span></span>  
  
 [<span data-ttu-id="b43ed-118">Kimlik Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="b43ed-118">Authentication</span></span>](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
 <span data-ttu-id="b43ed-119">Yaygın kimlik doğrulama görevlerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b43ed-119">Demonstrates common authentication tasks.</span></span>  
  
 [<span data-ttu-id="b43ed-120">Yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="b43ed-120">Authorization</span></span>](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
 <span data-ttu-id="b43ed-121">Güvenlik uygulamalarıyla ortak yetkilendirme senaryolarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="b43ed-121">Describes common authorization scenarios with security implementations.</span></span>  
  
 [<span data-ttu-id="b43ed-122">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="b43ed-122">Federation and Issued Tokens</span></span>](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 <span data-ttu-id="b43ed-123">Federasyon ve Federasyon sunucularıyla iletişim kuran istemcilerin oluşturulması hakkında temel bilgileri açıklar.</span><span class="sxs-lookup"><span data-stu-id="b43ed-123">Describes the basics of federation and how to create clients that communicate with federated servers.</span></span>  
  
 [<span data-ttu-id="b43ed-124">Kısmi Güven</span><span class="sxs-lookup"><span data-stu-id="b43ed-124">Partial Trust</span></span>](../../../../docs/framework/wcf/feature-details/partial-trust.md)  
 <span data-ttu-id="b43ed-125">Kısmen güvenilir bir şekilde çalıştırıldığında kısmen güvenilen senaryoların ve WCF kısıtlamalarının nasıl çalıştırılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="b43ed-125">Describes how to run partially-trusted scenarios and WCF limitations when running partially trusted.</span></span>  
  
 [<span data-ttu-id="b43ed-126">Denetim</span><span class="sxs-lookup"><span data-stu-id="b43ed-126">Auditing</span></span>](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)  
 <span data-ttu-id="b43ed-127">Güvenlik olaylarının nasıl denetleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="b43ed-127">Describes how to audit security events.</span></span>  
  
 [<span data-ttu-id="b43ed-128">Güvenlik Kılavuzu ve En İyi Uygulamalar</span><span class="sxs-lookup"><span data-stu-id="b43ed-128">Security Guidance and Best Practices</span></span>](../../../../docs/framework/wcf/feature-details/security-guidance-and-best-practices.md)  
 <span data-ttu-id="b43ed-129">Güvenli WCF uygulamaları oluşturmaya yönelik yönergeler.</span><span class="sxs-lookup"><span data-stu-id="b43ed-129">Guidelines for creating secure WCF applications.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="b43ed-130">Başvuru</span><span class="sxs-lookup"><span data-stu-id="b43ed-130">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Security>  
  
## <a name="related-sections"></a><span data-ttu-id="b43ed-131">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="b43ed-131">Related Sections</span></span>  
 [<span data-ttu-id="b43ed-132">WCF Özellik Ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="b43ed-132">WCF Feature Details</span></span>](../../../../docs/framework/wcf/feature-details/index.md)  
  
 [<span data-ttu-id="b43ed-133">Temel WCF Programlama</span><span class="sxs-lookup"><span data-stu-id="b43ed-133">Basic WCF Programming</span></span>](../../../../docs/framework/wcf/basic-wcf-programming.md)  
  
 [<span data-ttu-id="b43ed-134">Başlangıç Öğreticisi</span><span class="sxs-lookup"><span data-stu-id="b43ed-134">Getting Started Tutorial</span></span>](../../../../docs/framework/wcf/getting-started-tutorial.md)  
  
 [<span data-ttu-id="b43ed-135">Kavramsal Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b43ed-135">Conceptual Overview</span></span>](../../../../docs/framework/wcf/conceptual-overview.md)  
  
## <a name="see-also"></a><span data-ttu-id="b43ed-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b43ed-136">See also</span></span>

- [<span data-ttu-id="b43ed-137">Uygulamanızı Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b43ed-137">Configuring Your Application</span></span>](../../../../docs/framework/wcf/diagnostics/configuring-your-application.md)
