---
title: "Hizmet ve İstemcileri Güvenli Hale Getirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: message security [WCF]
ms.assetid: e681f3bd-0c09-4a58-b0e4-0ecbdf1aa6c7
caps.latest.revision: "13"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: ed37992b5488d33b9292bdd54eef47f9eb12f225
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="securing-services-and-clients"></a><span data-ttu-id="99552-102">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="99552-102">Securing Services and Clients</span></span>
<span data-ttu-id="99552-103">Bu bölümdeki bilgiler odaklanır güvenlik programlama [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="99552-103">The information in this section focuses on programming security in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span> <span data-ttu-id="99552-104">Genellikle, bu uygun bir sistem tarafından sağlanan bağlama, güvenlik öğesinin özelliklerini ayarlama ve nasıl kimlik bilgilerini kullanmak için hizmet veya istemci tarafından alınır yöneten hizmet davranışları özelliklerin ayarlanmasını seçerek içerir.</span><span class="sxs-lookup"><span data-stu-id="99552-104">Generally, this includes selecting an appropriate system-provided binding, setting the properties of the security element, and then setting properties of the service behaviors that govern how credentials are retrieved for use by either the service or the client.</span></span> <span data-ttu-id="99552-105">Gösterildiği gibi güvenlik kullanıcıların çoğunun gereksinimlerine yönelik çoğu senaryo için bu teknikler kapak [ortak güvenlik senaryoları](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md).</span><span class="sxs-lookup"><span data-stu-id="99552-105">These techniques cover the security requirements of most users for most scenarios, as shown in [Common Security Scenarios](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md).</span></span> <span data-ttu-id="99552-106">Daha fazla yetenekleri senaryonuz gerektiriyorsa, önce bkz [özel bağlamalarla güvenlik özellikleri](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md); bir çözüm görünür, değilse bkz [genişletme güvenlik](../../../../docs/framework/wcf/extending/extending-security.md).</span><span class="sxs-lookup"><span data-stu-id="99552-106">If your scenario requires more capabilities, first see [Security Capabilities with Custom Bindings](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md); if a solution is not apparent, see [Extending Security](../../../../docs/framework/wcf/extending/extending-security.md).</span></span> <span data-ttu-id="99552-107">Oluşturuyorsanız (veya ile birlikte varsa) zengin talep kullanan bir sistemi Bkz konularındaki [yetkilendirme](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="99552-107">If you are creating (or interoperating with) a system that uses rich claims, see the topics in [Authorization](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="99552-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="99552-108">In This Section</span></span>  
 [<span data-ttu-id="99552-109">WCF güvenliğini programlama</span><span class="sxs-lookup"><span data-stu-id="99552-109">Programming WCF Security</span></span>](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)  
 <span data-ttu-id="99552-110">İletileri güvenli hale getirmek için kullanılan programlama modeli genel bakış.</span><span class="sxs-lookup"><span data-stu-id="99552-110">An overview of the programming model used to secure messages.</span></span>  
  
 [<span data-ttu-id="99552-111">Taşıma güvenliği genel bakış</span><span class="sxs-lookup"><span data-stu-id="99552-111">Transport Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/transport-security-overview.md)  
 <span data-ttu-id="99552-112">Aktarım katmanı üzerinden ileti güvenliğini sağlama genel bakış.</span><span class="sxs-lookup"><span data-stu-id="99552-112">An overview of how to secure messages through the transport layer.</span></span>  
  
 [<span data-ttu-id="99552-113">İleti güvenliği</span><span class="sxs-lookup"><span data-stu-id="99552-113">Message Security</span></span>](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)  
 <span data-ttu-id="99552-114">İleti düzeyi güvenlik kullanma nedenleri özetler [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="99552-114">Summarizes reasons for using message-level security in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span>  
  
 [<span data-ttu-id="99552-115">Güvenli oturumlar</span><span class="sxs-lookup"><span data-stu-id="99552-115">Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/secure-sessions.md)  
 <span data-ttu-id="99552-116">Güvenli hale getirirken gerekli konuları tartışması bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] oturumu.</span><span class="sxs-lookup"><span data-stu-id="99552-116">A discussion of the considerations required when securing a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] session.</span></span>  
  
 [<span data-ttu-id="99552-117">Sertifikalar ile çalışma</span><span class="sxs-lookup"><span data-stu-id="99552-117">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 <span data-ttu-id="99552-118">Bir açıklama bazı ortak görevler X.509 sertifikalarını kullanılırken gereklidir.</span><span class="sxs-lookup"><span data-stu-id="99552-118">An explanation of some of the common tasks required when using X.509 certificates.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="99552-119">Başvuru</span><span class="sxs-lookup"><span data-stu-id="99552-119">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Security>  
  
## <a name="related-sections"></a><span data-ttu-id="99552-120">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="99552-120">Related Sections</span></span>  
 [<span data-ttu-id="99552-121">Güvenlik kavramları</span><span class="sxs-lookup"><span data-stu-id="99552-121">Security Concepts</span></span>](../../../../docs/framework/wcf/feature-details/security-concepts.md)  
  
 [<span data-ttu-id="99552-122">Güvenliği genişletme</span><span class="sxs-lookup"><span data-stu-id="99552-122">Extending Security</span></span>](../../../../docs/framework/wcf/extending/extending-security.md)  
  
 [<span data-ttu-id="99552-123">Ortak Güvenlik senaryoları</span><span class="sxs-lookup"><span data-stu-id="99552-123">Common Security Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
  
 [<span data-ttu-id="99552-124">Bağlamalar ve güvenlik</span><span class="sxs-lookup"><span data-stu-id="99552-124">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
  
 [<span data-ttu-id="99552-125">Özel bağlamalarla güvenlik özellikleri</span><span class="sxs-lookup"><span data-stu-id="99552-125">Security Capabilities with Custom Bindings</span></span>](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
  
 [<span data-ttu-id="99552-126">Güvenliği genişletme</span><span class="sxs-lookup"><span data-stu-id="99552-126">Extending Security</span></span>](../../../../docs/framework/wcf/extending/extending-security.md)  
  
 [<span data-ttu-id="99552-127">Yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="99552-127">Authorization</span></span>](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
  
## <a name="see-also"></a><span data-ttu-id="99552-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="99552-128">See Also</span></span>  
 [<span data-ttu-id="99552-129">Temel WCF programlama</span><span class="sxs-lookup"><span data-stu-id="99552-129">Basic WCF Programming</span></span>](../../../../docs/framework/wcf/basic-wcf-programming.md)  
 [<span data-ttu-id="99552-130">Windows Server App Fabric için güvenlik modeli</span><span class="sxs-lookup"><span data-stu-id="99552-130">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
