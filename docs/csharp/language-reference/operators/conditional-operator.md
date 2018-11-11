---
title: '?: İşleci (C# Başvurusu)'
ms.date: 07/20/2015
f1_keywords:
- ?:_CSharpKeyword
- ?_CSharpKeyword
- :_CSharpKeyword
helpviewer_keywords:
- '?: operator [C#]'
- conditional operator (?:) [C#]
ms.assetid: e83a17f1-7500-48ba-8bee-2fbc4c847af4
ms.openlocfilehash: 3e45ff6eaaefa5829c3ed9415abe1a12b7a1d069
ms.sourcegitcommit: 4bca8f7e172fd019ef437a4803bf5895c6bc4781
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2018
ms.locfileid: "50980628"
---
# <a name="-operator-c-reference"></a>?: İşleci (C# Başvurusu)

Koşullu işleç (`?:`), yaygın olarak bilinen bir Üçlü koşullu işleç, bir Boolean ifadesinin değerine bağlı olarak iki değerden birini döndürür. Aşağıda, koşullu işlecin sözdizimi belirtilmiştir.  

```csharp
condition ? first_expression : second_expression;  
```

İle başlayarak C# 7.2, `first_expression` ve `second_expression` my olması [ `ref` ifadeleri](https://github.com/dotnet/csharplang/blob/master/proposals/csharp-7.2/conditional-ref.md):

```csharp
ref condition ? ref first_expression : ref second_expression;  
```

Sonuç atanabilir bir `ref` veya `ref readonly` değişkenine veya bir değişkene hiçbiri değiştiricisi.

## <a name="remarks"></a>Açıklamalar

`condition` Değerlendirilmelidir `true` veya `false`. Varsa `condition` olduğu `true`, `first_expression` değerlendirilir ve sonuç olur. Varsa `condition` olduğu `false`, `second_expression` değerlendirilir ve sonuç olur. İki ifadeden yalnızca biri değerlendirilir. Bu sonucu olduğu ifadeler için özellikle önemlidir bir `ref`, aşağıdaki geçerli olduğu gibi:

```csharp
ref (storage != null) ? ref storage[3] : ref defaultValue;
```

Başvuru `storage` olduğunda değerlendirilmez `storage` null.

Bir değer türü olduğunda sonucu `first_expression` ve `second_expression` aynı veya orada bir türden diğerine örtülü bir dönüştürme diğerine olmalıdır olması gerekir. Sonuç olduğunda bir `ref`, türü `first_expression` ve `second_expression` aynı olmalıdır.

Aksi takdirde gerektirebilecek hesaplamaları ifade edebilirsiniz bir `if-else` koşullu işleç kullanarak daha kısaca oluşturma. Örneğin, aşağıdaki kod önce kullanan bir `if` deyimi ve sonra bir tamsayı artı veya eksi olarak sınıflandırmak için koşullu bir işleç.

```csharp
int input = Convert.ToInt32(Console.ReadLine());  
string classify;  
  
// if-else construction.  
if (input > 0)  
    classify = "positive";  
else  
    classify = "negative";  
  
// ?: conditional operator.  
classify = (input > 0) ? "positive" : "negative";  
```

Koşullu işleç, sağa ilişkilendirilir. İfade `a ? b : c ? d : e` değerlendirmesinde `a ? b : (c ? d : e)`, olarak değil `(a ? b : c) ? d : e`.  
  
Koşullu işleç aşırı yüklenemez.
  
## <a name="example"></a>Örnek

Aşağıdaki örnek, koşullu işlecin sonucu olan bir değer gösterir:

[!code-csharp[csRefOperators?:](~/samples/snippets/csharp/language-reference/operators/ConditionalExamples.cs#ConditionalValue)]

Aşağıdaki alternatif koşullu işlecin sonucu başvuru olduğu gösterilmektedir:

[!code-csharp[csRefOperatorsRef?:](~/samples/snippets/csharp/language-reference/operators/ConditionalExamples.cs#ConditionalRef)]

## <a name="see-also"></a>Ayrıca Bkz.

- [C# başvurusu](../../../csharp/language-reference/index.md)  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [C# İşleçleri](../../../csharp/language-reference/operators/index.md)  
- [if-else](../../../csharp/language-reference/keywords/if-else.md)  
- [?. and ?[] İşleçleri](../../../csharp/language-reference/operators/null-conditional-operators.md)  
- [?? İşleç](../../../csharp/language-reference/operators/null-coalescing-operator.md)
