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
ms.openlocfilehash: 279e0536f69ebd4b45d9458a88c4f930f6bb3262
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33389115"
---
# <a name="developing-client-applications-with-the-net-framework"></a><span data-ttu-id="f62d5-102">.NET Framework ile istemci uygulamaları geliştirme</span><span class="sxs-lookup"><span data-stu-id="f62d5-102">Developing client applications with the .NET Framework</span></span>

<span data-ttu-id="f62d5-103">.NET Framework ile Windows tabanlı uygulamalar geliştirmek için birkaç yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="f62d5-103">There are several ways to develop Windows-based applications with the .NET Framework.</span></span> <span data-ttu-id="f62d5-104">Bu araçlar ve çerçeveleri herhangi birini kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f62d5-104">You can use any of these tools and frameworks:</span></span> 

* [<span data-ttu-id="f62d5-105">Evrensel Windows Platformu (UWP)</span><span class="sxs-lookup"><span data-stu-id="f62d5-105">Universal Windows Platform (UWP)</span></span>](https://developer.microsoft.com/windows/apps)
* [<span data-ttu-id="f62d5-106">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="f62d5-106">Windows Presentation Foundation (WPF)</span></span>](../../docs/framework/wpf/index.md)
* [<span data-ttu-id="f62d5-107">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f62d5-107">Windows Forms</span></span>](../../docs/framework/winforms/index.md)

<span data-ttu-id="f62d5-108">Bu bölüm, Windows Presentation Foundation kullanarak veya Windows formları kullanarak Windows tabanlı uygulamalar oluşturmak nasıl açıklayan konuları içerir.</span><span class="sxs-lookup"><span data-stu-id="f62d5-108">This section contains topics that describe how to create Windows-based applications by using Windows Presentation Foundation or by using Windows Forms.</span></span> <span data-ttu-id="f62d5-109">Ancak, .NET Framework ile web uygulamaları ve bilgisayarlar veya Microsoft Store kullanılabilir hale aygıtlar için istemci uygulamaları da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f62d5-109">However, you can also create web applications using the .NET Framework, and client applications for computers or devices that you make available through the Microsoft Store.</span></span>
 
## <a name="in-this-section"></a><span data-ttu-id="f62d5-110">Bu bölümde</span><span class="sxs-lookup"><span data-stu-id="f62d5-110">In this section</span></span>

[<span data-ttu-id="f62d5-111">Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="f62d5-111">Windows Presentation Foundation</span></span>](../../docs/framework/wpf/index.md)  
<span data-ttu-id="f62d5-112">WPF kullanarak uygulamaları geliştirme hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="f62d5-112">Provides information about developing applications by using WPF.</span></span>

[<span data-ttu-id="f62d5-113">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f62d5-113">Windows Forms</span></span>](../../docs/framework/winforms/index.md)  
<span data-ttu-id="f62d5-114">Windows Forms kullanarak uygulamaları geliştirme hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="f62d5-114">Provides information about developing applications by using Windows Forms.</span></span>

[<span data-ttu-id="f62d5-115">Ortak İstemci Teknolojileri</span><span class="sxs-lookup"><span data-stu-id="f62d5-115">Common Client Technologies</span></span>](../../docs/framework/common-client-technologies/index.md)  
<span data-ttu-id="f62d5-116">İstemci uygulamaları geliştirirken kullanılan ek teknolojiler hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="f62d5-116">Provides information about additional technologies that can be used when developing client applications.</span></span>

## <a name="related-sections"></a><span data-ttu-id="f62d5-117">İlgili bölümler</span><span class="sxs-lookup"><span data-stu-id="f62d5-117">Related sections</span></span>

[<span data-ttu-id="f62d5-118">Evrensel Windows platformu</span><span class="sxs-lookup"><span data-stu-id="f62d5-118">Universal Windows Platform</span></span>](https://developer.microsoft.com/windows/apps)  
<span data-ttu-id="f62d5-119">Windows 10'de, kullanıcılar için Windows mağazası yoluyla kullanılabilir hale getirebilirsiniz uygulamalarının nasıl oluşturulacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="f62d5-119">Describes how to create applications for Windows 10 that you can make available to users through the Windows Store.</span></span>

[<span data-ttu-id="f62d5-120">UWP uygulamalar için .NET</span><span class="sxs-lookup"><span data-stu-id="f62d5-120">.NET for UWP apps</span></span>](https://msdn.microsoft.com/library/windows/apps/mt185501.aspx)  
<span data-ttu-id="f62d5-121">Windows bilgisayarları ve aygıtları dağıtılabilir mağazası uygulamaları için .NET Framework Destek açıklanır.</span><span class="sxs-lookup"><span data-stu-id="f62d5-121">Describes the .NET Framework support for Store apps, which can be deployed to Windows computers and devices.</span></span>

<span data-ttu-id="f62d5-122">[Windows Phone Silverlight için .NET API](https://docs.microsoft.com/en-us/previous-versions/windows/apps/jj207211\(v=vs.105\))</span><span class="sxs-lookup"><span data-stu-id="f62d5-122">[.NET API for Windows Phone Silverlight](https://docs.microsoft.com/en-us/previous-versions/windows/apps/jj207211\(v=vs.105\))</span></span>  
<span data-ttu-id="f62d5-123">.NET Framework ile Windows Phone Silverlight uygulamaları oluşturmak için kullanabileceğiniz API'ları listeler.</span><span class="sxs-lookup"><span data-stu-id="f62d5-123">Lists the .NET Framework APIs you can use for building apps with Windows Phone Silverlight.</span></span>
  
[<span data-ttu-id="f62d5-124">Çoklu Platformlar için Geliştirme</span><span class="sxs-lookup"><span data-stu-id="f62d5-124">Developing for Multiple Platforms</span></span>](../../docs/standard/cross-platform/index.md)  
<span data-ttu-id="f62d5-125">.NET Framework birden çok istemci uygulama türleri hedeflemek için kullanabileceğiniz farklı yöntemler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f62d5-125">Describes the different methods you can use the .NET Framework to target multiple client app types.</span></span>

[<span data-ttu-id="f62d5-126">ASP.NET Web siteleri ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="f62d5-126">Get Started with ASP.NET Web Sites</span></span>](http://www.asp.net/get-started/websites)  
<span data-ttu-id="f62d5-127">ASP.NET kullanarak web uygulamaları geliştirmek yolları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f62d5-127">Describes the ways you can develop web apps using ASP.NET.</span></span>

## <a name="see-also"></a><span data-ttu-id="f62d5-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f62d5-128">See also</span></span>

[<span data-ttu-id="f62d5-129">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="f62d5-129">.NET Standard</span></span>](../../docs/standard/net-standard.md)  
[<span data-ttu-id="f62d5-130">Genel bakış</span><span class="sxs-lookup"><span data-stu-id="f62d5-130">Overview</span></span>](../../docs/framework/get-started/overview.md)  
[<span data-ttu-id="f62d5-131">Geliştirme Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="f62d5-131">Development Guide</span></span>](../../docs/framework/development-guide.md)  
[<span data-ttu-id="f62d5-132">Windows Hizmeti Uygulamaları</span><span class="sxs-lookup"><span data-stu-id="f62d5-132">Windows Service Applications</span></span>](../../docs/framework/windows-services/index.md)  
