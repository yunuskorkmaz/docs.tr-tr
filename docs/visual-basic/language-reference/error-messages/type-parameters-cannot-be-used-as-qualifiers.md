---
title: Tür parametreleri niteleyici olarak kullanılamaz
ms.date: 07/20/2015
f1_keywords:
- vbc32098
- bc32098
helpviewer_keywords:
- BC32098
ms.assetid: bab05325-dde8-4621-a5f6-368b5b7b2d76
ms.openlocfilehash: ba7348ae50965ffcf2719b20934451916c8fa95a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59296361"
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
  
1. Tür parametresi nitelik dizeden kaldırın veya tanımlanan bir tür ile değiştirin.  
  
2. Oluşturulan tür nitelendirme programlama öğesine bulmak için kullanmanız gerekiyorsa, ek bir programın mantığı kullanmanız gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bildirilmiş Öğelere Başvurular](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Visual Basic'de Genel Türler](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Tür Listesi](../../../visual-basic/language-reference/statements/type-list.md)
