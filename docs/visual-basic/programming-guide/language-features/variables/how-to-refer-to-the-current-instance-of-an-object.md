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
ms.openlocfilehash: 43bfd54592fb1d26cbf7f268b7e098e01e3745d8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410431"
---
# <a name="how-to-refer-to-the-current-instance-of-an-object-visual-basic"></a>Nasıl yapılır: Bir Nesnenin Geçerli Örneğine Başvurma (Visual Basic)
Bir nesnenin *geçerli örneği* , kodun Şu anda yürütüldüğü örneğidir.  
  
 `Me`Geçerli örneğe başvurmak için anahtar sözcüğünü kullanırsınız.  
  
### <a name="to-refer-to-the-current-instance"></a>Geçerli örneğe başvurmak için  
  
- `Me`Normalde bir nesne değişkeninin adını kullanacağınız anahtar sözcüğünü kullanın.  
  
    ```vb  
    Me.ForeColor = System.Drawing.Color.Crimson  
    Me.Close()  
    ```  
  
     `Me`Bir nesne değişkeni gibi davranmakla birlikte, bunu bildiremez veya buna hiçbir şey atayamazsınız. `Me`her zaman geçerli örneğe başvurur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nesne Değişkenleri](object-variables.md)
- [Nesne Değişkeni Ataması](object-variable-assignment.md)
- [Me, My, MyBase ve MyClass](../../program-structure/me-my-mybase-and-myclass.md)
