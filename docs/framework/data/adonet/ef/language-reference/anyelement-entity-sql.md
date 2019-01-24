---
title: ANYELEMENT (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 475a9ad6-8c8d-4f49-9970-af273e5360f1
ms.openlocfilehash: 16dbccf66413776af73f0b84463f9a56d2cee360
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54624125"
---
# <a name="anyelement-entity-sql"></a>ANYELEMENT (varlık SQL)
Birden çok değerli bir koleksiyondan bir öğe ayıklar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
ANYELEMENT ( expression )  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Öğeden ayıklamak için bir koleksiyon döndürür herhangi bir geçerli ifade.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Tek bir öğe koleksiyonu veya koleksiyon birden fazla varsa, rastgele bir öğe; koleksiyon boş ise döndürür `null`. Varsa `collection` türü koleksiyonudur `Collection<T>`, ardından `ANYELEMENT(collection)` verir türünün bir örneği geçerli bir ifade `T`.  
  
## <a name="remarks"></a>Açıklamalar  
 ANYELEMENT rastgele bir öğe birden çok değerli bir koleksiyondan ayıklar. Örneğin, aşağıdaki örnekte bir singleton öğesi kümesinden ayıklamaya çalışır `Customers`.  
  
```  
ANYELEMENT(Customers)  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu birden çok değerli bir koleksiyondan bir öğe ayıklanacak ANYELEMENT işleci kullanır. Sorgu, AdventureWorks satış modelini temel alıyor. Derleme ve bu sorguyu çalıştırmak için bu adımları izleyin:  
  
1.  Verilen yordamı izleyin [nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:  
  
 [!code-csharp[DP EntityServices Concepts 2#ANYELEMENT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#anyelement)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [Null Değer Atanabilir Yapılandırılmış Türler](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)
