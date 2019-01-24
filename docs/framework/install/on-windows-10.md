---
title: Windows 10 üzerinde .NET Framework yükleme
description: Windows 10 veya Windows Server 2016 üzerinde .NET Framework'ü yüklemeyi öğrenin.
author: rlander
ms.author: mairaw
ms.date: 04/10/2018
ms.custom: updateeachrelease
ms.openlocfilehash: 08f2640613335b0ba54a4ff970b7d105d52b92c7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54743484"
---
# <a name="install-the-net-framework-on-windows-10-and-windows-server-2016"></a><span data-ttu-id="5f76d-103">Windows 10 ve Windows Server 2016 üzerinde .NET Framework yükleme</span><span class="sxs-lookup"><span data-stu-id="5f76d-103">Install the .NET Framework on Windows 10 and Windows Server 2016</span></span>

<span data-ttu-id="5f76d-104">.NET Framework, Windows üzerinde birçok uygulama çalıştırmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="5f76d-104">The .NET Framework is required to run many applications on Windows.</span></span> <span data-ttu-id="5f76d-105">Bu makaledeki yönergeleri gereken .NET Framework sürümlerini yüklemenize yardımcı olması.</span><span class="sxs-lookup"><span data-stu-id="5f76d-105">The instructions in this article should help you install the .NET Framework versions that you need.</span></span> <span data-ttu-id="5f76d-106">[.NET Framework 4.7.2](https://go.microsoft.com/fwlink/?LinkID=863255) kullanılabilir en son sürümü.</span><span class="sxs-lookup"><span data-stu-id="5f76d-106">The [.NET Framework 4.7.2](https://go.microsoft.com/fwlink/?LinkID=863255) is the latest available version.</span></span>

<span data-ttu-id="5f76d-107">Bir uygulama çalıştırmaya ve makinenizde aşağıdakine benzer bir iletişim kutusu görmesini sonra bu sayfada gelmedi:</span><span class="sxs-lookup"><span data-stu-id="5f76d-107">You may have arrived on this page after trying to run an application and seeing a dialog on your machine similar to the following one:</span></span>

![Bu uygulama başlatılamadı](./media/this-application-could-not-be-started.png)

## <a name="net-framework-472"></a><span data-ttu-id="5f76d-109">.NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="5f76d-109">.NET Framework 4.7.2</span></span>

<span data-ttu-id="5f76d-110">.NET Framework 4.7.2 bulunur:</span><span class="sxs-lookup"><span data-stu-id="5f76d-110">The .NET Framework 4.7.2 is included with:</span></span>

* [<span data-ttu-id="5f76d-111">Windows 10 Ekim 2018 güncelleştirmesi</span><span class="sxs-lookup"><span data-stu-id="5f76d-111">Windows 10 October 2018 Update</span></span>](https://support.microsoft.com/help/4028685/windows-10-get-the-update)

* [<span data-ttu-id="5f76d-112">Windows 10 Nisan 2018 güncelleştirmesi</span><span class="sxs-lookup"><span data-stu-id="5f76d-112">Windows 10 April 2018 Update</span></span>](https://www.microsoft.com/software-download/windows10)

> [!div class="button"]
> [<span data-ttu-id="5f76d-113">.NET Framework'ün 4.7.2 indirin</span><span class="sxs-lookup"><span data-stu-id="5f76d-113">Download .NET Framework 4.7.2</span></span>](https://www.microsoft.com/net/download/thank-you/net472?utm_source=ms-docs&utm_medium=referral)

<span data-ttu-id="5f76d-114">[.NET Framework 4.7.2](https://go.microsoft.com/fwlink/?LinkID=863255) 4.7.1 aracılığıyla .NET Framework 4.0 için oluşturulan uygulamalarını çalıştırmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5f76d-114">The [.NET Framework 4.7.2](https://go.microsoft.com/fwlink/?LinkID=863255) can be used to run applications built for the .NET Framework 4.0 through 4.7.1.</span></span>

<span data-ttu-id="5f76d-115">Yükleyebileceğiniz [.NET Framework 4.7.2](https://go.microsoft.com/fwlink/?LinkID=863255) üzerinde:</span><span class="sxs-lookup"><span data-stu-id="5f76d-115">You can install the [.NET Framework 4.7.2](https://go.microsoft.com/fwlink/?LinkID=863255) on:</span></span>

* <span data-ttu-id="5f76d-116">Windows 10 Fall Creators Update (1709 sürümü)</span><span class="sxs-lookup"><span data-stu-id="5f76d-116">Windows 10 Fall Creators Update (version 1709)</span></span>
* <span data-ttu-id="5f76d-117">Windows 10 Creators Update (sürüm 1703)</span><span class="sxs-lookup"><span data-stu-id="5f76d-117">Windows 10 Creators Update (version 1703)</span></span>
* <span data-ttu-id="5f76d-118">Windows 10 Yıldönümü Güncelleştirmesi (sürüm 1607)</span><span class="sxs-lookup"><span data-stu-id="5f76d-118">Windows 10 Anniversary Update (version 1607)</span></span>
* <span data-ttu-id="5f76d-119">Windows Server 1709 sürümü</span><span class="sxs-lookup"><span data-stu-id="5f76d-119">Windows Server, version 1709</span></span>
* <span data-ttu-id="5f76d-120">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="5f76d-120">Windows Server 2016</span></span>

<span data-ttu-id="5f76d-121">.NET Framework 4.7.2 desteklenmiyor:</span><span class="sxs-lookup"><span data-stu-id="5f76d-121">The .NET Framework 4.7.2 is not supported on:</span></span>

* <span data-ttu-id="5f76d-122">Windows 10 1507</span><span class="sxs-lookup"><span data-stu-id="5f76d-122">Windows 10 1507</span></span>
* <span data-ttu-id="5f76d-123">Windows 10 1511</span><span class="sxs-lookup"><span data-stu-id="5f76d-123">Windows 10 1511</span></span>

<span data-ttu-id="5f76d-124">Windows 10 1507 veya 1511 kullanıyorsanız ve .NET Framework'ü 4.7.2 yüklemek istiyorsanız, önce daha sonraki bir Windows 10 sürümüne yükseltmek gerekir.</span><span class="sxs-lookup"><span data-stu-id="5f76d-124">If you're using Windows 10 1507 or 1511 and you want to install the .NET Framework 4.7.2, you first need to upgrade to a later Windows 10 version.</span></span>

## <a name="net-framework-462"></a><span data-ttu-id="5f76d-125">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="5f76d-125">.NET Framework 4.6.2</span></span>

<span data-ttu-id="5f76d-126">[.NET Framework 4.6.2](https://www.microsoft.com/en-us/download/details.aspx?id=53345) en son desteklenen .NET Framework Windows 10 1507 ve 1511 sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="5f76d-126">The [.NET Framework 4.6.2](https://www.microsoft.com/en-us/download/details.aspx?id=53345) is the latest supported .NET Framework version on Windows 10 1507 and 1511.</span></span>

<span data-ttu-id="5f76d-127">.NET Framework 4.6.2, .NET Framework 4.0 4.6.2 aracılığıyla oluşturulan uygulamaları destekler.</span><span class="sxs-lookup"><span data-stu-id="5f76d-127">The .NET Framework 4.6.2 supports apps built for the .NET Framework 4.0 through 4.6.2.</span></span>

## <a name="net-framework-35"></a><span data-ttu-id="5f76d-128">.NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="5f76d-128">.NET Framework 3.5</span></span>

<span data-ttu-id="5f76d-129">Yüklemek için yönergeleri izleyin [Windows 10 üzerinde .NET Framework 3.5](dotnet-35-windows-10.md).</span><span class="sxs-lookup"><span data-stu-id="5f76d-129">Follow the instructions to install the [.NET Framework 3.5 on Windows 10](dotnet-35-windows-10.md).</span></span>

<span data-ttu-id="5f76d-130">.NET Framework 3.5 .NET Framework 1.0 3.5 aracılığıyla oluşturulan uygulamaları destekler.</span><span class="sxs-lookup"><span data-stu-id="5f76d-130">The .NET Framework 3.5 supports apps built for the .NET Framework 1.0 through 3.5.</span></span>

## <a name="additional-information"></a><span data-ttu-id="5f76d-131">Ek bilgiler</span><span class="sxs-lookup"><span data-stu-id="5f76d-131">Additional information</span></span>

<span data-ttu-id="5f76d-132">.NET framework 4.x önceki sürümleri için yerinde güncelleştirmeler sürümleridir.</span><span class="sxs-lookup"><span data-stu-id="5f76d-132">.NET Framework 4.x versions are in-place updates to earlier versions.</span></span> <span data-ttu-id="5f76d-133">Aşağıdaki ifade etmektedir:</span><span class="sxs-lookup"><span data-stu-id="5f76d-133">That means the following:</span></span>

- <span data-ttu-id="5f76d-134">Yalnızca .NET Framework'ün bir sürümünü olabilir, makinenizde yüklü 4.x.</span><span class="sxs-lookup"><span data-stu-id="5f76d-134">You can only have one version of the .NET Framework 4.x installed on your machine.</span></span>

- <span data-ttu-id="5f76d-135">Sonraki bir sürümü zaten yüklü değilse, makinenizde .NET Framework'ün önceki bir sürümünü yükleyemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="5f76d-135">You cannot install an earlier version of the .NET Framework on your machine if a later version is already installed.</span></span>

- <span data-ttu-id="5f76d-136">.NET Framework 4.x sürümleri, .NET Framework 4.0 bu sürümü ile oluşturulmuş uygulamaları çalıştırmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5f76d-136">4.x versions of the .NET Framework can be used to run applications built for the .NET Framework 4.0 through that version.</span></span> <span data-ttu-id="5f76d-137">Örneğin, .NET Framework 4.7, .NET Framework 4.0 4.7 aracılığıyla oluşturulan uygulamalarını çalıştırmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5f76d-137">For example, .NET Framework 4.7 can be used to run applications built for the .NET Framework 4.0 through 4.7.</span></span> <span data-ttu-id="5f76d-138">En son sürümünü (.NET Framework 4.7.2), .NET Framework 4.0 ile başlayan tüm sürümleri ile oluşturulan uygulamalarını çalıştırmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5f76d-138">The latest version (the .NET Framework 4.7.2) can be used to run applications built with all versions of the .NET Framework starting with 4.0.</span></span>

<span data-ttu-id="5f76d-139">İndirmek kullanılabilir .NET Framework'ün tüm sürümleri listesi için bkz. [.NET indirir](https://www.microsoft.com/net/download?utm_source=ms-docs&utm_medium=referral) sayfası.</span><span class="sxs-lookup"><span data-stu-id="5f76d-139">For a list of all the versions of the .NET Framework available to download, see the [.NET Downloads](https://www.microsoft.com/net/download?utm_source=ms-docs&utm_medium=referral) page.</span></span>

## <a name="help"></a><span data-ttu-id="5f76d-140">Yardım</span><span class="sxs-lookup"><span data-stu-id="5f76d-140">Help</span></span>

<span data-ttu-id="5f76d-141">Yüklü .NET Framework'ün doğru sürümü alınamıyor. Yapabiliyorsanız [Yardım için Microsoft ile iletişime geçin](mailto:dotnet-install-help@service.microsoft.com?subject=Install-Help).</span><span class="sxs-lookup"><span data-stu-id="5f76d-141">If you cannot get the correct version of the .NET Framework installed, you can [contact Microsoft for help](mailto:dotnet-install-help@service.microsoft.com?subject=Install-Help).</span></span>

## <a name="see-also"></a><span data-ttu-id="5f76d-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5f76d-142">See also</span></span>

- [<span data-ttu-id="5f76d-143">.NET yükleme</span><span class="sxs-lookup"><span data-stu-id="5f76d-143">.NET Downloads</span></span>](https://www.microsoft.com/net/download?utm_source=ms-docs&utm_medium=referral)
- [<span data-ttu-id="5f76d-144">Engellenen .NET Framework yükleme ve kaldırma sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="5f76d-144">Troubleshoot blocked .NET Framework installations and uninstallations</span></span>](troubleshoot-blocked-installations-and-uninstallations.md)
- [<span data-ttu-id="5f76d-145">Geliştiriciler için .NET Framework'ü yükleme</span><span class="sxs-lookup"><span data-stu-id="5f76d-145">Install the .NET Framework for developers</span></span>](guide-for-developers.md)
