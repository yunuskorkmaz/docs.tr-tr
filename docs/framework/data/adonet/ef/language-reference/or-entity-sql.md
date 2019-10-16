---
title: '|| VEYA (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 8e649648-eb9a-4380-9d74-36e62260628c
ms.openlocfilehash: 6437b17fe1c1277701f06988ef6c02f4caf70e62
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319464"
---
# <a name="-or-entity-sql"></a>|| VEYA (Entity SQL)
İki `Boolean` ifadesini birleştirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```sql  
boolean_expression OR boolean_expression  
-- or   
boolean_expression || boolean_expression  
```  
  
## <a name="arguments"></a>Arguments  
 `boolean_expression`  
 @No__t-0 döndüren geçerli bir ifade.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `true`, koşullardan biri `true`; Aksi takdirde, `false`.  
  
## <a name="remarks"></a>Açıklamalar  
 YA da [!INCLUDE[esql](../../../../../../includes/esql-md.md)] mantıksal bir işleçtir. İki koşulu birleştirmek için kullanılır. Bir ifadede birden çok mantıksal operatör kullanıldığında veya işleçler ve işleçlerden sonra değerlendirilir. Ancak, parantez kullanarak değerlendirmenin sırasını değiştirebilirsiniz.  
  
 Çift dikey çubuklar (&#124;&#124;), or işleciyle aynı işlevselliğe sahiptir.  
  
 Aşağıdaki tabloda olası giriş değerleri ve dönüş türleri gösterilmektedir.  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|TRUE|TRUE|TRUE|  
|`FALSE`|TRUE|YANLÝÞ|NULL|  
|`NULL`|TRUE|NULL|NULL|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki Entity SQL sorgusu iki `Boolean` ifadesini birleştirmek için OR işlecini kullanır. Sorgu AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.  
  
2. Aşağıdaki sorguyu `ExecuteStructuralTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:  
  
 [!code-sql[DP EntityServices Concepts 2#OR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#or)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
