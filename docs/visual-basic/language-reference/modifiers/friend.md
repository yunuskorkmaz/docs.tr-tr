---
title: Arkadaş (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Friend
helpviewer_keywords:
- Friend keyword [Visual Basic]
- Friend access modifier
- Friend keyword [Visual Basic], syntax
- Protected Friend keyword combination
- Friend keyword [Visual Basic], and Protected
ms.assetid: b664605e-1c79-4728-b996-aa59c50846bc
ms.openlocfilehash: 18681935d0380f9be3970fdb5d17ffb089152f59
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61802550"
---
# <a name="friend-visual-basic"></a>Arkadaş (Visual Basic)
Bir veya daha fazla bildirilmiş programlama öğesine, bildirimi içeren derlemede yalnızca erişilebileceğini belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
 Çoğu durumda, sınıflar ve yapılar yalnızca bunları bildiren bileşen tarafından tüm derleme tarafından kullanılacak gibi öğeleri programlama istersiniz. Ancak, bunları (örneğin, uygulama özel ise) derleme dışındaki kod tarafından erişilebilmesi için istemeyebilirsiniz. Bu şekilde bir öğe erişimi sınırlandırmak istiyorsanız, bunu kullanarak bildirebilirsiniz `Friend` değiştiricisi.  
  
 Diğer sınıflar, yapılar ve aynı derlenmiş modüller kodda derleme tüm erişebilir `Friend` derlemeye öğeleri.  
  
 `Friend` erişim, genellikle uygulamanın programlama öğeleri için tercih edilen düzeyi ve `Friend` varsayılan bir arabirim, bir modül, bir sınıf veya yapı düzeyi erişimdir.  
  
 Kullanabileceğiniz `Friend` modülü, arabirim veya ad alanı düzeyinde yalnızca. Bu nedenle, bildirimi bağlamı bir `Friend` öğesi bir kaynak dosyası, bir ad alanı, bir arabirim, bir modül, bir sınıf veya yapı olmalıdır; bir yordam olamaz.  

> [!NOTE]
> Ayrıca [Protected Friend](protected-friend.md) erişim değiştiricisi, bir sınıf üyesinin Bu sınıf, türetilen sınıflar ve sınıf tanımlanır aynı derleme içinde erişilebilir hale getirir. Sınıfı içinde ve türetilen sınıfların aynı derlemedeki bir üye erişimi kısıtlamak için kullandığınız [Protected Private](private-protected.md) erişim değiştiricisi.

 Bir karşılaştırması `Friend` ve diğer erişim değiştiricilerine bkz [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
> [!NOTE]
>  Başka bir derlemenin tüm türleri ve üyeleri olarak işaretlenmiş erişmesine izin veren bir arkadaş derleme olduğunu belirtebilirsiniz `Friend`. Daha fazla bilgi için [arkadaş derlemeleri](../../../standard/assembly/friend-assemblies.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki sınıf kullandığı `Friend` diğer programlama öğelerinin belirli üyelere erişmek için aynı bütünleştirilmiş kod içinde değiştiricisi.  
  
 [!code-vb[VbVbalrAccessModifiers#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalraccessmodifiers/vb/class1.vb#1)]  
  
## <a name="usage"></a>Kullanım  
 Kullanabileceğiniz `Friend` şu bağlamlarda değiştiricisi:  
  
 [Class Deyimi](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Const Deyimi](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [Declare Deyimi](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Delegate Deyimi](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [Dim Deyimi](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Enum Deyimi](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [Event Deyimi](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Function Deyimi](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Interface Deyimi](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [Module Deyimi](../../../visual-basic/language-reference/statements/module-statement.md)  
  
 [Property Deyimi](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Structure Deyimi](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Sub Deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [Public](../../../visual-basic/language-reference/modifiers/public.md)
- [Protected](../../../visual-basic/language-reference/modifiers/protected.md)
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
- [Private Protected](./private-protected.md)
- [Protected Friend](./protected-friend.md)
- [Visual Basic'de erişim düzeyleri](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Yordamlar](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [Yapılar](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Nesneler ve Sınıflar](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
