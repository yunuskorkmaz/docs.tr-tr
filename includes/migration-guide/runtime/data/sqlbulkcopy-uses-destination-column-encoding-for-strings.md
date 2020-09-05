---
ms.openlocfilehash: fd9f4f3de8f7be39242d4ff6924d480f20a1a06b
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497508"
---
### <a name="sqlbulkcopy-uses-destination-column-encoding-for-strings"></a>SqlBulkCopy dizeler için hedef sütun kodlamasını kullanır

#### <a name="details"></a>Ayrıntılar

Bir sütuna veri eklenirken, <xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=fullName> ve türleri için varsayılan kodlama yerine, hedef sütunun kodlamasını kullanır <code>VARCHAR</code> <code>CHAR</code> . Bu değişiklik, hedef sütun varsayılan kodlamayı kullanmadığında varsayılan kodlamayı kullanarak neden olunan veri bozulması olasılığını ortadan kaldırır. Nadir durumlarda, Kodlamadaki değişiklik hedef sütuna sığmayacak kadar büyük veriler üretirse, mevcut bir uygulama bir SqlException özel durumu oluşturabilir.

#### <a name="suggestion"></a>Öneri

<xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=fullName>Kodlama farklılıkları nedeniyle artık verileri bozmayacak. Hedef sütunun boyut sınırına yakın olan dizeler kopyalanırsa, verilerin önceden kodlanması gerekebilir (verilerin hedef sütuna sığması için kopyalanması için) veya Catch <xref:System.Data.SqlClient.SqlException?displayProperty=fullName> öğeleri.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Edge|
|Sürüm|4,5|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=nameWithType>
- <xref:System.Data.SqlClient.SqlBulkCopy.%23ctor(System.Data.SqlClient.SqlConnection)>

<!--

#### Affected APIs

- `T:System.Data.SqlClient.SqlBulkCopy`
- `M:System.Data.SqlClient.SqlBulkCopy.#ctor(System.Data.SqlClient.SqlConnection)`

-->
