---
title: Döküm ve tür dönüşümleri - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- type conversion [C#]
- data type conversion [C#]
- numeric conversions [C#]
- conversions [C#], type
- casting [C#]
- converting types [C#]
ms.assetid: 568df58a-d292-4b55-93ba-601578722878
ms.openlocfilehash: ae8f18deff5e96d7e475df8814ad64b38d14d585
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121385"
---
# <a name="casting-and-type-conversions-c-programming-guide"></a>Döküm ve tür dönüşümleri (C# Programlama Kılavuzu)

C# derleme zamanında statik olarak yazıldığı için, bir değişken beyan edildikten sonra, bu tür değişkenin türüne dolaylı olarak dönüştürülemediği sürece yeniden bildirilemez veya başka bir türe değer atanamaz. Örneğin, `string` örtülü olarak `int`. Bu nedenle, `i` bir `int`, aşağıdaki kodun gösterdiği gibi, "Merhaba" dizesini atayamazsınız:
  
```csharp  
int i;  
i = "Hello"; // error CS0029: Cannot implicitly convert type 'string' to 'int'
```  
  
 Ancak, bazen bir değeri başka bir türdeki bir değişken veya yöntem parametresine kopyalamanız gerekebilir. Örneğin, parametresi . olarak `double`yazılan bir yönteme geçirmeniz gereken bir tamsayı değişkenine sahip olabilirsiniz. Veya bir arabirim türünde bir değişkene bir sınıf değişkeni atamanız gerekebilir. Bu tür *işlemlere tür dönüştürmeleri*denir. C#'da aşağıdaki tür dönüşümleri gerçekleştirebilirsiniz:  
  
- **Örtülü dönüşümler**: Dönüştürme türü güvenli olduğundan ve veri kaybolmayacağından özel sözdizimi gerekmez. Örnekler arasında daha küçük integral türlerinden dönüşümler ve türemiş sınıflardan temel sınıflara dönüşümler yer almaktadır.  
  
- **Açık dönüşümler (dökümler)**: Açık dönüştürmeler [dökme ifade](../../language-reference/operators/type-testing-and-cast.md#cast-expression)gerektirir. Dönüştürmede bilgi kaybolabileceği veya dönüştürmenin başka nedenlerle başarılı olamayabileceği durumlarda döküm gereklidir. Tipik örnekler arasında daha az duyarlıklı veya daha küçük aralıklı bir türe sayısal dönüştürme ve taban sınıf örneği türemiş sınıfa dönüştürme sayılabilir.  
  
- **Kullanıcı tanımlı dönüşümler**: Kullanıcı tanımlı dönüşümler, taban sınıf türetilmiş sınıf ilişkisi olmayan özel türler arasında açık ve örtülü dönüşümleri etkinleştirmek için tanımlayabileceğiniz özel yöntemlerle gerçekleştirilir. Daha fazla bilgi için [Bkz. Kullanıcı tanımlı dönüşüm operatörleri.](../../language-reference/operators/user-defined-conversion-operators.md)  
  
- **Yardımcı sınıflı dönüşümler**: Tamsayılar ve nesneler veya heksadedemimal dizeleri <xref:System.DateTime?displayProperty=nameWithType> ve bayt dizileri gibi uyumsuz türler <xref:System.BitConverter?displayProperty=nameWithType> arasında <xref:System.Convert?displayProperty=nameWithType> dönüştürme yapmak `Parse` için sınıfı, sınıfı ve yerleşik sayısal <xref:System.Int32.Parse%2A?displayProperty=nameWithType>türlerin yöntemlerini kullanabilirsiniz. Daha fazla bilgi için, bir [bayt dizisini int'e nasıl dönüştüreceğiniz](./how-to-convert-a-byte-array-to-an-int.md), [bir dizeyi bir sayıya nasıl dönüştüreceğini](./how-to-convert-a-string-to-a-number.md)ve [hexadecimal dizeleri ile sayısal türleri arasında nasıl dönüştürüleceğini](./how-to-convert-between-hexadecimal-strings-and-numeric-types.md)öğrenin.
  
## <a name="implicit-conversions"></a>Örtülü dönüşümler

 Yerleşik sayısal türler için, depolanacak değer kesilmeden veya yuvarlatılmadan değişkene sığabildiği zaman örtülü bir dönüştürme yapılabilir. İntegral türleri için bu, kaynak türünün aralığının hedef türü için aralığın uygun bir alt kümesi olduğu anlamına gelir. Örneğin, tür [uzun](../../language-reference/builtin-types/integral-numeric-types.md) (64 bit tamsayı) bir değişken, bir [int](../../language-reference/builtin-types/integral-numeric-types.md) (32 bit tamsayı) depolayabilir herhangi bir değer saklayabilir. Aşağıdaki örnekte, derleyici, `num` `long` `bigNum`''yi atamadan önce sağdaki değeri dolaylı olarak bir türe dönüştürür.  
  
 [!code-csharp[csProgGuideTypes#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#34)]  
  
 Tüm örtülü sayısal dönüşümlerin tam listesi için, [Yerleşik sayısal dönüşümler](../../language-reference/builtin-types/numeric-conversions.md) makalesinin Örtülü sayısal [dönüşümler](../../language-reference/builtin-types/numeric-conversions.md#implicit-numeric-conversions) bölümüne bakın.
  
 Başvuru türleri için, örtülü dönüştürme her zaman bir sınıftan doğrudan veya dolaylı temel sınıflarından veya arabirimlerinden herhangi birine vardır. Türemiş bir sınıf her zaman bir taban sınıfın tüm üyelerini içerdiğinden özel sözdizimi gerekmez.  
  
```csharp
Derived d = new Derived();  
Base b = d; // Always OK.  
```  
  
## <a name="explicit-conversions"></a>Açık dönüşümler

 Ancak, bilgi kaybetme riski olmadan bir dönüşüm yapılamıyorsa, derleyici, *döküm*olarak adlandırılan açık bir dönüştürme gerçekleştirmenizi gerektirir. Döküm, derleyiciye dönüştürme yi yapmak istediğinizi ve veri kaybı olabileceğinin farkında olduğunuzu açıkça bildirmenin bir yoludur. Bir dökümü gerçekleştirmek için, dönüştürülecek değer veya değişkenin önündeki parantez içinde döküm türünü belirtin. Aşağıdaki program bir [int](../../language-reference/builtin-types/integral-numeric-types.md)için bir [çift](../../language-reference/builtin-types/floating-point-numeric-types.md) atar. Program döküm olmadan derlemek olmaz.  
  
 [!code-csharp[csProgGuideTypes#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#2)]  
  
 Desteklenen açık sayısal dönüşümlerin tam listesi için, [Yerleşik sayısal dönüşümler](../../language-reference/builtin-types/numeric-conversions.md) makalesinin Açık sayısal [dönüşümler](../../language-reference/builtin-types/numeric-conversions.md#explicit-numeric-conversions) bölümüne bakın.
  
 Başvuru türleri için, taban türden türemiş bir türe dönüştürmeniz gerekiyorsa, açık bir döküm gereklidir:  
  
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
  
 Başvuru türleri arasında bir döküm işlemi, temel nesnenin çalışma zamanı türünü değiştirmez; yalnızca o nesneye başvuru olarak kullanılan değerin türünü değiştirir. Daha fazla bilgi için [bkz.](../classes-and-structs/polymorphism.md)  
  
## <a name="type-conversion-exceptions-at-run-time"></a>Çalışma zamanında dönüşüm özel durumlarını yazın

 Bazı başvuru türü dönüşümlerinde derleyici, bir dökümün geçerli olup olmayacağını belirleyemez. Çalışma zamanında başarısız olmak için doğru derleyen bir döküm işlemi mümkündür. Aşağıdaki örnekte gösterildiği gibi, çalışma zamanında başarısız olan <xref:System.InvalidCastException> bir tür döküm bir atılmasına neden olur.  
  
 [!code-csharp[csProgGuideTypes#41](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#41)]  
  
 C# aslında bir döküm gerçekleştirmeden önce uyumluluk için test etmek için etkinleştirmek için [is](../../language-reference/operators/type-testing-and-cast.md#is-operator) işleci sağlar. Daha fazla bilgi için, [desen eşleştirme ve as ve operatörler kullanarak güvenli bir şekilde döküm nasıl](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md)bakın.  
  
## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Dönüşümler](~/_csharplang/spec/conversions.md) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Türler](./index.md)
- [Oyuncu ifadesi](../../language-reference/operators/type-testing-and-cast.md#cast-expression)
- [Kullanıcı tanımlı dönüştürme işleçleri](../../language-reference/operators/user-defined-conversion-operators.md)
- [Genelleşmiş Tür Dönüştürme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/yy580hbd(v=vs.120))
- [Bir dizeyi sayıya dönüştürme](./how-to-convert-a-string-to-a-number.md)
