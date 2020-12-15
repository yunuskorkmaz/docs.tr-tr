---
title: 'Son değişiklik: WPF ve WinForms uygulamaları için OutputType, WinExe olarak ayarlanmıştır'
description: OutputType Windows Forms uygulamalar için otomatik olarak WinExe olarak ayarlandığı .NET 5,0 ' deki Son değişiklik hakkında bilgi edinin.
ms.date: 09/18/2020
ms.openlocfilehash: 7b2c7a76983c9e7958808e3cc4716be7792841c6
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97513191"
---
# <a name="outputtype-set-to-winexe-for-wpf-and-winforms-apps"></a>OutputType WPF ve WinForms uygulamaları için WinExe olarak ayarlandı

`OutputType``WinExe`Windows Presentation Foundation (WPF) ve Windows Forms uygulamalar için otomatik olarak ayarlanır. Ne zaman `OutputType` ayarlandığında `WinExe` , Uygulama yürütüldüğünde konsol penceresi açılmaz.

## <a name="change-description"></a>Açıklamayı Değiştir

.NET SDK 'sının önceki sürümlerinde, proje dosyasında için belirtilen değer `OutputType` kullanılır. Örnek:

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

.NET SDK 'sının 5.0.1 sürümünden itibaren, `OutputType` `WinExe` .NET Framework dahil olmak üzere tüm Framework SÜRÜMLERINI hedefleyen WPF ve Windows Forms uygulamalar için otomatik olarak ayarlanır. Örnek:

```xml
<PropertyGroup>
  <OutputType>WinExe</OutputType>
</PropertyGroup>
```

## <a name="reason-for-change"></a>Değişiklik nedeni

Çoğu kullanıcının bir WPF veya Windows Forms uygulaması yürütüldüğünde konsol penceresinin açılmasını istemediğiniz varsayılır. Ayrıca, [artık bu uygulama türleri](sdk-and-target-framework-change.md) Windows Masaüstü SDK 'sı yerıne .NET SDK 'yı kullandığına göre, doğru varsayılan değer ayarlanır. Ayrıca, iOS ve Android 'i hedeflemek için destek eklendiğinde, hepsi aynı çıkış türünü kullanıyorsa, birden çok platform arasında çoklu hedefe daha kolay olur.

## <a name="version-introduced"></a>Sunulan sürüm

.NET 5.0.1

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
