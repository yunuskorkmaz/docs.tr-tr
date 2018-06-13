---
title: '|| (VEYA) (Varlık SQL)'
ms.date: 03/30/2017
ms.assetid: 8e649648-eb9a-4380-9d74-36e62260628c
ms.openlocfilehash: 09ae742f648f95819a8c6fc64d402c4f11c7748a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32764625"
---
# <a name="-or-entity-sql"></a>|| (VEYA) (Varlık SQL)
İki birleştirir `Boolean` ifadeler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
boolean_expression OR boolean_expression  
or   
boolean_expression || boolean_expression  
```  
  
## <a name="arguments"></a>Arguments  
 `boolean_expression`  
 Döndüren herhangi bir geçerli ifadeler bir `Boolean`.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `true` koşullardan biri olduğunda `true`; Aksi halde, `false`.  
  
## <a name="remarks"></a>Açıklamalar  
 VEYA bir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] mantıksal işleç. İki koşul birleştirmek için kullanılır. Birden fazla mantıksal işleç bir deyimde kullanıldığında veya işleçler ve işleçler sonra değerlendirilir. Ancak, parantez kullanarak Değerlendirme sırasını değiştirebilirsiniz.  
  
 Çift dikey çubuk (&#124;&#124;) veya işlecini aynı işlevselliğe sahiptir.  
  
 Aşağıdaki tabloda olası giriş değerleri gösterir ve dönüş türleri.  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|TRUE|TRUE|TRUE|  
|`FALSE`|TRUE|FALSE|NULL|  
|`NULL`|TRUE|NULL|NULL|  
  
## <a name="example"></a>Örnek  
 İki birleştirmek için aşağıdaki varlık SQL sorgusunu veya işlecini kullanan `Boolean` ifadeler. Sorgu AdventureWorks satış modelini temel alır. Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:  
  
1.  Yordamı izleyin [nasıl yapılır: Sorgu döndürür StructuralType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:  
  
 [!code-csharp[DP EntityServices Concepts 2#OR](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#or)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
