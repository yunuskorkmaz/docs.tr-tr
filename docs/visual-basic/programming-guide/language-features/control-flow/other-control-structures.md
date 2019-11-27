---
title: Diğer Denetim Yapıları
ms.date: 07/20/2015
helpviewer_keywords:
- statements [Visual Basic], control flow
- control structures [Visual Basic]
ms.assetid: 24b811f7-98ba-40ec-8dd3-4d528cfa4574
ms.openlocfilehash: 758df361f421684655147ae288af3f350e53c4d7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348128"
---
# <a name="other-control-structures-visual-basic"></a><span data-ttu-id="bd51c-102">Diğer Denetim Yapıları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bd51c-102">Other Control Structures (Visual Basic)</span></span>
<span data-ttu-id="bd51c-103">Visual Basic, bir kaynağı atmayı veya bir nesne başvurusunu tekrarlamanız için gereken süreyi azaltmanızı sağlayan denetim yapıları sağlar.</span><span class="sxs-lookup"><span data-stu-id="bd51c-103">Visual Basic provides control structures that help you dispose of a resource or reduce the number of times you have to repeat an object reference.</span></span>  
  
## <a name="usingend-using-construction"></a><span data-ttu-id="bd51c-104">Kullanılıyor... Oluşturma kullanarak bitir</span><span class="sxs-lookup"><span data-stu-id="bd51c-104">Using...End Using Construction</span></span>  
 <span data-ttu-id="bd51c-105">`Using...End Using` oluşturma, SQL bağlantısı gibi bir kaynağı kullandığınız bir bildirim bloğu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bd51c-105">The `Using...End Using` construction establishes a statement block within which you make use of a resource such as a SQL connection.</span></span> <span data-ttu-id="bd51c-106">İsteğe bağlı olarak `Using` ifadesiyle kaynağı elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bd51c-106">You can optionally acquire the resource with the `Using` statement.</span></span> <span data-ttu-id="bd51c-107">`Using` bloğundan çıktığınızda, diğer kodun kullanabilmesi için kaynağın otomatik olarak ortadan kaldırmasına Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="bd51c-107">When you exit the `Using` block, Visual Basic automatically disposes of the resource so that it is available for other code to use.</span></span> <span data-ttu-id="bd51c-108">Kaynak yerel ve atılabilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bd51c-108">The resource must be local and disposable.</span></span> <span data-ttu-id="bd51c-109">Daha fazla bilgi için bkz. [using deyimleri](../../../../visual-basic/language-reference/statements/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="bd51c-109">For more information, see [Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md).</span></span>  
  
## <a name="withend-with-construction"></a><span data-ttu-id="bd51c-110">İle... Yapım Ile bitir</span><span class="sxs-lookup"><span data-stu-id="bd51c-110">With...End With Construction</span></span>  
 <span data-ttu-id="bd51c-111">`With...End With` oluşturma bir kez nesne başvurusu belirtmenizi ve sonra üyelerine erişen bir dizi deyim çalıştırmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="bd51c-111">The `With...End With` construction lets you specify an object reference once and then run a series of statements that access its members.</span></span> <span data-ttu-id="bd51c-112">Bu, kodunuzun basitleşmesini ve performansını iyileştirebildiğinden, Visual Basic kendisine erişen her bir deyimin başvurusunu yeniden oluşturmak zorunda değildir.</span><span class="sxs-lookup"><span data-stu-id="bd51c-112">This can simplify your code and improve performance because Visual Basic does not have to re-establish the reference for each statement that accesses it.</span></span> <span data-ttu-id="bd51c-113">Daha fazla bilgi için bkz [.... WITH Ifadesiyle biter](../../../../visual-basic/language-reference/statements/with-end-with-statement.md).</span><span class="sxs-lookup"><span data-stu-id="bd51c-113">For more information, see [With...End With Statement](../../../../visual-basic/language-reference/statements/with-end-with-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd51c-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bd51c-114">See also</span></span>

- [<span data-ttu-id="bd51c-115">Denetim Akışı</span><span class="sxs-lookup"><span data-stu-id="bd51c-115">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [<span data-ttu-id="bd51c-116">Karar Yapıları</span><span class="sxs-lookup"><span data-stu-id="bd51c-116">Decision Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [<span data-ttu-id="bd51c-117">Döngü Yapıları</span><span class="sxs-lookup"><span data-stu-id="bd51c-117">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="bd51c-118">İç İçe Geçmiş Denetim Yapıları</span><span class="sxs-lookup"><span data-stu-id="bd51c-118">Nested Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="bd51c-119">Using Deyimi</span><span class="sxs-lookup"><span data-stu-id="bd51c-119">Using Statement</span></span>](../../../../visual-basic/language-reference/statements/using-statement.md)
- [<span data-ttu-id="bd51c-120">With...End With Deyimi</span><span class="sxs-lookup"><span data-stu-id="bd51c-120">With...End With Statement</span></span>](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)
