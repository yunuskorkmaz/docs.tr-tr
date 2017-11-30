---
title: "Tür parametreleri niteleyici olarak kullanılamaz"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc32098
- bc32098
helpviewer_keywords: BC32098
ms.assetid: bab05325-dde8-4621-a5f6-368b5b7b2d76
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 58be51e0c05750ee044f0287cde8db037718b4aa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
 [Bildirilmiş öğelere başvurular](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [Visual Basic'de genel türler](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Tür listesi](../../../visual-basic/language-reference/statements/type-list.md)
