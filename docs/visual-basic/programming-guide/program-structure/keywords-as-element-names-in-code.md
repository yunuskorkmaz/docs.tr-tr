---
title: Kodda Öğe Adları Olarak Anahtar Sözcükler (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, naming conventions
- keywords [Visual Basic], in code
- name conflicts [Visual Basic]
- element names [Visual Basic], in code
ms.assetid: 2e4e8e02-23f7-49b9-a1c8-2b0402b6b525
ms.openlocfilehash: c247ada67f6554362f287cf252dd49856c4995da
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61955590"
---
# <a name="keywords-as-element-names-in-code-visual-basic"></a>Kodda Öğe Adları Olarak Anahtar Sözcükler (Visual Basic)
Herhangi bir program öğesi — bir değişkeni, sınıf veya üye gibi — kısıtlı bir anahtar sözcüğü ile aynı ada sahip olabilir. Örneğin, adında bir değişken oluşturabilirsiniz `Loop`. Ancak, sürümü için başvuruda bulunmak için — kısıtlı aynı ada sahip `Loop` anahtar sözcüğü — tam nitelenmiş dizesiyle önünde veya köşeli parantez içine (`[ ]`), aşağıdaki örnekte gösterildiği gibi.  
  
 [!code-vb[VbVbcnConventions#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#8)]  
  
 Bunlardan birini yapmak sonra Visual Basic varsayar iç kullanımı `Loop` anahtar sözcüğü ve aşağıdaki örnekte olduğu gibi bir hata oluşturur:  
  
 `' The following statement causes a compiler error.`  
  
 `Loop.Visible = True`  
  
 Formlar ve denetimler için söz konusu olduğunda ve ne zaman köşeli ayraç kullanabileceğiniz bir değişken bildirme veya kısıtlanmış bir anahtar aynı ada sahip bir yordam tanımlama. Adları uygun veya köşeli ayraçlar dahil olan ve bu nedenle kodunuza hatalara ve okumak daha zor hale unutmak çok kolaydır olabilir. Bu nedenle, sınırlı anahtar sözcükleri program öğelerinin adlarını kullanmamanızı öneririz. Visual Basic gelecek bir sürümünde yeni bir anahtar sözcüğü bir var olan form veya denetim adı ile çakışan tanımlar, ancak daha sonra bu tekniği kodunuzu güncelleştirirken yeni sürümle çalışmak için kullanabilirsiniz.  
  
> [!NOTE]
>  Programınız, ayrıca diğer başvurulan derlemelerde tarafından sağlanan öğe adları içerebilir. Bu adlar sınırlı anahtar sözcüklerle arasında çakışma varsa, daha sonra bunları köşeli ayraç yerleştirme tanımlanmış, öğelerin yorumlamaya Visual Basic neden olur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic adlandırma kuralları](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
- [Program Yapısı ve Kod Kuralları](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [Anahtar Sözcükler](../../../visual-basic/language-reference/keywords/index.md)
