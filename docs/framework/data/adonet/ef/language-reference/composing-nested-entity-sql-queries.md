---
title: "İç içe geçmiş varlık SQL sorguları oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 685d4cd3-2c1f-419f-bb46-c9d97a351eeb
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 175affdd8e9763f6cc7d0c48c38498af6e8ffabb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="composing-nested-entity-sql-queries"></a>İç içe geçmiş varlık SQL sorguları oluşturma
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]bir zengin işlevsel dilidir. Yapı bloğu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] bir ifadedir. Geleneksel SQL aksine [!INCLUDE[esql](../../../../../../includes/esql-md.md)] bir tablo sonuç kümesi sınırlı değildir: [!INCLUDE[esql](../../../../../../includes/esql-md.md)] değişmez değerleri, parametre veya iç içe geçmiş ifadeler olabilir karmaşık ifadeler oluşturmayı destekler. İfade bir değer parametreli veya diğer bazı ifadesi oluşur.  
  
## <a name="nested-expressions"></a>İç içe geçmiş ifadeler  
 İç içe geçmiş bir ifade, kabul edilen döndürür türünde bir değer herhangi bir yere yerleştirilebilir. Örneğin:  
  
```  
-- Returns a hierarchical collection of three elements at top-level.   
-- x must be passed in the parameter collection.  
ROW(@x, {@x}, {@x, 4, 5}, {@x, 7, 8, 9})  
  
-- Returns a hierarchical collection of one element at top-level.  
-- x must be passed in the parameter collection.  
{{{@x}}};  
```  
  
 İç içe bir sorgu projeksiyon yan tümcesinde yerleştirilebilir. Örneğin:  
  
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
  
 Aşağıdaki örnek düzgün ifadelerinde iç içe gösterilmiştir [!INCLUDE[esql](../../../../../../includes/esql-md.md)]: [nasıl yapılır: birleşim, iki sorguları sipariş](http://msdn.microsoft.com/en-us/853c583a-eaba-4400-830d-be974e735313).  
  
## <a name="nested-queries-in-projection"></a>İç içe yerleştirilmiş sorguda projeksiyon  
 Proje yan tümcesi iç içe geçmiş sorguları Kartezyen ürün sorguları sunucuda içine çevrilmiş. SQL Server dahil olmak üzere bazı arka uç sunucularında, bu sunucu performansını olumsuz yönde etkilenebilir çok büyük almak TempDB tablo neden olabilir.  
  
 Bu tür bir sorgunun bir örnek verilmiştir:  
  
```  
SELECT c, (SELECT c, (SELECT c FROM AdventureWorksModel.Vendor AS c  ) As Inner2 FROM AdventureWorksModel.JobCandidate AS c  ) As Inner1 FROM AdventureWorksModel.EmployeeDepartmentHistory AS c  
```  
  
## <a name="ordering-nested-queries"></a>İç içe geçmiş sorgular sıralama  
 Entity Framework iç içe geçmiş bir ifade herhangi bir yere sorguda yerleştirilebilir. Varlık SQL sorguları yazma büyük esneklik izin verdiğinden, bir iç içe geçmiş sorguları sıralama içeren bir sorgu yazmak mümkündür. Ancak, iç içe bir sorgu sırası korunmaz.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Varlık SQL genel bakış](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
