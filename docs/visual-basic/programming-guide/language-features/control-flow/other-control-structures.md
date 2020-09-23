---
title: Diğer Denetim Yapıları
ms.date: 07/20/2015
helpviewer_keywords:
- statements [Visual Basic], control flow
- control structures [Visual Basic]
ms.assetid: 24b811f7-98ba-40ec-8dd3-4d528cfa4574
ms.openlocfilehash: 8e7ca699e532ac7cfbe7918d850e7a28d1b27bcf
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91058618"
---
# <a name="other-control-structures-visual-basic"></a><span data-ttu-id="423c0-102">Diğer Denetim Yapıları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="423c0-102">Other Control Structures (Visual Basic)</span></span>

<span data-ttu-id="423c0-103">Visual Basic, bir kaynağı atmayı veya bir nesne başvurusunu tekrarlamanız için gereken süreyi azaltmanızı sağlayan denetim yapıları sağlar.</span><span class="sxs-lookup"><span data-stu-id="423c0-103">Visual Basic provides control structures that help you dispose of a resource or reduce the number of times you have to repeat an object reference.</span></span>  
  
## <a name="usingend-using-construction"></a><span data-ttu-id="423c0-104">Kullanılıyor... Oluşturma kullanarak bitir</span><span class="sxs-lookup"><span data-stu-id="423c0-104">Using...End Using Construction</span></span>  

 <span data-ttu-id="423c0-105">`Using...End Using`Oluşturma, SQL bağlantısı gibi bir kaynağı kullandığınız bir ifade bloğu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="423c0-105">The `Using...End Using` construction establishes a statement block within which you make use of a resource such as a SQL connection.</span></span> <span data-ttu-id="423c0-106">Kaynak ile isteğe bağlı olarak kaynağı elde edebilirsiniz `Using` .</span><span class="sxs-lookup"><span data-stu-id="423c0-106">You can optionally acquire the resource with the `Using` statement.</span></span> <span data-ttu-id="423c0-107">`Using`Bloğundan çıktığınızda, diğer kodun kullanabilmesi için kaynağın otomatik olarak ortadan Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="423c0-107">When you exit the `Using` block, Visual Basic automatically disposes of the resource so that it is available for other code to use.</span></span> <span data-ttu-id="423c0-108">Kaynak yerel ve atılabilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="423c0-108">The resource must be local and disposable.</span></span> <span data-ttu-id="423c0-109">Daha fazla bilgi için bkz. [using deyimleri](../../../language-reference/statements/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="423c0-109">For more information, see [Using Statement](../../../language-reference/statements/using-statement.md).</span></span>  
  
## <a name="withend-with-construction"></a><span data-ttu-id="423c0-110">İle... Yapım Ile bitir</span><span class="sxs-lookup"><span data-stu-id="423c0-110">With...End With Construction</span></span>  

 <span data-ttu-id="423c0-111">`With...End With`Oluşturma bir kez nesne başvurusu belirtmenizi ve sonra üyelerine erişen bir dizi deyim çalıştırmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="423c0-111">The `With...End With` construction lets you specify an object reference once and then run a series of statements that access its members.</span></span> <span data-ttu-id="423c0-112">Bu, kodunuzun basitleşmesini ve performansını iyileştirebildiğinden, Visual Basic kendisine erişen her bir deyimin başvurusunu yeniden oluşturmak zorunda değildir.</span><span class="sxs-lookup"><span data-stu-id="423c0-112">This can simplify your code and improve performance because Visual Basic does not have to re-establish the reference for each statement that accesses it.</span></span> <span data-ttu-id="423c0-113">Daha fazla bilgi için bkz [.... WITH Ifadesiyle biter](../../../language-reference/statements/with-end-with-statement.md).</span><span class="sxs-lookup"><span data-stu-id="423c0-113">For more information, see [With...End With Statement](../../../language-reference/statements/with-end-with-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="423c0-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="423c0-114">See also</span></span>

- [<span data-ttu-id="423c0-115">Denetim akışı</span><span class="sxs-lookup"><span data-stu-id="423c0-115">Control Flow</span></span>](index.md)
- [<span data-ttu-id="423c0-116">Karar Yapıları</span><span class="sxs-lookup"><span data-stu-id="423c0-116">Decision Structures</span></span>](decision-structures.md)
- [<span data-ttu-id="423c0-117">Döngü Yapıları</span><span class="sxs-lookup"><span data-stu-id="423c0-117">Loop Structures</span></span>](loop-structures.md)
- [<span data-ttu-id="423c0-118">İç İçe Geçmiş Denetim Yapıları</span><span class="sxs-lookup"><span data-stu-id="423c0-118">Nested Control Structures</span></span>](nested-control-structures.md)
- [<span data-ttu-id="423c0-119">Using deyimleri</span><span class="sxs-lookup"><span data-stu-id="423c0-119">Using Statement</span></span>](../../../language-reference/statements/using-statement.md)
- [<span data-ttu-id="423c0-120">With...End With Deyimi</span><span class="sxs-lookup"><span data-stu-id="423c0-120">With...End With Statement</span></span>](../../../language-reference/statements/with-end-with-statement.md)
