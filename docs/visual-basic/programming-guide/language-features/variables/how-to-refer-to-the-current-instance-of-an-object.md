---
title: 'Nasıl yapılır: Bir Nesnenin Geçerli Örneğine Başvurma (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], object
- objects [Visual Basic], referring to current instance
- instances [Visual Basic], referring to current
- current instance
- object variables [Visual Basic]
ms.assetid: 7f9b2c77-03cd-428f-adc2-b18070226e7c
ms.openlocfilehash: c1b79f1b6a9768941d6fe966c5b5886ea742f808
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648365"
---
# <a name="how-to-refer-to-the-current-instance-of-an-object-visual-basic"></a>Nasıl yapılır: Bir Nesnenin Geçerli Örneğine Başvurma (Visual Basic)
*Geçerli örnek* bir nesne, kod şu anda Yürütülüyor örneğidir.  
  
 Kullandığınız `Me` geçerli örneğine başvurma anahtar sözcüğü.  
  
### <a name="to-refer-to-the-current-instance"></a>Geçerli örneğine başvurma  
  
-   Kullanmak `Me` anahtar sözcüğü burada normalde kullandığınız bir nesne değişkeninin adı.  
  
    ```  
    Me.ForeColor = System.Drawing.Color.Crimson  
    Me.Close()  
    ```  
  
     Ancak `Me` bir nesne gibi davranır değişken, edemezsiniz bildirirken veya hiçbir şey atayın. `Me` her zaman geçerli örneğine başvurur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nesne Değişkenleri](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [Nesne Değişkeni Ataması](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)  
 [Me, My, MyBase ve MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
