---
title: MustInherit
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
ms.openlocfilehash: 30befaaf194d78d26a57f29c59bf0a603e9f07a3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351504"
---
# <a name="mustinherit-visual-basic"></a>MustInherit (Visual Basic)
Bir sınıfın sadece temel sınıf olarak kullanılabileceğini ve doğrudan bundan bir nesne oluşturkullanılamayacağını belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
 *Temel sınıfın* amacı ( *soyut sınıf*olarak da bilinir), bundan türetilmiş tüm sınıflar için ortak olan işlevleri tanımlamaktır. Bu, türetilmiş sınıfları ortak öğeleri yeniden tanımlamak zorunda kalmadan kaydeder. Bazı durumlarda, bu ortak işlevsellik kullanılabilir bir nesne oluşturmak için yeterli değildir ve her türetilmiş sınıf eksik işlevselliği tanımlar. Böyle bir durumda, tüketen kodun yalnızca türetilmiş sınıflardan nesneler oluşturmasını istersiniz. Bunu zorlamak için temel sınıfta `MustInherit` kullanırsınız.  
  
 `MustInherit` sınıfının başka bir kullanımı, bir değişkeni ilgili sınıflar kümesiyle kısıtlamadır. Bir temel sınıf tanımlayabilir ve bu ilgili sınıfları bundan türetebilirsiniz. Temel sınıfın tüm türetilmiş sınıflarda ortak bir işlev sağlaması gerekmez, ancak değişkenlere değer atamak için bir filtre işlevi görebilir. Tüketim kodunuz temel sınıf olarak bir değişken bildirirse Visual Basic, yalnızca türetilmiş sınıflardan birindeki bir nesneyi bu değişkene atamanıza izin verir.  
  
 .NET Framework, <xref:System.Array>, <xref:System.Enum>ve <xref:System.ValueType>arasında çeşitli `MustInherit` sınıfları tanımlar. <xref:System.ValueType>, bir değişkeni kısıtlayan temel sınıfa bir örnektir. Tüm değer türleri <xref:System.ValueType>türetilir. Bir değişkeni <xref:System.ValueType>olarak bildirirseniz, bu değişkene yalnızca değer türlerini atayabilirsiniz.  
  
## <a name="rules"></a>Kurallar  
  
- **Bildirim bağlamı.** Yalnızca bir `Class` bildiriminde `MustInherit` kullanabilirsiniz.  
  
- **Birleşik değiştiriciler.** Aynı bildirimde `NotInheritable` birlikte `MustInherit` belirtemezsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, hem zorunlu devralmayı hem de geçersiz kılmayı gösterir. Temel sınıf `shape` bir değişken `acrossLine`tanımlar. Sınıflar `circle` ve `square` `shape`türetilir. `acrossLine`tanımını alırlar, ancak bu hesaplama her bir şekil türü için farklı olduğundan, bu, işlevi `area` tanımlamalıdır.  
  
 [!code-vb[VbVbalrKeywords#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#2)]  
  
 `shape1` ve `shape2` `shape`türünde olacak şekilde bildirebilirsiniz. Ancak, `shape` bir nesne oluşturamazsınız çünkü bu, işlev `area` işlevselliğine sahip ve `MustInherit`olarak işaretlenmiş.  
  
 `shape`olarak bildirildiği için, `shape1` ve `shape2` değişkenleri türetilmiş sınıflardaki nesnelerle kısıtlıdır `circle` ve `square`. Visual Basic, bu değişkenlere başka herhangi bir nesne atamanıza izin vermez, bu da size yüksek düzeyde güvenlik düzeyi sağlar.  
  
## <a name="usage"></a>Kullanım  
 `MustInherit` değiştiricisi Bu bağlamda kullanılabilir:  
  
 [Class Deyimi](../../../visual-basic/language-reference/statements/class-statement.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Inherits Deyimi](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md)
- [Anahtar Sözcükler](../../../visual-basic/language-reference/keywords/index.md)
- [Devralma Temelleri](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
