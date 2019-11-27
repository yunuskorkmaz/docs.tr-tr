---
title: İç İçe Geçmiş Denetim Yapıları
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
ms.openlocfilehash: 5818b13661fb4415c6f531b741b8a963a80bd2b8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348145"
---
# <a name="nested-control-structures-visual-basic"></a>İç İçe Geçmiş Denetim Yapıları (Visual Basic)
Denetim deyimlerini diğer denetim deyimlerine yerleştirebilirsiniz. Örneğin, bir `For...Next` döngüsü içinde `If...Then...Else` bloğu. Başka bir denetim ifadesinin içine yerleştirilmiş bir denetim ifadesinin *iç içe*olduğu söylenir.  
  
## <a name="nesting-levels"></a>İç içe düzeyler  
 Visual Basic içindeki denetim yapıları, istediğiniz kadar sayıda düzeyde iç içe olabilir. İç içe yapıları, her birinin gövdesini girintileyerek daha okunaklı hale getirmek yaygın bir uygulamadır. Tümleşik geliştirme ortamı (IDE) Düzenleyicisi bunu otomatik olarak yapar.  
  
 Aşağıdaki örnekte, `sumRows` yordam, matrisin her satırının pozitif öğelerini bir araya ekler.  
  
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
  
 Yukarıdaki örnekte, ilk `Next` ifade iç `For` döngüsünü kapatır ve son `Next` açıklaması dıştaki `For` döngüsünü kapatır.  
  
 Benzer şekilde, iç içe geçmiş `If` deyimlerinde, `End If` deyimleri otomatik olarak en yakın önceki `If` ifadesine uygulanır. İç içe geçmiş `Do` döngüleri, en içteki `Do` ifadesiyle eşleşen en içteki `Loop` ifadesiyle benzer bir biçimde çalışır.  
  
> [!NOTE]
> Birçok denetim yapısında, bir anahtar sözcüğe tıkladığınızda yapıdaki tüm anahtar sözcükler vurgulanır. Örneğin, `If...Then...Else` bir yapıta `If` tıklattığınızda, oluşturulmakta olan tüm `If`, `Then`, `ElseIf`, `Else`ve `End If` örnekleri vurgulanır. Sonraki veya önceki vurgulanmış anahtar sözcüğe geçmek için CTRL + SHIFT + aşağı ok veya CTRL + SHIFT + yukarı ok tuşlarına basın.  
  
## <a name="nesting-different-kinds-of-control-structures"></a>Farklı türlerdeki denetim yapılarını iç içe geçirme  
 Bir tür denetim yapısını başka bir tür içinde iç içe geçirebilirsiniz. Aşağıdaki örnek, bir `For Each` döngüsü içinde `With` bloğunu ve `With` bloğunun içinde iç içe geçmiş `If` blokları kullanır.  
  
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
 Denetim yapılarıyla çakışamaz. Bu, herhangi bir iç içe yapının bir sonraki en içteki yapıda tamamen dahil olması gerektiği anlamına gelir. Örneğin, `For` döngüsü iç `With` bloğunun sonlandırmadan önce sonlandırdığı için aşağıdaki düzenleme geçersizdir.  
  
 ![Geçersiz iç içe geçme örneğini gösteren diyagram.](./media/nested-control-structures/example-invalid-nesting.gif) 
  
 Visual Basic derleyici, bu tür çakışan denetim yapılarını algılar ve derleme zamanı hatasına işaret eder.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Denetim Akışı](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [Karar Yapıları](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [Döngü Yapıları](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [Diğer Denetim Yapıları](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
