---
title: 'Son değişiklik: WinForms ve WPF uygulamaları Microsoft. NET. SDK kullanır'
description: Windows Forms ve Windows Presentation Framework uygulamalarının artık .NET Core WinForms ve WPF SDK yerine .NET SDK 'yi kullanacağı .NET 5 ' teki önemli değişiklik hakkında bilgi edinin.
ms.date: 09/18/2020
ms.openlocfilehash: ebd4f51d5436cec2f0463558e99a85cb261ae682
ms.sourcegitcommit: 109507b6c16704ed041efe9598c70cd3438a9fbc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/31/2021
ms.locfileid: "106079498"
---
# <a name="winforms-and-wpf-apps-use-microsoftnetsdk"></a>WinForms ve WPF uygulamaları Microsoft. NET. SDK kullanır

Windows Forms ve Windows Presentation Framework (WPF) uygulamaları artık `Microsoft.NET.Sdk` .NET Core WinForms ve WPF SDK () yerine .NET SDK () kullanır `Microsoft.NET.Sdk.WindowsDesktop` .

## <a name="change-description"></a>Açıklamayı Değiştir

Önceki .NET Core sürümlerinde, WinForms ve WPF uygulamaları ayrı bir [Proje SDK 'sı](../../../project-sdk/overview.md) ( `Microsoft.NET.Sdk.WindowsDesktop` ) kullandı. .NET 5 ' den başlayarak, WinForms ve WPF SDK 'Sı .NET SDK () ile birleştirilmiştir `Microsoft.NET.Sdk` . Ayrıca, yeni [hedef çerçeve takma adları (tfd)](../../../../standard/frameworks.md) , `netcoreapp` `netstandard` .NET 5 ' in yerini alır. Aşağıdaki örnek, .NET 5 veya sonraki bir sürümünü yeniden hedeflerken WPF proje dosyası için yapmanız gereken değişiklikleri gösterir.

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

.NET 5 ve sonraki sürümlerde:

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

.NET SDK 5.0.100

## <a name="recommended-action"></a>Önerilen eylem

WPF veya Windows Forms proje dosyasında:

- `Sdk`Özniteliğini olarak güncelleştirin `Microsoft.NET.Sdk` .
- `TargetFramework`Özelliğini olarak güncelleştirin `net5.0-windows` .

## <a name="affected-apis"></a>Etkilenen API’ler

Yok.

<!--

### Affected APIs

Not detectable via API analysis.

### Category

- Windows Forms
- Windows Presentation Framework (WPF)

-->
