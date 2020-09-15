---
ms.openlocfilehash: 48d2f1b5fa2eced30d3c9fb65804268904f11ab8
ms.sourcegitcommit: a69d548f90a03e105ee6701236c38390ecd9ccd1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2020
ms.locfileid: "90065076"
---
### <a name="unicode-category-changed-for-some-latin-1-characters"></a>Bazı Latin-1 karakterleri için Unicode kategorisi değişti

<xref:System.Char> Yöntemler şimdi Latin-1 aralığındaki karakterler için doğru Unicode kategorisini döndürüyor. Kategori Unicode standardına göre eşleşir.

#### <a name="change-description"></a>Açıklamayı Değiştir

Önceki .NET sürümlerinde, <xref:System.Char> Yöntemler Latin-1 aralığındaki karakterler için sabit bir Unicode kategori listesi kullandı. Ancak, Unicode standardı Bu API 'lerin uygulandığından bu karakterlerin bazı kategorilerini değiştirmiştir, bu da bir tutarsızlık oluşturuyor. Ayrıca, ve API 'ler arasında bir tutarsızlık vardı <xref:System.Char> <xref:System.Globalization.CharUnicodeInfo> , bu da Unicode standardını izler. .NET 5,0 ve sonraki sürümlerde Yöntemler, <xref:System.Char> tüm karakterler Için Unicode standartınkilerle eşleşen Unicode kategorisini kullanır ve döndürür.

Aşağıdaki tabloda, .NET 5,0 ' de Unicode kategorileri değişmiş olan karakterler gösterilmektedir:

| Karakter    | Unicode kategorisi<br>önceki .NET sürümlerinde | Unicode kategorisi<br>.NET 5,0 ve sonraki sürümlerde |
|:------------:|:---------------------------------------------:|:--------------------------------------------------:|
| § (\u00a7)   | `OtherSymbol`                                 | `OtherPunctuation`                                 |
| ª (\u00aa)   | `LowercaseLetter`                             | `OtherLetter`                                      |
| KıY (\u00ad) | `DashPunctuation`                             | `Format`                                           |
| ¶ (\u00b6)   | `OtherSymbol`                                 | `OtherPunctuation`                                 |
| † (\u00ba)   | `LowercaseLetter`                             | `OtherLetter`                                      |

#### <a name="version-introduced"></a>Sunulan sürüm

.NET 5,0 RC1

#### <a name="recommended-action"></a>Önerilen eylem

Sınıfını kullanarak Unicode karakter kategorisini alan herhangi bir kodunuz varsa <xref:System.Char> ve kategorinin hiçbir şekilde değişmediğini kabul eterdiğinizi, güncelleştirmeniz gerekebilir.

#### <a name="reason-for-change"></a>Değişiklik nedeni

Bu değişiklik, türü tarafından döndürülen kategorilerin <xref:System.Char> hem Unicode standardı hem de türü ile tutarlı olması için yapılmıştır <xref:System.Globalization.CharUnicodeInfo> .

#### <a name="category"></a>Kategori

- Core .NET kitaplıkları
- Genelleştirme

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Char.GetUnicodeCategory%2A?displayProperty=fullName>
- <xref:System.Char.IsLetter%2A?displayProperty=fullName>
- <xref:System.Char.IsPunctuation%2A?displayProperty=fullName>
- <xref:System.Char.IsSymbol%2A?displayProperty=fullName>
- <xref:System.Char.IsLower%2A?displayProperty=fullName>

Ayrıca, <xref:System.Char> Unicode karakter kategorisini elde etmek için bağlı olan herhangi bir sınıf, örneğin, <xref:System.Text.RegularExpressions.Regex> Bu değişiklikten etkilenir.

<!--

#### Affected APIs

- `Overload:System.Char.GetUnicodeCategory`
- `Overload:System.Char.IsLetter`
- `Overload:System.Char.IsPunctuation`
- `Overload:System.Char.IsSymbol`
- `Overload:System.Char.IsLower`

-->
