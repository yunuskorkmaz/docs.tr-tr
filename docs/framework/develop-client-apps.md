---
title: .NET Framework ile Windows tabanlı istemci uygulamaları geliştirme
description: .NET ile Windows tabanlı uygulamalar geliştirin. Evrensel Windows Platformu (UWP), Windows Presentation Foundation (WPF) veya Windows Forms kullanabilirsiniz.
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
ms.openlocfilehash: 33d0ca2918e4e3b00e2b09f7a47c538bbe903dba
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90547915"
---
# <a name="develop-client-applications-with-net-framework"></a><span data-ttu-id="45883-104">.NET Framework ile istemci uygulamaları geliştirme</span><span class="sxs-lookup"><span data-stu-id="45883-104">Develop client applications with .NET Framework</span></span>

<span data-ttu-id="45883-105">.NET Framework ile Windows tabanlı uygulamalar geliştirmenin birkaç yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="45883-105">There are several ways to develop Windows-based applications with .NET Framework.</span></span> <span data-ttu-id="45883-106">Bu araçlardan ve çerçevelerin herhangi birini kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="45883-106">You can use any of these tools and frameworks:</span></span>

- [<span data-ttu-id="45883-107">Evrensel Windows Platformu (UWP)</span><span class="sxs-lookup"><span data-stu-id="45883-107">Universal Windows Platform (UWP)</span></span>](/windows/uwp/)
- [<span data-ttu-id="45883-108">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="45883-108">Windows Presentation Foundation (WPF)</span></span>](/dotnet/desktop/wpf/)
- [<span data-ttu-id="45883-109">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="45883-109">Windows Forms</span></span>](/dotnet/desktop/winforms/)

<span data-ttu-id="45883-110">Bu bölüm, Windows Presentation Foundation veya Windows Forms kullanarak Windows tabanlı uygulamalar oluşturmayı anlatan makaleleri içerir.</span><span class="sxs-lookup"><span data-stu-id="45883-110">This section contains articles that describe how to create Windows-based applications by using Windows Presentation Foundation or Windows Forms.</span></span> <span data-ttu-id="45883-111">Ancak, Microsoft Store (UWP uygulamaları) aracılığıyla kullanıma hazır hale getirmek istediğiniz bilgisayarlar veya cihazlar için .NET Framework ve istemci uygulamalarını kullanarak Web uygulamaları da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="45883-111">However, you can also create web applications using .NET Framework and client applications for computers or devices that you make available through Microsoft Store (UWP apps).</span></span>

## <a name="related-sections"></a><span data-ttu-id="45883-112">İlgili bölümler</span><span class="sxs-lookup"><span data-stu-id="45883-112">Related sections</span></span>

<span data-ttu-id="45883-113">[Evrensel Windows Platformu](/windows/uwp/)</span><span class="sxs-lookup"><span data-stu-id="45883-113">[Universal Windows Platform](/windows/uwp/)</span></span>\
<span data-ttu-id="45883-114">Microsoft Store aracılığıyla kullanıcılara kullanılabilir hale getirmek için UWP uygulamalarının nasıl oluşturulacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="45883-114">Describes how to create UWP applications that you can make available to users through Microsoft Store.</span></span>

<span data-ttu-id="45883-115">[UWP uygulamaları için .NET API](../../api/index.md?view=dotnet-uwp-10.0)</span><span class="sxs-lookup"><span data-stu-id="45883-115">[.NET API for UWP apps](../../api/index.md?view=dotnet-uwp-10.0)</span></span>\
<span data-ttu-id="45883-116">UWP uygulamalarını destekleyen .NET türleri için başvuru.</span><span class="sxs-lookup"><span data-stu-id="45883-116">Reference for .NET types that support UWP apps.</span></span>
  
<span data-ttu-id="45883-117">[Birden çok platform için geliştirme](../standard/cross-platform/index.md)</span><span class="sxs-lookup"><span data-stu-id="45883-117">[Develop for Multiple Platforms](../standard/cross-platform/index.md)</span></span>\
<span data-ttu-id="45883-118">Birden çok istemci uygulama türünü hedeflemek için .NET Framework kullanabileceğiniz farklı yöntemleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="45883-118">Describes the different methods you can use .NET Framework to target multiple client app types.</span></span>

<span data-ttu-id="45883-119">[ASP.NET Web siteleri 'ni kullanmaya başlama](https://dotnet.microsoft.com/apps/aspnet/web-apps)</span><span class="sxs-lookup"><span data-stu-id="45883-119">[Get Started with ASP.NET Web Sites](https://dotnet.microsoft.com/apps/aspnet/web-apps)</span></span>\
<span data-ttu-id="45883-120">ASP.NET kullanarak Web uygulamaları geliştirebileceğiniz yolları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="45883-120">Describes the ways you can develop web apps using ASP.NET.</span></span>

<span data-ttu-id="45883-121">[Silverlight Windows Phone için .NET API](/previous-versions/windows/apps/jj207211\(v=vs.105\))</span><span class="sxs-lookup"><span data-stu-id="45883-121">[.NET API for Windows Phone Silverlight](/previous-versions/windows/apps/jj207211\(v=vs.105\))</span></span>\
<span data-ttu-id="45883-122">Windows Phone Silverlight ile uygulama oluşturmak için kullanabileceğiniz .NET Framework API 'Leri listeler.</span><span class="sxs-lookup"><span data-stu-id="45883-122">Lists .NET Framework APIs you can use for building apps with Windows Phone Silverlight.</span></span>

## <a name="see-also"></a><span data-ttu-id="45883-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="45883-123">See also</span></span>

- [<span data-ttu-id="45883-124">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="45883-124">.NET Standard</span></span>](../standard/net-standard.md)
- [<span data-ttu-id="45883-125">Genel bakış</span><span class="sxs-lookup"><span data-stu-id="45883-125">Overview</span></span>](./get-started/overview.md)
- [<span data-ttu-id="45883-126">Geliştirme Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="45883-126">Development Guide</span></span>](./development-guide.md)
- [<span data-ttu-id="45883-127">Windows Hizmeti Uygulamaları</span><span class="sxs-lookup"><span data-stu-id="45883-127">Windows Service Applications</span></span>](./windows-services/index.md)
