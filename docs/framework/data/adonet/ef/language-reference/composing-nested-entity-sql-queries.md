---
title: İç İçe Geçmiş Entity SQL Sorguları Oluşturma
ms.date: 03/30/2017
ms.assetid: 685d4cd3-2c1f-419f-bb46-c9d97a351eeb
ms.openlocfilehash: 6b2fc9a32fc30d205b9c33257bf98781cfa07499
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150395"
---
# <a name="composing-nested-entity-sql-queries"></a>İç İçe Geçmiş Entity SQL Sorguları Oluşturma
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]zengin bir fonksiyonel dildir. Yapı taşı [!INCLUDE[esql](../../../../../../includes/esql-md.md)] bir deyimdir. Geleneksel SQL'in aksine, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] bir tabular [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sonuç kümesiyle sınırlı değildir: gerçek, parametre veya iç içe geçmiş ifadelere sahip karmaşık ifadeler oluşturmayı destekler. İfadedeki bir değer parametreli veya başka bir ifadeden oluşabilir.  
  
## <a name="nested-expressions"></a>İç Içe İfadeler  
 İç içe bir ifade, döndürdettiği türün değerinin kabul edildiği herhangi bir yere yerleştirilebilir. Örnek:  
  
```sql  
-- Returns a hierarchical collection of three elements at top-level.
-- x must be passed in the parameter collection.  
ROW(@x, {@x}, {@x, 4, 5}, {@x, 7, 8, 9})  
  
-- Returns a hierarchical collection of one element at top-level.  
-- x must be passed in the parameter collection.  
{{{@x}}};  
```  
  
 İç içe bir sorgu bir projeksiyon yan tümcesine yerleştirilebilir. Örnek:  
  
```sql  
-- Returns a collection of rows where each row contains an Address entity.  
-- and a collection of references to its corresponding SalesOrderHeader entities.  
SELECT address, (SELECT DEREF(soh)
                    FROM NAVIGATE(address, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS soh)
                    AS salesOrderHeader FROM AdventureWorksEntities.Address AS address  
```  
  
 İç [!INCLUDE[esql](../../../../../../includes/esql-md.md)]içe gelen sorgular her zaman parantez içinde eklenmelidir:  
  
```sql  
-- Pseudo-Entity SQL  
( SELECT …  
FROM … )  
UNION ALL  
( SELECT …  
FROM … );  
```  
  
 Aşağıdaki örnek, ifadelerin düzgün bir şekilde [!INCLUDE[esql](../../../../../../includes/esql-md.md)]nasıl yuvaya yerleşdirilir: [İki Sorgu Birliği'ni sırala.](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100))  
  
## <a name="nested-queries-in-projection"></a>Projeksiyonda İç Içe Sorgular  
 Proje yan tümcesindeki iç içe sorgular, sunucudaki Kartezyen ürün sorgularına çevrilebilir. SQL Server da dahil olmak üzere bazı arka uç sunucularında, bu durum TempDB tablosunun çok büyük olmasını sağlayabilir ve bu da sunucu performansını olumsuz etkileyebilir.  
  
 Aşağıdaki tür bir sorgu örneğidir:  
  
```sql  
SELECT c, (SELECT c, (SELECT c FROM AdventureWorksModel.Vendor AS c  ) As Inner2 FROM AdventureWorksModel.JobCandidate AS c  ) As Inner1 FROM AdventureWorksModel.EmployeeDepartmentHistory AS c  
```  
  
## <a name="ordering-nested-queries"></a>İç Içe Sorguları Sıralama  
 Varlık Çerçevesi'nde, iç içe bir ifade sorgunun herhangi bir yerine yerleştirilebilir. Entity SQL sorguları yazarken büyük esneklik sağladığından, iç içe sorgu sırasını içeren bir sorgu yazmak mümkündür. Ancak, iç içe sorgu sırası korunmaz.  
  
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
