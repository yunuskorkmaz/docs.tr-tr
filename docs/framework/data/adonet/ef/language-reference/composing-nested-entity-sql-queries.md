---
title: Iç Içe Entity SQL sorguları oluşturma
ms.date: 03/30/2017
ms.assetid: 685d4cd3-2c1f-419f-bb46-c9d97a351eeb
ms.openlocfilehash: 0ab92c1e41c89f141c3cbd37be3e1e18e64d9666
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833909"
---
# <a name="composing-nested-entity-sql-queries"></a>Iç Içe Entity SQL sorguları oluşturma
[!INCLUDE[esql](../../../../../../includes/esql-md.md)], zengin bir işlevsel dildir. @No__t-0 yapı taşı bir ifadedir. Geleneksel SQL 'den farklı olarak [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tablosal sonuç kümesiyle sınırlı değildir: [!INCLUDE[esql](../../../../../../includes/esql-md.md)], sabit değerler, parametreler veya iç içe geçmiş ifadelerle karmaşık ifadeler oluşturmayı destekler. İfadedeki bir değer parametreli olabilir veya başka bir ifadeden oluşabilir.  
  
## <a name="nested-expressions"></a>İç içe geçmiş Ifadeler  
 İç içe geçmiş bir ifade, döndürdüğü türden bir değerin kabul edildiği her yerde yerleştirilebilir. Örnek:  
  
```sql  
-- Returns a hierarchical collection of three elements at top-level.   
-- x must be passed in the parameter collection.  
ROW(@x, {@x}, {@x, 4, 5}, {@x, 7, 8, 9})  
  
-- Returns a hierarchical collection of one element at top-level.  
-- x must be passed in the parameter collection.  
{{{@x}}};  
```  
  
 İç içe geçmiş bir sorgu, bir izdüşüm yan tümcesine yerleştirilebilir. Örnek:  
  
```sql  
-- Returns a collection of rows where each row contains an Address entity.  
-- and a collection of references to its corresponding SalesOrderHeader entities.  
SELECT address, (SELECT DEREF(soh)   
                    FROM NAVIGATE(address, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS soh)   
                    AS salesOrderHeader FROM AdventureWorksEntities.Address AS address  
```  
  
 @No__t-0 ' da, iç içe sorguların her zaman parantez içine alınması gerekir:  
  
```sql  
-- Pseudo-Entity SQL  
( SELECT …  
FROM … )  
UNION ALL  
( SELECT …  
FROM … );  
```  
  
 Aşağıdaki örnek, [!INCLUDE[esql](../../../../../../includes/esql-md.md)]: [nasıl yapılır: Iki sorgunun birleşimini sıralama](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100))gibi ifadeleri nasıl doğru bir şekilde iç içe geçirebileceğinizi gösterir.  
  
## <a name="nested-queries-in-projection"></a>Yansıtmada iç içe geçmiş sorgular  
 Project yan tümcesindeki iç içe geçmiş sorgular, sunucuda Kartezyen ürün sorgularına çevrilebilir. SLQ sunucusu dahil bazı arka uç sunucularında, bu, TempDB tablosunun çok büyük sürmesine neden olabilir ve bu da sunucu performansını olumsuz yönde etkileyebilir.  
  
 Bu tür bir sorgunun örneği aşağıda verilmiştir:  
  
```sql  
SELECT c, (SELECT c, (SELECT c FROM AdventureWorksModel.Vendor AS c  ) As Inner2 FROM AdventureWorksModel.JobCandidate AS c  ) As Inner1 FROM AdventureWorksModel.EmployeeDepartmentHistory AS c  
```  
  
## <a name="ordering-nested-queries"></a>Iç Içe sorguları sıralama  
 Entity Framework, iç içe geçmiş bir ifade sorgunun herhangi bir yerine yerleştirilebilir. Entity SQL sorguları yazarken harika esneklik sağladığından, iç içe geçmiş sorguların sıralamasını içeren bir sorgu yazmak mümkündür. Ancak, iç içe geçmiş bir sorgunun sırası korunmaz.  
  
```sql  
-- The following query will order the results by last name.  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorksModel.Contact as C1  
        ORDER BY C1.LastName  
```  
  
```sql  
-- In the following query, ordering of the nested query is ignored.  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorksModel.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL genel bakış](entity-sql-overview.md)
