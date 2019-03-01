---
title: MustInherit (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- MustInherit
- vb.MustInherit
helpviewer_keywords:
- classes [Visual Basic], abstract
- MustInherit classes [Visual Basic], MustInherit keyword
- abstract classes [Visual Basic], MustInherit class
- MustInherit keyword [Visual Basic]
ms.assetid: b8f05185-90e3-4dd7-adc2-90d852fab5b4
ms.openlocfilehash: 124262695f9333ce31c4097662688e0fe30f300d
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56969537"
---
# <a name="mustinherit-visual-basic"></a>MustInherit (Visual Basic)
Bir sınıf yalnızca temel sınıf olarak kullanılabilir ve doğrudan bir nesne oluşturamazsınız belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
 Amacı, bir *temel sınıfı* (olarak da bilinen bir *soyut sınıf*) bundan türetilmiş tüm sınıflara ortak işlevselliği tanımlamaktır. Bu, türetilmiş sınıfları ortak öğeleri yeniden tanımlamak zorunda kalmaktan kurtarır. Bazı durumlarda, bu ortak işlevselliği kullanışlı bir nesne haline getirmek için eksiksiz değildir ve eksik işlevselliğe her türetilmiş bir sınıf tanımlar. Böyle bir durumda, tüketici kod yalnızca türetilmiş sınıflardan nesneleri oluşturmak için istediğiniz. Kullandığınız `MustInherit` bunu zorunlu kılmak için taban sınıfta.  
  
 Başka bir kullanımını bir `MustInherit` sınıfı, bir dizi ilgili sınıflar için bir değişken kısıtlamak için. Bir temel sınıf tanımlayabilir ve tüm ilgili sınıflar bundan türetir. Temel sınıfın türetilmiş sınıfların tümü için ortak olan herhangi bir işlevsellik sağlayan gerekmez, ancak değerleri değişkenlere atamak için bir filtre olarak hizmet verebilir. Visual Basic kullanan kod temel sınıf olarak bir değişken bildiriyorsa, yalnızca bir nesne türetilmiş sınıflarının birinden bu değişkene atamanıza izin verir.  
  
 .NET Framework birkaç tanımlar `MustInherit` sınıfları, aralarında <xref:System.Array>, <xref:System.Enum>, ve <xref:System.ValueType>. <xref:System.ValueType> bir değişken kısıtlayan bir taban sınıfın bir örnektir. Tüm değer türleri türetin <xref:System.ValueType>. Bir değişken olarak bildirirseniz <xref:System.ValueType>, değer türleri yalnızca bu değişkene atayabilirsiniz.  
  
## <a name="rules"></a>Kurallar  
  
-   **Bildirim bağlamı.** Kullanabileceğiniz `MustInherit` yalnızca bir `Class` deyimi.  
  
-   **Birleşik değiştiriciler.** Belirtemezsiniz `MustInherit` ile birlikte `NotInheritable` aynı bildirimde.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, zorla devralma ve geçersiz kılma zorlanmış gösterir. Temel sınıf `shape` bir değişkeni tanımlar `acrossLine`. Sınıfları `circle` ve `square` öğesinden türetilen `shape`. Bunlar tanımını devral `acrossLine`, ancak işlev tanımlamanız gerekir `area` Bu hesaplamayı şekli her tür için farklı olduğu için.  
  
 [!code-vb[VbVbalrKeywords#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#2)]  
  
 Bildirebilirsiniz `shape1` ve `shape2` türünde olmasını `shape`. Ancak, bir nesneden oluşturamazsınız `shape` işlevinin işlevselliğine eksik olduğundan `area` ve işaretlenmiş `MustInherit`.  
  
 Olarak bildirilen çünkü `shape`, değişkenleri `shape1` ve `shape2` nesnelere türetilmiş sınıflardan kısıtlanmıştır `circle` ve `square`. Visual Basic, bu değişkenler için herhangi bir nesneye atamak yüksek düzeyde bir tür güvenliği sağlayan izin vermez.  
  
## <a name="usage"></a>Kullanım  
 `MustInherit` Bu bağlamda değiştirici kullanılabilir:  
  
 [Class Deyimi](../../../visual-basic/language-reference/statements/class-statement.md)  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Inherits Deyimi](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md)
- [Anahtar Sözcükler](../../../visual-basic/language-reference/keywords/index.md)
- [Devralma Temelleri](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
