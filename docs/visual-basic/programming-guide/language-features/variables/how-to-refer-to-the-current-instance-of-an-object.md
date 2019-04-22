---
title: 'Nasıl yapılır: (Visual Basic) bir nesnenin geçerli örneğine başvurma'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], object
- objects [Visual Basic], referring to current instance
- instances [Visual Basic], referring to current
- current instance
- object variables [Visual Basic]
ms.assetid: 7f9b2c77-03cd-428f-adc2-b18070226e7c
ms.openlocfilehash: 3c44748798d5ed554fc9fbded9c3a4d981a66d2f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58823369"
---
# <a name="how-to-refer-to-the-current-instance-of-an-object-visual-basic"></a>Nasıl yapılır: (Visual Basic) bir nesnenin geçerli örneğine başvurma
*Geçerli örneğin* nesnenin hangi kod şu anda Yürütülüyor örneğidir.  
  
 Kullandığınız `Me` geçerli örneğine başvurma anahtar sözcüğü.  
  
### <a name="to-refer-to-the-current-instance"></a>Geçerli örneğine başvurma  
  
-   Kullanma `Me` anahtar sözcüğü nerede normalde kullandığınız bir nesne değişkeninin adı.  
  
    ```  
    Me.ForeColor = System.Drawing.Color.Crimson  
    Me.Close()  
    ```  
  
     Olsa da `Me` davranacağını gibi bir nesne değişkeni, bildirmek veya herhangi bir şey atayın. `Me` her zaman geçerli örneğine başvurur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nesne Değişkenleri](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Nesne Değişkeni Ataması](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [Me, My, MyBase ve MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
