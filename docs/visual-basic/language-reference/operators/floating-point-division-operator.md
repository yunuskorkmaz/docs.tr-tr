---
title: / İşleci
ms.date: 07/20/2015
f1_keywords:
- vb./
helpviewer_keywords:
- division operator [Visual Basic], floating point
- floating-point numbers [Visual Basic], division operator
- slash (/) operator
- zero, division by zero
- operators [Visual Basic], arithmetic
- arithmetic operators [Visual Basic], division
- division [Visual Basic], by zero
- operators [Visual Basic], division
- division operator [Visual Basic], syntax
- / operator [Visual Basic]
- math operators [Visual Basic]
ms.assetid: 335e97f2-c434-439e-9064-76973a051101
ms.openlocfilehash: 765a80d45908e0ecf17e4c21b748dbf6b2a4c0f5
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867035"
---
# <a name="-operator-visual-basic"></a>/ İşleci (Visual Basic)

İki sayıyı böler ve kayan noktalı bir sonuç döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
expression1 / expression2  
```  
  
## <a name="parts"></a>Bölümler  

 `expression1`  
 Gereklidir. Herhangi bir sayısal ifade.  
  
 `expression2`  
 Gereklidir. Herhangi bir sayısal ifade.  
  
## <a name="supported-types"></a>Desteklenen türler  

 İmzasız ve kayan nokta türleri de dahil olmak üzere tüm sayısal türler `Decimal` .  
  
## <a name="result"></a>Sonuç  

 Sonuç, `expression1` `expression2` kalanı da dahil olmak üzere bölünen tam bölüm.  
  
 [\ İşleci (Visual Basic)](integer-division-operator.md) , kalanı döndüren tamsayı bölümünü döndürür.  
  
## <a name="remarks"></a>Açıklamalar  

 Sonucun veri türü, işlenenlerinin türlerine bağlıdır. Aşağıdaki tabloda, sonucun veri türünün nasıl belirlendiği gösterilmektedir.  
  
|İşlenen veri türleri|Sonuç veri türü|  
|------------------------|----------------------|  
|Her iki ifade de İntegral veri türleridir[(SByte](../data-types/sbyte-data-type.md), [byte](../data-types/byte-data-type.md), [Short](../data-types/short-data-type.md), [ushort](../data-types/ushort-data-type.md), [Integer](../data-types/integer-data-type.md), [UInteger](../data-types/uinteger-data-type.md), [Long](../data-types/long-data-type.md), [ulong](../data-types/ulong-data-type.md))|`Double`|  
|Tek bir ifade [tek](../data-types/single-data-type.md) bir veri türüdür ve diğeri [Double](../data-types/double-data-type.md) değildir|`Single`|  
|Bir ifade [ondalık](../data-types/decimal-data-type.md) veri türüdür ve diğeri [tek](../data-types/single-data-type.md) veya [çift](../data-types/double-data-type.md) değil|`Decimal`|  
|İki ifade de bir [Double](../data-types/double-data-type.md) veri türüdür|`Double`|  
  
 Bölüm gerçekleştirilmeden önce, tüm integral sayısal ifadeler iletildiklerinde ' dir `Double` . Sonucu bir integral veri türüne atarsanız, Visual Basic sonucu `Double` Bu türe dönüştürmeye çalışır. Bu, sonuç bu türe uygun değilse bir özel durum oluşturabilir. Özellikle, bu Yardım sayfasında "sıfıra bölme yapılmaya çalışıldı" bölümüne bakın.  
  
 `expression1`Ya da `expression2` [hiçbir şey](../nothing.md)değerlendirilirse, sıfır olarak değerlendirilir.  
  
## <a name="attempted-division-by-zero"></a>Sıfıra bölme denendi  

 `expression2`Sıfır olarak değerlendirilirse, `/` işleç farklı işlenen veri türleri için farklı davranır. Aşağıdaki tabloda olası davranışlar gösterilmektedir.  
  
|İşlenen veri türleri|Sıfır ise davranış `expression2`|  
|------------------------|---------------------------------------|  
|Kayan nokta ( `Single` veya `Double` )|<xref:System.Double.PositiveInfinity> <xref:System.Double.NegativeInfinity> Sıfır ise, sonsuz (veya), ya <xref:System.Double.NaN> da (sayı değil) döndürür `expression1`|  
|`Decimal`|Oluşturur <xref:System.DivideByZeroException>|  
|Integral (işaretli veya imzasız)|<xref:System.OverflowException>İntegral türler <xref:System.Double.PositiveInfinity> , veya kabul edilemediğinden integral türüne geri dönüştürme denendi. <xref:System.Double.NegativeInfinity><xref:System.Double.NaN>|  
  
> [!NOTE]
> `/`İşleç *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir. Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz. [operatör yordamları](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  

 Bu örnek, `/` kayan nokta bölme gerçekleştirmek için işlecini kullanır. Sonuç iki işlenenin bir bölümü olur.  
  
 [!code-vb[VbVbalrOperators#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#16)]  
  
 Yukarıdaki örnekteki ifadeler 2,5 ve 3,333333 değerlerini döndürür. `Double`Her iki işlenen de tamsayı sabiti olsa da sonucun her zaman kayan nokta () olduğunu unutmayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [/= İşleci (Visual Basic)](floating-point-division-assignment-operator.md)
- [\ İşleci (Visual Basic)](integer-division-operator.md)
- [İşleç Sonuçlarının Veri Türleri](data-types-of-operator-results.md)
- [Aritmetik Işleçler](arithmetic-operators.md)
- [Visual Basic'de İşleç Önceliği](operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](operators-listed-by-functionality.md)
- [Visual Basic'de Aritmetik İşleçler](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
