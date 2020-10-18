---
ms.openlocfilehash: 1ddc2cea19872b44ff9659bcebd76117587ea89a
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92159501"
---
### <a name="targetframework-change-from-netcoreapp-to-net"></a><span data-ttu-id="c9fb9-101">TargetFramework, netcoreapp 'ten net 'e değişiklik</span><span class="sxs-lookup"><span data-stu-id="c9fb9-101">TargetFramework change from netcoreapp to net</span></span>

<span data-ttu-id="c9fb9-102">MSBuild `TargetFramework` özelliğinin değeri iken `netcoreapp3.1` olarak değiştirildi `net5.0` .</span><span class="sxs-lookup"><span data-stu-id="c9fb9-102">The value for the MSBuild `TargetFramework` property changed from `netcoreapp3.1` to `net5.0`.</span></span> <span data-ttu-id="c9fb9-103">Bu, değerini ayrıştırmaya dayalı kodu kesebilir `TargetFramework` .</span><span class="sxs-lookup"><span data-stu-id="c9fb9-103">This can break code that relies on parsing the value of `TargetFramework`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="c9fb9-104">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="c9fb9-104">Version introduced</span></span>

<span data-ttu-id="c9fb9-105">5.0</span><span class="sxs-lookup"><span data-stu-id="c9fb9-105">5.0</span></span>

#### <a name="change-description"></a><span data-ttu-id="c9fb9-106">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="c9fb9-106">Change description</span></span>

<span data-ttu-id="c9fb9-107">.NET Core 1,0-3,1 ' de, MSBuild `TargetFramework` özelliğinin değeri `netcoreapp` , örneğin `netcoreapp3.1` .NET Core 3,1 ' i hedefleyen uygulamalar için ile başlar.</span><span class="sxs-lookup"><span data-stu-id="c9fb9-107">In .NET Core 1.0 - 3.1, the value for the MSBuild `TargetFramework` property starts with `netcoreapp`, for example, `netcoreapp3.1` for apps that target .NET Core 3.1.</span></span> <span data-ttu-id="c9fb9-108">.NET 5,0 ' den başlayarak, bu değer .NET 5,0 için yalnızca ile başlamak üzere basitleştirilmiştir `net` `net5.0` .</span><span class="sxs-lookup"><span data-stu-id="c9fb9-108">Starting in .NET 5.0, this value is simplified to just start with `net`, for example, `net5.0` for .NET 5.0.</span></span>

<span data-ttu-id="c9fb9-109">Daha fazla bilgi için, [The future of .NET Standard](https://devblogs.microsoft.com/dotnet/the-future-of-net-standard/) [.NET 5 ' te .NET Standard ve hedef çerçeve adları](https://github.com/dotnet/designs/blob/main/accepted/2020/net5/net5.md)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="c9fb9-109">For more information, see [The future of .NET Standard](https://devblogs.microsoft.com/dotnet/the-future-of-net-standard/) and [Target framework names in .NET 5](https://github.com/dotnet/designs/blob/main/accepted/2020/net5/net5.md).</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="c9fb9-110">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="c9fb9-110">Reason for change</span></span>

- <span data-ttu-id="c9fb9-111">Değeri basitleştirir `TargetFramework` .</span><span class="sxs-lookup"><span data-stu-id="c9fb9-111">Simplifies the `TargetFramework` value.</span></span>
- <span data-ttu-id="c9fb9-112">Projelerin özelliği içine içermesini sağlar `TargetPlatform` `TargetFramework` .</span><span class="sxs-lookup"><span data-stu-id="c9fb9-112">Enables projects to include a `TargetPlatform` in the `TargetFramework` property.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="c9fb9-113">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="c9fb9-113">Recommended action</span></span>

<span data-ttu-id="c9fb9-114">Değerini ayrıştırdığı mantığa sahipseniz `TargetFramework` güncelleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="c9fb9-114">If you have logic that parses the value of `TargetFramework`, you'll need to update it.</span></span> <span data-ttu-id="c9fb9-115">Örneğin, aşağıdaki MSBuild koşulu değerini kullanır `TargetFramework` .</span><span class="sxs-lookup"><span data-stu-id="c9fb9-115">For example, the following MSBuild condition relies on the value of `TargetFramework`.</span></span>

```xml
<PropertyGroup Condition="$(TargetFramework.StartsWith('netcoreapp'))">
```

<span data-ttu-id="c9fb9-116">Bu gereksinim için kodu, hedef Framework tanımlayıcısını karşılaştırmak üzere güncelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c9fb9-116">For this requirement, you can update the code to compare the target framework identifier instead.</span></span>

```xml
<PropertyGroup Condition="'$([MSBuild]::GetTargetFrameworkIdentifier('$(TargetFramework)'))' == '.NETCoreApp'">
```

#### <a name="category"></a><span data-ttu-id="c9fb9-117">Kategori</span><span class="sxs-lookup"><span data-stu-id="c9fb9-117">Category</span></span>

<span data-ttu-id="c9fb9-118">MSBuild</span><span class="sxs-lookup"><span data-stu-id="c9fb9-118">MSBuild</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c9fb9-119">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="c9fb9-119">Affected APIs</span></span>

<span data-ttu-id="c9fb9-120">YOK</span><span class="sxs-lookup"><span data-stu-id="c9fb9-120">N/A</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
