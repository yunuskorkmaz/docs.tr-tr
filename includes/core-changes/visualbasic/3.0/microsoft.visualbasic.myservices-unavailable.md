---
ms.openlocfilehash: 58e65bae1593f23945a971b896a1db4a929b4587
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74567466"
---
### <a name="types-in-microsoftvisualbasicmyservices-namespace-not-available"></a>Microsoft. VisualBasic. MyServices ad alanındaki türler kullanılamıyor

<xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> ad alanındaki türler kullanılamıyor.

#### <a name="version-introduced"></a>Sunulan sürüm

.NET Core 3,0 Preview 8

#### <a name="change-description"></a>Açıklamayı Değiştir

<xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> ad alanındaki türler bazı .NET Core 3,0 önizleme sürümlerinde mevcuttur. .NET Core 3,0 Preview 9 ' dan itibaren artık kullanılabilir değildir.

Gereksiz bütünleştirilmiş kod bağımlılıklarından veya sonraki sürümlerde son değişikliklerden kaçınmak için türler kaldırılmıştır.

#### <a name="recommended-action"></a>Önerilen eylem

Kodunuz **Microsoft. VisualBasic. MyServices** türlerinin ve üyelerinin kullanımına bağımlıysa, .NET sınıf kitaplığı 'nda karşılık gelen türler ve Üyeler vardır. Aşağıda, **Microsoft. VisualBasic. MyServices** türlerinin eşdeğer .NET sınıf kitaplığı türlerine eşlenmesi verilmiştir:

|Microsoft. VisualBasic. MyServices türü|.NET sınıf kitaplığı türü|
|--|--|
|<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>|WPF uygulamaları için <xref:System.Windows.Clipboard?displayProperty=nameWithType>, Windows Forms uygulamalar için <xref:System.Windows.Forms.Clipboard?displayProperty=nameWithType>|
|<xref:Microsoft.VisualBasic.MyServices.FileSystemProxy>|<xref:System.IO> ad alanındaki türler|
|<xref:Microsoft.VisualBasic.MyServices.RegistryProxy>|<xref:Microsoft.Win32> ad alanındaki kayıt defteriyle ilgili türler|
|<xref:Microsoft.VisualBasic.MyServices.SpecialDirectoriesProxy>|<xref:System.Environment.GetFolderPath%2A?displayProperty=nameWithType>|

#### <a name="category"></a>Kategori

Visual Basic

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.MyServices`

-- >

