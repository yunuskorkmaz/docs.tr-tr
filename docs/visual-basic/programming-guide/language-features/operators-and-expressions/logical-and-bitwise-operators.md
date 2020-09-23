---
title: Mantıksal ve Bit Düzeyinde İşleçler
ms.date: 07/20/2015
helpviewer_keywords:
- short-circuiting
- Boolean expressions
- logical operators [Visual Basic], Boolean expressions
- operators [Visual Basic], logical
- AndAlso operator [Visual Basic]
- Not operator [Visual Basic], Boolean expressions
- Xor operator [Visual Basic], Boolean expressions
- And operator [Visual Basic], logical operators
- logical operators [Visual Basic]
- expressions [Visual Basic], Boolean
- Or operator [Visual Basic], logical operators
- Visual Basic code, operators
- short-circuiting [Visual Basic], logical operators
- logical operators [Visual Basic], short-circuiting
- Visual Basic code, expressions
- logical operators [Visual Basic], binary
- OrElse operator [Visual Basic]
- logical operators [Visual Basic], unary
ms.assetid: ca474e13-567d-4b1d-a18b-301433705e57
ms.openlocfilehash: c15b9337f262563941699c0ff8fe5219ca6a5c93
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91086003"
---
# <a name="logical-and-bitwise-operators-in-visual-basic"></a>Visual Basic'de Mantıksal ve Bit Düzeyinde İşleçler

Mantıksal işleçler `Boolean` ifadeleri karşılaştırır ve bir `Boolean` sonuç döndürür. `And`,, `Or` , `AndAlso` `OrElse` Ve `Xor` işleçleri iki işlenen kullandığından, *binary* `Not` tek bir işlenen aldığı için işleç *tekil* olduğu için ikili bir dosyaysa. Bu işleçlerden bazıları, tam sayı değerlerinde bit düzeyinde mantıksal işlemler de gerçekleştirebilir.  
  
## <a name="unary-logical-operator"></a>Birli mantıksal Işleç  

 [Not işleci](../../../language-reference/operators/not-operator.md) bir ifadede mantıksal *değilleme* gerçekleştirir `Boolean` . İşleneni, işleneninin mantıksal tersini verir. İfade olarak değerlendirilirse,, `True` `Not` `False` ifadesi olarak değerlendirilirse, öğesini döndürür `False` `Not` `True` . Aşağıdaki örnek bunu göstermektedir.  
  
 [!code-vb[VbVbalrOperators#77](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#77)]  
  
## <a name="binary-logical-operators"></a>İkili mantıksal Işleçler  

 [And işleci](../../../language-reference/operators/and-operator.md) iki ifade üzerinde mantıksal bir *birlikte* gerçekleştirir `Boolean` . Her iki ifade olarak değerlendirilir `True` , öğesini `And` döndürür `True` . Deyimlerden en az biri olarak değerlendirilirse, öğesini `False` `And` döndürür `False` .  
  
 [OR işleci](../../../language-reference/operators/or-operator.md) , mantıksal *ayırıcı* veya iki ifadeye *dahil* etme işlemini gerçekleştirir `Boolean` . İki ifade olarak değerlendirilirse `True` veya her ikisi de olarak değerlendirilirse, öğesini `True` `Or` döndürür `True` . Hiçbir ifadenin olarak değerlendiriliyorsa `True` , `Or` döndürür `False` .  
  
 [Xor işleci](../../../language-reference/operators/xor-operator.md) iki ifadeye mantıksal *dışlama* gerçekleştirir `Boolean` . Tam olarak bir ifade olarak değerlendirilir `True` , ancak her ikisini de değil, `Xor` döndürür `True` . Her iki ifade de olarak değerlendirilir `True` veya her ikisini de olarak değerlendirir `False` , `Xor` döndürür `False` .  
  
 Aşağıdaki örnekte `And` ,, `Or` ve işleçleri gösterilmektedir `Xor` .  
  
 [!code-vb[VbVbalrOperators#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#78)]  
  
## <a name="short-circuiting-logical-operations"></a>Kısa devre mantıksal Işlemler yürütülüyor  

 [AndAlso işleci](../../../language-reference/operators/andalso-operator.md) , `And` işleçle çok benzerdir, bu da iki ifadeye de mantıksal bir işlem yapar `Boolean` . İkisi arasındaki temel fark, kısa devre uygulayan `AndAlso` davranışı *short-circuiting* gösteriyor. Bir ifadedeki ilk ifade `AndAlso` olarak değerlendirilirse `False` , ikinci ifade nihai sonucu değiştirmediği ve döndürdüğü için değerlendirilmez `AndAlso` `False` .  
  
 Benzer şekilde, [OrElse işleci](../../../language-reference/operators/orelse-operator.md) iki ifadeye kısa devre uygulayan mantıksal bir birleşim uygular `Boolean` . Bir ifadedeki ilk ifade `OrElse` olarak değerlendirilirse `True` , ikinci ifade nihai sonucu değiştirmediği ve döndürdüğü için değerlendirilmez `OrElse` `True` .  
  
### <a name="short-circuiting-trade-offs"></a>Kısa süreli bir denge  

 Kısa devre uygulayan, mantıksal işlemin sonucunu değiştirebilecek bir ifadeyi değerlendirmeden performansı iyileştirebilir. Ancak, bu ifade ek eylemler gerçekleştirdiğinde, kısa devre uygulayan bu eylemleri atlar. Örneğin, ifade bir yordama çağrı içeriyorsa `Function` , ifade kısa devre dışı ise ve içinde yer alan ek kodlar çalıştırılsa, bu yordam çağrılmaz `Function` . Bu nedenle, işlev yalnızca belirli bir zaman çalışabilir ve doğru şekilde sınanmayabilir. Ya da program mantığı içindeki koda bağlı olabilirler `Function` .  
  
 Aşağıdaki örnek `And` ,, `Or` ve bunların kısa devre dışı karşılıkları arasındaki farkı gösterir.  
  
 [!code-vb[VbVbalrOperators#81](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#81)]  
  
 [!code-vb[VbVbalrOperators#80](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#80)]  
  
 [!code-vb[VbVbalrOperators#79](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#79)]  
  
 Yukarıdaki örnekte, `checkIfValid()` çağrı kısa devre dışı olduğunda, içindeki bazı önemli kodların çalıştırılmadığını unutmayın. İlk `If` ifade çağrı yapmaz `checkIfValid()` , ancak `12 > 45` `False` `And` kısa devre dışı değildir. İkinci `If` deyim çağırmaz `checkIfValid()` , çünkü `12 > 45` döndürür, `False` `AndAlso` kısa devreler ikinci ifadedir. `If`Kısa devre olmadığından, üçüncü ifade çağrıları `checkIfValid()` `12 < 45` döndürür `True` `Or` . Dördüncü `If` deyim çağrı yapmaz `checkIfValid()` , çünkü `12 < 45` döndürür, `True` `OrElse` kısa devreler ikinci ifadedir.  
  
## <a name="bitwise-operations"></a>Bit düzeyinde Işlemler  

 Bit düzeyinde işlemler ikili (taban 2) formda iki integral değeri değerlendirir. Bunlara karşılık gelen konumlarda bitleri karşılaştırırlar ve sonra karşılaştırmaya göre değerler atar. Aşağıdaki örnekte `And` işleç gösterilmektedir.  
  
 [!code-vb[VbVbalrConcepts#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConcepts/VB/Class1.vb#2)]  
  
 Önceki örnek değerini `x` 1 olarak ayarlar. Bu durum aşağıdaki nedenlerden dolayı gerçekleşir:  
  
- Değerler ikili olarak değerlendirilir:  
  
     3 ikili biçiminde 3 = 011  
  
     5 ikili biçimi = 101  
  
- İşleci, tek seferde bir `And` ikili konum (bit) ikili gösterimlerini karşılaştırır. Belirli bir konumdaki bitlerin her ikisi de 1 ise, sonuçta bu konuma bir 1 konur. Her iki bit de 0 ise, sonuçta bu konuma 0 yerleştirilir. Yukarıdaki örnekte bu, aşağıdaki gibi çalışmaktadır:  
  
     011 (ikili biçimde 3)  
  
     101 (ikili biçimde 5)  
  
     001 (sonuç, ikili biçimde)  
  
- Sonuç ondalık olarak değerlendirilir. 001 değeri 1, bu nedenle = 1 ' in ikili gösterimidir `x` .  
  
 Bit düzeyinde `Or` işlem benzerdir, ancak karşılaştırılan bitlerin biri veya her ikisi 1 ise sonuç bitine 1 atanır. `Xor` karşılaştırılan bitlerin (her ikisi de değil) tam olarak biri 1 ise, sonuç bitini 1 atar. `Not` tek bir işlenen alır ve işaret biti dahil olmak üzere tüm bitleri ters çevirir ve bu değeri sonuca atar. Bu, işaretli pozitif sayıların `Not` her zaman negatif bir değer döndüğü ve negatif sayıların `Not` her zaman pozitif veya sıfır değer döndürdüğü anlamına gelir.  
  
 `AndAlso`Ve `OrElse` işleçleri bit düzeyinde işlemleri desteklemez.  
  
> [!NOTE]
> Bit düzeyinde işlemler yalnızca integral türlerinde gerçekleştirilebilir. Bit düzeyinde işlemin devam edebilmesi için kayan nokta değerlerinin tamsayı türlerine dönüştürülmesi gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Mantıksal/Bit Düzeyinde İşleçler (Visual Basic)](../../../language-reference/operators/logical-bitwise-operators.md)
- [Boole Ifadeleri](boolean-expressions.md)
- [Visual Basic'de Aritmetik İşleçler](arithmetic-operators.md)
- [Visual Basic'de Karşılaştırma İşleçleri](comparison-operators.md)
- [Visual Basic'de Birleştirme İşleçleri](concatenation-operators.md)
- [İşleçlerin Etkili Bileşimi](efficient-combination-of-operators.md)
