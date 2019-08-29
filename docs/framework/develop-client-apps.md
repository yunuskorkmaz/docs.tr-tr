---
title: .NET Framework ile Windows tabanlı istemci uygulamaları geliştirme
ms.date: 01/09/2018
helpviewer_keywords:
- client application services
- applications [Windows Forms]
- Windows Presentation Foundation, in Visual Studio
- WPF, in Visual Studio
- Windows applications
- rich client applications
- .NET applications, Windows applications
- Visual Basic code, creating applications
- Visual C#, creating applications
- client/server applications, Windows applications
ms.assetid: 2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68
ms.openlocfilehash: b8c63aa074f699fa77c25441995a2ae74b78caf8
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106491"
---
# <a name="developing-client-applications-with-the-net-framework"></a><span data-ttu-id="797de-102">.NET Framework ile istemci uygulamaları geliştirme</span><span class="sxs-lookup"><span data-stu-id="797de-102">Developing client applications with the .NET Framework</span></span>

<span data-ttu-id="797de-103">.NET Framework Windows tabanlı uygulamalar geliştirmenin birkaç yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="797de-103">There are several ways to develop Windows-based applications with the .NET Framework.</span></span> <span data-ttu-id="797de-104">Bu araçlardan ve çerçevelerin herhangi birini kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="797de-104">You can use any of these tools and frameworks:</span></span> 

- [<span data-ttu-id="797de-105">Evrensel Windows Platformu (UWP)</span><span class="sxs-lookup"><span data-stu-id="797de-105">Universal Windows Platform (UWP)</span></span>](https://developer.microsoft.com/windows/apps)
- [<span data-ttu-id="797de-106">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="797de-106">Windows Presentation Foundation (WPF)</span></span>](../../docs/framework/wpf/index.md)
- [<span data-ttu-id="797de-107">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="797de-107">Windows Forms</span></span>](../../docs/framework/winforms/index.md)

<span data-ttu-id="797de-108">Bu bölümde, Windows Presentation Foundation kullanarak veya Windows Forms kullanarak Windows tabanlı uygulamalar oluşturmayı betimleyen konular yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="797de-108">This section contains topics that describe how to create Windows-based applications by using Windows Presentation Foundation or by using Windows Forms.</span></span> <span data-ttu-id="797de-109">Ancak, .NET Framework kullanarak Web uygulamaları ve Microsoft Store üzerinden kullanılabilir hale getirmek istediğiniz bilgisayarlar veya cihazlar için istemci uygulamaları da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="797de-109">However, you can also create web applications using the .NET Framework, and client applications for computers or devices that you make available through the Microsoft Store.</span></span>
 
## <a name="in-this-section"></a><span data-ttu-id="797de-110">Bu bölümde</span><span class="sxs-lookup"><span data-stu-id="797de-110">In this section</span></span>

[<span data-ttu-id="797de-111">Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="797de-111">Windows Presentation Foundation</span></span>](../../docs/framework/wpf/index.md)  
<span data-ttu-id="797de-112">WPF kullanarak uygulama geliştirme hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="797de-112">Provides information about developing applications by using WPF.</span></span>

[<span data-ttu-id="797de-113">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="797de-113">Windows Forms</span></span>](../../docs/framework/winforms/index.md)  
<span data-ttu-id="797de-114">Windows Forms kullanarak uygulama geliştirme hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="797de-114">Provides information about developing applications by using Windows Forms.</span></span>

[<span data-ttu-id="797de-115">Ortak İstemci Teknolojileri</span><span class="sxs-lookup"><span data-stu-id="797de-115">Common Client Technologies</span></span>](../../docs/framework/common-client-technologies/index.md)  
<span data-ttu-id="797de-116">İstemci uygulamaları geliştirirken kullanılabilecek ek teknolojiler hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="797de-116">Provides information about additional technologies that can be used when developing client applications.</span></span>

## <a name="related-sections"></a><span data-ttu-id="797de-117">İlgili bölümler</span><span class="sxs-lookup"><span data-stu-id="797de-117">Related sections</span></span>

[<span data-ttu-id="797de-118">Evrensel Windows Platformu</span><span class="sxs-lookup"><span data-stu-id="797de-118">Universal Windows Platform</span></span>](https://developer.microsoft.com/windows/apps)  
<span data-ttu-id="797de-119">Windows Mağazası aracılığıyla kullanıcılara kullanılabilir hale getirmek için Windows 10 uygulamalarının nasıl oluşturulacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="797de-119">Describes how to create applications for Windows 10 that you can make available to users through the Windows Store.</span></span>

[<span data-ttu-id="797de-120">UWP uygulamaları için .NET</span><span class="sxs-lookup"><span data-stu-id="797de-120">.NET for UWP apps</span></span>](https://msdn.microsoft.com/library/windows/apps/mt185501.aspx)  
<span data-ttu-id="797de-121">Windows bilgisayarlarına ve cihazlarına dağıtılabilecek Mağaza uygulamaları için .NET Framework desteğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="797de-121">Describes the .NET Framework support for Store apps, which can be deployed to Windows computers and devices.</span></span>

<span data-ttu-id="797de-122">[Silverlight Windows Phone için .NET API](https://docs.microsoft.com/previous-versions/windows/apps/jj207211\(v=vs.105\))</span><span class="sxs-lookup"><span data-stu-id="797de-122">[.NET API for Windows Phone Silverlight](https://docs.microsoft.com/previous-versions/windows/apps/jj207211\(v=vs.105\))</span></span>  
<span data-ttu-id="797de-123">Windows Phone Silverlight ile uygulama oluşturmak için kullanabileceğiniz .NET Framework API 'Leri listeler.</span><span class="sxs-lookup"><span data-stu-id="797de-123">Lists the .NET Framework APIs you can use for building apps with Windows Phone Silverlight.</span></span>
  
[<span data-ttu-id="797de-124">Çoklu Platformlar için Geliştirme</span><span class="sxs-lookup"><span data-stu-id="797de-124">Developing for Multiple Platforms</span></span>](../../docs/standard/cross-platform/index.md)  
<span data-ttu-id="797de-125">Birden çok istemci uygulama türünü hedeflemek için .NET Framework kullanabileceğiniz farklı yöntemleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="797de-125">Describes the different methods you can use the .NET Framework to target multiple client app types.</span></span>

[<span data-ttu-id="797de-126">ASP.NET Web siteleri 'ni kullanmaya başlama</span><span class="sxs-lookup"><span data-stu-id="797de-126">Get Started with ASP.NET Web Sites</span></span>](https://www.asp.net/get-started/websites)  
<span data-ttu-id="797de-127">ASP.NET kullanarak Web uygulamaları geliştirebileceğiniz yolları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="797de-127">Describes the ways you can develop web apps using ASP.NET.</span></span>

## <a name="see-also"></a><span data-ttu-id="797de-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="797de-128">See also</span></span>

- [<span data-ttu-id="797de-129">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="797de-129">.NET Standard</span></span>](../../docs/standard/net-standard.md)
- [<span data-ttu-id="797de-130">Genel bakış</span><span class="sxs-lookup"><span data-stu-id="797de-130">Overview</span></span>](../../docs/framework/get-started/overview.md)
- [<span data-ttu-id="797de-131">Geliştirme Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="797de-131">Development Guide</span></span>](../../docs/framework/development-guide.md)
- [<span data-ttu-id="797de-132">Windows Hizmeti Uygulamaları</span><span class="sxs-lookup"><span data-stu-id="797de-132">Windows Service Applications</span></span>](../../docs/framework/windows-services/index.md)
