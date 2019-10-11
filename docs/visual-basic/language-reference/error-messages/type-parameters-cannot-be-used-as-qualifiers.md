---
title: Tür parametreleri niteleyici olarak kullanılamaz
ms.date: 07/20/2015
f1_keywords:
- vbc32098
- bc32098
helpviewer_keywords:
- BC32098
ms.assetid: bab05325-dde8-4621-a5f6-368b5b7b2d76
ms.openlocfilehash: 3ff4b189539bf119351a94dabadd596c336ac723
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/10/2019
ms.locfileid: "72250337"
---
# <a name="type-parameters-cannot-be-used-as-qualifiers"></a>Tür parametreleri niteleyici olarak kullanılamaz

Bir programlama öğesi, bir tür parametresi içeren bir nitelik dizesi ile nitelenir.

Bir tür parametresi, genel tür oluşturulduğunda sağlanacak bir tür için bir gereksinimi temsil eder. Belirli bir tanımlı türü temsil etmez. Bir nitelik dizesinin yalnızca derleme zamanında tanımlanan öğeleri içermesi gerekir.

Aşağıdaki kod bu hatayı verebilir:

```vb  
Public Function CheckText(Of c As System.Windows.Forms.Control)(
    badText As String) As Boolean
  
    Dim saveText As c.Text  
    ' Insert code to look for badText within saveText.
End Function  
```  
  
 **Hata kimliği:** BC32098  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. Nitelik dizesinden tür parametresini kaldırın veya tanımlı bir türle değiştirin.  
  
2. Nitelenmiş programlama öğesini bulmak için oluşturulmuş bir tür kullanmanız gerekiyorsa ek program mantığını kullanmanız gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bildirilmiş Öğelere Başvurular](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Visual Basic genel türler](../../programming-guide/language-features/data-types/generic-types.md)
- [Tür Listesi](../statements/type-list.md)
