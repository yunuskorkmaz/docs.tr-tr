---
title: Operator ekstresi (Visual Basic)
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
ms.openlocfilehash: c4fae40992fa665121aff637ae427ef0cafbf547
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582377"
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
İsteğe bağlı. Bkz. [öznitelik listesi](../../../visual-basic/language-reference/statements/attribute-list.md).

`Public`  
Gerekli. Bu işleç yordamının [ortak](../../../visual-basic/language-reference/modifiers/public.md) erişime sahip olduğunu gösterir.

`Overloads`  
İsteğe bağlı. Bkz. [aşırı yüklemeler](../../../visual-basic/language-reference/modifiers/overloads.md).

`Shared`  
Gerekli. Bu işleç yordamının [paylaşılan](../../../visual-basic/language-reference/modifiers/shared.md) bir yordam olduğunu gösterir.

`Shadows`  
İsteğe bağlı. Bkz. [gölgeler](../../../visual-basic/language-reference/modifiers/shadows.md).

`Widening`  
@No__t_0 belirtmediğiniz takdirde bir dönüştürme işleci için gereklidir. Bu işleç yordamının bir [genişletme](../../../visual-basic/language-reference/modifiers/widening.md) dönüşümünü tanımladığını gösterir. Bu Yardım sayfasında "genişletme ve daraltma dönüşümleri" başlığına bakın.

`Narrowing`  
@No__t_0 belirtmediğiniz takdirde bir dönüştürme işleci için gereklidir. Bu işleç yordamının bir [daraltma](../../../visual-basic/language-reference/modifiers/narrowing.md) dönüşümünü tanımladığını gösterir. Bu Yardım sayfasında "genişletme ve daraltma dönüşümleri" başlığına bakın.

`operatorsymbol`  
Gerekli. Bu işleç yordamının tanımladığı işlecin simgesi veya tanımlayıcısı.

`operand1`  
Gerekli. Birli işlecin tek işleneninin adı ve türü (dönüştürme işleci dahil) veya bir ikili işlecinin sol işleneni.

`operand2`  
İkili işleçler için gereklidir. Bir ikili işlecinin sağ işleneninin adı ve türü.

`operand1` ve `operand2` aşağıdaki söz dizimi ve bölümlere sahiptir:

`[ ByVal ] operandname [ As operandtype ]`

|Bölümüyle|Açıklama|
|----------|-----------------|
|`ByVal`|İsteğe bağlı, ancak geçen mekanizmanın [ByVal](../../../visual-basic/language-reference/modifiers/byval.md)olması gerekir.|
|`operandname`|Gerekli. Bu işleneni temsil eden değişkenin adı. Bkz. [tanımlanmış öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|
|`operandtype`|@No__t_0 `On` olmadığı müddetçe isteğe bağlıdır. Bu işlenenin veri türü.|

`type`  
@No__t_0 `On` olmadığı müddetçe isteğe bağlıdır. İşleç yordamının döndürdüğü değerin veri türü.

`statements`  
İsteğe bağlı. İşleç yordamının çalıştığı deyimler bloğu.

`returnvalue`  
Gerekli. İşleç yordamının çağırma koduna döndürdüğü değer.

`End``Operator`  
Gerekli. Bu işleç yordamının tanımını sonlandırır.

## <a name="remarks"></a>Açıklamalar

Yalnızca bir sınıf veya yapıda `Operator` kullanabilirsiniz. Bu, bir işlecin *bildirim bağlamının* kaynak dosya, ad alanı, modül, arabirim, yordam veya blok olamayacağı anlamına gelir. Daha fazla bilgi için bkz. [bildirim bağlamları ve varsayılan erişim düzeyleri](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).

Tüm işleçler `Public Shared` olmalıdır. Her iki işlenen için `ByRef`, `Optional` veya `ParamArray` belirtemezsiniz.

Dönüş değerini tutmak için işleç sembolünü veya tanımlayıcıyı kullanamazsınız. @No__t_0 ifadesini kullanmanız ve bir değer belirtmesi gerekir. Herhangi bir sayıda `Return` deyimi yordamda herhangi bir yerde görünebilir.

Bir işlecin bu şekilde tanımlanması, `Overloads` anahtar sözcüğünü kullanıp kullanmayacağınızı, *işleç aşırı yüklemesi*olarak adlandırılır. Aşağıdaki tabloda, tanımlayabilmeniz için kullanabileceğiniz işleçler listelenmektedir.

|Tür|İşleçler|
|----------|---------------|
|Li|`+`, `-`, `IsFalse`, `IsTrue`, `Not`|
|İkili|`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, 0, 1, 2, 3, 4, 5 , 6, 7, 8, 9|
|Dönüştürme (birli)|`CType`|

İkili listedeki `=` işlecinin, atama operatörü değil karşılaştırma operatörü olduğunu unutmayın.

@No__t_0 tanımladığınızda, `Widening` veya `Narrowing` belirtmeniz gerekir.

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

- @No__t_0 ve `IsFalse` işleçlerini tanımlarsanız, her ikisi de `Boolean` türünü döndürmelidir.

- @No__t_0 ve `>>` işleçlerini tanımlarsanız, her ikisi de `operand2` `operandtype` için `Integer` türünü belirtmelidir.

Dönüş türünün, her iki işlenenin türüne karşılık gelmesi gerekmez. Örneğin, `=` veya `<>` gibi bir karşılaştırma işleci, hiçbir işlenen `Boolean` bile `Boolean` döndürebilir.

## <a name="logical-and-bitwise-operators"></a>Mantıksal ve Bit Düzeyinde İşleçler

@No__t_0, `Or`, `Not` ve `Xor` işleçleri Visual Basic mantıksal veya bit tabanlı işlemler gerçekleştirebilir. Ancak, bu işleçlerden birini bir sınıf veya yapıda tanımlarsanız, yalnızca bit düzeyinde işlemini tanımlayabilirsiniz.

@No__t_0 işlecini doğrudan bir `Operator` ifadesiyle tanımlayamazsınız. Ancak, aşağıdaki koşulları karşıladıysanız `AndAlso` kullanabilirsiniz:

- @No__t_1 için kullanmak istediğiniz aynı işlenen türlerinde `And` tanımladınız.

- @No__t_0 tanımınız, tanımladığınız sınıf veya yapı ile aynı türü döndürür.

- @No__t_1 tanımladığınız sınıf veya yapıda `IsFalse` işlecini tanımladınız.

Benzer şekilde, aynı işlenenler üzerinde `Or` tanımladıysanız, sınıf veya yapının dönüş türü ile ve sınıf veya yapı üzerinde `IsTrue` tanımlamış olmanız durumunda `OrElse` kullanabilirsiniz.

## <a name="widening-and-narrowing-conversions"></a>Genişletme ve Daraltma Dönüşümleri

Her *zaman* çalışma zamanında bir daraltma dönüştürmesi başarısız olsa da, bir *daraltma* dönüştürmesi çalışma zamanında başarısız olabilir. Daha fazla bilgi için bkz. [genişletme ve daraltma dönüştürmeleri](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).

@No__t_0 bir dönüştürme yordamı bildirirseniz, yordam kodunuzun herhangi bir başarısızlık üretmemelidir. Bu, aşağıdakiler anlamına gelir:

- Her zaman `type` türünde geçerli bir değer döndürmelidir.

- Tüm olası özel durumları ve diğer hata koşullarını ele almalıdır.

- Çağrı yaptığı tüm yordamlardan hata getirlerinin işlenmesi gerekir.

Bir dönüştürme yordamının başarılı bir şekilde başarısız olabileceği veya işlenmemiş bir özel duruma neden olabileceği durumlarda, `Narrowing` olması gerekir.

## <a name="example"></a>Örnek

Aşağıdaki kod örneği, `And`, `Or`, `IsFalse` ve `IsTrue` işleçleri için işleç yordamları içeren bir yapının anahattını tanımlamak için `Operator` ifadesini kullanır. `And` ve `Or` her biri, `abc` türü ve dönüş türü `abc` iki işlenen alır. `IsFalse` ve `IsTrue` her biri `abc` türünde tek bir işlenen alır ve `Boolean` döndürür. Bu tanımlar çağıran kodun, `abc` türündeki işlenenleri `And`, `AndAlso`, `Or` ve `OrElse` kullanmasına izin verir.

[!code-vb[VbVbalrStatements#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#44)]

## <a name="see-also"></a>Ayrıca bkz.

- [IsFalse İşleci](../../../visual-basic/language-reference/operators/isfalse-operator.md)
- [IsTrue İşleci](../../../visual-basic/language-reference/operators/istrue-operator.md)
- [Widening](../../../visual-basic/language-reference/modifiers/widening.md)
- [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md)
- [Genişletme ve Daraltma Dönüştürmeleri](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [İşleç Yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)
- [Nasıl yapılır: İşleç Tanımlama](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [Nasıl yapılır: Dönüştürme İşleci Tanımlama](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [Nasıl yapılır: Bir İşleç Yordamı Çağırma](../../../visual-basic/programming-guide/language-features/procedures/how-to-call-an-operator-procedure.md)
- [Nasıl yapılır: İşleçleri Tanımlayan Bir Sınıf Kullanma](../../../visual-basic/programming-guide/language-features/procedures/how-to-use-a-class-that-defines-operators.md)
