---
ms.openlocfilehash: 54bee14f6de409550357194e905b6ee5d8ef8f18
ms.sourcegitcommit: aa6d8a90a4f5d8fe0f6e967980b8c98433f05a44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90679011"
---
### <a name="outputtype-set-to-winexe-for-wpf-and-winforms-apps"></a>OutputType WPF ve WinForms uygulamaları için WinExe olarak ayarlandı

`OutputType``WinExe`Windows Presentation Foundation (WPF) ve Windows Forms uygulamalar için otomatik olarak ayarlanır. Ne zaman `OutputType` ayarlandığında `WinExe` , Uygulama yürütüldüğünde konsol penceresi açılmaz.

#### <a name="change-description"></a>Açıklamayı Değiştir

Önceki .NET sürümlerinde, proje dosyasında için belirtilen değer `OutputType` kullanılır. Örnek:

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

.NET 5,0 ' den itibaren, `OutputType` `WinExe` WPF ve Windows Forms uygulamaları için otomatik olarak olarak ayarlanır. Örnek:

```xml
<PropertyGroup>
  <OutputType>WinExe</OutputType>
</PropertyGroup>
```

#### <a name="reason-for-change"></a>Değişiklik nedeni

Çoğu kullanıcının bir WPF veya Windows Forms uygulaması yürütüldüğünde konsol penceresinin açılmasını istemediğiniz varsayılır. Ayrıca, [artık bu uygulama türleri](../../../../docs/core/compatibility/wpf.md#winforms-and-wpf-apps-use-microsoftnetsdk) Windows Masaüstü SDK 'sı yerıne .NET SDK 'yı kullandığına göre, doğru varsayılan değer ayarlanır. Ayrıca, iOS ve Android 'i hedeflemek için destek eklendiğinde, hepsi aynı çıkış türünü kullanıyorsa, birden çok platform arasında çoklu hedefe daha kolay olur.

#### <a name="version-introduced"></a>Sunulan sürüm

.NET 5,0 Preview 8

#### <a name="recommended-action"></a>Önerilen eylem

Sizin bölüminizdeki herhangi bir eylem gerekmiyor. Ancak, eski davranışa dönmek istiyorsanız, `DisableWinExeOutputInference` özelliği `true` proje dosyanızda olarak ayarlayın.

```xml
<DisableWinExeOutputInference>true</DisableWinExeOutputInference>
```

#### <a name="category"></a>Kategori

- Windows Forms
- Windows Presentation Framework (WPF)

#### <a name="affected-apis"></a>Etkilenen API’ler

API analizi aracılığıyla algılanamaz.

<!-- 

#### Affected APIs

Not detectable via API analysis.

-->
