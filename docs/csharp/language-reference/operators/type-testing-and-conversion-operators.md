---
title: Tür test etme ve dönüştürme işleçleri - C# başvurusu
description: Hakkında bilgi edinin C# bir ifadenin sonuç türü denetleyin ve gerekiyorsa, başka bir türe dönüştürmek için kullanabileceğiniz işleçler.
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
ms.openlocfilehash: 4468bc86634ad97f2dfbdb5f842eb5206f957a79
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/21/2019
ms.locfileid: "67307512"
---
# <a name="type-testing-and-conversion-operators-c-reference"></a>Tür test etme ve dönüştürme işleçleri (C# Başvurusu)

Tür dönüşümü veya tür denetimi gerçekleştirmek için aşağıdaki işleçleri kullanabilirsiniz:

- [Is işleci](#is-operator): bir ifade çalışma zamanı türünün belirli bir tür ile uyumlu olup olmadığını denetlemek için
- [işleci olarak](#as-operator): açıkça kendi çalışma zamanı türü bu tür ile uyumlu ise bir ifade belirli bir türe dönüştürmek için
- [atama işleci ()](#cast-operator-): açık bir dönüştürme gerçekleştirmek için
- [typeof işleci](#typeof-operator): edinme <xref:System.Type?displayProperty=nameWithType> bir tür örneği

## <a name="is-operator"></a>Is işleci

`is` İşleci bir ifade sonucu çalışma zamanı türü belirli bir tür ile uyumlu olup olmadığını denetler. İle başlayarak C# 7.0 `is` işleci bir ifade sonucunu belirli bir desene göre de test eder.

Tür testi ifadesiyle `is` işleci aşağıdaki biçime sahip

```csharp
E is T
```

Burada `E` değer döndüren bir ifadedir ve `T` bir türü veya tür parametresi adıdır. `E` Anonim bir yöntem veya lambda ifadesi olamaz.

`E is T` İfade döndürür `true` varsa sonucunu `E` null olmayan ve türüne dönüştürülebilir `T` başvuru dönüştürmesi, paketleme dönüştürmesi ya da bir kutudan çıkarma dönüştürme; Aksi halde döndürür `false`. `is` İşleci değil kullanıcı tanımlı dönüşümler düşünün.

Aşağıdaki örnek, gösterir `is` işleci döndürür `true` ifade sonucu çalışma zamanı türü belirtilen türünden türer, diğer bir deyişle, mevcut bir başvuru dönüştürmesi türler arasında:

[!code-csharp[is with reference conversion](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#IsWithReferenceConversion)]

Sonraki örnek, gösterir `is` işleci kutulama ve kutudan çıkarma dönüştürme dikkate alır ancak sayısal dönüşümler dikkate almaz:

[!code-csharp-interactive[is with int](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#IsWithInt)]

Hakkında bilgi için C# dönüştürmeleri bkz [dönüştürmeler](~/_csharplang/spec/conversions.md) bölüm [ C# dil belirtimi](~/_csharplang/spec/introduction.md).

### <a name="type-testing-with-pattern-matching"></a>Desen eşleştirme ile test türü

İle başlayarak C# 7.0 `is` işleci bir ifade sonucunu belirli bir desene göre de test eder. Özellikle, aşağıdaki biçimde türü desenini destekler:

```csharp
E is T v
```

Burada `E` bir değer döndüren bir ifadedir `T` bir türü veya tür parametresi, adıdır ve `v` türünde yeni bir yerel değişken `T`. Sonucu `E` null olmayan ve dönüştürülebilir `T` kutulama ve kutudan çıkarma, dönüştürme, bir başvuruya göre `E is T v` ifade döndürür `true` ve sonucu dönüştürülmüş değeri `E` atanır değişken `v`.

Aşağıdaki örnek, kullanımını gösterir. `is` işleç türü desen ile:

[!code-csharp-interactive[is with type pattern](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#IsTypePattern)]

Tür deseni ve diğer desteklenen desenler hakkında daha fazla bilgi için bkz. [deseni ile eşleşen](../keywords/is.md#pattern-matching-with-is).

## <a name="as-operator"></a>operatör olarak

`as` İşleci bir verilen başvuru veya null değer türü bir ifadenin sonucu açıkça dönüştürür. Dönüştürme mümkün değilse `as` işleci döndürür `null`. Farklı [atama işleci ()](#cast-operator-), `as` işleci hiçbir zaman bir özel durum oluşturur.

Formun ifadesi

```csharp
E as T
```

Burada `E` değer döndüren bir ifadedir ve `T` aynı sonucu üretir, bir türü veya tür parametresi adı

```csharp
E is T ? (T)(E) : (T)null
```

dışında `E` yalnızca bir kez değerlendirilir.

`as` İşleci, yalnızca başvuru null yapılabilir, kutulama ve kutudan çıkarma dönüştürme göz önünde bulundurur. Kullanamazsınız `as` kullanıcı tanımlı bir dönüştürme gerçekleştirmek için işleci. Bunu yapmak için kullanın [atama işleci ()](#cast-operator-).

Aşağıdaki örnek, kullanımını gösterir. `as` işleci:

[!code-csharp-interactive[as operator](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#AsOperator)]

> [!NOTE]
> Yukarıdaki örnekte gösterildiği gibi sonucunu karşılaştırmak gereken `as` ifadesiyle `null` dönüştürme başarılı olup olmadığını denetlemek için. İle başlayarak C# kullanabileceğiniz 7.0 [işleci](#type-testing-with-pattern-matching) yeni bir değişkene dönüştürme başarılı olursa ve başarılı olursa, test etmek için her ikisi de atama sonucu.

## <a name="cast-operator-"></a>Atama işleci (.)

Atama ifadesi formun `(T)E` ifadenin sonucu, açık bir dönüştürme gerçekleştiren `E` türüne `T`. Açık bir dönüştürme türünden varsa `E` türüne `T`, bir derleme zamanı hatası oluşur. Çalışma zamanında açık bir dönüştürme başarısız olabilir ve bir atama ifadesi bir özel durum fırlatabilir.

Aşağıdaki örnek, sayısal ve başvuru açık dönüştürmeler gösterir:

[!code-csharp-interactive[cast expression](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#Cast)]

Desteklenen açık dönüştürmeler hakkında daha fazla bilgi için bkz. [açık dönüştürmeler](~/_csharplang/spec/conversions.md#explicit-conversions) bölümünü [ C# dil belirtimi](~/_csharplang/spec/introduction.md). Bir özel açık veya örtük tür dönüştürme tanımlama hakkında daha fazla bilgi için bkz: [açık](../keywords/explicit.md) veya [örtük](../keywords/implicit.md) anahtar sözcüğü makalesi, sırasıyla.

### <a name="other-usages-of-"></a>()'nin diğer kullanımları

Parantez de [bir yöntemi çağırabilir veya bir temsilcinin çağırma](member-access-operators.md#invocation-operator-).

Diğer parantez işlemleri bir ifade Değerlendirme sırasını belirlemek için kullanılır. Daha fazla bilgi için [ayraç ekleme](../../programming-guide/statements-expressions-operators/operators.md#adding-parentheses) bölümünü [işleçleri](../../programming-guide/statements-expressions-operators/operators.md) makalesi. İşleçler, öncelik düzeyine göre sıralı listesi için bkz. [ C# işleçleri](index.md).

## <a name="typeof-operator"></a>typeof işleci

`typeof` İşleci alır <xref:System.Type?displayProperty=nameWithType> örneği için bir tür. Bağımsız değişkeninin `typeof` işleci, bir türü veya tür parametresi, adı aşağıdaki örnekte gösterildiği gibi olmalıdır:

[!code-csharp-interactive[typeof operator](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#TypeOf)]

Ayrıca `typeof` işleci ile ilişkisiz genel türler. İlişkisiz bir genel tür adı, türü parametre sayısı'den küçük bir virgül uygun bir sayı içermelidir. Aşağıdaki örnek, kullanımını gösterir. `typeof` ilişkisiz bir genel tür işleç:

[!code-csharp-interactive[typeof unbound generic](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#TypeOfUnboundGeneric)]

Bir ifade bir bağımsız değişkeni olamaz `typeof` işleci. Alınacak <xref:System.Type?displayProperty=nameWithType> kullan ifade sonucu çalışma zamanı türünün örneği <xref:System.Object.GetType%2A?displayProperty=nameWithType> yöntemi.

### <a name="type-testing-with-the-typeof-operator"></a>Testi türü `typeof` işleci

Kullanım `typeof` ifade sonucu çalışma zamanı türü verilen tür tam olarak eşleşip eşleşmediğini anlamak için işleci. Aşağıdaki örnek tür ile gerçekleştirilen denetimi arasındaki farkı gösterir `typeof` işleci ve [işleci](#is-operator):

[!code-csharp[typeof vs is](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#TypeCheckWithTypeOf)]

## <a name="operator-overloadability"></a>İşleç overloadability

`is`, `as`, Ve `typeof` işleçleri aşırı yüklenebilir değildir.

Kullanıcı tanımlı bir tür aşırı yüklenemez `()` işleci, ancak bir atama ifadesi tarafından gerçekleştirilen özel tür dönüştürmeler tanımlayabilirsiniz. Daha fazla bilgi için [açık](../keywords/explicit.md) ve [örtük](../keywords/implicit.md) anahtar sözcüğü makaleler.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için aşağıdaki bölümlere bakın [ C# dil belirtimi](~/_csharplang/spec/introduction.md):

- [Is işleci](~/_csharplang/spec/expressions.md#the-is-operator)
- [AS işleci](~/_csharplang/spec/expressions.md#the-as-operator)
- [Cast ifadeleri](~/_csharplang/spec/expressions.md#cast-expressions)
- [Typeof işleci](~/_csharplang/spec/expressions.md#the-typeof-operator)

## <a name="see-also"></a>Ayrıca bkz.

- [C#başvuru](../index.md)
- [C# işleçleri](index.md)
- [Nasıl yapılır: desen eşleştirme kullanarak güvenli bir şekilde noktaya yayın ve olduğu ve işleçler](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md)
