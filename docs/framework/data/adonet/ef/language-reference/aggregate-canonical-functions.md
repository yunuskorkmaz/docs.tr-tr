---
title: Kurallı toplama işlevleri
ms.date: 03/30/2017
ms.assetid: 3bcff826-ca90-41b3-a791-04d6ff0e5085
ms.openlocfilehash: 04b7d9c20373a465c073d55a090f1c2fd7fc6e07
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32761941"
---
# <a name="aggregate-canonical-functions"></a>Kurallı toplama işlevleri

Toplamalar, örneğin, tek bir değer olarak, bir dizi giriş değerleri azaltmak ifadelerini. Toplamalar normalde SELECT deyiminin GROUP BY yan tümcesi ile birlikte kullanılır ve burada kullanılabilmesi için kısıtlamaları vardır.

Aşağıdaki tabloda toplama gösterilmektedir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kurallı işlevleri.

| İşlev | Açıklama |
| -------- | ----------- |
| `Avg(expression)` | Null olmayan değerlerin ortalamasını döndürür.<br><br>**Bağımsız Değişkenler**<br><br>Bir `Int32`, `Int64`, `Double`, ve `Decimal`.<br><br>**Dönüş değeri**<br><br>Türü `expression`. `Null`, tüm giriş değerlerini varsa `null` değerleri.<br><br>**Örnek**[!code-csharp[DP EntityServices Concepts#EDM_AVG](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_avg)] [!code-sql[DP EntityServices Concepts#EDM_AVG](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_avg)] |
| `BigCount(expression)` | Null yinelenen değerler dahil olmak üzere toplam boyutu döndürür.<br><br>**Bağımsız Değişkenler**<br><br>Herhangi bir türü.<br><br>**Dönüş değeri**<br><br>Bir `Int64`.<br><br>**Örnek**[!code-csharp[DP EntityServices Concepts#EDM_BIGCOUNT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_bigcount)] [!code-sql[DP EntityServices Concepts#EDM_BIGCOUNT](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_bigcount)] |
| `Count(expression)` | Null yinelenen değerler dahil olmak üzere toplam boyutu döndürür.<br><br>**Bağımsız Değişkenler**<br><br>Herhangi bir türü.<br><br>**Dönüş değeri**<br><br>Bir `Int32`.<br><br>**Örnek**[!code-csharp[DP EntityServices Concepts#EDM_COUNT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_count)] [!code-sql[DP EntityServices Concepts#EDM_COUNT](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_count)] |
| `Max(expression)` | Null olmayan değerler maksimum döndürür.<br><br>**Bağımsız Değişkenler**<br><br>A `Byte`, `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, `Decimal`, `DateTime`, `DateTimeOffset`, `Time`, `String`, `Binary`.<br><br>**Dönüş değeri**<br><br>Türü `expression`. `Null`, tüm giriş değerlerini varsa `null` değerleri.<br><br>**Örnek**[!code-csharp[DP EntityServices Concepts#EDM_MAX](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_max)] [!code-sql[DP EntityServices Concepts#EDM_MAX](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_max)] |
| `Min(expression)` | Boş olmayan değerlerinin en küçüğünü döndürür.<br><br>**Bağımsız Değişkenler**<br><br>A `Byte`, `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, `Decimal`, `DateTime`, `DateTimeOffset`, `Time`, `String`, `Binary`.<br><br>**Dönüş değeri**<br><br>Türü `expression`. `Null`, tüm giriş değerlerini varsa `null` değerleri.<br><br>**Örnek**[!code-csharp[DP EntityServices Concepts#EDM_MIN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_min)] [!code-sql[DP EntityServices Concepts#EDM_MIN](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_min)] |
| `StDev(expression)` | Boş olmayan değerlerinin standart sapmasını döndürür.<br><br>**Bağımsız Değişkenler**<br><br>Bir `Int32`, `Int64`, `Double`, `Decimal`.<br><br>**Dönüş değeri**<br><br>A `Double`. `Null`, tüm giriş değerlerini varsa `null` değerleri.<br><br>**Örnek**[!code-csharp[DP EntityServices Concepts#EDM_STDEV](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_stdev)] [!code-sql[DP EntityServices Concepts#EDM_STDEV](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_stdev)] |
| `StDevP(expression)` | Tüm değerlerin popülasyon standart sapmasını döndürür.<br><br>**Bağımsız Değişkenler**<br><br>Bir `Int32`, `Int64`, `Double`, `Decimal`.<br><br>**Dönüş değeri**<br><br>A `Double`. `Null`, tüm giriş değerlerini varsa `null` değerleri.<br><br>**Örnek**[!code-csharp[DP EntityServices Concepts#EDM_STDEVP](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_stdevp)] [!code-sql[DP EntityServices Concepts#EDM_STDEVP](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_stdevp)] |
| `Sum(expression)` | Null olmayan değerlerin toplamını döndürür.<br><br>**Bağımsız Değişkenler**<br><br>Bir `Int32`, `Int64`, `Double`, `Decimal`.<br><br>**Dönüş değeri**<br><br>A `Double`. `Null`, tüm giriş değerlerini varsa `null` değerleri.<br><br>**Örnek**[!code-csharp[DP EntityServices Concepts#EDM_SUM](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_sum)] [!code-sql[DP EntityServices Concepts#EDM_SUM](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_sum)] |
| `Var(expression)` | Null olmayan tüm değerlerin varyansını döndürür.<br><br>**Bağımsız Değişkenler**<br><br>Bir `Int32`, `Int64`, `Double`, `Decimal`.<br><br>**Dönüş değeri**<br><br>A `Double`. `Null`, tüm giriş değerlerini varsa `null` değerleri.<br><br>**Örnek**[!code-csharp[DP EntityServices Concepts#EDM_VAR](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_var)] [!code-sql[DP EntityServices Concepts#EDM_VAR](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_var)] |
| `VarP(expression)` | Null olmayan tüm değerlerinin popülasyon varyansını döndürür.<br><br>**Bağımsız Değişkenler**<br><br>Bir `Int32`, `Int64`, `Double`, `Decimal`.<br><br>**Dönüş değeri**<br><br>A `Double`. `Null`, tüm giriş değerlerini varsa `null` değerleri.<br><br>**Örnek**[!code-csharp[DP EntityServices Concepts#EDM_VARP](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_varp)] [!code-sql[DP EntityServices Concepts#EDM_VARP](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_varp)] |

Microsoft SQL istemci yönetilen sağlayıcısında eşdeğer işlevselliği kullanılabilir. Daha fazla bilgi için bkz: [SqlClient Entity Framework işlevleri için](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).

## <a name="collection-based-aggregates"></a>Koleksiyon tabanlı toplar

Koleksiyon tabanlı toplamalar (toplama işlevleri) koleksiyonlar üzerinde çalışır ve bir değer döndürür. Örneğin tüm siparişleri koleksiyonu SİPARİŞLERİ ise, aşağıdaki ifade en erken sevk tarihi hesaplayabilirsiniz:

```sql
min(select value o.ShipDate from LOB.Orders as o)
```

Koleksiyon tabanlı toplamalar içindeki ifadeleri geçerli ortam ad çözümleme kapsamı içinde değerlendirilir.

## <a name="group-based-aggregates"></a>Grup tabanlı toplar

Grup tabanlı toplamalar, GROUP BY yan tümcesi tarafından tanımlanan bir grup üzerinden hesaplanır. Sonuç her grup için ayrı bir toplama toplama hesaplama giriş olarak olan her grupta öğeleri kullanılarak hesaplanır. Group by yan tümcesi select ifadesinde kullanıldığında, ifade adları, toplamalar veya sabit ifadeleri yalnızca gruplandırma projeksiyon ya da order by yan tümcesi mevcut olabilir.

Aşağıdaki örnekte, her ürün için sipariş edilen ortalama miktarı hesaplar:

```sql
select p, avg(ol.Quantity) from LOB.OrderLines as ol 
  group by ol.Product as p
```

Bir grup tabanlı toplama açık group by yan tümcesi olmadan SELECT ifadesinde olması mümkündür. Bu durumda, tüm öğeler tek bir grup olarak kabul edilir. Bu, bir sabit üzerinde alan bir gruplama belirtme eşdeğerdir. , Örneğin, aşağıdaki ifade alın:

```sql
select avg(ol.Quantity) from LOB.OrderLines as ol
```

Bu şuna eşdeğerdir:

```sql
select avg(ol.Quantity) from LOB.OrderLines as ol group by 1
```

İfadelerinin içinde grup tabanlı toplama WHERE yan tümcesi ifade görünür olacak ad çözümleme kapsamında değerlendirilir.

Olarak [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], Grup tabanlı toplamalar ayrıca bir tüm belirtin veya farklı değiştiricisi. AYRI değiştiricisi belirtilmemişse, toplama hesaplanan önce yinelenenleri birleşik giriş koleksiyonundan ortadan kalkar. Tüm değiştiricisi belirtilirse (veya hiçbir değiştiricisi belirtilmişse), hiçbir yinelenen eleme gerçekleştirilir.  

## <a name="see-also"></a>Ayrıca bkz.

[Kurallı İşlevler](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
