---
title: "'<membername>', '<typename>' türünü proje dışında <containertype> '<containertypename>' üzerinden gösteremez"
ms.date: 07/20/2015
f1_keywords:
- bc30909
- vbc30909
helpviewer_keywords:
- BC30909
ms.assetid: ffa7395d-e182-4087-8ce8-079810fdae54
ms.openlocfilehash: 03767501488a395073f925e27adea439751c0de6
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55265070"
---
# <a name="membername-cannot-expose-type-typename-outside-the-project-through-containertype-containertypename"></a>'\<membername >' türü gösteremez '\<typename >' aracılığıyla projenin dışına \<containertype > '\<containertypename >'
Bir değişken, yordam parametre veya dönüş işlevi kapsayıcısı dışında sunulur, ancak kapsayıcı dışında açılmamalıdır bir türü olarak bildirilmiş.  
  
 Aşağıdaki çatı kod bu hatayı oluşturan durumu gösterir.  
  
```  
Private Class privateClass  
End Class  
Public Class mainClass  
    Public exposedVar As New privateClass  
End Class  
```  
  
 Bildirilen tür `Protected`, `Friend`, `Protected Friend`, veya `Private` sınırlı erişimi ile bildirimi bağlamı dışında amaçlanmıştır. Verileri olarak kullanarak daha az kısıtlı erişime sahip bir değişken türü bu amacını boşa. Önceki iskelet kodda `exposedVar` olduğu `Public` ve kullanılabilmesini `privateClass` , erişimi olmaması gereken kod için.  
  
 **Hata Kimliği:** BC30909  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Değişken, yordam parametresi veya işlev erişim düzeyini değiştir en az olabildiğince kısıtlayıcı kendi veri türüne erişim düzeyini döndürür.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Visual Basic'de erişim düzeyleri](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
