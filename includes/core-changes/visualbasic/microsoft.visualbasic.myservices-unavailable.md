---
ms.openlocfilehash: 75ba041a93b71377928591967e1554742e1d17e1
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/09/2019
ms.locfileid: "72237481"
---
### <a name="types-in-microsoftvisualbasicmyservices-namespace-not-available"></a>Microsoft. VisualBasic. MyServices ad alanındaki türler kullanılamıyor

@No__t-0 ad alanındaki türler kullanılamıyor.

#### <a name="version-introduced"></a>Sunulan sürüm

.NET Core 3,0 Preview 8

#### <a name="change-description"></a>Açıklamayı Değiştir

@No__t-0 ad alanındaki türler, bazı .NET Core 3,0 önizleme sürümlerinde mevcuttur. .NET Core 3,0 Preview 9 ' dan itibaren artık kullanılabilir değildir.

Gereksiz bütünleştirilmiş kod bağımlılıklarından veya sonraki sürümlerde son değişikliklerden kaçınmak için türler kaldırılmıştır.
 
#### <a name="recommended-action"></a>Önerilen eylem

Kodunuz **Microsoft. VisualBasic. MyServices** türlerinin ve üyelerinin kullanımına bağımlıysa, .NET sınıf kitaplığı 'nda karşılık gelen türler ve Üyeler vardır. Aşağıda, **Microsoft. VisualBasic. MyServices** türlerinin eşdeğer .NET sınıf kitaplığı türlerine eşlenmesi verilmiştir:

|Microsoft. VisualBasic. MyServices türü|.NET sınıf kitaplığı türü|
|--|--|
|<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>|<xref:System.Windows.Clipboard?displayProperty=nameWithType> WPF uygulamaları için <xref:System.Windows.Forms.Clipboard?displayProperty=nameWithType> Windows Forms uygulamalar için| 
|<xref:Microsoft.VisualBasic.MyServices.FileSystemProxy>|@No__t-0 ad alanındaki türler|
|<xref:Microsoft.VisualBasic.MyServices.RegistryProxy>|@No__t-0 ad alanındaki kayıt defteriyle ilgili türler|
|<xref:Microsoft.VisualBasic.MyServices.SpecialDirectoriesProxy>|<xref:System.Environment.GetFolderPath%2A?displayProperty=nameWithType>|

#### <a name="category"></a>Kategori

Visual Basic

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.MyServices`

-- >

