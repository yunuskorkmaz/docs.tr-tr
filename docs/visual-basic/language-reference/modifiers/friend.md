---
title: Arkadaş
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
ms.openlocfilehash: 4ac8e5942cf6097642ec111992ebfcdb91e8d7c1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392177"
---
# <a name="friend-visual-basic"></a>Arkadaş (Visual Basic)
Bir veya daha fazla tanımlanmış programlama öğesine, yalnızca bildirimini içeren derlemenin içinden erişilebilir olduğunu belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
 Çoğu durumda, sınıflar ve yapılar gibi programlama öğelerinin, yalnızca bunları bildiren bileşen tarafından değil, tüm derleme tarafından kullanılmasını istersiniz. Ancak, bunların derleme dışındaki kod tarafından erişilebilmesini istemeyebilirsiniz (örneğin, uygulama özel ise). Bu şekilde bir öğeye erişimi sınırlandırmak istiyorsanız, değiştiricisini kullanarak bunu bildirebilirsiniz `Friend` .  
  
 Aynı derlemeye derlenen diğer sınıf, yapı ve modüllerindeki kod, `Friend` Bu derlemedeki tüm öğelere erişebilir.  
  
 `Friend`erişim genellikle bir uygulamanın programlama öğeleri için tercih edilen düzeydir ve `Friend` bir arabirimin, modülün, sınıfın veya yapının varsayılan erişim düzeyidir.  
  
 `Friend`Yalnızca modül, arabirim veya ad alanı düzeyinde kullanabilirsiniz. Bu nedenle, bir öğe için bildirim bağlamı `Friend` bir kaynak dosyası, bir ad alanı, arabirim, bir modül, sınıf veya yapı olmalıdır; bir yordam olamaz.  

> [!NOTE]
> Ayrıca, bir sınıf üyesini bu sınıftan, türetilmiş sınıflardan ve sınıfın tanımlandığı aynı derlemeden erişilebilir hale getiren [Protected Friend](protected-friend.md) erişim değiştiricisini de kullanabilirsiniz. Bir üyenin sınıfından ve aynı derlemede bulunan türetilmiş sınıflardan erişimi kısıtlamak için, [özel korumalı](private-protected.md) erişim değiştiricisini kullanırsınız.

 `Friend`Ve diğer erişim değiştiricilerine ilişkin bir karşılaştırma için bkz. [Visual Basic erişim düzeyleri](../../programming-guide/language-features/declared-elements/access-levels.md).  
  
> [!NOTE]
> Başka bir derlemenin, olarak işaretlenen tüm türlere ve üyelere erişmesine izin veren bir Friend derlemesi olduğunu belirtebilirsiniz `Friend` . Daha fazla bilgi için bkz. [arkadaş derlemeler](../../../standard/assembly/friend.md).

## <a name="example"></a>Örnek  
 Aşağıdaki sınıf, `Friend` aynı derleme içindeki diğer programlama öğelerinin belirli üyelere erişmesine izin vermek için değiştiricisini kullanır.  
  
 [!code-vb[VbVbalrAccessModifiers#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalraccessmodifiers/vb/class1.vb#1)]  
  
## <a name="usage"></a>Kullanım  
 `Friend`Değiştiricisini şu bağlamlarda kullanabilirsiniz:  
  
 [Class Deyimi](../statements/class-statement.md)  
  
 [Const Deyimi](../statements/const-statement.md)  
  
 [Declare Deyimi](../statements/declare-statement.md)  
  
 [Delegate Deyimi](../statements/delegate-statement.md)  
  
 [Dim Deyimi](../statements/dim-statement.md)  
  
 [Enum Deyimi](../statements/enum-statement.md)  
  
 [Event Deyimi](../statements/event-statement.md)  
  
 [Function Deyimi](../statements/function-statement.md)  
  
 [Interface Deyimi](../statements/interface-statement.md)  
  
 [Module Deyimi](../statements/module-statement.md)  
  
 [Property Deyimi](../statements/property-statement.md)  
  
 [Structure Yapısı](../statements/structure-statement.md)  
  
 [Sub Deyimi](../statements/sub-statement.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [Geneldir](public.md)
- [Korunamadı](protected.md)
- [Özelleştirme](private.md)
- [Özel korumalı](./private-protected.md)
- [Protected Friend](./protected-friend.md)
- [Visual Basic erişim düzeyleri](../../programming-guide/language-features/declared-elements/access-levels.md)
- [Yordamlar](../../programming-guide/language-features/procedures/index.md)
- [Yapılar](../../programming-guide/language-features/data-types/structures.md)
- [Nesneler ve sınıflar](../../programming-guide/language-features/objects-and-classes/index.md)
