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
# <a name="nested-control-structures-visual-basic"></a><span data-ttu-id="5600d-102">İç İçe Geçmiş Denetim Yapıları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5600d-102">Nested Control Structures (Visual Basic)</span></span>
<span data-ttu-id="5600d-103">Diğer denetim ifadelerine içine denetim ifadeleri örneğin yerleştirebilirsiniz bir `If...Then...Else` içinde engelleme bir `For...Next` döngü.</span><span class="sxs-lookup"><span data-stu-id="5600d-103">You can place control statements inside other control statements, for example an `If...Then...Else` block within a `For...Next` loop.</span></span> <span data-ttu-id="5600d-104">Başka bir denetim deyimi içinde yerleştirilen bir denetim ifadesi olarak kabul edilir *iç içe geçmiş*.</span><span class="sxs-lookup"><span data-stu-id="5600d-104">A control statement placed inside another control statement is said to be *nested*.</span></span>  
  
## <a name="nesting-levels"></a><span data-ttu-id="5600d-105">İç içe geçme düzeyi</span><span class="sxs-lookup"><span data-stu-id="5600d-105">Nesting Levels</span></span>  
 <span data-ttu-id="5600d-106">Visual Basic'de denetim yapıları için istediğiniz kadar çok düzeyde iç içe.</span><span class="sxs-lookup"><span data-stu-id="5600d-106">Control structures in Visual Basic can be nested to as many levels as you want.</span></span> <span data-ttu-id="5600d-107">Her biri gövdesi girintileme tarafından iç içe geçmiş yapılar daha okunabilir hale getirmek için yaygın bir uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="5600d-107">It is common practice to make nested structures more readable by indenting the body of each one.</span></span> <span data-ttu-id="5600d-108">Tümleşik geliştirme ortamı (IDE) Düzenleyicisi'ni otomatik olarak bunu yapar.</span><span class="sxs-lookup"><span data-stu-id="5600d-108">The integrated development environment (IDE) editor automatically does this.</span></span>  
  
 <span data-ttu-id="5600d-109">Aşağıdaki örnekte, yordamı `sumRows` birlikte pozitif öğeleri matrisin her bir satır ekler.</span><span class="sxs-lookup"><span data-stu-id="5600d-109">In the following example, the procedure `sumRows` adds together the positive elements of each row of the matrix.</span></span>  
  
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
  
 <span data-ttu-id="5600d-110">Önceki örnekte, ilk `Next` deyimi kapatır iç `For` döngü ve son `Next` deyimi kapatır dış `For` döngü.</span><span class="sxs-lookup"><span data-stu-id="5600d-110">In the preceding example, the first `Next` statement closes the inner `For` loop and the last `Next` statement closes the outer `For` loop.</span></span>  
  
 <span data-ttu-id="5600d-111">Benzer şekilde, iç içe geçmiş `If` deyimleri `End If` deyimleri otomatik olarak uygulamak için en yakın önceki `If` deyimi.</span><span class="sxs-lookup"><span data-stu-id="5600d-111">Likewise, in nested `If` statements, the `End If` statements automatically apply to the nearest prior `If` statement.</span></span> <span data-ttu-id="5600d-112">İç içe geçmiş `Do` döngüler iş ise en içteki ile benzer bir şekilde `Loop` ise en içteki eşleşen deyimi `Do` deyimi.</span><span class="sxs-lookup"><span data-stu-id="5600d-112">Nested `Do` loops work in a similar fashion, with the innermost `Loop` statement matching the innermost `Do` statement.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5600d-113">Bir anahtar sözcüğü tıklattığınızda birçok denetim yapıları için tüm anahtar sözcükleri yapısında vurgulanır.</span><span class="sxs-lookup"><span data-stu-id="5600d-113">For many control structures, when you click a keyword, all of the keywords in the structure are highlighted.</span></span> <span data-ttu-id="5600d-114">Örneği için tıkladığınızda `If` içinde bir `If...Then...Else` yapım, tüm örneklerini `If`, `Then`, `ElseIf`, `Else`, ve `End If` yapısında vurgulanır.</span><span class="sxs-lookup"><span data-stu-id="5600d-114">For instance, when you click `If` in an `If...Then...Else` construction, all instances of `If`, `Then`, `ElseIf`, `Else`, and `End If` in the construction are highlighted.</span></span> <span data-ttu-id="5600d-115">Sonraki veya önceki vurgulanan anahtar sözcüğe taşımak için CTRL + SHIFT + Aşağı Ok veya CTRL + SHIFT + Yukarı Ok tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="5600d-115">To move to the next or previous highlighted keyword, press CTRL+SHIFT+DOWN ARROW or CTRL+SHIFT+UP ARROW.</span></span>  
  
## <a name="nesting-different-kinds-of-control-structures"></a><span data-ttu-id="5600d-116">Farklı türde denetim yapıları geçirme</span><span class="sxs-lookup"><span data-stu-id="5600d-116">Nesting Different Kinds of Control Structures</span></span>  
 <span data-ttu-id="5600d-117">Başka bir tür denetimi yapısında bir tür yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5600d-117">You can nest one kind of control structure within another kind.</span></span> <span data-ttu-id="5600d-118">Aşağıdaki örnek kullanan bir `With` içinde engelleme bir `For Each` döngü ve iç içe `If` içinde engeller `With` bloğu.</span><span class="sxs-lookup"><span data-stu-id="5600d-118">The following example uses a `With` block inside a `For Each` loop and nested `If` blocks inside the `With` block.</span></span>  
  
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
  
## <a name="overlapping-control-structures"></a><span data-ttu-id="5600d-119">Çakışan denetim yapıları</span><span class="sxs-lookup"><span data-stu-id="5600d-119">Overlapping Control Structures</span></span>  
 <span data-ttu-id="5600d-120">Denetim yapıları çakışamaz.</span><span class="sxs-lookup"><span data-stu-id="5600d-120">You cannot overlap control structures.</span></span> <span data-ttu-id="5600d-121">Başka bir deyişle, herhangi bir iç içe geçmiş yapısını tamamen sonraki en içteki yapısı içinde bulunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5600d-121">This means that any nested structure must be completely contained within the next innermost structure.</span></span> <span data-ttu-id="5600d-122">Örneğin, aşağıdaki düzenleme geçersiz olduğundan `For` döngü sonlandırır önce iç `With` blok sona erer.</span><span class="sxs-lookup"><span data-stu-id="5600d-122">For example, the following arrangement is invalid because the `For` loop terminates before the inner `With` block terminates.</span></span>  
  
 <span data-ttu-id="5600d-123">![Geçersiz iç içe grafik diyagramı](../../../../visual-basic/programming-guide/language-features/control-flow/media/nestexampleinvalid.gif "NestExampleInvalid")</span><span class="sxs-lookup"><span data-stu-id="5600d-123">![Graphic diagram of invalid nesting](../../../../visual-basic/programming-guide/language-features/control-flow/media/nestexampleinvalid.gif "NestExampleInvalid")</span></span>  
<span data-ttu-id="5600d-124">Geçersiz iç içe geçmiş için ile yapıları</span><span class="sxs-lookup"><span data-stu-id="5600d-124">Invalid nesting of For and With structures</span></span>  
  
 <span data-ttu-id="5600d-125">Visual Basic derleyici böyle çakışan denetim yapıları algılar ve bir derleme zamanı hatası işaret eder.</span><span class="sxs-lookup"><span data-stu-id="5600d-125">The Visual Basic compiler detects such overlapping control structures and signals a compile-time error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5600d-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5600d-126">See Also</span></span>  
 [<span data-ttu-id="5600d-127">Denetim Akışı</span><span class="sxs-lookup"><span data-stu-id="5600d-127">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)  
 [<span data-ttu-id="5600d-128">Karar Yapıları</span><span class="sxs-lookup"><span data-stu-id="5600d-128">Decision Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)  
 [<span data-ttu-id="5600d-129">Döngü Yapıları</span><span class="sxs-lookup"><span data-stu-id="5600d-129">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [<span data-ttu-id="5600d-130">Diğer Denetim Yapıları</span><span class="sxs-lookup"><span data-stu-id="5600d-130">Other Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
