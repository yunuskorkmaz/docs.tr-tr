---
title: Karar Yapıları (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- statements [Visual Basic], control flow
- If statement [Visual Basic], decision structures
- If statement [Visual Basic], If...Then...Else
- control flow [Visual Basic], decision structures
- decision structures [Visual Basic]
- conditional statements [Visual Basic], decision structures
ms.assetid: 2e2e0895-4483-442a-b17c-26aead751ec2
ms.openlocfilehash: f8b653b941c5959036256cde097a41f8c6251c7a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64601239"
---
# <a name="decision-structures-visual-basic"></a><span data-ttu-id="b6582-102">Karar Yapıları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b6582-102">Decision Structures (Visual Basic)</span></span>
<span data-ttu-id="b6582-103">Visual Basic koşulları test etmeye ve test sonuçlarına bağlı olarak farklı işlemler gerçekleştirmek olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="b6582-103">Visual Basic lets you test conditions and perform different operations depending on the results of that test.</span></span> <span data-ttu-id="b6582-104">True veya false, bir ifadenin çeşitli değerleri için veya bir deyimler serisini çalıştırdığınızda oluşturulan çeşitli özel durumlar için olan bir koşul için test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b6582-104">You can test for a condition being true or false, for various values of an expression, or for various exceptions generated when you execute a series of statements.</span></span>  
  
 <span data-ttu-id="b6582-105">Aşağıdaki çizim true olan bir koşulu sınar ve doğru veya yanlış olmasına bağlı olarak farklı eylemler geçen bir karar yapısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b6582-105">The following illustration shows a decision structure that tests for a condition being true and takes different actions depending on whether it is true or false.</span></span>  
  
 ![Eğer bir akış çizelgesi... Daha sonra... Başka oluşturma.](./media/decision-structures/if-then-else-construction.gif)  
  
## <a name="ifthenelse-construction"></a><span data-ttu-id="b6582-107">If... Daha sonra... Başka bir yapı</span><span class="sxs-lookup"><span data-stu-id="b6582-107">If...Then...Else Construction</span></span>  
 <span data-ttu-id="b6582-108">`If...Then...Else` yapılarını için bir veya daha fazla koşulları test etmeye ve bir veya daha fazla deyim her koşula bağlı çalıştırmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="b6582-108">`If...Then...Else` constructions let you test for one or more conditions and run one or more statements depending on each condition.</span></span> <span data-ttu-id="b6582-109">Koşulları test etmeye ve eylemleri aşağıdaki yollarla kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="b6582-109">You can test conditions and take actions in the following ways:</span></span>  
  
- <span data-ttu-id="b6582-110">Bir koşul ise, bir veya daha fazla deyimleri çalıştırın `True`</span><span class="sxs-lookup"><span data-stu-id="b6582-110">Run one or more statements if a condition is `True`</span></span>  
  
- <span data-ttu-id="b6582-111">Bir koşul ise, bir veya daha fazla deyimleri çalıştırın `False`</span><span class="sxs-lookup"><span data-stu-id="b6582-111">Run one or more statements if a condition is `False`</span></span>  
  
- <span data-ttu-id="b6582-112">Bir koşul ise, bazı deyimleri çalıştırın `True` ve diğerleri ise `False`</span><span class="sxs-lookup"><span data-stu-id="b6582-112">Run some statements if a condition is `True` and others if it is `False`</span></span>  
  
- <span data-ttu-id="b6582-113">Önceki koşul ise, ek bir koşul testi `False`</span><span class="sxs-lookup"><span data-stu-id="b6582-113">Test an additional condition if a prior condition is `False`</span></span>  
  
 <span data-ttu-id="b6582-114">Tüm bu olanaklar sunan denetim yapısı [varsa... Daha sonra... Else deyimi](../../../../visual-basic/language-reference/statements/if-then-else-statement.md).</span><span class="sxs-lookup"><span data-stu-id="b6582-114">The control structure that offers all these possibilities is the [If...Then...Else Statement](../../../../visual-basic/language-reference/statements/if-then-else-statement.md).</span></span> <span data-ttu-id="b6582-115">Sadece bir test ve çalıştırmak için bir ifade varsa, tek satır sürümü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b6582-115">You can use a single-line version if you have just one test and one statement to run.</span></span> <span data-ttu-id="b6582-116">Koşullar ve Eylemler daha karmaşık bir dizi varsa, birden çok satır sürümü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b6582-116">If you have a more complex set of conditions and actions, you can use the multiple-line version.</span></span>  
  
## <a name="selectcase-construction"></a><span data-ttu-id="b6582-117">Seçin... Servis talebi oluşturma</span><span class="sxs-lookup"><span data-stu-id="b6582-117">Select...Case Construction</span></span>  
 <span data-ttu-id="b6582-118">`Select...Case` Yapım bir ifade bir kez ve farklı farklı olası değerlere dayalı ifadeler kümesi çalıştırmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="b6582-118">The `Select...Case` construction lets you evaluate an expression one time and run different sets of statements based on different possible values.</span></span> <span data-ttu-id="b6582-119">Daha fazla bilgi için [seçin... Case deyimi](../../../../visual-basic/language-reference/statements/select-case-statement.md).</span><span class="sxs-lookup"><span data-stu-id="b6582-119">For more information, see [Select...Case Statement](../../../../visual-basic/language-reference/statements/select-case-statement.md).</span></span>  
  
## <a name="trycatchfinally-construction"></a><span data-ttu-id="b6582-120">Deneyin... Catch... Son olarak oluşturma</span><span class="sxs-lookup"><span data-stu-id="b6582-120">Try...Catch...Finally Construction</span></span>  
 <span data-ttu-id="b6582-121">`Try...Catch...Finally` yapılarını deyimler, deyim herhangi bir özel durum neden olursa denetimi elinde bir ortamda altında kümesi çalıştırmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="b6582-121">`Try...Catch...Finally` constructions let you run a set of statements under an environment that retains control if any one of your statements causes an exception.</span></span> <span data-ttu-id="b6582-122">Farklı özel durumlar için farklı eylemleri gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b6582-122">You can take different actions for different exceptions.</span></span> <span data-ttu-id="b6582-123">İsteğe bağlı olarak tüm çıkmadan önce çalışan bir kod bloğunu belirtebilirsiniz `Try...Catch...Finally` ne olacağını bağımsız olarak oluşturma,.</span><span class="sxs-lookup"><span data-stu-id="b6582-123">You can optionally specify a block of code that runs before you exit the whole `Try...Catch...Finally` construction, regardless of what occurs.</span></span> <span data-ttu-id="b6582-124">Daha fazla bilgi için [deneyin... Catch... Finally deyimini](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="b6582-124">For more information, see [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b6582-125">Bir anahtar sözcük tıkladığınızda birçok denetim yapıları için anahtar sözcükleri yapısındaki tüm vurgulanır.</span><span class="sxs-lookup"><span data-stu-id="b6582-125">For many control structures, when you click a keyword, all of the keywords in the structure are highlighted.</span></span> <span data-ttu-id="b6582-126">Örneği için tıkladığınızda `If` içinde bir `If...Then...Else` oluşturma, tüm örneklerini `If`, `Then`, `ElseIf`, `Else`, ve `End If` yapısında vurgulanır.</span><span class="sxs-lookup"><span data-stu-id="b6582-126">For instance, when you click `If` in an `If...Then...Else` construction, all instances of `If`, `Then`, `ElseIf`, `Else`, and `End If` in the construction are highlighted.</span></span> <span data-ttu-id="b6582-127">Sonraki veya önceki vurgulanan anahtar taşımak için CTRL + SHIFT + Aşağı Ok veya CTRL + SHIFT + Yukarı Ok tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="b6582-127">To move to the next or previous highlighted keyword, press CTRL+SHIFT+DOWN ARROW or CTRL+SHIFT+UP ARROW.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6582-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b6582-128">See also</span></span>

- [<span data-ttu-id="b6582-129">Denetim Akışı</span><span class="sxs-lookup"><span data-stu-id="b6582-129">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [<span data-ttu-id="b6582-130">Döngü Yapıları</span><span class="sxs-lookup"><span data-stu-id="b6582-130">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="b6582-131">Diğer Denetim Yapıları</span><span class="sxs-lookup"><span data-stu-id="b6582-131">Other Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
- [<span data-ttu-id="b6582-132">İç İçe Geçmiş Denetim Yapıları</span><span class="sxs-lookup"><span data-stu-id="b6582-132">Nested Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="b6582-133">If İşleci</span><span class="sxs-lookup"><span data-stu-id="b6582-133">If Operator</span></span>](../../../../visual-basic/language-reference/operators/if-operator.md)
