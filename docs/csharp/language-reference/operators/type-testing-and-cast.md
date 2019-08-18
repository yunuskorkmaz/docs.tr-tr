---
title: Tür testi ve atama işleçleri- C# başvuru
description: Bir ifade C# sonucunun türünü denetlemek ve gerekirse başka bir türe dönüştürmek için kullanabileceğiniz işleçler hakkında bilgi edinin.
ms.date: 06/21/2019
author: pkulikov
f1_keywords:
- is_CSharpKeyword
- as_CSharpKeyword
- ()_CSharpKeyword
- typeof_CSharpKeyword
helpviewer_keywords:
- type-testing operators [C#]
- conversion operators [C#]
- type conversion [C#]
- is operator [C#]
- as operator [C#]
- cast operator [C#]
- cast expression [C#]
- () operator [C#]
- typeof operator [C#]
ms.openlocfilehash: 6966d0b7a4f8a96bddb17ce2017fd53fc07ae922
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/17/2019
ms.locfileid: "69572332"
---
# <a name="type-testing-and-cast-operators-c-reference"></a>Tür-test ve atama işleçleri (C# başvuru)

Tür denetimi veya tür dönüştürme gerçekleştirmek için aşağıdaki işleçleri kullanabilirsiniz:

- [işleç](#is-operator): bir ifadenin çalışma zamanı türünün belirli bir tür ile uyumlu olup olmadığını denetlemek için
- [as işleci](#as-operator): çalışma zamanı türü bu türle uyumluysa bir ifadeyi açıkça belirli bir türe dönüştürmek için
- [cast işleci ()](#cast-operator-): açık bir dönüştürme gerçekleştirmek için
- [typeof işleci](#typeof-operator): bir türün <xref:System.Type?displayProperty=nameWithType> örneğini almak için

## <a name="is-operator"></a>işleç

`is` İşleci, bir ifade sonucunun çalışma zamanı türünün belirli bir tür ile uyumlu olup olmadığını denetler. `is` Operatör 7,0 C# ' den itibaren bir ifade sonucunu bir düzene göre de sınar.

Type-Testing `is` işlecine sahip ifade aşağıdaki biçimdedir

```csharp
E is T
```

, bir değer döndüren ve `T` bir tür ya da tür parametresinin adı olan bir ifadedir. `E` `E`anonim bir yöntem veya lambda ifadesi olamaz.

`false` `T` `true` İfadesi, sonucu`E` null olmayan ve bir başvuru dönüştürmesi, paketleme dönüştürmesi ya da bir kutudan çıkarma dönüştürmesi tarafından türe dönüştürülebileceğinden, öğesini döndürür; Aksi takdirde, döndürür. `E is T` `is` İşleci Kullanıcı tanımlı dönüştürmeleri dikkate almaz.

Aşağıdaki örnek, bir ifade sonucunun `is` çalışma zamanı `true` türü verilen bir türden türetilse, yani türler arasında bir başvuru dönüştürmesi varsa, işlecinin döndürdüğü gösterilmektedir:

[!code-csharp[is with reference conversion](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#IsWithReferenceConversion)]

Sonraki örnekte, `is` işlecin hesap paketleme ve kutudan çıkarma dönüştürmelerinin gösterdiği ancak sayısal dönüştürmeleri düşünmeyen bir örnek gösterilmektedir:

[!code-csharp-interactive[is with int](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#IsWithInt)]

Dönüşümler hakkında C# daha fazla bilgi için bkz. [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [dönüşümler](~/_csharplang/spec/conversions.md) bölümü.

### <a name="type-testing-with-pattern-matching"></a>Model eşleştirme ile test türü

`is` Operatör 7,0 C# ' den itibaren bir ifade sonucunu bir düzene göre de sınar. Özellikle, aşağıdaki biçimde tür düzenlerini destekler:

```csharp
E is T v
```

, bir `v` değer döndüren bir ifade, bir tür veya tür parametresinin adıdır ve yeni bir yerel değişken türünde `T`. `T` `E` Sonucu `E` null olmayan ve bir başvuru, paketleme `E is T v` veya kutudan çıkarma dönüştürmesi tarafından `T` ' e dönüştürülebiliyorsanız, ifade döner `true` ve şuna atanan sonuç `E` değeri değişken `v`.

Aşağıdaki örnek, `is` işleç kullanımını tür düzeniyle birlikte gösterir:

[!code-csharp-interactive[is with type pattern](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#IsTypePattern)]

Tür deseni ve diğer desteklenen desenler hakkında daha fazla bilgi için, bkz. [deseniyle eşleme](../keywords/is.md#pattern-matching-with-is).

## <a name="as-operator"></a>as işleci

`as` İşleci, bir ifadenin sonucunu açıkça belirli bir başvuruya veya null yapılabilir değer türüne dönüştürür. Dönüştürme mümkün değilse, `as` işleç döndürülür. `null` [Atama işlecinin ()](#cast-operator-)aksine, `as` işleç hiçbir şekilde özel durum oluşturmaz.

Formun ifadesi

```csharp
E as T
```

, bir değer döndüren ve `T` bir tür ya da tür parametresinin adı olan bir ifadedir, aynı sonucu şöyle üretir `E`

```csharp
E is T ? (T)(E) : (T)null
```

`E` hariç yalnızca bir kez değerlendirilir.

`as` İşleci yalnızca başvuru, null yapılabilir, kutulama ve kutudan çıkarma dönüştürmelerini dikkate alır. Kullanıcı tanımlı bir dönüştürme `as` gerçekleştirmek için işlecini kullanamazsınız. Bunu yapmak için, [cast işlecini ()](#cast-operator-)kullanın.

Aşağıdaki örnek `as` işlecinin kullanımını gösterir:

[!code-csharp-interactive[as operator](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#AsOperator)]

> [!NOTE]
> Yukarıdaki örnekte gösterildiği gibi, dönüştürmenin başarılı olup olmadığını kontrol `as` `null` etmek için ifadesinin sonucunu karşılaştırmanız gerekir. 7,0 ile C# başlayarak, dönüştürme işleminin başarılı olup olmadığını test etmek için, her iki [işleci](#type-testing-with-pattern-matching) de kullanabilirsiniz ve başarılı olursa sonucunu yeni bir değişkene atayın.

## <a name="cast-operator-"></a>Cast işleci ()

Formun `(T)E` bir atama ifadesi, ifadenin `E` sonucunun türüne `T`açık bir şekilde dönüştürülmesini gerçekleştirir. Türünden türüne hiçbir açık dönüştürme `E` `T`yoksa, derleme zamanı hatası oluşur. Çalışma zamanında, açık bir dönüştürme başarılı olmayabilir ve bir atama ifadesi bir özel durum oluşturabilir.

Aşağıdaki örnek, açık sayısal ve başvuru dönüştürmelerini göstermektedir:

[!code-csharp-interactive[cast expression](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#Cast)]

Desteklenen açık dönüştürmeler hakkında daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Açık dönüşümler](~/_csharplang/spec/conversions.md#explicit-conversions) bölümüne bakın. Özel bir açık veya örtük tür dönüştürme tanımlama hakkında daha fazla bilgi için bkz. [Kullanıcı tanımlı dönüştürme işleçleri](user-defined-conversion-operators.md).

### <a name="other-usages-of-"></a>() Diğer kullanımları

Ayrıca, [bir yöntemi çağırmak veya bir temsilciyi çağırmak](member-access-operators.md#invocation-operator-)için parantezleri de kullanabilirsiniz.

Diğer parantez kullanımı, bir ifadede işlemlerin değerlendirileceği sırayı belirtmektir. Daha fazla bilgi için [işleçler](../../programming-guide/statements-expressions-operators/operators.md) makalesinin [parantezler ekleme](../../programming-guide/statements-expressions-operators/operators.md#adding-parentheses) bölümüne bakın. Öncelik düzeyine göre sıralanan işleçlerin listesi için bkz [ C# . işleçler](index.md).

## <a name="typeof-operator"></a>typeof işleci

İşleci bir tür için <xref:System.Type?displayProperty=nameWithType> örneği edinir. `typeof` Aşağıdaki örnekte gösterildiği gibi `typeof` , işlecin bağımsız değişkeni bir tür veya tür parametresinin adı olmalıdır:

[!code-csharp-interactive[typeof operator](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#TypeOf)]

`typeof` İşleci ilişkisiz genel türler ile de kullanabilirsiniz. İlişkisiz genel türün adı, tür parametrelerinin sayısından küçük olan uygun sayıda virgül içermelidir. Aşağıdaki örnek, sınırsız bir genel türü olan `typeof` işlecinin kullanımını gösterir:

[!code-csharp-interactive[typeof unbound generic](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#TypeOfUnboundGeneric)]

İfade, `typeof` işlecin bağımsız değişkeni olamaz. İfade sonucunun çalışma <xref:System.Type?displayProperty=nameWithType> zamanı türünün örneğini almak için <xref:System.Object.GetType%2A?displayProperty=nameWithType> yöntemini kullanın.

### <a name="type-testing-with-the-typeof-operator"></a>`typeof` İşleci ile test türü

İfade sonucunun çalışma zamanı türünün verilen bir türle tam olarak eşleşip eşleşmediğini denetlemek için işlecinikullanın.`typeof` Aşağıdaki örnek, `typeof` işleç ve işleç [işleci](#is-operator)ile gerçekleştirilen tür denetimi arasındaki farkı gösterir:

[!code-csharp[typeof vs is](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#TypeCheckWithTypeOf)]

## <a name="operator-overloadability"></a>Operatör overloadability

`is`, Veişleçleri`typeof`aşırıyüklenebilirdeğildir. `as`

Kullanıcı tanımlı bir tür `()` işleci aşırı yükleyemez, ancak bir atama ifadesi tarafından gerçekleştirilebilecek özel tür dönüştürmeleri tanımlayabilir. Daha fazla bilgi için bkz. [Kullanıcı tanımlı dönüştürme işleçleri](user-defined-conversion-operators.md).

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:

- [SIS işleci](~/_csharplang/spec/expressions.md#the-is-operator)
- [As işleci](~/_csharplang/spec/expressions.md#the-as-operator)
- [Atama ifadeleri](~/_csharplang/spec/expressions.md#cast-expressions)
- [Typeof işleci](~/_csharplang/spec/expressions.md#the-typeof-operator)

## <a name="see-also"></a>Ayrıca bkz.

- [C#başvurunun](../index.md)
- [C# işleçleri](index.md)
- [Nasıl yapılır: model eşleştirme ve ve olarak işleç kullanarak güvenli bir şekilde atama](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md)
