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
ms.openlocfilehash: 86758c68f0f3bfe214a695f656d3924eadd27e31
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64642680"
---
# <a name="protected-visual-basic"></a>Korumalı (Visual Basic)
Bir veya daha fazla bildirilmiş programlama öğesine belirten bir üye erişim değiştiricisi erişilebilir sadece kendi sınıfı veya türetilmiş sınıf.  
  
## <a name="remarks"></a>Açıklamalar  
 Bazen bir sınıfta bildirilen bir programlama öğesi hassas veriler ya da kısıtlı kodu içerir ve öğeye erişimi sınırlandırmak istersiniz. Ancak, devralınabilir bir sınıftır ve türetilmiş sınıflarının bir hiyerarşi beklediğiniz, bunu bu türetilmiş sınıfları veri veya kod erişmek gerekli olabilir. Böyle bir durumda, öğe temel sınıfını hem türetilen tüm sınıflardan erişilebilir olmasını istiyorsunuz. Bu şekilde bir öğe erişimi sınırlamak için onunla bildirebilirsiniz `Protected`.  

> [!NOTE]
> `Protected` Erişim değiştiricisi ile iki değiştirici birleştirilebilir:
> - [Protected Friend](protected-friend.md) değiştiricisi bir sınıf üyesi o sınıfın türetilmiş sınıflar ve sınıf tanımlanır aynı derleme içinde erişilebilir kılar. 
> - [Protected Private](private-protected.md) değiştiricisi yapar bir sınıf üyesinin erişilebilir derlemeyi içeren, kendi içinde ancak yalnızca türetilmiş türler tarafından.
  
## <a name="rules"></a>Kurallar  
  
- **Bildirim bağlamı.** Kullanabileceğiniz `Protected` yalnızca sınıf düzeyinde. Bildirim bağlamı başka bir deyişle bir `Protected` öğesi bir sınıf olması gerekir ve bir kaynak dosyası, ad alanı, arabirim, modülü, yapı veya yordamı olamaz.  

## <a name="behavior"></a>Davranış  
  
- **Erişim düzeyi.** Bir sınıftaki tüm kod öğelerine erişebilirsiniz. Kodda bir taban sınıftan türetilen herhangi bir sınıfın tüm erişebilir `Protected` öğeleri temel sınıf. Bu türetme tüm nesiller boyunca geçerlidir. Bu sınıf erişebileceği anlamına gelir `Protected` temel sınıfın temel sınıf ve benzeri öğeleri.  
  
     Korumalı Erişim, bir üst veya alt öğesine friend erişimi değil.  
  
- **Erişim değiştiricileri.** Erişim düzeyini sağlayacaklarını anahtar sözcükleri adlı *erişim değiştiricilerine*. Erişim değiştiricileri bir karşılaştırması için bkz: [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 `Protected` Bu bağlamda değiştirici kullanılabilir:  
  
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
- [Visual Basic'de erişim düzeyleri](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Yordamlar](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [Yapılar](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Nesneler ve Sınıflar](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
