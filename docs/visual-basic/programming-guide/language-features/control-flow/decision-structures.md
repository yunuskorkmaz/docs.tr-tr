---
title: Karar Yapıları (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- statements [Visual Basic], control flow
- If statement [Visual Basic], decision structures
- If statement [Visual Basic], If...Then...Else
- control flow [Visual Basic], decision structures
- decision structures [Visual Basic]
- conditional statements [Visual Basic], decision structures
ms.assetid: 2e2e0895-4483-442a-b17c-26aead751ec2
caps.latest.revision: 29
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3b89d6f9b27e086b657c29f3353b63cdd855ae19
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="decision-structures-visual-basic"></a><span data-ttu-id="da802-102">Karar Yapıları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="da802-102">Decision Structures (Visual Basic)</span></span>
<span data-ttu-id="da802-103">Visual Basic koşullarda test ve test sonuçlarını bağlı olarak farklı işlemler gerçekleştirmek olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="da802-103">Visual Basic lets you test conditions and perform different operations depending on the results of that test.</span></span> <span data-ttu-id="da802-104">True veya false ifade çeşitli değerleri için veya bir dizi deyimi yürüttüğünüzde oluşturulan çeşitli özel durumlar için olan bir koşul için test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="da802-104">You can test for a condition being true or false, for various values of an expression, or for various exceptions generated when you execute a series of statements.</span></span>  
  
 <span data-ttu-id="da802-105">Aşağıdaki çizimde, true olan bir koşulu sınar ve doğru veya yanlış olmasına bağlı olarak farklı eylemleri gerçekleştirir karar yapısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="da802-105">The following illustration shows a decision structure that tests for a condition being true and takes different actions depending on whether it is true or false.</span></span>  
  
 <span data-ttu-id="da802-106">![Akış Çizelgesi bir if... Then... Else yapım](../../../../visual-basic/programming-guide/language-features/control-flow/media/ifthenelse.gif "IfThenElse")</span><span class="sxs-lookup"><span data-stu-id="da802-106">![Flow chart of an If...Then...Else construction](../../../../visual-basic/programming-guide/language-features/control-flow/media/ifthenelse.gif "IfThenElse")</span></span>  
<span data-ttu-id="da802-107">Bir koşul true ve false olduğunda olduğunda farklı eylemler alma</span><span class="sxs-lookup"><span data-stu-id="da802-107">Taking different actions when a condition is true and when it is false</span></span>  
  
## <a name="ifthenelse-construction"></a><span data-ttu-id="da802-108">If... Then... Else yapımı</span><span class="sxs-lookup"><span data-stu-id="da802-108">If...Then...Else Construction</span></span>  
 <span data-ttu-id="da802-109">`If...Then...Else` kurulumlarını için bir veya daha fazla koşullarda test ve her koşul bağlı olarak bir veya daha fazla deyimleri çalıştırmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="da802-109">`If...Then...Else` constructions let you test for one or more conditions and run one or more statements depending on each condition.</span></span> <span data-ttu-id="da802-110">Koşullarda test ve aşağıdaki yollarla eylemleri gerçekleştirin:</span><span class="sxs-lookup"><span data-stu-id="da802-110">You can test conditions and take actions in the following ways:</span></span>  
  
-   <span data-ttu-id="da802-111">Bir koşul ise, bir veya daha fazla deyimlerini çalıştırın `True`</span><span class="sxs-lookup"><span data-stu-id="da802-111">Run one or more statements if a condition is `True`</span></span>  
  
-   <span data-ttu-id="da802-112">Bir koşul ise, bir veya daha fazla deyimlerini çalıştırın `False`</span><span class="sxs-lookup"><span data-stu-id="da802-112">Run one or more statements if a condition is `False`</span></span>  
  
-   <span data-ttu-id="da802-113">Bir koşul ise, bazı deyimleri çalıştırmak `True` ve diğerleri etkinleştirilmişse `False`</span><span class="sxs-lookup"><span data-stu-id="da802-113">Run some statements if a condition is `True` and others if it is `False`</span></span>  
  
-   <span data-ttu-id="da802-114">Önceki bir koşul ise, ek bir koşulu test `False`</span><span class="sxs-lookup"><span data-stu-id="da802-114">Test an additional condition if a prior condition is `False`</span></span>  
  
 <span data-ttu-id="da802-115">Bu olanakları sunar denetim yapısı [varsa... Then... Else deyimi](../../../../visual-basic/language-reference/statements/if-then-else-statement.md).</span><span class="sxs-lookup"><span data-stu-id="da802-115">The control structure that offers all these possibilities is the [If...Then...Else Statement](../../../../visual-basic/language-reference/statements/if-then-else-statement.md).</span></span> <span data-ttu-id="da802-116">Yalnızca bir test ve çalıştırmak için bir deyim varsa tek satırlı sürüm kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="da802-116">You can use a single-line version if you have just one test and one statement to run.</span></span> <span data-ttu-id="da802-117">Koşullar ve Eylemler daha karmaşık bir dizi varsa, birden çok satır sürümü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="da802-117">If you have a more complex set of conditions and actions, you can use the multiple-line version.</span></span>  
  
## <a name="selectcase-construction"></a><span data-ttu-id="da802-118">Seçin... Örnek oluşturma</span><span class="sxs-lookup"><span data-stu-id="da802-118">Select...Case Construction</span></span>  
 <span data-ttu-id="da802-119">`Select...Case` Yapım bir ifadenin bir kez değerlendirmek ve çalışma farklı olası değerlerine göre deyimlerinin farklı ayarlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="da802-119">The `Select...Case` construction lets you evaluate an expression one time and run different sets of statements based on different possible values.</span></span> <span data-ttu-id="da802-120">Daha fazla bilgi için bkz: [seçin... Case deyimi](../../../../visual-basic/language-reference/statements/select-case-statement.md).</span><span class="sxs-lookup"><span data-stu-id="da802-120">For more information, see [Select...Case Statement](../../../../visual-basic/language-reference/statements/select-case-statement.md).</span></span>  
  
## <a name="trycatchfinally-construction"></a><span data-ttu-id="da802-121">Try... Catch... Son olarak oluşturma</span><span class="sxs-lookup"><span data-stu-id="da802-121">Try...Catch...Finally Construction</span></span>  
 <span data-ttu-id="da802-122">`Try...Catch...Finally` kurulumlarını deyimleri altında bir özel durum, deyimleri herhangi biri neden olursa, Denetim korur bir ortam kümesi çalıştırmanıza izin.</span><span class="sxs-lookup"><span data-stu-id="da802-122">`Try...Catch...Finally` constructions let you run a set of statements under an environment that retains control if any one of your statements causes an exception.</span></span> <span data-ttu-id="da802-123">Farklı özel durumlar için farklı işlemler yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="da802-123">You can take different actions for different exceptions.</span></span> <span data-ttu-id="da802-124">İsteğe bağlı olarak tüm çıkmadan önce çalışan bir kod bloğunu belirtebilirsiniz `Try...Catch...Finally` neler bağımsız olarak oluşturma.</span><span class="sxs-lookup"><span data-stu-id="da802-124">You can optionally specify a block of code that runs before you exit the whole `Try...Catch...Finally` construction, regardless of what occurs.</span></span> <span data-ttu-id="da802-125">Daha fazla bilgi için bkz: [deneyin... Catch... Finally ifadesi](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="da802-125">For more information, see [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="da802-126">Bir anahtar sözcüğü tıklattığınızda birçok denetim yapıları için tüm anahtar sözcükleri yapısında vurgulanır.</span><span class="sxs-lookup"><span data-stu-id="da802-126">For many control structures, when you click a keyword, all of the keywords in the structure are highlighted.</span></span> <span data-ttu-id="da802-127">Örneği için tıkladığınızda `If` içinde bir `If...Then...Else` yapım, tüm örneklerini `If`, `Then`, `ElseIf`, `Else`, ve `End If` yapısında vurgulanır.</span><span class="sxs-lookup"><span data-stu-id="da802-127">For instance, when you click `If` in an `If...Then...Else` construction, all instances of `If`, `Then`, `ElseIf`, `Else`, and `End If` in the construction are highlighted.</span></span> <span data-ttu-id="da802-128">Sonraki veya önceki vurgulanan anahtar sözcüğe taşımak için CTRL + SHIFT + Aşağı Ok veya CTRL + SHIFT + Yukarı Ok tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="da802-128">To move to the next or previous highlighted keyword, press CTRL+SHIFT+DOWN ARROW or CTRL+SHIFT+UP ARROW.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da802-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="da802-129">See Also</span></span>  
 [<span data-ttu-id="da802-130">Denetim Akışı</span><span class="sxs-lookup"><span data-stu-id="da802-130">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)  
 [<span data-ttu-id="da802-131">Döngü Yapıları</span><span class="sxs-lookup"><span data-stu-id="da802-131">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [<span data-ttu-id="da802-132">Diğer Denetim Yapıları</span><span class="sxs-lookup"><span data-stu-id="da802-132">Other Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)  
 [<span data-ttu-id="da802-133">İç İçe Geçmiş Denetim Yapıları</span><span class="sxs-lookup"><span data-stu-id="da802-133">Nested Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [<span data-ttu-id="da802-134">If İşleci</span><span class="sxs-lookup"><span data-stu-id="da802-134">If Operator</span></span>](../../../../visual-basic/language-reference/operators/if-operator.md)
