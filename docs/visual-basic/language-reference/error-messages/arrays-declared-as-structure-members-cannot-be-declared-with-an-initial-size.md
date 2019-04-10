---
title: Yapı üyeleri olarak bildirilen diziler için başlangıç boyutu bildirilemez
ms.date: 07/20/2015
f1_keywords:
- vbc31043
- bc31043
helpviewer_keywords:
- BC31043
ms.assetid: 5bd90c71-1b78-444b-91e1-4789451ef085
ms.openlocfilehash: 5d58b531b670715716e849cd37227bc899195df6
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59335309"
---
# <a name="arrays-declared-as-structure-members-cannot-be-declared-with-an-initial-size"></a>Yapı üyeleri olarak bildirilen diziler için başlangıç boyutu bildirilemez
Bir yapıdaki dizi başlangıç boyutuyla bildirilir. Herhangi bir yapı öğe başlatılamıyor ve bir dizi boyutu bildirme bir başlatma biçimidir.  
  
 **Hata Kimliği:** BC31043  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. Dizi, yapısında (ilk boyut) dinamik tanımlayın.  
  
2. Belirli bir dizinin boyutunu gerekiyorsa, dinamik bir dizi ile redimension bir [ReDim deyimi](../../../visual-basic/language-reference/statements/redim-statement.md) kodunuz çalışırken. Aşağıdaki örnek bunu göstermektedir.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [Diziler](../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [Nasıl yapılır: Bir yapıyı bildirme](../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
