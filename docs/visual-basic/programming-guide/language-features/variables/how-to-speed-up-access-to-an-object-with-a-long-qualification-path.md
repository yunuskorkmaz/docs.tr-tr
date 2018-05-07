---
title: 'Nasıl yapılır: Uzun Bir Nitelenmiş Yola Sahip Nesneye Erişimi Hızlandırma (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], accessing
- variables [Visual Basic], object
- With statement [Visual Basic]
- With block
- object variables [Visual Basic], accessing
ms.assetid: 3eb7657f-c9fe-4e05-8bc3-4bb14d5ae585
ms.openlocfilehash: d52d13feb0f85065c0623b5937f558b841c036dd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-speed-up-access-to-an-object-with-a-long-qualification-path-visual-basic"></a>Nasıl yapılır: Uzun Bir Nitelenmiş Yola Sahip Nesneye Erişimi Hızlandırma (Visual Basic)
Çeşitli yöntemleri ve özellikleri nitelenmiş yolunu gerektirir nesneyi sık erişirse, nitelenmiş yola tekrarlayarak değil, kod hızlandırabilir.  
  
 Nitelenmiş yola kaçınmanızı iki yolu vardır. Nesneyi bir değişkene atayın veya içinde kullanabileceğiniz bir `With`... `End With` bloğu.  
  
### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-assigning-it-to-a-variable"></a>Bir değişkene atayarak yoğun olarak tam bir nesneye erişimi hızlandırma için  
  
1.  Sık sık eriştiğiniz nesne türünde bir değişken bildirin. Nitelenmiş yola bildirimi başlatma parçası belirtin.  
  
    ```  
    Dim ctrlActv As Control = someForm.ActiveForm.ActiveControl  
    ```  
  
2.  Nesnenin üyelere erişmek için değişkeni kullanın.  
  
    ```  
    ctrlActv.Text = "Test"  
    ctrlActv.Location = New Point(100, 100)  
    ctrlActv.Show()  
    ```  
  
### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-using-a-withend-with-block"></a>Bir WITH kullanarak yoğun olarak tam bir nesneye erişimi hızlandırma için... End With bloğu  
  
1.  Nitelenmiş yola yerleştirecek bir `With` deyimi.  
  
    ```  
    With someForm.ActiveForm.ActiveControl  
    ```  
  
2.  Nesnenin üyeleri içinde erişim `With` önce bloğunu `End With` deyimi.  
  
    ```  
        .Text = "Test"  
        .Location = New Point(100, 100)  
        .Show()  
    End With  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nesne Değişkenleri](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [With...End With Deyimi](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)
