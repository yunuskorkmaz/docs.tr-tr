---
ms.openlocfilehash: d207a937917da78f6b902ad8ca4f02fa9a46c2e1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76116331"
---
### <a name="types-in-microsoftvisualbasicmyservices-namespace-not-available"></a>Microsoft.VisualBasic.MyServices ad alanında türleri kullanılamıyor

<xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> Ad alanındaki türler kullanılamıyor.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

.NET Core 3.0 Önizleme 8

#### <a name="change-description"></a>Açıklamayı değiştir

<xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> Ad alanındaki türler bazı .NET Core 3.0 Önizleme sürümlerinde kullanılabilir. .NET Core 3.0 Preview 9 ile başlayarak artık kullanılamazlar.

Türler, gereksiz derleme bağımlılıklarını veya sonraki sürümlerde değişiklikleri kırmayı önlemek için kaldırıldı.

#### <a name="recommended-action"></a>Önerilen eylem

Kodunuz **Microsoft.VisualBasic.MyServices** türlerinin ve üyelerinin kullanımına bağlıysa, .NET sınıf kitaplığında karşılık gelen türler ve üyeler vardır. Aşağıda, **Microsoft.VisualBasic.MyServices** türlerinin eşdeğer .NET sınıf kitaplık türlerine göre eşlemeleri verilmiştir:

|Microsoft.VisualBasic.MyServices türü|.NET sınıf kitaplık türü|
|--|--|
|<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>|<xref:System.Windows.Clipboard?displayProperty=nameWithType>WPF uygulamaları için, <xref:System.Windows.Forms.Clipboard?displayProperty=nameWithType> Windows Forms uygulamaları için|
|<xref:Microsoft.VisualBasic.MyServices.FileSystemProxy>|<xref:System.IO> Ad alanındaki türleri|
|<xref:Microsoft.VisualBasic.MyServices.RegistryProxy>|<xref:Microsoft.Win32> Ad alanında kayıt defteri yle ilgili türler|
|<xref:Microsoft.VisualBasic.MyServices.SpecialDirectoriesProxy>|<xref:System.Environment.GetFolderPath%2A?displayProperty=nameWithType>|

#### <a name="category"></a>Kategori

Visual Basic

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.MyServices`

-->
