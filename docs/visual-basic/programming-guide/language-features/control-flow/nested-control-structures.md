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
ms.openlocfilehash: 539ad639320615c1e53176fe47e5468864aa21d8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414395"
---
# <a name="nested-control-structures-visual-basic"></a>İç İçe Geçmiş Denetim Yapıları (Visual Basic)
Denetim deyimlerini diğer denetim deyimlerinin içine yerleştirebilirsiniz. Örneğin, `If...Then...Else` bir döngü içindeki bir blok `For...Next` . Başka bir denetim ifadesinin içine yerleştirilmiş bir denetim ifadesinin *iç içe*olduğu söylenir.  
  
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
  
 Yukarıdaki örnekte, ilk `Next` ifade iç `For` döngüyü kapatır ve son `Next` ifade dıştaki `For` döngüyü kapatır.  
  
 Benzer şekilde, iç içe geçmiş `If` deyimlerde `End If` deyimler, en yakın önceki ifadeye otomatik olarak uygulanır `If` . İç içe `Do` döngüler benzer bir şekilde çalışarak en `Loop` içteki ifadesiyle eşleşen en içteki deyimle birlikte çalışır `Do` .  
  
> [!NOTE]
> Birçok denetim yapısında, bir anahtar sözcüğe tıkladığınızda yapıdaki tüm anahtar sözcükler vurgulanır. Örneğin, bir yapıya tıkladığınızda,,,, `If` `If...Then...Else` `If` `Then` `ElseIf` `Else` ve `End If` oluşturma içindeki tüm örnekleri vurgulanır. Sonraki veya önceki vurgulanmış anahtar sözcüğe geçmek için CTRL + SHIFT + aşağı ok veya CTRL + SHIFT + yukarı ok tuşlarına basın.  
  
## <a name="nesting-different-kinds-of-control-structures"></a>Farklı türlerdeki denetim yapılarını iç içe geçirme  
 Bir tür denetim yapısını başka bir tür içinde iç içe geçirebilirsiniz. Aşağıdaki örnek, `With` döngüsünün içinde bir blok `For Each` ve `If` blok içindeki iç içe bloklar kullanır `With` .  
  
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
 Denetim yapılarıyla çakışamaz. Bu, herhangi bir iç içe yapının bir sonraki en içteki yapıda tamamen dahil olması gerektiği anlamına gelir. Örneğin, `For` döngü iç blok sonlandırılmadan önce sonlandırdığı için aşağıdaki düzenleme geçersizdir `With` .  
  
 ![Geçersiz iç içe geçme örneğini gösteren diyagram.](./media/nested-control-structures/example-invalid-nesting.gif)
  
 Visual Basic derleyici, bu tür çakışan denetim yapılarını algılar ve derleme zamanı hatasına işaret eder.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Denetim akışı](index.md)
- [Karar Yapıları](decision-structures.md)
- [Döngü Yapıları](loop-structures.md)
- [Diğer Denetim Yapıları](other-control-structures.md)
