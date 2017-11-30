---
title: "Diğer Denetim Yapıları (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- statements [Visual Basic], control flow
- control structures [Visual Basic]
ms.assetid: 24b811f7-98ba-40ec-8dd3-4d528cfa4574
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 09e59d25b3b2fc89026295e8500c30dad7b75086
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="other-control-structures-visual-basic"></a><span data-ttu-id="a6fc3-102">Diğer Denetim Yapıları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a6fc3-102">Other Control Structures (Visual Basic)</span></span>
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="a6fc3-103">yardımcı denetim yapıları bir kaynağını atma veya bir nesne başvurusu yinelemek zorunda sayısını azaltmak sağlar.</span><span class="sxs-lookup"><span data-stu-id="a6fc3-103"> provides control structures that help you dispose of a resource or reduce the number of times you have to repeat an object reference.</span></span>  
  
## <a name="usingend-using-construction"></a><span data-ttu-id="a6fc3-104">Kullanarak... Son yapı kullanma</span><span class="sxs-lookup"><span data-stu-id="a6fc3-104">Using...End Using Construction</span></span>  
 <span data-ttu-id="a6fc3-105">`Using...End Using` Yapım kurar içinde yaptığınız deyimi blok SQL bağlantısı gibi bir kaynağın kullanın.</span><span class="sxs-lookup"><span data-stu-id="a6fc3-105">The `Using...End Using` construction establishes a statement block within which you make use of a resource such as a SQL connection.</span></span> <span data-ttu-id="a6fc3-106">İsteğe bağlı olarak ile kaynak elde edebilirsiniz `Using` deyimi.</span><span class="sxs-lookup"><span data-stu-id="a6fc3-106">You can optionally acquire the resource with the `Using` statement.</span></span> <span data-ttu-id="a6fc3-107">Çıktığınızda `Using` bloğu [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] böylece diğer kod kullanmak kullanılabilir kaynak otomatik olarak siler.</span><span class="sxs-lookup"><span data-stu-id="a6fc3-107">When you exit the `Using` block, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] automatically disposes of the resource so that it is available for other code to use.</span></span> <span data-ttu-id="a6fc3-108">Kaynak, yerel ve atılabilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a6fc3-108">The resource must be local and disposable.</span></span> <span data-ttu-id="a6fc3-109">Daha fazla bilgi için bkz: [kullanarak deyimi](../../../../visual-basic/language-reference/statements/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a6fc3-109">For more information, see [Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md).</span></span>  
  
## <a name="withend-with-construction"></a><span data-ttu-id="a6fc3-110">İle... Yapı ile bitmelidir</span><span class="sxs-lookup"><span data-stu-id="a6fc3-110">With...End With Construction</span></span>  
 <span data-ttu-id="a6fc3-111">`With...End With` Yapım nesne başvurusu bir kez belirtmenize olanak sağlar ve bir dizi üyelerine erişim deyimi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a6fc3-111">The `With...End With` construction lets you specify an object reference once and then run a series of statements that access its members.</span></span> <span data-ttu-id="a6fc3-112">Bu, kodunuzu basitleştirerek olduğundan performansı [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] eriştiği her deyim için başvuru yeniden oluşturmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="a6fc3-112">This can simplify your code and improve performance because [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] does not have to re-establish the reference for each statement that accesses it.</span></span> <span data-ttu-id="a6fc3-113">Daha fazla bilgi için bkz: [ile... End With deyimi](../../../../visual-basic/language-reference/statements/with-end-with-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a6fc3-113">For more information, see [With...End With Statement](../../../../visual-basic/language-reference/statements/with-end-with-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6fc3-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a6fc3-114">See Also</span></span>  
 [<span data-ttu-id="a6fc3-115">Denetim akışı</span><span class="sxs-lookup"><span data-stu-id="a6fc3-115">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)  
 [<span data-ttu-id="a6fc3-116">Karar yapıları</span><span class="sxs-lookup"><span data-stu-id="a6fc3-116">Decision Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)  
 [<span data-ttu-id="a6fc3-117">Döngü yapıları</span><span class="sxs-lookup"><span data-stu-id="a6fc3-117">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [<span data-ttu-id="a6fc3-118">İç içe geçmiş denetim yapıları</span><span class="sxs-lookup"><span data-stu-id="a6fc3-118">Nested Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [<span data-ttu-id="a6fc3-119">Using deyimi</span><span class="sxs-lookup"><span data-stu-id="a6fc3-119">Using Statement</span></span>](../../../../visual-basic/language-reference/statements/using-statement.md)  
 [<span data-ttu-id="a6fc3-120">İle... End With deyimi</span><span class="sxs-lookup"><span data-stu-id="a6fc3-120">With...End With Statement</span></span>](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)
