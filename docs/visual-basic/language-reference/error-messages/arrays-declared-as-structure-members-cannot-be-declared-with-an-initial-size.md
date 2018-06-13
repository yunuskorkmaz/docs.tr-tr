---
title: Yapı üyeleri olarak bildirilen diziler için başlangıç boyutu bildirilemez
ms.date: 07/20/2015
f1_keywords:
- vbc31043
- bc31043
helpviewer_keywords:
- BC31043
ms.assetid: 5bd90c71-1b78-444b-91e1-4789451ef085
ms.openlocfilehash: 0a7424e5dbfadd78c4071ba5b76086b7f6c9b94a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33585859"
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
 [Nasıl yapılır: Bir Yapıyı Bildirme](../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
