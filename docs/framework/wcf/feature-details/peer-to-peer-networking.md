---
title: Eşler Arası Ağ
ms.date: 03/30/2017
ms.assetid: ad6cb67b-fd1c-4ca1-a767-b410da2e16ca
ms.openlocfilehash: 2905a429e907f7e97c482c22229a6bc928c52243
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744679"
---
# <a name="peer-to-peer-networking"></a><span data-ttu-id="f7482-102">Eşler Arası Ağ</span><span class="sxs-lookup"><span data-stu-id="f7482-102">Peer-to-Peer Networking</span></span>
<span data-ttu-id="f7482-103">Eş kanal, Windows Communication Foundation (WCF) ' de çok taraf, eşler arası (P2P) iletişim teknolojisidir.</span><span class="sxs-lookup"><span data-stu-id="f7482-103">Peer Channel is a multiparty, peer-to-peer (P2P) communication technology in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="f7482-104">Uygulama geliştiricileri için güvenli ve ölçeklenebilir ileti tabanlı bir P2P iletişim kanalı sağlar.</span><span class="sxs-lookup"><span data-stu-id="f7482-104">It provides a secure and scalable message-based P2P communication channel for application developers.</span></span> <span data-ttu-id="f7482-105">Eş kanaldan faydalanabilir bir çok taraflı uygulamanın yaygın bir örneği, sohbet gibi işbirliğine dayalı bir uygulamadır. Örneğin, bir kişi grubu, sunucular olmadan eşler arası bir şekilde bir başkası ile sohbet edebilir.</span><span class="sxs-lookup"><span data-stu-id="f7482-105">One common example of a multiparty application that can benefit from Peer Channel is a collaborative application, such as chat, where a group of people chat with one another in a peer-to-peer manner without servers.</span></span> <span data-ttu-id="f7482-106">Eş kanal, hem tüketici hem de kurumsal senaryolar için P2P işbirliği, içerik dağıtımı, yük dengeleme ve dağıtılmış işleme imkanı sunar.</span><span class="sxs-lookup"><span data-stu-id="f7482-106">Peer Channel enables P2P collaboration, content distribution, load balancing, and distributed processing for both consumer and enterprise scenarios.</span></span>  
  
 <span data-ttu-id="f7482-107">Tüm WCF 'de olduğu gibi, eş kanal Windows Vista 'da varsayılan olarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="f7482-107">Peer Channel is enabled by default on Windows Vista, as is all of WCF.</span></span> <span data-ttu-id="f7482-108">Eş kanal sınıflarına erişmek için System. ServiceModel. dll dosyasına başvuruları projenize ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f7482-108">To access Peer Channel classes, add references to System.ServiceModel.dll to your project.</span></span>  
  
 <span data-ttu-id="f7482-109">Aşağıdaki bölümlerde eşler arası ağ oluşturma ve eş kanal sınıflarının kullanımı ile eş özellikli ağ uygulamaları oluşturma hakkında bilgiler yer verilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f7482-109">The following sections contain information about peer-to-peer networking and the use of Peer Channel classes to create peer-enabled network applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f7482-110">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="f7482-110">In This Section</span></span>  
 <span data-ttu-id="f7482-111">[Eş kanal senaryoları](../../../../docs/framework/wcf/feature-details/peer-channel-scenarios.md): yayın/abonelik mesajlaşma, işbirliği, dağıtılmış işlem ve oyun gibi eş kanal API 'leri tarafından desteklenen geliştirme senaryolarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="f7482-111">[Peer Channel Scenarios](../../../../docs/framework/wcf/feature-details/peer-channel-scenarios.md):  Describes development scenarios supported by the Peer Channel APIs, such as publication/subscription messaging, collaboration, distributed processing, and gaming.</span></span>  
  
 <span data-ttu-id="f7482-112">[Eş kanal kavramları](../../../../docs/framework/wcf/feature-details/peer-channel-concepts.md): eşdüzey kafesler, Eş düğümleri, eş kanal güvenliği ve eş çözümleyiciler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f7482-112">[Peer Channel Concepts](../../../../docs/framework/wcf/feature-details/peer-channel-concepts.md):  Describes Peer Meshes, Peer Nodes, Peer Channel security, and Peer Resolvers.</span></span>  
  
 <span data-ttu-id="f7482-113">[Eş kanal uygulaması oluşturma](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md): eş kanal uygulamaları geliştirme hakkında rehberlik sağlar.</span><span class="sxs-lookup"><span data-stu-id="f7482-113">[Building a Peer Channel Application](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md):  Provides guidance on developing Peer Channel applications.</span></span>  
  
## <a name="peer-channel-code-examples"></a><span data-ttu-id="f7482-114">Eş kanal kodu örnekleri</span><span class="sxs-lookup"><span data-stu-id="f7482-114">Peer Channel Code Examples</span></span>  
 <span data-ttu-id="f7482-115">[Eş kanal özel eş Çözümleyicisi](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751466(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="f7482-115">[Peer Channel Custom Peer Resolver](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751466(v=vs.90))</span></span>  
  
## <a name="peer-channel-team-blog"></a><span data-ttu-id="f7482-116">Eş kanal ekip blogu</span><span class="sxs-lookup"><span data-stu-id="f7482-116">Peer Channel Team blog</span></span>  
 [<span data-ttu-id="f7482-117">Eş kanal ekip blogu</span><span class="sxs-lookup"><span data-stu-id="f7482-117">Peer Channel Team Blog</span></span>](https://docs.microsoft.com/archive/blogs/peerchan/)
