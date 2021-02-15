---
description: 'Daha fazla bilgi edinin: diğer denetim yapıları (Visual Basic)'
title: Diğer Denetim Yapıları
ms.date: 07/20/2015
helpviewer_keywords:
- statements [Visual Basic], control flow
- control structures [Visual Basic]
ms.assetid: 24b811f7-98ba-40ec-8dd3-4d528cfa4574
ms.openlocfilehash: 39654b8c780369eeea043087c8a04e2ba1f928c2
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100473582"
---
# <a name="other-control-structures-visual-basic"></a><span data-ttu-id="08bef-103">Diğer Denetim Yapıları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="08bef-103">Other Control Structures (Visual Basic)</span></span>

<span data-ttu-id="08bef-104">Visual Basic, bir kaynağı atmayı veya bir nesne başvurusunu tekrarlamanız için gereken süreyi azaltmanızı sağlayan denetim yapıları sağlar.</span><span class="sxs-lookup"><span data-stu-id="08bef-104">Visual Basic provides control structures that help you dispose of a resource or reduce the number of times you have to repeat an object reference.</span></span>  
  
## <a name="usingend-using-construction"></a><span data-ttu-id="08bef-105">Kullanılıyor... Oluşturma kullanarak bitir</span><span class="sxs-lookup"><span data-stu-id="08bef-105">Using...End Using Construction</span></span>  

 <span data-ttu-id="08bef-106">`Using...End Using`Oluşturma, SQL bağlantısı gibi bir kaynağı kullandığınız bir ifade bloğu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="08bef-106">The `Using...End Using` construction establishes a statement block within which you make use of a resource such as a SQL connection.</span></span> <span data-ttu-id="08bef-107">Kaynak ile isteğe bağlı olarak kaynağı elde edebilirsiniz `Using` .</span><span class="sxs-lookup"><span data-stu-id="08bef-107">You can optionally acquire the resource with the `Using` statement.</span></span> <span data-ttu-id="08bef-108">`Using`Bloğundan çıktığınızda, diğer kodun kullanabilmesi için kaynağın otomatik olarak ortadan Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="08bef-108">When you exit the `Using` block, Visual Basic automatically disposes of the resource so that it is available for other code to use.</span></span> <span data-ttu-id="08bef-109">Kaynak yerel ve atılabilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="08bef-109">The resource must be local and disposable.</span></span> <span data-ttu-id="08bef-110">Daha fazla bilgi için bkz. [using deyimleri](../../../language-reference/statements/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="08bef-110">For more information, see [Using Statement](../../../language-reference/statements/using-statement.md).</span></span>  
  
## <a name="withend-with-construction"></a><span data-ttu-id="08bef-111">İle... Yapım Ile bitir</span><span class="sxs-lookup"><span data-stu-id="08bef-111">With...End With Construction</span></span>  

 <span data-ttu-id="08bef-112">`With...End With`Oluşturma bir kez nesne başvurusu belirtmenizi ve sonra üyelerine erişen bir dizi deyim çalıştırmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="08bef-112">The `With...End With` construction lets you specify an object reference once and then run a series of statements that access its members.</span></span> <span data-ttu-id="08bef-113">Bu, kodunuzun basitleşmesini ve performansını iyileştirebildiğinden, Visual Basic kendisine erişen her bir deyimin başvurusunu yeniden oluşturmak zorunda değildir.</span><span class="sxs-lookup"><span data-stu-id="08bef-113">This can simplify your code and improve performance because Visual Basic does not have to re-establish the reference for each statement that accesses it.</span></span> <span data-ttu-id="08bef-114">Daha fazla bilgi için bkz [.... WITH Ifadesiyle biter](../../../language-reference/statements/with-end-with-statement.md).</span><span class="sxs-lookup"><span data-stu-id="08bef-114">For more information, see [With...End With Statement](../../../language-reference/statements/with-end-with-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08bef-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="08bef-115">See also</span></span>

- [<span data-ttu-id="08bef-116">Denetim akışı</span><span class="sxs-lookup"><span data-stu-id="08bef-116">Control Flow</span></span>](index.md)
- [<span data-ttu-id="08bef-117">Karar Yapıları</span><span class="sxs-lookup"><span data-stu-id="08bef-117">Decision Structures</span></span>](decision-structures.md)
- [<span data-ttu-id="08bef-118">Döngü Yapıları</span><span class="sxs-lookup"><span data-stu-id="08bef-118">Loop Structures</span></span>](loop-structures.md)
- [<span data-ttu-id="08bef-119">İç İçe Geçmiş Denetim Yapıları</span><span class="sxs-lookup"><span data-stu-id="08bef-119">Nested Control Structures</span></span>](nested-control-structures.md)
- [<span data-ttu-id="08bef-120">Using deyimleri</span><span class="sxs-lookup"><span data-stu-id="08bef-120">Using Statement</span></span>](../../../language-reference/statements/using-statement.md)
- [<span data-ttu-id="08bef-121">With...End With Deyimi</span><span class="sxs-lookup"><span data-stu-id="08bef-121">With...End With Statement</span></span>](../../../language-reference/statements/with-end-with-statement.md)
