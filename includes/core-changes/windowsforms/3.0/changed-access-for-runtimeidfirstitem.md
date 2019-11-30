---
ms.openlocfilehash: 5bbbf9075683b0f124e126b661b4ab85011e6c2e
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74644049"
---
### <a name="change-of-access-for-accessibleobjectruntimeidfirstitem"></a>Erişilebilir nesne. Runtimeıdfirtıtem için erişim değişikliği

.NET Core 3,0 RC1 'den başlayarak `AccessibleObject.RuntimeIDFirstItem` erişilebilirliği `protected` `internal`olarak değiştirilmiştir.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Core 3,0 Preview 4 ' te başlayarak `AccessibleObject.RuntimeIDFirstItem` alanı `protected`. .NET Core 3,0 RC1 ile başlayarak, .NET Framework alanın erişilebilirliği ile hizalamak için `protected` `internal` olarak değiştirilmiştir.

#### <a name="version-introduced"></a>Sunulan sürüm

3,0 RC1

#### <a name="recommended-action"></a>Önerilen eylem

<xref:System.Windows.Forms.AccessibleObject> bir .NET Core uygulamasını geliştirdiyseniz ve `RuntimeIDFirstItem` alanına eriştiğinde bu değişiklik sizi etkileyebilir. Bu durumda, yerel bir sabiti şu şekilde tanımlayabilirsiniz:

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
