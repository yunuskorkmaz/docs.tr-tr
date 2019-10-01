---
title: "'<membername>', '<typename>' türünü proje dışında <containertype> '<containertypename>' üzerinden gösteremez"
ms.date: 07/20/2015
f1_keywords:
- bc30909
- vbc30909
helpviewer_keywords:
- BC30909
ms.assetid: ffa7395d-e182-4087-8ce8-079810fdae54
ms.openlocfilehash: ca67e74d7790352bd1842cb8a59fe1525af6e18c
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700896"
---
# <a name="membername-cannot-expose-type-typename-outside-the-project-through-containertype-containertypename"></a>' \<membername > ', ' \<typename > ' türünü @no__t ' >-3containertypename @no__t ' aracılığıyla projenin dışına gösteremez
Bir değişken, yordam parametresi veya işlev dönüşü kapsayıcının dışında sunulur, ancak kapsayıcı dışında gösterilmemesi gereken bir tür olarak bildirilmiştir.  
  
 Aşağıdaki iskelet kodu, bu hatayı üreten bir durumu gösterir.  
  
```vb  
Private Class privateClass  
End Class  
Public Class mainClass  
    Public exposedVar As New privateClass  
End Class  
```  
  
 @No__t-0, `Friend`, `Protected Friend` veya `Private` olarak belirtilen bir türün, bildirim bağlamı dışında sınırlı erişimi olması amaçlanmıştır. Bunu daha az kısıtlanmış erişimi olan bir değişkenin veri türü olarak kullanmak, bu amacı erteçine neden olur. Önceki iskelet kodunda, `exposedVar` ' ı `Public` ' dir ve erişimi olmayan koda `privateClass` ' yi kullanıma sunacaktır.  
  
 **Hata kimliği:** BC30909  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Değişkenin, yordam parametresinin veya işlevin erişim düzeyini, veri türünün erişim düzeyi olarak en az kısıtlayıcı olacak şekilde değiştirin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic erişim düzeyleri](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
