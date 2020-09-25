---
title: ANYELEMENT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 475a9ad6-8c8d-4f49-9970-af273e5360f1
ms.openlocfilehash: e060956545ca924fa6fedb80b2f53ff312f307a2
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201206"
---
# <a name="anyelement-entity-sql"></a>ANYELEMENT (Entity SQL)

Çok değerli bir koleksiyondan bir öğe ayıklar.  
  
## <a name="syntax"></a>Söz dizimi  
  
```csharp
ANYELEMENT ( expression )  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  

 `expression`  
 Öğesinden bir öğe Ayıklanacak bir koleksiyon döndüren geçerli bir sorgu ifadesi.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Koleksiyonda tek bir öğe veya koleksiyonda birden fazla varsa rastgele öğe. Koleksiyon boşsa, döndürür `null` . `collection`, Türünde bir koleksiyondur `Collection<T>` , bir `ANYELEMENT(collection)` türü örneği veren geçerli bir ifadedir `T` .  
  
## <a name="remarks"></a>Açıklamalar  

 ANYELEMENT çok değerli bir koleksiyondaki rastgele bir öğeyi ayıklar. Örneğin, aşağıdaki örnek kümeden tek bir öğe ayıklamaya çalışır `Customers` .  
  
```csharp
ANYELEMENT(Customers)  
```  
  
## <a name="example"></a>Örnek  

 Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu, çok değerli bir koleksiyondan bir öğe ayıklamak IÇIN AnyElement işlecini kullanır. Sorgu AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.  
  
2. Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecuteStructuralTypeQuery` :  
  
 [!code-csharp[DP EntityServices Concepts 2#ANYELEMENT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#anyelement)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
- [Null Değer Atanabilir Yapılandırılmış Türler](nullable-structured-types-entity-sql.md)
