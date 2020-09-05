---
ms.openlocfilehash: eb5c032a020799fa19cc0a8cfaabb56e01417ff4
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497820"
---
### <a name="contentdisposition-datetimes-returns-slightly-different-string"></a>ContentDisposition DateTimes biraz farklı bir dize döndürüyor

#### <a name="details"></a>Ayrıntılar

Öğesinin dize temsilleri <xref:System.Net.Mime.ContentDisposition?displayProperty=fullName> , 4,6 ' dan başlayarak, her zaman iki basamaklı bir saat bileşenini temsil edecek şekilde güncelleştirilmiştir <xref:System.DateTime?displayProperty=fullName> . Bu, [RFC822](https://www.ietf.org/rfc/rfc0822.txt) ve [RFC2822](https://www.ietf.org/rfc/rfc2822.txt)ile uyumlu değildir. Bu <xref:System.Net.Mime.ContentDisposition.ToString> , disposition 'nin zaman öğelerinden birinin 10:00 ' den önceki senaryolarda 4,6 ' de biraz farklı bir dize döndürmesine neden olur. ContentDispositions bazen dizelere dönüştürerek serileştirildiğine, böylece tüm <xref:System.Net.Mime.ContentDisposition.ToString> işlemler, serileştirme veya GetHashCode çağrılarının gözden geçirilmesi gerekir.

#### <a name="suggestion"></a>Öneri

Farklı .NET Framework sürümlerinden Contentdepositions dize temsilinin doğru bir şekilde karşılaştırılacağını beklememeniz beklenmez. Bir karşılaştırma yapmadan önce, mümkünse dizeleri tekrar Contentdepositions 'e dönüştürün.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |İkincil|
|Sürüm|4.6|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Net.Mime.ContentDisposition.ToString?displayProperty=nameWithType>
- <xref:System.Net.Mime.ContentDisposition.GetHashCode?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Net.Mime.ContentDisposition.ToString`
- `M:System.Net.Mime.ContentDisposition.GetHashCode`

-->
