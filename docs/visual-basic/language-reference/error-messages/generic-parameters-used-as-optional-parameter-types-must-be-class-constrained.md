---
title: İsteğe bağlı parametre türleri olarak kullanılan genel parametreler üzerinde sınıf kısıtlaması olmalıdır
ms.date: 07/20/2015
f1_keywords:
- vbc32124
- bc32124
helpviewer_keywords:
- BC32124
ms.assetid: 55aa8b2a-9ce3-4620-a710-2f9b0feb6143
ms.openlocfilehash: 2e3f50d08fdf78b5ca9bf9e3399b00ed0328320f
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874025"
---
# <a name="generic-parameters-used-as-optional-parameter-types-must-be-class-constrained"></a>İsteğe bağlı parametre türleri olarak kullanılan genel parametreler üzerinde sınıf kısıtlaması olmalıdır

Bir yordam, bir başvuru türü olarak kısıtlanmış olmayan bir tür parametresi kullanan isteğe bağlı bir parametreyle bildirilmiştir.  
  
 Her isteğe bağlı parametre için her zaman bir varsayılan değer sağlamanız gerekir. Parametresi bir başvuru türü ise, isteğe bağlı değer `Nothing` , herhangi bir başvuru türü için geçerli bir değer olan olmalıdır. Ancak, parametre bir değer türünde ise, bu tür Visual Basic tarafından önceden tanımlanan bir elemensel veri türü olmalıdır. Bunun nedeni, Kullanıcı tanımlı yapı gibi bir bileşik değer türünün geçerli bir varsayılan değer içermez.  
  
 İsteğe bağlı bir parametre için bir tür parametresi kullandığınızda, geçerli bir varsayılan değer olmadan bir değer türü olasılığa engel olmak için bir başvuru türü olduğunu garanti etmeniz gerekir. Bu, tür parametresini `Class` anahtar sözcüğüyle veya belirli bir sınıfın adıyla sınırlandırmalısınız.  
  
 **Hata kimliği:** BC32124  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Tür parametresini yalnızca bir başvuru türünü kabul edecek şekilde sınırlayın veya isteğe bağlı parametre için kullanmayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic genel türler](../../programming-guide/language-features/data-types/generic-types.md)
- [Tür Listesi](../statements/type-list.md)
- [Class Deyimi](../statements/class-statement.md)
- [İsteğe Bağlı Parametreler](../../programming-guide/language-features/procedures/optional-parameters.md)
- [Yapılar](../../programming-guide/language-features/data-types/structures.md)
- [Yapma](../nothing.md)
