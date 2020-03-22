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
# <a name="nested-control-structures-visual-basic"></a><span data-ttu-id="1d5d6-102">İç İçe Geçmiş Denetim Yapıları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1d5d6-102">Nested Control Structures (Visual Basic)</span></span>
<span data-ttu-id="1d5d6-103">Denetim deyimlerini diğer denetim deyimleri içine(örneğin, `For...Next` bir döngü içinde bir `If...Then...Else` blok) yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1d5d6-103">You can place control statements inside other control statements, for example an `If...Then...Else` block within a `For...Next` loop.</span></span> <span data-ttu-id="1d5d6-104">Başka bir kontrol deyiminin içine yerleştirilen bir kontrol deyiminin *iç içe*olduğu söylenir.</span><span class="sxs-lookup"><span data-stu-id="1d5d6-104">A control statement placed inside another control statement is said to be *nested*.</span></span>  
  
## <a name="nesting-levels"></a><span data-ttu-id="1d5d6-105">İç Içe Düzeyleri</span><span class="sxs-lookup"><span data-stu-id="1d5d6-105">Nesting Levels</span></span>  
 <span data-ttu-id="1d5d6-106">Visual Basic'teki denetim yapıları istediğiniz kadar düzeye iç içe olabilir.</span><span class="sxs-lookup"><span data-stu-id="1d5d6-106">Control structures in Visual Basic can be nested to as many levels as you want.</span></span> <span data-ttu-id="1d5d6-107">İç içe yapıların her birinin gövdesini girinterek daha okunabilir hale getirmek yaygın bir uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="1d5d6-107">It is common practice to make nested structures more readable by indenting the body of each one.</span></span> <span data-ttu-id="1d5d6-108">Tümleşik geliştirme ortamı (IDE) düzenleyicisi bunu otomatik olarak yapar.</span><span class="sxs-lookup"><span data-stu-id="1d5d6-108">The integrated development environment (IDE) editor automatically does this.</span></span>  
  
 <span data-ttu-id="1d5d6-109">Aşağıdaki örnekte, yordam `sumRows` matrisin her satırının pozitif öğelerini bir araya getirir.</span><span class="sxs-lookup"><span data-stu-id="1d5d6-109">In the following example, the procedure `sumRows` adds together the positive elements of each row of the matrix.</span></span>  
  
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
  
 <span data-ttu-id="1d5d6-110">Önceki örnekte, `Next` ilk deyim iç `For` döngüyü kapatır `Next` ve son deyim `For` dış döngüyü kapatır.</span><span class="sxs-lookup"><span data-stu-id="1d5d6-110">In the preceding example, the first `Next` statement closes the inner `For` loop and the last `Next` statement closes the outer `For` loop.</span></span>  
  
 <span data-ttu-id="1d5d6-111">Aynı şekilde, iç `If` içe `End If` geçen ifadelerde, ifadeler `If` otomatik olarak en yakın önceki deyime uygulanır.</span><span class="sxs-lookup"><span data-stu-id="1d5d6-111">Likewise, in nested `If` statements, the `End If` statements automatically apply to the nearest prior `If` statement.</span></span> <span data-ttu-id="1d5d6-112">İç `Do` içe geçmiş döngüler benzer bir şekilde `Loop` çalışır ve `Do` en içteki deyim en içteki deyimle eşleşiyor.</span><span class="sxs-lookup"><span data-stu-id="1d5d6-112">Nested `Do` loops work in a similar fashion, with the innermost `Loop` statement matching the innermost `Do` statement.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1d5d6-113">Birçok denetim yapısı için, bir anahtar kelimeyi tıklattığınızda, yapıdaki tüm anahtar kelimeler vurgulanır.</span><span class="sxs-lookup"><span data-stu-id="1d5d6-113">For many control structures, when you click a keyword, all of the keywords in the structure are highlighted.</span></span> <span data-ttu-id="1d5d6-114">Örneğin, bir `If` `If...Then...Else` yapıyı tıklattığınızda, tüm `If` `Then`, `ElseIf` `Else`, `End If` , ve inşaattaki tüm örnekleri vurgulanır.</span><span class="sxs-lookup"><span data-stu-id="1d5d6-114">For instance, when you click `If` in an `If...Then...Else` construction, all instances of `If`, `Then`, `ElseIf`, `Else`, and `End If` in the construction are highlighted.</span></span> <span data-ttu-id="1d5d6-115">Bir sonraki veya önceki vurgulanan anahtar kelimeye geçmek için CTRL+SHIFT+DOWN ARROW veya CTRL+SHIFT+UP ARROW tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="1d5d6-115">To move to the next or previous highlighted keyword, press CTRL+SHIFT+DOWN ARROW or CTRL+SHIFT+UP ARROW.</span></span>  
  
## <a name="nesting-different-kinds-of-control-structures"></a><span data-ttu-id="1d5d6-116">Farklı Kontrol Yapılarının İç Içe Geçme</span><span class="sxs-lookup"><span data-stu-id="1d5d6-116">Nesting Different Kinds of Control Structures</span></span>  
 <span data-ttu-id="1d5d6-117">Bir tür kontrol yapısını başka bir türe yuvalayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1d5d6-117">You can nest one kind of control structure within another kind.</span></span> <span data-ttu-id="1d5d6-118">Aşağıdaki örnekte `With` bir döngü `For Each` içinde bir `If` blok `With` ve blok içinde iç içe blokları kullanır.</span><span class="sxs-lookup"><span data-stu-id="1d5d6-118">The following example uses a `With` block inside a `For Each` loop and nested `If` blocks inside the `With` block.</span></span>  
  
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
  
## <a name="overlapping-control-structures"></a><span data-ttu-id="1d5d6-119">Üst Üste Binen Kontrol Yapıları</span><span class="sxs-lookup"><span data-stu-id="1d5d6-119">Overlapping Control Structures</span></span>  
 <span data-ttu-id="1d5d6-120">Denetim yapıları çakışamazsınız.</span><span class="sxs-lookup"><span data-stu-id="1d5d6-120">You cannot overlap control structures.</span></span> <span data-ttu-id="1d5d6-121">Bu, iç içe geçen herhangi bir yapının bir sonraki en içteki yapıiçinde tamamen yer alması gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="1d5d6-121">This means that any nested structure must be completely contained within the next innermost structure.</span></span> <span data-ttu-id="1d5d6-122">Örneğin, iç `For` `With` blok sona ermeden önce döngü sona erdiğinden aşağıdaki düzenleme geçersizdir.</span><span class="sxs-lookup"><span data-stu-id="1d5d6-122">For example, the following arrangement is invalid because the `For` loop terminates before the inner `With` block terminates.</span></span>  
  
 ![Geçersiz iç içe geçme örneğini gösteren diyagram.](./media/nested-control-structures/example-invalid-nesting.gif)
  
 <span data-ttu-id="1d5d6-124">Visual Basic derleyicisi bu tür çakışan denetim yapılarını algılar ve derleme zamanı hatası sinyalleri vetir.</span><span class="sxs-lookup"><span data-stu-id="1d5d6-124">The Visual Basic compiler detects such overlapping control structures and signals a compile-time error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d5d6-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1d5d6-125">See also</span></span>

- [<span data-ttu-id="1d5d6-126">Kontrol Akışı</span><span class="sxs-lookup"><span data-stu-id="1d5d6-126">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [<span data-ttu-id="1d5d6-127">Karar Yapıları</span><span class="sxs-lookup"><span data-stu-id="1d5d6-127">Decision Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [<span data-ttu-id="1d5d6-128">Döngü Yapıları</span><span class="sxs-lookup"><span data-stu-id="1d5d6-128">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="1d5d6-129">Diğer Denetim Yapıları</span><span class="sxs-lookup"><span data-stu-id="1d5d6-129">Other Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
