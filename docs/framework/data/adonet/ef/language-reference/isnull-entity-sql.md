---
title: ISNULL (Entity SQL)
ms.date: 03/30/2017
ms.assetid: dc7a0173-3664-4c90-a57b-5cbb0a8ed7ee
ms.openlocfilehash: 9066f9fb68ce2c50e9523881cfa0dd930cd0b52e
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319726"
---
# <a name="isnull-entity-sql"></a>ISNULL (Entity SQL)
Sorgu ifadesinin null olup olmadığını belirler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```sql  
expression IS [ NOT ] NULL  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Herhangi bir geçerli sorgu ifadesi. Koleksiyon, koleksiyon üyeleri veya koleksiyon türü özellikleri olan bir kayıt türü olamaz.  
  
 BAŞLATıLMADı  
 EDM 'yi geçersiz kılar. Boolean sonucu NULL.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `expression` null döndürürse `true`; Aksi takdirde, `false`.  
  
## <a name="remarks"></a>Açıklamalar  
 Dış birleştirmenin öğesinin null olup olmadığını anlamak için `IS NULL` kullanın:  
  
```sql  
select c   
      from LOB.Customers as c left outer join LOB.Orders as o   
                              on c.ID = o.CustomerID    
      where o is not null and o.OrderQuantity = @x  
```  
  
 Üyenin gerçek bir değere sahip olup olmadığını anlamak için `IS NULL` kullanın:  
  
```sql  
select c from LOB.Customer as c where c.DOB is not null  
```  
  
 Aşağıdaki tabloda bazı desenlerdeki `IS NULL` ' ın davranışı gösterilmektedir. Sağlayıcı çağrılmadan önce istemci tarafında tüm özel durumlar atılır:  
  
|Desen|Davranış|  
|-------------|--------------|  
|NULL NULL|@No__t-0 döndürür.|  
|DAVRAN (EntityType olarak null) NULL|@No__t-0 döndürür.|  
|DAVRAN (ComplexType olarak null) NULL|Bir hata oluşturur.|  
|DEĞERLENDIRIN (RowType olarak null) NULL|Bir hata oluşturur.|  
|EntityType NULL|@No__t-0 veya `false` döndürür.|  
|ComplexType NULL|Bir hata oluşturur.|  
|RowType NULL|Bir hata oluşturur.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgusu, bir sorgu ifadesinin null olmadığını anlamak için NULL işlecini kullanır. Sorgu AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.  
  
2. Aşağıdaki sorguyu `ExecuteStructuralTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:  
  
 [!code-sql[DP EntityServices Concepts#ISNULL](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#isnull)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
