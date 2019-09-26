---
title: Özyinelemeli Yordamlar (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], that call themselves
- procedures [Visual Basic], recursive
- procedures [Visual Basic], calling
- recursive procedures
- functions [Visual Basic], calling recursively
- recursion
ms.assetid: ba1d3962-b4c3-48d3-875e-96fdb4198327
ms.openlocfilehash: b08a06a07f134b7c95251848862d39339e59fe61
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274351"
---
# <a name="recursive-procedures-visual-basic"></a><span data-ttu-id="464e3-102">Özyinelemeli Yordamlar (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="464e3-102">Recursive Procedures (Visual Basic)</span></span>

<span data-ttu-id="464e3-103">*Özyinelemeli* yordam kendisini çağıran bir yordamdır.</span><span class="sxs-lookup"><span data-stu-id="464e3-103">A *recursive* procedure is one that calls itself.</span></span> <span data-ttu-id="464e3-104">Genel olarak, Visual Basic kodu yazmak için en etkili yol değildir.</span><span class="sxs-lookup"><span data-stu-id="464e3-104">In general, this is not the most effective way to write Visual Basic code.</span></span>  
  
 <span data-ttu-id="464e3-105">Aşağıdaki yordam, orijinal bağımsız değişkeninin faktöriyelini hesaplamak için özyineleme kullanır.</span><span class="sxs-lookup"><span data-stu-id="464e3-105">The following procedure uses recursion to calculate the factorial of its original argument.</span></span>  
  
 [!code-vb[VbVbcnProcedures#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#51)]  
  
## <a name="considerations-with-recursive-procedures"></a><span data-ttu-id="464e3-106">Özyinelemeli yordamlarla ilgili konular</span><span class="sxs-lookup"><span data-stu-id="464e3-106">Considerations with Recursive Procedures</span></span>

 <span data-ttu-id="464e3-107">**Koşulları sınırlandırma**.</span><span class="sxs-lookup"><span data-stu-id="464e3-107">**Limiting Conditions**.</span></span> <span data-ttu-id="464e3-108">Özyineleme 'yi sonlandıran en az bir koşul için test etmek üzere yinelemeli bir yordam tasarlaması gerekir ve ayrıca makul sayıda özyinelemeli çağrı içinde böyle bir koşulun karşılanmadığı durumu da işlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="464e3-108">You must design a recursive procedure to test for at least one condition that can terminate the recursion, and you must also handle the case where no such condition is satisfied within a reasonable number of recursive calls.</span></span> <span data-ttu-id="464e3-109">Başarısız olmadan karşılanabilecek en az bir koşul olmadan, yordamınız sonsuz bir döngüde yürütmenin yüksek bir riskini çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="464e3-109">Without at least one condition that can be met without fail, your procedure runs a high risk of executing in an infinite loop.</span></span>

 <span data-ttu-id="464e3-110">**Bellek kullanımı**.</span><span class="sxs-lookup"><span data-stu-id="464e3-110">**Memory Usage**.</span></span> <span data-ttu-id="464e3-111">Uygulamanızın yerel değişkenler için sınırlı miktarda alanı vardır.</span><span class="sxs-lookup"><span data-stu-id="464e3-111">Your application has a limited amount of space for local variables.</span></span> <span data-ttu-id="464e3-112">Her bir yordam kendi kendine her çağırdığında, yerel değişkenlerinin ek kopyaları için bu alanın daha fazlasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="464e3-112">Each time a procedure calls itself, it uses more of that space for additional copies of its local variables.</span></span> <span data-ttu-id="464e3-113">Bu işlem süresiz olarak devam ederse, bir <xref:System.StackOverflowException> hataya neden olur.</span><span class="sxs-lookup"><span data-stu-id="464e3-113">If this process continues indefinitely, it eventually causes a <xref:System.StackOverflowException> error.</span></span>

 <span data-ttu-id="464e3-114">**Verimlilik**.</span><span class="sxs-lookup"><span data-stu-id="464e3-114">**Efficiency**.</span></span> <span data-ttu-id="464e3-115">Özyineleme için neredeyse her zaman bir döngü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="464e3-115">You can almost always substitute a loop for recursion.</span></span> <span data-ttu-id="464e3-116">Döngü, bağımsız değişken geçirme, ek depolama başlatma ve değer döndürme ek yüküne sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="464e3-116">A loop does not have the overhead of passing arguments, initializing additional storage, and returning values.</span></span> <span data-ttu-id="464e3-117">Performans özyinelemeli çağrılar olmadan çok daha iyi olabilir.</span><span class="sxs-lookup"><span data-stu-id="464e3-117">Your performance can be much better without recursive calls.</span></span>

 <span data-ttu-id="464e3-118">**Karşılıklı özyineleme**.</span><span class="sxs-lookup"><span data-stu-id="464e3-118">**Mutual Recursion**.</span></span> <span data-ttu-id="464e3-119">İki yordam de varsa, çok kötü performans veya sonsuz bir döngü gözlemleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="464e3-119">You might observe very poor performance, or even an infinite loop, if two procedures call each other.</span></span> <span data-ttu-id="464e3-120">Böyle bir tasarım, tek bir özyinelemeli yordamla aynı sorunları sunar, ancak algılaması ve hata ayıklaması zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="464e3-120">Such a design presents the same problems as a single recursive procedure, but can be harder to detect and debug.</span></span>

 <span data-ttu-id="464e3-121">**Parantez Ile çağırma**.</span><span class="sxs-lookup"><span data-stu-id="464e3-121">**Calling with Parentheses**.</span></span> <span data-ttu-id="464e3-122">Bir `Function` yordam yinelemeli olarak çağırdığında, bağımsız değişken listesi olmasa bile, parantez ile yordam adını izlemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="464e3-122">When a `Function` procedure calls itself recursively, you must follow the procedure name with parentheses, even if there is no argument list.</span></span> <span data-ttu-id="464e3-123">Aksi takdirde, işlev adı işlevin dönüş değerini temsil eden olarak alınır.</span><span class="sxs-lookup"><span data-stu-id="464e3-123">Otherwise, the function name is taken as representing the return value of the function.</span></span>

 <span data-ttu-id="464e3-124">**Test ediliyor**.</span><span class="sxs-lookup"><span data-stu-id="464e3-124">**Testing**.</span></span> <span data-ttu-id="464e3-125">Özyinelemeli bir yordam yazarsanız, her zaman sınırlandırma koşullarını karşıladığından emin olmak için bunu dikkatle sınamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="464e3-125">If you write a recursive procedure, you should test it very carefully to make sure it always meets some limiting condition.</span></span> <span data-ttu-id="464e3-126">Ayrıca çok fazla özyinelemeli çağrı olduğundan belleği tükendiğinizden emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="464e3-126">You should also ensure that you cannot run out of memory due to having too many recursive calls.</span></span>

## <a name="see-also"></a><span data-ttu-id="464e3-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="464e3-127">See also</span></span>

- <xref:System.StackOverflowException>
- [<span data-ttu-id="464e3-128">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="464e3-128">Procedures</span></span>](index.md)
- [<span data-ttu-id="464e3-129">Alt Yordamlar</span><span class="sxs-lookup"><span data-stu-id="464e3-129">Sub Procedures</span></span>](sub-procedures.md)
- [<span data-ttu-id="464e3-130">İşlev Yordamları</span><span class="sxs-lookup"><span data-stu-id="464e3-130">Function Procedures</span></span>](function-procedures.md)
- [<span data-ttu-id="464e3-131">Özellik Yordamları</span><span class="sxs-lookup"><span data-stu-id="464e3-131">Property Procedures</span></span>](property-procedures.md)
- [<span data-ttu-id="464e3-132">İşleç Yordamları</span><span class="sxs-lookup"><span data-stu-id="464e3-132">Operator Procedures</span></span>](operator-procedures.md)
- [<span data-ttu-id="464e3-133">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="464e3-133">Procedure Parameters and Arguments</span></span>](procedure-parameters-and-arguments.md)
- [<span data-ttu-id="464e3-134">Yordam Aşırı Yüklemesi</span><span class="sxs-lookup"><span data-stu-id="464e3-134">Procedure Overloading</span></span>](procedure-overloading.md)
- [<span data-ttu-id="464e3-135">Yordam Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="464e3-135">Troubleshooting Procedures</span></span>](troubleshooting-procedures.md)
- [<span data-ttu-id="464e3-136">Döngü Yapıları</span><span class="sxs-lookup"><span data-stu-id="464e3-136">Loop Structures</span></span>](../control-flow/loop-structures.md)
