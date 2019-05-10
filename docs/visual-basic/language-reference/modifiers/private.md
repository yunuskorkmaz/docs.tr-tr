---
title: Özel (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Private
helpviewer_keywords:
- Private keyword [Visual Basic]
- Private keyword [Visual Basic], syntax
ms.assetid: aba74a2e-5824-4613-bf63-b9ec7787f4e6
ms.openlocfilehash: ddb2d165de330758f58fbbcb5872e820e639808f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64642794"
---
# <a name="private-visual-basic"></a>Özel (Visual Basic)
Bir veya daha fazla bildirilmiş programlama öğesine yalnızca gelen içinde kapsanan tüm türleri dahil olmak üzere bildirim bağlamları içinde erişilebileceğini belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir programlama öğesi özel işlevleri temsil eder ya da gizli veriler içeren, genellikle erişimi mümkün olduğunca kesinlikle sınırlamak istiyorsunuz. En fazla sınırlama, yalnızca modül, sınıf veya ona erişmek için tanımladığı yapısı sağlayarak elde edin. Bu şekilde bir öğe erişimi sınırlamak için onunla bildirebilirsiniz `Private`.  

> [!NOTE]
> Ayrıca [Protected Private](private-protected.md) erişim değiştiricisi, üye erişilebilir bir sınıftaki ve türetilen sınıflar, kapsayan bir derlemede yer sağlar.

## <a name="rules"></a>Kurallar  

- **Bildirim bağlamı.** Kullanabileceğiniz `Private` yalnızca Modül düzeyinde. Bildirim bağlamı başka bir deyişle bir `Private` öğesi bir modül, sınıf veya yapı olmalıdır ve bir kaynak dosyası, ad alanı, arabirim ya da yordamın olamaz.  
  
## <a name="behavior"></a>Davranış  
  
- **Erişim düzeyi.** Bildirim bağlam içinde tüm kod erişip kendi `Private` öğeleri. Bu, iç içe geçmiş bir sınıf veya bir sabit listesi içindeki bir atama ifadesi gibi bağımsız bir tür içindeki kodu içerir. Bildirim bağlamı dışında hiçbir kod erişip kendi `Private` öğeleri.  
  
- **Erişim değiştiricileri.** Erişim düzeyini sağlayacaklarını anahtar sözcükleri adlı *erişim değiştiricilerine*. Erişim değiştiricileri bir karşılaştırması için bkz: [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 `Private` Bu bağlamda değiştirici kullanılabilir:  
  
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
- [Protected](../../../visual-basic/language-reference/modifiers/protected.md)
- [Friend](../../../visual-basic/language-reference/modifiers/friend.md)
- [Private Protected](./private-protected.md)
- [Korumalı Friend](./protected-friend.md)[erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Yordamlar](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [Yapılar](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Nesneler ve Sınıflar](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
