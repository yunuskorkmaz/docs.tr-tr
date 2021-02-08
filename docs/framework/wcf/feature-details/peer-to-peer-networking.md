---
description: 'Daha fazla bilgi edinin: eşler arası ağ oluşturma'
title: Eşler Arası Ağ
ms.date: 03/30/2017
ms.assetid: ad6cb67b-fd1c-4ca1-a767-b410da2e16ca
ms.openlocfilehash: 39ca4580c5b00b3962247d45ba3f60926035ea58
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793655"
---
# <a name="peer-to-peer-networking"></a><span data-ttu-id="16e5c-103">Eşler Arası Ağ</span><span class="sxs-lookup"><span data-stu-id="16e5c-103">Peer-to-Peer Networking</span></span>

<span data-ttu-id="16e5c-104">Eş kanal, Windows Communication Foundation (WCF) ' de çok taraf, eşler arası (P2P) iletişim teknolojisidir.</span><span class="sxs-lookup"><span data-stu-id="16e5c-104">Peer Channel is a multiparty, peer-to-peer (P2P) communication technology in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="16e5c-105">Uygulama geliştiricileri için güvenli ve ölçeklenebilir ileti tabanlı bir P2P iletişim kanalı sağlar.</span><span class="sxs-lookup"><span data-stu-id="16e5c-105">It provides a secure and scalable message-based P2P communication channel for application developers.</span></span> <span data-ttu-id="16e5c-106">Eş kanaldan faydalanabilir bir çok taraflı uygulamanın yaygın bir örneği, sohbet gibi işbirliğine dayalı bir uygulamadır. Örneğin, bir kişi grubu, sunucular olmadan eşler arası bir şekilde bir başkası ile sohbet edebilir.</span><span class="sxs-lookup"><span data-stu-id="16e5c-106">One common example of a multiparty application that can benefit from Peer Channel is a collaborative application, such as chat, where a group of people chat with one another in a peer-to-peer manner without servers.</span></span> <span data-ttu-id="16e5c-107">Eş kanal, hem tüketici hem de kurumsal senaryolar için P2P işbirliği, içerik dağıtımı, yük dengeleme ve dağıtılmış işleme imkanı sunar.</span><span class="sxs-lookup"><span data-stu-id="16e5c-107">Peer Channel enables P2P collaboration, content distribution, load balancing, and distributed processing for both consumer and enterprise scenarios.</span></span>  
  
 <span data-ttu-id="16e5c-108">Tüm WCF 'de olduğu gibi, eş kanal Windows Vista 'da varsayılan olarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="16e5c-108">Peer Channel is enabled by default on Windows Vista, as is all of WCF.</span></span> <span data-ttu-id="16e5c-109">Eş kanal sınıflarına erişmek için System.ServiceModel.dll başvuruları projenize ekleyin.</span><span class="sxs-lookup"><span data-stu-id="16e5c-109">To access Peer Channel classes, add references to System.ServiceModel.dll to your project.</span></span>  
  
 <span data-ttu-id="16e5c-110">Aşağıdaki bölümlerde eşler arası ağ oluşturma ve eş kanal sınıflarının kullanımı ile eş özellikli ağ uygulamaları oluşturma hakkında bilgiler yer verilmektedir.</span><span class="sxs-lookup"><span data-stu-id="16e5c-110">The following sections contain information about peer-to-peer networking and the use of Peer Channel classes to create peer-enabled network applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="16e5c-111">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="16e5c-111">In This Section</span></span>  

 <span data-ttu-id="16e5c-112">[Eş kanal senaryoları](peer-channel-scenarios.md): yayın/abonelik mesajlaşma, işbirliği, dağıtılmış işlem ve oyun gibi eş kanal API 'leri tarafından desteklenen geliştirme senaryolarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="16e5c-112">[Peer Channel Scenarios](peer-channel-scenarios.md):  Describes development scenarios supported by the Peer Channel APIs, such as publication/subscription messaging, collaboration, distributed processing, and gaming.</span></span>  
  
 <span data-ttu-id="16e5c-113">[Eş kanal kavramları](peer-channel-concepts.md): eşdüzey kafesler, Eş düğümleri, eş kanal güvenliği ve eş çözümleyiciler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="16e5c-113">[Peer Channel Concepts](peer-channel-concepts.md):  Describes Peer Meshes, Peer Nodes, Peer Channel security, and Peer Resolvers.</span></span>  
  
 <span data-ttu-id="16e5c-114">[Eş kanal uygulaması oluşturma](building-a-peer-channel-application.md): eş kanal uygulamaları geliştirme hakkında rehberlik sağlar.</span><span class="sxs-lookup"><span data-stu-id="16e5c-114">[Building a Peer Channel Application](building-a-peer-channel-application.md):  Provides guidance on developing Peer Channel applications.</span></span>  
  
## <a name="peer-channel-code-examples"></a><span data-ttu-id="16e5c-115">Eş kanal kodu örnekleri</span><span class="sxs-lookup"><span data-stu-id="16e5c-115">Peer Channel Code Examples</span></span>  

 <span data-ttu-id="16e5c-116">[Eş kanal özel eş Çözümleyicisi](/previous-versions/dotnet/netframework-3.5/ms751466(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="16e5c-116">[Peer Channel Custom Peer Resolver](/previous-versions/dotnet/netframework-3.5/ms751466(v=vs.90))</span></span>  
  
## <a name="peer-channel-team-blog"></a><span data-ttu-id="16e5c-117">Eş kanal ekip blogu</span><span class="sxs-lookup"><span data-stu-id="16e5c-117">Peer Channel Team blog</span></span>  

 [<span data-ttu-id="16e5c-118">Eş kanal ekip blogu</span><span class="sxs-lookup"><span data-stu-id="16e5c-118">Peer Channel Team Blog</span></span>](/archive/blogs/peerchan/)
