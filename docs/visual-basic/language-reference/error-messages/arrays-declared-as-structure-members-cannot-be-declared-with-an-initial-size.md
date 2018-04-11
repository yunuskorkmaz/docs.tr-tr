---
title: Yapı üyeleri olarak bildirilen diziler için başlangıç boyutu bildirilemez
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31043
- bc31043
helpviewer_keywords:
- BC31043
ms.assetid: 5bd90c71-1b78-444b-91e1-4789451ef085
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 983154a144a79991c86db5056ad0e0e563a3ba73
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="arrays-declared-as-structure-members-cannot-be-declared-with-an-initial-size"></a>Yapı üyeleri olarak bildirilen diziler için başlangıç boyutu bildirilemez
Yapı bir dizi başlangıç boyutuyla bildirildi. Herhangi bir yapı öğesi başlatılamıyor ve bir dizi boyutu bildirme bir başlatma biçimidir.  
  
 **Hata Kimliği:** BC31043  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Dizi, yapısında (ilk büyüklük) dinamik tanımlayın.  
  
2.  Belirli bir boyuta dizinin gerektiriyorsa, dinamik bir dizinin redimension bir [ReDim deyimi](../../../visual-basic/language-reference/statements/redim-statement.md) kodunuzu çalışmadığı zaman. Aşağıdaki örnek bunu göstermektedir.  
  
    ```  
    Structure demoStruct  
        Public demoArray() As Integer  
    End Structure  
    Sub useStruct()  
        Dim struct As demoStruct  
        ReDim struct.demoArray(9)  
        Struct.demoArray(2) = 777  
    End Sub  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Diziler](../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [Nasıl yapılır: bir yapıyı bildirme](../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
