---
title: Anahtar (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.AnonymousKey
helpviewer_keywords:
- anonymous types [Visual Basic], key
- Key [Visual Basic]
- Key keyword [Visual Basic]
ms.assetid: 7697a928-7d14-4430-a72a-c9e96e8d6c11
ms.openlocfilehash: 695f356f44bfd6ea5ad3c0a977ec31ddfbea2b05
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54668229"
---
# <a name="key-visual-basic"></a>Anahtar (Visual Basic)
`Key` Anahtar sözcüğü anonim türler, özellikler için davranışını belirtmenize imkan tanır. Anonim tür örnekleri veya bir karma kod değerleri hesaplama arasındaki testlerinde anahtar özellikleri arttıkça, yalnızca özellikleri belirleyin. Anahtar özelliklerin değerlerini değiştirilemez.  
  
 Anahtar sözcüğünü koyarak bir anahtar özellik olarak belirlediğiniz anonim bir türün bir özellik `Key` başlatma listesi bildiriminde önünde. Aşağıdaki örnekte, `Airline` ve `FlightNo` anahtar özellikleri, ancak `Gate` değil.  
  
 [!code-vb[VbVbalrAnonymousTypes#26](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_1.vb)]  
  
 Yeni bir anonim tür oluşturulduğunda, doğrudan devralan <xref:System.Object>. Derleyici, üç devralınan üyeleri geçersiz kılar: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, ve <xref:System.Object.ToString%2A>. İçin üretilen geçersiz kılma kod <xref:System.Object.Equals%2A> ve <xref:System.Object.GetHashCode%2A> anahtar özelliklerini temel alır. Tür, anahtar özellik varsa <xref:System.Object.GetHashCode%2A> ve <xref:System.Object.Equals%2A> geçersiz kılınmadığını.  
  
## <a name="equality"></a>Eşitlik  
 Aynı türdeki örneklerin olmaları durumunda ve bunların anahtar özelliklerinin değerler eşitse, iki anonim tür örnekleri eşit olur. Aşağıdaki örneklerde, `flight2` eşittir `flight1` aynı anonim örneklerini olduklarından önceki örnekteki tür değerleri kendi anahtar özellikleri için eşleşen sahip olur. Ancak, `flight3` eşit değildir `flight1` , bir anahtar özellik için farklı bir değer içerdiğinden `FlightNo`. Örnek `flight4` aynı türde değil `flight1` çünkü bunlar farklı özellikleri anahtar özellik olarak belirleyin.  
  
 [!code-vb[VbVbalrAnonymousTypes#27](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_2.vb)]  
  
 Yalnızca anahtar olmayan özellikleri olan adı, türü, sırası ve değeri, aynı iki örneği bildirilmişse iki örnek eşit değildir. Örneği anahtar özellikleri olmadan yalnızca kendisine eşittir.  
  
 İki anonim tür örnekleri altında aynı anonim tür örnekleri olan koşullar hakkında daha fazla bilgi için bkz. [anonim türler](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
## <a name="hash-code-calculation"></a>Karma kod hesaplama  
 Gibi <xref:System.Object.Equals%2A>, tanımlanan karma işlevi <xref:System.Object.GetHashCode%2A> türü anahtar özellikleri anonim bir tür temel alınır. Aşağıdaki örnekler arasındaki etkileşimler anahtar özellikleri ve karma kod değerlerini gösterir.  
  
 Anahtar olmayan özellikler eşleşen değerler olmasa bile, tüm anahtar özellikleri için aynı değerlere sahip anonim bir türün örneklerinin aynı karma kodu değeri var. Aşağıdaki ifade döndürür `True`.  
  
 [!code-vb[VbVbalrAnonymousTypes#37](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_3.vb)]  
  
 Bir veya daha fazla anahtar özelliği için farklı değerlere sahip anonim bir türün örneklerinin farklı bir karma kod değerlere sahip. Aşağıdaki ifade döndürür `False`.  
  
 [!code-vb[VbVbalrAnonymousTypes#38](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_4.vb)]  
  
 Farklı özellikleri anahtar özellik olarak belirlediğiniz anonim türlerin örneklerini örnekleri aynı türde değil. Adları ve değerleri tüm özelliklerin aynı olsa bile farklı bir karma kod değerlere sahiptirler. Aşağıdaki ifade döndürür `False`.  
  
 [!code-vb[VbVbalrAnonymousTypes#39](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_5.vb)]  
  
## <a name="read-only-values"></a>Salt okunur değerleri  
 Anahtar özelliklerin değerlerini değiştirilemez. Örneğin, `flight1` önceki örneklerde, `Airline` ve `FlightNo` alanları salt okunur ancak `Gate` değiştirilebilir.  
  
 [!code-vb[VbVbalrAnonymousTypes#28](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_6.vb)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Anonim Tip Tanımı](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)
- [Nasıl yapılır: Özellik adları ve türleri anonim türde bildirimlerden çıkarma](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
- [Anonim Tipler](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
