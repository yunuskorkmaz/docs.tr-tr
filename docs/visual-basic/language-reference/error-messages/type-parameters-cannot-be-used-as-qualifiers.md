---
title: Tür parametreleri niteleyici olarak kullanılamaz
ms.date: 07/20/2015
f1_keywords:
- vbc32098
- bc32098
helpviewer_keywords:
- BC32098
ms.assetid: bab05325-dde8-4621-a5f6-368b5b7b2d76
ms.openlocfilehash: 88b5f365c47b98964d9f5a0d22a941d85dcfb95f
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592144"
---
# <a name="type-parameters-cannot-be-used-as-qualifiers"></a>Tür parametreleri niteleyici olarak kullanılamaz
Bir programlama öğesi, bir tür parametresi içeren bir nitelik dizesi ile nitelenir.  
  
 Bir tür parametresi, genel tür oluşturulduğunda sağlanacak bir tür için bir gereksinimi temsil eder. Belirli bir tanımlı türü temsil etmez. Bir nitelik dizesinin yalnızca derleme zamanında tanımlanan öğeleri içermesi gerekir.  
  
 Aşağıdaki deyimler bu hatayı oluşturabilir.  
  
```vb  
Public Function checkText(Of c As System.Windows.Forms.Control)(  
    ByVal badText As String) As Boolean  
  
    Dim saveText As c.Text  
    ' Insert code to look for badText within saveText.  
End Function  
```  
  
 **Hata KIMLIĞI:** BC32098  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. Nitelik dizesinden tür parametresini kaldırın veya tanımlı bir türle değiştirin.  
  
2. Nitelenmiş programlama öğesini bulmak için oluşturulmuş bir tür kullanmanız gerekiyorsa ek program mantığını kullanmanız gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bildirilmiş Öğelere Başvurular](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Visual Basic genel türler](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Tür Listesi](../../../visual-basic/language-reference/statements/type-list.md)
