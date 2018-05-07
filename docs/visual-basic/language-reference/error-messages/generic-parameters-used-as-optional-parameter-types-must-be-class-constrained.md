---
title: İsteğe bağlı parametre türleri olarak kullanılan genel parametreler üzerinde sınıf kısıtlaması olmalıdır
ms.date: 07/20/2015
f1_keywords:
- vbc32124
- bc32124
helpviewer_keywords:
- BC32124
ms.assetid: 55aa8b2a-9ce3-4620-a710-2f9b0feb6143
ms.openlocfilehash: 7e2b59f758ef236717a912694576b514e2ae8a60
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="generic-parameters-used-as-optional-parameter-types-must-be-class-constrained"></a>İsteğe bağlı parametre türleri olarak kullanılan genel parametreler üzerinde sınıf kısıtlaması olmalıdır
Bir yordam bir başvuru türü kısıtlı olmayan bir tür parametresi kullanan isteğe bağlı bir parametre ile bildirilir.  
  
 Her zaman her isteğe bağlı bir parametre için varsayılan bir değer sağlamanız gerekir. Parametre bir başvuru türü ise, isteğe bağlı değeri olmalıdır `Nothing`, herhangi bir başvuru türü için geçerli bir değer değil. Ancak, parametre değeri türü ise, bu tür Visual Basic tarafından önceden tanımlanmış bir başlangıç veri türü olmalıdır. Bir kullanıcı tarafından tanımlanan yapısı gibi bir bileşik değeri türü geçerli varsayılan değere sahip olmasıdır.  
  
 İsteğe bağlı bir parametre için bir tür parametresi kullandığınızda, geçerli varsayılan bir değeri ile bir değer türü olasılığını önlemek için başvuru türünde olduğunu güvence altına almalıdır. Bu, gerekir sınırlamak tür parametresi ile birlikte gelir `Class` anahtar sözcüğü veya belirli bir sınıf adı.  
  
 **Hata Kimliği:** BC32124  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Yalnızca bir başvuru türü kabul etmek için tür parametresi sınırlamak veya isteğe bağlı bir parametre için kullanmayın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic'de genel türler](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Tür Listesi](../../../visual-basic/language-reference/statements/type-list.md)  
 [Class Deyimi](../../../visual-basic/language-reference/statements/class-statement.md)  
 [İsteğe Bağlı Parametreler](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)  
 [Yapılar](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Nothing](../../../visual-basic/language-reference/nothing.md)
