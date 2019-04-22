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
ms.openlocfilehash: c016722332dafa3d3be91a1e9e98cc0ce9a49717
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58835199"
---
# <a name="nested-control-structures-visual-basic"></a>İç İçe Geçmiş Denetim Yapıları (Visual Basic)
Örneğin denetim ifadeleri diğer denetim ifadelerine içine yerleştirebilirsiniz bir `If...Then...Else` içinde engelleyecek bir `For...Next` döngü. Başka bir denetim deyiminin içinde yer bir denetim deyimidir olduğu söylenir *iç içe geçmiş*.  
  
## <a name="nesting-levels"></a>İç içe geçme düzeyi  
 Visual Basic'de denetim yapıları için istediğiniz sayıda düzeyi yuvalanabilir. İç içe geçmiş yapılar gövdesi her biri, girintilendirme tarafından daha okunabilir yapmak için yaygın bir uygulamadır. Tümleşik geliştirme ortamı (IDE) Düzenleyicisi'ni otomatik olarak bunu yapar.  
  
 Aşağıdaki örnekte, yordam `sumRows` matris her satırın pozitif öğeleri bir araya getirir.  
  
```vb
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
  
 Yukarıdaki örnekte, ilk `Next` deyimi kapatır iç `For` döngüsü ve son `Next` deyimi kapatır dış `For` döngü.  
  
 Buna benzer şekilde, iç içe `If` deyimleri `End If` ifadeleri otomatik olarak uygulamak için en yakın önceki `If` deyimi. İç içe geçmiş `Do` döngüler çalışma en içteki ile benzer bir biçimde `Loop` ifade en içteki eşleşen `Do` deyimi.  
  
> [!NOTE]
>  Bir anahtar sözcük tıkladığınızda birçok denetim yapıları için anahtar sözcükleri yapısındaki tüm vurgulanır. Örneği için tıkladığınızda `If` içinde bir `If...Then...Else` oluşturma, tüm örneklerini `If`, `Then`, `ElseIf`, `Else`, ve `End If` yapısında vurgulanır. Sonraki veya önceki vurgulanan anahtar taşımak için CTRL + SHIFT + Aşağı Ok veya CTRL + SHIFT + Yukarı Ok tuşuna basın.  
  
## <a name="nesting-different-kinds-of-control-structures"></a>Farklı türlerde denetim yapılarını iç içe geçirme  
 Bir tür denetim yapısı başka bir tür içinde iç içe yerleştirebilirsiniz. Aşağıdaki örnekte bir `With` içinde engelleyecek bir `For Each` döngü ve iç içe geçmiş `If` içinde engeller `With` blok.  
  
```vb
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
 Denetim yapıları çakışamaz. Başka bir deyişle, tüm iç içe yapı tamamen sonraki en içteki yapısı içinde bulunmalıdır. Örneğin, aşağıdaki düzenleme geçersiz olduğundan `For` döngüyü sonlandırır önce iç `With` bloğunu sonlandırır.  
  
 ![Geçersiz iç içe bir örneğini gösteren diyagram.](./media/nested-control-structures/example-invalid-nesting.gif) 
  
 Visual Basic Derleyicisi, böyle çakışan denetim yapıları algılar ve bir derleme zamanı hatası bildirir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Denetim Akışı](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [Karar Yapıları](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [Döngü Yapıları](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [Diğer Denetim Yapıları](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
