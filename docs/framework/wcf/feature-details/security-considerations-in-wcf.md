---
title: "WCF'de Güvenlik Değerlendirmeleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [WCF]
- Windows Communication Foundation, security
- WCF, security
ms.assetid: 42055ee0-6d0c-443d-9d89-788dfc345d6d
caps.latest.revision: "49"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: c0af5a5d96f20b2ba5118909a3f0c5ba405bdb11
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="security-considerations-in-wcf"></a><span data-ttu-id="8d05a-102">WCF'de Güvenlik Değerlendirmeleri</span><span class="sxs-lookup"><span data-stu-id="8d05a-102">Security Considerations in WCF</span></span>
<span data-ttu-id="8d05a-103">Bu bölümdeki konular, tasarlarken dikkate alınması gereken çeşitli güvenlikle ilgili öğeleri listesinde bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] uygulama.</span><span class="sxs-lookup"><span data-stu-id="8d05a-103">The topics in this section list various security-related items to consider when designing a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] application.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8d05a-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="8d05a-104">In This Section</span></span>  
 [<span data-ttu-id="8d05a-105">Bilgilerin açığa çıkmasına</span><span class="sxs-lookup"><span data-stu-id="8d05a-105">Information Disclosure</span></span>](../../../../docs/framework/wcf/feature-details/information-disclosure.md)  
 <span data-ttu-id="8d05a-106">Bilgi ifşa veya saldırıya dikkat çeşitli şekillerde ve bunu azaltmak nasıl anlatılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8d05a-106">Discusses the various ways that information can be disclosed or attacked, and how to mitigate this.</span></span>  
  
 [<span data-ttu-id="8d05a-107">Ayrıcalık yükseltme</span><span class="sxs-lookup"><span data-stu-id="8d05a-107">Elevation of Privilege</span></span>](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)  
 <span data-ttu-id="8d05a-108">Bir saldırgan yetkilendirme izinleri başlangıçta verilenlerin ötesinde ve bunu azaltmak nasıl vermiş etkilerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="8d05a-108">Discusses the effects of giving an attacker authorization permissions beyond those initially granted and how to mitigate this.</span></span>  
  
 [<span data-ttu-id="8d05a-109">Hizmet reddi</span><span class="sxs-lookup"><span data-stu-id="8d05a-109">Denial of Service</span></span>](../../../../docs/framework/wcf/feature-details/denial-of-service.md)  
 <span data-ttu-id="8d05a-110">Ne olacağını açıklar ne zaman bir sistemi iletileri uygun şekilde işleyemedi ve nasıl önlenebileceğini.</span><span class="sxs-lookup"><span data-stu-id="8d05a-110">Discusses what happens when a system is unable to process messages appropriately and how to mitigate it.</span></span>  
  
 [<span data-ttu-id="8d05a-111">Oynama</span><span class="sxs-lookup"><span data-stu-id="8d05a-111">Tampering</span></span>](../../../../docs/framework/wcf/feature-details/tampering.md)  
 <span data-ttu-id="8d05a-112">İletileri veya iletileri ve nasıl önlenebileceğini teslimini değiştirmeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="8d05a-112">Discusses the altering of messages or the delivery of messages and how to mitigate it.</span></span>  
  
 [<span data-ttu-id="8d05a-113">Yeniden yürütme saldırıları</span><span class="sxs-lookup"><span data-stu-id="8d05a-113">Replay Attacks</span></span>](../../../../docs/framework/wcf/feature-details/replay-attacks.md)  
 <span data-ttu-id="8d05a-114">Bir saldırgan kopyalarken iki arasında ileti akışı taraflarla ve bir veya daha fazla tarafların akış başlayarak yeniden oynatılır ne olur ve bu durumu iyileştirmek nasıl anlatılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8d05a-114">Discusses what happens when an attacker copies a stream of messages between two parties and replays the stream to one or more of the parties, and how to mitigate this.</span></span>  
  
 [<span data-ttu-id="8d05a-115">Güvenli oturumlar için güvenlik konuları</span><span class="sxs-lookup"><span data-stu-id="8d05a-115">Security Considerations for Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/security-considerations-for-secure-sessions.md)  
 <span data-ttu-id="8d05a-116">Güvenli oturumlar uygularken güvenliğini etkileyen aşağıdaki öğeleri açıklanır.</span><span class="sxs-lookup"><span data-stu-id="8d05a-116">Discusses the following items that affect security when implementing secure sessions.</span></span>  
  
 [<span data-ttu-id="8d05a-117">Desteklenmeyen senaryolar</span><span class="sxs-lookup"><span data-stu-id="8d05a-117">Unsupported Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)  
 <span data-ttu-id="8d05a-118">Belirli bir güvenlik durumuyla desteklemez ve kaçınılması veya kabul çeşitli senaryoları listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="8d05a-118">Lists various scenarios that do not support a particular aspect of security and should be avoided or considered.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="8d05a-119">Başvuru</span><span class="sxs-lookup"><span data-stu-id="8d05a-119">Reference</span></span>  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a><span data-ttu-id="8d05a-120">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="8d05a-120">Related Sections</span></span>  
 [<span data-ttu-id="8d05a-121">Güvenlik Kılavuzu ve en iyi yöntemler</span><span class="sxs-lookup"><span data-stu-id="8d05a-121">Security Guidance and Best Practices</span></span>](../../../../docs/framework/wcf/feature-details/security-guidance-and-best-practices.md)  
  
## <a name="see-also"></a><span data-ttu-id="8d05a-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8d05a-122">See Also</span></span>  
 [<span data-ttu-id="8d05a-123">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="8d05a-123">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)
