---
title: İç İçe Geçmiş Entity SQL Sorguları Oluşturma
ms.date: 03/30/2017
ms.assetid: 685d4cd3-2c1f-419f-bb46-c9d97a351eeb
ms.openlocfilehash: b28c46ba9a89ffffe8cd95ad55eb502eb8ea48a6
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90541102"
---
# <a name="composing-nested-entity-sql-queries"></a>İç İçe Geçmiş Entity SQL Sorguları Oluşturma
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] , zengin bir işlevsel dildir. Yapı Taşı [!INCLUDE[esql](../../../../../../includes/esql-md.md)] bir ifadedir. Geleneksel SQL 'den farklı olarak [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tablosal sonuç kümesiyle sınırlı değildir: [!INCLUDE[esql](../../../../../../includes/esql-md.md)] değişmez değerler, parametreler veya iç içe geçmiş deyimlere sahip karmaşık ifadeler oluşturmayı destekler. İfadedeki bir değer parametreli olabilir veya başka bir ifadeden oluşabilir.  
  
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
  
 İçinde [!INCLUDE[esql](../../../../../../includes/esql-md.md)] , iç içe sorguların her zaman parantez içine alınması gerekir:  
  
```sql  
-- Pseudo-Entity SQL  
( SELECT …  
FROM … )  
UNION ALL  
( SELECT …  
FROM … );  
```  
  
 Aşağıdaki örnek, içindeki ifadelerin nasıl düzgün bir şekilde iç içe alınacağını gösterir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] : [nasıl yapılır: Iki sorgunun birleşimini sıralama](/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100)).  
  
## <a name="nested-queries-in-projection"></a>Yansıtmada iç içe geçmiş sorgular  
 Project yan tümcesindeki iç içe geçmiş sorgular, sunucuda Kartezyen ürün sorgularına çevrilebilir. SQL Server dahil bazı arka uç sunucularında, bu, TempDB tablosunun çok büyük sürmesine neden olabilir ve bu da sunucu performansını olumsuz yönde etkileyebilir.  
  
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

- [Entity SQL’e Genel Bakış](entity-sql-overview.md)
