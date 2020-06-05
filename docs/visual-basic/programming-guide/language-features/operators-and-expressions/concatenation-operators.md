---
title: Birleştirme İşleçleri
ms.date: 07/20/2015
helpviewer_keywords:
- '& operator [Visual Basic], concatenation'
- concatenation operators [Visual Basic]
- operators [Visual Basic], concatenation
- Visual Basic code, operators
- + operator [Visual Basic], concatenation
- concatenation operators [Visual Basic]
ms.assetid: e59908c3-89e0-41ae-933d-3e8826c16a04
ms.openlocfilehash: c123438a86a2c3293a99770107d970535fcdbdf8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388796"
---
# <a name="concatenation-operators-in-visual-basic"></a>Visual Basic'de Birleştirme İşleçleri

Birleştirme işleçleri birden çok dizeyi tek bir dizeye birleştirir. İki birleştirme işleci vardır `+` `&` . Her ikisi de aşağıdaki örnekte gösterildiği gibi temel birleştirme işlemini çalıştırır.

```vb
Dim x As String = "Mic" & "ro" & "soft"
Dim y As String = "Mic" + "ro" + "soft"
' The preceding statements set both x and y to "Microsoft".
```

Bu işleçler `String` , aşağıdaki örnekte gösterildiği gibi değişkenleri de birleştirebilir.

[!code-vb[VbVbalrOperators#76](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#76)]

## <a name="differences-between-the-two-concatenation-operators"></a>Iki birleştirme Işleci arasındaki farklar

[+ İşlecinin](../../../language-reference/operators/addition-operator.md) iki sayı eklemenin birincil amacı vardır. Ancak, sayısal işlenenleri dize işlenenleri ile de birleştirebilir. `+`İşlecinde, bir derleyici hatasına ekleme, birleştirme, sinyal sinyali atma veya bir çalışma zamanı özel durumu oluşturma gibi karmaşık bir kural kümesi vardır <xref:System.InvalidCastException> .

[& işleci](../../../language-reference/operators/concatenation-operator.md) yalnızca işlenenler için tanımlanır `String` ve ayarından bağımsız olarak her zaman işlenenlerini olarak widens `String` `Option Strict` . `&`İşleci, dizeler için özel olarak tanımlandığından ve istenmeyen bir dönüştürme oluşturma olasılığınızı azalttığından dize birleştirme için önerilir.

## <a name="performance-string-and-stringbuilder"></a>Performans: dize ve StringBuilder

Birleştirmeleri, silmeler ve değişiklikler gibi bir dizede önemli sayıda değişiklik yaparsanız, performans, <xref:System.Text.StringBuilder> ad alanındaki sınıftan elde edebilir <xref:System.Text> . Bir nesne oluşturmak ve başlatmak için ek bir yönerge <xref:System.Text.StringBuilder> ve son değerini a 'ya dönüştürmek için başka bir yönerge kullanır `String` , ancak daha hızlı bir şekilde gerçekleştirilebileceğinden bu süreyi kurtarabilirsiniz <xref:System.Text.StringBuilder> .

## <a name="see-also"></a>Ayrıca bkz.

- [Option Strict Deyimi](../../../language-reference/statements/option-strict-statement.md)
- [Visual Basic'de Dize Düzenleme Yöntemlerinin Türleri](../strings/types-of-string-manipulation-methods.md)
- [Visual Basic'de Aritmetik İşleçler](arithmetic-operators.md)
- [Visual Basic'de Karşılaştırma İşleçleri](comparison-operators.md)
- [Visual Basic'de Mantıksal ve Bit Düzeyinde İşleçler](logical-and-bitwise-operators.md)
