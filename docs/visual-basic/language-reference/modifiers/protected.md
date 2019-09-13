---
title: Korumalı (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Protected
helpviewer_keywords:
- Protected Friend keyword combination
- Protected keyword [Visual Basic], and Friend
- Protected keyword [Visual Basic], syntax
- Protected access modifier
- Protected keyword [Visual Basic]
ms.assetid: 74ad3d56-309f-49d2-b60c-1d0157d010e8
ms.openlocfilehash: a80e504cc8e88dfc8968f70fee2c17991b28aff5
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929466"
---
# <a name="protected-visual-basic"></a>Korumalı (Visual Basic)
Bir veya daha fazla tanımlanmış programlama öğesinin yalnızca kendi sınıfının içinden veya türetilmiş bir sınıftan erişilebilir olduğunu belirten bir üye erişim değiştiricisi.  
  
## <a name="remarks"></a>Açıklamalar  
 Bazen bir sınıfta tanımlanan programlama öğesi hassas veriler veya kısıtlı kod içeriyorsa ve öğeye erişimi sınırlandırmak istiyorsanız. Ancak, sınıf devralınabilir ise ve türetilmiş sınıfların hiyerarşisini düşünüyorsanız, bu türetilmiş sınıfların verilere veya koda erişmesi gerekebilir. Böyle bir durumda, öğesinin hem taban sınıftan hem de tüm türetilmiş sınıflardan erişilebilir olmasını istersiniz. Bu şekilde bir öğeye erişimi sınırlandırmak için, ile `Protected`bildirimini yapabilirsiniz.  

> [!NOTE]
> `Protected` Erişim değiştiricisi iki farklı değiştiriciyle birleştirilebilir:
>
> - [Protected Friend](protected-friend.md) değiştiricisi, bir sınıf üyesini türetilmiş sınıflardan ve sınıfın tanımlandığı aynı derlemeden erişilebilir hale getirir. 
> - [Özel korumalı](private-protected.md) değiştirici, bir sınıf üyesini türetilmiş türler tarafından erişilebilir hale getirir, ancak yalnızca kendi kapsayıcı bütünleştirilmiş kodu içinde.
  
## <a name="rules"></a>Kurallar  
  
- **Bildirim bağlamı.** Yalnızca sınıf düzeyinde `Protected` kullanabilirsiniz. Yani bir `Protected` öğe için bildirim bağlamı bir sınıf olmalıdır ve kaynak dosya, ad alanı, arabirim, modül, yapı veya yordam olamaz.  

## <a name="behavior"></a>Davranış  
  
- **Erişim düzeyi.** Bir sınıftaki tüm kod öğelerine erişebilir. Bir taban sınıftan türetilen herhangi bir sınıftaki kod, temel sınıfın tüm `Protected` öğelerine erişebilir. Bu, tüm türetme oluşumlarında geçerlidir. Bu, bir sınıfın temel sınıfın temel `Protected` sınıfının öğelerine erişebileceği anlamına gelir.  
  
     Korumalı erişim arkadaş erişiminin bir üst kümesi veya alt kümesi değil.  
  
- **Erişim değiştiricileri.** Erişim düzeyi belirten anahtar sözcüklere *erişim değiştiricileri*denir. Erişim değiştiricilerinden oluşan bir karşılaştırma için bkz. [Visual Basic erişim düzeyleri](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 `Protected` Değiştirici şu bağlamlarda kullanılabilir:  
  
 [Class Deyimi](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Const Deyimi](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [Declare Deyimi](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Delegate Deyimi](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [Dim Deyimi](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Enum Deyimi](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [Event Deyimi](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Function Deyimi](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Interface Deyimi](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [Property Deyimi](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Structure Deyimi](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Sub Deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Public](../../../visual-basic/language-reference/modifiers/public.md)
- [Friend](../../../visual-basic/language-reference/modifiers/friend.md)
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
- [Private Protected](private-protected.md)
- [Protected Friend](protected-friend.md)
- [Visual Basic erişim düzeyleri](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Yordamlar](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [Yapılar](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Nesneler ve Sınıflar](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
