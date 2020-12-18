---
title: 'NETSDK1005 ve NETSDK1047: varlık dosyasında hedef yok'
description: Bir hedef eksik olan varlık dosyası sorununu çözme.
author: sfoslund
ms.topic: error-reference
ms.date: 12/17/2020
f1_keywords:
- NETSDK1005
- NETSDK1047
ms.openlocfilehash: e3e7389adf6a9a715d44661a5f7cbae5efe299e4
ms.sourcegitcommit: 4b79862c5b41fbd86cf38f926f6a49516059f6f2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/18/2020
ms.locfileid: "97678171"
---
# <a name="netsdk1005-and-netsdk1047-asset-file-is-missing-target"></a><span data-ttu-id="ce83e-103">NETSDK1005 ve NETSDK1047: varlık dosyasında hedef yok</span><span class="sxs-lookup"><span data-stu-id="ce83e-103">NETSDK1005 and NETSDK1047: Asset file is missing target</span></span>

<span data-ttu-id="ce83e-104">**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 2.1.100 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="ce83e-104">**This article applies to:** ✔️ .NET Core 2.1.100 SDK and later versions</span></span>

<span data-ttu-id="ce83e-105">.NET SDK hatası NETSDK1005 veya NETSDK1047 hata verdiği zaman, projenin varlıklar dosyasında hedef çerçevelerinizdeki bir bilgi eksik.</span><span class="sxs-lookup"><span data-stu-id="ce83e-105">When the .NET SDK issues error NETSDK1005 or NETSDK1047, the project's assets file is missing information on one of your target frameworks.</span></span> <span data-ttu-id="ce83e-106">NuGet, *obj* klasöründe *project.assets.js* adlı bir dosya yazar ve .NET SDK bunu derleyiciye geçirilecek paketler hakkında bilgi almak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="ce83e-106">NuGet writes a file named *project.assets.json* in the *obj* folder, and the .NET SDK uses it to get information about packages to pass into the compiler.</span></span> <span data-ttu-id="ce83e-107">.NET 5 ' te, NuGet adlı yeni bir alan ekledi `TargetFrameworkAlias` , bu nedenle MSBuild veya NuGet 'in önceki sürümleri yeni alan olmadan bir varlık dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ce83e-107">In .NET 5, NuGet added a new field named `TargetFrameworkAlias`, so earlier versions of MSBuild or NuGet generate an assets file without the new field.</span></span> <span data-ttu-id="ce83e-108">Daha fazla bilgi için bkz. [Error NETSDK1005](https://developercommunity.visualstudio.com/content/problem/1248649/error-netsdk1005-assets-file-projectassetsjson-doe.html).</span><span class="sxs-lookup"><span data-stu-id="ce83e-108">For more information, see [error NETSDK1005](https://developercommunity.visualstudio.com/content/problem/1248649/error-netsdk1005-assets-file-projectassetsjson-doe.html).</span></span>

<span data-ttu-id="ce83e-109">Bu hatayı çözebilecek bazı eylemler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="ce83e-109">Here are some actions you can take that may resolve the error:</span></span>

* <span data-ttu-id="ce83e-110">MSBuild sürüm 16,8 veya üstünü, NuGet sürüm 5,8 veya üstünü kullandığınızdan emin olun ve araçlarınızı güncelleştirdikten sonra projeyi geri yükleyin.</span><span class="sxs-lookup"><span data-stu-id="ce83e-110">Make sure that you're using MSBuild version 16.8 or later and NuGet version 5.8 or later, and restore the project after updating your tools.</span></span> <span data-ttu-id="ce83e-111">NuGet sürüm 5,8 veya üstünü kullanırken, Visual Studio 2019 sürüm 16,8 veya üzeri, MSBuild sürüm 16,8 veya üzeri ve .NET 5,0 SDK veya sonraki bir sürümünü kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ce83e-111">When you're using NuGet version 5.8 or later, you should be using Visual Studio 2019 version 16.8 or later, MSBuild version 16.8 or later, and .NET 5.0 SDK or later.</span></span>

* <span data-ttu-id="ce83e-112">Visual Studio 2019 ' de proje derlerken hata alırsanız, sürüm 16,8 ' yi yükledikten sonra veya projenin hedef çerçevesini değiştirdikten sonra projeyi ikinci kez derleyin.</span><span class="sxs-lookup"><span data-stu-id="ce83e-112">If you get the error while building a project in Visual Studio 2019 for the first time after installing version 16.8 or after changing the project's target framework, build the project a second time.</span></span>

* <span data-ttu-id="ce83e-113">Projeyi oluşturmadan önce *obj* klasörünü silin.</span><span class="sxs-lookup"><span data-stu-id="ce83e-113">Delete the *obj* folder before building the project.</span></span>

* <span data-ttu-id="ce83e-114">Eksik hedef değerin projenizin özelliğine eklendiğinden emin olun `TargetFrameworks` .</span><span class="sxs-lookup"><span data-stu-id="ce83e-114">Make sure that the missing target value is included in the `TargetFrameworks` property of your project.</span></span>
