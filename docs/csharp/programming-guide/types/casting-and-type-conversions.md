---
title: Atama ve tür dönüştürmeleri-C# Programlama Kılavuzu
description: Örtük, Açık (yayınlar) ve Kullanıcı tanımlı dönüştürmeler gibi atama ve tür dönüştürmeleri hakkında bilgi edinin.
ms.date: 07/06/2020
helpviewer_keywords:
- type conversion [C#]
- data type conversion [C#]
- numeric conversions [C#]
- conversions [C#], type
- casting [C#]
- converting types [C#]
ms.assetid: 568df58a-d292-4b55-93ba-601578722878
ms.openlocfilehash: cfe5376675808559f4bf9c9cd8b21180dcd0cc49
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555334"
---
# <a name="casting-and-type-conversions-c-programming-guide"></a>Atama ve tür dönüşümleri (C# Programlama Kılavuzu)

C#, derleme zamanında statik olarak yazıldığı için, bir değişken bildirildiğinde, bu tür bir değişken türüne örtülü olarak dönüştürülemediği takdirde, yeniden bildirilemez veya başka bir türde bir değer atanamaz. Örneğin, `string` örtülü olarak öğesine dönüştürülemez `int` . Bu nedenle, bir olarak bildirdikten sonra `i` `int` , aşağıdaki kodda gösterildiği gibi, "Merhaba" dizesini buna atayamazsınız.

```csharp
int i;

// error CS0029: Cannot implicitly convert type 'string' to 'int'
i = "Hello";
```

Ancak bazen bir değeri başka bir türün değişken veya yöntem parametresine kopyalamanız gerekebilir. Örneğin, parametresi olarak yazılmış bir yönteme geçirmeniz gereken bir tamsayı değişkenine sahip olabilirsiniz `double` . Ya da bir arabirim türü değişkenine bir sınıf değişkeni atamanız gerekebilir. Bu tür işlemlere *tür dönüştürmeleri*denir. C# ' de, aşağıdaki tür dönüştürmeleri gerçekleştirebilirsiniz:

- **Örtük dönüştürmeler**: dönüştürme her zaman başarılı olduğundan ve hiçbir veri kaybolacağı için özel bir sözdizimi gerekli değildir. Örnekler, daha küçük integral türlerine ve türetilmiş sınıflardan taban sınıflara Dönüştürmelere dönüşümler içerir.

- **Açık dönüşümler (yayınlar)**: açık dönüştürmeler bir [atama ifadesi](../../language-reference/operators/type-testing-and-cast.md#cast-expression)gerektirir. Dönüştürme işlemi, dönüştürmede bilgiler kaybediliyorsa veya dönüştürme işleminin diğer nedenlerle başarısız olabileceği durumlarda gereklidir. Tipik örneklerde, daha az duyarlık veya daha küçük bir aralığa sahip olan bir türe sayısal dönüştürme ve bir temel sınıf örneğinin türetilmiş bir sınıfa dönüştürülmesi sayılabilir.

- **Kullanıcı tanımlı dönüştürmeler**: Kullanıcı tanımlı dönüştürmeler, temel sınıf ile türetilmiş sınıf ilişkisine sahip olmayan özel türler arasında açık ve örtük dönüştürmeleri etkinleştirmek için tanımlayabileceğiniz özel yöntemler tarafından gerçekleştirilir. Daha fazla bilgi için bkz. [Kullanıcı tanımlı dönüştürme işleçleri](../../language-reference/operators/user-defined-conversion-operators.md).

- **Yardımcı sınıflarla dönüşümler**: tamsayılar ve <xref:System.DateTime?displayProperty=nameWithType> nesneler ya da onaltılı dizeler ve bayt dizileri gibi uyumlu olmayan türler arasında dönüştürmek için <xref:System.BitConverter?displayProperty=nameWithType> sınıfı, <xref:System.Convert?displayProperty=nameWithType> sınıfı ve `Parse` gibi yerleşik sayısal türlerin yöntemlerini kullanabilirsiniz <xref:System.Int32.Parse%2A?displayProperty=nameWithType> . Daha fazla bilgi için bkz. [byte dizisini int 'e dönüştürme](./how-to-convert-a-byte-array-to-an-int.md), [bir dizeyi sayıya dönüştürme](./how-to-convert-a-string-to-a-number.md)ve [onaltılık dizeler ve sayısal türler arasında dönüştürme](./how-to-convert-between-hexadecimal-strings-and-numeric-types.md).

## <a name="implicit-conversions"></a>Örtük dönüştürmeler

Yerleşik sayısal türler için, saklanacak değer kesilmeden veya yuvarlanmadan değişkene sığmayacak olan örtük bir dönüştürme yapılabilir. İntegral türleri için bu, kaynak türü aralığının hedef tür için uygun bir alt küme olduğu anlamına gelir. Örneğin, [Long](../../language-reference/builtin-types/integral-numeric-types.md) (64-bit tamsayı) türünde bir değişken, bir [int](../../language-reference/builtin-types/integral-numeric-types.md) (32 bit tamsayı) depolayabileceği herhangi bir değeri depolayabilirler. Aşağıdaki örnekte, derleyici `num` öğesine atamadan önce değeri örtük olarak bir türe dönüştürür `long` `bigNum` .

[!code-csharp[csProgGuideTypes#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#34)]

Tüm örtük sayısal dönüştürmelerin tam listesi için, [yerleşik sayısal](../../language-reference/builtin-types/numeric-conversions.md) dönüşümler makalesinin [Örtük Sayısal Dönüşümler](../../language-reference/builtin-types/numeric-conversions.md#implicit-numeric-conversions) bölümüne bakın.

Başvuru türleri için, örtük bir dönüştürme her zaman bir sınıftan doğrudan veya dolaylı temel sınıflarından veya arabirimlerinden herhangi birine bulunur. Türetilmiş bir sınıf her zaman bir temel sınıfın tüm üyelerini içerdiğinden özel bir sözdizimi gerekli değildir.

```csharp
Derived d = new Derived();

// Always OK.
Base b = d;
```

## <a name="explicit-conversions"></a>Açık dönüşümler

Ancak, bilgileri kaybetme riski olmadan bir dönüştürme gerçekleştirilemez, derleyici *bir dönüştürme olarak*adlandırılan açık bir dönüştürme gerçekleştirmenizi gerektirir. Bir dönüştürme, dönüştürmeyi yapmayı düşündüğünüz ve veri kaybını ortaya çıkardığınızı veya çalışma zamanında başarısız olabileceğini fark eden derleyicinin açıkça bilgilendirmesinin bir yoludur. Bir tür dönüştürme gerçekleştirmek için, dönüştürülecek değeri veya değişkeni önünde parantez içinde içine, dönüştürmekte olduğunuz türü belirtin. Aşağıdaki program bir Double öğesine bir [Double](../../language-reference/builtin-types/floating-point-numeric-types.md) yayınlar [.](../../language-reference/builtin-types/integral-numeric-types.md) Program, atama olmadan derlenmeyecektir.

[!code-csharp[csProgGuideTypes#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#2)]

Desteklenen açık sayısal dönüştürmelerin tam listesi için [yerleşik sayısal](../../language-reference/builtin-types/numeric-conversions.md) dönüşümler konusunun [Açık Sayısal Dönüşümler](../../language-reference/builtin-types/numeric-conversions.md#explicit-numeric-conversions) bölümüne bakın.

Başvuru türleri için bir temel türden türetilmiş bir türe dönüştürmeniz gerekiyorsa açık bir atama gerekir:

```csharp
// Create a new derived type.
Giraffe g = new Giraffe();

// Implicit conversion to base type is safe.
Animal a = g;

// Explicit conversion is required to cast back
// to derived type. Note: This will compile but will
// throw an exception at run time if the right-side
// object is not in fact a Giraffe.
Giraffe g2 = (Giraffe)a;
```

Başvuru türleri arasındaki bir atama işlemi, temel alınan nesnenin çalışma zamanı türünü değiştirmez; yalnızca bu nesneye başvuru olarak kullanılan değerin türünü değiştirir. Daha fazla bilgi için bkz. çok [biçimlilik](../classes-and-structs/polymorphism.md).

## <a name="type-conversion-exceptions-at-run-time"></a>Çalışma zamanında dönüştürme özel durumlarını yazın

Bazı başvuru türü dönüştürmelerinde, derleyici bir dönüştürmenin geçerli olup olmayacağını belirleyemez. Çalışma zamanında düzgün şekilde derlenen bir atama işlemi mümkündür. Aşağıdaki örnekte gösterildiği gibi, çalışma zamanında başarısız olan bir tür dönüştürme bir oluşturulmasına neden olur <xref:System.InvalidCastException> .

[!code-csharp[csProgGuideTypes#41](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#41)]

`Test`Yönteminde bir parametre bulunur `Animal` , bu nedenle bağımsız değişkeni açıkça `a` bir ' a atamak tehlikeli bir `Reptile` varsayımına neden olur. Varsayımın olmaması daha güvenlidir, ancak türü kontrol edin. C#, bir dönüştürmeyi gerçekten yapmadan önce uyumluluğun test etmeniz için [,](../../language-reference/operators/type-testing-and-cast.md#is-operator) . Daha fazla bilgi için bkz. [model eşleştirme ve as ve işleç işleçlerini kullanarak güvenle atama](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md).

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [dönüşümler](~/_csharplang/spec/conversions.md) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Türler](./index.md)
- [Atama ifadesi](../../language-reference/operators/type-testing-and-cast.md#cast-expression)
- [Kullanıcı tanımlı dönüştürme işleçleri](../../language-reference/operators/user-defined-conversion-operators.md)
- [Genelleşmiş Tür Dönüştürme](/previous-versions/visualstudio/visual-studio-2013/yy580hbd(v=vs.120))
- [Bir dizeyi sayıya dönüştürme](./how-to-convert-a-string-to-a-number.md)
