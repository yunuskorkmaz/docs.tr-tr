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
ms.openlocfilehash: b696c79cd3cada4416b3f4b6cdf96f00b89a5a0a
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266930"
---
# <a name="nested-control-structures-visual-basic"></a>İç İçe Geçmiş Denetim Yapıları (Visual Basic)
Denetim deyimlerini diğer denetim deyimleri içine(örneğin, `For...Next` bir döngü içinde bir `If...Then...Else` blok) yerleştirebilirsiniz. Başka bir kontrol deyiminin içine yerleştirilen bir kontrol deyiminin *iç içe*olduğu söylenir.  
  
## <a name="nesting-levels"></a>İç Içe Düzeyleri  
 Visual Basic'teki denetim yapıları istediğiniz kadar düzeye iç içe olabilir. İç içe yapıların her birinin gövdesini girinterek daha okunabilir hale getirmek yaygın bir uygulamadır. Tümleşik geliştirme ortamı (IDE) düzenleyicisi bunu otomatik olarak yapar.  
  
 Aşağıdaki örnekte, yordam `sumRows` matrisin her satırının pozitif öğelerini bir araya getirir.  
  
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
  
 Önceki örnekte, `Next` ilk deyim iç `For` döngüyü kapatır `Next` ve son deyim `For` dış döngüyü kapatır.  
  
 Aynı şekilde, iç `If` içe `End If` geçen ifadelerde, ifadeler `If` otomatik olarak en yakın önceki deyime uygulanır. İç `Do` içe geçmiş döngüler benzer bir şekilde `Loop` çalışır ve `Do` en içteki deyim en içteki deyimle eşleşiyor.  
  
> [!NOTE]
> Birçok denetim yapısı için, bir anahtar kelimeyi tıklattığınızda, yapıdaki tüm anahtar kelimeler vurgulanır. Örneğin, bir `If` `If...Then...Else` yapıyı tıklattığınızda, tüm `If` `Then`, `ElseIf` `Else`, `End If` , ve inşaattaki tüm örnekleri vurgulanır. Bir sonraki veya önceki vurgulanan anahtar kelimeye geçmek için CTRL+SHIFT+DOWN ARROW veya CTRL+SHIFT+UP ARROW tuşlarına basın.  
  
## <a name="nesting-different-kinds-of-control-structures"></a>Farklı Kontrol Yapılarının İç Içe Geçme  
 Bir tür kontrol yapısını başka bir türe yuvalayabilirsiniz. Aşağıdaki örnekte `With` bir döngü `For Each` içinde bir `If` blok `With` ve blok içinde iç içe blokları kullanır.  
  
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
  
## <a name="overlapping-control-structures"></a>Üst Üste Binen Kontrol Yapıları  
 Denetim yapıları çakışamazsınız. Bu, iç içe geçen herhangi bir yapının bir sonraki en içteki yapıiçinde tamamen yer alması gerektiği anlamına gelir. Örneğin, iç `For` `With` blok sona ermeden önce döngü sona erdiğinden aşağıdaki düzenleme geçersizdir.  
  
 ![Geçersiz iç içe geçme örneğini gösteren diyagram.](./media/nested-control-structures/example-invalid-nesting.gif)
  
 Visual Basic derleyicisi bu tür çakışan denetim yapılarını algılar ve derleme zamanı hatası sinyalleri vetir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kontrol Akışı](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [Karar Yapıları](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [Döngü Yapıları](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [Diğer Denetim Yapıları](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
