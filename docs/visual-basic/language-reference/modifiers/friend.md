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
ms.openlocfilehash: d906fc8ada19f22059da44acbd76dd07dacd4801
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
---
# <a name="friend-visual-basic"></a>Arkadaş (Visual Basic)
Bir veya daha fazla bildirilen programlama öğeleri bildirimleri içeren bütünleştirilmiş kodun içinde yalnızca üzerinden erişilebilir olduğunu belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
 Çoğu durumda, sınıflar ve yapılar tüm derlemesi tarafından değil yalnızca bunları bildiren bileşen tarafından kullanılmak üzere gibi programlama istiyor. Ancak, siz bunları (örneğin, uygulama özel ise) derleme dışına kodu tarafından erişilebilmesi için istemeyebilirsiniz. Bu şekilde bir öğeyi erişimi sınırlamak istiyorsanız, bunu kullanarak bildirebilirsiniz `Friend` değiştiricisi.  
  
 Diğer sınıflar, yapılar ve aynı derlenmiş modüller kodda derleme tüm erişebilir `Friend` bu derleme öğeleri.  
  
 `Friend` erişim, genellikle bir uygulama programlama öğeleri için tercih edilen düzeyi ve `Friend` varsayılan erişim bir arabirim, bir modül, bir sınıf veya bir yapı düzeyinde gerçekleşir.  
  
 Kullanabileceğiniz `Friend` modül, arabirim veya ad alanı düzeyinde yalnızca. Bu nedenle, bildirimi bağlamı için bir `Friend` kaynak dosyasını, bir ad alanı, bir arabirim, bir modül, bir sınıf veya bir yapı öğesi olması gerekir; bir yordam olamaz.  

> [!NOTE]
> Aynı zamanda [Protected Friend](protected-friend.md) sınıf üyesine bir sınıftaki, türetilen sınıflar ve sınıf tanımlanır aynı bütünleştirilmiş erişilebilir hale getirir erişim değiştiricisi. Kendi sınıfı içinde ve aynı bütünleştirilmiş kodda türetilmiş sınıflardan üyeden erişimi kısıtlamak için kullandığınız [özel korumalı](private-protected.md) erişim değiştiricisi.

 Bir karşılaştırması `Friend` ve diğer değiştiricileri erişmek için bkz: [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
> [!NOTE]
>  Başka bir derleme tüm türleri ve olarak işaretlenmiş üyeleri erişmesine izin veren bir arkadaş derleme olduğunu belirtebilirsiniz `Friend`. Daha fazla bilgi için bkz: [arkadaş derlemeleri](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki sınıf kullanır `Friend` diğer programlama öğeleri belirli üyeleri erişmek için aynı bütünleştirilmiş kod içinde izin vermek için değiştiricisi.  
  
 [!code-vb[VbVbalrAccessModifiers#1](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/friend_1.vb)]  
  
## <a name="usage"></a>Kullanım  
 Kullanabileceğiniz `Friend` bu bağlamlarında değiştiricisi:  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>  
 [Public](../../../visual-basic/language-reference/modifiers/public.md)  
 [Protected](../../../visual-basic/language-reference/modifiers/protected.md)  
 [Private](../../../visual-basic/language-reference/modifiers/private.md)  
 [Özel korumalı](./private-protected.md)   
 [Korumalı Friend](./protected-friend.md)   
 [Visual Basic'de erişim düzeyleri](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [Yordamlar](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [Yapılar](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Nesneler ve Sınıflar](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
