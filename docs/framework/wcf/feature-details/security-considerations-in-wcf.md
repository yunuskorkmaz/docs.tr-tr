---
description: Daha fazla bilgi için bkz. WCF 'de güvenlik konuları
title: WCF'de Güvenlik Değerlendirmeleri
ms.date: 03/30/2017
helpviewer_keywords:
- security [WCF]
- Windows Communication Foundation, security
- WCF, security
ms.assetid: 42055ee0-6d0c-443d-9d89-788dfc345d6d
ms.openlocfilehash: d75ff0d6eede4a46a5b795873e83445a04532993
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99632483"
---
# <a name="security-considerations-in-wcf"></a><span data-ttu-id="7c968-103">WCF'de Güvenlik Değerlendirmeleri</span><span class="sxs-lookup"><span data-stu-id="7c968-103">Security Considerations in WCF</span></span>

<span data-ttu-id="7c968-104">Bu bölümdeki konularda, Windows Communication Foundation (WCF) uygulaması tasarlarken göz önünde bulundurmanız gereken güvenlikle ilgili çeşitli öğeler listelenir.</span><span class="sxs-lookup"><span data-stu-id="7c968-104">The topics in this section list various security-related items to consider when designing a Windows Communication Foundation (WCF) application.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7c968-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="7c968-105">In This Section</span></span>  

 [<span data-ttu-id="7c968-106">Bilgilerin Açığa Çıkması</span><span class="sxs-lookup"><span data-stu-id="7c968-106">Information Disclosure</span></span>](information-disclosure.md)  
 <span data-ttu-id="7c968-107">Bilgilerin açıklanmasında veya saldırıya neden olabilecek çeşitli yollar ve bunun nasıl azaltılacağını ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7c968-107">Discusses the various ways that information can be disclosed or attacked, and how to mitigate this.</span></span>  
  
 [<span data-ttu-id="7c968-108">Ayrıcalık Yükseltme</span><span class="sxs-lookup"><span data-stu-id="7c968-108">Elevation of Privilege</span></span>](elevation-of-privilege.md)  
 <span data-ttu-id="7c968-109">Başlangıçta verilen ve bu sorunu hafifletmenin ötesinde bir saldırgan yetkilendirme izinleri verme etkilerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="7c968-109">Discusses the effects of giving an attacker authorization permissions beyond those initially granted and how to mitigate this.</span></span>  
  
 [<span data-ttu-id="7c968-110">Hizmet Reddi</span><span class="sxs-lookup"><span data-stu-id="7c968-110">Denial of Service</span></span>](denial-of-service.md)  
 <span data-ttu-id="7c968-111">Bir sistem iletileri uygun şekilde işleyemezse ne olduğunu ve bunun nasıl azaltılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="7c968-111">Discusses what happens when a system is unable to process messages appropriately and how to mitigate it.</span></span>  
  
 [<span data-ttu-id="7c968-112">Kurcalama</span><span class="sxs-lookup"><span data-stu-id="7c968-112">Tampering</span></span>](tampering.md)  
 <span data-ttu-id="7c968-113">İletilerin değiştirilmesini veya iletilerin teslimini ve bunun nasıl azaltılacağını ele alır.</span><span class="sxs-lookup"><span data-stu-id="7c968-113">Discusses the altering of messages or the delivery of messages and how to mitigate it.</span></span>  
  
 [<span data-ttu-id="7c968-114">Yeniden Yürütme Saldırıları</span><span class="sxs-lookup"><span data-stu-id="7c968-114">Replay Attacks</span></span>](replay-attacks.md)  
 <span data-ttu-id="7c968-115">Bir saldırgan bir ileti akışını iki taraf arasında kopyaladığında ne olduğunu ve akışın bir veya daha fazla tarafın akışını yeniden oynadığını ve bunun nasıl azaltılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="7c968-115">Discusses what happens when an attacker copies a stream of messages between two parties and replays the stream to one or more of the parties, and how to mitigate this.</span></span>  
  
 [<span data-ttu-id="7c968-116">Güvenli Oturumlar için Güvenlikli İlgili Önemli Noktalar</span><span class="sxs-lookup"><span data-stu-id="7c968-116">Security Considerations for Secure Sessions</span></span>](security-considerations-for-secure-sessions.md)  
 <span data-ttu-id="7c968-117">Güvenli oturumları uygularken güvenliği etkileyen aşağıdaki öğeleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="7c968-117">Discusses the following items that affect security when implementing secure sessions.</span></span>  
  
 [<span data-ttu-id="7c968-118">Desteklenmeyen Senaryolar</span><span class="sxs-lookup"><span data-stu-id="7c968-118">Unsupported Scenarios</span></span>](unsupported-scenarios.md)  
 <span data-ttu-id="7c968-119">Belirli güvenlik yönlerini desteklemeyen çeşitli senaryolar listeler ve kaçınılması veya dikkate alınmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="7c968-119">Lists various scenarios that do not support a particular aspect of security and should be avoided or considered.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="7c968-120">Başvuru</span><span class="sxs-lookup"><span data-stu-id="7c968-120">Reference</span></span>  

 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a><span data-ttu-id="7c968-121">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="7c968-121">Related Sections</span></span>  

 [<span data-ttu-id="7c968-122">Güvenlik Kılavuzu ve En İyi Uygulamalar</span><span class="sxs-lookup"><span data-stu-id="7c968-122">Security Guidance and Best Practices</span></span>](security-guidance-and-best-practices.md)  
  
## <a name="see-also"></a><span data-ttu-id="7c968-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7c968-123">See also</span></span>

- [<span data-ttu-id="7c968-124">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="7c968-124">Security</span></span>](security.md)
