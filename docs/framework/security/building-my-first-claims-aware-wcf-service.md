---
title: "My ilk talep kullanan WCF hizmeti oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e0e6d091-9a97-4888-8f2c-cbcee42d90ee
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: af39c3c5788db95eaee248ca8454534022cab659
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="building-my-first-claims-aware-wcf-service"></a><span data-ttu-id="d7250-102">My ilk talep kullanan WCF hizmeti oluşturma</span><span class="sxs-lookup"><span data-stu-id="d7250-102">Building My First Claims-Aware WCF Service</span></span>
## <a name="applies-to"></a><span data-ttu-id="d7250-103">Uygulandığı öğe:</span><span class="sxs-lookup"><span data-stu-id="d7250-103">Applies To</span></span>  
  
-   <span data-ttu-id="d7250-104">Windows Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="d7250-104">Windows Identity Foundation (WIF)</span></span>  
  
-   <span data-ttu-id="d7250-105">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="d7250-105">Windows Communication Foundation (WCF)</span></span>  
  
## <a name="overview"></a><span data-ttu-id="d7250-106">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="d7250-106">Overview</span></span>  
 <span data-ttu-id="d7250-107">Bu konuda, WIF kullanarak talep kullanan WCF hizmetleri oluşturma senaryosu açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d7250-107">This topic outlines the scenario of building claims-aware WCF services using WIF.</span></span> <span data-ttu-id="d7250-108">Talep kullanan web hizmeti senaryosunda genellikle üç katılımcı vardır: web hizmetinin kendisi, son kullanıcı ve Güvenlik Belirteci Hizmeti (STS).</span><span class="sxs-lookup"><span data-stu-id="d7250-108">There are usually three participants in a claims-aware web service scenario: the web service itself, the end user, and the Security Token Service (STS).</span></span> <span data-ttu-id="d7250-109">Aşağıdaki şekilde bu senaryo anlatılmaktadır:</span><span class="sxs-lookup"><span data-stu-id="d7250-109">The following figure describes this scenario:</span></span>  
  
 <span data-ttu-id="d7250-110">![WIF Basic talep kullanan WCF Hizmeti](../../../docs/framework/security/media/wifbasicclaimsawarewcfservice.gif "WIFBasicClaimsAwareWCFService")</span><span class="sxs-lookup"><span data-stu-id="d7250-110">![WIF Basic Claims Aware WCF Service](../../../docs/framework/security/media/wifbasicclaimsawarewcfservice.gif "WIFBasicClaimsAwareWCFService")</span></span>  
  
1.  <span data-ttu-id="d7250-111">WCF hizmeti istemcisi (bazen aracı olarak adlandırılır), STS'ye kimlik bilgilerini göndermek için WIF'yi kullanır ve başarılı bir kimlik doğrulamadan sonra aracıya STS tarafından bir belirteç verilir.</span><span class="sxs-lookup"><span data-stu-id="d7250-111">The WCF service client (sometimes called agent) uses WIF to send credentials to the STS and upon successful authentication, the agent is issued a token by the STS.</span></span>  
  
2.  <span data-ttu-id="d7250-112">Aracı, bu STS tarafından verilen belirteci WCF hizmetine gönderir.</span><span class="sxs-lookup"><span data-stu-id="d7250-112">The agent sends this STS-issued token to the WCF service.</span></span>  
  
3.  <span data-ttu-id="d7250-113">Talep kullanan WCF hizmeti, STS'ye ve verdiği belirteçlere güvenecek şekilde yapılandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="d7250-113">The claims-aware WCF service is configured to trust the STS and the tokens it issues.</span></span> <span data-ttu-id="d7250-114">Talep kullanan WCF hizmeti, belirteci uygulamak ve ayrıştırmak için WIF kullanır.</span><span class="sxs-lookup"><span data-stu-id="d7250-114">The claims-aware WCF service uses WIF to validate the token and to parse it.</span></span> <span data-ttu-id="d7250-115">Geliştiriciler kullanın uygun WIF API ve türler, örneğin, **ClaimsPrincipal** yetkilendirme için bu uygulama gibi uygulamanın gerekir.</span><span class="sxs-lookup"><span data-stu-id="d7250-115">Developers use the appropriate WIF API and types, for example, **ClaimsPrincipal** for the application’s needs, such as implementing authorization for it.</span></span>  
  
 <span data-ttu-id="d7250-116">.NET 4. 5 ' başlayarak, WIF .NET Framework paketi parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="d7250-116">Starting from .NET 4.5, WIF is part of the .NET Framework package.</span></span> <span data-ttu-id="d7250-117">Framework'te doğrudan kullanılabilen WIF sınıfları çok derin tümleştirme talep tabanlı kimlik talepleri kullanan kolaylaştırma .NET içinde sağlar.</span><span class="sxs-lookup"><span data-stu-id="d7250-117">Having the WIF classes directly available in the framework allows a much deeper integration of claims-based identity in .NET, making it easier to use claims.</span></span> <span data-ttu-id="d7250-118">WIF 4.5 ile, talep kullanan web uygulamaları geliştirmeye başlamak için bant dışı bileşenler yüklemenize gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="d7250-118">With WIF 4.5, you do not need to install any out-of-band components in order to start developing claims-aware web applications.</span></span> <span data-ttu-id="d7250-119">WIF sınıfları artık çeşitli derlemeler arasında yayılmaktadır. Temel sınıflar System.Security.Claims, System.IdentityModel ve System.IdentityModel.Services'dır.</span><span class="sxs-lookup"><span data-stu-id="d7250-119">WIF classes are now spread across various assemblies, the main ones being System.Security.Claims, System.IdentityModel and System.IdentityModel.Services.</span></span>  
  
 <span data-ttu-id="d7250-120">STS, başarılı kimlik doğrulamadan sonra belirteçler veren bir hizmettir.</span><span class="sxs-lookup"><span data-stu-id="d7250-120">STS is a service that issues tokens upon successful authentication.</span></span> <span data-ttu-id="d7250-121">Microsoft, iki sektör standardı STS sunar:</span><span class="sxs-lookup"><span data-stu-id="d7250-121">Microsoft offers two industry standard STS’s:</span></span>  
  
-   <span data-ttu-id="d7250-122">[Active Directory Federasyon Hizmetleri (AD FS) 2.0](http://go.microsoft.com/fwlink/?LinkID=247516) (http://go.microsoft.com/fwlink/?LinkID=247516)</span><span class="sxs-lookup"><span data-stu-id="d7250-122">[Active Directory Federation Services (AD FS) 2.0](http://go.microsoft.com/fwlink/?LinkID=247516) (http://go.microsoft.com/fwlink/?LinkID=247516)</span></span>  
  
-   <span data-ttu-id="d7250-123">[Windows Azure erişim denetimi hizmeti (ACS)](http://go.microsoft.com/fwlink/?LinkID=247517) (http://go.microsoft.com/fwlink/?LinkID=247517).</span><span class="sxs-lookup"><span data-stu-id="d7250-123">[Windows Azure Access Control Service (ACS)](http://go.microsoft.com/fwlink/?LinkID=247517) (http://go.microsoft.com/fwlink/?LinkID=247517).</span></span>  
  
 <span data-ttu-id="d7250-124">AD FS 2.0, Windows Server R2'nin bir parçasıdır ve şirket içi senaryolar için STS olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d7250-124">AD FS 2.0 is part of the Windows Server R2 and can be used as an STS for on-premise scenarios.</span></span> <span data-ttu-id="d7250-125">Azure Active Directory erişim denetimi (erişim denetimi hizmeti veya ACS olarak da bilinir), Microsoft Azure bir parçası olarak sunulan bulut hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="d7250-125">Azure Active Directory Access Control (also known as Access Control Service or ACS) is a cloud service, offered as part of Microsoft Azure.</span></span> <span data-ttu-id="d7250-126">Test ve eğitim amaçları için talep kullanan uygulamalar oluşturmak üzere başka STS'ler de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d7250-126">For testing or educational purposes, you can also use other STS’s in order to build your claims-aware applications.</span></span> <span data-ttu-id="d7250-127">Örneğin, bir parçası olan yerel geliştirme STS kullanabilirsiniz [kimlik ve erişim aracı Visual Studio için](http://go.microsoft.com/fwlink/?LinkID=245849) (http://go.microsoft.com/fwlink/?LinkID=245849) olduğu ücretsiz çevrimiçi.</span><span class="sxs-lookup"><span data-stu-id="d7250-127">For example, you can use the Local Development STS that is part of the [Identity and Access Tool for Visual Studio](http://go.microsoft.com/fwlink/?LinkID=245849) (http://go.microsoft.com/fwlink/?LinkID=245849) which is freely available online.</span></span>  
  
 <span data-ttu-id="d7250-128">WIF kullanan, ilk talep kullanan WCF hizmeti oluşturmak için bkz: [nasıl yapılır: derleme talep kullanan WCF hizmeti kullanarak WIF](http://msdn.microsoft.com/en-us/431e6415-62ed-4a9f-af03-f14d2b4dfe6d).</span><span class="sxs-lookup"><span data-stu-id="d7250-128">To build your first claims-aware WCF service using WIF, see [How To: Build Claims-Aware WCF Service Using WIF](http://msdn.microsoft.com/en-us/431e6415-62ed-4a9f-af03-f14d2b4dfe6d).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7250-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d7250-129">See Also</span></span>  
 [<span data-ttu-id="d7250-130">WIF Kullanmaya Başlama</span><span class="sxs-lookup"><span data-stu-id="d7250-130">Getting Started With WIF</span></span>](../../../docs/framework/security/getting-started-with-wif.md)
