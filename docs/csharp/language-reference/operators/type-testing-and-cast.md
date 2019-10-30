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
ms.openlocfilehash: d2fd43644949c842ff883731d3c7f00228cabfd7
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73038862"
---
# <a name="type-testing-and-cast-operators-c-reference"></a>Tür-test ve atama işleçleri (C# başvuru)

Tür denetimi veya tür dönüştürme gerçekleştirmek için aşağıdaki işleçleri kullanabilirsiniz:

- [işleç](#is-operator): bir ifadenin çalışma zamanı türünün belirli bir tür ile uyumlu olup olmadığını denetlemek için
- [as işleci](#as-operator): çalışma zamanı türü bu türle uyumluysa bir ifadeyi açıkça belirli bir türe dönüştürmek için
- [cast işleci ()](#cast-operator-): açık bir dönüştürme gerçekleştirmek için
- [typeof işleci](#typeof-operator): bir türün <xref:System.Type?displayProperty=nameWithType> örneğini almak için

## <a name="is-operator"></a>işleç

`is` işleci, bir ifade sonucunun çalışma zamanı türünün belirli bir tür ile uyumlu olup olmadığını denetler. C# 7,0 ' den başlayarak,`is`işleci bir düzene karşı bir ifade sonucunu da sınar.

Tür-test `is` işleci olan ifade aşağıdaki biçimdedir

```csharp
E is T
```

Burada `E` bir değer döndüren bir ifadedir ve `T` bir türün veya bir tür parametresinin adıdır. `E` anonim bir yöntem veya lambda ifadesi olamaz.

`E is T` ifadesi, `E` sonucu null değilse ve bir başvuru dönüştürmesi, paketleme dönüştürmesi ya da bir kutudan çıkarma dönüştürmesi tarafından `T` türüne dönüştürülebiliyorsanız `true` döndürür. Aksi takdirde, `false`döndürür. `is` işleci Kullanıcı tanımlı dönüştürmeleri dikkate almaz.

Aşağıdaki örnek, bir ifade sonucunun çalışma zamanı türü verilen bir türden türetilse, yani türler arasında bir başvuru dönüştürmesi varsa `is` işlecinin `true` döndürdüğünü gösterir:

[!code-csharp[is with reference conversion](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#IsWithReferenceConversion)]

Sonraki örnek, `is` işlecinin hesap paketleme ve kutudan çıkarma dönüştürmelerine sahip olduğunu ancak [sayısal dönüştürmeleri](../builtin-types/numeric-conversions.md)düşünmediğini gösterir:

[!code-csharp-interactive[is with int](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#IsWithInt)]

Dönüşümler hakkında C# daha fazla bilgi için bkz. [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [dönüşümler](~/_csharplang/spec/conversions.md) bölümü.

### <a name="type-testing-with-pattern-matching"></a>Model eşleştirme ile test türü

C# 7,0 ' den başlayarak,`is`işleci bir düzene karşı bir ifade sonucunu da sınar. Özellikle, aşağıdaki biçimde tür düzenlerini destekler:

```csharp
E is T v
```

`E`, bir değer döndüren bir ifadedir, `T` bir tür ya da bir tür parametresidir ve `v` `T`türünde yeni bir yerel değişkendir. `E` sonucu null değilse ve bir başvuru, paketleme veya kutudan çıkarma dönüştürmesi tarafından `T` dönüştürülebiliyorsanız, `E is T v` ifadesi `true` döndürür ve `E` sonucunun dönüştürülmüş değeri değişken `v`atanır.

Aşağıdaki örnek, `is` işlecinin tür düzeniyle kullanımını gösterir:

[!code-csharp-interactive[is with type pattern](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#IsTypePattern)]

Tür deseni ve diğer desteklenen desenler hakkında daha fazla bilgi için, bkz. [deseniyle eşleme](../keywords/is.md#pattern-matching-with-is).

## <a name="as-operator"></a>as işleci

`as` işleci, bir ifadenin sonucunu açıkça belirli bir başvuruya veya null yapılabilir değer türüne dönüştürür. Dönüştürme mümkün değilse, `as` işleci `null`döndürür. [Atama işlecinin ()](#cast-operator-)aksine, `as` işleci hiçbir şekilde özel durum oluşturmaz.

Formun ifadesi

```csharp
E as T
```

`E`, bir değer döndüren ve `T` bir tür veya tür parametresinin adı olan bir ifadedir, aynı sonucu şöyle üretir

```csharp
E is T ? (T)(E) : (T)null
```

`E` hariç, yalnızca bir kez değerlendirilir.

`as` işleci yalnızca başvuru, null yapılabilir, kutulama ve kutudan çıkarma dönüştürmelerini dikkate alır. Kullanıcı tanımlı bir dönüştürme gerçekleştirmek için `as` işlecini kullanamazsınız. Bunu yapmak için, [cast işlecini ()](#cast-operator-)kullanın.

Aşağıdaki örnek `as` işlecinin kullanımını gösterir:

[!code-csharp-interactive[as operator](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#AsOperator)]

> [!NOTE]
> Yukarıdaki örnekte gösterildiği gibi, dönüştürmenin başarılı olup olmadığını denetlemek için `as` ifadesinin sonucunu `null` karşılaştırmanız gerekir. 7,0 ' C# den başlayarak, dönüştürmenin başarılı olup olmadığını test etmek için, her iki [işleci](#type-testing-with-pattern-matching) de kullanabilirsiniz ve başarılı olursa, sonucunu yeni bir değişkene atayın.

## <a name="cast-operator-"></a>Cast işleci ()

Form `(T)E` bir atama ifadesi, `T`yazmak için ifade `E` sonucunun açık bir şekilde dönüştürülmesini gerçekleştirir. `E` türünden `T`türüne açık bir dönüştürme yoksa, derleme zamanı hatası oluşur. Çalışma zamanında, açık bir dönüştürme başarılı olmayabilir ve bir atama ifadesi bir özel durum oluşturabilir.

Aşağıdaki örnek, açık sayısal ve başvuru dönüştürmelerini göstermektedir:

[!code-csharp-interactive[cast expression](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#Cast)]

Desteklenen açık dönüştürmeler hakkında daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Açık dönüşümler](~/_csharplang/spec/conversions.md#explicit-conversions) bölümüne bakın. Özel bir açık veya örtük tür dönüştürme tanımlama hakkında daha fazla bilgi için bkz. [Kullanıcı tanımlı dönüştürme işleçleri](user-defined-conversion-operators.md).

### <a name="other-usages-of-"></a>() Diğer kullanımları

Ayrıca, [bir yöntemi çağırmak veya bir temsilciyi çağırmak](member-access-operators.md#invocation-operator-)için parantezleri de kullanabilirsiniz.

Diğer parantez kullanımı, bir ifadede işlemlerin değerlendirileceği sırayı ayarlamadır. Daha fazla bilgi için bkz [ C# . işleçler](index.md).

## <a name="typeof-operator"></a>typeof işleci

`typeof` işleci bir tür için <xref:System.Type?displayProperty=nameWithType> örneğini alır. Aşağıdaki örnekte gösterildiği gibi `typeof` işlecinin bağımsız değişkeni bir tür veya tür parametresinin adı olmalıdır:

[!code-csharp-interactive[typeof operator](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#TypeOf)]

`typeof` işlecini ilişkisiz genel türlerle de kullanabilirsiniz. İlişkisiz genel türün adı, tür parametrelerinin sayısından küçük olan uygun sayıda virgül içermelidir. Aşağıdaki örnek, `typeof` işlecinin ilişkisiz genel bir tür kullanımını gösterir:

[!code-csharp-interactive[typeof unbound generic](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#TypeOfUnboundGeneric)]

İfade `typeof` işlecinin bağımsız değişkeni olamaz. Bir ifade sonucunun çalışma zamanı türü <xref:System.Type?displayProperty=nameWithType> örneğini almak için <xref:System.Object.GetType%2A?displayProperty=nameWithType> metodunu kullanın.

### <a name="type-testing-with-the-typeof-operator"></a>`typeof` işleci ile test yazın

İfade sonucunun çalışma zamanı türünün verilen bir türle tam olarak eşleşip eşleşmediğini denetlemek için `typeof` işlecini kullanın. Aşağıdaki örnek, `typeof` işleci ve [işleç işleci](#is-operator)ile gerçekleştirilen tür denetimi arasındaki farkı gösterir:

[!code-csharp[typeof vs is](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#TypeCheckWithTypeOf)]

## <a name="operator-overloadability"></a>Operatör overloadability

`is`, `as`ve `typeof` işleçleri aşırı yüklenemez.

Kullanıcı tanımlı bir tür `()` işlecini aşırı yükleyemez, ancak bir atama ifadesi tarafından gerçekleştirilebilecek özel tür dönüştürmeleri tanımlayabilir. Daha fazla bilgi için bkz. [Kullanıcı tanımlı dönüştürme işleçleri](user-defined-conversion-operators.md).

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
- [.NET 'teki genel türler](../../../standard/generics/index.md)
