---
title: "Son değişiklik: .NET Core yerine FrameworkDescription 'un değeri .NET"
description: RunTimeInformation. FrameworkDescription 'un şimdi ".NET Core" yerine ".NET" döndüğü çekirdek .NET kitaplıklarında .NET 5,0 son değişikliği hakkında bilgi edinin.
ms.date: 11/01/2020
ms.openlocfilehash: 3925fb092135c26291e1e60b99f359974d21553c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761558"
---
# <a name="frameworkdescriptions-value-is-net-instead-of-net-core"></a><span data-ttu-id="0ed1b-103">FrameworkDescription 'un değeri .NET Core yerine .NET</span><span class="sxs-lookup"><span data-stu-id="0ed1b-103">FrameworkDescription's value is .NET instead of .NET Core</span></span>

<span data-ttu-id="0ed1b-104"><xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> Şimdi ".NET Core" yerine ".NET" döndürür.</span><span class="sxs-lookup"><span data-stu-id="0ed1b-104"><xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> now returns ".NET" instead of ".NET Core".</span></span>

## <a name="change-description"></a><span data-ttu-id="0ed1b-105">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="0ed1b-105">Change description</span></span>

<span data-ttu-id="0ed1b-106">Önceki .NET sürümlerinde, <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> Açıklama dizesinin parçası olarak ".NET Core" döndürür. Örneğin, `.NET Core 3.1.1` .</span><span class="sxs-lookup"><span data-stu-id="0ed1b-106">In previous .NET versions, <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> returns ".NET Core" as part of the description string, for example, `.NET Core 3.1.1`.</span></span>

<span data-ttu-id="0ed1b-107">.NET 5,0 ' den başlayarak, <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> Açıklama dizesinin parçası olarak ".net" döndürür. Örneğin, `.NET 5.0.0` .</span><span class="sxs-lookup"><span data-stu-id="0ed1b-107">Starting in .NET 5.0, <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> returns ".NET" as part of the description string, for example, `.NET 5.0.0`.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="0ed1b-108">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="0ed1b-108">Reason for change</span></span>

<span data-ttu-id="0ed1b-109">.NET 5 ile, `netcoreapp` `net` kısa hedef çerçeve bilinen adıyla değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="0ed1b-109">With .NET 5, `netcoreapp` is replaced by `net` as the short target-framework moniker.</span></span> <span data-ttu-id="0ed1b-110">Tutarlılık için çerçevenin açıklaması da güncelleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="0ed1b-110">For consistency, the framework's description has also been updated.</span></span> <span data-ttu-id="0ed1b-111">Değişiklik, `FrameworkName` özelliğin dışında herhangi bir yerde kodlanmadığından, yüzeysel <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="0ed1b-111">The change is cosmetic, as the `FrameworkName` isn't encoded anywhere else than in the <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> property.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="0ed1b-112">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="0ed1b-112">Version introduced</span></span>

<span data-ttu-id="0ed1b-113">5.0</span><span class="sxs-lookup"><span data-stu-id="0ed1b-113">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="0ed1b-114">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="0ed1b-114">Recommended action</span></span>

<span data-ttu-id="0ed1b-115">Tarafından döndürülen dizedeki ".NET Core" için arama yapan tüm kodları güncelleştirin <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription> .</span><span class="sxs-lookup"><span data-stu-id="0ed1b-115">Update any code that searches for ".NET Core" in the string returned by <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription>.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="0ed1b-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="0ed1b-116">Affected APIs</span></span>

- <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `P:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription`

-->
