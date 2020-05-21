---
ms.openlocfilehash: acb8ed44b7d18b257731e32339f087c8fe5fdd4a
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721696"
---
### <a name="types-in-microsoftvisualbasicmyservices-namespace-not-available"></a>Microsoft. VisualBasic. MyServices ad alanındaki türler kullanılamıyor

<xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName>Ad alanındaki türler kullanılamıyor.

#### <a name="version-introduced"></a>Sunulan sürüm

.NET Core 3,0 Preview 8

#### <a name="change-description"></a>Açıklamayı Değiştir

Ad alanındaki türler, <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> bazı .NET Core 3,0 önizleme sürümlerinde mevcuttur. .NET Core 3,0 Preview 9 ' dan itibaren artık kullanılabilir değildir.

Gereksiz bütünleştirilmiş kod bağımlılıklarından veya sonraki sürümlerde son değişikliklerden kaçınmak için türler kaldırılmıştır.

#### <a name="recommended-action"></a>Önerilen eylem

Kodunuz **Microsoft. VisualBasic. MyServices** türlerinin ve üyelerinin kullanımına bağımlıysa, .NET sınıf kitaplığı 'nda karşılık gelen türler ve Üyeler vardır. Aşağıda, **Microsoft. VisualBasic. MyServices** türlerinin eşdeğer .NET sınıf kitaplığı türlerine eşlenmesi verilmiştir:

|Microsoft. VisualBasic. MyServices türü|.NET sınıf kitaplığı türü|
|--|--|
|<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>|<xref:System.Windows.Clipboard?displayProperty=nameWithType>WPF uygulamaları için <xref:System.Windows.Forms.Clipboard?displayProperty=nameWithType> Windows Forms uygulamalar için|
|<xref:Microsoft.VisualBasic.MyServices.FileSystemProxy>|<xref:System.IO>Ad alanındaki türler|
|<xref:Microsoft.VisualBasic.MyServices.RegistryProxy>|Ad alanındaki kayıt defteri ile ilgili türler <xref:Microsoft.Win32>|
|<xref:Microsoft.VisualBasic.MyServices.SpecialDirectoriesProxy>|<xref:System.Environment.GetFolderPath%2A?displayProperty=nameWithType>|

#### <a name="category"></a>Kategori

Visual Basic

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName>

<!--

#### Affected APIs

- `N:Microsoft.VisualBasic.MyServices`

-->
