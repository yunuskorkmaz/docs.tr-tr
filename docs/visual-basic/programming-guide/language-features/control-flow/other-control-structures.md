---
title: Diğer Denetim Yapıları
ms.date: 07/20/2015
helpviewer_keywords:
- statements [Visual Basic], control flow
- control structures [Visual Basic]
ms.assetid: 24b811f7-98ba-40ec-8dd3-4d528cfa4574
ms.openlocfilehash: c6d80b237c7c3512c2904547842fdeb3c69bef68
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402024"
---
# <a name="other-control-structures-visual-basic"></a><span data-ttu-id="2d9e4-102">Diğer Denetim Yapıları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2d9e4-102">Other Control Structures (Visual Basic)</span></span>
<span data-ttu-id="2d9e4-103">Visual Basic, bir kaynağı atmayı veya bir nesne başvurusunu tekrarlamanız için gereken süreyi azaltmanızı sağlayan denetim yapıları sağlar.</span><span class="sxs-lookup"><span data-stu-id="2d9e4-103">Visual Basic provides control structures that help you dispose of a resource or reduce the number of times you have to repeat an object reference.</span></span>  
  
## <a name="usingend-using-construction"></a><span data-ttu-id="2d9e4-104">Kullanılıyor... Oluşturma kullanarak bitir</span><span class="sxs-lookup"><span data-stu-id="2d9e4-104">Using...End Using Construction</span></span>  
 <span data-ttu-id="2d9e4-105">`Using...End Using`Oluşturma, SQL bağlantısı gibi bir kaynağı kullandığınız bir ifade bloğu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2d9e4-105">The `Using...End Using` construction establishes a statement block within which you make use of a resource such as a SQL connection.</span></span> <span data-ttu-id="2d9e4-106">Kaynak ile isteğe bağlı olarak kaynağı elde edebilirsiniz `Using` .</span><span class="sxs-lookup"><span data-stu-id="2d9e4-106">You can optionally acquire the resource with the `Using` statement.</span></span> <span data-ttu-id="2d9e4-107">`Using`Bloğundan çıktığınızda, diğer kodun kullanabilmesi için kaynağın otomatik olarak ortadan Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="2d9e4-107">When you exit the `Using` block, Visual Basic automatically disposes of the resource so that it is available for other code to use.</span></span> <span data-ttu-id="2d9e4-108">Kaynak yerel ve atılabilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2d9e4-108">The resource must be local and disposable.</span></span> <span data-ttu-id="2d9e4-109">Daha fazla bilgi için bkz. [using deyimleri](../../../language-reference/statements/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="2d9e4-109">For more information, see [Using Statement](../../../language-reference/statements/using-statement.md).</span></span>  
  
## <a name="withend-with-construction"></a><span data-ttu-id="2d9e4-110">İle... Yapım Ile bitir</span><span class="sxs-lookup"><span data-stu-id="2d9e4-110">With...End With Construction</span></span>  
 <span data-ttu-id="2d9e4-111">`With...End With`Oluşturma bir kez nesne başvurusu belirtmenizi ve sonra üyelerine erişen bir dizi deyim çalıştırmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="2d9e4-111">The `With...End With` construction lets you specify an object reference once and then run a series of statements that access its members.</span></span> <span data-ttu-id="2d9e4-112">Bu, kodunuzun basitleşmesini ve performansını iyileştirebildiğinden, Visual Basic kendisine erişen her bir deyimin başvurusunu yeniden oluşturmak zorunda değildir.</span><span class="sxs-lookup"><span data-stu-id="2d9e4-112">This can simplify your code and improve performance because Visual Basic does not have to re-establish the reference for each statement that accesses it.</span></span> <span data-ttu-id="2d9e4-113">Daha fazla bilgi için bkz [.... WITH Ifadesiyle biter](../../../language-reference/statements/with-end-with-statement.md).</span><span class="sxs-lookup"><span data-stu-id="2d9e4-113">For more information, see [With...End With Statement](../../../language-reference/statements/with-end-with-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d9e4-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2d9e4-114">See also</span></span>

- [<span data-ttu-id="2d9e4-115">Denetim akışı</span><span class="sxs-lookup"><span data-stu-id="2d9e4-115">Control Flow</span></span>](index.md)
- [<span data-ttu-id="2d9e4-116">Karar Yapıları</span><span class="sxs-lookup"><span data-stu-id="2d9e4-116">Decision Structures</span></span>](decision-structures.md)
- [<span data-ttu-id="2d9e4-117">Döngü Yapıları</span><span class="sxs-lookup"><span data-stu-id="2d9e4-117">Loop Structures</span></span>](loop-structures.md)
- [<span data-ttu-id="2d9e4-118">İç İçe Geçmiş Denetim Yapıları</span><span class="sxs-lookup"><span data-stu-id="2d9e4-118">Nested Control Structures</span></span>](nested-control-structures.md)
- [<span data-ttu-id="2d9e4-119">Using deyimleri</span><span class="sxs-lookup"><span data-stu-id="2d9e4-119">Using Statement</span></span>](../../../language-reference/statements/using-statement.md)
- [<span data-ttu-id="2d9e4-120">With...End With Deyimi</span><span class="sxs-lookup"><span data-stu-id="2d9e4-120">With...End With Statement</span></span>](../../../language-reference/statements/with-end-with-statement.md)
