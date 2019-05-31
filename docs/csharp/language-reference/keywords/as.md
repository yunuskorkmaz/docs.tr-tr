---
title: olarak - C# başvurusu
ms.custom: seodec18
ms.date: 10/11/2018
f1_keywords:
- as_CSharpKeyword
- as
helpviewer_keywords:
- type conversion [C#], as keyword
- as keyword [C#]
ms.assetid: a9be126b-cbf4-4990-a70d-d0e1983cad0e
ms.openlocfilehash: 84e599340877ce52dc6242ea259c69672915c546
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66422021"
---
# <a name="as-c-reference"></a>as (C# Başvurusu)
Kullanabileceğiniz `as` belirli türlerdeki uyumlu başvuru türleri arasında dönüştürmeler gerçekleştirmek için işleci veya [boş değer atanabilir türler](../../../csharp/programming-guide/nullable-types/index.md). Aşağıdaki kod örneği gösterir.  
  
[!code-csharp[csrefKeywordsOperator#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#1)]

Örnekte gösterildiği gibi sonucunu karşılaştırmak gereken `as` ifadesiyle `null` dönüştürme başarılı olup olmadığını denetlemek için. Kullanabileceğiniz C# 7.0 ile başlayarak, [olduğu](is.md) dönüştürme başarılı olduğunu test etmek ve Dönüştürme başarılı olduğunda bir değişken koşullu olarak atamak için ifadesinde iki. Birçok senaryoda kullanmaktan daha kısa `as` işleci. Daha fazla bilgi için [türü deseni](is.md#type) bölümünü [ `is` işleci](is.md) makalesi.
  
## <a name="remarks"></a>Açıklamalar  
 `as` İşleci, bir tür dönüştürme işlemini gibi. Ancak, dönüştürme mümkün değilse `as` döndürür `null` yerine bir özel durum oluşturur. Aşağıdaki örnek göz önünde bulundurun:  
  
```csharp  
expression as type  
```  
  
 Kod, aşağıdaki ifade hariç eşdeğerdir `expression` değişken yalnızca bir kez değerlendirilir.  
  
```csharp  
expression is type ? (type)expression : (type)null  
```  
  
 Unutmayın `as` işleci, yalnızca başvuru dönüşümleri, boş değer atanabilir dönüştürmeler ve kutulama dönüştürmeleri gerçekleştirir. `as` İşleci, bunun yerine cast ifadeleri kullanarak gerçekleştirilmelidir kullanıcı tanımlı dönüşümler gibi diğer dönüştürmeler gerçekleştiremezsiniz.  
  
## <a name="example"></a>Örnek  

[!code-csharp[csrefKeywordsOperator#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#2)]
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  

Daha fazla bilgi için [işleci olarak](~/_csharplang/spec/expressions.md#the-as-operator) içinde [ C# dil belirtimi](../language-specification/index.md). Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.
 
## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../../../csharp/language-reference/index.md)
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)
- [is](../../../csharp/language-reference/keywords/is.md)
- [?: İşleç](../../../csharp/language-reference/operators/conditional-operator.md)
