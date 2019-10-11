---
ms.openlocfilehash: dae4afa92b8833f326b4eacd00b36bb3e1199cc1
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/09/2019
ms.locfileid: "72237478"
---
### <a name="types-in-microsoftvisualbasicdevices-namespace-not-available"></a>Microsoft. VisualBasic. Devices ad alanındaki türler kullanılamıyor

@No__t-0 ad alanındaki türler kullanılamıyor.

#### <a name="version-introduced"></a>Sunulan sürüm

.NET Core 3,0 Preview 8

#### <a name="change-description"></a>Açıklamayı Değiştir

@No__t-0 ad alanındaki türler, bazı .NET Core 3,0 önizleme sürümlerinde mevcuttur. .NET Core 3,0 Preview 9 ' dan itibaren artık kullanılabilir değildir.

Gereksiz bütünleştirilmiş kod bağımlılıklarından veya sonraki sürümlerde son değişikliklerden kaçınmak için türler kaldırılmıştır.
 
#### <a name="recommended-action"></a>Önerilen eylem

Kodunuz <xref:Microsoft.VisualBasic.Devices> türlerinin ve üyelerinin kullanımına bağımlıysa, .NET sınıf kitaplığı 'nda karşılık gelen bir türü veya üyeyi kullanabilirsiniz. Örneğin, <xref:Microsoft.VisualBasic.Devices.Clock?displayProperty=nameWithType> sınıfına denk işlevsellik <xref:System.DateTime?displayProperty=nameWithType> ve <xref:System.Environment?displayProperty=nameWithType> türleri tarafından sağlanır ve <xref:Microsoft.VisualBasic.Devices.Ports?displayProperty=nameWithType> sınıfına denk işlevsellik <xref:System.IO.Ports?displayProperty=nameWithType> ad alanındaki türler tarafından sağlanır.

#### <a name="category"></a>Kategori

Visual Basic

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.Devices`

-- >

