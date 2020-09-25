---
title: "&amp;&amp; ' (Entity SQL)"
ms.date: 03/30/2017
ms.assetid: e7d24213-471d-4807-b85e-570375df89b5
ms.openlocfilehash: 86ff43f8ed20c5696d15e21284394c3cb63200e3
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198047"
---
# <a name="ampamp-and-entity-sql"></a>&amp;&amp; ' (Entity SQL)

`true`Her iki ifade de varsa döndürür `true` ; Aksi takdirde `false` veya `NULL` .  
  
## <a name="syntax"></a>Syntax  
  
```csharp  
boolean_expression AND boolean_expression
```

veya  

```csharp
boolean_expression && boolean_expression  
```  
  
## <a name="arguments"></a>Arguments  

 `boolean_expression`  
 Boolean döndüren geçerli bir ifade.  
  
## <a name="remarks"></a>Açıklamalar  

 Çift ve + işaretleri (&&) ve işleciyle aynı işlevselliğe sahiptir.  
  
 Aşağıdaki tabloda olası giriş değerleri ve dönüş türleri gösterilmektedir.  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|TRUE|FALSE|NULL|  
|`FALSE`|FALSE|FALSE|FALSE|  
|`NULL`|NULL|FALSE|NULL|  
  
## <a name="example"></a>Örnek  

 Aşağıdaki Entity SQL sorgusu, ve işlecinin nasıl kullanılacağını göstermektedir. Sorgu AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.  
  
2. Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecuteStructuralTypeQuery` :  
  
 [!code-csharp[DP EntityServices Concepts 2#AND](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#and)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
