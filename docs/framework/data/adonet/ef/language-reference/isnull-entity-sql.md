---
title: IsNull (varlık SQL)
ms.date: 03/30/2017
ms.assetid: dc7a0173-3664-4c90-a57b-5cbb0a8ed7ee
ms.openlocfilehash: aaecce3ff74d64b8e07b31329ced5b5e581fca5b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59295100"
---
# <a name="isnull-entity-sql"></a>IsNull (varlık SQL)
Sorgu ifadesi null olup olmadığını belirler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
expression IS [ NOT ] NULL  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Herhangi bir geçerli ifade. Olamaz, bir koleksiyon, koleksiyon üyeleri veya bir kayıt türü ile toplama türü özellikleri vardır.  
  
 DEĞİL  
 EDM olumsuz duruma getirir. IS NULL, Boolean sonucu.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `true` varsa `expression` döndürür, aksi takdirde `false`.  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanım `IS NULL` dış birleşim öğesinin boş olup olmadığını belirlemek için:  
  
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
  
 Aşağıdaki tabloda davranışını gösteren `IS NULL` bazı desenleri üzerinden. Sağlayıcı çağrılır önce tüm istemci tarafında özel durumlar:  
  
|Desen|Davranış|  
|-------------|--------------|  
|Is Null NULL|Döndürür `true`.|  
|IS NULL DAVRANMA (null AS EntityType)|Döndürür `true`.|  
|IS NULL DAVRANMA (null AS ComplexType)|Bir hata oluşturur.|  
|IS NULL DAVRANMA (null AS RowType)|Bir hata oluşturur.|  
|EntityType IS NULL|Döndürür `true` veya `false`.|  
|ComplexType null|Bir hata oluşturur.|  
|RowType IS NULL|Bir hata oluşturur.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu IS NOT NULL işleci bir sorgu ifadesi null değilse belirlemek için kullanır. Sorgu, AdventureWorks satış modelini temel alıyor. Derleme ve bu sorguyu çalıştırmak için bu adımları izleyin:  
  
1. Verilen yordamı izleyin [nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:  
  
 [!code-csharp[DP EntityServices Concepts 2#ISNULL](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#isnull)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
