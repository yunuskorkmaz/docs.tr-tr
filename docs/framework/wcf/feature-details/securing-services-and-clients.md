---
title: Hizmet ve İstemcileri Güvenli Hale Getirme
ms.date: 03/30/2017
helpviewer_keywords:
- message security [WCF]
ms.assetid: e681f3bd-0c09-4a58-b0e4-0ecbdf1aa6c7
ms.openlocfilehash: 719ab26198bd7b83310025e03e541fa11b109612
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746421"
---
# <a name="securing-services-and-clients"></a><span data-ttu-id="1ba54-102">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="1ba54-102">Securing Services and Clients</span></span>
<span data-ttu-id="1ba54-103">Bu bölümdeki bilgiler Windows Communication Foundation (WCF) ' deki programlama güvenliği ' ne odaklanır.</span><span class="sxs-lookup"><span data-stu-id="1ba54-103">The information in this section focuses on programming security in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="1ba54-104">Genellikle, bu, uygun bir sistem tarafından sağlanmış bağlamayı seçmeyi, Güvenlik öğesinin özelliklerini ayarlamayı ve ardından hizmet davranışlarının, kimlik bilgilerinin hizmet veya istemci tarafından kullanılmak üzere nasıl alındığını belirleyen özellikler ayarlanmasını içerir.</span><span class="sxs-lookup"><span data-stu-id="1ba54-104">Generally, this includes selecting an appropriate system-provided binding, setting the properties of the security element, and then setting properties of the service behaviors that govern how credentials are retrieved for use by either the service or the client.</span></span> <span data-ttu-id="1ba54-105">Bu teknikler, [yaygın güvenlik senaryolarında](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)gösterildiği gibi çoğu senaryonun çoğu kullanıcının güvenlik gereksinimlerini kapsar.</span><span class="sxs-lookup"><span data-stu-id="1ba54-105">These techniques cover the security requirements of most users for most scenarios, as shown in [Common Security Scenarios](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md).</span></span> <span data-ttu-id="1ba54-106">Senaryonuz daha fazla özellik gerektiriyorsa, önce [özel bağlamalarla güvenlik özelliklerine](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)bakın; bir çözüm görünmüyorsa bkz. [güvenliği genişletme](../../../../docs/framework/wcf/extending/extending-security.md).</span><span class="sxs-lookup"><span data-stu-id="1ba54-106">If your scenario requires more capabilities, first see [Security Capabilities with Custom Bindings](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md); if a solution is not apparent, see [Extending Security](../../../../docs/framework/wcf/extending/extending-security.md).</span></span> <span data-ttu-id="1ba54-107">Zengin talepler kullanan bir sistem oluşturuyorsanız (veya ile birlikte çalışıyorsanız), [Yetkilendirme](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)' de yer alan konulara bakın.</span><span class="sxs-lookup"><span data-stu-id="1ba54-107">If you are creating (or interoperating with) a system that uses rich claims, see the topics in [Authorization](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1ba54-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="1ba54-108">In This Section</span></span>  
 [<span data-ttu-id="1ba54-109">WCF Güvenliğini Programlama</span><span class="sxs-lookup"><span data-stu-id="1ba54-109">Programming WCF Security</span></span>](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)  
 <span data-ttu-id="1ba54-110">İletileri güvenli hale getirmek için kullanılan programlama modeline genel bakış.</span><span class="sxs-lookup"><span data-stu-id="1ba54-110">An overview of the programming model used to secure messages.</span></span>  
  
 [<span data-ttu-id="1ba54-111">Aktarım Güvenliğine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="1ba54-111">Transport Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/transport-security-overview.md)  
 <span data-ttu-id="1ba54-112">Aktarım katmanı üzerinden iletilerin güvenliğini sağlama konusuna genel bakış.</span><span class="sxs-lookup"><span data-stu-id="1ba54-112">An overview of how to secure messages through the transport layer.</span></span>  
  
 [<span data-ttu-id="1ba54-113">İleti Güvenliği</span><span class="sxs-lookup"><span data-stu-id="1ba54-113">Message Security</span></span>](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)  
 <span data-ttu-id="1ba54-114">Windows Communication Foundation (WCF) ' de ileti düzeyi güvenliği kullanma nedenlerini özetler.</span><span class="sxs-lookup"><span data-stu-id="1ba54-114">Summarizes reasons for using message-level security in Windows Communication Foundation (WCF).</span></span>  
  
 [<span data-ttu-id="1ba54-115">Güvenli Oturumlar</span><span class="sxs-lookup"><span data-stu-id="1ba54-115">Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/secure-sessions.md)  
 <span data-ttu-id="1ba54-116">Bir WCF oturumunun güvenliğini sağlarken gereken önemli noktalar hakkında bir tartışma.</span><span class="sxs-lookup"><span data-stu-id="1ba54-116">A discussion of the considerations required when securing a WCF session.</span></span>  
  
 [<span data-ttu-id="1ba54-117">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="1ba54-117">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 <span data-ttu-id="1ba54-118">X. 509.440 sertifikaları kullanılırken gereken bazı yaygın görevlerden oluşan bir açıklama.</span><span class="sxs-lookup"><span data-stu-id="1ba54-118">An explanation of some of the common tasks required when using X.509 certificates.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="1ba54-119">Başvuru</span><span class="sxs-lookup"><span data-stu-id="1ba54-119">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Security>  
  
## <a name="related-sections"></a><span data-ttu-id="1ba54-120">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="1ba54-120">Related Sections</span></span>  
 [<span data-ttu-id="1ba54-121">Güvenlik Kavramları</span><span class="sxs-lookup"><span data-stu-id="1ba54-121">Security Concepts</span></span>](../../../../docs/framework/wcf/feature-details/security-concepts.md)  
  
 [<span data-ttu-id="1ba54-122">Güvenliği Genişletme</span><span class="sxs-lookup"><span data-stu-id="1ba54-122">Extending Security</span></span>](../../../../docs/framework/wcf/extending/extending-security.md)  
  
 [<span data-ttu-id="1ba54-123">Ortak Güvenlik Senaryoları</span><span class="sxs-lookup"><span data-stu-id="1ba54-123">Common Security Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
  
 [<span data-ttu-id="1ba54-124">Bağlamalar ve Güvenlik</span><span class="sxs-lookup"><span data-stu-id="1ba54-124">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
  
 [<span data-ttu-id="1ba54-125">Özel Bağlamalarla Güvenlik Özellikleri</span><span class="sxs-lookup"><span data-stu-id="1ba54-125">Security Capabilities with Custom Bindings</span></span>](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
  
 [<span data-ttu-id="1ba54-126">Güvenliği Genişletme</span><span class="sxs-lookup"><span data-stu-id="1ba54-126">Extending Security</span></span>](../../../../docs/framework/wcf/extending/extending-security.md)  
  
 [<span data-ttu-id="1ba54-127">Yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="1ba54-127">Authorization</span></span>](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
  
## <a name="see-also"></a><span data-ttu-id="1ba54-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1ba54-128">See also</span></span>

- [<span data-ttu-id="1ba54-129">Temel WCF Programlama</span><span class="sxs-lookup"><span data-stu-id="1ba54-129">Basic WCF Programming</span></span>](../../../../docs/framework/wcf/basic-wcf-programming.md)
- <span data-ttu-id="1ba54-130">[Windows Server App Fabric için güvenlik modeli](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="1ba54-130">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
