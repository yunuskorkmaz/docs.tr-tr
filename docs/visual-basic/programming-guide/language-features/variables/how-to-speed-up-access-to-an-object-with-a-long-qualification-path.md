---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: uzun bir nitelik yolu olan bir nesneye erişimi hızlandırma (Visual Basic)'
title: 'Nasıl yapılır: Uzun Bir Nitelenmiş Yola Sahip Nesneye Erişimi Hızlandırma'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], accessing
- variables [Visual Basic], object
- With statement [Visual Basic]
- With block
- object variables [Visual Basic], accessing
ms.assetid: 3eb7657f-c9fe-4e05-8bc3-4bb14d5ae585
ms.openlocfilehash: 8e0b5dc2ab6c23d57a4e9d905cfd711a79843185
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100467049"
---
# <a name="how-to-speed-up-access-to-an-object-with-a-long-qualification-path-visual-basic"></a>Nasıl yapılır: Uzun Bir Nitelenmiş Yola Sahip Nesneye Erişimi Hızlandırma (Visual Basic)

Birçok yöntem ve özellik için bir nitelik yolu gerektiren bir nesneye sık sık erişiyorsanız, nitelik yolunu tekrarlayarak kodunuzun hızını hızlandırabilirsiniz.

Nitelik yolunu tekrardan kaçınmanın iki yolu vardır. Nesnesini bir değişkene atayabilir veya bir `With` ... `End With` bloğunda kullanabilirsiniz.

### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-assigning-it-to-a-variable"></a>Büyük ölçüde nitelikli bir nesneye erişimi bir değişkene atayarak hızlandırmak için

1. Sıklıkla eriştiğiniz nesnenin türünde bir değişken bildirin. Bildirimin başlatma bölümünde nitelik yolunu belirtin.

    ```vb
    Dim ctrlActv As Control = someForm.ActiveForm.ActiveControl
    ```

2. Nesnenin üyelerine erişmek için değişkenini kullanın.

    ```vb
    ctrlActv.Text = "Test"
    ctrlActv.Location = New Point(100, 100)
    ctrlActv.Show()
    ```

### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-using-a-withend-with-block"></a>Ile bir Ile kullanarak bir büyük ölçüde nitelenmiş nesneye erişimi hızlandırmak için... Blokla bitir

1. Nitelik yolunu bir `With` deyime koyun.

    ```vb
    With someForm.ActiveForm.ActiveControl
    ```

2. `With`Deyimden önce nesnenin blok içindeki üyelerine erişin `End With` .

    ```vb
        .Text = "Test"
        .Location = New Point(100, 100)
        .Show()
    End With
    ```

## <a name="see-also"></a>Ayrıca bkz.

- [Nesne Değişkenleri](object-variables.md)
- [With...End With Deyimi](../../../language-reference/statements/with-end-with-statement.md)
