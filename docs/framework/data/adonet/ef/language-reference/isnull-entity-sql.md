---
title: ISNULL (Entity SQL)
ms.date: 03/30/2017
ms.assetid: dc7a0173-3664-4c90-a57b-5cbb0a8ed7ee
ms.openlocfilehash: d54c350196ad1ef7cfafa6d931d9d1ad8f267177
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250565"
---
# <a name="isnull-entity-sql"></a>ISNULL (Entity SQL)
Sorgu ifadesinin null olup olmadığını belirler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
expression IS [ NOT ] NULL  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Herhangi bir geçerli sorgu ifadesi. Koleksiyon, koleksiyon üyeleri veya koleksiyon türü özellikleri olan bir kayıt türü olamaz.  
  
 DEĞİL  
 EDM 'yi geçersiz kılar. Boolean sonucu NULL.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `true`Eğer `expression` null döndürürse, `false`tersi durumda.  
  
## <a name="remarks"></a>Açıklamalar  
 Dış `IS NULL` birleştirmenin öğesinin null olup olmadığını anlamak için kullanın:  
  
```  
select c   
      from LOB.Customers as c left outer join LOB.Orders as o   
                              on c.ID = o.CustomerID    
      where o is not null and o.OrderQuantity = @x  
```  
  
 Üyenin `IS NULL` gerçek bir değere sahip olup olmadığını anlamak için kullanın:  
  
```  
select c from LOB.Customer as c where c.DOB is not null  
```  
  
 Aşağıdaki tabloda bazı desenlerin `IS NULL` üzerinde davranış gösterilmektedir. Sağlayıcı çağrılmadan önce istemci tarafında tüm özel durumlar atılır:  
  
|Desen|Davranış|  
|-------------|--------------|  
|NULL NULL|Döndürür `true`.|  
|DAVRAN (EntityType olarak null) NULL|Döndürür `true`.|  
|DAVRAN (ComplexType olarak null) NULL|Bir hata oluşturur.|  
|DEĞERLENDIRIN (RowType olarak null) NULL|Bir hata oluşturur.|  
|EntityType NULL|`true` Veya`false`döndürür.|  
|ComplexType NULL|Bir hata oluşturur.|  
|RowType NULL|Bir hata oluşturur.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu, bir sorgu ifadesinin null olmadığını anlamak için null olmayan bir işleç kullanır. Sorgu AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Aşağıdaki adımları uygulayın: StructuralType sonuçları](../how-to-execute-a-query-that-returns-structuraltype-results.md)döndüren bir sorgu yürütün.  
  
2. Aşağıdaki sorguyu `ExecuteStructuralTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:  
  
 [!code-csharp[DP EntityServices Concepts 2#ISNULL](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#isnull)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
