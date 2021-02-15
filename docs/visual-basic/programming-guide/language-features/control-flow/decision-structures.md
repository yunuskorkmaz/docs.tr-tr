---
description: 'Daha fazla bilgi edinin: karar yapıları (Visual Basic)'
title: Karar Yapıları
ms.date: 07/20/2015
helpviewer_keywords:
- statements [Visual Basic], control flow
- If statement [Visual Basic], decision structures
- If statement [Visual Basic], If...Then...Else
- control flow [Visual Basic], decision structures
- decision structures [Visual Basic]
- conditional statements [Visual Basic], decision structures
ms.assetid: 2e2e0895-4483-442a-b17c-26aead751ec2
ms.openlocfilehash: 76b63d2cdc238ec5590d11a6a802f55866990a3a
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100480693"
---
# <a name="decision-structures-visual-basic"></a><span data-ttu-id="900bd-103">Karar Yapıları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="900bd-103">Decision Structures (Visual Basic)</span></span>

<span data-ttu-id="900bd-104">Visual Basic, test koşullarını test etmenizi ve bu testin sonuçlarına bağlı olarak farklı işlemler gerçekleştirmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="900bd-104">Visual Basic lets you test conditions and perform different operations depending on the results of that test.</span></span> <span data-ttu-id="900bd-105">Bir koşulu doğru veya yanlış olarak, bir ifadenin çeşitli değerleri için ya da bir dizi deyim yürüttüğünüzde oluşturulan çeşitli özel durumlar için test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="900bd-105">You can test for a condition being true or false, for various values of an expression, or for various exceptions generated when you execute a series of statements.</span></span>  
  
 <span data-ttu-id="900bd-106">Aşağıdaki çizimde, bir koşulu test eden ve doğru ya da yanlış olmasına bağlı olarak farklı eylemler alan bir karar yapısı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="900bd-106">The following illustration shows a decision structure that tests for a condition being true and takes different actions depending on whether it is true or false.</span></span>  
  
 ![If... öğesinin akış grafiği Sonra... Başka oluşturma.](./media/decision-structures/if-then-else-construction.gif)  
  
## <a name="ifthenelse-construction"></a><span data-ttu-id="900bd-108">If... Sonra... Başka oluşturma</span><span class="sxs-lookup"><span data-stu-id="900bd-108">If...Then...Else Construction</span></span>  

 <span data-ttu-id="900bd-109">`If...Then...Else` kurulumlarını bir veya daha fazla koşulu test etmenize ve her koşula bağlı olarak bir veya daha fazla deyim çalıştırmanıza izin verir.</span><span class="sxs-lookup"><span data-stu-id="900bd-109">`If...Then...Else` constructions let you test for one or more conditions and run one or more statements depending on each condition.</span></span> <span data-ttu-id="900bd-110">Koşulları test edebilir ve aşağıdaki yollarla işlem yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="900bd-110">You can test conditions and take actions in the following ways:</span></span>  
  
- <span data-ttu-id="900bd-111">Bir koşul varsa bir veya daha fazla deyimi çalıştırma `True`</span><span class="sxs-lookup"><span data-stu-id="900bd-111">Run one or more statements if a condition is `True`</span></span>  
  
- <span data-ttu-id="900bd-112">Bir koşul varsa bir veya daha fazla deyimi çalıştırma `False`</span><span class="sxs-lookup"><span data-stu-id="900bd-112">Run one or more statements if a condition is `False`</span></span>  
  
- <span data-ttu-id="900bd-113">Bir koşul varsa `True` ve diğer durumlarda bazı deyimleri Çalıştır `False`</span><span class="sxs-lookup"><span data-stu-id="900bd-113">Run some statements if a condition is `True` and others if it is `False`</span></span>  
  
- <span data-ttu-id="900bd-114">Önceki bir koşul varsa, daha fazla durum test edin `False`</span><span class="sxs-lookup"><span data-stu-id="900bd-114">Test an additional condition if a prior condition is `False`</span></span>  
  
 <span data-ttu-id="900bd-115">Tüm bu olasılıkları sunan denetim yapısı If.. [. Sonra... Else bildirisi](../../../language-reference/statements/if-then-else-statement.md).</span><span class="sxs-lookup"><span data-stu-id="900bd-115">The control structure that offers all these possibilities is the [If...Then...Else Statement](../../../language-reference/statements/if-then-else-statement.md).</span></span> <span data-ttu-id="900bd-116">Yalnızca bir testiniz ve çalıştırmak için bir deyiminiz varsa, tek satırlık bir sürüm kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="900bd-116">You can use a single-line version if you have just one test and one statement to run.</span></span> <span data-ttu-id="900bd-117">Daha karmaşık koşullar ve eylemler kümesine sahipseniz, çok satırlı sürümü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="900bd-117">If you have a more complex set of conditions and actions, you can use the multiple-line version.</span></span>  
  
## <a name="selectcase-construction"></a><span data-ttu-id="900bd-118">Seç... Örnek oluşturma</span><span class="sxs-lookup"><span data-stu-id="900bd-118">Select...Case Construction</span></span>  

 <span data-ttu-id="900bd-119">`Select...Case`Oluşturma, bir ifadeyi bir kez değerlendirmenizi ve farklı olası değerlere göre farklı deyim kümelerini çalıştırmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="900bd-119">The `Select...Case` construction lets you evaluate an expression one time and run different sets of statements based on different possible values.</span></span> <span data-ttu-id="900bd-120">Daha fazla bilgi için bkz [. Select... Case bildirisi](../../../language-reference/statements/select-case-statement.md).</span><span class="sxs-lookup"><span data-stu-id="900bd-120">For more information, see [Select...Case Statement](../../../language-reference/statements/select-case-statement.md).</span></span>  
  
## <a name="trycatchfinally-construction"></a><span data-ttu-id="900bd-121">Deneyin... Yakala... Son yapım</span><span class="sxs-lookup"><span data-stu-id="900bd-121">Try...Catch...Finally Construction</span></span>  

 <span data-ttu-id="900bd-122">`Try...Catch...Finally` kurulumlarını, deyimlerinizin herhangi biri özel duruma neden olursa denetimi koruyan bir ortam altında deyim kümesi çalıştırmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="900bd-122">`Try...Catch...Finally` constructions let you run a set of statements under an environment that retains control if any one of your statements causes an exception.</span></span> <span data-ttu-id="900bd-123">Farklı özel durumlar için farklı eylemler gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="900bd-123">You can take different actions for different exceptions.</span></span> <span data-ttu-id="900bd-124">Ne olursa olsun, tüm oluşturma işleminden çıkmadan önce çalışan bir kod bloğu belirtebilirsiniz `Try...Catch...Finally` .</span><span class="sxs-lookup"><span data-stu-id="900bd-124">You can optionally specify a block of code that runs before you exit the whole `Try...Catch...Finally` construction, regardless of what occurs.</span></span> <span data-ttu-id="900bd-125">Daha fazla bilgi için bkz [. TRY... Yakala... Finally ekstresi](../../../language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="900bd-125">For more information, see [Try...Catch...Finally Statement](../../../language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="900bd-126">Birçok denetim yapısında, bir anahtar sözcüğe tıkladığınızda yapıdaki tüm anahtar sözcükler vurgulanır.</span><span class="sxs-lookup"><span data-stu-id="900bd-126">For many control structures, when you click a keyword, all of the keywords in the structure are highlighted.</span></span> <span data-ttu-id="900bd-127">Örneğin, bir yapıya tıkladığınızda,,,, `If` `If...Then...Else` `If` `Then` `ElseIf` `Else` ve `End If` oluşturma içindeki tüm örnekleri vurgulanır.</span><span class="sxs-lookup"><span data-stu-id="900bd-127">For instance, when you click `If` in an `If...Then...Else` construction, all instances of `If`, `Then`, `ElseIf`, `Else`, and `End If` in the construction are highlighted.</span></span> <span data-ttu-id="900bd-128">Sonraki veya önceki vurgulanmış anahtar sözcüğe geçmek için CTRL + SHIFT + aşağı ok veya CTRL + SHIFT + yukarı ok tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="900bd-128">To move to the next or previous highlighted keyword, press CTRL+SHIFT+DOWN ARROW or CTRL+SHIFT+UP ARROW.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="900bd-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="900bd-129">See also</span></span>

- [<span data-ttu-id="900bd-130">Denetim akışı</span><span class="sxs-lookup"><span data-stu-id="900bd-130">Control Flow</span></span>](index.md)
- [<span data-ttu-id="900bd-131">Döngü Yapıları</span><span class="sxs-lookup"><span data-stu-id="900bd-131">Loop Structures</span></span>](loop-structures.md)
- [<span data-ttu-id="900bd-132">Diğer Denetim Yapıları</span><span class="sxs-lookup"><span data-stu-id="900bd-132">Other Control Structures</span></span>](other-control-structures.md)
- [<span data-ttu-id="900bd-133">İç İçe Geçmiş Denetim Yapıları</span><span class="sxs-lookup"><span data-stu-id="900bd-133">Nested Control Structures</span></span>](nested-control-structures.md)
- [<span data-ttu-id="900bd-134">If İşleci</span><span class="sxs-lookup"><span data-stu-id="900bd-134">If Operator</span></span>](../../../language-reference/operators/if-operator.md)
