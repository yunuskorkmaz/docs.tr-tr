---
ms.openlocfilehash: 7f528510e4158dad71280a7b1f269a231b8c60f2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76116359"
---
### <a name="types-in-microsoftvisualbasicdevices-namespace-not-available"></a>Microsoft.VisualBasic.Devices ad alanında türleri kullanılamıyor

<xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> Ad alanındaki türler kullanılamıyor.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

.NET Core 3.0 Önizleme 8

#### <a name="change-description"></a>Açıklamayı değiştir

<xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> Ad alanındaki türler bazı .NET Core 3.0 Önizleme sürümlerinde kullanılabilirdi. .NET Core 3.0 Preview 9 ile başlayarak artık kullanılamazlar.

Türler, gereksiz derleme bağımlılıklarını veya sonraki sürümlerde değişiklikleri kırmayı önlemek için kaldırıldı.

#### <a name="recommended-action"></a>Önerilen eylem

Kodunuz <xref:Microsoft.VisualBasic.Devices> türlerin ve üyelerinin kullanımına bağlıysa, .NET sınıf kitaplığında karşılık gelen bir türü veya üyeyi kullanabilirsiniz. Örneğin, <xref:Microsoft.VisualBasic.Devices.Clock?displayProperty=nameWithType> sınıfa eşdeğer işlevsellik <xref:System.DateTime?displayProperty=nameWithType> ve <xref:System.Environment?displayProperty=nameWithType> türleri tarafından sağlanır ve <xref:Microsoft.VisualBasic.Devices.Ports?displayProperty=nameWithType> sınıfa eşdeğer işlevsellik <xref:System.IO.Ports?displayProperty=nameWithType> ad alanındaki türler tarafından sağlanır.

#### <a name="category"></a>Kategori

Visual Basic

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.Devices`

-->
