---
title: WCF'de Güvenlik Değerlendirmeleri
ms.date: 03/30/2017
helpviewer_keywords:
- security [WCF]
- Windows Communication Foundation, security
- WCF, security
ms.assetid: 42055ee0-6d0c-443d-9d89-788dfc345d6d
ms.openlocfilehash: 796098258601ec5fa208fd8a8060b28c3eeeb4d6
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96276028"
---
# <a name="security-considerations-in-wcf"></a><span data-ttu-id="aa1f1-102">WCF'de Güvenlik Değerlendirmeleri</span><span class="sxs-lookup"><span data-stu-id="aa1f1-102">Security Considerations in WCF</span></span>

<span data-ttu-id="aa1f1-103">Bu bölümdeki konularda, Windows Communication Foundation (WCF) uygulaması tasarlarken göz önünde bulundurmanız gereken güvenlikle ilgili çeşitli öğeler listelenir.</span><span class="sxs-lookup"><span data-stu-id="aa1f1-103">The topics in this section list various security-related items to consider when designing a Windows Communication Foundation (WCF) application.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="aa1f1-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="aa1f1-104">In This Section</span></span>  

 [<span data-ttu-id="aa1f1-105">Bilgilerin Açığa Çıkması</span><span class="sxs-lookup"><span data-stu-id="aa1f1-105">Information Disclosure</span></span>](information-disclosure.md)  
 <span data-ttu-id="aa1f1-106">Bilgilerin açıklanmasında veya saldırıya neden olabilecek çeşitli yollar ve bunun nasıl azaltılacağını ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="aa1f1-106">Discusses the various ways that information can be disclosed or attacked, and how to mitigate this.</span></span>  
  
 [<span data-ttu-id="aa1f1-107">Ayrıcalık Yükseltme</span><span class="sxs-lookup"><span data-stu-id="aa1f1-107">Elevation of Privilege</span></span>](elevation-of-privilege.md)  
 <span data-ttu-id="aa1f1-108">Başlangıçta verilen ve bu sorunu hafifletmenin ötesinde bir saldırgan yetkilendirme izinleri verme etkilerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="aa1f1-108">Discusses the effects of giving an attacker authorization permissions beyond those initially granted and how to mitigate this.</span></span>  
  
 [<span data-ttu-id="aa1f1-109">Hizmet Reddi</span><span class="sxs-lookup"><span data-stu-id="aa1f1-109">Denial of Service</span></span>](denial-of-service.md)  
 <span data-ttu-id="aa1f1-110">Bir sistem iletileri uygun şekilde işleyemezse ne olduğunu ve bunun nasıl azaltılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="aa1f1-110">Discusses what happens when a system is unable to process messages appropriately and how to mitigate it.</span></span>  
  
 [<span data-ttu-id="aa1f1-111">Kurcalama</span><span class="sxs-lookup"><span data-stu-id="aa1f1-111">Tampering</span></span>](tampering.md)  
 <span data-ttu-id="aa1f1-112">İletilerin değiştirilmesini veya iletilerin teslimini ve bunun nasıl azaltılacağını ele alır.</span><span class="sxs-lookup"><span data-stu-id="aa1f1-112">Discusses the altering of messages or the delivery of messages and how to mitigate it.</span></span>  
  
 [<span data-ttu-id="aa1f1-113">Yeniden Yürütme Saldırıları</span><span class="sxs-lookup"><span data-stu-id="aa1f1-113">Replay Attacks</span></span>](replay-attacks.md)  
 <span data-ttu-id="aa1f1-114">Bir saldırgan bir ileti akışını iki taraf arasında kopyaladığında ne olduğunu ve akışın bir veya daha fazla tarafın akışını yeniden oynadığını ve bunun nasıl azaltılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="aa1f1-114">Discusses what happens when an attacker copies a stream of messages between two parties and replays the stream to one or more of the parties, and how to mitigate this.</span></span>  
  
 [<span data-ttu-id="aa1f1-115">Güvenli Oturumlar için Güvenlikli İlgili Önemli Noktalar</span><span class="sxs-lookup"><span data-stu-id="aa1f1-115">Security Considerations for Secure Sessions</span></span>](security-considerations-for-secure-sessions.md)  
 <span data-ttu-id="aa1f1-116">Güvenli oturumları uygularken güvenliği etkileyen aşağıdaki öğeleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="aa1f1-116">Discusses the following items that affect security when implementing secure sessions.</span></span>  
  
 [<span data-ttu-id="aa1f1-117">Desteklenmeyen Senaryolar</span><span class="sxs-lookup"><span data-stu-id="aa1f1-117">Unsupported Scenarios</span></span>](unsupported-scenarios.md)  
 <span data-ttu-id="aa1f1-118">Belirli güvenlik yönlerini desteklemeyen çeşitli senaryolar listeler ve kaçınılması veya dikkate alınmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="aa1f1-118">Lists various scenarios that do not support a particular aspect of security and should be avoided or considered.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="aa1f1-119">Başvuru</span><span class="sxs-lookup"><span data-stu-id="aa1f1-119">Reference</span></span>  

 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a><span data-ttu-id="aa1f1-120">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="aa1f1-120">Related Sections</span></span>  

 [<span data-ttu-id="aa1f1-121">Güvenlik Kılavuzu ve En İyi Uygulamalar</span><span class="sxs-lookup"><span data-stu-id="aa1f1-121">Security Guidance and Best Practices</span></span>](security-guidance-and-best-practices.md)  
  
## <a name="see-also"></a><span data-ttu-id="aa1f1-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aa1f1-122">See also</span></span>

- [<span data-ttu-id="aa1f1-123">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="aa1f1-123">Security</span></span>](security.md)
