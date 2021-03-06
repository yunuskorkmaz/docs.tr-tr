---
title: 'Son değişiklik: Windows dışı platformlarda bir/W soneki yoklama yok'
description: Windows dışı platformlarda P/Invoke için yoklama sırasında son eklerin artık işlev dışa aktarma adlarına eklenmemiş olduğunu .NET 5 ' teki birlikte çalışma son değişikliği hakkında bilgi edinin.
ms.date: 08/13/2020
ms.openlocfilehash: 924cbcb6c432e2f7c52c7218d48a938b61306c9c
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256627"
---
# <a name="no-aw-suffix-probing-on-non-windows-platforms"></a>Windows olmayan platformlarda A/W sonek yoklaması yok

.NET çalışma zamanları artık `A` `W` Windows dışı platformlarda P/Invoke için yoklama sırasında dışarı aktarma adlarını işlevine bir veya sonek eklemez.

## <a name="version-introduced"></a>Sunulan sürüm

5.0

## <a name="change-description"></a>Açıklamayı Değiştir

[Windows](/windows/win32/intl/conventions-for-function-prototypes) , `A` `W` sırasıyla Windows kod sayfasına ve Unicode sürümlerine karşılık gelen Windows SDK işlev adlarına bir veya son ek ekleme kuralına sahiptir.

Önceki .NET sürümlerinde CoreCLR ve mono çalışma zamanları, `A` `W` *tüm platformlarda* P/Invoke için dışarı aktarma keşfi sırasında dışarı aktarma adına bir veya son ek ekler.

.NET 5 ve sonraki sürümlerinde, `A` `W` *yalnızca Windows üzerinde* dışarı aktarma sırasında dışarı aktarma adına bir veya soneki eklenir. UNIX platformlarında, sonek eklenmez. Windows platformunda her iki çalışma alanının semantiği değişmeden kalır.

## <a name="reason-for-change"></a>Değişiklik nedeni

Platformlar arası yoklama basitleştirecek bu değişiklik yapılmıştır. Windows dışı platformların Bu anlam içermediğini göz önüne alındığında, bu, tahakkuk etmemelidir.

## <a name="recommended-action"></a>Önerilen eylem

Değişikliği azaltmak için, istenen soneki Windows olmayan platformlarda el ile ekleyebilirsiniz. Örnek:

```csharp
[DllImport(...)]
extern static void SetWindowTextW();
```

## <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>

<!--

### Affected APIs

- `T:System.Runtime.InteropServices.DllImportAttribute`

### Category

Interop

-->
