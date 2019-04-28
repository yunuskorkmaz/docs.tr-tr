---
title: İç İçe Geçmiş Entity SQL Sorguları Oluşturma
ms.date: 03/30/2017
ms.assetid: 685d4cd3-2c1f-419f-bb46-c9d97a351eeb
ms.openlocfilehash: 4d6892e96cfbc9c5ba9d389aa03588c5133c7943
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61606231"
---
# <a name="composing-nested-entity-sql-queries"></a>İç İçe Geçmiş Entity SQL Sorguları Oluşturma
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] bir zengin işlevsel bir dildir. Yapı bloğu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] bir ifadedir. Geleneksel SQL aksine [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tablosal sonuçtaki kümesine sınırlı değildir: [!INCLUDE[esql](../../../../../../includes/esql-md.md)] değişmez değerleri, parametre veya iç içe geçmiş deyimler olabilir karmaşık ifadeleri oluşturmayı destekler. İfade bir değer parametreli veya başka bir ifadenin oluşur.  
  
## <a name="nested-expressions"></a>İç içe geçmiş deyimler  
 İç içe geçmiş bir ifade kabul döndürür türünde bir değer herhangi bir yerde yerleştirilebilir. Örneğin:  
  
```  
-- Returns a hierarchical collection of three elements at top-level.   
-- x must be passed in the parameter collection.  
ROW(@x, {@x}, {@x, 4, 5}, {@x, 7, 8, 9})  
  
-- Returns a hierarchical collection of one element at top-level.  
-- x must be passed in the parameter collection.  
{{{@x}}};  
```  
  
 İç içe yerleştirilmiş sorguda projeksiyon yan tümcesinde yerleştirilebilir. Örneğin:  
  
```  
-- Returns a collection of rows where each row contains an Address entity.  
-- and a collection of references to its corresponding SalesOrderHeader entities.  
SELECT address, (SELECT DEREF(soh)   
                    FROM NAVIGATE(address, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS soh)   
                    AS salesOrderHeader FROM AdventureWorksEntities.Address AS address  
```  
  
 İçinde [!INCLUDE[esql](../../../../../../includes/esql-md.md)], iç içe geçmiş sorgular parantez içinde her zaman alınmalıdır:  
  
```  
-- Pseudo-Entity SQL  
( SELECT …  
FROM … )  
UNION ALL  
( SELECT …  
FROM … );  
```  
  
 Aşağıdaki örnek düzgün ifadeleri iç içe gösterilmektedir [!INCLUDE[esql](../../../../../../includes/esql-md.md)]: [Nasıl yapılır: UNION iki sorgunun sipariş](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100)).  
  
## <a name="nested-queries-in-projection"></a>İç içe geçmiş sorgularda projeksiyonu  
 Proje yan tümcesi iç içe geçmiş sorgularda sunucuda Kartezyen ürün sorgulara çevrilmiş. SQL Server dahil olmak üzere bazı arka uç sunucular bu sunucu performansını olumsuz etkileyebilir, çok büyük almak TempDB tablodaki neden olabilir.  
  
 Bu tür bir sorgu örneği verilmiştir:  
  
```  
SELECT c, (SELECT c, (SELECT c FROM AdventureWorksModel.Vendor AS c  ) As Inner2 FROM AdventureWorksModel.JobCandidate AS c  ) As Inner1 FROM AdventureWorksModel.EmployeeDepartmentHistory AS c  
```  
  
## <a name="ordering-nested-queries"></a>İç içe geçmiş sorgular sıralama  
 Varlık Çerçevesi'nde, iç içe geçmiş bir ifade herhangi bir sorguda yerleştirilebilir. Entity SQL sorguları yazma büyük esneklik izin verdiğinden, bir iç içe geçmiş sorguları sıralamasını içeren bir sorgu yazmak mümkündür. Ancak, iç içe bir sorgu sırasını korunmaz.  
  
```  
-- The following query will order the results by last name.  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorksModel.Contact as C1  
        ORDER BY C1.LastName  
```  
  
```  
-- In the following query, ordering of the nested query is ignored.  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorksModel.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL’e Genel Bakış](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
