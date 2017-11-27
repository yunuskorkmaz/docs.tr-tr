---
title: "Nasıl yapılır: Bir Nesnenin Geçerli Örneğine Başvurma (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- variables [Visual Basic], object
- objects [Visual Basic], referring to current instance
- instances [Visual Basic], referring to current
- current instance
- object variables [Visual Basic]
ms.assetid: 7f9b2c77-03cd-428f-adc2-b18070226e7c
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 33ea612253b00e12f47258189da4ac7d8d98ade5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
  
     Ancak `Me` bir nesne gibi davranır değişken, edemezsiniz bildirirken veya hiçbir şey atayın. `Me`her zaman geçerli örneğine başvurur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nesne değişkenleri](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [Nesne değişkeni ataması](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)  
 [Me, My, MyBase ve MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
