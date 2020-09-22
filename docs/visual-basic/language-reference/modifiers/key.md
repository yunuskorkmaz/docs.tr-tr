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
ms.openlocfilehash: 582ed5bb67b9c7504e736710aa4649cffb12ef45
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867997"
---
# <a name="key-visual-basic"></a>Anahtar (Visual Basic)

`Key`Anahtar sözcüğü anonim türlerin özellikleri için davranış belirtmenizi sağlar. Yalnızca anahtar özellikleri olarak belirleyeceğiniz özellikler, anonim tür örnekleri arasındaki eşitlik testlerine veya karma kodu değerlerinin hesaplanmasına katılır. Anahtar özelliklerinin değerleri değiştirilemez.  
  
 Anahtar sözcüğünü `Key` başlatma listesindeki bildiriminin önüne yerleştirerek, anonim türdeki bir özelliği anahtar özelliği olarak belirlersiniz. Aşağıdaki örnekte `Airline` ve `FlightNo` temel özelliklerdir, ancak `Gate` değildir.  
  
 [!code-vb[VbVbalrAnonymousTypes#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#26)]  
  
 Yeni bir anonim tür oluşturulduğunda, doğrudan öğesinden devralır <xref:System.Object> . Derleyici, devralınan üç üyeyi geçersiz kılar: <xref:System.Object.Equals%2A> , <xref:System.Object.GetHashCode%2A> , ve <xref:System.Object.ToString%2A> . Ve için üretilen geçersiz kılma kodu, <xref:System.Object.Equals%2A> <xref:System.Object.GetHashCode%2A> anahtar özelliklerini temel alır. Türde hiç anahtar özellik yoksa <xref:System.Object.GetHashCode%2A> ve <xref:System.Object.Equals%2A> geçersiz kılınmamışsa.  
  
## <a name="equality"></a>Eşitlik  

 İki anonim tür örneği aynı türde örneklerse ve anahtar özelliklerinin değerleri eşitse eşittir. Aşağıdaki örneklerde, `flight2` `flight1` aynı anonim türün örnekleri olduklarından ve bunların anahtar özellikleri için eşleşen değerleri bulunduğundan, önceki örnekteki öğesine eşittir. Ancak, `flight3` `flight1` bir anahtar özelliği için farklı bir değere sahip olduğundan, öğesine eşit değildir `FlightNo` . Örnek `flight4` , `flight1` anahtar özellikler olarak farklı özellikleri belirlemediklerinden aynı türde değildir.  
  
 [!code-vb[VbVbalrAnonymousTypes#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#27)]  
  
 İki örnek yalnızca anahtar olmayan özelliklerle, ad, tür, düzen ve değer ile bildirilirse, iki örnek eşit değildir. Anahtar özellikleri olmayan bir örnek yalnızca kendi kendine eşit değildir.  
  
 İki anonim tür örneğinin aynı anonim türdeki örnekleri olduğu koşullar hakkında daha fazla bilgi için bkz. [anonim türler](../../programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
## <a name="hash-code-calculation"></a>Karma kod hesaplama  

 Benzer şekilde <xref:System.Object.Equals%2A> , anonim bir tür için ' de tanımlanan karma işlevi, <xref:System.Object.GetHashCode%2A> türün anahtar özelliklerine bağlıdır. Aşağıdaki örneklerde, anahtar özellikleri ve karma kod değerleri arasındaki etkileşim gösterilmektedir.  
  
 Anahtar olmayan özelliklerde eşleşen değerler olmasa bile, tüm anahtar özellikleri için aynı değere sahip anonim bir türün örnekleri aynı karma kod değerine sahiptir. Aşağıdaki ifade döndürür `True` .  
  
 [!code-vb[VbVbalrAnonymousTypes#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#37)]  
  
 Bir veya daha fazla anahtar özelliği için farklı değerlere sahip anonim bir türün örnekleri, farklı karma kodu değerlerine sahiptir. Aşağıdaki ifade döndürür `False` .  
  
 [!code-vb[VbVbalrAnonymousTypes#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#38)]  
  
 Anahtar özellikler olarak farklı özellikleri belirten anonim türlerin örnekleri aynı türde örnekler değildir. Tüm özelliklerin adları ve değerleri aynı olduğunda bile, farklı karma kodu değerleri vardır. Aşağıdaki ifade döndürür `False` .  
  
 [!code-vb[VbVbalrAnonymousTypes#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#39)]  
  
## <a name="read-only-values"></a>Salt okunurdur değerler  

 Anahtar özelliklerinin değerleri değiştirilemez. Örneğin, `flight1` Önceki örneklerde, `Airline` ve `FlightNo` alanları salt okunurdur, ancak `Gate` değiştirilebilir.  
  
 [!code-vb[VbVbalrAnonymousTypes#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#28)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Anonim Tip Tanımı](../../programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)
- [Nasıl yapılır: Anonim Tip Bildirimlerinden Özellik Adları ve Türlerini Çıkarma](../../programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
- [Anonim Türler](../../programming-guide/language-features/objects-and-classes/anonymous-types.md)
