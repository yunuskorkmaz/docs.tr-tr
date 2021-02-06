---
description: 'Daha fazla bilgi edinin: hizmet ve Istemcilerin güvenliğini sağlama'
title: Hizmet ve İstemcileri Güvenli Hale Getirme
ms.date: 03/30/2017
helpviewer_keywords:
- message security [WCF]
ms.assetid: e681f3bd-0c09-4a58-b0e4-0ecbdf1aa6c7
ms.openlocfilehash: ff947e8bf975fd3fb3c6513ee0bf49bb21a951dd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99632639"
---
# <a name="securing-services-and-clients"></a><span data-ttu-id="3e123-103">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="3e123-103">Securing Services and Clients</span></span>

<span data-ttu-id="3e123-104">Bu bölümdeki bilgiler Windows Communication Foundation (WCF) ' deki programlama güvenliği ' ne odaklanır.</span><span class="sxs-lookup"><span data-stu-id="3e123-104">The information in this section focuses on programming security in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="3e123-105">Genellikle, bu, uygun bir sistem tarafından sağlanmış bağlamayı seçmeyi, Güvenlik öğesinin özelliklerini ayarlamayı ve ardından hizmet davranışlarının, kimlik bilgilerinin hizmet veya istemci tarafından kullanılmak üzere nasıl alındığını belirleyen özellikler ayarlanmasını içerir.</span><span class="sxs-lookup"><span data-stu-id="3e123-105">Generally, this includes selecting an appropriate system-provided binding, setting the properties of the security element, and then setting properties of the service behaviors that govern how credentials are retrieved for use by either the service or the client.</span></span> <span data-ttu-id="3e123-106">Bu teknikler, [yaygın güvenlik senaryolarında](common-security-scenarios.md)gösterildiği gibi çoğu senaryonun çoğu kullanıcının güvenlik gereksinimlerini kapsar.</span><span class="sxs-lookup"><span data-stu-id="3e123-106">These techniques cover the security requirements of most users for most scenarios, as shown in [Common Security Scenarios](common-security-scenarios.md).</span></span> <span data-ttu-id="3e123-107">Senaryonuz daha fazla özellik gerektiriyorsa, önce [özel bağlamalarla güvenlik özelliklerine](security-capabilities-with-custom-bindings.md)bakın; bir çözüm görünmüyorsa bkz. [güvenliği genişletme](../extending/extending-security.md).</span><span class="sxs-lookup"><span data-stu-id="3e123-107">If your scenario requires more capabilities, first see [Security Capabilities with Custom Bindings](security-capabilities-with-custom-bindings.md); if a solution is not apparent, see [Extending Security](../extending/extending-security.md).</span></span> <span data-ttu-id="3e123-108">Zengin talepler kullanan bir sistem oluşturuyorsanız (veya ile birlikte çalışıyorsanız), [Yetkilendirme](authorization-in-wcf.md)' de yer alan konulara bakın.</span><span class="sxs-lookup"><span data-stu-id="3e123-108">If you are creating (or interoperating with) a system that uses rich claims, see the topics in [Authorization](authorization-in-wcf.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3e123-109">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="3e123-109">In This Section</span></span>  

 [<span data-ttu-id="3e123-110">WCF Güvenliğini Programlama</span><span class="sxs-lookup"><span data-stu-id="3e123-110">Programming WCF Security</span></span>](programming-wcf-security.md)  
 <span data-ttu-id="3e123-111">İletileri güvenli hale getirmek için kullanılan programlama modeline genel bakış.</span><span class="sxs-lookup"><span data-stu-id="3e123-111">An overview of the programming model used to secure messages.</span></span>  
  
 [<span data-ttu-id="3e123-112">Taşıma Güvenliği Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="3e123-112">Transport Security Overview</span></span>](transport-security-overview.md)  
 <span data-ttu-id="3e123-113">Aktarım katmanı üzerinden iletilerin güvenliğini sağlama konusuna genel bakış.</span><span class="sxs-lookup"><span data-stu-id="3e123-113">An overview of how to secure messages through the transport layer.</span></span>  
  
 [<span data-ttu-id="3e123-114">İleti Güvenliği</span><span class="sxs-lookup"><span data-stu-id="3e123-114">Message Security</span></span>](message-security-in-wcf.md)  
 <span data-ttu-id="3e123-115">Windows Communication Foundation (WCF) ' de ileti düzeyi güvenliği kullanma nedenlerini özetler.</span><span class="sxs-lookup"><span data-stu-id="3e123-115">Summarizes reasons for using message-level security in Windows Communication Foundation (WCF).</span></span>  
  
 [<span data-ttu-id="3e123-116">Güvenli Oturumlar</span><span class="sxs-lookup"><span data-stu-id="3e123-116">Secure Sessions</span></span>](secure-sessions.md)  
 <span data-ttu-id="3e123-117">Bir WCF oturumunun güvenliğini sağlarken gereken önemli noktalar hakkında bir tartışma.</span><span class="sxs-lookup"><span data-stu-id="3e123-117">A discussion of the considerations required when securing a WCF session.</span></span>  
  
 [<span data-ttu-id="3e123-118">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="3e123-118">Working with Certificates</span></span>](working-with-certificates.md)  
 <span data-ttu-id="3e123-119">X. 509.440 sertifikaları kullanılırken gereken bazı yaygın görevlerden oluşan bir açıklama.</span><span class="sxs-lookup"><span data-stu-id="3e123-119">An explanation of some of the common tasks required when using X.509 certificates.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="3e123-120">Başvuru</span><span class="sxs-lookup"><span data-stu-id="3e123-120">Reference</span></span>  

 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Security>  
  
## <a name="related-sections"></a><span data-ttu-id="3e123-121">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="3e123-121">Related Sections</span></span>  

 [<span data-ttu-id="3e123-122">Güvenlik Kavramları</span><span class="sxs-lookup"><span data-stu-id="3e123-122">Security Concepts</span></span>](security-concepts.md)  
  
 [<span data-ttu-id="3e123-123">Güvenliği Genişletme</span><span class="sxs-lookup"><span data-stu-id="3e123-123">Extending Security</span></span>](../extending/extending-security.md)  
  
 [<span data-ttu-id="3e123-124">Ortak Güvenlik Senaryoları</span><span class="sxs-lookup"><span data-stu-id="3e123-124">Common Security Scenarios</span></span>](common-security-scenarios.md)  
  
 [<span data-ttu-id="3e123-125">Bağlamalar ve Güvenlik</span><span class="sxs-lookup"><span data-stu-id="3e123-125">Bindings and Security</span></span>](bindings-and-security.md)  
  
 [<span data-ttu-id="3e123-126">Özel Bağlamalarla Güvenlik Özellikleri</span><span class="sxs-lookup"><span data-stu-id="3e123-126">Security Capabilities with Custom Bindings</span></span>](security-capabilities-with-custom-bindings.md)  
  
 [<span data-ttu-id="3e123-127">Güvenliği Genişletme</span><span class="sxs-lookup"><span data-stu-id="3e123-127">Extending Security</span></span>](../extending/extending-security.md)  
  
 [<span data-ttu-id="3e123-128">Yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="3e123-128">Authorization</span></span>](authorization-in-wcf.md)  
  
## <a name="see-also"></a><span data-ttu-id="3e123-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3e123-129">See also</span></span>

- [<span data-ttu-id="3e123-130">Temel WCF Programlama</span><span class="sxs-lookup"><span data-stu-id="3e123-130">Basic WCF Programming</span></span>](../basic-wcf-programming.md)
- <span data-ttu-id="3e123-131">[Windows Server App Fabric için güvenlik modeli](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="3e123-131">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
