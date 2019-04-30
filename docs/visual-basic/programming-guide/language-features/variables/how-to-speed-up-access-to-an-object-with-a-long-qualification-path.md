---
title: 'Nasıl yapılır: Uzun bir nitelenmiş yola (Visual Basic) sahip nesneye erişimi hızlandırma'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], accessing
- variables [Visual Basic], object
- With statement [Visual Basic]
- With block
- object variables [Visual Basic], accessing
ms.assetid: 3eb7657f-c9fe-4e05-8bc3-4bb14d5ae585
ms.openlocfilehash: 94c838a69aab9fcae9dc0c79b6038ee90e2369e7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61769050"
---
# <a name="how-to-speed-up-access-to-an-object-with-a-long-qualification-path-visual-basic"></a>Nasıl yapılır: Uzun bir nitelenmiş yola (Visual Basic) sahip nesneye erişimi hızlandırma
Bir nitelenmiş yola çeşitli yöntemleri ve özellikleri gerektiren bir nesne sık erişirseniz, kodunuzu oluşturan nitelenmiş yola tekrarlayarak değil hızlandırabilirsiniz.  
  
 Nitelenmiş yola kaçınmanızı iki yolu vardır. Nesneyi bir değişkene atayın ya da içinde kullanabileceğiniz bir `With`... `End With` blok.  
  
### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-assigning-it-to-a-variable"></a>Bir değişkene atayarak yoğun tam bir nesneye erişimi hızlandırma için  
  
1. Sık sık eriştiğiniz nesne türünde bir değişken bildirir. Nitelenmiş yola bildirimi başlatma kısmında belirtin.  
  
    ```  
    Dim ctrlActv As Control = someForm.ActiveForm.ActiveControl  
    ```  
  
2. Bir nesnenin üyelerine erişmek için bu değişkeni kullanın.  
  
    ```  
    ctrlActv.Text = "Test"  
    ctrlActv.Location = New Point(100, 100)  
    ctrlActv.Show()  
    ```  
  
### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-using-a-withend-with-block"></a>Bir ile kullanarak, yoğun bir şekilde tam bir nesneye erişimi hızlandırma için... End With bloğu  
  
1. Nitelenmiş yola yerleştirecek bir `With` deyimi.  
  
    ```  
    With someForm.ActiveForm.ActiveControl  
    ```  
  
2. İçinde bir nesnenin üyelerine erişmek `With` önce bloğunda `End With` deyimi.  
  
    ```  
        .Text = "Test"  
        .Location = New Point(100, 100)  
        .Show()  
    End With  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nesne Değişkenleri](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [With...End With Deyimi](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)
