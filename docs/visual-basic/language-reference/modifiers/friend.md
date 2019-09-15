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
ms.openlocfilehash: 2a5a2d6b9d99693a551480fa047cedf42888fdf3
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70969047"
---
# <a name="friend-visual-basic"></a>Arkadaş (Visual Basic)
Bir veya daha fazla tanımlanmış programlama öğesine, yalnızca bildirimini içeren derlemenin içinden erişilebilir olduğunu belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
 Çoğu durumda, sınıflar ve yapılar gibi programlama öğelerinin, yalnızca bunları bildiren bileşen tarafından değil, tüm derleme tarafından kullanılmasını istersiniz. Ancak, bunların derleme dışındaki kod tarafından erişilebilmesini istemeyebilirsiniz (örneğin, uygulama özel ise). Bu şekilde bir öğeye erişimi sınırlandırmak istiyorsanız, `Friend` değiştiricisini kullanarak bunu bildirebilirsiniz.  
  
 Aynı derlemeye derlenen diğer sınıf, yapı ve modüllerindeki kod, bu derlemedeki tüm `Friend` öğelere erişebilir.  
  
 `Friend`erişim genellikle bir uygulamanın programlama öğeleri için tercih edilen düzeydir ve `Friend` bir arabirimin, modülün, sınıfın veya yapının varsayılan erişim düzeyidir.  
  
 Yalnızca modül, `Friend` arabirim veya ad alanı düzeyinde kullanabilirsiniz. Bu nedenle, bir `Friend` öğe için bildirim bağlamı bir kaynak dosyası, bir ad alanı, arabirim, bir modül, sınıf veya yapı olmalıdır; bir yordam olamaz.  

> [!NOTE]
> Ayrıca, bir sınıf üyesini bu sınıftan, türetilmiş sınıflardan ve sınıfın tanımlandığı aynı derlemeden erişilebilir hale getiren [Protected Friend](protected-friend.md) erişim değiştiricisini de kullanabilirsiniz. Bir üyenin sınıfından ve aynı derlemede bulunan türetilmiş sınıflardan erişimi kısıtlamak için, [özel korumalı](private-protected.md) erişim değiştiricisini kullanırsınız.

 `Friend` Ve diğer erişim değiştiricilerine ilişkin bir karşılaştırma için bkz. [Visual Basic erişim düzeyleri](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
> [!NOTE]
> Başka bir derlemenin, olarak `Friend`işaretlenen tüm türlere ve üyelere erişmesine izin veren bir Friend derlemesi olduğunu belirtebilirsiniz. Daha fazla bilgi için bkz. [arkadaş derlemeler](../../../standard/assembly/friend.md).

## <a name="example"></a>Örnek  
 Aşağıdaki sınıf, aynı derleme `Friend` içindeki diğer programlama öğelerinin belirli üyelere erişmesine izin vermek için değiştiricisini kullanır.  
  
 [!code-vb[VbVbalrAccessModifiers#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalraccessmodifiers/vb/class1.vb#1)]  
  
## <a name="usage"></a>Kullanım  
 `Friend` Değiştiricisini şu bağlamlarda kullanabilirsiniz:  
  
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
- [Visual Basic erişim düzeyleri](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Yordamlar](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [Yapılar](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Nesneler ve Sınıflar](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
