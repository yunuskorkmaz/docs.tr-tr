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
ms.openlocfilehash: f559bf603605873f1b9155e9a96cb367e5420343
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941682"
---
# <a name="nested-control-structures-visual-basic"></a>İç İçe Geçmiş Denetim Yapıları (Visual Basic)
Denetim deyimlerini diğer denetim deyimlerinin içine yerleştirebilirsiniz. Örneğin, bir `If...Then...Else` `For...Next` döngü içindeki bir blok. Başka bir denetim ifadesinin içine yerleştirilmiş bir denetim ifadesinin *iç içe*olduğu söylenir.  
  
## <a name="nesting-levels"></a>İç içe düzeyler  
 Visual Basic içindeki denetim yapıları, istediğiniz kadar sayıda düzeyde iç içe olabilir. İç içe yapıları, her birinin gövdesini girintileyerek daha okunaklı hale getirmek yaygın bir uygulamadır. Tümleşik geliştirme ortamı (IDE) Düzenleyicisi bunu otomatik olarak yapar.  
  
 Aşağıdaki örnekte, yordam `sumRows` matrisin her satırının pozitif öğelerini birlikte ekler.  
  
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
  
 Yukarıdaki `Next` örnekte, ilk ifade iç `For` döngüyü kapatır ve son `Next` ifade dıştaki `For` döngüyü kapatır.  
  
 Benzer şekilde, iç `If` içe geçmiş deyimlerde `End If` deyimler, en yakın önceki `If` ifadeye otomatik olarak uygulanır. İç `Do` içe döngüler benzer bir şekilde çalışarak en içteki `Do` ifadesiyle eşleşen `Loop` en içteki deyimle birlikte çalışır.  
  
> [!NOTE]
> Birçok denetim yapısında, bir anahtar sözcüğe tıkladığınızda yapıdaki tüm anahtar sözcükler vurgulanır. `If` Örneğin, bir `ElseIf` `Then` `Else` yapıyatıkladığınızda`End If` ,,,, ve oluşturma içindeki tüm örnekleri vurgulanır.`If` `If...Then...Else` Sonraki veya önceki vurgulanmış anahtar sözcüğe geçmek için CTRL + SHIFT + aşağı ok veya CTRL + SHIFT + yukarı ok tuşlarına basın.  
  
## <a name="nesting-different-kinds-of-control-structures"></a>Farklı türlerdeki denetim yapılarını iç içe geçirme  
 Bir tür denetim yapısını başka bir tür içinde iç içe geçirebilirsiniz. Aşağıdaki örnek, `For Each` döngüsünün içinde `With` bir blok `With` ve blok içindeki iç `If` içe bloklar kullanır.  
  
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
 Denetim yapılarıyla çakışamaz. Bu, herhangi bir iç içe yapının bir sonraki en içteki yapıda tamamen dahil olması gerektiği anlamına gelir. Örneğin, `For` döngü iç `With` blok sonlandırılmadan önce sonlandırdığı için aşağıdaki düzenleme geçersizdir.  
  
 ![Geçersiz iç içe geçme örneğini gösteren diyagram.](./media/nested-control-structures/example-invalid-nesting.gif) 
  
 Visual Basic derleyici, bu tür çakışan denetim yapılarını algılar ve derleme zamanı hatasına işaret eder.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Denetim Akışı](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [Karar Yapıları](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [Döngü Yapıları](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [Diğer Denetim Yapıları](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
