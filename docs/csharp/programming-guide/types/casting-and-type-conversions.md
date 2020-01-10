---
title: Atama ve tür dönüşümleri- C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- type conversion [C#]
- data type conversion [C#]
- numeric conversions [C#]
- conversions [C#], type
- casting [C#]
- converting types [C#]
ms.assetid: 568df58a-d292-4b55-93ba-601578722878
ms.openlocfilehash: 252d509617ab5dbc53b282bac52e356396d82fab
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711902"
---
# <a name="casting-and-type-conversions-c-programming-guide"></a>Atama ve tür dönüşümleri (C# Programlama Kılavuzu)

C# , Derleme zamanında statik olarak yazıldığı için, bir değişken oluşturulduktan sonra yeniden bildirilemez veya tür değişken türüne örtük olarak dönüştürülemediği takdirde başka bir türde bir değer atanamaz. Örneğin, `string` örtülü olarak `int`dönüştürülemez. Bu nedenle, `i` `int`olarak bildirdikten sonra, aşağıdaki kodda gösterildiği gibi, "Merhaba" dizesini buna atayamazsınız:
  
```csharp  
int i;  
i = "Hello"; // error CS0029: Cannot implicitly convert type 'string' to 'int'
```  
  
 Ancak bazen bir değeri başka bir türün değişken veya yöntem parametresine kopyalamanız gerekebilir. Örneğin, parametresi `double`olarak yazılan bir yönteme geçirmeniz gereken bir tamsayı değişkenine sahip olabilirsiniz. Ya da bir arabirim türü değişkenine bir sınıf değişkeni atamanız gerekebilir. Bu tür işlemlere *tür dönüştürmeleri*denir. ' C#De, aşağıdaki tür dönüştürmeleri gerçekleştirebilirsiniz:  
  
- **Örtük dönüştürmeler**: dönüştürme türü güvenli olduğundan ve hiçbir veri kaybolacağı için özel bir sözdizimi gerekli değildir. Örnekler, daha küçük integral türlerine ve türetilmiş sınıflardan taban sınıflara Dönüştürmelere dönüşümler içerir.  
  
- **Açık dönüşümler (yayınlar)** : açık dönüşümler [`()`atama işleci ](../../language-reference/operators/type-testing-and-cast.md#cast-operator-)gerektirir. Dönüştürme işlemi, dönüştürmede bilgiler kaybediliyorsa veya dönüştürme işleminin diğer nedenlerle başarısız olabileceği durumlarda gereklidir. Tipik örneklerde, daha az duyarlık veya daha küçük bir aralığa sahip olan bir türe sayısal dönüştürme ve bir temel sınıf örneğinin türetilmiş bir sınıfa dönüştürülmesi sayılabilir.  
  
- **Kullanıcı tanımlı dönüştürmeler**: Kullanıcı tanımlı dönüştürmeler, temel sınıf ile türetilmiş sınıf ilişkisine sahip olmayan özel türler arasında açık ve örtük dönüştürmeleri etkinleştirmek için tanımlayabileceğiniz özel yöntemler tarafından gerçekleştirilir. Daha fazla bilgi için bkz. [Kullanıcı tanımlı dönüştürme işleçleri](../../language-reference/operators/user-defined-conversion-operators.md).  
  
- **Yardımcı sınıflarla dönüşümler**: tamsayılar ve <xref:System.DateTime?displayProperty=nameWithType> nesneleri ya da onaltılı dizeler ve bayt dizileri gibi uyumlu olmayan türler arasında dönüştürme yapmak için <xref:System.BitConverter?displayProperty=nameWithType> sınıfını, <xref:System.Convert?displayProperty=nameWithType> sınıfını ve <xref:System.Int32.Parse%2A?displayProperty=nameWithType>gibi yerleşik sayısal türlerin `Parse` yöntemlerini kullanabilirsiniz. Daha fazla bilgi için bkz. [byte dizisini int 'e dönüştürme](./how-to-convert-a-byte-array-to-an-int.md), [bir dizeyi sayıya dönüştürme](./how-to-convert-a-string-to-a-number.md)ve [onaltılık dizeler ve sayısal türler arasında dönüştürme](./how-to-convert-between-hexadecimal-strings-and-numeric-types.md).
  
## <a name="implicit-conversions"></a>Örtük dönüştürmeler

 Yerleşik sayısal türler için, saklanacak değer kesilmeden veya yuvarlanmadan değişkene sığmayacak olan örtük bir dönüştürme yapılabilir. İntegral türleri için bu, kaynak türü aralığının hedef tür için uygun bir alt küme olduğu anlamına gelir. Örneğin, [Long](../../language-reference/builtin-types/integral-numeric-types.md) (64-bit tamsayı) türünde bir değişken, bir [int](../../language-reference/builtin-types/integral-numeric-types.md) (32 bit tamsayı) depolayabileceği herhangi bir değeri depolayabilirler. Aşağıdaki örnekte, derleyici `bigNum`atamak için, sağdaki `num` değerini örtülü olarak bir tür `long` dönüştürür.  
  
 [!code-csharp[csProgGuideTypes#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#34)]  
  
 Tüm örtük sayısal dönüştürmelerin tam listesi için, [yerleşik sayısal](../../language-reference/builtin-types/numeric-conversions.md) dönüşümler makalesinin [Örtük Sayısal Dönüşümler](../../language-reference/builtin-types/numeric-conversions.md#implicit-numeric-conversions) bölümüne bakın.
  
 Başvuru türleri için, örtük bir dönüştürme her zaman bir sınıftan doğrudan veya dolaylı temel sınıflarından veya arabirimlerinden herhangi birine bulunur. Türetilmiş bir sınıf her zaman bir temel sınıfın tüm üyelerini içerdiğinden özel bir sözdizimi gerekli değildir.  
  
```csharp
Derived d = new Derived();  
Base b = d; // Always OK.  
```  
  
## <a name="explicit-conversions"></a>Açık dönüşümler

 Ancak, bilgileri kaybetme riski olmadan bir dönüştürme gerçekleştirilemez, derleyici *bir dönüştürme olarak*adlandırılan açık bir dönüştürme gerçekleştirmenizi gerektirir. Bir atama, dönüştürmeyi yapmayı düşündüğünüz ve veri kaybını fark ettiğini farkında olabileceğiniz derleyicisini açıkça bildiren bir yoldur. Bir tür dönüştürme gerçekleştirmek için, dönüştürülecek değeri veya değişkeni önünde parantez içinde içine, dönüştürmekte olduğunuz türü belirtin. Aşağıdaki program bir Double öğesine bir [Double](../../language-reference/builtin-types/floating-point-numeric-types.md) yayınlar [.](../../language-reference/builtin-types/integral-numeric-types.md) Program, atama olmadan derlenmeyecektir.  
  
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
Giraffe g2 = (Giraffe) a;  
```  
  
 Başvuru türleri arasındaki bir atama işlemi, temel alınan nesnenin çalışma zamanı türünü değiştirmez; yalnızca bu nesneye başvuru olarak kullanılan değerin türünü değiştirir. Daha fazla bilgi için bkz. çok [biçimlilik](../classes-and-structs/polymorphism.md).  
  
## <a name="type-conversion-exceptions-at-run-time"></a>Çalışma zamanında dönüştürme özel durumlarını yazın

 Bazı başvuru türü dönüştürmelerinde, derleyici bir dönüştürmenin geçerli olup olmayacağını belirleyemez. Çalışma zamanında düzgün şekilde derlenen bir atama işlemi mümkündür. Aşağıdaki örnekte gösterildiği gibi, çalışma zamanında başarısız olan bir tür dönüştürme bir <xref:System.InvalidCastException> oluşturulmasına neden olur.  
  
 [!code-csharp[csProgGuideTypes#41](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#41)]  
  
 C#, gerçekten bir dönüştürme yapmadan önce uyumluluğu test etmeniz için [,](../../language-reference/operators/type-testing-and-cast.md#is-operator) . işlecini sağlar. Daha fazla bilgi için bkz. [model eşleştirme ve as ve işleç işleçlerini kullanarak güvenle atama](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md).  
  
## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [dönüşümler](~/_csharplang/spec/conversions.md) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Türler](./index.md)
- [() Cast işleci](../../language-reference/operators/type-testing-and-cast.md#cast-operator-)
- [Kullanıcı tanımlı dönüştürme işleçleri](../../language-reference/operators/user-defined-conversion-operators.md)
- [Genelleştirilmiş tür dönüştürmesi](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/yy580hbd(v=vs.120))
- [Bir dizeyi sayıya dönüştürme](./how-to-convert-a-string-to-a-number.md)
