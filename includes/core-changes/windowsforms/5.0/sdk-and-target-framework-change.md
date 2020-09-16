---
ms.openlocfilehash: 975e331ad3e7bd7e0e8f49b62795c6acc7031ca9
ms.sourcegitcommit: 1e8382d0ce8b5515864f8fbb178b9fd692a7503f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2020
ms.locfileid: "89656358"
---
### <a name="winforms-and-wpf-apps-use-microsoftnetsdk"></a><span data-ttu-id="a9fb7-101">WinForms ve WPF uygulamaları Microsoft. NET. SDK kullanır</span><span class="sxs-lookup"><span data-stu-id="a9fb7-101">WinForms and WPF apps use Microsoft.NET.Sdk</span></span>

<span data-ttu-id="a9fb7-102">Windows Forms ve Windows Presentation Framework (WPF) uygulamaları artık `Microsoft.NET.Sdk` .NET Core WinForms ve WPF SDK () yerine .NET SDK () kullanır `Microsoft.NET.Sdk.WindowsDesktop` .</span><span class="sxs-lookup"><span data-stu-id="a9fb7-102">Windows Forms and Windows Presentation Framework (WPF) apps now use the .NET SDK (`Microsoft.NET.Sdk`) instead of the .NET Core WinForms and WPF SDK (`Microsoft.NET.Sdk.WindowsDesktop`).</span></span>

#### <a name="change-description"></a><span data-ttu-id="a9fb7-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="a9fb7-103">Change description</span></span>

<span data-ttu-id="a9fb7-104">Önceki .NET Core sürümlerinde, WinForms ve WPF uygulamaları ayrı bir [Proje SDK 'sı](../../../../docs/core/project-sdk/overview.md) ( `Microsoft.NET.Sdk.WindowsDesktop` ) kullandı.</span><span class="sxs-lookup"><span data-stu-id="a9fb7-104">In previous .NET Core versions, WinForms and WPF apps used a separate [project SDK](../../../../docs/core/project-sdk/overview.md) (`Microsoft.NET.Sdk.WindowsDesktop`).</span></span> <span data-ttu-id="a9fb7-105">.NET 5,0 ' den başlayarak, WinForms ve WPF SDK 'Sı .NET SDK () ile birleştirilmiştir `Microsoft.NET.Sdk` .</span><span class="sxs-lookup"><span data-stu-id="a9fb7-105">Starting in .NET 5.0, the WinForms and WPF SDK has been unified with the .NET SDK (`Microsoft.NET.Sdk`).</span></span> <span data-ttu-id="a9fb7-106">Ayrıca, yeni [hedef çerçeve takma adları (tfd)](../../../../docs/standard/frameworks.md) , `netcoreapp` `netstandard` .NET 5 ' in yerini alır.</span><span class="sxs-lookup"><span data-stu-id="a9fb7-106">In addition, new [target framework monikers (TFM)](../../../../docs/standard/frameworks.md) replace `netcoreapp` and `netstandard` in .NET 5.</span></span> <span data-ttu-id="a9fb7-107">Aşağıdaki örnekte, .NET 5,0 veya sonraki bir sürümü yeniden hedeflerken WPF proje dosyası için yapmanız gereken değişiklikler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a9fb7-107">The following example shows the changes you'd need to make for a WPF project file when retargeting to .NET 5.0 or later.</span></span>

<span data-ttu-id="a9fb7-108">Önceki .NET Core sürümlerinde:</span><span class="sxs-lookup"><span data-stu-id="a9fb7-108">In previous .NET Core versions:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.1</TargetFramework>
    <UseWPF>true</UseWPF>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="a9fb7-109">.NET 5,0 ve sonraki sürümlerde:</span><span class="sxs-lookup"><span data-stu-id="a9fb7-109">In .NET 5.0 and later versions:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>net5.0-windows</TargetFramework>
    <UseWPF>true</UseWPF>
  </PropertyGroup>

</Project>
```

#### <a name="version-introduced"></a><span data-ttu-id="a9fb7-110">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="a9fb7-110">Version introduced</span></span>

<span data-ttu-id="a9fb7-111">.NET 5,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="a9fb7-111">.NET 5.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a9fb7-112">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="a9fb7-112">Recommended action</span></span>

<span data-ttu-id="a9fb7-113">WPF veya Windows Forms proje dosyasında:</span><span class="sxs-lookup"><span data-stu-id="a9fb7-113">In your WPF or Windows Forms project file:</span></span>

- <span data-ttu-id="a9fb7-114">`Sdk`Özniteliğini olarak güncelleştirin `Microsoft.NET.Sdk` .</span><span class="sxs-lookup"><span data-stu-id="a9fb7-114">Update the `Sdk` attribute  to `Microsoft.NET.Sdk`.</span></span>
- <span data-ttu-id="a9fb7-115">`TargetFramework`Özelliğini olarak güncelleştirin `net5.0-windows` .</span><span class="sxs-lookup"><span data-stu-id="a9fb7-115">Update the `TargetFramework` property to `net5.0-windows`.</span></span>

#### <a name="category"></a><span data-ttu-id="a9fb7-116">Kategori</span><span class="sxs-lookup"><span data-stu-id="a9fb7-116">Category</span></span>

- <span data-ttu-id="a9fb7-117">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a9fb7-117">Windows Forms</span></span>
- <span data-ttu-id="a9fb7-118">Windows Presentation Framework (WPF)</span><span class="sxs-lookup"><span data-stu-id="a9fb7-118">Windows Presentation Framework (WPF)</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a9fb7-119">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="a9fb7-119">Affected APIs</span></span>

<span data-ttu-id="a9fb7-120">API analizi aracılığıyla algılanamaz.</span><span class="sxs-lookup"><span data-stu-id="a9fb7-120">Not detectable via API analysis.</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis.

-->
