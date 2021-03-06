---
title: 'Son değişiklik: bazı Latin-1 karakterleri için Unicode kategorisi değişti'
description: .NET 5 ' teki Genelleştirme bölünmesi değişikliği hakkında bilgi edinmek için Char yöntemlerinin artık Latin-1 aralığındaki karakterler için doğru Unicode kategorisini döndürdüğü yerde.
ms.date: 04/07/2020
ms.openlocfilehash: 03355c488d2bdae78f989e647c9b5b7913d73649
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256679"
---
# <a name="unicode-category-changed-for-some-latin-1-characters"></a>Bazı Latin-1 karakterleri için Unicode kategorisi değişti

<xref:System.Char> Yöntemler şimdi Latin-1 aralığındaki karakterler için doğru Unicode kategorisini döndürüyor. Kategori Unicode standardına göre eşleşir.

## <a name="change-description"></a>Açıklamayı Değiştir

Önceki .NET sürümlerinde, <xref:System.Char> Yöntemler Latin-1 aralığındaki karakterler için sabit bir Unicode kategori listesi kullandı. Ancak, Unicode standardı Bu API 'lerin uygulandığından bu karakterlerin bazı kategorilerini değiştirmiştir, bu da bir tutarsızlık oluşturuyor. Ayrıca, ve API 'ler arasında bir tutarsızlık vardı <xref:System.Char> <xref:System.Globalization.CharUnicodeInfo> , bu da Unicode standardını izler. .NET 5 ve sonraki sürümlerde Yöntemler, <xref:System.Char> tüm karakterler Için Unicode standardı ile eşleşen Unicode kategorisini kullanır ve döndürür.

Aşağıdaki tabloda, .NET 5,0 ' de Unicode kategorileri değişmiş olan karakterler gösterilmektedir:

| Karakter    | Unicode kategorisi<br>önceki .NET sürümlerinde | Unicode kategorisi<br>.NET 5 ve sonraki sürümlerde |
|:------------:|:---------------------------------------------:|:--------------------------------------------------:|
| § (\u00a7)   | `OtherSymbol`                                 | `OtherPunctuation`                                 |
| ª (\u00aa)   | `LowercaseLetter`                             | `OtherLetter`                                      |
| KıY (\u00ad) | `DashPunctuation`                             | `Format`                                           |
| ¶ (\u00b6)   | `OtherSymbol`                                 | `OtherPunctuation`                                 |
| † (\u00ba)   | `LowercaseLetter`                             | `OtherLetter`                                      |

## <a name="version-introduced"></a>Sunulan sürüm

.NET 5.0

## <a name="recommended-action"></a>Önerilen eylem

Sınıfını kullanarak Unicode karakter kategorisini alan herhangi bir kodunuz varsa <xref:System.Char> ve kategorinin hiçbir şekilde değişmediğini kabul eterdiğinizi, güncelleştirmeniz gerekebilir.

## <a name="reason-for-change"></a>Değişiklik nedeni

Bu değişiklik, türü tarafından döndürülen kategorilerin <xref:System.Char> hem Unicode standardı hem de türü ile tutarlı olması için yapılmıştır <xref:System.Globalization.CharUnicodeInfo> .

## <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Char.GetUnicodeCategory%2A?displayProperty=fullName>
- <xref:System.Char.IsLetter%2A?displayProperty=fullName>
- <xref:System.Char.IsPunctuation%2A?displayProperty=fullName>
- <xref:System.Char.IsSymbol%2A?displayProperty=fullName>
- <xref:System.Char.IsLower%2A?displayProperty=fullName>

Ayrıca, <xref:System.Char> Unicode karakter kategorisini elde etmek için bağlı olan herhangi bir sınıf, örneğin, <xref:System.Text.RegularExpressions.Regex> Bu değişiklikten etkilenir.

<!--

### Affected APIs

- `Overload:System.Char.GetUnicodeCategory`
- `Overload:System.Char.IsLetter`
- `Overload:System.Char.IsPunctuation`
- `Overload:System.Char.IsSymbol`
- `Overload:System.Char.IsLower`

### Category

- Core .NET libraries
- Globalization
-
-->
