---
title: Tür parametreleri niteleyici olarak kullanılamaz
ms.date: 07/20/2015
f1_keywords:
- vbc32098
- bc32098
helpviewer_keywords:
- BC32098
ms.assetid: bab05325-dde8-4621-a5f6-368b5b7b2d76
ms.openlocfilehash: 563010efc4f3049d330ee2b38b7f59e23292e630
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="type-parameters-cannot-be-used-as-qualifiers"></a>Tür parametreleri niteleyici olarak kullanılamaz
Bir programlama öğesi bir tür parametresi içeren bir niteliği dizeyle tam.  
  
 Tür parametresi genel türü oluşturulduğunda sağlanacak olan bir türü gereksinimini temsil eder. Belirli tanımlanmış bir türü göstermiyor. Niteliğe dize derleme zamanında tanımlanan öğeleri eklemeniz gerekir.  
  
 Aşağıdaki deyimleri bu hata oluşmasına neden olabilir.  
  
```  
Public Function checkText(Of c As System.Windows.Forms.Control)(  
    ByVal badText As String) As Boolean  
  
    Dim saveText As c.Text  
    ' Insert code to look for badText within saveText.  
End Function  
```  
  
 **Hata Kimliği:** BC32098  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Tür parametresi niteliğe dizeden kaldırın veya tanımlanmış bir türü ile değiştirin.  
  
2.  Tamamlandıktan programlama öğesi bulmak için yapılandırılmış bir tür kullanmanız gerekiyorsa, ek program mantığı kullanmanız gerekir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bildirilmiş Öğelere Başvurular](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [Visual Basic'de genel türler](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Tür Listesi](../../../visual-basic/language-reference/statements/type-list.md)
