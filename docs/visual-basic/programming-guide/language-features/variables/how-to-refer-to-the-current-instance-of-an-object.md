---
title: 'Nasıl yapılır: Bir Nesnenin Geçerli Örneğine Başvurma'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], object
- objects [Visual Basic], referring to current instance
- instances [Visual Basic], referring to current
- current instance
- object variables [Visual Basic]
ms.assetid: 7f9b2c77-03cd-428f-adc2-b18070226e7c
ms.openlocfilehash: 62b22a54904a45380052d3d81d9415517d4f8d3b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346891"
---
# <a name="how-to-refer-to-the-current-instance-of-an-object-visual-basic"></a>Nasıl yapılır: Bir Nesnenin Geçerli Örneğine Başvurma (Visual Basic)
Bir nesnenin *geçerli örneği* , kodun Şu anda yürütüldüğü örneğidir.  
  
 Geçerli örneğe başvurmak için `Me` anahtar sözcüğünü kullanırsınız.  
  
### <a name="to-refer-to-the-current-instance"></a>Geçerli örneğe başvurmak için  
  
- Bir nesne değişkeninin adını normalde kullandığınız `Me` anahtar sözcüğünü kullanın.  
  
    ```vb  
    Me.ForeColor = System.Drawing.Color.Crimson  
    Me.Close()  
    ```  
  
     `Me` bir nesne değişkeni gibi davransa da, bunu bildiremez veya buna hiçbir şey atayamazsınız. `Me` her zaman geçerli örneğe başvurur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nesne Değişkenleri](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Nesne Değişkeni Ataması](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [Me, My, MyBase ve MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
