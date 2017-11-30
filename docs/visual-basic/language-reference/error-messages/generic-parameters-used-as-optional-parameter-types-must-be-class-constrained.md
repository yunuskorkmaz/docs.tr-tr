---
title: "İsteğe bağlı parametre türleri olarak kullanılan genel parametreler üzerinde sınıf kısıtlaması olmalıdır"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc32124
- bc32124
helpviewer_keywords: BC32124
ms.assetid: 55aa8b2a-9ce3-4620-a710-2f9b0feb6143
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a13ea66f12e54db4e585577e20e1f5396669f1a8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
 [Tür listesi](../../../visual-basic/language-reference/statements/type-list.md)  
 [Class deyimi](../../../visual-basic/language-reference/statements/class-statement.md)  
 [İsteğe bağlı parametreler](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)  
 [Yapıları](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Hiçbir şey](../../../visual-basic/language-reference/nothing.md)
