---
title: "IsNull (varlık SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dc7a0173-3664-4c90-a57b-5cbb0a8ed7ee
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 31e0b77e397bd4f190119a01719da185211f7715
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="isnull-entity-sql"></a>IsNull (varlık SQL)
Bir sorgu ifadesi null olup olmadığını belirler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
expression IS [ NOT ] NULL  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Herhangi bir geçerli sorgu ifade. Gönderilemiyor koleksiyonu, koleksiyon üyeleri veya bir kayıt türü ile toplama türü özellikleri vardır.  
  
 DEĞİL  
 EDM üzerindeki geçersiz kılar. Boolean sonucu IS NULL.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `true`varsa `expression` döndürür; tersi durumda, `false`.  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanım `IS NULL` dış birleşim öğesi boş olup olmadığını belirlemek için:  
  
```  
select c   
      from LOB.Customers as c left outer join LOB.Orders as o   
                              on c.ID = o.CustomerID    
      where o is not null and o.OrderQuantity = @x  
```  
  
 Kullanım `IS NULL` üyesi gerçek bir değer olup olmadığını belirlemek için:  
  
```  
select c from LOB.Customer as c where c.DOB is not null  
```  
  
 Aşağıdaki tabloda davranışını gösterilmektedir `IS NULL` bazı desenleri üzerinden. Sağlayıcı çağrılır önce tüm istemci tarafındaki özel durumlar:  
  
|Desen|Davranış|  
|-------------|--------------|  
|Is Null NULL|Döndürür `true`.|  
|KABUL (null AS EntityType) IS NULL|Döndürür `true`.|  
|KABUL (null AS ComplexType) IS NULL|Bir hata oluşturur.|  
|KABUL (null AS RowType) IS NULL|Bir hata oluşturur.|  
|EntityType NULL|Döndürür `true` veya `false`.|  
|ComplexType NULL|Bir hata oluşturur.|  
|RowType NULL|Bir hata oluşturur.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu IS NOT NULL işleci bir sorgu ifadesi null olup olmadığını belirlemek için kullanır. Sorgu AdventureWorks satış modelini temel alır. Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:  
  
1.  Yordamı izleyin [nasıl yapılır: Sorgu döndürür StructuralType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:  
  
 [!code-csharp[DP EntityServices Concepts 2#ISNULL](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#isnull)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Varlık SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
