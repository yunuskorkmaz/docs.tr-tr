---
ms.openlocfilehash: 705bbd0e0bf80e0726d41898685a5e166e039f99
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858382"
---
### <a name="contentdisposition-datetimes-returns-slightly-different-string"></a>ContentDisposition DateTimes biraz farklı dize döndürür

|   |   |
|---|---|
|Ayrıntılar|<xref:System.Net.Mime.ContentDisposition?displayProperty=name>''lerin string gösterimleri, her zaman iki basamaklı bir <xref:System.DateTime?displayProperty=name> saat bileşenini temsil edecek şekilde 4,6'dan başlayarak güncelleştirildi. Bu [RFC822 ve RFC2822](https://www.ietf.org/rfc/rfc0822.txt) uymaktır. [RFC2822](https://www.ietf.org/rfc/rfc2822.txt) Bu, <xref:System.Net.Mime.ContentDisposition.ToString> mizaç zaman öğelerinden birinin 10:00'dan önce olduğu senaryolarda 4,6'da biraz daha farklı bir dize döndürmeye neden olur. ContentDispositions bazen dizeleri dönüştürerek seri hale getirilir, <xref:System.Net.Mime.ContentDisposition.ToString> bu nedenle herhangi bir işlem, serileştirme veya GetHashCode aramaları gözden geçirilmelidir.|
|Öneri|Farklı .NET Framework sürümlerinden ContentDispositions dize gösterimlerinin birbirleriyle doğru bir şekilde karşılaştırMasını beklemeyin. Bir karşılaştırma yapmadan önce dizeleri mümkünse ContentDispositions'a dönüştürün.|
|Kapsam|İkincil|
|Sürüm|4.6|
|Tür|Çalışma Zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Net.Mime.ContentDisposition.ToString?displayProperty=nameWithType></li><li><xref:System.Net.Mime.ContentDisposition.GetHashCode?displayProperty=nameWithType></li></ul>|
