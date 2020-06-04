---
title: Ortak
ms.date: 07/20/2015
f1_keywords:
- vb.Public
helpviewer_keywords:
- Public keyword [Visual Basic]
- Public keyword [Visual Basic], syntax
- Public access modifier
ms.assetid: 284c9e1b-ed23-499b-9bc9-ad87c11485a5
ms.openlocfilehash: 35332e50227cdef6386362df17c10b5b2cdaa689
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415355"
---
# <a name="public-visual-basic"></a>Public (Visual Basic)
Bir veya daha fazla tanımlanmış programlama öğesinin erişim kısıtlaması olmadığını belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
 Sınıf kitaplığı gibi bir bileşeni veya bileşen kümesini yayınlıyorsanız, genellikle programlama öğelerine derlemele birlikte çalışan herhangi bir kod tarafından erişilebilmesini istersiniz. Bir öğe üzerinde sınırsız erişim sağlamak için, ile bildirimini yapabilirsiniz `Public` .  
  
 Genel erişim, bir programlama öğesi için erişimi sınırlandırmanıza gerek olmadığında normal düzeydir. Bir arabirim, modül, sınıf veya yapı içinde belirtilen bir öğenin erişim düzeyinin, aksi belirtilmedikçe, varsayılan olarak olduğunu unutmayın `Public` .  
  
## <a name="rules"></a>Kurallar  
  
- **Bildirim bağlamı.** `Public`Yalnızca modül, arabirim veya ad alanı düzeyinde kullanabilirsiniz. Bu, bir öğe için bildirim bağlamının `Public` bir kaynak dosya, ad alanı, arabirim, modül, sınıf veya yapı olması gerektiği anlamına gelir ve bir yordam olamaz.  
  
## <a name="behavior"></a>Davranış  
  
- **Erişim düzeyi.** Bir modüle, sınıfa veya yapıya erişebilen tüm kodlar `Public` öğelerine erişebilir.  
  
- **Varsayılan erişim.** Bir yordamın içindeki yerel değişkenler, genel erişim için varsayılan olarak kullanılır ve bunlara herhangi bir erişim değiştiricisi kullanamazsınız.  
  
- **Erişim değiştiricileri.** Erişim düzeyi belirten anahtar sözcüklere *erişim değiştiricileri*denir. Erişim değiştiricilerinden oluşan bir karşılaştırma için bkz. [Visual Basic erişim düzeyleri](../../programming-guide/language-features/declared-elements/access-levels.md).  
  
 `Public`Değiştirici şu bağlamlarda kullanılabilir:  
  
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
  
 [Operator Deyimi](../statements/operator-statement.md)  
  
 [Property Deyimi](../statements/property-statement.md)  
  
 [Structure Yapısı](../statements/structure-statement.md)  
  
 [Sub Deyimi](../statements/sub-statement.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Korunamadı](protected.md)
- [Dost](friend.md)
- [Özelleştirme](private.md)
- [Özel korumalı](private-protected.md)
- [Protected Friend](protected-friend.md)
- [Visual Basic erişim düzeyleri](../../programming-guide/language-features/declared-elements/access-levels.md)
- [Yordamlar](../../programming-guide/language-features/procedures/index.md)
- [Yapılar](../../programming-guide/language-features/data-types/structures.md)
- [Nesneler ve sınıflar](../../programming-guide/language-features/objects-and-classes/index.md)
