---
ms.openlocfilehash: 5bbbf9075683b0f124e126b661b4ab85011e6c2e
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002999"
---
### <a name="change-of-access-for-accessibleobjectruntimeidfirstitem"></a>Erişilebilir nesne. Runtimeıdfirtıtem için erişim değişikliği

.NET Core 3,0 RC1 'den başlayarak, `AccessibleObject.RuntimeIDFirstItem` ' ı ' nin erişilebilirliği `protected` ' den `internal` ' ye değişti.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Core 3,0 Preview 4 ' te başlayarak `AccessibleObject.RuntimeIDFirstItem` alanı `protected` idi. .NET Core 3,0 RC1 ile başlayarak, .NET Framework alanın erişilebilirliği ile hizalamak için `protected` ' dan `internal` ' e değişmiştir.

#### <a name="version-introduced"></a>Sunulan sürüm

3,0 RC1

#### <a name="recommended-action"></a>Önerilen eylem

@No__t-0 ' dan türetilen ve `RuntimeIDFirstItem` alanına erişen bir türde .NET Core uygulaması geliştirdiyseniz değişiklik sizi etkileyebilir. Bu durumda, yerel bir sabiti şu şekilde tanımlayabilirsiniz:

```csharp
const int RuntimeIDFirstItem = 0x2a;
```

#### <a name="category"></a>Kategori

Windows Forms

#### <a name="affected-apis"></a>Etkilenen API’ler

- API analizi aracılığıyla algılanamaz.

<!-- 

### Affected APIs

- Not detectable via API analysis.

-->
