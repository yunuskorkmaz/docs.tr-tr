---
ms.openlocfilehash: 5bbbf9075683b0f124e126b661b4ab85011e6c2e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74644049"
---
### <a name="change-of-access-for-accessibleobjectruntimeidfirstitem"></a>ErişilebilirObject.RuntimeIDFirstItem için erişim değişikliği

.NET Core 3.0 RC1'den `AccessibleObject.RuntimeIDFirstItem` `protected` başlayarak erişilebilirlik `internal`.

#### <a name="change-description"></a>Açıklamayı değiştir

.NET Core 3.0 Preview 4 `AccessibleObject.RuntimeIDFirstItem` ile `protected`başlayarak, alan . .NET Core 3.0 RC1 ile başlayarak, .NET Framework'deki alanın erişilebilirliğiyle hizaya `protected` kadar `internal` değişti.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

3.0 RC1

#### <a name="recommended-action"></a>Önerilen eylem

Bu değişiklik, <xref:System.Windows.Forms.AccessibleObject> `RuntimeIDFirstItem` alandan türemiş ve alana erişen bir türe sahip bir .NET Core uygulaması geliştirdiyseniz sizi etkileyebilir. Bu durumda, yerel bir sabiti aşağıdaki gibi tanımlayabilirsiniz:

```csharp
const int RuntimeIDFirstItem = 0x2a;
```

#### <a name="category"></a>Kategori

Windows Forms

#### <a name="affected-apis"></a>Etkilenen API’ler

- API analizi ile tespit edilemez.

<!-- 

### Affected APIs

- Not detectable via API analysis.

-->
