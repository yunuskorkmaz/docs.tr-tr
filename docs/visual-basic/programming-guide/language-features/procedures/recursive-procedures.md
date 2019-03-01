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
ms.openlocfilehash: 97cceb833da0ef6f9ee4e3dab5abb1f2ba73a94e
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56969329"
---
# <a name="recursive-procedures-visual-basic"></a><span data-ttu-id="71524-102">Özyinelemeli Yordamlar (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="71524-102">Recursive Procedures (Visual Basic)</span></span>
<span data-ttu-id="71524-103">A *özyinelemeli* yordam, kendi kendini çağıran bir kullanılır.</span><span class="sxs-lookup"><span data-stu-id="71524-103">A *recursive* procedure is one that calls itself.</span></span> <span data-ttu-id="71524-104">Genel olarak, Visual Basic kod yazmak için en etkili yolu değil.</span><span class="sxs-lookup"><span data-stu-id="71524-104">In general, this is not the most effective way to write Visual Basic code.</span></span>  
  
 <span data-ttu-id="71524-105">Aşağıdaki yordam, özgün bağımsız değişkeninin faktöriyelini hesaplamak için özyineleme kullanır.</span><span class="sxs-lookup"><span data-stu-id="71524-105">The following procedure uses recursion to calculate the factorial of its original argument.</span></span>  
  
 [!code-vb[VbVbcnProcedures#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#51)]  
  
## <a name="considerations-with-recursive-procedures"></a><span data-ttu-id="71524-106">Özyinelemeli yordamlar hakkında konuları</span><span class="sxs-lookup"><span data-stu-id="71524-106">Considerations with Recursive Procedures</span></span>  
 <span data-ttu-id="71524-107">**Koşullar sınırlama**.</span><span class="sxs-lookup"><span data-stu-id="71524-107">**Limiting Conditions**.</span></span> <span data-ttu-id="71524-108">Özyineleme sonlandırabilirsiniz en az bir koşul için test etmek için bir özyinelemeli yordamı tasarlamanız gerekir ve ayrıca burada herhangi bir koşul makul bir özyinelemeli çağrıların sayısı içinde sağlanırsa durum işlemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="71524-108">You must design a recursive procedure to test for at least one condition that can terminate the recursion, and you must also handle the case where no such condition is satisfied within a reasonable number of recursive calls.</span></span> <span data-ttu-id="71524-109">Başarısız karşılanabiliyorsa en az bir koşul olmadan yordamınız sonsuz bir döngüde yürütmenin bir yüksek riskli çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="71524-109">Without at least one condition that can be met without fail, your procedure runs a high risk of executing in an infinite loop.</span></span>  
  
 <span data-ttu-id="71524-110">**Bellek kullanımı**.</span><span class="sxs-lookup"><span data-stu-id="71524-110">**Memory Usage**.</span></span> <span data-ttu-id="71524-111">Uygulamanızı yerel değişkenler için alan sınırlı bir süre vardır.</span><span class="sxs-lookup"><span data-stu-id="71524-111">Your application has a limited amount of space for local variables.</span></span> <span data-ttu-id="71524-112">Bir yordam kendisini çağıran her zaman daha bu alan yerel değişkenlerini ek kopyalarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="71524-112">Each time a procedure calls itself, it uses more of that space for additional copies of its local variables.</span></span> <span data-ttu-id="71524-113">Bu işlem süresiz olarak devam ederse, sonunda neden olan bir <xref:System.StackOverflowException> hata.</span><span class="sxs-lookup"><span data-stu-id="71524-113">If this process continues indefinitely, it eventually causes a <xref:System.StackOverflowException> error.</span></span>  
  
 <span data-ttu-id="71524-114">**Verimliliği**.</span><span class="sxs-lookup"><span data-stu-id="71524-114">**Efficiency**.</span></span> <span data-ttu-id="71524-115">Neredeyse her zaman bir döngü için özyineleme birbirinin yerine kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="71524-115">You can almost always substitute a loop for recursion.</span></span> <span data-ttu-id="71524-116">Bir döngü, ek depolama alanı'nı başlatma ve değerler döndüren argümanları başlatır, yükü yok.</span><span class="sxs-lookup"><span data-stu-id="71524-116">A loop does not have the overhead of passing arguments, initializing additional storage, and returning values.</span></span> <span data-ttu-id="71524-117">Performansınızı özyinelemeli çağrılar çok daha iyi olabilir.</span><span class="sxs-lookup"><span data-stu-id="71524-117">Your performance can be much better without recursive calls.</span></span>  
  
 <span data-ttu-id="71524-118">**Karşılıklı özyineleme**.</span><span class="sxs-lookup"><span data-stu-id="71524-118">**Mutual Recursion**.</span></span> <span data-ttu-id="71524-119">Her iki yordam çağırırsanız çok kötü performans veya hatta bir sonsuz döngüye mümkün görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="71524-119">You might observe very poor performance, or even an infinite loop, if two procedures call each other.</span></span> <span data-ttu-id="71524-120">Bu tür bir tasarım tek özyinelemeli yordamla aynı oluşturur, ancak algılama ve hata ayıklamayı daha zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="71524-120">Such a design presents the same problems as a single recursive procedure, but can be harder to detect and debug.</span></span>  
  
 <span data-ttu-id="71524-121">**Parantezler ile çağırma**.</span><span class="sxs-lookup"><span data-stu-id="71524-121">**Calling with Parentheses**.</span></span> <span data-ttu-id="71524-122">Olduğunda bir `Function` yordam çağrıları kendisini yinelemeli olarak, hiçbir bağımsız değişken listesi olsa bile, parantezli yordam adı izlemelidir.</span><span class="sxs-lookup"><span data-stu-id="71524-122">When a `Function` procedure calls itself recursively, you must follow the procedure name with parentheses, even if there is no argument list.</span></span> <span data-ttu-id="71524-123">Aksi halde, işlev adı alınmış işlevinin dönüş değerini temsil eden olarak.</span><span class="sxs-lookup"><span data-stu-id="71524-123">Otherwise, the function name is taken as representing the return value of the function.</span></span>  
  
 <span data-ttu-id="71524-124">**Test**.</span><span class="sxs-lookup"><span data-stu-id="71524-124">**Testing**.</span></span> <span data-ttu-id="71524-125">Bir özyinelemeli yordam yazarsanız, bu çok dikkatli bir şekilde her zaman bir sınırlama bazı koşullar karşıladığından emin olmak için test etmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="71524-125">If you write a recursive procedure, you should test it very carefully to make sure it always meets some limiting condition.</span></span> <span data-ttu-id="71524-126">Ayrıca, özyinelemeli çağrı sayısı çok fazla olması nedeniyle bellek yetersiz çalıştıramazsınız emin olmalısınız.</span><span class="sxs-lookup"><span data-stu-id="71524-126">You should also ensure that you cannot run out of memory due to having too many recursive calls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71524-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="71524-127">See also</span></span>
- <xref:System.StackOverflowException>
- [<span data-ttu-id="71524-128">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="71524-128">Procedures</span></span>](./index.md)
- [<span data-ttu-id="71524-129">Alt Yordamlar</span><span class="sxs-lookup"><span data-stu-id="71524-129">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="71524-130">İşlev Yordamları</span><span class="sxs-lookup"><span data-stu-id="71524-130">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="71524-131">Özellik Yordamları</span><span class="sxs-lookup"><span data-stu-id="71524-131">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="71524-132">İşleç Yordamları</span><span class="sxs-lookup"><span data-stu-id="71524-132">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="71524-133">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="71524-133">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="71524-134">Yordam Aşırı Yüklemesi</span><span class="sxs-lookup"><span data-stu-id="71524-134">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="71524-135">Yordam Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="71524-135">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="71524-136">Döngü Yapıları</span><span class="sxs-lookup"><span data-stu-id="71524-136">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
