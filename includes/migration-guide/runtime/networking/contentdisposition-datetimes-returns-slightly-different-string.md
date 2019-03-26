---
ms.openlocfilehash: 529d1b83c0637f705b725a64aa82e2c053bbfd19
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "58467087"
---
### <a name="contentdisposition-datetimes-returns-slightly-different-string"></a>ContentDisposition tarih saatleri biraz farklı bir dize döndürür.

|   |   |
|---|---|
|Ayrıntılar|Dize temsillerini <xref:System.Net.Mime.ContentDisposition?displayProperty=name>ait her zaman saat bileşenini temsil etmek için 4.6 itibaren güncelleştirilen bir <xref:System.DateTime?displayProperty=name> iki basamakla. Uymak için budur [RFC822](https://www.ietf.org/rfc/rfc0822.txt) ve [RFC2822](https://www.ietf.org/rfc/rfc2822.txt). Bu neden <xref:System.Net.Mime.ContentDisposition.ToString> değerlendirme'nın zaman öğelerden birine 10: 00'da önce olduğu senaryolarda 4.6 olarak biraz farklı bir dize döndürecek şekilde. ContentDispositions bazen dizelerine şekilde dönüştürme aracılığıyla seri halde olmadığını unutmayın <xref:System.Net.Mime.ContentDisposition.ToString> işlemleri, seri hale getirme veya GetHashCode çağrıları gözden geçirileceğini.|
|Öneri|Dize temsillerini ContentDispositions farklı .NET Framework sürümlerinden doğru bir başkasına karşılaştıracağız olduğunu beklemiyoruz. Dizelere ContentDispositions, mümkün olduğunda, bir karşılaştırma yapmadan önce dönüştürün.|
|Kapsam|İkincil|
|Sürüm|4.6|
|Tür|Çalışma zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Net.Mime.ContentDisposition.ToString?displayProperty=nameWithType></li><li><xref:System.Net.Mime.ContentDisposition.GetHashCode?displayProperty=nameWithType></li></ul>|

