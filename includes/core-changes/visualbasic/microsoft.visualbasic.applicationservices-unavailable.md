---
ms.openlocfilehash: 294c077b837899bd714deb2afd1bdff2b3185f38
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/09/2019
ms.locfileid: "72237476"
---
### <a name="types-in-microsoftvisualbasicapplicationservices-namespace-not-available"></a>Microsoft. VisualBasic. ApplicationServices ad alanındaki türler kullanılamıyor

@No__t-0 ad alanındaki türler kullanılamıyor.

#### <a name="version-introduced"></a>Sunulan sürüm

.NET Core 3,0 Preview 8

#### <a name="change-description"></a>Açıklamayı Değiştir

@No__t-0 ad alanındaki türler, bazı .NET Core 3,0 önizleme sürümlerinde mevcuttur. .NET Core 3,0 Preview 9 ' dan itibaren artık kullanılabilir değildir.

Gereksiz bütünleştirilmiş kod bağımlılıklarından veya sonraki sürümlerde son değişikliklerden kaçınmak için türler kaldırılmıştır.
 
#### <a name="recommended-action"></a>Önerilen eylem

Kodunuz <xref:Microsoft.VisualBasic.ApplicationServices> türlerinin ve üyelerinin kullanımına bağımlıysa, .NET sınıf kitaplığı 'nda karşılık gelen bir türü veya üyeyi kullanabilirsiniz. Örneğin, bazı <xref:System.Environment?displayProperty=nameWithType> ve <xref:System.Security.Principal.WindowsIdentity?displayProperty=nameWithType> üyeleri, <xref:Microsoft.VisualBasic.ApplicationServices.User?displayProperty=nameWithType> sınıfının özelliklerine denk işlevsellik sağlar.

#### <a name="category"></a>Kategori

Visual Basic

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:Microsoft.VisualBasic.ApplicationServices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.ApplicationServices`

-- >

