---
title: Hizmet ve İstemcileri Güvenli Hale Getirme
ms.date: 03/30/2017
helpviewer_keywords:
- message security [WCF]
ms.assetid: e681f3bd-0c09-4a58-b0e4-0ecbdf1aa6c7
author: BrucePerlerMS
ms.openlocfilehash: 111a0dd003b0427490b498f895a7e526bafb52b7
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47157603"
---
# <a name="securing-services-and-clients"></a><span data-ttu-id="74d73-102">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="74d73-102">Securing Services and Clients</span></span>
<span data-ttu-id="74d73-103">Bu bölümdeki bilgiler, Windows Communication Foundation (WCF) güvenlik programlama üzerinde odaklanır.</span><span class="sxs-lookup"><span data-stu-id="74d73-103">The information in this section focuses on programming security in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="74d73-104">Genellikle, bu uygun bir sistem tarafından sağlanan bağlaması, güvenlik öğesinin özelliklerini ayarlama ve sonra nasıl kimlik bilgilerini kullanmak için hizmet veya istemci tarafından alınan yöneten hizmet davranışları özelliklerini ayarlayarak seçerek içerir.</span><span class="sxs-lookup"><span data-stu-id="74d73-104">Generally, this includes selecting an appropriate system-provided binding, setting the properties of the security element, and then setting properties of the service behaviors that govern how credentials are retrieved for use by either the service or the client.</span></span> <span data-ttu-id="74d73-105">Gösterildiği gibi güvenlik kullanıcıların çoğunun gereksinimlerine yönelik çoğu senaryo için bu tekniklerin ele [ortak güvenlik senaryoları](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md).</span><span class="sxs-lookup"><span data-stu-id="74d73-105">These techniques cover the security requirements of most users for most scenarios, as shown in [Common Security Scenarios](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md).</span></span> <span data-ttu-id="74d73-106">Daha fazla özellik senaryonuz gerektiriyorsa, öncelikle görmek [özel bağlamalarla güvenlik özellikleri](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md); bir çözümün görünür, değilse bkz [genişletme güvenlik](../../../../docs/framework/wcf/extending/extending-security.md).</span><span class="sxs-lookup"><span data-stu-id="74d73-106">If your scenario requires more capabilities, first see [Security Capabilities with Custom Bindings](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md); if a solution is not apparent, see [Extending Security](../../../../docs/framework/wcf/extending/extending-security.md).</span></span> <span data-ttu-id="74d73-107">Oluşturuyorsanız (veya ile birlikte varsa) zengin talep kullanan bir sistemi Bkz konularındaki [yetkilendirme](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="74d73-107">If you are creating (or interoperating with) a system that uses rich claims, see the topics in [Authorization](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="74d73-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="74d73-108">In This Section</span></span>  
 [<span data-ttu-id="74d73-109">WCF Güvenliğini Programlama</span><span class="sxs-lookup"><span data-stu-id="74d73-109">Programming WCF Security</span></span>](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)  
 <span data-ttu-id="74d73-110">İletileri güvenli hale getirmek için kullanılan programlama modeli genel bakış.</span><span class="sxs-lookup"><span data-stu-id="74d73-110">An overview of the programming model used to secure messages.</span></span>  
  
 [<span data-ttu-id="74d73-111">Aktarım Güvenliğine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="74d73-111">Transport Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/transport-security-overview.md)  
 <span data-ttu-id="74d73-112">Aktarım katmanı aracılığıyla iletileri güvenli hale getirmeyi genel bakış.</span><span class="sxs-lookup"><span data-stu-id="74d73-112">An overview of how to secure messages through the transport layer.</span></span>  
  
 [<span data-ttu-id="74d73-113">İleti Güvenliği</span><span class="sxs-lookup"><span data-stu-id="74d73-113">Message Security</span></span>](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)  
 <span data-ttu-id="74d73-114">Windows Communication Foundation (WCF) ileti düzeyi güvenliği kullanma nedenleri özetler.</span><span class="sxs-lookup"><span data-stu-id="74d73-114">Summarizes reasons for using message-level security in Windows Communication Foundation (WCF).</span></span>  
  
 [<span data-ttu-id="74d73-115">Güvenli Oturumlar</span><span class="sxs-lookup"><span data-stu-id="74d73-115">Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/secure-sessions.md)  
 <span data-ttu-id="74d73-116">Bir WCF oturumu güvenli hale getirirken gereken konuları hakkında ayrıntılı bilgi.</span><span class="sxs-lookup"><span data-stu-id="74d73-116">A discussion of the considerations required when securing a WCF session.</span></span>  
  
 [<span data-ttu-id="74d73-117">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="74d73-117">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 <span data-ttu-id="74d73-118">Bir açıklama bazı ortak görevlerin X.509 sertifikaları kullanırken gereklidir.</span><span class="sxs-lookup"><span data-stu-id="74d73-118">An explanation of some of the common tasks required when using X.509 certificates.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="74d73-119">Başvuru</span><span class="sxs-lookup"><span data-stu-id="74d73-119">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Security>  
  
## <a name="related-sections"></a><span data-ttu-id="74d73-120">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="74d73-120">Related Sections</span></span>  
 [<span data-ttu-id="74d73-121">Güvenlik Kavramları</span><span class="sxs-lookup"><span data-stu-id="74d73-121">Security Concepts</span></span>](../../../../docs/framework/wcf/feature-details/security-concepts.md)  
  
 [<span data-ttu-id="74d73-122">Güvenliği Genişletme</span><span class="sxs-lookup"><span data-stu-id="74d73-122">Extending Security</span></span>](../../../../docs/framework/wcf/extending/extending-security.md)  
  
 [<span data-ttu-id="74d73-123">Ortak Güvenlik Senaryoları</span><span class="sxs-lookup"><span data-stu-id="74d73-123">Common Security Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
  
 [<span data-ttu-id="74d73-124">Bağlamalar ve Güvenlik</span><span class="sxs-lookup"><span data-stu-id="74d73-124">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
  
 [<span data-ttu-id="74d73-125">Özel Bağlamalarla Güvenlik Özellikleri</span><span class="sxs-lookup"><span data-stu-id="74d73-125">Security Capabilities with Custom Bindings</span></span>](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
  
 [<span data-ttu-id="74d73-126">Güvenliği Genişletme</span><span class="sxs-lookup"><span data-stu-id="74d73-126">Extending Security</span></span>](../../../../docs/framework/wcf/extending/extending-security.md)  
  
 [<span data-ttu-id="74d73-127">Yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="74d73-127">Authorization</span></span>](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
  
## <a name="see-also"></a><span data-ttu-id="74d73-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="74d73-128">See Also</span></span>  
 [<span data-ttu-id="74d73-129">Temel WCF Programlama</span><span class="sxs-lookup"><span data-stu-id="74d73-129">Basic WCF Programming</span></span>](../../../../docs/framework/wcf/basic-wcf-programming.md)  
 [<span data-ttu-id="74d73-130">Windows Server AppFabric için güvenlik modeli</span><span class="sxs-lookup"><span data-stu-id="74d73-130">Security Model for Windows Server App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
