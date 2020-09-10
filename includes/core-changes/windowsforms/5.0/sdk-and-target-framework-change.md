---
ms.openlocfilehash: 975e331ad3e7bd7e0e8f49b62795c6acc7031ca9
ms.sourcegitcommit: 1e8382d0ce8b5515864f8fbb178b9fd692a7503f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2020
ms.locfileid: "89656358"
---
### <a name="winforms-and-wpf-apps-use-microsoftnetsdk"></a>WinForms ve WPF uygulamaları Microsoft. NET. SDK kullanır

Windows Forms ve Windows Presentation Framework (WPF) uygulamaları artık `Microsoft.NET.Sdk` .NET Core WinForms ve WPF SDK () yerine .NET SDK () kullanır `Microsoft.NET.Sdk.WindowsDesktop` .

#### <a name="change-description"></a>Açıklamayı Değiştir

Önceki .NET Core sürümlerinde, WinForms ve WPF uygulamaları ayrı bir [Proje SDK 'sı](../../../../docs/core/project-sdk/overview.md) ( `Microsoft.NET.Sdk.WindowsDesktop` ) kullandı. .NET 5,0 ' den başlayarak, WinForms ve WPF SDK 'Sı .NET SDK () ile birleştirilmiştir `Microsoft.NET.Sdk` . Ayrıca, yeni [hedef çerçeve takma adları (tfd)](../../../../docs/standard/frameworks.md) , `netcoreapp` `netstandard` .NET 5 ' in yerini alır. Aşağıdaki örnekte, .NET 5,0 veya sonraki bir sürümü yeniden hedeflerken WPF proje dosyası için yapmanız gereken değişiklikler gösterilmektedir.

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

#### <a name="version-introduced"></a>Sunulan sürüm

.NET 5,0 Preview 8

#### <a name="recommended-action"></a>Önerilen eylem

WPF veya Windows Forms proje dosyasında:

- `Sdk`Özniteliğini olarak güncelleştirin `Microsoft.NET.Sdk` .
- `TargetFramework`Özelliğini olarak güncelleştirin `net5.0-windows` .

#### <a name="category"></a>Kategori

- Windows Forms
- Windows Presentation Framework (WPF)

#### <a name="affected-apis"></a>Etkilenen API’ler

API analizi aracılığıyla algılanamaz.

<!-- 

#### Affected APIs

Not detectable via API analysis.

-->
