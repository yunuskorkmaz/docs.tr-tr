---
title: Kodda Öğe Adları Olarak Anahtar Sözcükler (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, naming conventions
- keywords [Visual Basic], in code
- name conflicts [Visual Basic]
- element names [Visual Basic], in code
ms.assetid: 2e4e8e02-23f7-49b9-a1c8-2b0402b6b525
ms.openlocfilehash: 53c3172e8518115d001c23be2430fbc87ae1b60f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
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
 [Program Yapısı ve Kod Kuralları](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 [Anahtar Sözcükler](../../../visual-basic/language-reference/keywords/index.md)
