---
title: '|| (VEYA) (Varlık SQL)'
ms.date: 03/30/2017
ms.assetid: 8e649648-eb9a-4380-9d74-36e62260628c
ms.openlocfilehash: 8c93e68095a0e0ff63532f53152f166d6c3d047c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150099"
---
# <a name="-or-entity-sql"></a>|| (VEYA) (Varlık SQL)
İki `Boolean` ifadeyi birleştirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```sql  
boolean_expression OR boolean_expression  
-- or
boolean_expression || boolean_expression  
```  
  
## <a name="arguments"></a>Bağımsız Değişkenler  
 `boolean_expression`  
 Bir . döndüren geçerli ifadeler `Boolean`  
  
## <a name="return-value"></a>Dönüş Değeri  
 `true`koşullardan biri olduğunda; `true` aksi `false`takdirde, .  
  
## <a name="remarks"></a>Açıklamalar  
 OR mantıksal [!INCLUDE[esql](../../../../../../includes/esql-md.md)] bir işleçtir. İki koşulu birleştirmek için kullanılır. Bir bildirimde birden fazla mantıksal işleç kullanıldığında, OR işleçleri AND işleçlerinden sonra değerlendirilir. Ancak, parantez kullanarak değerlendirme sırasını değiştirebilirsiniz.  
  
 Çift dikey çubuklar (&#124;&#124;) OR işleciyle aynı işlevsellik tesahiptir.  
  
 Aşağıdaki tabloda olası giriş değerleri ve dönüş türleri gösterilmektedir.  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|TRUE|TRUE|TRUE|  
|`FALSE`|TRUE|FALSE|NULL|  
|`NULL`|TRUE|NULL|NULL|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki Entity SQL sorgusu, iki `Boolean` ifadeyi birleştirmek için OR işlecikullanır. Sorgu AdventureWorks Satış Modeli dayanmaktadır. Bu sorguyı derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [YapısalTürü Sonuçları Döndüren Bir Sorguyu Yürütme: Nasıl Yapılır'daki](../how-to-execute-a-query-that-returns-structuraltype-results.md)yordamı izleyin.  
  
2. Aşağıdaki sorguyu bağımsız değişken `ExecuteStructuralTypeQuery` olarak yönteme geçirin:  
  
 [!code-sql[DP EntityServices Concepts 2#OR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#or)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
