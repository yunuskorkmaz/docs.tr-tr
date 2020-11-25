---
title: "Son değişiklik: TargetFramework, netcoreapp 'ten net 'e değiştirildi"
description: MSBuild TargetFramework özelliği için değerin netcoreapp 3.1'den net 5.0'a değiştiği .NET 5,0 ' deki Son değişiklik hakkında bilgi edinin.
ms.date: 10/17/2020
ms.openlocfilehash: c3b39a36548d58d6ed75fd8b1c84b0cccfc738f0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761450"
---
# <a name="targetframework-change-from-netcoreapp-to-net"></a><span data-ttu-id="36652-103">TargetFramework, netcoreapp 'ten net 'e değişiklik</span><span class="sxs-lookup"><span data-stu-id="36652-103">TargetFramework change from netcoreapp to net</span></span>

<span data-ttu-id="36652-104">MSBuild `TargetFramework` özelliğinin değeri iken `netcoreapp3.1` olarak değiştirildi `net5.0` .</span><span class="sxs-lookup"><span data-stu-id="36652-104">The value for the MSBuild `TargetFramework` property changed from `netcoreapp3.1` to `net5.0`.</span></span> <span data-ttu-id="36652-105">Bu, değerini ayrıştırmaya dayalı kodu kesebilir `TargetFramework` .</span><span class="sxs-lookup"><span data-stu-id="36652-105">This can break code that relies on parsing the value of `TargetFramework`.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="36652-106">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="36652-106">Version introduced</span></span>

<span data-ttu-id="36652-107">5.0</span><span class="sxs-lookup"><span data-stu-id="36652-107">5.0</span></span>

## <a name="change-description"></a><span data-ttu-id="36652-108">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="36652-108">Change description</span></span>

<span data-ttu-id="36652-109">.NET Core 1,0-3,1 ' de, MSBuild `TargetFramework` özelliğinin değeri `netcoreapp` , örneğin `netcoreapp3.1` .NET Core 3,1 ' i hedefleyen uygulamalar için ile başlar.</span><span class="sxs-lookup"><span data-stu-id="36652-109">In .NET Core 1.0 - 3.1, the value for the MSBuild `TargetFramework` property starts with `netcoreapp`, for example, `netcoreapp3.1` for apps that target .NET Core 3.1.</span></span> <span data-ttu-id="36652-110">.NET 5,0 ' den başlayarak, bu değer .NET 5,0 için yalnızca ile başlamak üzere basitleştirilmiştir `net` `net5.0` .</span><span class="sxs-lookup"><span data-stu-id="36652-110">Starting in .NET 5.0, this value is simplified to just start with `net`, for example, `net5.0` for .NET 5.0.</span></span>

<span data-ttu-id="36652-111">Daha fazla bilgi için, [The future of .NET Standard](https://devblogs.microsoft.com/dotnet/the-future-of-net-standard/) [.NET 5 ' te .NET Standard ve hedef çerçeve adları](https://github.com/dotnet/designs/blob/main/accepted/2020/net5/net5.md)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="36652-111">For more information, see [The future of .NET Standard](https://devblogs.microsoft.com/dotnet/the-future-of-net-standard/) and [Target framework names in .NET 5](https://github.com/dotnet/designs/blob/main/accepted/2020/net5/net5.md).</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="36652-112">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="36652-112">Reason for change</span></span>

- <span data-ttu-id="36652-113">Değeri basitleştirir `TargetFramework` .</span><span class="sxs-lookup"><span data-stu-id="36652-113">Simplifies the `TargetFramework` value.</span></span>
- <span data-ttu-id="36652-114">Projelerin özelliği içine içermesini sağlar `TargetPlatform` `TargetFramework` .</span><span class="sxs-lookup"><span data-stu-id="36652-114">Enables projects to include a `TargetPlatform` in the `TargetFramework` property.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="36652-115">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="36652-115">Recommended action</span></span>

<span data-ttu-id="36652-116">Değerini ayrıştırdığı mantığa sahipseniz `TargetFramework` güncelleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="36652-116">If you have logic that parses the value of `TargetFramework`, you'll need to update it.</span></span> <span data-ttu-id="36652-117">Örneğin, aşağıdaki MSBuild koşulu değerini kullanır `TargetFramework` .</span><span class="sxs-lookup"><span data-stu-id="36652-117">For example, the following MSBuild condition relies on the value of `TargetFramework`.</span></span>

```xml
<PropertyGroup Condition="$(TargetFramework.StartsWith('netcoreapp'))">
```

<span data-ttu-id="36652-118">Bu gereksinim için kodu, hedef Framework tanımlayıcısını karşılaştırmak üzere güncelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="36652-118">For this requirement, you can update the code to compare the target framework identifier instead.</span></span>

```xml
<PropertyGroup Condition="'$([MSBuild]::GetTargetFrameworkIdentifier('$(TargetFramework)'))' == '.NETCoreApp'">
```

## <a name="affected-apis"></a><span data-ttu-id="36652-119">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="36652-119">Affected APIs</span></span>

<span data-ttu-id="36652-120">YOK</span><span class="sxs-lookup"><span data-stu-id="36652-120">N/A</span></span>

<!--

### Affected APIs

Not detectable via API analysis.

### Category

MSBuild

-->
