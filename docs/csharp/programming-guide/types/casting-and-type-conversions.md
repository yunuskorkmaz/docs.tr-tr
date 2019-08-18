---
title: Atama ve tür dönüşümleri- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- type conversion [C#]
- data type conversion [C#]
- numeric conversions [C#]
- conversions [C#], type
- casting [C#]
- converting types [C#]
ms.assetid: 568df58a-d292-4b55-93ba-601578722878
ms.openlocfilehash: 2ec18f9afed04882f26b5d2f34f64c25be042ed5
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/17/2019
ms.locfileid: "69566870"
---
# <a name="casting-and-type-conversions-c-programming-guide"></a>Atama ve tür dönüşümleri (C# Programlama Kılavuzu)

C# , Derleme zamanında statik olarak yazıldığı için, bir değişken oluşturulduktan sonra yeniden bildirilemez veya tür değişken türüne örtük olarak dönüştürülemediği takdirde başka bir türde bir değer atanamaz. Örneğin `string` , örtülü olarak öğesine `int`dönüştürülemez. Bu nedenle, bir `i` `int`olarak bildirdikten sonra, aşağıdaki kodda gösterildiği gibi, "Merhaba" dizesini buna atayamazsınız.
  
```csharp  
int i;  
i = "Hello"; // error CS0029: Cannot implicitly convert type 'string' to 'int'
```  
  
 Ancak bazen bir değeri başka bir türün değişken veya yöntem parametresine kopyalamanız gerekebilir. Örneğin, parametresi olarak `double`yazılmış bir yönteme geçirmeniz gereken bir tamsayı değişkenine sahip olabilirsiniz. Ya da bir arabirim türü değişkenine bir sınıf değişkeni atamanız gerekebilir. Bu tür işlemlere *tür dönüştürmeleri*denir. ' C#De, aşağıdaki tür dönüştürmeleri gerçekleştirebilirsiniz:  
  
- **Örtük dönüştürmeler**: Dönüştürme türü güvenli olduğundan ve hiçbir veri kaybolacağı için özel bir sözdizimi gerekmez. Örnekler, daha küçük integral türlerine ve türetilmiş sınıflardan taban sınıflara Dönüştürmelere dönüşümler içerir.  
  
- **Açık dönüştürmeler (yayınlar)** : Açık dönüşümler bir atama işleci gerektirir. Dönüştürme işlemi, dönüştürmede bilgiler kaybediliyorsa veya dönüştürme işleminin diğer nedenlerle başarısız olabileceği durumlarda gereklidir.  Tipik örneklerde, daha az duyarlık veya daha küçük bir aralığa sahip olan bir türe sayısal dönüştürme ve bir temel sınıf örneğinin türetilmiş bir sınıfa dönüştürülmesi sayılabilir.  
  
- **Kullanıcı tanımlı dönüştürmeler**: Kullanıcı tanımlı dönüştürmeler, temel sınıf ile türetilmiş sınıf ilişkisine sahip olmayan özel türler arasında açık ve örtük dönüştürmeleri etkinleştirmek için tanımlayabileceğiniz özel yöntemler tarafından gerçekleştirilir. Daha fazla bilgi için bkz. [Kullanıcı tanımlı dönüştürme işleçleri](../../../csharp/language-reference/operators/user-defined-conversion-operators.md).  
  
- **Yardımcı sınıflarla dönüşümler**: Tamsayılar ve <xref:System.DateTime?displayProperty=nameWithType> nesneler ya da onaltılı dizeler ve bayt dizileri gibi uyumlu olmayan türler arasında dönüştürme yapmak için, <xref:System.BitConverter?displayProperty=nameWithType> sınıfı, <xref:System.Convert?displayProperty=nameWithType> sınıfı ve `Parse` yerleşik sayısal türlerin yöntemlerini (örneğin,) kullanabilirsiniz. <xref:System.Int32.Parse%2A?displayProperty=nameWithType>. Daha fazla bilgi için [nasıl yapılır: Bir Byte dizisini int](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md)'e dönüştürme, [nasıl yapılır: Bir dizeyi sayıya](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md)dönüştürün ve [şunları yapın: Onaltılık dizeler ve sayısal türler](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md)arasında dönüştürme.  
  
## <a name="implicit-conversions"></a>Örtük dönüştürmeler

 Yerleşik sayısal türler için, saklanacak değer kesilmeden veya yuvarlanmadan değişkene sığmayacak olan örtük bir dönüştürme yapılabilir. İntegral türleri için bu, kaynak türü aralığının hedef tür için uygun bir alt küme olduğu anlamına gelir. Örneğin, [Long](../../../csharp/language-reference/builtin-types/integral-numeric-types.md) (64-bit tamsayı) türünde bir değişken, bir [int](../../../csharp/language-reference/builtin-types/integral-numeric-types.md) (32 bit tamsayı) depolayabileceği herhangi bir değeri depolayabilirler. Aşağıdaki örnekte, derleyici öğesine `num` `bigNum`atamadan önce değeri örtük olarak bir türe `long` dönüştürür.  
  
 [!code-csharp[csProgGuideTypes#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#34)]  
  
 Tüm örtük sayısal dönüştürmelerin tüm listesi için bkz. [örtük sayısal dönüştürmeler tablosu](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).  
  
 Başvuru türleri için, örtük bir dönüştürme her zaman bir sınıftan doğrudan veya dolaylı temel sınıflarından veya arabirimlerinden herhangi birine bulunur. Türetilmiş bir sınıf her zaman bir temel sınıfın tüm üyelerini içerdiğinden özel bir sözdizimi gerekli değildir.  
  
```csharp
Derived d = new Derived();  
Base b = d; // Always OK.  
```  
  
## <a name="explicit-conversions"></a>Açık dönüşümler

 Ancak, bilgileri kaybetme riski olmadan bir dönüştürme gerçekleştirilemez, derleyici bir dönüştürme olarak adlandırılan açık bir dönüştürme gerçekleştirmenizi gerektirir. Bir atama, dönüştürmeyi yapmayı düşündüğünüz ve veri kaybını fark ettiğini farkında olabileceğiniz derleyicisini açıkça bildiren bir yoldur. Bir tür dönüştürme gerçekleştirmek için, dönüştürülecek değeri veya değişkeni önünde parantez içinde içine, dönüştürmekte olduğunuz türü belirtin. Aşağıdaki program bir Double öğesine bir [Double](../../../csharp/language-reference/builtin-types/floating-point-numeric-types.md) yayınlar [](../../../csharp/language-reference/builtin-types/integral-numeric-types.md). Program, atama olmadan derlenmeyecektir.  
  
 [!code-csharp[csProgGuideTypes#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#2)]  
  
 İzin verilen açık sayısal dönüşümler listesi için bkz. [Açık Sayısal Dönüşümler Tablosu](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md).  
  
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
  
 Başvuru türleri arasındaki bir atama işlemi, temel alınan nesnenin çalışma zamanı türünü değiştirmez; yalnızca bu nesneye başvuru olarak kullanılan değerin türünü değiştirir. Daha fazla bilgi için bkz. çok [biçimlilik](../../../csharp/programming-guide/classes-and-structs/polymorphism.md).  
  
## <a name="type-conversion-exceptions-at-run-time"></a>Çalışma zamanında dönüştürme özel durumlarını yazın

 Bazı başvuru türü dönüştürmelerinde, derleyici bir dönüştürmenin geçerli olup olmayacağını belirleyemez. Çalışma zamanında düzgün şekilde derlenen bir atama işlemi mümkündür. Aşağıdaki örnekte gösterildiği gibi, çalışma zamanında başarısız olan bir tür dönüştürme bir <xref:System.InvalidCastException> oluşturulmasına neden olur.  
  
 [!code-csharp[csProgGuideTypes#41](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#41)]  
  
 C#, gerçekten bir dönüştürme yapmadan önce uyumluluğu test etmeniz için [,](../../language-reference/operators/type-testing-and-cast.md#is-operator) . işlecini sağlar. Daha fazla bilgi için bkz. [nasıl yapılır: model eşleştirme ve as ve işleç işleçlerini kullanarak güvenle atama](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md).  
  
## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [dönüşümler](~/_csharplang/spec/conversions.md) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [Türler](../../../csharp/programming-guide/types/index.md)
- [() Cast işleci](../../../csharp/language-reference/operators/type-testing-and-cast.md#cast-operator-)
- [Kullanıcı tanımlı dönüştürme işleçleri](../../../csharp/language-reference/operators/user-defined-conversion-operators.md)
- [Genelleştirilmiş tür dönüştürmesi](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/yy580hbd(v=vs.120))
- [Nasıl yapılır: Bir dizeyi sayıya Dönüştür](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md)
