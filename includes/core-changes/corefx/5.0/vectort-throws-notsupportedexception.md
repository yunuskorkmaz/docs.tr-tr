---
ms.openlocfilehash: 43ebb37124b8efe077b9f81fe5351bd7db2c72f7
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302730"
---
### <a name="vectort-always-throws-notsupportedexception-for-unsupported-types"></a>Vektör, \<T> Desteklenmeyen türler için her zaman NotSupportedException oluşturur

<xref:System.Numerics.Vector%601?displayProperty=nameWithType>Artık, <xref:System.NotSupportedException> desteklenmeyen tür parametreleri için her zaman bir oluşturur.

#### <a name="change-description"></a>Açıklamayı Değiştir

Daha önce, üyeleri <xref:System.Numerics.Vector%601> <xref:System.NotSupportedException> Desteklenmeyen bir tür olduğunda her zaman bir oluşturmaz `T` . [unsupported type](#unsupported-types) Donanım hızlandırmasının desteklediği kod yolları nedeniyle özel durum her zaman oluşturulmaz. Örneğin, `Vector<bool> + Vector<bool>` ARM32 gibi `default` donanım hızlandırmayan platformlarda bir özel durum oluşturmak yerine döndürüldü. Desteklenmeyen türler için, <xref:System.Numerics.Vector%601> Üyeler farklı platformlarda ve donanım yapılandırmalarında tutarsız davranışlar sergilen.

.NET 5,0 ' den başlayarak, <xref:System.Numerics.Vector%601> Üyeler <xref:System.NotSupportedException> `T` desteklenen bir tür olmadığında her zaman tüm donanım yapılandırmalarında bir oluşturur.

##### <a name="unsupported-types"></a>Desteklenmeyen türler

Tür parametresi için desteklenen türler <xref:System.Numerics.Vector%601> şunlardır:

- `byte`
- `sbyte`
- `short`
- `ushort`
- `int`
- `uint`
- `long`
- `ulong`
- `float`
- `double`

Desteklenen türler değişmemiştir, ancak gelecekte değişebilir.

#### <a name="version-introduced"></a>Sunulan sürüm

5,0 Preview 8

#### <a name="recommended-action"></a>Önerilen eylem

Tür parametresi için desteklenmeyen bir tür kullanmayın <xref:System.Numerics.Vector%601> .

#### <a name="category"></a>Kategori

Core .NET kitaplıkları

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Numerics.Vector%601?displayProperty=fullName>ve tüm üyelerini

<!--

#### Affected APIs

- ``T:System.Numerics.Vector`1``

-->
