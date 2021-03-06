---
title: 'Son değişiklik: OSPlatform öznitelikleri yeniden adlandırıldı veya kaldırıldı'
description: Bir önizleme sürümünde sunulan işletim sistemi platformu özniteliklerinin kaldırılmış veya yeniden adlandırılmakta olduğu çekirdek .NET kitaplıklarında .NET 5 ile ilgili son değişiklik hakkında bilgi edinin.
ms.date: 11/01/2020
ms.openlocfilehash: 118c5360eb02c1b4d57fccbd3b2cfdeff0b9fe12
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257264"
---
# <a name="osplatform-attributes-renamed-or-removed"></a><span data-ttu-id="a2a84-103">OSPlatform öznitelikleri yeniden adlandırıldı veya kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="a2a84-103">OSPlatform attributes renamed or removed</span></span>

<span data-ttu-id="a2a84-104">.NET 5 Preview 8 ' de tanıtılan aşağıdaki öznitelikler kaldırılmıştır veya yeniden adlandırıldı: `MinimumOSPlatformAttribute` , `RemovedInOSPlatformAttribute` , ve `ObsoletedInOSPlatformAttribute` .</span><span class="sxs-lookup"><span data-stu-id="a2a84-104">The following attributes that were introduced in .NET 5 Preview 8 have been removed or renamed: `MinimumOSPlatformAttribute`, `RemovedInOSPlatformAttribute`, and `ObsoletedInOSPlatformAttribute`.</span></span>

## <a name="change-description"></a><span data-ttu-id="a2a84-105">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="a2a84-105">Change description</span></span>

<span data-ttu-id="a2a84-106">.NET 5 Preview 8, ad alanında aşağıdaki öznitelikleri getirdi <xref:System.Runtime.Versioning> :</span><span class="sxs-lookup"><span data-stu-id="a2a84-106">.NET 5 Preview 8 introduced the following attributes in the <xref:System.Runtime.Versioning> namespace:</span></span>

- `MinimumOSPlatformAttribute`
- `RemovedInOSPlatformAttribute`
- `ObsoletedInOSPlatformAttribute`

<span data-ttu-id="a2a84-107">.NET 5 Preview 8 ' de bir proje, gibi bir [hedef çerçeve](../../../../standard/frameworks.md) adı kullanarak .NET 5 ' ın işletim sistemine özgü bir `net5.0-windows` özelliği hedefliyorsa, derleme bir derleme düzeyi `System.Runtime.Versioning.MinimumOSPlatformAttribute` öznitelik ekler.</span><span class="sxs-lookup"><span data-stu-id="a2a84-107">In .NET 5 Preview 8, when a project targets an OS-specific flavor of .NET 5 by using a [target framework moniker](../../../../standard/frameworks.md) such as `net5.0-windows`, the build adds an assembly-level `System.Runtime.Versioning.MinimumOSPlatformAttribute` attribute.</span></span>

<span data-ttu-id="a2a84-108">.NET 5 RC1 'de, `ObsoletedInOSPlatformAttribute` kaldırılmıştır ve `MinimumOSPlatformAttribute` `RemovedInOSPlatformAttribute` aşağıdaki şekilde yeniden adlandırılmıştır:</span><span class="sxs-lookup"><span data-stu-id="a2a84-108">In .NET 5 RC1, the `ObsoletedInOSPlatformAttribute` has been removed, and `MinimumOSPlatformAttribute` and `RemovedInOSPlatformAttribute` have been renamed as follows:</span></span>

| <span data-ttu-id="a2a84-109">Önizleme 8 adı</span><span class="sxs-lookup"><span data-stu-id="a2a84-109">Preview 8 name</span></span> | <span data-ttu-id="a2a84-110">RC1 ve üzeri adı</span><span class="sxs-lookup"><span data-stu-id="a2a84-110">RC1 and later name</span></span> |
| - | - |
| `MinimumOSPlatformAttribute` | <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> |
| `RemovedInOSPlatformAttribute` | <xref:System.Runtime.Versioning.UnsupportedOSPlatformAttribute> |

<span data-ttu-id="a2a84-111">.NET 5 RC1 ve üzeri sürümlerde, bir proje gibi bir [hedef çerçeve](../../../../standard/frameworks.md) adı kullanarak .NET 5 ' ın işletim sistemine özgü bir `net5.0-windows` özelliğini hedefliyorsa, derleme bir derleme düzeyi <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> öznitelik ekler.</span><span class="sxs-lookup"><span data-stu-id="a2a84-111">In .NET 5 RC1 and later, when a project targets an OS-specific flavor of .NET 5 by using a [target framework moniker](../../../../standard/frameworks.md) such as `net5.0-windows`, the build adds an assembly-level <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> attribute.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="a2a84-112">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="a2a84-112">Reason for change</span></span>

<span data-ttu-id="a2a84-113">.NET 5 Preview 8 ' de <xref:System.Runtime.Versioning> API 'ler için desteklenen platformları belirtmek üzere ' deki öznitelikler sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="a2a84-113">.NET 5 Preview 8 introduced attributes in <xref:System.Runtime.Versioning> to specify supported platforms for APIs.</span></span> <span data-ttu-id="a2a84-114">Öznitelikler, platforma özgü API 'Ler bu API 'Leri desteklemeyen platformlarda kullanılırken derleme uyarıları oluşturmak için [Platform uyumluluk Çözümleyicisi](../../code-analysis/5.0/ca1416-platform-compatibility-analyzer.md) tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a2a84-114">The attributes are consumed by the [Platform compatibility analyzer](../../code-analysis/5.0/ca1416-platform-compatibility-analyzer.md) to produce build warnings when platform-specific APIs are consumed on platforms that don't support those APIs.</span></span>

<span data-ttu-id="a2a84-115">.NET 5 RC1 için platform uyumluluk Çözümleyicisi ' ne platform dışlaması için ek bir özellik eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="a2a84-115">For .NET 5 RC1, an additional feature was added to the platform compatibility analyzer for platform exclusion.</span></span> <span data-ttu-id="a2a84-116">Özelliği, API 'Lerin işletim sistemi platformlarında tamamen desteklenmeyen şekilde işaretlenmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="a2a84-116">The feature allows APIs to be marked as entirely unsupported on OS platforms.</span></span> <span data-ttu-id="a2a84-117">Bu özellik, daha uygun adlar kullanılması da dahil olmak üzere özniteliklerde değişiklikler istendi.</span><span class="sxs-lookup"><span data-stu-id="a2a84-117">That feature prompted changes to the attributes, including using more suitable names.</span></span> <span data-ttu-id="a2a84-118">`ObsoletedInOSPlatformAttribute`Artık gerekli olmadığından kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="a2a84-118">The `ObsoletedInOSPlatformAttribute` was removed because it was no longer needed.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="a2a84-119">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="a2a84-119">Version introduced</span></span>

<span data-ttu-id="a2a84-120">5,0 RC1</span><span class="sxs-lookup"><span data-stu-id="a2a84-120">5.0 RC1</span></span>

## <a name="recommended-action"></a><span data-ttu-id="a2a84-121">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="a2a84-121">Recommended action</span></span>

<span data-ttu-id="a2a84-122">Projenizi .NET 5 Preview 8 ' den .NET 5 RC1 'ye yeniden hedeflerken, bu değişiklikler nedeniyle derleme veya çalışma zamanı hatalarıyla karşılaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a2a84-122">When you retarget your project from .NET 5 Preview 8 to .NET 5 RC1, you might encounter build or run-time errors due to these changes.</span></span> <span data-ttu-id="a2a84-123">Örneğin, `MinimumOSPlatformAttribute` özniteliği derleme zamanında platforma özgü derlemelere uygulandığından ve eski derleme yapıtlarının hala eskı API adına başvurmasına neden olduğu için, yeniden adlandırmada hata oluşma olasılığı yüksektir.</span><span class="sxs-lookup"><span data-stu-id="a2a84-123">For example, the renaming of `MinimumOSPlatformAttribute` is likely to produce errors, because the attribute is applied to platform-specific assemblies at build time, and old build artifacts will still reference the old API name.</span></span>

<span data-ttu-id="a2a84-124">Örnek derleme zamanı hataları:</span><span class="sxs-lookup"><span data-stu-id="a2a84-124">Example build-time errors:</span></span>

- <span data-ttu-id="a2a84-125">**hata CS0246: ' MinimumOSPlatformAttribute ' türü veya ad alanı adı bulunamadı (bir using yönergeniz veya derleme başvurunuz mu eksik?)**</span><span class="sxs-lookup"><span data-stu-id="a2a84-125">**error CS0246: The type or namespace name 'MinimumOSPlatformAttribute' could not be found (are you missing a using directive or an assembly reference?)**</span></span>
- <span data-ttu-id="a2a84-126">**hata CS0246: ' RemovedInOSPlatformAttribute ' türü veya ad alanı adı bulunamadı (bir using yönergeniz veya derleme başvurunuz mu eksik?)**</span><span class="sxs-lookup"><span data-stu-id="a2a84-126">**error CS0246: The type or namespace name 'RemovedInOSPlatformAttribute' could not be found (are you missing a using directive or an assembly reference?)**</span></span>
- <span data-ttu-id="a2a84-127">**hata CS0246: ' ObsoletedInOSPlatformAttribute ' türü veya ad alanı adı bulunamadı (bir using yönergeniz veya derleme başvurunuz mu eksik?)**</span><span class="sxs-lookup"><span data-stu-id="a2a84-127">**error CS0246: The type or namespace name 'ObsoletedInOSPlatformAttribute' could not be found (are you missing a using directive or an assembly reference?)**</span></span>

<span data-ttu-id="a2a84-128">Örnek çalışma zamanı hatası:</span><span class="sxs-lookup"><span data-stu-id="a2a84-128">Example run-time error:</span></span>

<span data-ttu-id="a2a84-129">**İşlenmeyen özel durum. System. TypeLoadException: ' System. Runtime, Version = 5.0.0.0, Culture = neutral, PublicKeyToken = b03f5f7f11d50a3a ' derlemesinden ' System. Runtime. sürümkodu. MinimumOSPlatformAttribute ' türü yüklenemedi.**</span><span class="sxs-lookup"><span data-stu-id="a2a84-129">**Unhandled exception. System.TypeLoadException: Could not load type 'System.Runtime.Versioning.MinimumOSPlatformAttribute' from assembly 'System.Runtime, Version=5.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a'.**</span></span>

<span data-ttu-id="a2a84-130">Bu hataları çözmek için:</span><span class="sxs-lookup"><span data-stu-id="a2a84-130">To resolve these errors:</span></span>

- <span data-ttu-id="a2a84-131">Tüm başvurularını güncelleştirin `MinimumOSPlatformAttribute` <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> .</span><span class="sxs-lookup"><span data-stu-id="a2a84-131">Update any references of `MinimumOSPlatformAttribute` to <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute>.</span></span>
- <span data-ttu-id="a2a84-132">Tüm başvurularını güncelleştirin `RemovedInOSPlatformAttribute` <xref:System.Runtime.Versioning.UnsupportedOSPlatformAttribute> .</span><span class="sxs-lookup"><span data-stu-id="a2a84-132">Update any references of `RemovedInOSPlatformAttribute` to <xref:System.Runtime.Versioning.UnsupportedOSPlatformAttribute>.</span></span>
- <span data-ttu-id="a2a84-133">Tüm başvuruları kaldırın `ObsoletedInOSPlatformAttribute` .</span><span class="sxs-lookup"><span data-stu-id="a2a84-133">Remove any references to `ObsoletedInOSPlatformAttribute`.</span></span>
- <span data-ttu-id="a2a84-134">Eski derleme yapılarını silmek için projenizi yeniden derleyin (veya temiz + derleme gerçekleştirin).</span><span class="sxs-lookup"><span data-stu-id="a2a84-134">Rebuild your project (or perform clean + build) to delete old build artifacts.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="a2a84-135">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="a2a84-135">Affected APIs</span></span>

- `System.Runtime.Versioning.MinimumOSPlatformAttribute`
- `System.Runtime.Versioning.ObsoletedInOSPlatformAttribute`
- `System.Runtime.Versioning.RemovedInOSPlatformAttribute`

<!--

### Category

Core .NET libraries

### Affected APIs

- `T:System.Runtime.Versioning.MinimumOSPlatformAttribute`
- `T:System.Runtime.Versioning.ObsoletedInOSPlatformAttribute`
- `T:System.Runtime.Versioning.RemovedInOSPlatformAttribute`

-->
