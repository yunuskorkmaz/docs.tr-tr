---
title: ANYELEMENT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 475a9ad6-8c8d-4f49-9970-af273e5360f1
ms.openlocfilehash: c0f7686f7ff3f6458637b51e29ecafe0c0ccfbc4
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040321"
---
# <a name="anyelement-entity-sql"></a>ANYELEMENT (Entity SQL)
Çok değerli bir koleksiyondan bir öğe ayıklar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```csharp
ANYELEMENT ( expression )  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Öğesinden bir öğe Ayıklanacak bir koleksiyon döndüren geçerli bir sorgu ifadesi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Koleksiyonda tek bir öğe veya koleksiyonda birden fazla varsa rastgele öğe. Koleksiyon boşsa `null`döndürür. `collection`, `Collection<T>`türünde bir koleksiyondur `ANYELEMENT(collection)`, `T`türünde bir örnek veren geçerli bir ifadedir.  
  
## <a name="remarks"></a>Açıklamalar  
 ANYELEMENT çok değerli bir koleksiyondaki rastgele bir öğeyi ayıklar. Örneğin, aşağıdaki örnek `Customers`kümesinden tek bir öğe çıkarmaya çalışır.  
  
```csharp
ANYELEMENT(Customers)  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgusu, çok değerli bir koleksiyondan bir öğe ayıklamak için ANYELEMENT işlecini kullanır. Sorgu AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.  
  
2. Aşağıdaki sorguyu `ExecuteStructuralTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:  
  
 [!code-csharp[DP EntityServices Concepts 2#ANYELEMENT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#anyelement)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
- [Null Değer Atanabilir Yapılandırılmış Türler](nullable-structured-types-entity-sql.md)
