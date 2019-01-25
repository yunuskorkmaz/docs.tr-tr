---
title: WCF'de Güvenlik Değerlendirmeleri
ms.date: 03/30/2017
helpviewer_keywords:
- security [WCF]
- Windows Communication Foundation, security
- WCF, security
ms.assetid: 42055ee0-6d0c-443d-9d89-788dfc345d6d
ms.openlocfilehash: 6cc19f7719b9cdbcd3852c99f450c1d728dc833b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54746005"
---
# <a name="security-considerations-in-wcf"></a><span data-ttu-id="bc47d-102">WCF'de Güvenlik Değerlendirmeleri</span><span class="sxs-lookup"><span data-stu-id="bc47d-102">Security Considerations in WCF</span></span>
<span data-ttu-id="bc47d-103">Bu bölümdeki konularda, Windows Communication Foundation (WCF) bir uygulama tasarlanırken dikkate alınması gereken çeşitli güvenlikle ilgili öğeleri listelenir.</span><span class="sxs-lookup"><span data-stu-id="bc47d-103">The topics in this section list various security-related items to consider when designing a Windows Communication Foundation (WCF) application.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bc47d-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="bc47d-104">In This Section</span></span>  
 [<span data-ttu-id="bc47d-105">Bilgilerin Açığa Çıkması</span><span class="sxs-lookup"><span data-stu-id="bc47d-105">Information Disclosure</span></span>](../../../../docs/framework/wcf/feature-details/information-disclosure.md)  
 <span data-ttu-id="bc47d-106">Çeşitli yollarla bilgi ifşa veya Saldırıya uğrayan dikkat ve bunu azaltmak nasıl ele alır.</span><span class="sxs-lookup"><span data-stu-id="bc47d-106">Discusses the various ways that information can be disclosed or attacked, and how to mitigate this.</span></span>  
  
 [<span data-ttu-id="bc47d-107">Ayrıcalıkların Yükseltilmesi</span><span class="sxs-lookup"><span data-stu-id="bc47d-107">Elevation of Privilege</span></span>](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)  
 <span data-ttu-id="bc47d-108">Başlangıçta verilen ötesinde bir saldırgan yetkilendirme izni ve bunu azaltmak nasıl etkilerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="bc47d-108">Discusses the effects of giving an attacker authorization permissions beyond those initially granted and how to mitigate this.</span></span>  
  
 [<span data-ttu-id="bc47d-109">Hizmet Reddi</span><span class="sxs-lookup"><span data-stu-id="bc47d-109">Denial of Service</span></span>](../../../../docs/framework/wcf/feature-details/denial-of-service.md)  
 <span data-ttu-id="bc47d-110">Ne olacağını açıklar bir sistemde iletilerin uygun şekilde işleyemedi olduğunda ve nasıl önlenebileceğini.</span><span class="sxs-lookup"><span data-stu-id="bc47d-110">Discusses what happens when a system is unable to process messages appropriately and how to mitigate it.</span></span>  
  
 [<span data-ttu-id="bc47d-111">İzinsiz Değişiklik</span><span class="sxs-lookup"><span data-stu-id="bc47d-111">Tampering</span></span>](../../../../docs/framework/wcf/feature-details/tampering.md)  
 <span data-ttu-id="bc47d-112">İletileri veya iletileri ve nasıl önlenebileceğini teslimini değiştirmeyi anlatır.</span><span class="sxs-lookup"><span data-stu-id="bc47d-112">Discusses the altering of messages or the delivery of messages and how to mitigate it.</span></span>  
  
 [<span data-ttu-id="bc47d-113">Yeniden Yürütme Saldırıları</span><span class="sxs-lookup"><span data-stu-id="bc47d-113">Replay Attacks</span></span>](../../../../docs/framework/wcf/feature-details/replay-attacks.md)  
 <span data-ttu-id="bc47d-114">Bir saldırganın kopyalarken arasında iki ileti akışı taraflarla ve bir veya daha fazla taraflar akışa başlayarak yeniden oynatılır ne olur ve bu durumu iyileştirmek nasıl ele alır.</span><span class="sxs-lookup"><span data-stu-id="bc47d-114">Discusses what happens when an attacker copies a stream of messages between two parties and replays the stream to one or more of the parties, and how to mitigate this.</span></span>  
  
 [<span data-ttu-id="bc47d-115">Güvenli Oturumlar için Güvenlikle İlgili Önemli Noktalar</span><span class="sxs-lookup"><span data-stu-id="bc47d-115">Security Considerations for Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/security-considerations-for-secure-sessions.md)  
 <span data-ttu-id="bc47d-116">Güvenli oturumlar uygularken güvenliğini etkileyen aşağıdaki öğeleri açıklanır.</span><span class="sxs-lookup"><span data-stu-id="bc47d-116">Discusses the following items that affect security when implementing secure sessions.</span></span>  
  
 [<span data-ttu-id="bc47d-117">Desteklenmeyen Senaryolar</span><span class="sxs-lookup"><span data-stu-id="bc47d-117">Unsupported Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)  
 <span data-ttu-id="bc47d-118">Belirli bir güvenlik durumuyla desteklemez ve önlenmiş veya kabul çeşitli senaryolar listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="bc47d-118">Lists various scenarios that do not support a particular aspect of security and should be avoided or considered.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="bc47d-119">Başvuru</span><span class="sxs-lookup"><span data-stu-id="bc47d-119">Reference</span></span>  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a><span data-ttu-id="bc47d-120">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="bc47d-120">Related Sections</span></span>  
 [<span data-ttu-id="bc47d-121">Güvenlik Kılavuzu ve En İyi Uygulamalar</span><span class="sxs-lookup"><span data-stu-id="bc47d-121">Security Guidance and Best Practices</span></span>](../../../../docs/framework/wcf/feature-details/security-guidance-and-best-practices.md)  
  
## <a name="see-also"></a><span data-ttu-id="bc47d-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bc47d-122">See also</span></span>
- [<span data-ttu-id="bc47d-123">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="bc47d-123">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)
