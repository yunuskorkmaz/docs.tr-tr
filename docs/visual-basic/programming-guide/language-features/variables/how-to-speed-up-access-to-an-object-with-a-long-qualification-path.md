---
title: "Nasıl yapılır: Uzun Bir Nitelenmiş Yola Sahip Nesneye Erişimi Hızlandırma (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- variables [Visual Basic], accessing
- variables [Visual Basic], object
- With statement [Visual Basic]
- With block
- object variables [Visual Basic], accessing
ms.assetid: 3eb7657f-c9fe-4e05-8bc3-4bb14d5ae585
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5d91eeaeb034a4c8b4fefcffdf2fdebe72127d66
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
 [Nesne değişkenleri](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [İle... End With deyimi](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)
