---
title: Operator Deyimi
ms.date: 07/20/2015
f1_keywords:
- vb.operator
helpviewer_keywords:
- operators [Visual Basic]
- procedures [Visual Basic], operator
- Narrowing keyword [Visual Basic], conversion operators
- Visual Basic code, operators
- Widening keyword [Visual Basic], conversion operators
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- overloaded operators [Visual Basic]
- operator overloading
- operator procedures
- Operator statement [Visual Basic]
- CType function [Visual Basic], Operator statement
ms.assetid: b12ec4af-1ad7-4a17-865b-c5ee96320ae5
ms.openlocfilehash: f9e6ffe5a49715592399321ab471d73826e05d8e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404401"
---
# <a name="operator-statement"></a>Operator Deyimi

Bir sınıf veya yapıda operatör yordamını tanımlayan işleç sembolünü, işlenenleri ve kodu bildirir.

## <a name="syntax"></a>Sözdizimi

```vb
[ <attrlist> ] Public [ Overloads ] Shared [ Shadows ] [ Widening | Narrowing ]
Operator operatorsymbol ( operand1 [, operand2 ]) [ As [ <attrlist> ] type ]
    [ statements ]
    [ statements ]
    Return returnvalue
    [ statements ]
End Operator
```

## <a name="parts"></a>Bölümler

`attrlist`  
İsteğe bağlı. Bkz. [öznitelik listesi](attribute-list.md).

`Public`  
Gereklidir. Bu işleç yordamının [ortak](../modifiers/public.md) erişime sahip olduğunu gösterir.

`Overloads`  
İsteğe bağlı. Bkz. [aşırı yüklemeler](../modifiers/overloads.md).

`Shared`  
Gereklidir. Bu işleç yordamının [paylaşılan](../modifiers/shared.md) bir yordam olduğunu gösterir.

`Shadows`  
İsteğe bağlı. Bkz. [gölgeler](../modifiers/shadows.md).

`Widening`  
Belirtmediğiniz takdirde bir dönüştürme işleci için gereklidir `Narrowing` . Bu işleç yordamının bir [genişletme](../modifiers/widening.md) dönüşümünü tanımladığını gösterir. Bu Yardım sayfasında "genişletme ve daraltma dönüşümleri" başlığına bakın.

`Narrowing`  
Belirtmediğiniz takdirde bir dönüştürme işleci için gereklidir `Widening` . Bu işleç yordamının bir [daraltma](../modifiers/narrowing.md) dönüşümünü tanımladığını gösterir. Bu Yardım sayfasında "genişletme ve daraltma dönüşümleri" başlığına bakın.

`operatorsymbol`  
Gereklidir. Bu işleç yordamının tanımladığı işlecin simgesi veya tanımlayıcısı.

`operand1`  
Gereklidir. Birli işlecin tek işleneninin adı ve türü (dönüştürme işleci dahil) veya bir ikili işlecinin sol işleneni.

`operand2`  
İkili işleçler için gereklidir. Bir ikili işlecinin sağ işleneninin adı ve türü.

`operand1`ve `operand2` aşağıdaki söz dizimi ve bölümlere sahiptir:

`[ ByVal ] operandname [ As operandtype ]`

|Bölüm|Description|
|----------|-----------------|
|`ByVal`|İsteğe bağlı, ancak geçen mekanizmanın [ByVal](../modifiers/byval.md)olması gerekir.|
|`operandname`|Gereklidir. Bu işleneni temsil eden değişkenin adı. Bkz. [tanımlanmış öğe adları](../../programming-guide/language-features/declared-elements/declared-element-names.md).|
|`operandtype`|Olmadığı müddetçe isteğe bağlıdır `Option Strict` `On` . Bu işlenenin veri türü.|

`type`  
Olmadığı müddetçe isteğe bağlıdır `Option Strict` `On` . İşleç yordamının döndürdüğü değerin veri türü.

`statements`  
İsteğe bağlı. İşleç yordamının çalıştığı deyimler bloğu.

`returnvalue`  
Gereklidir. İşleç yordamının çağırma koduna döndürdüğü değer.

`End` `Operator`  
Gereklidir. Bu işleç yordamının tanımını sonlandırır.

## <a name="remarks"></a>Açıklamalar

`Operator`Yalnızca bir sınıf veya yapı içinde kullanabilirsiniz. Bu, bir işlecin *bildirim bağlamının* kaynak dosya, ad alanı, modül, arabirim, yordam veya blok olamayacağı anlamına gelir. Daha fazla bilgi için bkz. [bildirim bağlamları ve varsayılan erişim düzeyleri](declaration-contexts-and-default-access-levels.md).

Tüm işleçler olmalıdır `Public Shared` . `ByRef` `Optional` `ParamArray` Her iki işlenen için, veya belirtemezsiniz.

Dönüş değerini tutmak için işleç sembolünü veya tanımlayıcıyı kullanamazsınız. İfadesini kullanmanız gerekir `Return` ve bir değer belirtmelidir. Herhangi bir sayıda `Return` deyim yordamda herhangi bir yerde görünebilir.

Bu şekilde bir işleci tanımlamak *işleç aşırı yüklemesi*olarak adlandırılır, `Overloads` anahtar sözcüğünü kullanıp kullanmayacağınızı. Aşağıdaki tabloda, tanımlayabilmeniz için kullanabileceğiniz işleçler listelenmektedir.

|Tür|İşleçler|
|----------|---------------|
|Birli|`+`, `-`, `IsFalse`, `IsTrue`, `Not`|
|İkili|`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`|
|Dönüştürme (birli)|`CType`|

`=`İkili listedeki işlecin atama işleci değil karşılaştırma operatörü olduğunu unutmayın.

Tanımlarken, ya `CType` da belirtmeniz gerekir `Widening` `Narrowing` .

## <a name="matched-pairs"></a>Eşleşen çiftler

Belirli işleçleri eşleşen çiftler olarak tanımlamanız gerekir. Böyle bir çiftin işlecini tanımlarsanız, diğerini de tanımlamanız gerekir. Eşleşen çiftler şunlardır:

- `=` ve `<>`

- `>` ve `<`

- `>=` ve `<=`

- `IsTrue` ve `IsFalse`

## <a name="data-type-restrictions"></a>Veri türü kısıtlamaları

Tanımladığınız her operatör, üzerinde tanımladığınız sınıf veya yapıyı içermelidir. Bu, sınıfın veya yapının aşağıdakilerin veri türü olarak görünmesi gerektiği anlamına gelir:

- Birli işlecin işleneni.

- Bir ikili işlecinin işlenenlerinden en az biri.

- Bir dönüştürme işlecinin işleneni ya da dönüş türü.

 Bazı işleçler, aşağıdaki gibi ek veri türü kısıtlamalarına sahiptir:

- `IsTrue`Ve `IsFalse` işleçlerini tanımlarsanız, her ikisi de `Boolean` türü döndürmelidir.

- Ve işleçlerini tanımlarsanız, `<<` `>>` her ikisi de `Integer` öğesinin türünü belirtmelidir `operandtype` `operand2` .

Dönüş türünün, her iki işlenenin türüne karşılık gelmesi gerekmez. Örneğin, veya gibi bir karşılaştırma işleci `=` `<>` `Boolean` , hiçbir işleneni olmasa bile dönebilir `Boolean` .

## <a name="logical-and-bitwise-operators"></a>Mantıksal ve Bit Düzeyinde İşleçler

`And`,, `Or` `Not` Ve `Xor` işleçleri Visual Basic mantıksal veya bit tabanlı işlemler gerçekleştirebilir. Ancak, bu işleçlerden birini bir sınıf veya yapıda tanımlarsanız, yalnızca bit düzeyinde işlemini tanımlayabilirsiniz.

`AndAlso`İşleci bir ifadesiyle doğrudan tanımlayamazsınız `Operator` . Ancak, `AndAlso` aşağıdaki koşulları karşıladıysanız kullanabilirsiniz:

- `And`İçin kullanmak istediğiniz aynı işlenen türlerinde tanımladınız `AndAlso` .

- Tanımınız, `And` tanımladığınız sınıf veya yapı ile aynı türü döndürür.

- `IsFalse`İşleci, tanımladığınız sınıf veya yapı üzerinde tanımladınız `And` .

Benzer şekilde, `OrElse` `Or` sınıf veya yapının dönüş türü ile aynı işlenenler üzerinde tanımlamış olmanız ve `IsTrue` sınıf veya yapıda tanımladığınız durumlarda kullanabilirsiniz.

## <a name="widening-and-narrowing-conversions"></a>Genişletme ve Daraltma Dönüşümleri

Her *zaman* çalışma zamanında bir daraltma dönüştürmesi başarısız olsa da, bir *daraltma* dönüştürmesi çalışma zamanında başarısız olabilir. Daha fazla bilgi için bkz. [genişletme ve daraltma dönüştürmeleri](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).

Bir dönüştürme yordamı belirtmek isterseniz `Widening` , yordam kodunuzun herhangi bir başarısızlık üretmemelidir. Bunun anlamı:

- Her zaman geçerli bir tür değeri döndürmelidir `type` .

- Tüm olası özel durumları ve diğer hata koşullarını ele almalıdır.

- Çağrı yaptığı tüm yordamlardan hata getirlerinin işlenmesi gerekir.

Bir dönüştürme yordamının başarılı bir şekilde başarısız olabileceği veya işlenmemiş bir özel duruma neden olabileceği durumlarda, bunu olarak bildirmeniz gerekir `Narrowing` .

## <a name="example"></a>Örnek

Aşağıdaki kod örneği,,, `Operator` ve işleçleri için işleç yordamları içeren bir yapının anahattını tanımlamak için ifadesini kullanır `And` `Or` `IsFalse` `IsTrue` . `And`ve `Or` her biri türü ve dönüş türü iki işleneni alır `abc` `abc` . `IsFalse`ve `IsTrue` her biri, türünde tek bir işlenen alır `abc` ve döndürür `Boolean` . Bu tanımlar çağıran kodun,,, `And` `AndAlso` `Or` ve `OrElse` türündeki işlenenleri `abc` kullanmasına izin verir.

[!code-vb[VbVbalrStatements#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#44)]

## <a name="see-also"></a>Ayrıca bkz.

- [IsFalse İşleci](../operators/isfalse-operator.md)
- [IsTrue İşleci](../operators/istrue-operator.md)
- [Genişletme](../modifiers/widening.md)
- [Narrowing](../modifiers/narrowing.md)
- [Genişletme ve Daraltma Dönüşümleri](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [İşleç Yordamları](../../programming-guide/language-features/procedures/operator-procedures.md)
- [Nasıl yapılır: İşleç Tanımlama](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [Nasıl yapılır: Dönüştürme İşleci Tanımlama](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [Nasıl yapılır: Bir İşleç Yordamı Çağırma](../../programming-guide/language-features/procedures/how-to-call-an-operator-procedure.md)
- [Nasıl yapılır: İşleçleri Tanımlayan Bir Sınıf Kullanma](../../programming-guide/language-features/procedures/how-to-use-a-class-that-defines-operators.md)
