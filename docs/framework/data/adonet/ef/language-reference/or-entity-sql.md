---
title: '|| VEYA (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 8e649648-eb9a-4380-9d74-36e62260628c
ms.openlocfilehash: c88e041638fbe6f32717ce9c4f9c2ff6fb56d803
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249768"
---
# <a name="-or-entity-sql"></a>|| VEYA (Entity SQL)
İki `Boolean` ifadeyi birleştirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
boolean_expression OR boolean_expression  
or   
boolean_expression || boolean_expression  
```  
  
## <a name="arguments"></a>Arguments  
 `boolean_expression`  
 Döndüren geçerli bir `Boolean`ifade.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `true`koşullardan `true`biri olduğunda; Aksi durumda, `false`.  
  
## <a name="remarks"></a>Açıklamalar  
 Veya mantıksal bir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] işleçtir. İki koşulu birleştirmek için kullanılır. Bir ifadede birden çok mantıksal operatör kullanıldığında veya işleçler ve işleçlerden sonra değerlendirilir. Ancak, parantez kullanarak değerlendirmenin sırasını değiştirebilirsiniz.  
  
 Çift dikey çubuklar (&#124;&#124;), or işleciyle aynı işlevselliğe sahiptir.  
  
 Aşağıdaki tabloda olası giriş değerleri ve dönüş türleri gösterilmektedir.  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|TRUE|TRUE|TRUE|  
|`FALSE`|TRUE|YANLÝÞ|NULL|  
|`NULL`|TRUE|NULL|NULL|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki Entity SQL sorgusu iki `Boolean` ifadeyi birleştirmek için or işlecini kullanır. Sorgu AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Aşağıdaki adımları uygulayın: StructuralType sonuçları](../how-to-execute-a-query-that-returns-structuraltype-results.md)döndüren bir sorgu yürütün.  
  
2. Aşağıdaki sorguyu `ExecuteStructuralTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:  
  
 [!code-csharp[DP EntityServices Concepts 2#OR](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#or)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
