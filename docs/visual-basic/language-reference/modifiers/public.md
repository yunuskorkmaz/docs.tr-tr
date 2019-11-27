---
title: Genel
ms.date: 07/20/2015
f1_keywords:
- vb.Public
helpviewer_keywords:
- Public keyword [Visual Basic]
- Public keyword [Visual Basic], syntax
- Public access modifier
ms.assetid: 284c9e1b-ed23-499b-9bc9-ad87c11485a5
ms.openlocfilehash: 35bf1a65e0b8f24a1263adc480719c69b95dff9b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351290"
---
# <a name="public-visual-basic"></a>Public (Visual Basic)
Bir veya daha fazla tanımlanmış programlama öğesinin erişim kısıtlaması olmadığını belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
 Sınıf kitaplığı gibi bir bileşeni veya bileşen kümesini yayınlıyorsanız, genellikle programlama öğelerine derlemele birlikte çalışan herhangi bir kod tarafından erişilebilmesini istersiniz. Bir öğe üzerinde sınırsız erişim sağlamak için, `Public`ile bildirebilirsiniz.  
  
 Genel erişim, bir programlama öğesi için erişimi sınırlandırmanıza gerek olmadığında normal düzeydir. Bir arabirim, modül, sınıf veya yapı içinde belirtilen bir öğenin erişim düzeyinin, aksi belirtilmedikçe `Public` varsayılan olarak olduğunu unutmayın.  
  
## <a name="rules"></a>Kurallar  
  
- **Bildirim bağlamı.** `Public` yalnızca modül, arabirim veya ad alanı düzeyinde kullanabilirsiniz. Bu, bir `Public` öğesi için bildirim bağlamının kaynak dosya, ad alanı, arabirim, modül, sınıf veya yapı olması ve bir yordam olması gerektiği anlamına gelir.  
  
## <a name="behavior"></a>Davranış  
  
- **Erişim düzeyi.** Bir modüle, sınıfa veya yapıya erişebilen tüm kodlar `Public` öğelerine erişebilir.  
  
- **Varsayılan erişim.** Bir yordamın içindeki yerel değişkenler, genel erişim için varsayılan olarak kullanılır ve bunlara herhangi bir erişim değiştiricisi kullanamazsınız.  
  
- **Erişim değiştiricileri.** Erişim düzeyi belirten anahtar sözcüklere *erişim değiştiricileri*denir. Erişim değiştiricilerinden oluşan bir karşılaştırma için bkz. [Visual Basic erişim düzeyleri](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 `Public` değiştiricisi şu bağlamlarda kullanılabilir:  
  
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
- [Visual Basic erişim düzeyleri](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Yordamlar](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [Yapılar](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Nesneler ve Sınıflar](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
