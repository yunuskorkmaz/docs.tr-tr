---
title: ANYELEMENT (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 475a9ad6-8c8d-4f49-9970-af273e5360f1
ms.openlocfilehash: 11d1dd4b09ff07519f3435d313de72c5b9a3edf4
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="anyelement-entity-sql"></a>ANYELEMENT (varlık SQL)
Bir öğenin birden çok değerli bir koleksiyondan ayıklar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
ANYELEMENT ( expression )  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Bir öğeyi ayıklamak için bir koleksiyon döndürür herhangi bir geçerli sorgu ifade.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Tek bir öğeye koleksiyon ya da birden fazla koleksiyon varsa, bir öğeye; koleksiyon boş ise, döndürür `null`. Varsa `collection` türü koleksiyonudur `Collection<T>`, ardından `ANYELEMENT(collection)` türünün bir örneği üretir geçerli bir ifade `T`.  
  
## <a name="remarks"></a>Açıklamalar  
 ANYELEMENT birden çok değerli bir koleksiyondan bir öğeye ayıklar. Örneğin, aşağıdaki örnekte bir singleton öğesi kümesinden ayıklamaya çalışır `Customers`.  
  
```  
ANYELEMENT(Customers)  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu birden çok değerli bir koleksiyondaki bir öğe ayıklamak için ANYELEMENT işleci kullanır. Sorgu AdventureWorks satış modelini temel alır. Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:  
  
1.  Yordamı izleyin [nasıl yapılır: Sorgu döndürür StructuralType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:  
  
 [!code-csharp[DP EntityServices Concepts 2#ANYELEMENT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#anyelement)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Null Değer Atanabilir Yapılandırılmış Türler](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)
