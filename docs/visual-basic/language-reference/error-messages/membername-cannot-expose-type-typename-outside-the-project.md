---
description: "Hakkında daha fazla bilgi: BC30909: ' <membername> ', ' <typename> ' türünü proje dışında <containertype> ' ' olarak gösteremez<containertypename>"
title: "'<membername>', '<typename>' türünü proje dışında <containertype> '<containertypename>' üzerinden gösteremez"
ms.date: 07/20/2015
f1_keywords:
- bc30909
- vbc30909
helpviewer_keywords:
- BC30909
ms.assetid: ffa7395d-e182-4087-8ce8-079810fdae54
ms.openlocfilehash: e2cc1d950b646bb787dfe714c39efea78a530129
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795865"
---
# <a name="bc30909-membername-cannot-expose-type-typename-outside-the-project-through-containertype-containertypename"></a>BC30909: ' ', ' ' \<membername> türünü \<typename> proje dışında ' ' üzerinden \<containertype> gösteremez \<containertypename>

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
