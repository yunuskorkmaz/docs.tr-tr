---
title: 'Son değişiklik: WinForms ve WPF uygulamaları Microsoft. NET. SDK kullanır'
description: Windows Forms ve Windows Presentation Framework uygulamalarının artık .NET Core WinForms ve WPF SDK yerine .NET SDK 'yi kullanacağı .NET 5 ' teki önemli değişiklik hakkında bilgi edinin.
ms.date: 09/18/2020
ms.openlocfilehash: 408233f6f8801fb3d4e53beab28c26a777a4a3e1
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256211"
---
# <a name="winforms-and-wpf-apps-use-microsoftnetsdk"></a><span data-ttu-id="56587-103">WinForms ve WPF uygulamaları Microsoft. NET. SDK kullanır</span><span class="sxs-lookup"><span data-stu-id="56587-103">WinForms and WPF apps use Microsoft.NET.Sdk</span></span>

<span data-ttu-id="56587-104">Windows Forms ve Windows Presentation Framework (WPF) uygulamaları artık `Microsoft.NET.Sdk` .NET Core WinForms ve WPF SDK () yerine .NET SDK () kullanır `Microsoft.NET.Sdk.WindowsDesktop` .</span><span class="sxs-lookup"><span data-stu-id="56587-104">Windows Forms and Windows Presentation Framework (WPF) apps now use the .NET SDK (`Microsoft.NET.Sdk`) instead of the .NET Core WinForms and WPF SDK (`Microsoft.NET.Sdk.WindowsDesktop`).</span></span>

## <a name="change-description"></a><span data-ttu-id="56587-105">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="56587-105">Change description</span></span>

<span data-ttu-id="56587-106">Önceki .NET Core sürümlerinde, WinForms ve WPF uygulamaları ayrı bir [Proje SDK 'sı](../../../project-sdk/overview.md) ( `Microsoft.NET.Sdk.WindowsDesktop` ) kullandı.</span><span class="sxs-lookup"><span data-stu-id="56587-106">In previous .NET Core versions, WinForms and WPF apps used a separate [project SDK](../../../project-sdk/overview.md) (`Microsoft.NET.Sdk.WindowsDesktop`).</span></span> <span data-ttu-id="56587-107">.NET 5 ' den başlayarak, WinForms ve WPF SDK 'Sı .NET SDK () ile birleştirilmiştir `Microsoft.NET.Sdk` .</span><span class="sxs-lookup"><span data-stu-id="56587-107">Starting in .NET 5, the WinForms and WPF SDK has been unified with the .NET SDK (`Microsoft.NET.Sdk`).</span></span> <span data-ttu-id="56587-108">Ayrıca, yeni [hedef çerçeve takma adları (tfd)](../../../../standard/frameworks.md) , `netcoreapp` `netstandard` .NET 5 ' in yerini alır.</span><span class="sxs-lookup"><span data-stu-id="56587-108">In addition, new [target framework monikers (TFM)](../../../../standard/frameworks.md) replace `netcoreapp` and `netstandard` in .NET 5.</span></span> <span data-ttu-id="56587-109">Aşağıdaki örnek, .NET 5 veya sonraki bir sürümünü yeniden hedeflerken WPF proje dosyası için yapmanız gereken değişiklikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="56587-109">The following example shows the changes you'd need to make for a WPF project file when retargeting to .NET 5 or later.</span></span>

<span data-ttu-id="56587-110">Önceki .NET Core sürümlerinde:</span><span class="sxs-lookup"><span data-stu-id="56587-110">In previous .NET Core versions:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.1</TargetFramework>
    <UseWPF>true</UseWPF>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="56587-111">.NET 5 ve sonraki sürümlerde:</span><span class="sxs-lookup"><span data-stu-id="56587-111">In .NET 5 and later versions:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>net5.0-windows</TargetFramework>
    <UseWPF>true</UseWPF>
  </PropertyGroup>

</Project>
```

## <a name="version-introduced"></a><span data-ttu-id="56587-112">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="56587-112">Version introduced</span></span>

<span data-ttu-id="56587-113">.NET SDK 5.0.100</span><span class="sxs-lookup"><span data-stu-id="56587-113">.NET SDK 5.0.100</span></span>

## <a name="recommended-action"></a><span data-ttu-id="56587-114">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="56587-114">Recommended action</span></span>

<span data-ttu-id="56587-115">WPF veya Windows Forms proje dosyasında:</span><span class="sxs-lookup"><span data-stu-id="56587-115">In your WPF or Windows Forms project file:</span></span>

- <span data-ttu-id="56587-116">`Sdk`Özniteliğini olarak güncelleştirin `Microsoft.NET.Sdk` .</span><span class="sxs-lookup"><span data-stu-id="56587-116">Update the `Sdk` attribute  to `Microsoft.NET.Sdk`.</span></span>
- <span data-ttu-id="56587-117">`TargetFramework`Özelliğini olarak güncelleştirin `net5.0-windows` .</span><span class="sxs-lookup"><span data-stu-id="56587-117">Update the `TargetFramework` property to `net5.0-windows`.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="56587-118">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="56587-118">Affected APIs</span></span>

<span data-ttu-id="56587-119">API analizi aracılığıyla algılanamaz.</span><span class="sxs-lookup"><span data-stu-id="56587-119">Not detectable via API analysis.</span></span>

<!--

### Affected APIs

Not detectable via API analysis.

### Category

- Windows Forms
- Windows Presentation Framework (WPF)

-->
