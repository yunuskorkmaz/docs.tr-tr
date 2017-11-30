---
title: "Özyinelemeli Yordamlar (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], that call themselves
- procedures [Visual Basic], recursive
- procedures [Visual Basic], calling
- recursive procedures
- functions [Visual Basic], calling recursively
- recursion
ms.assetid: ba1d3962-b4c3-48d3-875e-96fdb4198327
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 444eeaf043cf3710c5154fd7e8577590e3ce7d1e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="recursive-procedures-visual-basic"></a><span data-ttu-id="45a63-102">Özyinelemeli Yordamlar (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="45a63-102">Recursive Procedures (Visual Basic)</span></span>
<span data-ttu-id="45a63-103">A *özyinelemeli* yordam kendisini çağıran bir kullanılır.</span><span class="sxs-lookup"><span data-stu-id="45a63-103">A *recursive* procedure is one that calls itself.</span></span> <span data-ttu-id="45a63-104">Genel olarak, bu yazmak için en etkili şekilde değil [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kodu.</span><span class="sxs-lookup"><span data-stu-id="45a63-104">In general, this is not the most effective way to write [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] code.</span></span>  
  
 <span data-ttu-id="45a63-105">Aşağıdaki yordamda özyineleme faktöriyelini özgün bağımsız değişkeninin değerini hesaplamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="45a63-105">The following procedure uses recursion to calculate the factorial of its original argument.</span></span>  
  
 [!code-vb[VbVbcnProcedures#51](./codesnippet/VisualBasic/recursive-procedures_1.vb)]  
  
## <a name="considerations-with-recursive-procedures"></a><span data-ttu-id="45a63-106">Özyinelemeli yordamlar ile ilgili önemli noktalar</span><span class="sxs-lookup"><span data-stu-id="45a63-106">Considerations with Recursive Procedures</span></span>  
 <span data-ttu-id="45a63-107">**Koşullar sınırlama**.</span><span class="sxs-lookup"><span data-stu-id="45a63-107">**Limiting Conditions**.</span></span> <span data-ttu-id="45a63-108">Özyineleme sonlandırabilir en az bir koşul için test etmek için bir özyinelemeli yordamı tasarlamanız gerekir ve bu tür bir koşul özyinelemeli çağrılara makul bir dizi içinde nerede sağlanırsa durum işlemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="45a63-108">You must design a recursive procedure to test for at least one condition that can terminate the recursion, and you must also handle the case where no such condition is satisfied within a reasonable number of recursive calls.</span></span> <span data-ttu-id="45a63-109">Başarısız karşılanabilir en az bir koşul olmadan yordamınız sonsuz bir döngüde yürütmenin yüksek riskli çalışır.</span><span class="sxs-lookup"><span data-stu-id="45a63-109">Without at least one condition that can be met without fail, your procedure runs a high risk of executing in an infinite loop.</span></span>  
  
 <span data-ttu-id="45a63-110">**Bellek kullanımı**.</span><span class="sxs-lookup"><span data-stu-id="45a63-110">**Memory Usage**.</span></span> <span data-ttu-id="45a63-111">Uygulamanızı yerel değişkenler için alan sınırlı miktarda sahiptir.</span><span class="sxs-lookup"><span data-stu-id="45a63-111">Your application has a limited amount of space for local variables.</span></span> <span data-ttu-id="45a63-112">Kendisini bir yordam çağrıları her zaman bu alanı daha fazla yerel değişkenlerini ek kopyalarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="45a63-112">Each time a procedure calls itself, it uses more of that space for additional copies of its local variables.</span></span> <span data-ttu-id="45a63-113">Bu işlem belirsiz bir süre devam ederse, sonunda neden olan bir <xref:System.StackOverflowException> hata.</span><span class="sxs-lookup"><span data-stu-id="45a63-113">If this process continues indefinitely, it eventually causes a <xref:System.StackOverflowException> error.</span></span>  
  
 <span data-ttu-id="45a63-114">**Verimlilik**.</span><span class="sxs-lookup"><span data-stu-id="45a63-114">**Efficiency**.</span></span> <span data-ttu-id="45a63-115">Özyineleme için bir döngü neredeyse her zaman değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="45a63-115">You can almost always substitute a loop for recursion.</span></span> <span data-ttu-id="45a63-116">Döngü ek depolama alanı başlatma ve dönüş değerleri argümanları başlatır, yükü yok.</span><span class="sxs-lookup"><span data-stu-id="45a63-116">A loop does not have the overhead of passing arguments, initializing additional storage, and returning values.</span></span> <span data-ttu-id="45a63-117">Performansınızı özyinelemeli çağrılara daha iyi olabilir.</span><span class="sxs-lookup"><span data-stu-id="45a63-117">Your performance can be much better without recursive calls.</span></span>  
  
 <span data-ttu-id="45a63-118">**Karşılıklı özyineleme**.</span><span class="sxs-lookup"><span data-stu-id="45a63-118">**Mutual Recursion**.</span></span> <span data-ttu-id="45a63-119">İki yordam birbirine çağırırsanız çok düşük performans ya da sonsuz bir döngüde bile, görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="45a63-119">You might observe very poor performance, or even an infinite loop, if two procedures call each other.</span></span> <span data-ttu-id="45a63-120">Bu tür bir tasarım tek özyinelemeli yordamla aynı sorunları gösterir, ancak algılamak ve hata ayıklama için daha zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="45a63-120">Such a design presents the same problems as a single recursive procedure, but can be harder to detect and debug.</span></span>  
  
 <span data-ttu-id="45a63-121">**Parantezler ile çağırma**.</span><span class="sxs-lookup"><span data-stu-id="45a63-121">**Calling with Parentheses**.</span></span> <span data-ttu-id="45a63-122">Zaman bir `Function` yordam çağrıları kendisini yinelemeli olarak, hiçbir bağımsız değişken listesi olsa bile parantez yordamı adıyla izlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="45a63-122">When a `Function` procedure calls itself recursively, you must follow the procedure name with parentheses, even if there is no argument list.</span></span> <span data-ttu-id="45a63-123">Aksi takdirde, işlev adı geçen işlevi dönüş değerini temsil eden olarak.</span><span class="sxs-lookup"><span data-stu-id="45a63-123">Otherwise, the function name is taken as representing the return value of the function.</span></span>  
  
 <span data-ttu-id="45a63-124">**Sınama**.</span><span class="sxs-lookup"><span data-stu-id="45a63-124">**Testing**.</span></span> <span data-ttu-id="45a63-125">Bir özyinelemeli yordamı yazarsanız, çok dikkatli bazı sınırlama koşul her zaman karşıladığından emin olmak için test.</span><span class="sxs-lookup"><span data-stu-id="45a63-125">If you write a recursive procedure, you should test it very carefully to make sure it always meets some limiting condition.</span></span> <span data-ttu-id="45a63-126">Ayrıca, çok fazla özyinelemeli çağrılara olması nedeniyle bellek yetersiz çalıştıramazsınız de emin olmalısınız.</span><span class="sxs-lookup"><span data-stu-id="45a63-126">You should also ensure that you cannot run out of memory due to having too many recursive calls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45a63-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="45a63-127">See Also</span></span>  
 <xref:System.StackOverflowException>  
 [<span data-ttu-id="45a63-128">Yordamları</span><span class="sxs-lookup"><span data-stu-id="45a63-128">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="45a63-129">Alt yordamlar</span><span class="sxs-lookup"><span data-stu-id="45a63-129">Sub Procedures</span></span>](./sub-procedures.md)  
 [<span data-ttu-id="45a63-130">İşlev yordamları</span><span class="sxs-lookup"><span data-stu-id="45a63-130">Function Procedures</span></span>](./function-procedures.md)  
 [<span data-ttu-id="45a63-131">Özellik yordamları</span><span class="sxs-lookup"><span data-stu-id="45a63-131">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="45a63-132">İşleç yordamları</span><span class="sxs-lookup"><span data-stu-id="45a63-132">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="45a63-133">Parametreler ve bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="45a63-133">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="45a63-134">Yordam aşırı yüklemesi</span><span class="sxs-lookup"><span data-stu-id="45a63-134">Procedure Overloading</span></span>](./procedure-overloading.md)  
 [<span data-ttu-id="45a63-135">Sorun giderme yordamları</span><span class="sxs-lookup"><span data-stu-id="45a63-135">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)  
 [<span data-ttu-id="45a63-136">Döngü yapıları</span><span class="sxs-lookup"><span data-stu-id="45a63-136">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [<span data-ttu-id="45a63-137">Özel durum sorunlarını giderme: System.StackOverflowException</span><span class="sxs-lookup"><span data-stu-id="45a63-137">Troubleshooting Exceptions: System.StackOverflowException</span></span>](http://msdn.microsoft.com/library/51b71217-c507-4f5b-bc35-0236180d7968)
