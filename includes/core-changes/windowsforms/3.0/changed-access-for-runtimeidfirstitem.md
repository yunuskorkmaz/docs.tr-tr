---
ms.openlocfilehash: 1ea2d70a7cfe04cc4c4b9b58ea6bb6fa0226b245
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721172"
---
### <a name="change-of-access-for-accessibleobjectruntimeidfirstitem"></a>Erişilebilir nesne. Runtimeıdfirtıtem için erişim değişikliği

.NET Core 3,0 RC1 'den başlayarak, uygulamasının erişilebilirliği `AccessibleObject.RuntimeIDFirstItem` `protected` olarak değiştirilmiştir `internal` .

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Core 3,0 Preview 4 ' ü kullanmaya başlama `AccessibleObject.RuntimeIDFirstItem` alanı `protected` . .NET Core 3,0 RC1 'den başlayarak, `protected` `internal` .NET Framework alanın erişilebilirliği ile hizalanacak şekilde değiştirilir.

#### <a name="version-introduced"></a>Sunulan sürüm

3,0 RC1

#### <a name="recommended-action"></a>Önerilen eylem

' Dan türetilmiş <xref:System.Windows.Forms.AccessibleObject> ve alanla erişilen bir tür ile .NET Core uygulaması geliştirdiyseniz değişiklik sizi etkileyebilir `RuntimeIDFirstItem` . Bu durumda, yerel bir sabiti şu şekilde tanımlayabilirsiniz:

```csharp
const int RuntimeIDFirstItem = 0x2a;
```

#### <a name="category"></a>Kategori

Windows Forms

#### <a name="affected-apis"></a>Etkilenen API’ler

- API analizi aracılığıyla algılanamaz.

<!-- 

#### Affected APIs

- Not detectable via API analysis.

-->
