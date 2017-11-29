---
title: "as (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- as_CSharpKeyword
- as
helpviewer_keywords:
- type conversion [C#], as keyword
- as keyword [C#]
ms.assetid: a9be126b-cbf4-4990-a70d-d0e1983cad0e
caps.latest.revision: "24"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a4f2964f32a4139ffeb6d51b761f1176a57c5be6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="as-c-reference"></a>as (C# Başvurusu)
Kullanabileceğiniz `as` belirli türde bir uyumlu başvuru türleri arasında dönüştürme gerçekleştirmek için işleci veya [boş değer atanabilir türler](../../../csharp/programming-guide/nullable-types/index.md). Aşağıdaki kod örneği gösterir.  
  
 [!code-csharp[csrefKeywordsOperator#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/as_1.cs)]  
  
## <a name="remarks"></a>Açıklamalar  
 `as` İşlecidir gibi bir dönüştürme işlemi. Ancak, dönüştürme mümkün değilse `as` döndürür `null` yerine bir özel durum oluşturur. Aşağıdaki örnek göz önünde bulundurun:  
  
```  
expression as type  
```  
  
 Kod aşağıdaki ifade, dışında eşdeğerdir `expression` değişken yalnızca bir kez değerlendirilir.  
  
```  
expression is type ? (type)expression : (type)null  
```  
  
 Unutmayın `as` işleci yalnızca başvuru dönüşümleri, boş değer atanabilir dönüşümler ve kutulamayı dönüşümleri gerçekleştirir. `as` İşleci cast ifadeler kullanarak yerine gerçekleştirilmesi gereken kullanıcı tanımlı dönüşümler gibi diğer dönüştürme gerçekleştirilemiyor.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csrefKeywordsOperator#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/as_2.cs)]  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# anahtar sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [değil](../../../csharp/language-reference/keywords/is.md)  
 [?: İşleci](../../../csharp/language-reference/operators/conditional-operator.md)  
 [İşleç anahtar sözcükleri](../../../csharp/language-reference/keywords/operator-keywords.md)
