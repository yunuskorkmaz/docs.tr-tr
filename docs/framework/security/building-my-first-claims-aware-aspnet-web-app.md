---
title: "My ilk talep kullanan ASP.NET Web uygulaması oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3ee8ee7f-caba-4267-9343-e313fae2876d
caps.latest.revision: "5"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: aa25f163199652618e35399c6548a9864a17370a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="building-my-first-claims-aware-aspnet-web-application"></a><span data-ttu-id="0394a-102">My ilk talep kullanan ASP.NET Web uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="0394a-102">Building My First Claims-Aware ASP.NET Web Application</span></span>
## <a name="applies-to"></a><span data-ttu-id="0394a-103">Uygulandığı öğe:</span><span class="sxs-lookup"><span data-stu-id="0394a-103">Applies To</span></span>  
  
-   <span data-ttu-id="0394a-104">Windows Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="0394a-104">Windows Identity Foundation (WIF)</span></span>  
  
-   <span data-ttu-id="0394a-105">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="0394a-105">ASP.NET</span></span>  
  
 <span data-ttu-id="0394a-106">Bu konuda, WIF kullanarak talep kullanan ASP.NET web uygulamaları oluşturma senaryosu açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0394a-106">This topic outlines the scenario of building claims-aware ASP.NET web applications using WIF.</span></span> <span data-ttu-id="0394a-107">Talep kullanan uygulama senaryosunda genellikle üç katılımcı vardır: uygulamanın kendisi, son kullanıcı ve Güvenlik Belirteci Hizmeti (STS).</span><span class="sxs-lookup"><span data-stu-id="0394a-107">There are usually three participants in a claims-aware application scenario: the application itself, the end user, and the Security Token Service (STS).</span></span> <span data-ttu-id="0394a-108">Aşağıdaki şekilde bu senaryo anlatılmaktadır:</span><span class="sxs-lookup"><span data-stu-id="0394a-108">The following figure describes this scenario:</span></span>  
  
 <span data-ttu-id="0394a-109">![WIF temel Web uygulamasını](../../../docs/framework/security/media/wifbasicwebapp.gif "WIFBasicWebApp")</span><span class="sxs-lookup"><span data-stu-id="0394a-109">![WIF Basic Web App](../../../docs/framework/security/media/wifbasicwebapp.gif "WIFBasicWebApp")</span></span>  
  
1.  <span data-ttu-id="0394a-110">Talep kullanan uygulama, kimliği doğrulanmamış istekleri tanımlamak ve bunları STS'ye yönlendirmek için WIF kullanır.</span><span class="sxs-lookup"><span data-stu-id="0394a-110">The claims-aware application uses WIF to identify unauthenticated requests and to redirect them to the STS.</span></span>  
  
2.  <span data-ttu-id="0394a-111">Son kullanıcı, STS'ye kimlik bilgileri sağlar ve başarılı bir kimlik doğrulamadan sonra kullanıcıya STS tarafından belirteç verilir.</span><span class="sxs-lookup"><span data-stu-id="0394a-111">The end user provides credentials to the STS and upon successful authentication the user is issued a token by the STS.</span></span>  
  
3.  <span data-ttu-id="0394a-112">Kullanıcı, istekte STS tarafından verilen belirteçle STS'den talep kullanan uygulamaya yönlendirilir.</span><span class="sxs-lookup"><span data-stu-id="0394a-112">The user is redirected from the STS to the claims-aware application with the STS-issued token in the request.</span></span>  
  
4.  <span data-ttu-id="0394a-113">Talep kullanan uygulama, STS'ye ve verdiği belirteçlere güvenecek şekilde yapılandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="0394a-113">The claims-aware application is configured to trust the STS and the tokens it issues.</span></span> <span data-ttu-id="0394a-114">Talep kullanan uygulama, belirteci doğrulamak ve ayrıştırmak için WIF kullanır.</span><span class="sxs-lookup"><span data-stu-id="0394a-114">The claims-aware application uses WIF to validate the token and to parse it.</span></span> <span data-ttu-id="0394a-115">Geliştiriciler kullanın uygun WIF API ve türler, örneğin, **ClaimsPrincpal** yetkilendirme için bu uygulama gibi uygulamanın gerekir.</span><span class="sxs-lookup"><span data-stu-id="0394a-115">Developers use the appropriate WIF API and types, for example, **ClaimsPrincpal** for the application’s needs, such as implementing authorization for it.</span></span>  
  
 <span data-ttu-id="0394a-116">.NET 4. 5 ' başlayarak, WIF .NET Framework paketi parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="0394a-116">Starting from .NET 4.5, WIF is part of the .NET Framework package.</span></span> <span data-ttu-id="0394a-117">Framework'te doğrudan kullanılabilen WIF sınıfları çok derin tümleştirme talep tabanlı kimlik talepleri kullanan kolaylaştırma .NET içinde sağlar.</span><span class="sxs-lookup"><span data-stu-id="0394a-117">Having the WIF classes directly available in the framework allows a much deeper integration of claims-based identity in .NET, making it easier to use claims.</span></span> <span data-ttu-id="0394a-118">WIF 4.5 ile, talep kullanan web uygulamaları geliştirmeye başlamak için bant dışı bileşenler yüklemenize gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="0394a-118">With WIF 4.5, you do not need to install any out-of-band components in order to start developing claims-aware web applications.</span></span> <span data-ttu-id="0394a-119">WIF sınıfları artık çeşitli derlemeler arasında yayılmaktadır. Temel sınıflar System.Security.Claims, System.IdentityModel ve System.IdentityModel.Services'dır.</span><span class="sxs-lookup"><span data-stu-id="0394a-119">WIF classes are now spread across various assemblies, the main ones being System.Security.Claims, System.IdentityModel and System.IdentityModel.Services.</span></span>  
  
 <span data-ttu-id="0394a-120">STS, başarılı kimlik doğrulamadan sonra belirteçler veren bir hizmettir.</span><span class="sxs-lookup"><span data-stu-id="0394a-120">STS is a service that issues tokens upon successful authentication.</span></span> <span data-ttu-id="0394a-121">Microsoft, iki sektör standardı STS sunar:</span><span class="sxs-lookup"><span data-stu-id="0394a-121">Microsoft offers two industry standard STS’s:</span></span>  
  
-   <span data-ttu-id="0394a-122">[Active Directory Federasyon Hizmetleri (AD FS) 2.0](http://go.microsoft.com/fwlink/?LinkID=247516) (http://go.microsoft.com/fwlink/?LinkID=247516)</span><span class="sxs-lookup"><span data-stu-id="0394a-122">[Active Directory Federation Services (AD FS) 2.0](http://go.microsoft.com/fwlink/?LinkID=247516) (http://go.microsoft.com/fwlink/?LinkID=247516)</span></span>  
  
-   <span data-ttu-id="0394a-123">[Windows Azure erişim denetimi hizmeti (ACS)](http://go.microsoft.com/fwlink/?LinkID=247517) (http://go.microsoft.com/fwlink/?LinkID=247517).</span><span class="sxs-lookup"><span data-stu-id="0394a-123">[Windows Azure Access Control Service (ACS)](http://go.microsoft.com/fwlink/?LinkID=247517) (http://go.microsoft.com/fwlink/?LinkID=247517).</span></span>  
  
 <span data-ttu-id="0394a-124">AD FS 2.0, Windows Server R2'nin bir parçasıdır ve şirket içi senaryolar için STS olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0394a-124">AD FS 2.0 is part of the Windows Server R2 and can be used as an STS for on-premise scenarios.</span></span> <span data-ttu-id="0394a-125">ACS, Microsoft Azure platformunun bir parçası olarak sunulan bir bulut hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="0394a-125">ACS is a cloud service, offered as part of the Windows Azure Platform.</span></span> <span data-ttu-id="0394a-126">Test ve eğitim amaçları için talep kullanan uygulamalar oluşturmak üzere başka STS'ler de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0394a-126">For testing or educational purposes, you can also use other STS’s in order to build your claims-aware applications.</span></span> <span data-ttu-id="0394a-127">Örneğin, bir parçası olan yerel geliştirme STS kullanabilirsiniz [kimlik ve erişim aracı Visual Studio için](http://go.microsoft.com/fwlink/?LinkID=245849) (http://go.microsoft.com/fwlink/?LinkID=245849) olduğu ücretsiz çevrimiçi.</span><span class="sxs-lookup"><span data-stu-id="0394a-127">For example, you can use the Local Development STS that is part of the [Identity and Access Tool for Visual Studio](http://go.microsoft.com/fwlink/?LinkID=245849) (http://go.microsoft.com/fwlink/?LinkID=245849) which is freely available online.</span></span>  
  
 <span data-ttu-id="0394a-128">WIF kullanarak ilk talep kullanan ASP.NET uygulamanızı oluşturmak için aşağıdakilerden birinde yer alan yönergeleri uygulayın:</span><span class="sxs-lookup"><span data-stu-id="0394a-128">To build your first claims-aware ASP.NET application using WIF, follow the instructions in one of the following:</span></span>  
  
-   [<span data-ttu-id="0394a-129">Nasıl yapılır: WIF kullanarak talep kullanan ASP.NET MVC Web uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="0394a-129">How To: Build Claims-Aware ASP.NET MVC Web Application Using WIF</span></span>](../../../docs/framework/security/how-to-build-claims-aware-aspnet-mvc-web-app-using-wif.md)  
  
-   [<span data-ttu-id="0394a-130">Nasıl yapılır: WIF kullanarak talep kullanan ASP.NET Web Forms uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="0394a-130">How To: Build Claims-Aware ASP.NET Web Forms Application Using WIF</span></span>](../../../docs/framework/security/how-to-build-claims-aware-aspnet-web-forms-app-using-wif.md)  
  
-   [<span data-ttu-id="0394a-131">Nasıl yapılır: Form tabanlı kimlik doğrulaması kullanarak talep kullanan ASP.NET uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="0394a-131">How To: Build Claims-Aware ASP.NET Application Using Forms-Based Authentication</span></span>](../../../docs/framework/security/claims-aware-aspnet-app-forms-authentication.md)  
  
## <a name="see-also"></a><span data-ttu-id="0394a-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0394a-132">See Also</span></span>  
 [<span data-ttu-id="0394a-133">WIF ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="0394a-133">Getting Started With WIF</span></span>](../../../docs/framework/security/getting-started-with-wif.md)
