---
title: 'NETSDK1145: hedefleme veya apphost paketi eksik'
description: NuGet paketi geri yüklemesi desteklenmediğinden hedefleme paketinin sorunu nasıl çözümlenir?
author: wli3
ms.topic: error-reference
ms.date: 09/14/2020
f1_keywords:
- NETSDK1145
ms.openlocfilehash: c343952582cafb63eae388fd216769e6c67d4741
ms.sourcegitcommit: 636af37170ae75a11c4f7d1ecd770820e7dfe7bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2020
ms.locfileid: "91805326"
---
# <a name="netsdk1145-targeting-or-apphost-pack-missing"></a><span data-ttu-id="16f93-103">NETSDK1145: hedefleme veya apphost paketi eksik</span><span class="sxs-lookup"><span data-stu-id="16f93-103">NETSDK1145: Targeting or apphost pack missing</span></span>

<span data-ttu-id="16f93-104">**Bu makale şu şekilde geçerlidir:** ✔️ .NET 5.0.100 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="16f93-104">**This article applies to:** ✔️ .NET 5.0.100 SDK and later versions</span></span>

<span data-ttu-id="16f93-105">.NET SDK hatası NETSDK1145 hata verdiği zaman, hedefleme veya apphost paketi yüklenmez ve NuGet paketi geri yükleme desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="16f93-105">When the .NET SDK issues error NETSDK1145, the targeting or apphost pack is not installed and NuGet package restore is not supported.</span></span> <span data-ttu-id="16f93-106">Bu, genellikle C++/CLı projeleri için Visual Studio 'ya dahil olandan daha yeni bir SDK olma nedeniyle oluşur.</span><span class="sxs-lookup"><span data-stu-id="16f93-106">This is typically caused by having a newer SDK than the one included in Visual Studio for C++/CLI projects.</span></span> <span data-ttu-id="16f93-107">Visual Studio 'Yu yükseltin, belirli bir SDK sürümü belirtiyorsa _global.json 'u_ kaldırın ve daha yeni SDK 'yı kaldırın.</span><span class="sxs-lookup"><span data-stu-id="16f93-107">Upgrade Visual Studio, remove _global.json_ if it specifies a certain SDK version, and uninstall the newer SDK.</span></span> <span data-ttu-id="16f93-108">Alternatif olarak, hedefleme veya apphost sürümünü geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="16f93-108">Alternatively, you could override the targeting or apphost version.</span></span> <span data-ttu-id="16f93-109">Hata iletisinden paket dizini altında bulunan sürümü bulun ve projenin hedef çerçevesiyle eşleşir.</span><span class="sxs-lookup"><span data-stu-id="16f93-109">Find the version that exists under the pack directory from the error message and matches the target framework of the project.</span></span> <span data-ttu-id="16f93-110">Aşağıdakileri projeye ekleyin:</span><span class="sxs-lookup"><span data-stu-id="16f93-110">Add the following to the project:</span></span>

<span data-ttu-id="16f93-111">Apphost paketi için</span><span class="sxs-lookup"><span data-stu-id="16f93-111">For apphost pack</span></span>

```xml
<ItemGroup>
  <KnownAppHostPack Update="@(KnownAppHostPack)">
    <AppHostPackVersion Condition="'%(TargetFramework)' == 'TARGETFRAMEWORK'">EXISTINGVERSION</AppHostPackVersion>
  </KnownAppHostPack>
</ItemGroup>
```

<span data-ttu-id="16f93-112">Hedefleme paketi için</span><span class="sxs-lookup"><span data-stu-id="16f93-112">For targeting pack</span></span>

```xml
<ItemGroup>
  <KnownAppHostPack Update="@(KnownAppHostPack)">
    <AppHostPackVersion Condition="'%(TargetFramework)' == 'TARGETFRAMEWORK'">EXISTINGVERSION</AppHostPackVersion>
  </KnownAppHostPack>
</ItemGroup>
```
