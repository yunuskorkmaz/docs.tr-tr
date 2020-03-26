---
title: Tip-test ve döküm operatörleri - C# referans
description: İfade sonucunun türünü denetlemek ve gerekirse başka bir türe dönüştürmek için kullanabileceğiniz C# işleçleri hakkında bilgi edinin.
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
ms.openlocfilehash: 2dc215a91c55be15e8eee488f0030f41e3492af5
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79507093"
---
# <a name="type-testing-and-cast-operators-c-reference"></a>Tip-test ve döküm operatörleri (C# referansı)

Tür denetimi veya tür dönüştürme gerçekleştirmek için aşağıdaki işleçleri kullanabilirsiniz:

- [is operator](#is-operator): bir ifadenin çalışma zamanı türünün belirli bir türle uyumlu olup olmadığını kontrol etmek için
- [olarak işleç](#as-operator): çalışma zamanı türü bu türle uyumluysa, bir ifadeyi açıkça belirli bir türe dönüştürmek için
- [döküm operatörü ()](#cast-operator-): açık bir dönüştürme gerçekleştirmek için
- [typeof operator](#typeof-operator): <xref:System.Type?displayProperty=nameWithType> bir tür için örnek elde etmek için

## <a name="is-operator"></a>işleç

İşleç, `is` bir ifade sonucunun çalışma zamanı türünün belirli bir türle uyumlu olup olmadığını denetler. C# 7.0 ile `is` başlayarak, işleç de bir desen karşı bir ifade sonucu test eder.

Tür test `is` işleci ile ifade aşağıdaki formu vardır

```csharp
E is T
```

nerede `E` bir değer döndürür `T` ve bir tür veya tür parametre adı olan bir ifadedir. `E`anonim bir yöntem veya lambda ifade olamaz.

Sonuç `E is T` null'suz `true` `E` ise ve bir başvuru dönüştürme, bir `T` kutulama dönüştürme veya unboxing dönüştürme tarafından türe dönüştürülebilir ifade döndürür; aksi takdirde, `false`döner . Operatör `is` kullanıcı tanımlı dönüşümleri dikkate almaz.

Aşağıdaki örnek, bir `is` ifade `true` sonucunun çalışma zamanı türü belirli bir türden türemişse işlecinin geri döndüğünü, yani türler arasında bir başvuru dönüştürmesi olduğunu gösterir:

[!code-csharp[is with reference conversion](snippets/TypeTestingAndConversionOperators.cs#IsWithReferenceConversion)]

Sonraki örnek, `is` işleç dikkate boks ve unboxing dönüşümleri alır ama sayısal [dönüşümleri](../builtin-types/numeric-conversions.md)dikkate almaz gösterir:

[!code-csharp-interactive[is with int](snippets/TypeTestingAndConversionOperators.cs#IsWithInt)]

C# dönüşümleri hakkında bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Dönüşümler](~/_csharplang/spec/conversions.md) bölümüne bakın.

### <a name="type-testing-with-pattern-matching"></a>Desen eşleştirmeli tür testi

C# 7.0 ile `is` başlayarak, işleç de bir desen karşı bir ifade sonucu test eder. Özellikle, aşağıdaki formda tür deseni destekler:

```csharp
E is T v
```

nerede `E` bir değer döndürür `T` bir ifade, bir tür veya tür `v` parametre adıdır `T`ve tür yeni bir yerel değişkendir . Sonucu `E` null olmayan ve bir referans, kutulama veya unboxing dönüştürme `T` tarafından dönüştürülebilir, `E is T v` ifade döndürür `true` ve `E` sonucudönüştürülen `v`değeri değişkene atanır.

Aşağıdaki örnek, `is` tür deseni ile işlecinin kullanımını gösterir:

[!code-csharp-interactive[is with type pattern](snippets/TypeTestingAndConversionOperators.cs#IsTypePattern)]

Tür deseni ve diğer desteklenen desenler hakkında daha fazla bilgi için [bkz.](../keywords/is.md#pattern-matching-with-is)

## <a name="as-operator"></a>operatör olarak

İşleç, `as` bir ifadenin sonucunu açıkça belirli bir başvuru veya nullable değer türüne dönüştürür. Dönüştürme mümkün değilse, `as` işleç `null`döndürür. Döküm [işlecinin ()](#cast-operator-)aksine, `as` operatör hiçbir zaman bir özel durum atmaz.

Formun ifadesi

```csharp
E as T
```

bir `E` değer döndüren ve `T` bir tür veya tür parametresinin adı olan bir ifade, aynı sonucu

```csharp
E is T ? (T)(E) : (T)null
```

`E` bunun dışında sadece bir kez değerlendirilir.

İşletici `as` yalnızca başvuru, nullable, boxing ve unboxing dönüşümleri dikkate alır. Kullanıcı tanımlı `as` bir dönüştürme gerçekleştirmek için işleci kullanamazsınız. Bunu yapmak [için, döküm işleci ()](#cast-operator-)kullanın.

Aşağıdaki örnek, işleç `as` kullanımını gösterir:

[!code-csharp-interactive[as operator](snippets/TypeTestingAndConversionOperators.cs#AsOperator)]

> [!NOTE]
> Önceki örnekte de görüldüğü gibi, dönüştürmenin `as` başarılı `null` olup olmadığını denetlemek için ifadenin sonucunu karşılaştırmanız gerekir. C# 7.0 ile başlayarak, hem dönüştürmenin başarılı olup olmadığını sınamak için [is işlecini](#type-testing-with-pattern-matching) kullanabilir ve başarılı olursa sonucunu yeni bir değişkene atayabilirsiniz.

## <a name="cast-operator-"></a>Dökme operatör ()

Formun `(T)E` döküm ifadesi, ifade `E` sonucunun türe `T`açık bir şekilde dönüştürülmesini gerçekleştirir. Tür `E` `T`türünden açık bir dönüştürme yoksa derleme zamanı hatası oluşur. Çalışma zamanında, açık bir dönüştürme başarılı olmayabilir ve bir döküm ifadesi bir özel durum atabilir.

Aşağıdaki örnek, açık sayısal ve başvuru dönüşümlerini gösterir:

[!code-csharp-interactive[cast expression](snippets/TypeTestingAndConversionOperators.cs#Cast)]

Desteklenen açık dönüşümler hakkında bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Açık dönüşümler](~/_csharplang/spec/conversions.md#explicit-conversions) bölümüne bakın. Özel bir açık veya örtülü tür dönüştürmesinin nasıl tanımlanaaçık olduğu hakkında bilgi için [Bkz. Kullanıcı tanımlı dönüştürme operatörleri.](user-defined-conversion-operators.md)

### <a name="other-usages-of-"></a>Diğer kullanımları ()

Bir [yöntemi çağırmak veya bir temsilci çağırmak](member-access-operators.md#invocation-expression-)için parantez de kullanıyorsunuz.

Parantezin diğer kullanımı, bir ifadedeki işlemleri değerlendirmek için sırasını ayarlamaktır. Daha fazla bilgi için [C# işleçleri'ne](index.md)bakın.

## <a name="typeof-operator"></a>typeof işleci

İşleç `typeof` bir <xref:System.Type?displayProperty=nameWithType> tür için örnek alır. Aşağıdaki örnekte `typeof` görüldüğü gibi, işlecibağımsız değişkenbir tür veya tür parametresi adı olmalıdır:

[!code-csharp-interactive[typeof operator](snippets/TypeTestingAndConversionOperators.cs#TypeOf)]

İşleç'i `typeof` bağlı olmayan genel türleri ile de kullanabilirsiniz. Bağlanmamış genel türün adı, tür parametreleri sayısından bir küçük olan uygun sayıda virgül içermelidir. Aşağıdaki örnek, `typeof` bağlı olmayan genel türü olan işleç kullanımını gösterir:

[!code-csharp-interactive[typeof unbound generic](snippets/TypeTestingAndConversionOperators.cs#TypeOfUnboundGeneric)]

Bir ifade işlecinin `typeof` bir bağımsız değişkeni olamaz. İfade sonucunun <xref:System.Type?displayProperty=nameWithType> çalışma zamanı türünü almak için <xref:System.Object.GetType%2A?displayProperty=nameWithType> yöntemi kullanın.

### <a name="type-testing-with-the-typeof-operator"></a>`typeof` Operatörle tip testi

İfade `typeof` sonucunun çalışma zamanı türünün belirli bir türle tam olarak eşleşip eşleşmeyemeyişmasını denetlemek için işleci kullanın. Aşağıdaki örnek, `typeof` işleç ile gerçekleştirilen tür denetimi ile [İşletici](#is-operator)arasındaki farkı gösterir:

[!code-csharp[typeof vs is](snippets/TypeTestingAndConversionOperators.cs#TypeCheckWithTypeOf)]

## <a name="operator-overloadability"></a>Operatör aşırı yüklenebilirlik

`is`, `as`ve `typeof` işleçler aşırı yüklenemez.

Kullanıcı tanımlı bir tür `()` işleç aşırı yükleyemez, ancak döküm ifadesi tarafından gerçekleştirilebilecek özel tür dönüşümleri tanımlayabilir. Daha fazla bilgi için [Bkz. Kullanıcı tanımlı dönüşüm operatörleri.](user-defined-conversion-operators.md)

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:

- [Is işleci](~/_csharplang/spec/expressions.md#the-is-operator)
- [As operatörü](~/_csharplang/spec/expressions.md#the-as-operator)
- [Döküm ifadeler](~/_csharplang/spec/expressions.md#cast-expressions)
- [Operatör türü](~/_csharplang/spec/expressions.md#the-typeof-operator)

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# işleçleri](index.md)
- [Desen eşleştirme ve is ve operatörler olarak kullanarak güvenli bir şekilde döküm nasıl](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md)
- [.NET içindeki Genel Türler](../../../standard/generics/index.md)
