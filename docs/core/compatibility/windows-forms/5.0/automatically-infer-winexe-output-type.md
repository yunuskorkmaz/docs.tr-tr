---
title: 'Son değişiklik: WPF ve WinForms uygulamaları için OutputType, WinExe olarak ayarlanmıştır'
description: Windows Forms uygulamalar için OutputType 'nin otomatik olarak WinExe olarak ayarlandığı .NET SDK 5.0.100 'deki Son değişiklik hakkında bilgi edinin.
ms.date: 09/18/2020
ms.openlocfilehash: 38d9b910374f9e44f7e35296808930c6a6d45f0d
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100431470"
---
# <a name="outputtype-set-to-winexe-for-wpf-and-winforms-apps"></a>OutputType WPF ve WinForms uygulamaları için WinExe olarak ayarlandı

`OutputType``WinExe`Windows Presentation Foundation (WPF) ve Windows Forms uygulamalar için otomatik olarak ayarlanır. Ne zaman `OutputType` ayarlandığında `WinExe` , Uygulama yürütüldüğünde konsol penceresi açılmaz.

## <a name="change-description"></a>Açıklamayı Değiştir

.NET SDK 'sının önceki sürümlerinde, proje dosyasında için belirtilen değer `OutputType` kullanılır. Örneğin:

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

.NET SDK 'nın 5.0.100 sürümünden itibaren, olarak `OutputType` ayarlandığında `Exe` ,, `WinExe` .NET Framework dahil olmak üzere tüm Framework sürümlerini hedefleyen WPF ve Windows Forms uygulamalar için otomatik olarak olarak değiştirilir.

```xml
<PropertyGroup>
  <OutputType>WinExe</OutputType>
</PropertyGroup>
```

 `OutputType`Proje dosyasında belirtilmemişse, varsayılan olarak `Library` Bu değer değişmez.

## <a name="reason-for-change"></a>Değişiklik nedeni

Çoğu kullanıcının bir WPF veya Windows Forms uygulaması yürütüldüğünde konsol penceresinin açılmasını istemediğiniz varsayılır. Ayrıca, [artık bu uygulama türleri](sdk-and-target-framework-change.md) Windows Masaüstü SDK 'sı yerıne .NET SDK 'yı kullandığına göre, doğru varsayılan değer ayarlanır. Ayrıca, iOS ve Android 'i hedeflemek için destek eklendiğinde, hepsi aynı çıkış türünü kullanıyorsa, birden çok platform arasında çoklu hedefe daha kolay olur.

## <a name="version-introduced"></a>Sunulan sürüm

.NET 5.0.100

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
