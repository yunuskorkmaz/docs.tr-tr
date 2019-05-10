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
ms.openlocfilehash: 70955cd55dfb91d4111e59ae58bfe409a4470433
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64663538"
---
# <a name="how-to-refer-to-the-current-instance-of-an-object-visual-basic"></a>Nasıl yapılır: (Visual Basic) bir nesnenin geçerli örneğine başvurma
*Geçerli örneğin* nesnenin hangi kod şu anda Yürütülüyor örneğidir.  
  
 Kullandığınız `Me` geçerli örneğine başvurma anahtar sözcüğü.  
  
### <a name="to-refer-to-the-current-instance"></a>Geçerli örneğine başvurma  
  
- Kullanma `Me` anahtar sözcüğü nerede normalde kullandığınız bir nesne değişkeninin adı.  
  
    ```  
    Me.ForeColor = System.Drawing.Color.Crimson  
    Me.Close()  
    ```  
  
     Olsa da `Me` davranacağını gibi bir nesne değişkeni, bildirmek veya herhangi bir şey atayın. `Me` her zaman geçerli örneğine başvurur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nesne Değişkenleri](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Nesne Değişkeni Ataması](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [Me, My, MyBase ve MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
