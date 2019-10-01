---
title: Yapı üyeleri olarak bildirilen diziler için başlangıç boyutu bildirilemez
ms.date: 07/20/2015
f1_keywords:
- vbc31043
- bc31043
helpviewer_keywords:
- BC31043
ms.assetid: 5bd90c71-1b78-444b-91e1-4789451ef085
ms.openlocfilehash: de9d77aa9ea853b6f044e91878044115588ca77c
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701248"
---
# <a name="arrays-declared-as-structure-members-cannot-be-declared-with-an-initial-size"></a>Yapı üyeleri olarak bildirilen diziler için başlangıç boyutu bildirilemez
Yapıdaki bir dizi, başlangıç boyutuyla birlikte bildirilmiştir. Herhangi bir yapı öğesini başlatamıyor ve bir dizi boyutunun bildirilmesi, tek bir başlatma biçimidir.  
  
 **Hata kimliği:** BC31043  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. Yapıdaki diziyi dinamik (başlangıç boyutu olmadan) olarak tanımlayın.  
  
2. Belirli bir dizi boyutuna ihtiyacınız varsa, kodunuz çalışırken bir [ReDim ifadesiyle](../../../visual-basic/language-reference/statements/redim-statement.md) dinamik bir diziyi yeniden Dimension uygulayabilirsiniz. Aşağıdaki örnek bunu göstermektedir.  
  
    ```vb  
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
- [Nasıl yapılır: Bir Yapıyı Bildirme](../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
