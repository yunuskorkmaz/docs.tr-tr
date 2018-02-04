---
title: "Eşler arası işbirliği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b6216d88-bccb-4a59-9f1c-9f751708e811
caps.latest.revision: 
author: mcleblanc
ms.author: markl
manager: markl
ms.workload:
- dotnet
ms.openlocfilehash: 5060e12fb6a9fcc1bac1dfe6ccdcbaea9f2e6385
ms.sourcegitcommit: cf22b29db780e532e1090c6e755aa52d28273fa6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/01/2018
---
# <a name="peer-to-peer-collaboration"></a><span data-ttu-id="55084-102">Eşler arası işbirliği</span><span class="sxs-lookup"><span data-stu-id="55084-102">Peer-to-Peer Collaboration</span></span>
<span data-ttu-id="55084-103">Eşler arası, birden fazla yalnızca istemci tabanlı bilgi işlem görevleri için Internet kenarında mevcut oldukça güçlü bilgisayarların (kişisel bilgisayarlar) kullanımını ağdır.</span><span class="sxs-lookup"><span data-stu-id="55084-103">Peer-to-peer networking is the utilization of the relatively powerful computers (personal computers) that exist at the edge of the Internet for more than just client-based computing tasks.</span></span> <span data-ttu-id="55084-104">Modern kişisel bilgisayar (PC) çok hızlı bir işlemciye, büyük bellek ve hangi hiçbiri tam e-posta ve Web'e gözatma gibi ortak bilgi işlem görevler gerçekleştirirken göstermesi büyük sabit disk vardır.</span><span class="sxs-lookup"><span data-stu-id="55084-104">The modern personal computer (PC) has a very fast processor, vast memory, and a large hard disk, none of which are being fully utilized when performing common computing tasks such as email and Web browsing.</span></span> <span data-ttu-id="55084-105">Modern PC kolayca hem istemci hem de birçok türdeki uygulamayı (bir eş) sunucusu olarak çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="55084-105">The modern PC can easily act as both a client and server (a peer) for many types of applications.</span></span>  
  
-   <span data-ttu-id="55084-106">Eşler arası işbirliği altyapısı kişiler bana hizmet Windows Vista ve sonraki platformlar yakınlarında yararlanır Microsoft Windows Eşler arası altyapısı basitleştirilmiş bir uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="55084-106">The Peer-to-Peer Collaboration Infrastructure is a simplified implementation of the Microsoft Windows Peer-to-Peer Infrastructure that leverages the People Near Me service in Windows Vista and later platforms.</span></span> <span data-ttu-id="55084-107">Bir alt ağ içindeki eş özellikli uygulamalar için en iyi şekilde kullanılan için kişiler yakın service bana faaliyet, Internet uç noktaları veya kişiler de hizmet rağmen.</span><span class="sxs-lookup"><span data-stu-id="55084-107">It is best used for peer-enabled applications within a subnet for which the People Near Me service operates, although it can service internet endpoints or contacts as well.</span></span> <span data-ttu-id="55084-108">Ortak kişi kişi uç noktaları, kullanılabilirlik ve iletişim durumu belirlemek için Live Messenger ve canlı kullanan diğer uygulamalar tarafından kullanılan Yöneticisi içerir.</span><span class="sxs-lookup"><span data-stu-id="55084-108">It incorporates the common Contact Manager that is used by Live Messenger and other Live-aware applications to determine contact endpoints, availability, and presence.</span></span>  
  
-  
  
## <a name="collaboration-applications"></a><span data-ttu-id="55084-109">Birlikte çalışma uygulamaları</span><span class="sxs-lookup"><span data-stu-id="55084-109">Collaboration Applications</span></span>  
 <span data-ttu-id="55084-110">Tipik eşler arası işbirliği uygulama aşağıdaki adımlardan oluşur:</span><span class="sxs-lookup"><span data-stu-id="55084-110">A typical peer-to-peer collaboration application is comprised of the following steps:</span></span>  
  
-   <span data-ttu-id="55084-111">Eş işbirliği oturumunu barındıran isteyen bir eş kimliğini belirler</span><span class="sxs-lookup"><span data-stu-id="55084-111">Peer determines the identity of a peer who is interested in hosting a collaboration session</span></span>  
  
-   <span data-ttu-id="55084-112">Bir oturum barındırmak için bir istek, şekilde, gönderilir ve işbirliği etkinlik yönetmek konak eş kabul eder.</span><span class="sxs-lookup"><span data-stu-id="55084-112">A request to host a session is sent, somehow, and the host peer agrees to manage collaboration activity.</span></span>  
  
-   <span data-ttu-id="55084-113">Konak bir oturuma (istek sahibinin dahil) alt ağda bulunan kişileri davet eder.</span><span class="sxs-lookup"><span data-stu-id="55084-113">The host invites contacts on the subnet (including the requestor) to a session.</span></span>  
  
-   <span data-ttu-id="55084-114">İşbirliği yapmak istediğiniz tüm eşleri kişi yöneticilerinin konağa ekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="55084-114">All peers who want to collaborate may add the host to their contact managers.</span></span>  
  
-   <span data-ttu-id="55084-115">Çoğu eş davet yanıtları kabul ya da reddedilen zamanında konak eş için geri gönderir.</span><span class="sxs-lookup"><span data-stu-id="55084-115">Most peers will send invitation responses, whether accepted or declined, back to the host peer in a timely fashion.</span></span>  
  
-   <span data-ttu-id="55084-116">Ana bilgisayar eşler arası işbirliği yapmak istediğiniz tüm eşleri abone olur.</span><span class="sxs-lookup"><span data-stu-id="55084-116">All peers who want to collaborate will subscribe to the host peer.</span></span>  
  
-   <span data-ttu-id="55084-117">Eş ilk işbirliği etkinliklerini gerçekleştirirken, ana bilgisayar eş kendi Kişi Yöneticisi uzak eşlerden ekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="55084-117">While the peers are performing their initial collaboration activity, the host peer may add remote peers to its contact manager.</span></span> <span data-ttu-id="55084-118">Bunu ayrıca belirlemek için tüm davet yanıtları, kimin reddetti ve kimlerin verilmemesi kabul işler.</span><span class="sxs-lookup"><span data-stu-id="55084-118">It also processes all invitation responses to determine who has accepted, who has declined, and who has not answered.</span></span>  <span data-ttu-id="55084-119">Bunu verilmemesi olanlar için davet iptal edin veya başka bir etkinlikle gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="55084-119">It may cancel invitations to those who have not answered, or perform some other activity.</span></span>  
  
-   <span data-ttu-id="55084-120">Bu noktada, ana bilgisayar eş tüm davet edilen kişilerle işbirliği oturumu başlatmak veya bir uygulamayı işbirliği altyapısı ile kaydedin.</span><span class="sxs-lookup"><span data-stu-id="55084-120">At this point, the host peer can start a collaboration session with all invited peers, or register an application with the collaboration infrastructure.</span></span>  <span data-ttu-id="55084-121">P2p uygulamaları eşler arası işbirliği altyapısı kullanır ve <xref:System.Net.PeerToPeer.Collaboration> iletişimleri oyunlar, Bülten panosu, konferans ve diğer sunucusuz varlığı uygulamaları için koordine etmek için ad alanı.</span><span class="sxs-lookup"><span data-stu-id="55084-121">P2P applications use the Peer-to-Peer Collaboration Infrastructure and the <xref:System.Net.PeerToPeer.Collaboration> namespace to coordinate communications for games, bulletin boards, conferencing, and other serverless presence applications.</span></span>  
  
-  
  
## <a name="peer-to-peer-networking-security"></a><span data-ttu-id="55084-122">Eşler arası ağ güvenliği</span><span class="sxs-lookup"><span data-stu-id="55084-122">Peer-to-Peer Networking Security</span></span>  
 <span data-ttu-id="55084-123">Bir Active Directory etki alanında etki alanı denetleyicileri, Kerberos kullanarak kimlik doğrulama hizmetleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="55084-123">In an Active Directory domain, domain controllers provide authentication services using Kerberos.</span></span> <span data-ttu-id="55084-124">Bir sunucusuz eş ortamında eşlerden kendi kimlik doğrulaması sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="55084-124">In a serverless peer environment, the peers must provide their own authentication.</span></span> <span data-ttu-id="55084-125">Ağ eşler için herhangi bir düğümün bir kök sertifika gereksinimi her eşin güvenilir kök deposuna kaldırma, bir CA olarak çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="55084-125">For Peer-to-Peer Networking, any node can act as a CA, removing the requirement of a root certificate in each peer's trusted root store.</span></span> <span data-ttu-id="55084-126">X.509 sertifikaları biçimlendirilmiş otomatik olarak imzalanan sertifikalar kullanarak kimlik doğrulaması sağlanır.</span><span class="sxs-lookup"><span data-stu-id="55084-126">Authentication is provided using self-signed certificates, formatted as X.509 certificates.</span></span> <span data-ttu-id="55084-127">Bunlar ortak anahtarı/özel anahtar çifti ve özel anahtarı ile imzalanmış bir sertifika oluşturur her eş tarafından oluşturulan sertifikalardır.</span><span class="sxs-lookup"><span data-stu-id="55084-127">These are certificates that are created by each peer, which generates the public key/private key pair and the certificate that is signed using the private key.</span></span> <span data-ttu-id="55084-128">Otomatik olarak imzalanan sertifika kimlik doğrulaması ve eş varlık hakkında bilgi sağlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="55084-128">The self-signed certificate is used for authentication and to provide information about the peer entity.</span></span> <span data-ttu-id="55084-129">X.509 kimlik doğrulaması gibi bir sertifika zinciri geri güvenilir bir ortak anahtar için izleme eş ağ kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="55084-129">Like X.509 authentication, peer networking authentication relies upon a chain of certificates tracing back to a public key that is trusted.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55084-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="55084-130">See Also</span></span>  
 <xref:System.Net.PeerToPeer.Collaboration>  
 [<span data-ttu-id="55084-131">System.Net.PeerToPeer.Collaboration Ad Alanı Hakkında</span><span class="sxs-lookup"><span data-stu-id="55084-131">About the System.Net.PeerToPeer.Collaboration Namespace</span></span>](../../../docs/framework/network-programming/about-the-system-net-peertopeer-collaboration-namespace.md)
