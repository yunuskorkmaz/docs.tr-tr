---
title: as (C# Başvurusu)
ms.date: 10/11/2018
f1_keywords:
- as_CSharpKeyword
- as
helpviewer_keywords:
- type conversion [C#], as keyword
- as keyword [C#]
ms.assetid: a9be126b-cbf4-4990-a70d-d0e1983cad0e
ms.openlocfilehash: d6c9d44ff22881e6e5e7a542e1df41bbf77b23d8
ms.sourcegitcommit: 3b1cb8467bd73dee854b604e306c0e7e3882d91a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2018
ms.locfileid: "49122735"
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
 
## <a name="see-also"></a>Ayrıca Bkz.  
- [C# başvurusu](../../../csharp/language-reference/index.md)  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
- [is](../../../csharp/language-reference/keywords/is.md)  
- [?: İşleci](../../../csharp/language-reference/operators/conditional-operator.md)  
- [İşleç Anahtar Sözcükleri](../../../csharp/language-reference/keywords/operator-keywords.md)
