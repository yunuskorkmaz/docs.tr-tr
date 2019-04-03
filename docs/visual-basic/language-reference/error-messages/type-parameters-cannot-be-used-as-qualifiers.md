---
title: Tür parametreleri niteleyici olarak kullanılamaz
ms.date: 07/20/2015
f1_keywords:
- vbc32098
- bc32098
helpviewer_keywords:
- BC32098
ms.assetid: bab05325-dde8-4621-a5f6-368b5b7b2d76
ms.openlocfilehash: 974d2935e64151109b688f576229fb008b59b229
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819807"
---
# <a name="type-parameters-cannot-be-used-as-qualifiers"></a>Tür parametreleri niteleyici olarak kullanılamaz
Bir programlama öğesi bir tür parametresi içeren bir nitelik dizesiyle nitelenmiş.  
  
 Bir tür parametresi, genel tür oluşturulduğunda sağlanacak olan bir türü için bir gereksinimi temsil eder. Tanımlanmış bir türü göstermiyor. Bir nitelik dize, derleme zamanında tanımlanan öğeler içermesi gerekir.  
  
 Aşağıdaki deyimleri, bu hata oluşturabilirsiniz.  
  
```  
Public Function checkText(Of c As System.Windows.Forms.Control)(  
    ByVal badText As String) As Boolean  
  
    Dim saveText As c.Text  
    ' Insert code to look for badText within saveText.  
End Function  
```  
  
 **Hata Kimliği:** BC32098  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Tür parametresi nitelik dizeden kaldırın veya tanımlanan bir tür ile değiştirin.  
  
2.  Oluşturulan tür nitelendirme programlama öğesine bulmak için kullanmanız gerekiyorsa, ek bir programın mantığı kullanmanız gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bildirilmiş Öğelere Başvurular](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Visual Basic'de genel türler](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Tür Listesi](../../../visual-basic/language-reference/statements/type-list.md)
