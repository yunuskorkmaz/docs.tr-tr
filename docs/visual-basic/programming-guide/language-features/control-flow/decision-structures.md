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
ms.openlocfilehash: 4aabb1eef717b06222696980d4cbce7a781fb567
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54735253"
---
# <a name="decision-structures-visual-basic"></a><span data-ttu-id="1aabf-102">Karar Yapıları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1aabf-102">Decision Structures (Visual Basic)</span></span>
<span data-ttu-id="1aabf-103">Visual Basic koşulları test etmeye ve test sonuçlarına bağlı olarak farklı işlemler gerçekleştirmek olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="1aabf-103">Visual Basic lets you test conditions and perform different operations depending on the results of that test.</span></span> <span data-ttu-id="1aabf-104">True veya false, bir ifadenin çeşitli değerleri için veya bir deyimler serisini çalıştırdığınızda oluşturulan çeşitli özel durumlar için olan bir koşul için test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1aabf-104">You can test for a condition being true or false, for various values of an expression, or for various exceptions generated when you execute a series of statements.</span></span>  
  
 <span data-ttu-id="1aabf-105">Aşağıdaki çizim true olan bir koşulu sınar ve doğru veya yanlış olmasına bağlı olarak farklı eylemler geçen bir karar yapısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1aabf-105">The following illustration shows a decision structure that tests for a condition being true and takes different actions depending on whether it is true or false.</span></span>  
  
 <span data-ttu-id="1aabf-106">![Akış Çizelgesi bir If... Daha sonra... Başka bir yapı](../../../../visual-basic/programming-guide/language-features/control-flow/media/ifthenelse.gif "IfThenElse")</span><span class="sxs-lookup"><span data-stu-id="1aabf-106">![Flow chart of an If...Then...Else construction](../../../../visual-basic/programming-guide/language-features/control-flow/media/ifthenelse.gif "IfThenElse")</span></span>  
<span data-ttu-id="1aabf-107">Bir koşul true ve false olduğunda olduğunda farklı eylemler alma</span><span class="sxs-lookup"><span data-stu-id="1aabf-107">Taking different actions when a condition is true and when it is false</span></span>  
  
## <a name="ifthenelse-construction"></a><span data-ttu-id="1aabf-108">If... Daha sonra... Başka bir yapı</span><span class="sxs-lookup"><span data-stu-id="1aabf-108">If...Then...Else Construction</span></span>  
 <span data-ttu-id="1aabf-109">`If...Then...Else` yapılarını için bir veya daha fazla koşulları test etmeye ve bir veya daha fazla deyim her koşula bağlı çalıştırmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="1aabf-109">`If...Then...Else` constructions let you test for one or more conditions and run one or more statements depending on each condition.</span></span> <span data-ttu-id="1aabf-110">Koşulları test etmeye ve eylemleri aşağıdaki yollarla kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1aabf-110">You can test conditions and take actions in the following ways:</span></span>  
  
-   <span data-ttu-id="1aabf-111">Bir koşul ise, bir veya daha fazla deyimleri çalıştırın `True`</span><span class="sxs-lookup"><span data-stu-id="1aabf-111">Run one or more statements if a condition is `True`</span></span>  
  
-   <span data-ttu-id="1aabf-112">Bir koşul ise, bir veya daha fazla deyimleri çalıştırın `False`</span><span class="sxs-lookup"><span data-stu-id="1aabf-112">Run one or more statements if a condition is `False`</span></span>  
  
-   <span data-ttu-id="1aabf-113">Bir koşul ise, bazı deyimleri çalıştırın `True` ve diğerleri ise `False`</span><span class="sxs-lookup"><span data-stu-id="1aabf-113">Run some statements if a condition is `True` and others if it is `False`</span></span>  
  
-   <span data-ttu-id="1aabf-114">Önceki koşul ise, ek bir koşul testi `False`</span><span class="sxs-lookup"><span data-stu-id="1aabf-114">Test an additional condition if a prior condition is `False`</span></span>  
  
 <span data-ttu-id="1aabf-115">Tüm bu olanaklar sunan denetim yapısı [varsa... Daha sonra... Else deyimi](../../../../visual-basic/language-reference/statements/if-then-else-statement.md).</span><span class="sxs-lookup"><span data-stu-id="1aabf-115">The control structure that offers all these possibilities is the [If...Then...Else Statement](../../../../visual-basic/language-reference/statements/if-then-else-statement.md).</span></span> <span data-ttu-id="1aabf-116">Sadece bir test ve çalıştırmak için bir ifade varsa, tek satır sürümü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1aabf-116">You can use a single-line version if you have just one test and one statement to run.</span></span> <span data-ttu-id="1aabf-117">Koşullar ve Eylemler daha karmaşık bir dizi varsa, birden çok satır sürümü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1aabf-117">If you have a more complex set of conditions and actions, you can use the multiple-line version.</span></span>  
  
## <a name="selectcase-construction"></a><span data-ttu-id="1aabf-118">Seçin... Servis talebi oluşturma</span><span class="sxs-lookup"><span data-stu-id="1aabf-118">Select...Case Construction</span></span>  
 <span data-ttu-id="1aabf-119">`Select...Case` Yapım bir ifade bir kez ve farklı farklı olası değerlere dayalı ifadeler kümesi çalıştırmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="1aabf-119">The `Select...Case` construction lets you evaluate an expression one time and run different sets of statements based on different possible values.</span></span> <span data-ttu-id="1aabf-120">Daha fazla bilgi için [seçin... Case deyimi](../../../../visual-basic/language-reference/statements/select-case-statement.md).</span><span class="sxs-lookup"><span data-stu-id="1aabf-120">For more information, see [Select...Case Statement](../../../../visual-basic/language-reference/statements/select-case-statement.md).</span></span>  
  
## <a name="trycatchfinally-construction"></a><span data-ttu-id="1aabf-121">Deneyin... Catch... Son olarak oluşturma</span><span class="sxs-lookup"><span data-stu-id="1aabf-121">Try...Catch...Finally Construction</span></span>  
 <span data-ttu-id="1aabf-122">`Try...Catch...Finally` yapılarını deyimler, deyim herhangi bir özel durum neden olursa denetimi elinde bir ortamda altında kümesi çalıştırmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="1aabf-122">`Try...Catch...Finally` constructions let you run a set of statements under an environment that retains control if any one of your statements causes an exception.</span></span> <span data-ttu-id="1aabf-123">Farklı özel durumlar için farklı eylemleri gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1aabf-123">You can take different actions for different exceptions.</span></span> <span data-ttu-id="1aabf-124">İsteğe bağlı olarak tüm çıkmadan önce çalışan bir kod bloğunu belirtebilirsiniz `Try...Catch...Finally` ne olacağını bağımsız olarak oluşturma,.</span><span class="sxs-lookup"><span data-stu-id="1aabf-124">You can optionally specify a block of code that runs before you exit the whole `Try...Catch...Finally` construction, regardless of what occurs.</span></span> <span data-ttu-id="1aabf-125">Daha fazla bilgi için [deneyin... Catch... Finally deyimini](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="1aabf-125">For more information, see [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1aabf-126">Bir anahtar sözcük tıkladığınızda birçok denetim yapıları için anahtar sözcükleri yapısındaki tüm vurgulanır.</span><span class="sxs-lookup"><span data-stu-id="1aabf-126">For many control structures, when you click a keyword, all of the keywords in the structure are highlighted.</span></span> <span data-ttu-id="1aabf-127">Örneği için tıkladığınızda `If` içinde bir `If...Then...Else` oluşturma, tüm örneklerini `If`, `Then`, `ElseIf`, `Else`, ve `End If` yapısında vurgulanır.</span><span class="sxs-lookup"><span data-stu-id="1aabf-127">For instance, when you click `If` in an `If...Then...Else` construction, all instances of `If`, `Then`, `ElseIf`, `Else`, and `End If` in the construction are highlighted.</span></span> <span data-ttu-id="1aabf-128">Sonraki veya önceki vurgulanan anahtar taşımak için CTRL + SHIFT + Aşağı Ok veya CTRL + SHIFT + Yukarı Ok tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="1aabf-128">To move to the next or previous highlighted keyword, press CTRL+SHIFT+DOWN ARROW or CTRL+SHIFT+UP ARROW.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1aabf-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1aabf-129">See also</span></span>
- [<span data-ttu-id="1aabf-130">Denetim Akışı</span><span class="sxs-lookup"><span data-stu-id="1aabf-130">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [<span data-ttu-id="1aabf-131">Döngü Yapıları</span><span class="sxs-lookup"><span data-stu-id="1aabf-131">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="1aabf-132">Diğer Denetim Yapıları</span><span class="sxs-lookup"><span data-stu-id="1aabf-132">Other Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
- [<span data-ttu-id="1aabf-133">İç İçe Geçmiş Denetim Yapıları</span><span class="sxs-lookup"><span data-stu-id="1aabf-133">Nested Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="1aabf-134">If İşleci</span><span class="sxs-lookup"><span data-stu-id="1aabf-134">If Operator</span></span>](../../../../visual-basic/language-reference/operators/if-operator.md)
