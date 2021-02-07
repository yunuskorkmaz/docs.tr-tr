---
description: 'Hakkında daha fazla bilgi edinin: ıSNULL (Entity SQL)'
title: ISNULL (Entity SQL)
ms.date: 03/30/2017
ms.assetid: dc7a0173-3664-4c90-a57b-5cbb0a8ed7ee
ms.openlocfilehash: 1dbaf964facf089ab6714ebd58baf8b040288cff
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99748498"
---
# <a name="isnull-entity-sql"></a>ISNULL (Entity SQL)

Sorgu ifadesinin null olup olmadığını belirler.  
  
## <a name="syntax"></a>Söz dizimi  
  
```sql  
expression IS [ NOT ] NULL  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  

 `expression`  
 Herhangi bir geçerli sorgu ifadesi. Koleksiyon, koleksiyon üyeleri veya koleksiyon türü özellikleri olan bir kayıt türü olamaz.  
  
 NOT  
 EDM 'yi geçersiz kılar. Boolean sonucu NULL.  
  
## <a name="return-value"></a>Dönüş Değeri  

 `true` Eğer `expression` null döndürürse, tersi durumda `false` .  
  
## <a name="remarks"></a>Açıklamalar  

 `IS NULL`Dış birleştirmenin öğesinin null olup olmadığını anlamak için kullanın:  
  
```sql  
select c
      from LOB.Customers as c left outer join LOB.Orders as o
                              on c.ID = o.CustomerID
      where o is not null and o.OrderQuantity = @x  
```  
  
 `IS NULL`Üyenin gerçek bir değere sahip olup olmadığını anlamak için kullanın:  
  
```sql  
select c from LOB.Customer as c where c.DOB is not null  
```  
  
 Aşağıdaki tabloda `IS NULL` bazı desenlerin üzerinde davranış gösterilmektedir. Sağlayıcı çağrılmadan önce istemci tarafında tüm özel durumlar atılır:  
  
|Desen|Davranış|  
|-------------|--------------|  
|NULL NULL|`true` döndürür.|  
|DAVRAN (EntityType olarak null) NULL|`true` döndürür.|  
|DAVRAN (ComplexType olarak null) NULL|Bir hata oluşturur.|  
|DEĞERLENDIRIN (RowType olarak null) NULL|Bir hata oluşturur.|  
|EntityType NULL|`true`Veya döndürür `false` .|  
|ComplexType NULL|Bir hata oluşturur.|  
|RowType NULL|Bir hata oluşturur.|  
  
## <a name="example"></a>Örnek  

 Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu, bir sorgu ifadesinin null olmadığını anlamak IÇIN null olmayan bir işleç kullanır. Sorgu AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.  
  
2. Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecuteStructuralTypeQuery` :  
  
 [!code-sql[DP EntityServices Concepts#ISNULL](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#isnull)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
