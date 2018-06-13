---
title: İç İçe Geçmiş Denetim Yapıları (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, control flow
- control structures [Visual Basic], nested
- conditional statements [Visual Basic], nested
- statements [Visual Basic], control flow
- control flow [Visual Basic], nested control statements
- structures [Visual Basic], nested control
- nested control statements [Visual Basic]
ms.assetid: cf60b061-65d9-44a8-81f2-b0bdccd23a05
ms.openlocfilehash: ec3d4d477290480cdfa0f5b1c88aa82c81040d11
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648079"
---
# <a name="nested-control-structures-visual-basic"></a>İç İçe Geçmiş Denetim Yapıları (Visual Basic)
Diğer denetim ifadelerine içine denetim ifadeleri örneğin yerleştirebilirsiniz bir `If...Then...Else` içinde engelleme bir `For...Next` döngü. Başka bir denetim deyimi içinde yerleştirilen bir denetim ifadesi olarak kabul edilir *iç içe geçmiş*.  
  
## <a name="nesting-levels"></a>İç içe geçme düzeyi  
 Visual Basic'de denetim yapıları için istediğiniz kadar çok düzeyde iç içe. Her biri gövdesi girintileme tarafından iç içe geçmiş yapılar daha okunabilir hale getirmek için yaygın bir uygulamadır. Tümleşik geliştirme ortamı (IDE) Düzenleyicisi'ni otomatik olarak bunu yapar.  
  
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
  
 Visual Basic derleyici böyle çakışan denetim yapıları algılar ve bir derleme zamanı hatası işaret eder.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Denetim Akışı](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)  
 [Karar Yapıları](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)  
 [Döngü Yapıları](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [Diğer Denetim Yapıları](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
