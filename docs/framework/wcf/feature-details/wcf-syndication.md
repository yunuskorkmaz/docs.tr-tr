---
title: WCF Dağıtımı
ms.date: 03/30/2017
helpviewer_keywords:
- syndication [WCF]
ms.assetid: ebf80384-0fc9-4919-a1e8-23ca2a13e300
ms.openlocfilehash: 825990c6c1690281af65d53c76dcca0f3e2ffb67
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239048"
---
# <a name="wcf-syndication"></a><span data-ttu-id="2e49a-102">WCF Dağıtımı</span><span class="sxs-lookup"><span data-stu-id="2e49a-102">WCF Syndication</span></span>

<span data-ttu-id="2e49a-103">Windows Communication Foundation (WCF), atom, RSS veya diğer özel biçimlerdeki dağıtım akışlarıyla kolayca çalışmak için destek sağlar; bu sayede bunları okuyup oluşturabilir ve bunları bir hizmet uç noktasında kullanıma sunabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2e49a-103">Windows Communication Foundation (WCF) provides support to easily work with syndication feeds in Atom, RSS or other custom formats, which allows you to read and create them as well as expose them on a service endpoint.</span></span> <span data-ttu-id="2e49a-104">Bu bölümdeki konularda, bu programlama modeli ayrıntılı dağıtım için açıklanır.</span><span class="sxs-lookup"><span data-stu-id="2e49a-104">The topics in this section describe this programming model for syndication in detail.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2e49a-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="2e49a-105">In This Section</span></span>  

 [<span data-ttu-id="2e49a-106">WCF Dağıtımı Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="2e49a-106">WCF Syndication Overview</span></span>](wcf-syndication-overview.md)  
 <span data-ttu-id="2e49a-107">WCF tarafından sağlanan dağıtım desteğine genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="2e49a-107">Provides an overview of syndication support provided by WCF.</span></span>  
  
 [<span data-ttu-id="2e49a-108">Dağıtım Mimarisi</span><span class="sxs-lookup"><span data-stu-id="2e49a-108">Architecture of Syndication</span></span>](architecture-of-syndication.md)  
 <span data-ttu-id="2e49a-109">Nesne modelindeki sınıfları ve Dağıtım Genişletilebilirliği açıklar.</span><span class="sxs-lookup"><span data-stu-id="2e49a-109">Describes the classes in the object model and the extensibility of syndication.</span></span>  
  
 [<span data-ttu-id="2e49a-110">WCF Dağıtım Nesnesi Modeli Atom ve RSS Eşlemelerini Nasıl Yapar?</span><span class="sxs-lookup"><span data-stu-id="2e49a-110">How the WCF Syndication Object Model Maps to Atom and RSS</span></span>](how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md)  
 <span data-ttu-id="2e49a-111">Özet akışlarının WCF dağıtım nesne modeli içinde nasıl temsil edileceğini ve bunların RSS ve Atom akışlarına nasıl dönüştürüleceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="2e49a-111">Describes how feeds are represented within the WCF Syndication Object Model and how they are converted to RSS and Atom feeds.</span></span>  
  
 [<span data-ttu-id="2e49a-112">Nasıl yapılır: Temel Bir RSS Akışı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="2e49a-112">How to: Create a Basic RSS Feed</span></span>](how-to-create-a-basic-rss-feed.md)  
 <span data-ttu-id="2e49a-113">Temel RSS akışını kullanılabilir hale getiren bir hizmetin nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2e49a-113">Shows how to create a service that makes a basic RSS feed available.</span></span>  
  
 [<span data-ttu-id="2e49a-114">Nasıl yapılır: Temel Bir Atom Akışı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="2e49a-114">How to: Create a Basic Atom Feed</span></span>](how-to-create-a-basic-atom-feed.md)  
 <span data-ttu-id="2e49a-115">Temel bir ATOM akışını kullanılabilir hale getiren bir hizmetin nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2e49a-115">Shows how to create a service that makes a basic ATOM feed available.</span></span>  
  
 [<span data-ttu-id="2e49a-116">Nasıl yapılır: Bir Akışı Hem Atom Hem de RSS Olarak Kullanıma Sunma</span><span class="sxs-lookup"><span data-stu-id="2e49a-116">How to: Expose a Feed as Both Atom and RSS</span></span>](how-to-expose-a-feed-as-both-atom-and-rss.md)  
 <span data-ttu-id="2e49a-117">Aynı akışın ATOM ve RSS ile kullanılabilir olmasını sağlayan bir hizmetin nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2e49a-117">Shows how to create a service that makes the same feed available with ATOM and RSS.</span></span>  
  
 [<span data-ttu-id="2e49a-118">Dağıtım Genişletilebilirliği</span><span class="sxs-lookup"><span data-stu-id="2e49a-118">Syndication Extensibility</span></span>](syndication-extensibility.md)  
 <span data-ttu-id="2e49a-119">Bir dağıtım akışına özel öğeler ve öznitelikler ekleme yöntemlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="2e49a-119">Describes the methods of adding custom elements and attributes to a syndication feed.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="2e49a-120">Başvuru</span><span class="sxs-lookup"><span data-stu-id="2e49a-120">Reference</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="2e49a-121">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="2e49a-121">Related Sections</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e49a-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2e49a-122">See also</span></span>

- [<span data-ttu-id="2e49a-123">WCF Web HTTP Programlama Modeli</span><span class="sxs-lookup"><span data-stu-id="2e49a-123">WCF Web HTTP Programming Model</span></span>](wcf-web-http-programming-model.md)
- [<span data-ttu-id="2e49a-124">Kısmi Güven</span><span class="sxs-lookup"><span data-stu-id="2e49a-124">Partial Trust</span></span>](partial-trust.md)
