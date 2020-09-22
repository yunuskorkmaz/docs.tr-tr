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
ms.openlocfilehash: 6502da947ae331a26e66d8ce2dbcda46e4172a6e
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867960"
---
# <a name="mustinherit-visual-basic"></a>MustInherit (Visual Basic)

Bir sınıfın sadece temel sınıf olarak kullanılabileceğini ve doğrudan bundan bir nesne oluşturkullanılamayacağını belirtir.  
  
## <a name="remarks"></a>Açıklamalar  

 *Temel sınıfın* amacı ( *soyut sınıf*olarak da bilinir), bundan türetilmiş tüm sınıflar için ortak olan işlevleri tanımlamaktır. Bu, türetilmiş sınıfları ortak öğeleri yeniden tanımlamak zorunda kalmadan kaydeder. Bazı durumlarda, bu ortak işlevsellik kullanılabilir bir nesne oluşturmak için yeterli değildir ve her türetilmiş sınıf eksik işlevselliği tanımlar. Böyle bir durumda, tüketen kodun yalnızca türetilmiş sınıflardan nesneler oluşturmasını istersiniz. `MustInherit`Bunu zorlamak için temel sınıfta kullanın.  
  
 Bir sınıfının başka bir kullanımı `MustInherit` , bir değişkeni ilgili sınıflar kümesiyle kısıtlamadır. Bir temel sınıf tanımlayabilir ve bu ilgili sınıfları bundan türetebilirsiniz. Temel sınıfın tüm türetilmiş sınıflarda ortak bir işlev sağlaması gerekmez, ancak değişkenlere değer atamak için bir filtre işlevi görebilir. Tüketim kodunuz temel sınıf olarak bir değişken bildirirse Visual Basic, yalnızca türetilmiş sınıflardan birindeki bir nesneyi bu değişkene atamanıza izin verir.  
  
 .NET Framework, `MustInherit` ve arasında birkaç sınıfı tanımlar <xref:System.Array> <xref:System.Enum> <xref:System.ValueType> . <xref:System.ValueType> , bir değişkeni kısıtlayan temel sınıfa bir örnektir. Tüm değer türleri öğesinden türetilir <xref:System.ValueType> . Bir değişkeni olarak bildirirseniz <xref:System.ValueType> , bu değişkene yalnızca değer türlerini atayabilirsiniz.  
  
## <a name="rules"></a>Kurallar  
  
- **Bildirim bağlamı.** `MustInherit`Yalnızca bir `Class` ifadede kullanabilirsiniz.  
  
- **Birleşik değiştiriciler.** `MustInherit`Aynı bildirimde ile birlikte belirtemezsiniz `NotInheritable` .  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, hem zorunlu devralmayı hem de geçersiz kılmayı gösterir. Temel sınıf `shape` bir değişkeni tanımlar `acrossLine` . Sınıflar `circle` ve `square` türetilir `shape` . Tanımları devralınır `acrossLine` , ancak `area` Bu hesaplama her bir şekil türü için farklı olduğu için işlevi tanımlamalıdır.  
  
 [!code-vb[VbVbalrKeywords#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#2)]  
  
 `shape1`' İ ve `shape2` türünü belirtebilirsiniz `shape` . Ancak, `shape` işlevin işlevselliğine sahip olmadığı ve işaretlendiği için bir nesnesi oluşturamazsınız `area` `MustInherit` .  
  
 `shape`, Değişkenleri olarak bildirildiği `shape1` için, ve `shape2` türetilmiş sınıflardaki nesnelerle kısıtlıdır `circle` `square` . Visual Basic, bu değişkenlere başka herhangi bir nesne atamanıza izin vermez, bu da size yüksek düzeyde güvenlik düzeyi sağlar.  
  
## <a name="usage"></a>Kullanım  

 `MustInherit`Değiştirici Bu bağlamda kullanılabilir:  
  
 [Class Deyimi](../statements/class-statement.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Inherits Deyimi](../statements/inherits-statement.md)
- [NotInheritable](notinheritable.md)
- [Anahtar sözcükler](../keywords/index.md)
- [Devralma Temelleri](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
