---
title: Toplu kurallı İşlevler
ms.date: 03/30/2017
ms.assetid: 3bcff826-ca90-41b3-a791-04d6ff0e5085
ms.openlocfilehash: e4772176130fc72a22645462921c90dd5b7967b2
ms.sourcegitcommit: a1e35d4e94edab384a63406c0a5438306873031b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2018
ms.locfileid: "42752266"
---
# <a name="aggregate-canonical-functions"></a>Toplu kurallı İşlevler

Toplamlar, örneğin, tek bir değer giriş değerlerini bir dizi azaltan ifadelerdir. Toplamlar normalde seçin ifadesinin GROUP BY yan tümcesi ile birlikte kullanılır ve burada kullanılabilirler üzerindeki kısıtlamalar vardır.

## <a name="aggegate-entity-sql-canonical-functions"></a>Entity SQL Aggegate kurallı İşlevler

Entity SQL toplu kurallı işlevler şunlardır:

### <a name="avgexpression"></a>AVG(Expression)

Null olmayan değerlerin ortalamasını döndürür.

**Bağımsız Değişkenler**

Bir `Int32`, `Int64`, `Double`, ve `Decimal`.

**Dönüş değeri**

Türünü `expression`, veya `null` tüm giriş değerlerini varsa `null` değerleri.

**Örnek**

[!code-csharp[DP EntityServices Concepts#EDM_AVG](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_avg)] 
[!code-sql[DP EntityServices Concepts#EDM_AVG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_avg)]

### <a name="bigcountexpression"></a>BigCount(expression)

Null ve yinelenen değerleri dahil olmak üzere toplam boyutunu döndürür.

**Bağımsız Değişkenler**

Herhangi bir türü.

**Dönüş değeri**

Bir `Int64`.

**Örnek**

[!code-csharp[DP EntityServices Concepts#EDM_BIGCOUNT](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_bigcount)] 
[!code-sql[DP EntityServices Concepts#EDM_BIGCOUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_bigcount)]

### <a name="countexpression"></a>Count (deyim) 

Null ve yinelenen değerleri dahil olmak üzere toplam boyutunu döndürür.

**Bağımsız Değişkenler**

Herhangi bir türü.

**Dönüş değeri**

Bir `Int32`.

**Örnek**

[!code-csharp[DP EntityServices Concepts#EDM_COUNT](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_count)]
[!code-sql[DP EntityServices Concepts#EDM_COUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_count)]

### <a name="maxexpression"></a>Max(Expression)

Maksimum null olmayan değerini döndürür.

**Bağımsız Değişkenler**

A `Byte`, `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, `Decimal`, `DateTime`, `DateTimeOffset`, `Time`, `String`, `Binary`.

**Dönüş değeri**

Türünü `expression`, veya `null` tüm giriş değerlerini varsa `null` değerleri.

**Örnek**

[!code-csharp[DP EntityServices Concepts#EDM_MAX](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_max)]
[!code-sql[DP EntityServices Concepts#EDM_MAX](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_max)]

### <a name="minexpression"></a>Min(Expression)

Boş olmayan değerlerinin en küçüğünü döndürür.

**Bağımsız Değişkenler**

A `Byte`, `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, `Decimal`, `DateTime`, `DateTimeOffset`, `Time`, `String`, `Binary`.

**Dönüş değeri**

Türünü `expression`, veya `null` tüm giriş değerlerini varsa `null` değerleri.

**Örnek**

[!code-csharp[DP EntityServices Concepts#EDM_MIN](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_min)]
[!code-sql[DP EntityServices Concepts#EDM_MIN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_min)]

### <a name="stdevexpression"></a>StDev(expression)

Boş olmayan değerlerinin standart sapmasını döndürür.

**Bağımsız Değişkenler**

Bir `Int32`, `Int64`, `Double`, `Decimal`.

**Dönüş değeri**

A `Double`. `Null`, tüm giriş değerlerini varsa `null` değerleri.

**Örnek**

[!code-csharp[DP EntityServices Concepts#EDM_STDEV](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_stdev)]
[!code-sql[DP EntityServices Concepts#EDM_STDEV](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_stdev)]

### <a name="stdevpexpression"></a>StDevP(expression)

İçin tüm değerlerin popülasyon standart sapmasını döndürür.

**Bağımsız Değişkenler**

Bir `Int32`, `Int64`, `Double`, `Decimal`.

**Dönüş değeri**

A `Double`, veya `null` tüm giriş değerlerini varsa `null` değerleri.

**Örnek**

[!code-csharp[DP EntityServices Concepts#EDM_STDEVP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_stdevp)]
[!code-sql[DP EntityServices Concepts#EDM_STDEVP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_stdevp)]

### <a name="sumexpression"></a>SUM(Expression)

Null olmayan değerlerin toplamını döndürür.

**Bağımsız Değişkenler**

Bir `Int32`, `Int64`, `Double`, `Decimal`.

**Dönüş değeri**

A `Double`, veya `null` tüm giriş değerlerini varsa `null` değerleri.

**Örnek**

[!code-csharp[DP EntityServices Concepts#EDM_SUM](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_sum)]
[!code-sql[DP EntityServices Concepts#EDM_SUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_sum)]

### <a name="varexpression"></a>Var(Expression)

Null olmayan tüm değerlerin varyansını döndürür.

**Bağımsız Değişkenler**

Bir `Int32`, `Int64`, `Double`, `Decimal`.

**Dönüş değeri**

A `Double`, veya `null` tüm giriş değerlerini varsa `null` değerleri.

**Örnek**

[!code-csharp[DP EntityServices Concepts#EDM_VAR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_var)]
[!code-sql[DP EntityServices Concepts#EDM_VAR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_var)]

### <a name="varpexpression"></a>VarP(expression)

Null olmayan tüm değerlerin popülasyon varyansını döndürür.

**Bağımsız Değişkenler**

Bir `Int32`, `Int64`, `Double`, `Decimal`.

**Dönüş değeri**

A `Double`, veya `null` tüm giriş değerlerini varsa `null` değerleri.

**Örnek**

[!code-csharp[DP EntityServices Concepts#EDM_VARP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_varp)]
[!code-sql[DP EntityServices Concepts#EDM_VARP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_varp)] 

Microsoft SQL istemci yönetilen sağlayıcısında eşdeğer bir işlevselliği kullanılabilir. Daha fazla bilgi için [Entity Framework işlevleri için SqlClient](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).

## <a name="collection-based-aggregates"></a>Koleksiyon tabanlı toplamaları

Koleksiyon tabanlı toplamlar (toplama işlevleri), koleksiyonlar üzerinde çalışır ve bir değer döndürür. Örneğin SİPARİŞLER varsa tüm siparişleri koleksiyonunu sevk tarihten şu ifadeyle hesaplayabilirsiniz:

```sql
min(select value o.ShipDate from LOB.Orders as o)
```

Koleksiyon tabanlı toplamalar içindeki ifadeler, geçerli ortam ad çözümlemesi kapsamında değerlendirilir.

## <a name="group-based-aggregates"></a>Grup tabanlı toplamaları

Grup tabanlı toplamalar GROUP BY yan tümcesi tarafından tanımlanan bir grup üzerinden hesaplanır. Sonuçta her bir grup için ayrı bir toplama, toplam hesaplaması için giriş olarak her gruba öğeleri kullanılarak hesaplanır. Group by yan tümcesi select ifadesinde kullanıldığında, ifade adlarının, toplamlar ve sabit ifadeler yalnızca gruplandırma projeksiyon veya order by yan tümcesi içinde bulunabilir.

Aşağıdaki örnek, her ürün için sıralı ortalama miktarı hesaplar:

```sql
select p, avg(ol.Quantity) from LOB.OrderLines as ol 
  group by ol.Product as p
```

Bir grup tabanlı toplama açık group by yan tümcesi olmadan seçme olması mümkündür. Bu durumda, tüm öğeleri tek bir grup kabul edilir. Bu, bir sabit üzerinde temel alan bir gruplama belirtme eşdeğerdir. Örneğin, aşağıdaki ifade'yı uygulayın:

```sql
select avg(ol.Quantity) from LOB.OrderLines as ol
```

Bu aşağıdakine eşdeğerdir:

```sql
select avg(ol.Quantity) from LOB.OrderLines as ol group by 1
```

Grup tabanlı toplama içinde ifadeler, WHERE yan tümcesi ifade görünür olur ad çözümlemesi kapsamında değerlendirilir.

Olarak [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], Grup tabanlı toplamalar BÜTÜN belirtebilirsiniz veya ayrı değiştiricisi. AYRI değiştiricisi belirtilmemişse, toplama hesaplanan önce yinelenenleri birleşik giriş koleksiyondan ortadan kalkar. Tüm değiştirici belirtilirse (veya herhangi bir değiştiricisi belirtilmişse), hiçbir yinelenen eleme gerçekleştirilir.  

## <a name="see-also"></a>Ayrıca bkz.

[Kurallı İşlevler](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
