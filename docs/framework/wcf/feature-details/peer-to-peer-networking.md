---
title: "Eşler Arası Ağ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ad6cb67b-fd1c-4ca1-a767-b410da2e16ca
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d3ef21d4ab431ea4e1e1ac0392b3f088a7053c80
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="peer-to-peer-networking"></a><span data-ttu-id="ba4cd-102">Eşler Arası Ağ</span><span class="sxs-lookup"><span data-stu-id="ba4cd-102">Peer-to-Peer Networking</span></span>
<span data-ttu-id="ba4cd-103">Eş kanal, çok taraflı, eşler arası (P2P) iletişim teknolojisinde [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ba4cd-103">Peer Channel is a multiparty, peer-to-peer (P2P) communication technology in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span> <span data-ttu-id="ba4cd-104">Bu uygulama geliştiricileri için bir güvenli ve ölçeklenebilir ileti tabanlı P2P iletişim kanalını sağlar.</span><span class="sxs-lookup"><span data-stu-id="ba4cd-104">It provides a secure and scalable message-based P2P communication channel for application developers.</span></span> <span data-ttu-id="ba4cd-105">Bir ortak eş kanaldan yararlanabilir taraflı bir uygulama gibi sohbet, ortak bir uygulama sunucuları olmadan bir eşler arası şekilde birbiriyle kişiler sohbet birtakım burada örnektir.</span><span class="sxs-lookup"><span data-stu-id="ba4cd-105">One common example of a multiparty application that can benefit from Peer Channel is a collaborative application, such as chat, where a group of people chat with one another in a peer-to-peer manner without servers.</span></span> <span data-ttu-id="ba4cd-106">Eş kanal P2P işbirliği, içerik dağıtımı, Yük Dengeleme sağlar ve tüketici ve kurumsal senaryoları için işleme dağıtılmış.</span><span class="sxs-lookup"><span data-stu-id="ba4cd-106">Peer Channel enables P2P collaboration, content distribution, load balancing, and distributed processing for both consumer and enterprise scenarios.</span></span>  
  
 <span data-ttu-id="ba4cd-107">Eş kanal üzerinde varsayılan olarak etkindir [!INCLUDE[wv](../../../../includes/wv-md.md)]tüm gibi [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ba4cd-107">Peer Channel is enabled by default on [!INCLUDE[wv](../../../../includes/wv-md.md)], as is all of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="ba4cd-108">Eş kanal sınıflara erişmek için System.ServiceModel.dll başvurular projenize ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ba4cd-108">To access Peer Channel classes, add references to System.ServiceModel.dll to your project.</span></span>  
  
 <span data-ttu-id="ba4cd-109">Aşağıdaki bölümler, eşler arası ağ ve eş özellikli ağ uygulamaları oluşturmak için eş kanalı sınıfları kullanımı hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="ba4cd-109">The following sections contain information about peer-to-peer networking and the use of Peer Channel classes to create peer-enabled network applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ba4cd-110">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="ba4cd-110">In This Section</span></span>  
 <span data-ttu-id="ba4cd-111">[Eş kanal senaryoları](../../../../docs/framework/wcf/feature-details/peer-channel-scenarios.md): yayımlama/abonelik, işbirliği, ileti işleme ve oyun dağıtılmış gibi eş kanal API tarafından desteklenen geliştirme senaryolar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ba4cd-111">[Peer Channel Scenarios](../../../../docs/framework/wcf/feature-details/peer-channel-scenarios.md):  Describes development scenarios supported by the Peer Channel APIs, such as publication/subscription messaging, collaboration, distributed processing, and gaming.</span></span>  
  
 <span data-ttu-id="ba4cd-112">[Eş kanal kavramları](../../../../docs/framework/wcf/feature-details/peer-channel-concepts.md): Eş düğümleri, eş kanalı güvenliği ve eş çözücüler eş kafesleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="ba4cd-112">[Peer Channel Concepts](../../../../docs/framework/wcf/feature-details/peer-channel-concepts.md):  Describes Peer Meshes, Peer Nodes, Peer Channel security, and Peer Resolvers.</span></span>  
  
 <span data-ttu-id="ba4cd-113">[Eş kanal uygulaması oluşturma](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md): Eş kanalı uygulamalarını geliştirmeye rehberlik sağlar.</span><span class="sxs-lookup"><span data-stu-id="ba4cd-113">[Building a Peer Channel Application](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md):  Provides guidance on developing Peer Channel applications.</span></span>  
  
## <a name="peer-channel-code-examples"></a><span data-ttu-id="ba4cd-114">Eş kanal kod örnekleri</span><span class="sxs-lookup"><span data-stu-id="ba4cd-114">Peer Channel Code Examples</span></span>  
 [<span data-ttu-id="ba4cd-115">Eş kanal özel eş Çözümleyicisi</span><span class="sxs-lookup"><span data-stu-id="ba4cd-115">Peer Channel Custom Peer Resolver</span></span>](http://msdn.microsoft.com/en-us/5b75a2bb-7ff1-4a14-abe7-3debf0537d23)  
  
## <a name="peer-channel-team-blog"></a><span data-ttu-id="ba4cd-116">Eş kanal ekip blogu</span><span class="sxs-lookup"><span data-stu-id="ba4cd-116">Peer Channel Team blog</span></span>  
 <span data-ttu-id="ba4cd-117">[Eş kanal ekip blogu](http://go.microsoft.com/fwlink/?LinkID=114530) (http://go.microsoft.com/fwlink/?LinkID=114530)</span><span class="sxs-lookup"><span data-stu-id="ba4cd-117">[Peer Channel Team Blog](http://go.microsoft.com/fwlink/?LinkID=114530) (http://go.microsoft.com/fwlink/?LinkID=114530)</span></span>
