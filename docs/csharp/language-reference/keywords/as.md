---
title: as (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- as_CSharpKeyword
- as
helpviewer_keywords:
- type conversion [C#], as keyword
- as keyword [C#]
ms.assetid: a9be126b-cbf4-4990-a70d-d0e1983cad0e
ms.openlocfilehash: 092c30a858df7baeb35bdf28bae53802fb0916d4
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2018
ms.locfileid: "34172025"
---
# <a name="as-c-reference"></a>as (C# Başvurusu)
Kullanabileceğiniz `as` belirli türde bir uyumlu başvuru türleri arasında dönüştürme gerçekleştirmek için işleci veya [boş değer atanabilir türler](../../../csharp/programming-guide/nullable-types/index.md). Aşağıdaki kod örneği gösterir.  
  
 [!code-csharp[csrefKeywordsOperator#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/as_1.cs)]  
  
## <a name="remarks"></a>Açıklamalar  
 `as` İşlecidir gibi bir dönüştürme işlemi. Ancak, dönüştürme mümkün değilse `as` döndürür `null` yerine bir özel durum oluşturur. Aşağıdaki örnek göz önünde bulundurun:  
  
```csharp  
expression as type  
```  
  
 Kod aşağıdaki ifade, dışında eşdeğerdir `expression` değişken yalnızca bir kez değerlendirilir.  
  
```csharp  
expression is type ? (type)expression : (type)null  
```  
  
 Unutmayın `as` işleci yalnızca başvuru dönüşümleri, boş değer atanabilir dönüşümler ve kutulamayı dönüşümleri gerçekleştirir. `as` İşleci cast ifadeler kullanarak yerine gerçekleştirilmesi gereken kullanıcı tanımlı dönüşümler gibi diğer dönüştürme gerçekleştirilemiyor.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csrefKeywordsOperator#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/as_2.cs)]  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [is](../../../csharp/language-reference/keywords/is.md)  
 [?: İşleci](../../../csharp/language-reference/operators/conditional-operator.md)  
 [İşleç Anahtar Sözcükleri](../../../csharp/language-reference/keywords/operator-keywords.md)
