---
description: 'Hakkında daha fazla bilgi edinin: Windows Communication Foundation güvenliği'
title: Windows Communication Foundation Güvenliği
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, programming
- security [WCF]
- Windows Communication Foundation, security
ms.assetid: 7ea87fcb-dcfb-4a4a-8b03-6b954575d45b
ms.openlocfilehash: 8cf748504c85844f82f8941be1b60bb29478f730
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99726799"
---
# <a name="windows-communication-foundation-security"></a><span data-ttu-id="6c933-103">Windows Communication Foundation Güvenliği</span><span class="sxs-lookup"><span data-stu-id="6c933-103">Windows Communication Foundation Security</span></span>

<span data-ttu-id="6c933-104">Bu bölümdeki konularda, iletilerin güvenli hale getirilmesine yardımcı olmak için Windows Communication Foundation (WCF) güvenlik özellikleri ve bunların nasıl kullanılacağı açıklanır.</span><span class="sxs-lookup"><span data-stu-id="6c933-104">The topics in this section describe Windows Communication Foundation (WCF) security features and how to use them to help secure messages.</span></span>  
  
 <span data-ttu-id="6c933-105">Windows Server AppFabric ve Security hakkında daha fazla bilgi için bkz. [Windows Server Için güvenlik modeli AppFabric](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="6c933-105">For more information about Windows Server AppFabric and security, see [Security Model for Windows Server AppFabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6c933-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="6c933-106">In This Section</span></span>  

 [<span data-ttu-id="6c933-107">Güvenliğe genel bakış</span><span class="sxs-lookup"><span data-stu-id="6c933-107">Security Overview</span></span>](security-overview.md)  
 <span data-ttu-id="6c933-108">WCF 'deki güvenlik özelliklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="6c933-108">Describes the security features in WCF.</span></span>  
  
 [<span data-ttu-id="6c933-109">Güvenlik Kavramları</span><span class="sxs-lookup"><span data-stu-id="6c933-109">Security Concepts</span></span>](security-concepts.md)  
 <span data-ttu-id="6c933-110">WCF güvenliği içinde kullanılan temel terminolojiyi ve kavramları açıklar.</span><span class="sxs-lookup"><span data-stu-id="6c933-110">Describes the basic terminology and concepts used in WCF security.</span></span>  
  
 [<span data-ttu-id="6c933-111">Ortak Güvenlik Senaryoları</span><span class="sxs-lookup"><span data-stu-id="6c933-111">Common Security Scenarios</span></span>](common-security-scenarios.md)  
 <span data-ttu-id="6c933-112">WCF ile yapılandırabileceğiniz senaryoları ve topolojileri açıklar.</span><span class="sxs-lookup"><span data-stu-id="6c933-112">Describes scenarios and topologies you can configure with WCF.</span></span>  
  
 [<span data-ttu-id="6c933-113">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="6c933-113">Security Behaviors</span></span>](security-behaviors-in-wcf.md)  
 <span data-ttu-id="6c933-114">Kimlik bilgilerini ayarlama gibi güvenliği etkileyen WCF davranışlarına genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c933-114">Provides an overview of WCF behaviors that affect security, such as setting credentials.</span></span>  
  
 [<span data-ttu-id="6c933-115">Bağlamalar ve Güvenlik</span><span class="sxs-lookup"><span data-stu-id="6c933-115">Bindings and Security</span></span>](bindings-and-security.md)  
 <span data-ttu-id="6c933-116">Özel güvenlik bağlamaları oluşturmayı gösteren konular da dahil olmak üzere bağlamaların güvenlik odaklı bir görünümü.</span><span class="sxs-lookup"><span data-stu-id="6c933-116">A security-oriented view of the bindings, including topics that demonstrate how to create custom security bindings.</span></span>  
  
 [<span data-ttu-id="6c933-117">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="6c933-117">Securing Services and Clients</span></span>](securing-services-and-clients.md)  
 <span data-ttu-id="6c933-118">WCF güvenlik özellikleri kullanılarak iletilerin nasıl güvenli hale alınacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="6c933-118">Describes how to secure messages using WCF security features.</span></span>  
  
 [<span data-ttu-id="6c933-119">Kimlik Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="6c933-119">Authentication</span></span>](authentication-in-wcf.md)  
 <span data-ttu-id="6c933-120">Yaygın kimlik doğrulama görevlerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="6c933-120">Demonstrates common authentication tasks.</span></span>  
  
 [<span data-ttu-id="6c933-121">Yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="6c933-121">Authorization</span></span>](authorization-in-wcf.md)  
 <span data-ttu-id="6c933-122">Güvenlik uygulamalarıyla ortak yetkilendirme senaryolarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="6c933-122">Describes common authorization scenarios with security implementations.</span></span>  
  
 [<span data-ttu-id="6c933-123">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="6c933-123">Federation and Issued Tokens</span></span>](federation-and-issued-tokens.md)  
 <span data-ttu-id="6c933-124">Federasyon ve Federasyon sunucularıyla iletişim kuran istemcilerin oluşturulması hakkında temel bilgileri açıklar.</span><span class="sxs-lookup"><span data-stu-id="6c933-124">Describes the basics of federation and how to create clients that communicate with federated servers.</span></span>  
  
 [<span data-ttu-id="6c933-125">Kısmi Güven</span><span class="sxs-lookup"><span data-stu-id="6c933-125">Partial Trust</span></span>](partial-trust.md)  
 <span data-ttu-id="6c933-126">Kısmen güvenilir bir şekilde çalıştırıldığında kısmen güvenilen senaryoların ve WCF kısıtlamalarının nasıl çalıştırılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="6c933-126">Describes how to run partially-trusted scenarios and WCF limitations when running partially trusted.</span></span>  
  
 [<span data-ttu-id="6c933-127">Denetim</span><span class="sxs-lookup"><span data-stu-id="6c933-127">Auditing</span></span>](auditing-security-events.md)  
 <span data-ttu-id="6c933-128">Güvenlik olaylarının nasıl denetleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="6c933-128">Describes how to audit security events.</span></span>  
  
 [<span data-ttu-id="6c933-129">Güvenlik Kılavuzu ve En İyi Uygulamalar</span><span class="sxs-lookup"><span data-stu-id="6c933-129">Security Guidance and Best Practices</span></span>](security-guidance-and-best-practices.md)  
 <span data-ttu-id="6c933-130">Güvenli WCF uygulamaları oluşturmaya yönelik yönergeler.</span><span class="sxs-lookup"><span data-stu-id="6c933-130">Guidelines for creating secure WCF applications.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="6c933-131">Başvuru</span><span class="sxs-lookup"><span data-stu-id="6c933-131">Reference</span></span>  

 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Security>  
  
## <a name="related-sections"></a><span data-ttu-id="6c933-132">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="6c933-132">Related Sections</span></span>  

 [<span data-ttu-id="6c933-133">WCF özellik ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="6c933-133">WCF Feature Details</span></span>](index.md)  
  
 [<span data-ttu-id="6c933-134">Temel WCF Programlama</span><span class="sxs-lookup"><span data-stu-id="6c933-134">Basic WCF Programming</span></span>](../basic-wcf-programming.md)  
  
 [<span data-ttu-id="6c933-135">Başlangıç Öğreticisi</span><span class="sxs-lookup"><span data-stu-id="6c933-135">Getting Started Tutorial</span></span>](../getting-started-tutorial.md)  
  
 [<span data-ttu-id="6c933-136">Kavramsal Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="6c933-136">Conceptual Overview</span></span>](../conceptual-overview.md)  
  
## <a name="see-also"></a><span data-ttu-id="6c933-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6c933-137">See also</span></span>

- [<span data-ttu-id="6c933-138">Uygulamanızı Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="6c933-138">Configuring Your Application</span></span>](../diagnostics/configuring-your-application.md)
