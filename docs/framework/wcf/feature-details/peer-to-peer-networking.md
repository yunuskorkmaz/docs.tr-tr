---
title: Eşler Arası Ağ
ms.date: 03/30/2017
ms.assetid: ad6cb67b-fd1c-4ca1-a767-b410da2e16ca
ms.openlocfilehash: 388f6659602276cd3f356da2af63e4d31b5e22d6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62046416"
---
# <a name="peer-to-peer-networking"></a><span data-ttu-id="955a5-102">Eşler Arası Ağ</span><span class="sxs-lookup"><span data-stu-id="955a5-102">Peer-to-Peer Networking</span></span>
<span data-ttu-id="955a5-103">Eş kanal bir misyonumuz, eşler arası (P2P) iletişimi Windows Communication Foundation (WCF) teknolojisidir.</span><span class="sxs-lookup"><span data-stu-id="955a5-103">Peer Channel is a multiparty, peer-to-peer (P2P) communication technology in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="955a5-104">Bu, uygulama geliştiricileri için bir güvenli ve ölçeklenebilir ileti tabanlı P2P iletişim kanalını sağlar.</span><span class="sxs-lookup"><span data-stu-id="955a5-104">It provides a secure and scalable message-based P2P communication channel for application developers.</span></span> <span data-ttu-id="955a5-105">Bir ortak eş kanaldan yararlanabilir misyonumuz bir uygulama gibi sohbet, işbirliğine dayalı bir uygulama sunucuları olmadan bir eşler arası şekilde kişiler sohbet birbiriyle grubu burada örneğidir.</span><span class="sxs-lookup"><span data-stu-id="955a5-105">One common example of a multiparty application that can benefit from Peer Channel is a collaborative application, such as chat, where a group of people chat with one another in a peer-to-peer manner without servers.</span></span> <span data-ttu-id="955a5-106">Eş kanal P2P işbirliği, içerik dağıtımı, Yük Dengeleme sağlar ve tüketici ve kurumsal senaryolar için işleme dağıtılmış.</span><span class="sxs-lookup"><span data-stu-id="955a5-106">Peer Channel enables P2P collaboration, content distribution, load balancing, and distributed processing for both consumer and enterprise scenarios.</span></span>  
  
 <span data-ttu-id="955a5-107">Eş kanal üzerinde varsayılan olarak etkindir [!INCLUDE[wv](../../../../includes/wv-md.md)]tüm WCF gibi.</span><span class="sxs-lookup"><span data-stu-id="955a5-107">Peer Channel is enabled by default on [!INCLUDE[wv](../../../../includes/wv-md.md)], as is all of WCF.</span></span> <span data-ttu-id="955a5-108">Eş kanal sınıfları erişmeye System.ServiceModel.dll başvuruları projenize ekleyin.</span><span class="sxs-lookup"><span data-stu-id="955a5-108">To access Peer Channel classes, add references to System.ServiceModel.dll to your project.</span></span>  
  
 <span data-ttu-id="955a5-109">Aşağıdaki bölümler, eşler arası ağ ve ağ eş özellikli uygulamalar oluşturmak için eş kanalı sınıfları kullanımı hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="955a5-109">The following sections contain information about peer-to-peer networking and the use of Peer Channel classes to create peer-enabled network applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="955a5-110">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="955a5-110">In This Section</span></span>  
 <span data-ttu-id="955a5-111">[Eş kanal senaryoları](../../../../docs/framework/wcf/feature-details/peer-channel-scenarios.md):  Eş kanal API'leri tarafından desteklenen geliştirme senaryoları gibi Mesajlaşma, işbirliği, yayımlama/abonelik ve oyun dağıtılmış açıklar.</span><span class="sxs-lookup"><span data-stu-id="955a5-111">[Peer Channel Scenarios](../../../../docs/framework/wcf/feature-details/peer-channel-scenarios.md):  Describes development scenarios supported by the Peer Channel APIs, such as publication/subscription messaging, collaboration, distributed processing, and gaming.</span></span>  
  
 <span data-ttu-id="955a5-112">[Eş kanal kavramları](../../../../docs/framework/wcf/feature-details/peer-channel-concepts.md):  Eş kafesleri, eş düğümleri, eş kanalı güvenliği ve eş çözücüler açıklar.</span><span class="sxs-lookup"><span data-stu-id="955a5-112">[Peer Channel Concepts](../../../../docs/framework/wcf/feature-details/peer-channel-concepts.md):  Describes Peer Meshes, Peer Nodes, Peer Channel security, and Peer Resolvers.</span></span>  
  
 <span data-ttu-id="955a5-113">[Eş kanal uygulaması oluşturma](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md):  Eş kanalı uygulamalarını geliştirmeye konusunda rehberlik yapmaktadır.</span><span class="sxs-lookup"><span data-stu-id="955a5-113">[Building a Peer Channel Application](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md):  Provides guidance on developing Peer Channel applications.</span></span>  
  
## <a name="peer-channel-code-examples"></a><span data-ttu-id="955a5-114">Eş kanal kod örnekleri</span><span class="sxs-lookup"><span data-stu-id="955a5-114">Peer Channel Code Examples</span></span>  
 <span data-ttu-id="955a5-115">[Eş kanal özel eş çözümleyici](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751466(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="955a5-115">[Peer Channel Custom Peer Resolver](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751466(v=vs.90))</span></span>  
  
## <a name="peer-channel-team-blog"></a><span data-ttu-id="955a5-116">Eş kanal ekip blogu</span><span class="sxs-lookup"><span data-stu-id="955a5-116">Peer Channel Team blog</span></span>  
 [<span data-ttu-id="955a5-117">Eş kanal ekip blogu</span><span class="sxs-lookup"><span data-stu-id="955a5-117">Peer Channel Team Blog</span></span>](https://go.microsoft.com/fwlink/?LinkID=114530)
