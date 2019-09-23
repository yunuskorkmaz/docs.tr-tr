---
ms.openlocfilehash: ba543414d4f84362c9b9b876395815e837efbd3f
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181721"
---
### <a name="types-in-microsoftvisualbasicmyservices-namespace-not-available"></a>Microsoft. VisualBasic. MyServices ad alanındaki türler kullanılamıyor

<xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> Ad alanındaki türler kullanılamıyor.

#### <a name="version-introduced"></a>Sunulan sürüm

.NET Core 3,0 Preview 8

#### <a name="details"></a>Ayrıntılar

<xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> Ad alanındaki türler, bazı .NET Core 3,0 önizleme sürümlerinde mevcuttur. .NET Core 3,0 Preview 9 ' dan itibaren artık kullanılabilir değildir.

Gereksiz bütünleştirilmiş kod bağımlılıklarından veya sonraki sürümlerde son değişikliklerden kaçınmak için türler kaldırılmıştır.
 
#### <a name="recommended-action"></a>Önerilen eylem

Kodunuz **Microsoft. VisualBasic. MyServices** türlerinin ve üyelerinin kullanımına bağımlıysa, .NET sınıf kitaplığı 'nda karşılık gelen türler ve Üyeler vardır. Aşağıda, **Microsoft. VisualBasic. MyServices** türlerinin eşdeğer .NET sınıf kitaplığı türlerine eşlenmesi verilmiştir:

|Microsoft. VisualBasic. MyServices türü|.NET sınıf kitaplığı türü|
|--|--|
|<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>|<xref:System.Windows.Clipboard?displayProperty=nameWithType>WPF uygulamaları <xref:System.Windows.Forms.Clipboard?displayProperty=nameWithType> için Windows Forms uygulamalar için| 
|<xref:Microsoft.VisualBasic.MyServices.FileSystemProxy>|<xref:System.IO> Ad alanındaki türler|
|<xref:Microsoft.VisualBasic.MyServices.RegistryProxy>|<xref:Microsoft.Win32> Ad alanındaki kayıt defteri ile ilgili türler|
|<xref:Microsoft.VisualBasic.MyServices.SpecialDirectoriesProxy>|<xref:System.Environment.GetFolderPath%2A?displayProperty=nameWithType>|

#### <a name="category"></a>Kategori

Visual Basic

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.MyServices`

-- >

