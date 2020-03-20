---
title: ISNULL (Varlık SQL)
ms.date: 03/30/2017
ms.assetid: dc7a0173-3664-4c90-a57b-5cbb0a8ed7ee
ms.openlocfilehash: b3fc2484e80b637ed5841375985f7bae476bbbf7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150206"
---
# <a name="isnull-entity-sql"></a>ISNULL (Varlık SQL)
Sorgu ifadesinin null olup olmadığını belirler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```sql  
expression IS [ NOT ] NULL  
```  
  
## <a name="arguments"></a>Bağımsız Değişkenler  
 `expression`  
 Geçerli bir sorgu ifadesi. Koleksiyon olamaz, koleksiyon üyeleri veya koleksiyon türü özelliklerine sahip bir kayıt türü olamaz.  
  
 NOT  
 EDM'i etkisiz erdirdi. IS NULL boolean sonucu.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `true`null `expression` dönerse; aksi `false`takdirde, .  
  
## <a name="remarks"></a>Açıklamalar  
 Dış `IS NULL` birleştirme öğesinin null olup olmadığını belirlemek için kullanın:  
  
```sql  
select c
      from LOB.Customers as c left outer join LOB.Orders as o
                              on c.ID = o.CustomerID
      where o is not null and o.OrderQuantity = @x  
```  
  
 Bir `IS NULL` üyenin gerçek bir değeri olup olmadığını belirlemek için kullanın:  
  
```sql  
select c from LOB.Customer as c where c.DOB is not null  
```  
  
 Aşağıdaki tablo, bazı `IS NULL` desenler üzerinde davranışgösterir. Sağlayıcı çağrılmadan önce tüm özel durumlar istemci tarafından atılır:  
  
|Desen|Davranış|  
|-------------|--------------|  
|null NULL|`true` döndürür.|  
|TREAT (null AS EntityType) IS NULL|`true` döndürür.|  
|TREAT (null AS ComplexType) IS NULL|Bir hata atar.|  
|TREAT (null AS RowType) IS NULL|Bir hata atar.|  
|EntityType IS NULL|İade `true` `false`veya .|  
|ComplexType IS NULL|Bir hata atar.|  
|Satır Tipi NULL|Bir hata atar.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu, sorgu ifadesinin null olup olmadığını belirlemek için NULL işleci Değİl'i kullanır. Sorgu AdventureWorks Satış Modeli dayanmaktadır. Bu sorguyı derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [YapısalTürü Sonuçları Döndüren Bir Sorguyu Yürütme: Nasıl Yapılır'daki](../how-to-execute-a-query-that-returns-structuraltype-results.md)yordamı izleyin.  
  
2. Aşağıdaki sorguyu bağımsız değişken `ExecuteStructuralTypeQuery` olarak yönteme geçirin:  
  
 [!code-sql[DP EntityServices Concepts#ISNULL](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#isnull)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
