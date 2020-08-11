---
ms.openlocfilehash: e128bdb5735b3e4844356ad4807cc092f6f2b105
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/11/2020
ms.locfileid: "88062437"
---
### <a name="no-aw-suffix-probing-on-non-windows-platforms"></a>Windows dışı platformlarda bir/W soneki yoklama yok

.NET çalışma zamanları artık `A` `W` Windows dışı platformlarda P/Invoke için yoklama sırasında dışarı aktarma adlarını işlevine bir veya sonek eklemez.

#### <a name="version-introduced"></a>Sunulan sürüm

5,0 Preview 4

#### <a name="change-description"></a>Açıklamayı Değiştir

[Windows](/windows/win32/intl/conventions-for-function-prototypes) , `A` `W` sırasıyla Windows kod sayfasına ve Unicode sürümlerine karşılık gelen Windows SDK işlev adlarına bir veya son ek ekleme kuralına sahiptir.

Önceki .NET sürümlerinde CoreCLR ve mono çalışma zamanları, `A` `W` *tüm platformlarda*P/Invoke için dışarı aktarma keşfi sırasında dışarı aktarma adına bir veya son ek ekler.

.NET 5,0 ve sonraki sürümlerinde, `A` `W` *yalnızca Windows üzerinde*dışarı aktarma sırasında dışarı aktarma adına bir veya soneki eklenir. UNIX platformlarında, sonek eklenmez. Windows platformunda her iki çalışma alanının semantiği değişmeden kalır.

#### <a name="reason-for-change"></a>Değişiklik nedeni

Platformlar arası yoklama basitleştirecek bu değişiklik yapılmıştır. Windows dışı platformların Bu anlam içermediğini göz önüne alındığında, bu, tahakkuk etmemelidir.

#### <a name="recommended-action"></a>Önerilen eylem

Değişikliği azaltmak için, istenen soneki Windows olmayan platformlarda el ile ekleyebilirsiniz. Örnek:

```csharp
[DllImport(...)]
extern static void SetWindowTextW();
```

#### <a name="category"></a>Kategori

Interop

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Runtime.InteropServices.DllImportAttribute`

-->
