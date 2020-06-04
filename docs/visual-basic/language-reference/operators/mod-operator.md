---
title: Mod İşleci
ms.date: 04/24/2018
f1_keywords:
- vb.Mod
helpviewer_keywords:
- remainder (Mod operator)
- division operator [Visual Basic], Mod operator
- modulus operator [Visual Basic], Visual Basic
- Mod operator [Visual Basic]
- operators [Visual Basic], division
- arithmetic operators [Visual Basic], Mod
- math operators [Visual Basic]
ms.assetid: 6ff7e40e-cec8-4c77-bff6-8ddd2791c25b
ms.openlocfilehash: 32065567799b023556a018ae2f5ba338796e0b49
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401517"
---
# <a name="mod-operator-visual-basic"></a>Mod işleci (Visual Basic)

İki sayıyı böler ve yalnızca kalanı döndürür.

## <a name="syntax"></a>Sözdizimi

```vb
result = number1 Mod number2
```

## <a name="parts"></a>Bölümler

`result` \
Gereklidir. Herhangi bir sayısal değişken veya özellik.

`number1` \
Gereklidir. Herhangi bir sayısal ifade.

`number2` \
Gereklidir. Herhangi bir sayısal ifade.

## <a name="supported-types"></a>Desteklenen türler

Tüm sayısal türler. Bu, imzasız ve kayan nokta türlerini içerir `Decimal` .

## <a name="result"></a>Sonuç

Sonuç, öğesinden `number1` bölündükten sonra kalanı `number2` . Örneğin, ifade `14 Mod 4` 2 olarak değerlendirilir.

> [!NOTE]
> Olumsuz ve mod arasında negatif sayıların farklı sonuçlarıyla birlikte *kalan* ve *mod* arasında bir farklılık vardır. `Mod`Visual Basic işleci, .NET Framework `op_Modulus` işleci ve temeldeki [REM](<xref:System.Reflection.Emit.OpCodes.Rem>) Il yönergesinin hepsi bir geri kalan işlem gerçekleştirir.

Bir işlemin sonucu, `Mod` bölünün işaretini korur, `number1` ve bu nedenle pozitif veya negatif olabilir. Sonuç her zaman (- `number2` , `number2` ), hariç değişir. Örnek:

```vb
Public Module Example
   Public Sub Main()
      Console.WriteLine($" 8 Mod  3 = {8 Mod 3}")
      Console.WriteLine($"-8 Mod  3 = {-8 Mod 3}")
      Console.WriteLine($" 8 Mod -3 = {8 Mod -3}")
      Console.WriteLine($"-8 Mod -3 = {-8 Mod -3}")
   End Sub
End Module
' The example displays the following output:
'       8 Mod  3 = 2
'      -8 Mod  3 = -2
'       8 Mod -3 = 2
'      -8 Mod -3 = -2
```

## <a name="remarks"></a>Açıklamalar

Ya da `number1` `number2` bir kayan nokta değeri ise, bölmenin kayan nokta geri kalanı döndürülür. Sonucun veri türü, ve veri türleri ile bölme işleminden kaynaklanan tüm olası değerleri tutabilecek en küçük veri türüdür `number1` `number2` .

`number1`Ya da `number2` [hiçbir şey](../nothing.md)değerlendirilirse, sıfır olarak değerlendirilir.

İlgili işleçler şunları içerir:

- [\ İşleci (Visual Basic)](integer-division-operator.md) bir bölmenin tamsayı bölümünü döndürür. Örneğin, ifade `14 \ 4` 3 olarak değerlendirilir.

- [/İşleci (Visual Basic)](floating-point-division-operator.md) , kayan noktalı bir sayı olarak kalanı dahil olmak üzere tam bölümü döndürür. Örneğin, ifade `14 / 4` 3,5 olarak değerlendirilir.

## <a name="attempted-division-by-zero"></a>Sıfıra bölme denendi

`number2`Sıfır olarak değerlendirilirse, `Mod` işlecin davranışı işlenenlerinin veri türüne bağlıdır:

- Derleme zamanında belirlenemiyorsa integral bölüm bir <xref:System.DivideByZeroException> özel durum `number2` oluşturur ve derleme zamanında `BC30542 Division by zero occurred while evaluating this expression` sıfır olarak değerlendirilirse bir derleme zamanı hatası oluşturur `number2` .
- Kayan nokta bölmesi döndürülür <xref:System.Double.NaN?displayProperty=nameWithType> .

## <a name="equivalent-formula"></a>Denk formül

İfade `a Mod b` aşağıdaki formüllerden birine eşdeğerdir:

`a - (b * (a \ b))`

`a - (b * Fix(a / b))`

## <a name="floating-point-imprecision"></a>Kayan nokta noktasında kesinlik eksikliği

Kayan noktalı sayılarla çalışırken her zaman bellekte kesin bir ondalık gösterimine sahip olmadıkları unutulmamalıdır. Bu, değer karşılaştırması ve işleç gibi belirli işlemlerden beklenmeyen sonuçlara neden olabilir `Mod` . Daha fazla bilgi için bkz. [sorun giderme veri türleri](../../programming-guide/language-features/data-types/troubleshooting-data-types.md).

## <a name="overloading"></a>Aşırı Yükleme

`Mod`İşleç *aşırı*yüklenebilir, yani bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir. Kodunuz `Mod` , bu tür bir aşırı yükleme içeren bir sınıf veya yapının örneği için geçerliyse, yeniden tanımlanmış davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz. [operatör yordamları](../../programming-guide/language-features/procedures/operator-procedures.md).

## <a name="example"></a>Örnek

Aşağıdaki örnek, `Mod` iki sayıyı bölmek ve yalnızca geri kalanı döndürmek için işlecini kullanır. Her iki sayı de bir kayan noktalı sayı ise sonuç, kalanı temsil eden bir kayan noktalı sayıdır.

[!code-vb[VbVbalrOperators#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#31)]

## <a name="example"></a>Örnek

Aşağıdaki örnek, kayan nokta işlenenlerinin olası noktasında kesinlik eksikliği gösterir. İlk ifadede işlenen `Double` ve 0,2, saklı bir değeri 0.20000000000000001 olan sonsuz bir yinelenen ikili kesirdir. İkinci ifadede, değişmez değer türü karakteri `D` her iki işleneni olarak zorlar `Decimal` ve 0,2 kesin bir gösterimine sahiptir.

[!code-vb[VbVbalrOperators#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#32)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Conversion.Int%2A>
- <xref:Microsoft.VisualBasic.Conversion.Fix%2A>
- [Aritmetik İşleçler](arithmetic-operators.md)
- [Visual Basic'de İşleç Önceliği](operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](operators-listed-by-functionality.md)
- [Veri Türü Sorunlarını Giderme](../../programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Visual Basic'de Aritmetik İşleçler](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [\ İşleci (Visual Basic)](integer-division-operator.md)
