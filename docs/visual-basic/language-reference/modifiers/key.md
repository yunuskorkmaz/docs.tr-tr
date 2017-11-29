---
title: Anahtar (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.AnonymousKey
helpviewer_keywords:
- anonymous types [Visual Basic], key
- Key [Visual Basic]
- Key keyword [Visual Basic]
ms.assetid: 7697a928-7d14-4430-a72a-c9e96e8d6c11
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 20dbe4e67fb3e415ba0202555ace7fd5afed68d2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="key-visual-basic"></a>Anahtar (Visual Basic)
`Key` Anahtar sözcüğü anonim türdeki özellikleri davranışını belirtmenize olanak sağlar. Anonim tür örneği veya karma kodu değerleri hesaplama arasında eşitlik testleri anahtar özellikleri katılan gibi yalnızca özellikleri, belirleyin. Anahtar özellikleri değerleri değiştirilemez.  
  
 Anahtar sözcüğünü girerek bir anahtar özellik olarak belirttiğiniz anonim bir türün bir özellik `Key` bildiriminden başlatma listesinde önünde. Aşağıdaki örnekte, `Airline` ve `FlightNo` anahtar özellikleri, ancak `Gate` değil.  
  
 [!code-vb[VbVbalrAnonymousTypes#26](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_1.vb)]  
  
 Yeni bir anonim türü oluşturulduğunda, doğrudan öğesinden devralınan <xref:System.Object>. Derleyici üç devralınan üyeleri geçersiz kılar: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, ve <xref:System.Object.ToString%2A>. İçin üretilen geçersiz kılma kodu <xref:System.Object.Equals%2A> ve <xref:System.Object.GetHashCode%2A> anahtar özelliklerinde dayanır. Tür, anahtar özellik varsa <xref:System.Object.GetHashCode%2A> ve <xref:System.Object.Equals%2A> değil geçersiz kılınır.  
  
## <a name="equality"></a>Eşitlik  
 İki anonim tür örnekleri aynı türde olup olmadığını ve anahtar özelliklerini değerleri aynıysa eşit örnekleridir. Aşağıdaki örneklerde, `flight2` eşittir `flight1` aynı anonim örneklerini olduklarından önceki örnekten türüne ve bunlar eşleşen anahtar özellikleri için değerleri sahip. Ancak, `flight3` eşit değil `flight1` bir anahtar özellik için farklı bir değere sahip olduğundan `FlightNo`. Örnek `flight4` aynı türde değil `flight1` çünkü bunlar farklı özellikleri anahtar özellik olarak belirleyin.  
  
 [!code-vb[VbVbalrAnonymousTypes#27](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_2.vb)]  
  
 Yalnızca anahtar olmayan özellikler, ad, tür, sipariş ve değer, aynı olan iki örneği bildirilen, iki örneği eşit değildir. Anahtar özellikleri olmayan bir örneği yalnızca kendisine eşittir.  
  
 İki anonim tür örnekleri altında aynı anonim türdeki örneklerin olan koşullar hakkında daha fazla bilgi için bkz: [anonim türler](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
## <a name="hash-code-calculation"></a>Karma kod hesaplama  
 Gibi <xref:System.Object.Equals%2A>, tanımlanan karma işlevi <xref:System.Object.GetHashCode%2A> anonim bir tür türü anahtar özelliklerinde temel alınır. Aşağıdaki örnekler anahtar özellikleri ve karma arasındaki etkileşim kod değerleri gösterir.  
  
 Anahtar olmayan özellikler eşleşen değerleri olmasa bile, tüm anahtar özellikler için aynı değerlere sahip anonim bir tür örnekleri aynı karma kodu değere sahip. Aşağıdaki deyim döndürür `True`.  
  
 [!code-vb[VbVbalrAnonymousTypes#37](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_3.vb)]  
  
 Bir veya daha fazla anahtar özellikleri için farklı değerlere sahip anonim bir tür örnekleri farklı bir karma kod değerlere sahiptir. Aşağıdaki deyim döndürür `False`.  
  
 [!code-vb[VbVbalrAnonymousTypes#38](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_4.vb)]  
  
 Farklı özellikleri anahtar özellikler örnekleri aynı türde olmadığından tanımladığınız anonim türler örnekleri. Adları ve değerleri tüm özelliklerin aynı olsa bile farklı bir karma kod değerleri sahiptirler. Aşağıdaki deyim döndürür `False`.  
  
 [!code-vb[VbVbalrAnonymousTypes#39](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_5.vb)]  
  
## <a name="read-only-values"></a>Salt okunur değerleri  
 Anahtar özellikleri değerleri değiştirilemez. Örneğin, `flight1` önceki örneklerde, `Airline` ve `FlightNo` alanları salt okunur, ancak `Gate` değiştirilebilir.  
  
 [!code-vb[VbVbalrAnonymousTypes#28](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_6.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Anonim tür tanımı](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)  
 [Nasıl yapılır: özellik adları ve türlerini anonim türde bildirimlerden çıkarma](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)  
 [Anonim türler](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
