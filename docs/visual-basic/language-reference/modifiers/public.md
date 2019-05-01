---
title: Public (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Public
helpviewer_keywords:
- Public keyword [Visual Basic]
- Public keyword [Visual Basic], syntax
- Public access modifier
ms.assetid: 284c9e1b-ed23-499b-9bc9-ad87c11485a5
ms.openlocfilehash: 0c85564503f3c83e436044cd92ee3014945f1ef3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051877"
---
# <a name="public-visual-basic"></a>Public (Visual Basic)
Bir veya daha fazla bildirilmiş programlama öğesine hiçbir erişim kısıtlamasına sahip olmadığını belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir bileşen ya da bir sınıf kitaplığı gibi bir bileşenler kümesi yayımlıyorsanız genellikle programlama öğeleri, derleme ile birlikte çalışır herhangi bir kod tarafından erişilebilir olmasını istersiniz. Bir öğe üzerinde sınırsız erişimi confer için onunla bildirebilirsiniz `Public`.  
  
 Erişimi sınırlamak gerekmediğinde genel erişim bir programlama öğesi için normal düzeydir. Bir öğenin erişim düzeyi bir arabirimi, modül, sınıf veya yapı içinde bildirilen Not Varsayılan olarak `Public` , aksi takdirde değil bildirirseniz.  
  
## <a name="rules"></a>Kurallar  
  
- **Bildirim bağlamı.** Kullanabileceğiniz `Public` yalnızca düzeyinde modülü, arabirim veya ad alanı. Bildirim bağlamı başka bir deyişle bir `Public` öğesi bir kaynak dosyası, ad alanı, arabirim, modül, sınıf veya yapı olmalıdır ve bir yordam olamaz.  
  
## <a name="behavior"></a>Davranış  
  
- **Erişim düzeyi.** Bir modül, sınıf veya yapı erişebilen tüm kod erişip kendi `Public` öğeleri.  
  
- **Varsayılan erişim.** Yerel değişkenleri ve ortak erişimi için bir yordam varsayılan içinde herhangi bir erişim değiştiricileri üzerlerinde kullanamazsınız.  
  
- **Erişim değiştiricileri.** Erişim düzeyini sağlayacaklarını anahtar sözcükleri adlı *erişim değiştiricilerine*. Erişim değiştiricileri bir karşılaştırması için bkz: [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 `Public` Bu bağlamda değiştirici kullanılabilir:  
  
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
  
 [Operator Deyimi](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [Property Deyimi](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Structure Deyimi](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Sub Deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Protected](../../../visual-basic/language-reference/modifiers/protected.md)
- [Friend](../../../visual-basic/language-reference/modifiers/friend.md)
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
- [Private Protected](private-protected.md)
- [Protected Friend](protected-friend.md)
- [Visual Basic'de erişim düzeyleri](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Yordamlar](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [Yapılar](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Nesneler ve Sınıflar](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
