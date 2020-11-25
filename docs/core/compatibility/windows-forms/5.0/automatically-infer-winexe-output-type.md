---
title: 'Son değişiklik: WPF ve WinForms uygulamaları için OutputType, WinExe olarak ayarlanmıştır'
description: OutputType Windows Forms uygulamalar için otomatik olarak WinExe olarak ayarlandığı .NET 5,0 ' deki Son değişiklik hakkında bilgi edinin.
ms.date: 09/18/2020
ms.openlocfilehash: 072c5b11c8304eb540e176ce9747930789f28505
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761685"
---
# <a name="outputtype-set-to-winexe-for-wpf-and-winforms-apps"></a>OutputType WPF ve WinForms uygulamaları için WinExe olarak ayarlandı

`OutputType``WinExe`Windows Presentation Foundation (WPF) ve Windows Forms uygulamalar için otomatik olarak ayarlanır. Ne zaman `OutputType` ayarlandığında `WinExe` , Uygulama yürütüldüğünde konsol penceresi açılmaz.

## <a name="change-description"></a>Açıklamayı Değiştir

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

## <a name="reason-for-change"></a>Değişiklik nedeni

Çoğu kullanıcının bir WPF veya Windows Forms uygulaması yürütüldüğünde konsol penceresinin açılmasını istemediğiniz varsayılır. Ayrıca, [artık bu uygulama türleri](sdk-and-target-framework-change.md) Windows Masaüstü SDK 'sı yerıne .NET SDK 'yı kullandığına göre, doğru varsayılan değer ayarlanır. Ayrıca, iOS ve Android 'i hedeflemek için destek eklendiğinde, hepsi aynı çıkış türünü kullanıyorsa, birden çok platform arasında çoklu hedefe daha kolay olur.

## <a name="version-introduced"></a>Sunulan sürüm

.NET 5,0

## <a name="recommended-action"></a>Önerilen eylem

Sizin bölüminizdeki herhangi bir eylem gerekmiyor. Ancak, eski davranışa dönmek istiyorsanız, `DisableWinExeOutputInference` özelliği `true` proje dosyanızda olarak ayarlayın.

```xml
<DisableWinExeOutputInference>true</DisableWinExeOutputInference>
```

## <a name="affected-apis"></a>Etkilenen API’ler

API analizi aracılığıyla algılanamaz.

<!--

### Affected APIs

Not detectable via API analysis.

### Category

- Windows Forms
- Windows Presentation Framework (WPF)

-->
