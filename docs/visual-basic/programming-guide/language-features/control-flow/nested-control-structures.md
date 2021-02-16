---
description: 'Daha fazla bilgi edinin: Iç Içe denetim yapıları (Visual Basic)'
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
ms.openlocfilehash: 086e1201cab3ea133b01a003de58f8d3e67bfc44
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100473608"
---
# <a name="nested-control-structures-visual-basic"></a><span data-ttu-id="53b6b-103">İç İçe Geçmiş Denetim Yapıları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="53b6b-103">Nested Control Structures (Visual Basic)</span></span>

<span data-ttu-id="53b6b-104">Denetim deyimlerini diğer denetim deyimlerinin içine yerleştirebilirsiniz. Örneğin, `If...Then...Else` bir döngü içindeki bir blok `For...Next` .</span><span class="sxs-lookup"><span data-stu-id="53b6b-104">You can place control statements inside other control statements, for example an `If...Then...Else` block within a `For...Next` loop.</span></span> <span data-ttu-id="53b6b-105">Başka bir denetim ifadesinin içine yerleştirilmiş bir denetim ifadesinin *iç içe* olduğu söylenir.</span><span class="sxs-lookup"><span data-stu-id="53b6b-105">A control statement placed inside another control statement is said to be *nested*.</span></span>  
  
## <a name="nesting-levels"></a><span data-ttu-id="53b6b-106">İç içe düzeyler</span><span class="sxs-lookup"><span data-stu-id="53b6b-106">Nesting Levels</span></span>  

 <span data-ttu-id="53b6b-107">Visual Basic içindeki denetim yapıları, istediğiniz kadar sayıda düzeyde iç içe olabilir.</span><span class="sxs-lookup"><span data-stu-id="53b6b-107">Control structures in Visual Basic can be nested to as many levels as you want.</span></span> <span data-ttu-id="53b6b-108">İç içe yapıları, her birinin gövdesini girintileyerek daha okunaklı hale getirmek yaygın bir uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="53b6b-108">It is common practice to make nested structures more readable by indenting the body of each one.</span></span> <span data-ttu-id="53b6b-109">Tümleşik geliştirme ortamı (IDE) Düzenleyicisi bunu otomatik olarak yapar.</span><span class="sxs-lookup"><span data-stu-id="53b6b-109">The integrated development environment (IDE) editor automatically does this.</span></span>  
  
 <span data-ttu-id="53b6b-110">Aşağıdaki örnekte, yordam `sumRows` matrisin her satırının pozitif öğelerini birlikte ekler.</span><span class="sxs-lookup"><span data-stu-id="53b6b-110">In the following example, the procedure `sumRows` adds together the positive elements of each row of the matrix.</span></span>  
  
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
  
 <span data-ttu-id="53b6b-111">Yukarıdaki örnekte, ilk `Next` ifade iç `For` döngüyü kapatır ve son `Next` ifade dıştaki `For` döngüyü kapatır.</span><span class="sxs-lookup"><span data-stu-id="53b6b-111">In the preceding example, the first `Next` statement closes the inner `For` loop and the last `Next` statement closes the outer `For` loop.</span></span>  
  
 <span data-ttu-id="53b6b-112">Benzer şekilde, iç içe geçmiş `If` deyimlerde `End If` deyimler, en yakın önceki ifadeye otomatik olarak uygulanır `If` .</span><span class="sxs-lookup"><span data-stu-id="53b6b-112">Likewise, in nested `If` statements, the `End If` statements automatically apply to the nearest prior `If` statement.</span></span> <span data-ttu-id="53b6b-113">İç içe `Do` döngüler benzer bir şekilde çalışarak en `Loop` içteki ifadesiyle eşleşen en içteki deyimle birlikte çalışır `Do` .</span><span class="sxs-lookup"><span data-stu-id="53b6b-113">Nested `Do` loops work in a similar fashion, with the innermost `Loop` statement matching the innermost `Do` statement.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="53b6b-114">Birçok denetim yapısında, bir anahtar sözcüğe tıkladığınızda yapıdaki tüm anahtar sözcükler vurgulanır.</span><span class="sxs-lookup"><span data-stu-id="53b6b-114">For many control structures, when you click a keyword, all of the keywords in the structure are highlighted.</span></span> <span data-ttu-id="53b6b-115">Örneğin, bir yapıya tıkladığınızda,,,, `If` `If...Then...Else` `If` `Then` `ElseIf` `Else` ve `End If` oluşturma içindeki tüm örnekleri vurgulanır.</span><span class="sxs-lookup"><span data-stu-id="53b6b-115">For instance, when you click `If` in an `If...Then...Else` construction, all instances of `If`, `Then`, `ElseIf`, `Else`, and `End If` in the construction are highlighted.</span></span> <span data-ttu-id="53b6b-116">Sonraki veya önceki vurgulanmış anahtar sözcüğe geçmek için CTRL + SHIFT + aşağı ok veya CTRL + SHIFT + yukarı ok tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="53b6b-116">To move to the next or previous highlighted keyword, press CTRL+SHIFT+DOWN ARROW or CTRL+SHIFT+UP ARROW.</span></span>  
  
## <a name="nesting-different-kinds-of-control-structures"></a><span data-ttu-id="53b6b-117">Farklı türlerdeki denetim yapılarını iç içe geçirme</span><span class="sxs-lookup"><span data-stu-id="53b6b-117">Nesting Different Kinds of Control Structures</span></span>  

 <span data-ttu-id="53b6b-118">Bir tür denetim yapısını başka bir tür içinde iç içe geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="53b6b-118">You can nest one kind of control structure within another kind.</span></span> <span data-ttu-id="53b6b-119">Aşağıdaki örnek, `With` döngüsünün içinde bir blok `For Each` ve `If` blok içindeki iç içe bloklar kullanır `With` .</span><span class="sxs-lookup"><span data-stu-id="53b6b-119">The following example uses a `With` block inside a `For Each` loop and nested `If` blocks inside the `With` block.</span></span>  
  
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
  
## <a name="overlapping-control-structures"></a><span data-ttu-id="53b6b-120">Çakışan denetim yapıları</span><span class="sxs-lookup"><span data-stu-id="53b6b-120">Overlapping Control Structures</span></span>  

 <span data-ttu-id="53b6b-121">Denetim yapılarıyla çakışamaz.</span><span class="sxs-lookup"><span data-stu-id="53b6b-121">You cannot overlap control structures.</span></span> <span data-ttu-id="53b6b-122">Bu, herhangi bir iç içe yapının bir sonraki en içteki yapıda tamamen dahil olması gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="53b6b-122">This means that any nested structure must be completely contained within the next innermost structure.</span></span> <span data-ttu-id="53b6b-123">Örneğin, `For` döngü iç blok sonlandırılmadan önce sonlandırdığı için aşağıdaki düzenleme geçersizdir `With` .</span><span class="sxs-lookup"><span data-stu-id="53b6b-123">For example, the following arrangement is invalid because the `For` loop terminates before the inner `With` block terminates.</span></span>  
  
 ![Geçersiz iç içe geçme örneğini gösteren diyagram.](./media/nested-control-structures/example-invalid-nesting.gif)
  
 <span data-ttu-id="53b6b-125">Visual Basic derleyici, bu tür çakışan denetim yapılarını algılar ve derleme zamanı hatasına işaret eder.</span><span class="sxs-lookup"><span data-stu-id="53b6b-125">The Visual Basic compiler detects such overlapping control structures and signals a compile-time error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53b6b-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="53b6b-126">See also</span></span>

- [<span data-ttu-id="53b6b-127">Denetim akışı</span><span class="sxs-lookup"><span data-stu-id="53b6b-127">Control Flow</span></span>](index.md)
- [<span data-ttu-id="53b6b-128">Karar Yapıları</span><span class="sxs-lookup"><span data-stu-id="53b6b-128">Decision Structures</span></span>](decision-structures.md)
- [<span data-ttu-id="53b6b-129">Döngü Yapıları</span><span class="sxs-lookup"><span data-stu-id="53b6b-129">Loop Structures</span></span>](loop-structures.md)
- [<span data-ttu-id="53b6b-130">Diğer Denetim Yapıları</span><span class="sxs-lookup"><span data-stu-id="53b6b-130">Other Control Structures</span></span>](other-control-structures.md)
