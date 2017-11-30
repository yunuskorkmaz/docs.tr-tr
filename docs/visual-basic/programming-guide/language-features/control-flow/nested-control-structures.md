---
title: "İç İçe Geçmiş Denetim Yapıları (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, control flow
- control structures [Visual Basic], nested
- conditional statements [Visual Basic], nested
- statements [Visual Basic], control flow
- control flow [Visual Basic], nested control statements
- structures [Visual Basic], nested control
- nested control statements [Visual Basic]
ms.assetid: cf60b061-65d9-44a8-81f2-b0bdccd23a05
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 22adf4086cd494202a540b2ec16310072329b6ca
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="nested-control-structures-visual-basic"></a>İç İçe Geçmiş Denetim Yapıları (Visual Basic)
Diğer denetim ifadelerine içine denetim ifadeleri örneğin yerleştirebilirsiniz bir `If...Then...Else` içinde engelleme bir `For...Next` döngü. Başka bir denetim deyimi içinde yerleştirilen bir denetim ifadesi olarak kabul edilir *iç içe geçmiş*.  
  
## <a name="nesting-levels"></a>İç içe geçme düzeyi  
 Denetim yapılarda [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] istediğiniz kadar çok düzeyde iç içe olamaz. Her biri gövdesi girintileme tarafından iç içe geçmiş yapılar daha okunabilir hale getirmek için yaygın bir uygulamadır. Tümleşik geliştirme ortamı (IDE) Düzenleyicisi'ni otomatik olarak bunu yapar.  
  
 Aşağıdaki örnekte, yordamı `sumRows` birlikte pozitif öğeleri matrisin her bir satır ekler.  
  
```  
Public Sub sumRows(ByVal a(,) As Double, ByRef r() As Double)  
    Dim i, j As Integer  
    For i = 0 To UBound(a, 1)  
        r(i) = 0  
        For j = 0 To UBound(a, 2)  
            If a(i, j) > 0 Then  
                r(i) = r(i) + a(i, j)  
            End If  
        Next j  
    Next i  
End Sub  
```  
  
 Önceki örnekte, ilk `Next` deyimi kapatır iç `For` döngü ve son `Next` deyimi kapatır dış `For` döngü.  
  
 Benzer şekilde, iç içe geçmiş `If` deyimleri `End If` deyimleri otomatik olarak uygulamak için en yakın önceki `If` deyimi. İç içe geçmiş `Do` döngüler iş ise en içteki ile benzer bir şekilde `Loop` ise en içteki eşleşen deyimi `Do` deyimi.  
  
> [!NOTE]
>  Bir anahtar sözcüğü tıklattığınızda birçok denetim yapıları için tüm anahtar sözcükleri yapısında vurgulanır. Örneği için tıkladığınızda `If` içinde bir `If...Then...Else` yapım, tüm örneklerini `If`, `Then`, `ElseIf`, `Else`, ve `End If` yapısında vurgulanır. Sonraki veya önceki vurgulanan anahtar sözcüğe taşımak için CTRL + SHIFT + Aşağı Ok veya CTRL + SHIFT + Yukarı Ok tuşuna basın.  
  
## <a name="nesting-different-kinds-of-control-structures"></a>Farklı türde denetim yapıları geçirme  
 Başka bir tür denetimi yapısında bir tür yerleştirebilirsiniz. Aşağıdaki örnek kullanan bir `With` içinde engelleme bir `For Each` döngü ve iç içe `If` içinde engeller `With` bloğu.  
  
```  
For Each ctl As System.Windows.Forms.Control In Me.Controls  
    With ctl  
        .BackColor = System.Drawing.Color.Yellow  
        .ForeColor = System.Drawing.Color.Black  
        If .CanFocus Then  
            .Text = "Colors changed"  
            If Not .Focus() Then  
                ' Insert code to process failed focus.  
            End If  
        End If  
    End With  
Next ctl  
```  
  
## <a name="overlapping-control-structures"></a>Çakışan denetim yapıları  
 Denetim yapıları çakışamaz. Başka bir deyişle, herhangi bir iç içe geçmiş yapısını tamamen sonraki en içteki yapısı içinde bulunmalıdır. Örneğin, aşağıdaki düzenleme geçersiz olduğundan `For` döngü sonlandırır önce iç `With` blok sona erer.  
  
 ![Geçersiz iç içe grafik diyagramı](../../../../visual-basic/programming-guide/language-features/control-flow/media/nestexampleinvalid.gif "NestExampleInvalid")  
Geçersiz iç içe geçmiş için ile yapıları  
  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Derleyici algılar böyle çakışan bir denetim yapıları ve derleme zamanı hata bildirir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Denetim akışı](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)  
 [Karar yapıları](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)  
 [Döngü yapıları](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [Diğer denetim yapıları](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
