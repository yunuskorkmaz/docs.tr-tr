---
title: Eşler Arası Ağ
ms.date: 03/30/2017
ms.assetid: ad6cb67b-fd1c-4ca1-a767-b410da2e16ca
ms.openlocfilehash: 16416ec467caa10216930ae3c961869cbfcd59d8
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43516338"
---
# <a name="peer-to-peer-networking"></a><span data-ttu-id="4347c-102">Eşler Arası Ağ</span><span class="sxs-lookup"><span data-stu-id="4347c-102">Peer-to-Peer Networking</span></span>
<span data-ttu-id="4347c-103">Eş kanal bir misyonumuz, eşler arası (P2P) iletişimi Windows Communication Foundation (WCF) teknolojisidir.</span><span class="sxs-lookup"><span data-stu-id="4347c-103">Peer Channel is a multiparty, peer-to-peer (P2P) communication technology in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="4347c-104">Bu, uygulama geliştiricileri için bir güvenli ve ölçeklenebilir ileti tabanlı P2P iletişim kanalını sağlar.</span><span class="sxs-lookup"><span data-stu-id="4347c-104">It provides a secure and scalable message-based P2P communication channel for application developers.</span></span> <span data-ttu-id="4347c-105">Bir ortak eş kanaldan yararlanabilir misyonumuz bir uygulama gibi sohbet, işbirliğine dayalı bir uygulama sunucuları olmadan bir eşler arası şekilde kişiler sohbet birbiriyle grubu burada örneğidir.</span><span class="sxs-lookup"><span data-stu-id="4347c-105">One common example of a multiparty application that can benefit from Peer Channel is a collaborative application, such as chat, where a group of people chat with one another in a peer-to-peer manner without servers.</span></span> <span data-ttu-id="4347c-106">Eş kanal P2P işbirliği, içerik dağıtımı, Yük Dengeleme sağlar ve tüketici ve kurumsal senaryolar için işleme dağıtılmış.</span><span class="sxs-lookup"><span data-stu-id="4347c-106">Peer Channel enables P2P collaboration, content distribution, load balancing, and distributed processing for both consumer and enterprise scenarios.</span></span>  
  
 <span data-ttu-id="4347c-107">Eş kanal üzerinde varsayılan olarak etkindir [!INCLUDE[wv](../../../../includes/wv-md.md)]tüm WCF gibi.</span><span class="sxs-lookup"><span data-stu-id="4347c-107">Peer Channel is enabled by default on [!INCLUDE[wv](../../../../includes/wv-md.md)], as is all of WCF.</span></span> <span data-ttu-id="4347c-108">Eş kanal sınıfları erişmeye System.ServiceModel.dll başvuruları projenize ekleyin.</span><span class="sxs-lookup"><span data-stu-id="4347c-108">To access Peer Channel classes, add references to System.ServiceModel.dll to your project.</span></span>  
  
 <span data-ttu-id="4347c-109">Aşağıdaki bölümler, eşler arası ağ ve ağ eş özellikli uygulamalar oluşturmak için eş kanalı sınıfları kullanımı hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="4347c-109">The following sections contain information about peer-to-peer networking and the use of Peer Channel classes to create peer-enabled network applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4347c-110">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="4347c-110">In This Section</span></span>  
 <span data-ttu-id="4347c-111">[Eş kanal senaryoları](../../../../docs/framework/wcf/feature-details/peer-channel-scenarios.md): gibi Mesajlaşma, işbirliği, yayımlama/abonelik ve oyun dağıtılmış eş kanalı API'leri tarafından desteklenen geliştirme senaryoları açıklar.</span><span class="sxs-lookup"><span data-stu-id="4347c-111">[Peer Channel Scenarios](../../../../docs/framework/wcf/feature-details/peer-channel-scenarios.md):  Describes development scenarios supported by the Peer Channel APIs, such as publication/subscription messaging, collaboration, distributed processing, and gaming.</span></span>  
  
 <span data-ttu-id="4347c-112">[Eş kanal kavramları](../../../../docs/framework/wcf/feature-details/peer-channel-concepts.md): Eş düğümleri, eş kanalı güvenliği ve eş çözücüler eş kafesleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="4347c-112">[Peer Channel Concepts](../../../../docs/framework/wcf/feature-details/peer-channel-concepts.md):  Describes Peer Meshes, Peer Nodes, Peer Channel security, and Peer Resolvers.</span></span>  
  
 <span data-ttu-id="4347c-113">[Eş kanal uygulaması oluşturma](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md): Eş kanalı uygulamalarını geliştirmeye rehberlik sağlar.</span><span class="sxs-lookup"><span data-stu-id="4347c-113">[Building a Peer Channel Application](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md):  Provides guidance on developing Peer Channel applications.</span></span>  
  
## <a name="peer-channel-code-examples"></a><span data-ttu-id="4347c-114">Eş kanal kod örnekleri</span><span class="sxs-lookup"><span data-stu-id="4347c-114">Peer Channel Code Examples</span></span>  
 [<span data-ttu-id="4347c-115">Eş kanal özel eş çözümleyici</span><span class="sxs-lookup"><span data-stu-id="4347c-115">Peer Channel Custom Peer Resolver</span></span>](https://msdn.microsoft.com/library/5b75a2bb-7ff1-4a14-abe7-3debf0537d23)  
  
## <a name="peer-channel-team-blog"></a><span data-ttu-id="4347c-116">Eş kanal ekip blogu</span><span class="sxs-lookup"><span data-stu-id="4347c-116">Peer Channel Team blog</span></span>  
 [<span data-ttu-id="4347c-117">Eş kanal ekip blogu</span><span class="sxs-lookup"><span data-stu-id="4347c-117">Peer Channel Team Blog</span></span>](https://go.microsoft.com/fwlink/?LinkID=114530)
