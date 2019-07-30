---
title: 'Nasıl yapılır: Uzun bir nitelik yolu (Visual Basic) ile bir nesneye erişimi hızlandırma'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], accessing
- variables [Visual Basic], object
- With statement [Visual Basic]
- With block
- object variables [Visual Basic], accessing
ms.assetid: 3eb7657f-c9fe-4e05-8bc3-4bb14d5ae585
ms.openlocfilehash: a8e50a2ed04037b48091321dc0c9ac2ea1db35f4
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68631091"
---
# <a name="how-to-speed-up-access-to-an-object-with-a-long-qualification-path-visual-basic"></a>Nasıl yapılır: Uzun bir nitelik yolu (Visual Basic) ile bir nesneye erişimi hızlandırma

Birçok yöntem ve özellik için bir nitelik yolu gerektiren bir nesneye sık sık erişiyorsanız, nitelik yolunu tekrarlayarak kodunuzun hızını hızlandırabilirsiniz.

Nitelik yolunu tekrardan kaçınmanın iki yolu vardır. Nesnesini bir değişkene atayabilir veya bir `With`... içinde kullanabilirsiniz. `End With` engelle.

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

2. Deyimden önce nesnenin `With` blok içindeki üyelerine erişin. `End With`

    ```vb
        .Text = "Test"
        .Location = New Point(100, 100)
        .Show()
    End With
    ```

## <a name="see-also"></a>Ayrıca bkz.

- [Nesne Değişkenleri](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [With...End With Deyimi](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)
