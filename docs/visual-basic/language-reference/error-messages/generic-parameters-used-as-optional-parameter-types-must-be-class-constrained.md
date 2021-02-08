---
description: 'Aşağıdakiler hakkında daha fazla bilgi edinin: BC32124: isteğe bağlı parametre türleri olarak kullanılan genel parametreler sınıf kısıtlı olmalıdır'
title: İsteğe bağlı parametre türleri olarak kullanılan genel parametreler üzerinde sınıf kısıtlaması olmalıdır
ms.date: 07/20/2015
f1_keywords:
- vbc32124
- bc32124
helpviewer_keywords:
- BC32124
ms.assetid: 55aa8b2a-9ce3-4620-a710-2f9b0feb6143
ms.openlocfilehash: 0014720d55dc4395178186b5e183d5b0279d7029
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796151"
---
# <a name="bc32124-generic-parameters-used-as-optional-parameter-types-must-be-class-constrained"></a>BC32124: isteğe bağlı parametre türleri olarak kullanılan genel parametreler sınıf kısıtlı olmalıdır

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
- [Nothing](../nothing.md)
