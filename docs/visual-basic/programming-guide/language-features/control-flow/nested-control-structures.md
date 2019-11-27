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
# <a name="nested-control-structures-visual-basic"></a><span data-ttu-id="8e0b7-102">İç İçe Geçmiş Denetim Yapıları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8e0b7-102">Nested Control Structures (Visual Basic)</span></span>
<span data-ttu-id="8e0b7-103">Denetim deyimlerini diğer denetim deyimlerine yerleştirebilirsiniz. Örneğin, bir `For...Next` döngüsü içinde `If...Then...Else` bloğu.</span><span class="sxs-lookup"><span data-stu-id="8e0b7-103">You can place control statements inside other control statements, for example an `If...Then...Else` block within a `For...Next` loop.</span></span> <span data-ttu-id="8e0b7-104">Başka bir denetim ifadesinin içine yerleştirilmiş bir denetim ifadesinin *iç içe*olduğu söylenir.</span><span class="sxs-lookup"><span data-stu-id="8e0b7-104">A control statement placed inside another control statement is said to be *nested*.</span></span>  
  
## <a name="nesting-levels"></a><span data-ttu-id="8e0b7-105">İç içe düzeyler</span><span class="sxs-lookup"><span data-stu-id="8e0b7-105">Nesting Levels</span></span>  
 <span data-ttu-id="8e0b7-106">Visual Basic içindeki denetim yapıları, istediğiniz kadar sayıda düzeyde iç içe olabilir.</span><span class="sxs-lookup"><span data-stu-id="8e0b7-106">Control structures in Visual Basic can be nested to as many levels as you want.</span></span> <span data-ttu-id="8e0b7-107">İç içe yapıları, her birinin gövdesini girintileyerek daha okunaklı hale getirmek yaygın bir uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="8e0b7-107">It is common practice to make nested structures more readable by indenting the body of each one.</span></span> <span data-ttu-id="8e0b7-108">Tümleşik geliştirme ortamı (IDE) Düzenleyicisi bunu otomatik olarak yapar.</span><span class="sxs-lookup"><span data-stu-id="8e0b7-108">The integrated development environment (IDE) editor automatically does this.</span></span>  
  
 <span data-ttu-id="8e0b7-109">Aşağıdaki örnekte, `sumRows` yordam, matrisin her satırının pozitif öğelerini bir araya ekler.</span><span class="sxs-lookup"><span data-stu-id="8e0b7-109">In the following example, the procedure `sumRows` adds together the positive elements of each row of the matrix.</span></span>  
  
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
  
 <span data-ttu-id="8e0b7-110">Yukarıdaki örnekte, ilk `Next` ifade iç `For` döngüsünü kapatır ve son `Next` açıklaması dıştaki `For` döngüsünü kapatır.</span><span class="sxs-lookup"><span data-stu-id="8e0b7-110">In the preceding example, the first `Next` statement closes the inner `For` loop and the last `Next` statement closes the outer `For` loop.</span></span>  
  
 <span data-ttu-id="8e0b7-111">Benzer şekilde, iç içe geçmiş `If` deyimlerinde, `End If` deyimleri otomatik olarak en yakın önceki `If` ifadesine uygulanır.</span><span class="sxs-lookup"><span data-stu-id="8e0b7-111">Likewise, in nested `If` statements, the `End If` statements automatically apply to the nearest prior `If` statement.</span></span> <span data-ttu-id="8e0b7-112">İç içe geçmiş `Do` döngüleri, en içteki `Do` ifadesiyle eşleşen en içteki `Loop` ifadesiyle benzer bir biçimde çalışır.</span><span class="sxs-lookup"><span data-stu-id="8e0b7-112">Nested `Do` loops work in a similar fashion, with the innermost `Loop` statement matching the innermost `Do` statement.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8e0b7-113">Birçok denetim yapısında, bir anahtar sözcüğe tıkladığınızda yapıdaki tüm anahtar sözcükler vurgulanır.</span><span class="sxs-lookup"><span data-stu-id="8e0b7-113">For many control structures, when you click a keyword, all of the keywords in the structure are highlighted.</span></span> <span data-ttu-id="8e0b7-114">Örneğin, `If...Then...Else` bir yapıta `If` tıklattığınızda, oluşturulmakta olan tüm `If`, `Then`, `ElseIf`, `Else`ve `End If` örnekleri vurgulanır.</span><span class="sxs-lookup"><span data-stu-id="8e0b7-114">For instance, when you click `If` in an `If...Then...Else` construction, all instances of `If`, `Then`, `ElseIf`, `Else`, and `End If` in the construction are highlighted.</span></span> <span data-ttu-id="8e0b7-115">Sonraki veya önceki vurgulanmış anahtar sözcüğe geçmek için CTRL + SHIFT + aşağı ok veya CTRL + SHIFT + yukarı ok tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="8e0b7-115">To move to the next or previous highlighted keyword, press CTRL+SHIFT+DOWN ARROW or CTRL+SHIFT+UP ARROW.</span></span>  
  
## <a name="nesting-different-kinds-of-control-structures"></a><span data-ttu-id="8e0b7-116">Farklı türlerdeki denetim yapılarını iç içe geçirme</span><span class="sxs-lookup"><span data-stu-id="8e0b7-116">Nesting Different Kinds of Control Structures</span></span>  
 <span data-ttu-id="8e0b7-117">Bir tür denetim yapısını başka bir tür içinde iç içe geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8e0b7-117">You can nest one kind of control structure within another kind.</span></span> <span data-ttu-id="8e0b7-118">Aşağıdaki örnek, bir `For Each` döngüsü içinde `With` bloğunu ve `With` bloğunun içinde iç içe geçmiş `If` blokları kullanır.</span><span class="sxs-lookup"><span data-stu-id="8e0b7-118">The following example uses a `With` block inside a `For Each` loop and nested `If` blocks inside the `With` block.</span></span>  
  
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
  
## <a name="overlapping-control-structures"></a><span data-ttu-id="8e0b7-119">Çakışan denetim yapıları</span><span class="sxs-lookup"><span data-stu-id="8e0b7-119">Overlapping Control Structures</span></span>  
 <span data-ttu-id="8e0b7-120">Denetim yapılarıyla çakışamaz.</span><span class="sxs-lookup"><span data-stu-id="8e0b7-120">You cannot overlap control structures.</span></span> <span data-ttu-id="8e0b7-121">Bu, herhangi bir iç içe yapının bir sonraki en içteki yapıda tamamen dahil olması gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="8e0b7-121">This means that any nested structure must be completely contained within the next innermost structure.</span></span> <span data-ttu-id="8e0b7-122">Örneğin, `For` döngüsü iç `With` bloğunun sonlandırmadan önce sonlandırdığı için aşağıdaki düzenleme geçersizdir.</span><span class="sxs-lookup"><span data-stu-id="8e0b7-122">For example, the following arrangement is invalid because the `For` loop terminates before the inner `With` block terminates.</span></span>  
  
 ![Geçersiz iç içe geçme örneğini gösteren diyagram.](./media/nested-control-structures/example-invalid-nesting.gif) 
  
 <span data-ttu-id="8e0b7-124">Visual Basic derleyici, bu tür çakışan denetim yapılarını algılar ve derleme zamanı hatasına işaret eder.</span><span class="sxs-lookup"><span data-stu-id="8e0b7-124">The Visual Basic compiler detects such overlapping control structures and signals a compile-time error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e0b7-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8e0b7-125">See also</span></span>

- [<span data-ttu-id="8e0b7-126">Denetim Akışı</span><span class="sxs-lookup"><span data-stu-id="8e0b7-126">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [<span data-ttu-id="8e0b7-127">Karar Yapıları</span><span class="sxs-lookup"><span data-stu-id="8e0b7-127">Decision Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [<span data-ttu-id="8e0b7-128">Döngü Yapıları</span><span class="sxs-lookup"><span data-stu-id="8e0b7-128">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="8e0b7-129">Diğer Denetim Yapıları</span><span class="sxs-lookup"><span data-stu-id="8e0b7-129">Other Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
