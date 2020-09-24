---
title: '|| VEYA (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 8e649648-eb9a-4380-9d74-36e62260628c
ms.openlocfilehash: 89c0a92030f2f067d5e5d45b58d475414a224ce4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91150810"
---
# <a name="-or-entity-sql"></a>|| VEYA (Entity SQL)

İki `Boolean` ifadeyi birleştirir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```sql  
boolean_expression OR boolean_expression  
-- or
boolean_expression || boolean_expression  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  

 `boolean_expression`  
 Döndüren geçerli bir ifade `Boolean` .  
  
## <a name="return-value"></a>Dönüş Değeri  

 `true` koşullardan biri olduğunda `true` ; Aksi durumda, `false` .  
  
## <a name="remarks"></a>Açıklamalar  

 VEYA mantıksal bir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] işleçtir. İki koşulu birleştirmek için kullanılır. Bir ifadede birden çok mantıksal operatör kullanıldığında veya işleçler ve işleçlerden sonra değerlendirilir. Ancak, parantez kullanarak değerlendirmenin sırasını değiştirebilirsiniz.  
  
 Çift dikey çubuklar (&#124;&#124;) veya işleciyle aynı işlevlere sahiptir.  
  
 Aşağıdaki tabloda olası giriş değerleri ve dönüş türleri gösterilmektedir.  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|TRUE|TRUE|TRUE|  
|`FALSE`|TRUE|FALSE|NULL|  
|`NULL`|TRUE|NULL|NULL|  
  
## <a name="example"></a>Örnek  

 Aşağıdaki Entity SQL sorgusu iki ifadeyi birleştirmek için OR işlecini kullanır `Boolean` . Sorgu AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.  
  
2. Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecuteStructuralTypeQuery` :  
  
 [!code-sql[DP EntityServices Concepts 2#OR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#or)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
