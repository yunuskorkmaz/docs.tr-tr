---
title: "Windows XP'de .NET Framework'ü yüklemek"
description: "Windows XP'de .NET Framework'ü yüklemek öğrenin."
author: rlander
ms.author: mairaw
keywords: ".NET framework, yükleme"
ms.date: 08/03/2017
ms.topic: article
ms.prod: .net-framework
ms.devlang: dotnet
ms.openlocfilehash: f79ae387b123527b3795a2e12a68bd153b308f81
ms.sourcegitcommit: 62d3e3e74c1b7ffa927590012c0b9f87de1b0848
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
---
# <a name="install-the-net-framework-on-windows-xp-and-windows-server-2003"></a><span data-ttu-id="de11d-104">.NET Framework Windows XP ve Windows Server 2003 üzerinde yükleme</span><span class="sxs-lookup"><span data-stu-id="de11d-104">Install the .NET Framework on Windows XP and Windows Server 2003</span></span>

> [!NOTE]
> <span data-ttu-id="de11d-105">Windows XP artık Microsoft tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="de11d-105">Windows XP is no longer supported by Microsoft.</span></span> <span data-ttu-id="de11d-106">Windows desteklenir ve .NET Framework'ün en son sürümünü içeren 10'a, yükseltme öneririz.</span><span class="sxs-lookup"><span data-stu-id="de11d-106">We recommend you upgrade to Windows 10, which is supported and includes the latest version of the .NET Framework.</span></span> <span data-ttu-id="de11d-107">Bu belge, yalnızca bir yararlı sorun giderme kılavuzu sağlanır.</span><span class="sxs-lookup"><span data-stu-id="de11d-107">This document is provided solely as a helpful troubleshooting guide.</span></span>

<span data-ttu-id="de11d-108">.NET Framework Windows birçok uygulamaları çalıştırmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="de11d-108">The .NET Framework is required to run many applications on Windows.</span></span> <span data-ttu-id="de11d-109">Yüklemek için aşağıdaki yönergeleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="de11d-109">You can use the following instructions to install it.</span></span> <span data-ttu-id="de11d-110">Bir uygulamayı çalıştırmak çalışıyor ve makinenizde aşağıdaki iletişim görmesini sonra bu sayfada gelmedi.</span><span class="sxs-lookup"><span data-stu-id="de11d-110">You may have arrived on this page after trying to run an application and seeing the following dialog on your machine.</span></span>

![Bu uygulama başlatılamadı](./media/this-application-could-not-be-started.png)

<span data-ttu-id="de11d-112">Bu yönergeleri, ihtiyacınız olan .NET Framework sürümlerini yüklemenize yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="de11d-112">These instructions will help you install the .NET Framework versions you need.</span></span> <span data-ttu-id="de11d-113">[.NET Framework 4.7.1](https://www.microsoft.com/en-us/download/details.aspx?id=56115&desc=dotnet47) en son sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="de11d-113">The [.NET Framework 4.7.1](https://www.microsoft.com/en-us/download/details.aspx?id=56115&desc=dotnet47) is the latest version.</span></span> <span data-ttu-id="de11d-114">Windows XP ve Windows Server 2003'te desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="de11d-114">It is not supported on Windows XP and Windows Server 2003.</span></span> <span data-ttu-id="de11d-115">Dahil olan [Windows 10 sonbaharda oluşturucuları güncelleştirme](https://www.microsoft.com/software-download/windows10) ve [Windows Server 2016 sürüm 1709](https://docs.microsoft.com/windows-server/get-started/get-started-with-1709).</span><span class="sxs-lookup"><span data-stu-id="de11d-115">It is included with the [Windows 10 Fall Creators Update](https://www.microsoft.com/software-download/windows10) and [Windows Server 2016 Version 1709](https://docs.microsoft.com/windows-server/get-started/get-started-with-1709).</span></span>

## <a name="net-framework-403"></a><span data-ttu-id="de11d-116">.NET framework 4.0.3</span><span class="sxs-lookup"><span data-stu-id="de11d-116">.NET Framework 4.0.3</span></span>

<span data-ttu-id="de11d-117">[.NET Framework 4.0.3](http://go.microsoft.com/fwlink/?LinkID=213834) en son desteklenen .NET Framework sürümü Windows XP ve Windows Server 2003'te.</span><span class="sxs-lookup"><span data-stu-id="de11d-117">The [.NET Framework 4.0.3](http://go.microsoft.com/fwlink/?LinkID=213834) is the latest supported .NET Framework version on Windows XP and Windows Server 2003.</span></span> <span data-ttu-id="de11d-118">.NET Framework 4.0.3 gerektiren [.NET Framework 4](http://go.microsoft.com/fwlink/?LinkID=213834) ilk olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="de11d-118">The .NET Framework 4.0.3 requires that the [.NET Framework 4](http://go.microsoft.com/fwlink/?LinkID=213834) is installed first.</span></span> <span data-ttu-id="de11d-119">Bu iki .NET Framework sürüm artık Microsoft tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="de11d-119">Both of these .NET Framework versions are no longer supported by Microsoft.</span></span>

## <a name="net-framework-4"></a><span data-ttu-id="de11d-120">.NET Framework 4</span><span class="sxs-lookup"><span data-stu-id="de11d-120">.NET Framework 4</span></span>

<span data-ttu-id="de11d-121">Yükleyebileceğiniz [.NET Framework 4](http://go.microsoft.com/fwlink/?LinkID=213834&dotnetdocs) Windows XP.</span><span class="sxs-lookup"><span data-stu-id="de11d-121">You can install the [.NET Framework 4](http://go.microsoft.com/fwlink/?LinkID=213834&dotnetdocs) on Windows XP.</span></span> <span data-ttu-id="de11d-122">Ayrıca, Microsoft tarafından artık desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="de11d-122">It's no longer supported by Microsoft.</span></span>

## <a name="net-framework-35"></a><span data-ttu-id="de11d-123">.NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="de11d-123">.NET Framework 3.5</span></span>

<span data-ttu-id="de11d-124">Yükleyebileceğiniz [.NET Framework 3.5](http://go.microsoft.com/fwlink/?LinkID=213834&dotnetdocs) Windows XP.</span><span class="sxs-lookup"><span data-stu-id="de11d-124">You can install the [.NET Framework 3.5](http://go.microsoft.com/fwlink/?LinkID=213834&dotnetdocs) on Windows XP.</span></span>

<span data-ttu-id="de11d-125">.NET Framework 3.5, .NET Framework 1.0 için 3.5 oluşturulan uygulamaları çalıştırmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="de11d-125">The .NET Framework 3.5 can be used to run applications built for .NET Framework 1.0 through 3.5.</span></span>

## <a name="see-also"></a><span data-ttu-id="de11d-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="de11d-126">See also</span></span>

<span data-ttu-id="de11d-127">[.NET Framework indirin](https://www.microsoft.com/net/download/framework?utm_source=ms-docs&utm_medium=referral) </span><span class="sxs-lookup"><span data-stu-id="de11d-127">[Download the .NET Framework](https://www.microsoft.com/net/download/framework?utm_source=ms-docs&utm_medium=referral) </span></span>  
<span data-ttu-id="de11d-128">[Engellenen .NET Framework yükleme ve kaldırma sorunlarını giderme](troubleshoot-blocked-installations-and-uninstallations.md) </span><span class="sxs-lookup"><span data-stu-id="de11d-128">[Troubleshoot blocked .NET Framework installations and uninstallations](troubleshoot-blocked-installations-and-uninstallations.md) </span></span>  
[<span data-ttu-id="de11d-129">Geliştiriciler için .NET Framework'ü yükleme</span><span class="sxs-lookup"><span data-stu-id="de11d-129">Install the .NET Framework for developers</span></span>](guide-for-developers.md)
