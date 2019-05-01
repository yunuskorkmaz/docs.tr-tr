---
title: Diğer Denetim Yapıları (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- statements [Visual Basic], control flow
- control structures [Visual Basic]
ms.assetid: 24b811f7-98ba-40ec-8dd3-4d528cfa4574
ms.openlocfilehash: c42070ce2ea866e59e1b2e190f7c05e1ee7cc922
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61907848"
---
# <a name="other-control-structures-visual-basic"></a><span data-ttu-id="1d800-102">Diğer Denetim Yapıları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1d800-102">Other Control Structures (Visual Basic)</span></span>
<span data-ttu-id="1d800-103">Visual Basic yardımcı denetim yapıları bir kaynağını atma veya bir nesne başvurusu yinelemek zorunda sayısını azaltmak sağlar.</span><span class="sxs-lookup"><span data-stu-id="1d800-103">Visual Basic provides control structures that help you dispose of a resource or reduce the number of times you have to repeat an object reference.</span></span>  
  
## <a name="usingend-using-construction"></a><span data-ttu-id="1d800-104">Kullanarak... Son yapı kullanma</span><span class="sxs-lookup"><span data-stu-id="1d800-104">Using...End Using Construction</span></span>  
 <span data-ttu-id="1d800-105">`Using...End Using` Yapım kurar, içinde yaptığınız bir deyim bloğunu bir kaynağın SQL bağlantısı kullanın.</span><span class="sxs-lookup"><span data-stu-id="1d800-105">The `Using...End Using` construction establishes a statement block within which you make use of a resource such as a SQL connection.</span></span> <span data-ttu-id="1d800-106">İsteğe bağlı olarak kaynak edinebileceğinizi `Using` deyimi.</span><span class="sxs-lookup"><span data-stu-id="1d800-106">You can optionally acquire the resource with the `Using` statement.</span></span> <span data-ttu-id="1d800-107">Çıktığınızda `Using` blok, Visual Basic böylece diğer kod kullanmak kullanılabilir kaynak otomatik olarak atar.</span><span class="sxs-lookup"><span data-stu-id="1d800-107">When you exit the `Using` block, Visual Basic automatically disposes of the resource so that it is available for other code to use.</span></span> <span data-ttu-id="1d800-108">Kaynak, yerel ve atılabilir olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1d800-108">The resource must be local and disposable.</span></span> <span data-ttu-id="1d800-109">Daha fazla bilgi için [Using deyimi](../../../../visual-basic/language-reference/statements/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="1d800-109">For more information, see [Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md).</span></span>  
  
## <a name="withend-with-construction"></a><span data-ttu-id="1d800-110">İle... Yapı ile bitmelidir</span><span class="sxs-lookup"><span data-stu-id="1d800-110">With...End With Construction</span></span>  
 <span data-ttu-id="1d800-111">`With...End With` Yapım bir nesne başvurusu bir kez belirtmenize olanak sağlar ve bir dizi üyelerine erişmek deyimleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="1d800-111">The `With...End With` construction lets you specify an object reference once and then run a series of statements that access its members.</span></span> <span data-ttu-id="1d800-112">Bu, kodunuzu basitleştirerek ve Visual Basic başvurusu eriştiği her deyim için yeniden oluşturmak sahip olmadığından performansı.</span><span class="sxs-lookup"><span data-stu-id="1d800-112">This can simplify your code and improve performance because Visual Basic does not have to re-establish the reference for each statement that accesses it.</span></span> <span data-ttu-id="1d800-113">Daha fazla bilgi için [ile... End With deyimi](../../../../visual-basic/language-reference/statements/with-end-with-statement.md).</span><span class="sxs-lookup"><span data-stu-id="1d800-113">For more information, see [With...End With Statement](../../../../visual-basic/language-reference/statements/with-end-with-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d800-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1d800-114">See also</span></span>

- [<span data-ttu-id="1d800-115">Denetim Akışı</span><span class="sxs-lookup"><span data-stu-id="1d800-115">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [<span data-ttu-id="1d800-116">Karar Yapıları</span><span class="sxs-lookup"><span data-stu-id="1d800-116">Decision Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [<span data-ttu-id="1d800-117">Döngü Yapıları</span><span class="sxs-lookup"><span data-stu-id="1d800-117">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="1d800-118">İç İçe Geçmiş Denetim Yapıları</span><span class="sxs-lookup"><span data-stu-id="1d800-118">Nested Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="1d800-119">Using Deyimi</span><span class="sxs-lookup"><span data-stu-id="1d800-119">Using Statement</span></span>](../../../../visual-basic/language-reference/statements/using-statement.md)
- [<span data-ttu-id="1d800-120">With...End With Deyimi</span><span class="sxs-lookup"><span data-stu-id="1d800-120">With...End With Statement</span></span>](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)
