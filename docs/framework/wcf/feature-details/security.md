---
title: Windows Communication Foundation Güvenliği
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Windows Communication Foundation, programming
- security [WCF]
- Windows Communication Foundation, security
ms.assetid: 7ea87fcb-dcfb-4a4a-8b03-6b954575d45b
caps.latest.revision: 21
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: 6b93bfff2cd97e10d9c0dba4373839337f36aacb
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="windows-communication-foundation-security"></a><span data-ttu-id="9368f-102">Windows Communication Foundation Güvenliği</span><span class="sxs-lookup"><span data-stu-id="9368f-102">Windows Communication Foundation Security</span></span>
<span data-ttu-id="9368f-103">Bu bölümdeki konularda açıklanmaktadır [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] güvenlik özellikleri ve bunları güvenli iletiler yardımcı olmak için kullanma.</span><span class="sxs-lookup"><span data-stu-id="9368f-103">The topics in this section describe [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] security features and how to use them to help secure messages.</span></span>  
  
 <span data-ttu-id="9368f-104">Windows Server AppFabric ve güvenlik hakkında daha fazla bilgi için bkz: [Windows Server AppFabric güvenlik modeli](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)</span><span class="sxs-lookup"><span data-stu-id="9368f-104">For more information about Windows Server AppFabric and security, see [Security Model for Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9368f-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="9368f-105">In This Section</span></span>  
 [<span data-ttu-id="9368f-106">Güvenliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9368f-106">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 <span data-ttu-id="9368f-107">Güvenlik özellikleri açıklar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9368f-107">Describes the security features in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 [<span data-ttu-id="9368f-108">Güvenlik Kavramları</span><span class="sxs-lookup"><span data-stu-id="9368f-108">Security Concepts</span></span>](../../../../docs/framework/wcf/feature-details/security-concepts.md)  
 <span data-ttu-id="9368f-109">Temel terimler ve kullanılan kavramlar açıklanmaktadır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] güvenlik.</span><span class="sxs-lookup"><span data-stu-id="9368f-109">Describes the basic terminology and concepts used in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] security.</span></span>  
  
 [<span data-ttu-id="9368f-110">Ortak Güvenlik Senaryoları</span><span class="sxs-lookup"><span data-stu-id="9368f-110">Common Security Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
 <span data-ttu-id="9368f-111">Senaryolar ve Topolojileri ile yapılandırabileceğiniz açıklanmıştır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9368f-111">Describes scenarios and topologies you can configure with [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 [<span data-ttu-id="9368f-112">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="9368f-112">Security Behaviors</span></span>](../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 <span data-ttu-id="9368f-113">Kimlik bilgilerini ayarlama gibi güvenliğini etkileyen WCF davranışları genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="9368f-113">Provides an overview of WCF behaviors that affect security, such as setting credentials.</span></span>  
  
 [<span data-ttu-id="9368f-114">Bağlamalar ve Güvenlik</span><span class="sxs-lookup"><span data-stu-id="9368f-114">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
 <span data-ttu-id="9368f-115">Özel güvenlik bağlamaları oluşturmak nasıl ekleyebileceğiniz gösterilmektedir konuları dahil olmak üzere bağlamaları, güvenlik odaklı görünümünü.</span><span class="sxs-lookup"><span data-stu-id="9368f-115">A security-oriented view of the bindings, including topics that demonstrate how to create custom security bindings.</span></span>  
  
 [<span data-ttu-id="9368f-116">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="9368f-116">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 <span data-ttu-id="9368f-117">Kullanarak iletileri güvenli hale getirmek açıklar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] güvenlik özellikleri.</span><span class="sxs-lookup"><span data-stu-id="9368f-117">Describes how to secure messages using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] security features.</span></span>  
  
 [<span data-ttu-id="9368f-118">Kimlik Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="9368f-118">Authentication</span></span>](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
 <span data-ttu-id="9368f-119">Genel kimlik doğrulama görevlerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="9368f-119">Demonstrates common authentication tasks.</span></span>  
  
 [<span data-ttu-id="9368f-120">Yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="9368f-120">Authorization</span></span>](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
 <span data-ttu-id="9368f-121">Güvenlik uygulamalarıyla birlikte genel yetkilendirme senaryolar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9368f-121">Describes common authorization scenarios with security implementations.</span></span>  
  
 [<span data-ttu-id="9368f-122">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="9368f-122">Federation and Issued Tokens</span></span>](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 <span data-ttu-id="9368f-123">Federasyon ve Federasyon sunucusu ile iletişim kuran istemciler oluşturmak nasıl temelleri açıklanır.</span><span class="sxs-lookup"><span data-stu-id="9368f-123">Describes the basics of federation and how to create clients that communicate with federated servers.</span></span>  
  
 [<span data-ttu-id="9368f-124">Kısmi Güven</span><span class="sxs-lookup"><span data-stu-id="9368f-124">Partial Trust</span></span>](../../../../docs/framework/wcf/feature-details/partial-trust.md)  
 <span data-ttu-id="9368f-125">Kısmen güvenilen senaryoları çalıştırılacağını açıklar ve [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kısmen güvenilen çalıştırırken sınırlamaları.</span><span class="sxs-lookup"><span data-stu-id="9368f-125">Describes how to run partially-trusted scenarios and [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] limitations when running partially trusted.</span></span>  
  
 [<span data-ttu-id="9368f-126">Denetim</span><span class="sxs-lookup"><span data-stu-id="9368f-126">Auditing</span></span>](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)  
 <span data-ttu-id="9368f-127">Güvenlik olaylarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="9368f-127">Describes how to audit security events.</span></span>  
  
 [<span data-ttu-id="9368f-128">Güvenlik Kılavuzu ve En İyi Uygulamalar</span><span class="sxs-lookup"><span data-stu-id="9368f-128">Security Guidance and Best Practices</span></span>](../../../../docs/framework/wcf/feature-details/security-guidance-and-best-practices.md)  
 <span data-ttu-id="9368f-129">Güvenli oluşturma yönergeleri [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulamalar.</span><span class="sxs-lookup"><span data-stu-id="9368f-129">Guidelines for creating secure [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="9368f-130">Başvuru</span><span class="sxs-lookup"><span data-stu-id="9368f-130">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Security>  
  
## <a name="related-sections"></a><span data-ttu-id="9368f-131">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="9368f-131">Related Sections</span></span>  
 [<span data-ttu-id="9368f-132">WCF Özellik Ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="9368f-132">WCF Feature Details</span></span>](../../../../docs/framework/wcf/feature-details/index.md)  
  
 [<span data-ttu-id="9368f-133">Temel WCF Programlama</span><span class="sxs-lookup"><span data-stu-id="9368f-133">Basic WCF Programming</span></span>](../../../../docs/framework/wcf/basic-wcf-programming.md)  
  
 [<span data-ttu-id="9368f-134">Başlangıç Öğreticisi</span><span class="sxs-lookup"><span data-stu-id="9368f-134">Getting Started Tutorial</span></span>](../../../../docs/framework/wcf/getting-started-tutorial.md)  
  
 [<span data-ttu-id="9368f-135">Kavramsal Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9368f-135">Conceptual Overview</span></span>](../../../../docs/framework/wcf/conceptual-overview.md)  
  
## <a name="see-also"></a><span data-ttu-id="9368f-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9368f-136">See Also</span></span>  
 [<span data-ttu-id="9368f-137">Uygulamanızı Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="9368f-137">Configuring Your Application</span></span>](../../../../docs/framework/wcf/diagnostics/configuring-your-application.md)
