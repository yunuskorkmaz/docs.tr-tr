---
title: "Kodda Öğe Adları Olarak Anahtar Sözcükler (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, naming conventions
- keywords [Visual Basic], in code
- name conflicts [Visual Basic]
- element names [Visual Basic], in code
ms.assetid: 2e4e8e02-23f7-49b9-a1c8-2b0402b6b525
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f410a0eaac0dcc034d406a89ed1d01a8f228a583
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="keywords-as-element-names-in-code-visual-basic"></a>Kodda Öğe Adları Olarak Anahtar Sözcükler (Visual Basic)
Herhangi bir program öğesi — bir değişkeni, sınıf veya üye gibi — sınırlı anahtar sözcüğü ile aynı ada sahip olabilir. Örneğin, adında bir değişken oluşturabilirsiniz `Loop`. Ancak, bunu sürümünüz için başvurmak için — kısıtlanmış aynı ada sahip `Loop` anahtar sözcüğü — tam nitelenmiş dizesiyle önünde veya köşeli parantez içine almanız (`[ ]`), aşağıdaki örnekte gösterildiği gibi.  
  
 [!code-vb[VbVbcnConventions#8](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/keywords-as-element-names-in-code_1.vb)]  
  
 Bunlardan birini yapmak sonra Visual Basic varsayar iç kullanımını `Loop` anahtar sözcüğü ve aşağıdaki örnekteki gibi bir hata üretir:  
  
 `' The following statement causes a compiler error.`  
  
 `Loop.Visible = True`  
  
 Formlar ve denetimler için söz konusu olduğunda ve ne zaman köşeli kullanabileceğiniz bir değişken bildirme veya aynı ada sahip bir yordamı kısıtlanmış bir anahtar sözcük olarak tanımlama. Adları nitelemeniz veya köşeli içerir ve bu nedenle kodunuza hatalara ve okumak daha zor hale unuttunuz kolay olabilir. Bu nedenle, sınırlı anahtar sözcükleri program öğe adları olarak kullanmamanızı öneririz. Visual Basic gelecek bir sürümünde yeni bir anahtar sözcük varolan form veya denetim adı ile çakışan tanımlıyorsa, ancak daha sonra bu teknik kodunuzu güncelleştirilirken yeni sürümle çalışmak için kullanabilirsiniz.  
  
> [!NOTE]
>  Programınızı diğer başvurulan derlemeler tarafından sağlanan öğe adları de içerebilir. Bu adları sınırlı anahtar sözcükleriyle çakışma varsa, bunları köşeli ayraç yerleştirme tanımlanan öğelerinizi yorumlamak Visual Basic neden olur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic adlandırma kuralları](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 [Program yapısı ve kod kuralları](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 [Anahtar sözcükler](../../../visual-basic/language-reference/keywords/index.md)
