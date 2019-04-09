---
title: '|| (VEYA) (Varlık SQL)'
ms.date: 03/30/2017
ms.assetid: 8e649648-eb9a-4380-9d74-36e62260628c
ms.openlocfilehash: 3ceaf33d8baba9776008cddcbe2e2d70f13fe089
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59141290"
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
 Döndüren herhangi bir geçerli ifade bir `Boolean`.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `true` koşullardan biri olduğunda `true`; Aksi takdirde `false`.  
  
## <a name="remarks"></a>Açıklamalar  
 VEYA bir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] mantıksal işleç. İki koşul birleştirmek için kullanılır. Bir deyimde birden fazla mantıksal işleç kullanıldığında, OR işleçlerini sonra ve işleçler değerlendirilir. Ancak, parantezler kullanarak Değerlendirme sırasını değiştirebilirsiniz.  
  
 Çift dikey çubuk (&#124;&#124;) OR işleci aynı işlevselliğe sahiptir.  
  
 Aşağıdaki tabloda olası giriş değerleri gösterir ve dönüş türleri.  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|TRUE|TRUE|TRUE|  
|`FALSE`|TRUE|FALSE|NULL|  
|`NULL`|TRUE|NULL|NULL|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki varlık SQL sorgusu OR işleci iki birleştirmek için kullanır. `Boolean` ifadeler. Sorgu, AdventureWorks satış modelini temel alıyor. Derleme ve bu sorguyu çalıştırmak için bu adımları izleyin:  
  
1.  Verilen yordamı izleyin [nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:  
  
 [!code-csharp[DP EntityServices Concepts 2#OR](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#or)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
