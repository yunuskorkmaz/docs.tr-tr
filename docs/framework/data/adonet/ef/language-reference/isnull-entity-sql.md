---
title: ISNULL (Entity SQL)
ms.date: 03/30/2017
ms.assetid: dc7a0173-3664-4c90-a57b-5cbb0a8ed7ee
ms.openlocfilehash: 3360ad4ca7306a8cc1b7d6948204f825ff9a93c6
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203624"
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
