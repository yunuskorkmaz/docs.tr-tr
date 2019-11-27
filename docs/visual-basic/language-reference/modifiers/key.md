---
title: Anahtar
ms.date: 07/20/2015
f1_keywords:
- vb.AnonymousKey
helpviewer_keywords:
- anonymous types [Visual Basic], key
- Key [Visual Basic]
- Key keyword [Visual Basic]
ms.assetid: 7697a928-7d14-4430-a72a-c9e96e8d6c11
ms.openlocfilehash: 92c8809779d6cab524f67ee47f355b72ab152403
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351512"
---
# <a name="key-visual-basic"></a>Anahtar (Visual Basic)
`Key` anahtar sözcüğü anonim türlerin özellikleri için davranış belirtmenize olanak sağlar. Yalnızca anahtar özellikleri olarak belirleyeceğiniz özellikler, anonim tür örnekleri arasındaki eşitlik testlerine veya karma kodu değerlerinin hesaplanmasına katılır. Anahtar özelliklerinin değerleri değiştirilemez.  
  
 Anahtar sözcüğü `Key` bir özellik olarak bir özelliği, başlangıç listesindeki bildiriminin önüne yazarak anahtar özelliği olarak belirlersiniz. Aşağıdaki örnekte, `Airline` ve `FlightNo` anahtar özelliklerdir, ancak `Gate` değildir.  
  
 [!code-vb[VbVbalrAnonymousTypes#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#26)]  
  
 Yeni bir anonim tür oluşturulduğunda, doğrudan <xref:System.Object>devralır. Derleyici, devralınan üç üyeyi geçersiz kılar: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>ve <xref:System.Object.ToString%2A>. <xref:System.Object.Equals%2A> ve <xref:System.Object.GetHashCode%2A> için üretilen geçersiz kılma kodu, anahtar özelliklerini temel alır. Türde hiç anahtar özelliği yoksa, <xref:System.Object.GetHashCode%2A> ve <xref:System.Object.Equals%2A> geçersiz kılınmaz.  
  
## <a name="equality"></a>Eşitlik  
 İki anonim tür örneği aynı türde örneklerse ve anahtar özelliklerinin değerleri eşitse eşittir. Aşağıdaki örneklerde `flight2`, aynı anonim türdeki örnekler olduklarından ve bunların anahtar özellikleri için eşleşen değerleri olduğundan, önceki örnekteki `flight1` eşittir. Ancak, bir anahtar özelliği için farklı bir değere sahip olduğundan, `flight3` `flight1` eşit değildir `FlightNo`. Örnek `flight4`, anahtar özellikler olarak farklı özellikleri tasardıklarından `flight1` aynı türde değil.  
  
 [!code-vb[VbVbalrAnonymousTypes#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#27)]  
  
 İki örnek yalnızca anahtar olmayan özelliklerle, ad, tür, düzen ve değer ile bildirilirse, iki örnek eşit değildir. Anahtar özellikleri olmayan bir örnek yalnızca kendi kendine eşit değildir.  
  
 İki anonim tür örneğinin aynı anonim türdeki örnekleri olduğu koşullar hakkında daha fazla bilgi için bkz. [anonim türler](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
## <a name="hash-code-calculation"></a>Karma kod hesaplama  
 <xref:System.Object.Equals%2A>gibi, anonim bir tür için <xref:System.Object.GetHashCode%2A> tanımlanan karma işlevi, türün anahtar özelliklerine bağlıdır. Aşağıdaki örneklerde, anahtar özellikleri ve karma kod değerleri arasındaki etkileşim gösterilmektedir.  
  
 Anahtar olmayan özelliklerde eşleşen değerler olmasa bile, tüm anahtar özellikleri için aynı değere sahip anonim bir türün örnekleri aynı karma kod değerine sahiptir. Aşağıdaki ifade `True`döndürür.  
  
 [!code-vb[VbVbalrAnonymousTypes#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#37)]  
  
 Bir veya daha fazla anahtar özelliği için farklı değerlere sahip anonim bir türün örnekleri, farklı karma kodu değerlerine sahiptir. Aşağıdaki ifade `False`döndürür.  
  
 [!code-vb[VbVbalrAnonymousTypes#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#38)]  
  
 Anahtar özellikler olarak farklı özellikleri belirten anonim türlerin örnekleri aynı türde örnekler değildir. Tüm özelliklerin adları ve değerleri aynı olduğunda bile, farklı karma kodu değerleri vardır. Aşağıdaki ifade `False`döndürür.  
  
 [!code-vb[VbVbalrAnonymousTypes#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#39)]  
  
## <a name="read-only-values"></a>Salt okunurdur değerler  
 Anahtar özelliklerinin değerleri değiştirilemez. Örneğin, önceki örneklerde `flight1`, `Airline` ve `FlightNo` alanları salt okunurdur, ancak `Gate` değiştirilebilir.  
  
 [!code-vb[VbVbalrAnonymousTypes#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#28)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Anonim Tip Tanımı](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)
- [Nasıl yapılır: Anonim Tip Bildirimlerinden Özellik Adları ve Türlerini Çıkarma](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
- [Anonim Tipler](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
