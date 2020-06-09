---
title: Hizmet ve İstemcileri Güvenli Hale Getirme
ms.date: 03/30/2017
helpviewer_keywords:
- message security [WCF]
ms.assetid: e681f3bd-0c09-4a58-b0e4-0ecbdf1aa6c7
ms.openlocfilehash: db0a0dcfbe04a7b7dbfabfed59f9b8637d0a2797
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84586214"
---
# <a name="securing-services-and-clients"></a><span data-ttu-id="9d305-102">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="9d305-102">Securing Services and Clients</span></span>
<span data-ttu-id="9d305-103">Bu bölümdeki bilgiler Windows Communication Foundation (WCF) ' deki programlama güvenliği ' ne odaklanır.</span><span class="sxs-lookup"><span data-stu-id="9d305-103">The information in this section focuses on programming security in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="9d305-104">Genellikle, bu, uygun bir sistem tarafından sağlanmış bağlamayı seçmeyi, Güvenlik öğesinin özelliklerini ayarlamayı ve ardından hizmet davranışlarının, kimlik bilgilerinin hizmet veya istemci tarafından kullanılmak üzere nasıl alındığını belirleyen özellikler ayarlanmasını içerir.</span><span class="sxs-lookup"><span data-stu-id="9d305-104">Generally, this includes selecting an appropriate system-provided binding, setting the properties of the security element, and then setting properties of the service behaviors that govern how credentials are retrieved for use by either the service or the client.</span></span> <span data-ttu-id="9d305-105">Bu teknikler, [yaygın güvenlik senaryolarında](common-security-scenarios.md)gösterildiği gibi çoğu senaryonun çoğu kullanıcının güvenlik gereksinimlerini kapsar.</span><span class="sxs-lookup"><span data-stu-id="9d305-105">These techniques cover the security requirements of most users for most scenarios, as shown in [Common Security Scenarios](common-security-scenarios.md).</span></span> <span data-ttu-id="9d305-106">Senaryonuz daha fazla özellik gerektiriyorsa, önce [özel bağlamalarla güvenlik özelliklerine](security-capabilities-with-custom-bindings.md)bakın; bir çözüm görünmüyorsa bkz. [güvenliği genişletme](../extending/extending-security.md).</span><span class="sxs-lookup"><span data-stu-id="9d305-106">If your scenario requires more capabilities, first see [Security Capabilities with Custom Bindings](security-capabilities-with-custom-bindings.md); if a solution is not apparent, see [Extending Security](../extending/extending-security.md).</span></span> <span data-ttu-id="9d305-107">Zengin talepler kullanan bir sistem oluşturuyorsanız (veya ile birlikte çalışıyorsanız), [Yetkilendirme](authorization-in-wcf.md)' de yer alan konulara bakın.</span><span class="sxs-lookup"><span data-stu-id="9d305-107">If you are creating (or interoperating with) a system that uses rich claims, see the topics in [Authorization](authorization-in-wcf.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9d305-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="9d305-108">In This Section</span></span>  
 [<span data-ttu-id="9d305-109">WCF Güvenliğini Programlama</span><span class="sxs-lookup"><span data-stu-id="9d305-109">Programming WCF Security</span></span>](programming-wcf-security.md)  
 <span data-ttu-id="9d305-110">İletileri güvenli hale getirmek için kullanılan programlama modeline genel bakış.</span><span class="sxs-lookup"><span data-stu-id="9d305-110">An overview of the programming model used to secure messages.</span></span>  
  
 [<span data-ttu-id="9d305-111">Aktarım Güvenliğine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9d305-111">Transport Security Overview</span></span>](transport-security-overview.md)  
 <span data-ttu-id="9d305-112">Aktarım katmanı üzerinden iletilerin güvenliğini sağlama konusuna genel bakış.</span><span class="sxs-lookup"><span data-stu-id="9d305-112">An overview of how to secure messages through the transport layer.</span></span>  
  
 [<span data-ttu-id="9d305-113">İleti Güvenliği</span><span class="sxs-lookup"><span data-stu-id="9d305-113">Message Security</span></span>](message-security-in-wcf.md)  
 <span data-ttu-id="9d305-114">Windows Communication Foundation (WCF) ' de ileti düzeyi güvenliği kullanma nedenlerini özetler.</span><span class="sxs-lookup"><span data-stu-id="9d305-114">Summarizes reasons for using message-level security in Windows Communication Foundation (WCF).</span></span>  
  
 [<span data-ttu-id="9d305-115">Güvenli Oturumlar</span><span class="sxs-lookup"><span data-stu-id="9d305-115">Secure Sessions</span></span>](secure-sessions.md)  
 <span data-ttu-id="9d305-116">Bir WCF oturumunun güvenliğini sağlarken gereken önemli noktalar hakkında bir tartışma.</span><span class="sxs-lookup"><span data-stu-id="9d305-116">A discussion of the considerations required when securing a WCF session.</span></span>  
  
 [<span data-ttu-id="9d305-117">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="9d305-117">Working with Certificates</span></span>](working-with-certificates.md)  
 <span data-ttu-id="9d305-118">X. 509.440 sertifikaları kullanılırken gereken bazı yaygın görevlerden oluşan bir açıklama.</span><span class="sxs-lookup"><span data-stu-id="9d305-118">An explanation of some of the common tasks required when using X.509 certificates.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="9d305-119">Başvuru</span><span class="sxs-lookup"><span data-stu-id="9d305-119">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Security>  
  
## <a name="related-sections"></a><span data-ttu-id="9d305-120">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="9d305-120">Related Sections</span></span>  
 [<span data-ttu-id="9d305-121">Güvenlik kavramları</span><span class="sxs-lookup"><span data-stu-id="9d305-121">Security Concepts</span></span>](security-concepts.md)  
  
 [<span data-ttu-id="9d305-122">Güvenliği Genişletme</span><span class="sxs-lookup"><span data-stu-id="9d305-122">Extending Security</span></span>](../extending/extending-security.md)  
  
 [<span data-ttu-id="9d305-123">Ortak Güvenlik Senaryoları</span><span class="sxs-lookup"><span data-stu-id="9d305-123">Common Security Scenarios</span></span>](common-security-scenarios.md)  
  
 [<span data-ttu-id="9d305-124">Bağlamalar ve Güvenlik</span><span class="sxs-lookup"><span data-stu-id="9d305-124">Bindings and Security</span></span>](bindings-and-security.md)  
  
 [<span data-ttu-id="9d305-125">Özel Bağlamalarla Güvenlik Özellikleri</span><span class="sxs-lookup"><span data-stu-id="9d305-125">Security Capabilities with Custom Bindings</span></span>](security-capabilities-with-custom-bindings.md)  
  
 [<span data-ttu-id="9d305-126">Güvenliği Genişletme</span><span class="sxs-lookup"><span data-stu-id="9d305-126">Extending Security</span></span>](../extending/extending-security.md)  
  
 [<span data-ttu-id="9d305-127">Yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="9d305-127">Authorization</span></span>](authorization-in-wcf.md)  
  
## <a name="see-also"></a><span data-ttu-id="9d305-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9d305-128">See also</span></span>

- [<span data-ttu-id="9d305-129">Temel WCF Programlama</span><span class="sxs-lookup"><span data-stu-id="9d305-129">Basic WCF Programming</span></span>](../basic-wcf-programming.md)
- <span data-ttu-id="9d305-130">[Windows Server App Fabric için güvenlik modeli](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="9d305-130">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
