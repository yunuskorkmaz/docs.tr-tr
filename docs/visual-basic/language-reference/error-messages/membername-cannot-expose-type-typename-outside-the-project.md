---
title: "'<membername>', '<typename>' türünü proje dışında <containertype> '<containertypename>' üzerinden gösteremez"
ms.date: 07/20/2015
f1_keywords:
- bc30909
- vbc30909
helpviewer_keywords:
- BC30909
ms.assetid: ffa7395d-e182-4087-8ce8-079810fdae54
ms.openlocfilehash: 729a9f385d94412469d318cb804d216827eeb0fd
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397291"
---
# <a name="membername-cannot-expose-type-typename-outside-the-project-through-containertype-containertypename"></a>'\<membername>', '\<typename>' türünü proje dışında \<containertype> '\<containertypename>' üzerinden gösteremez
Bir değişken, yordam parametresi veya işlev dönüşü kapsayıcının dışında sunulur, ancak kapsayıcı dışında gösterilmemesi gereken bir tür olarak bildirilmiştir.  
  
 Aşağıdaki iskelet kodu, bu hatayı üreten bir durumu gösterir.  
  
```vb  
Private Class privateClass  
End Class  
Public Class mainClass  
    Public exposedVar As New privateClass  
End Class  
```  
  
 ,, Veya olarak belirtilen bir türün `Protected` , `Friend` `Protected Friend` `Private` Bildirim bağlamı dışında sınırlı erişimi olması amaçlanmıştır. Bunu daha az kısıtlanmış erişimi olan bir değişkenin veri türü olarak kullanmak, bu amacı erteçine neden olur. Önceki iskelet kodunda, `exposedVar` `Public` ve `privateClass` erişimine sahip olmaması gereken kodla kullanıma sunacaktır.  
  
 **Hata kimliği:** BC30909  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Değişkenin, yordam parametresinin veya işlevin erişim düzeyini, veri türünün erişim düzeyi olarak en az kısıtlayıcı olacak şekilde değiştirin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic erişim düzeyleri](../../programming-guide/language-features/declared-elements/access-levels.md)
