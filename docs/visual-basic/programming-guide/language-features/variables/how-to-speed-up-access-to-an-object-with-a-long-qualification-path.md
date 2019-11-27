---
title: 'Nasıl yapılır: Uzun Bir Nitelenmiş Yola Sahip Nesneye Erişimi Hızlandırma'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], accessing
- variables [Visual Basic], object
- With statement [Visual Basic]
- With block
- object variables [Visual Basic], accessing
ms.assetid: 3eb7657f-c9fe-4e05-8bc3-4bb14d5ae585
ms.openlocfilehash: 83670ae6af0904156b08398024658cf504b7663f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346826"
---
# <a name="how-to-speed-up-access-to-an-object-with-a-long-qualification-path-visual-basic"></a>Nasıl yapılır: Uzun Bir Nitelenmiş Yola Sahip Nesneye Erişimi Hızlandırma (Visual Basic)

Birçok yöntem ve özellik için bir nitelik yolu gerektiren bir nesneye sık sık erişiyorsanız, nitelik yolunu tekrarlayarak kodunuzun hızını hızlandırabilirsiniz.

Nitelik yolunu tekrardan kaçınmanın iki yolu vardır. Nesnesini bir değişkene atayabilir veya onu bir `With`...`End With` bloğunda kullanabilirsiniz.

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

1. Nitelik yolunu bir `With` ifadesine koyun.

    ```vb
    With someForm.ActiveForm.ActiveControl
    ```

2. `End With` ifadesinden önce, nesnenin `With` bloğunun içindeki üyelerine erişin.

    ```vb
        .Text = "Test"
        .Location = New Point(100, 100)
        .Show()
    End With
    ```

## <a name="see-also"></a>Ayrıca bkz.

- [Nesne Değişkenleri](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [With...End With Deyimi](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)
