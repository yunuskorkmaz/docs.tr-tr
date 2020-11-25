---
title: 'Son değişiklik: WinForms ve WPF uygulamaları Microsoft. NET. SDK kullanır'
description: Windows Forms ve Windows Presentation Framework uygulamalarının artık .NET Core WinForms ve WPF SDK yerine .NET SDK 'yi kullanacağı .NET 5,0 'deki önemli değişiklik hakkında bilgi edinin.
ms.date: 09/18/2020
ms.openlocfilehash: 5f25be44c390abc173f155351d8cb007a6b370b0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761585"
---
# <a name="winforms-and-wpf-apps-use-microsoftnetsdk"></a>WinForms ve WPF uygulamaları Microsoft. NET. SDK kullanır

Windows Forms ve Windows Presentation Framework (WPF) uygulamaları artık `Microsoft.NET.Sdk` .NET Core WinForms ve WPF SDK () yerine .NET SDK () kullanır `Microsoft.NET.Sdk.WindowsDesktop` .

## <a name="change-description"></a>Açıklamayı Değiştir

Önceki .NET Core sürümlerinde, WinForms ve WPF uygulamaları ayrı bir [Proje SDK 'sı](../../../project-sdk/overview.md) ( `Microsoft.NET.Sdk.WindowsDesktop` ) kullandı. .NET 5,0 ' den başlayarak, WinForms ve WPF SDK 'Sı .NET SDK () ile birleştirilmiştir `Microsoft.NET.Sdk` . Ayrıca, yeni [hedef çerçeve takma adları (tfd)](../../../../standard/frameworks.md) , `netcoreapp` `netstandard` .NET 5 ' in yerini alır. Aşağıdaki örnekte, .NET 5,0 veya sonraki bir sürümü yeniden hedeflerken WPF proje dosyası için yapmanız gereken değişiklikler gösterilmektedir.

Önceki .NET Core sürümlerinde:

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.1</TargetFramework>
    <UseWPF>true</UseWPF>
  </PropertyGroup>

</Project>
```

.NET 5,0 ve sonraki sürümlerde:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>net5.0-windows</TargetFramework>
    <UseWPF>true</UseWPF>
  </PropertyGroup>

</Project>
```

## <a name="version-introduced"></a>Sunulan sürüm

.NET 5,0

## <a name="recommended-action"></a>Önerilen eylem

WPF veya Windows Forms proje dosyasında:

- `Sdk`Özniteliğini olarak güncelleştirin `Microsoft.NET.Sdk` .
- `TargetFramework`Özelliğini olarak güncelleştirin `net5.0-windows` .

## <a name="affected-apis"></a>Etkilenen API’ler

API analizi aracılığıyla algılanamaz.

<!--

### Affected APIs

Not detectable via API analysis.

### Category

- Windows Forms
- Windows Presentation Framework (WPF)

-->
