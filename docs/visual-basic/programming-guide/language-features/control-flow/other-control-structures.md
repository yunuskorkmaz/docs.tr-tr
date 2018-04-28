---
title: Diğer Denetim Yapıları (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- statements [Visual Basic], control flow
- control structures [Visual Basic]
ms.assetid: 24b811f7-98ba-40ec-8dd3-4d528cfa4574
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4e1ea44cf2f0405dc55f8df60fb842691e50a9a0
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="other-control-structures-visual-basic"></a><span data-ttu-id="2dccd-102">Diğer Denetim Yapıları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2dccd-102">Other Control Structures (Visual Basic)</span></span>
<span data-ttu-id="2dccd-103">Visual Basic yardımcı denetim yapıları bir kaynağını atma veya bir nesne başvurusu yinelemek zorunda sayısını azaltmak sağlar.</span><span class="sxs-lookup"><span data-stu-id="2dccd-103">Visual Basic provides control structures that help you dispose of a resource or reduce the number of times you have to repeat an object reference.</span></span>  
  
## <a name="usingend-using-construction"></a><span data-ttu-id="2dccd-104">Kullanarak... Son yapı kullanma</span><span class="sxs-lookup"><span data-stu-id="2dccd-104">Using...End Using Construction</span></span>  
 <span data-ttu-id="2dccd-105">`Using...End Using` Yapım kurar içinde yaptığınız deyimi blok SQL bağlantısı gibi bir kaynağın kullanın.</span><span class="sxs-lookup"><span data-stu-id="2dccd-105">The `Using...End Using` construction establishes a statement block within which you make use of a resource such as a SQL connection.</span></span> <span data-ttu-id="2dccd-106">İsteğe bağlı olarak ile kaynak elde edebilirsiniz `Using` deyimi.</span><span class="sxs-lookup"><span data-stu-id="2dccd-106">You can optionally acquire the resource with the `Using` statement.</span></span> <span data-ttu-id="2dccd-107">Çıktığınızda `Using` bloğu, Visual Basic böylece diğer kod kullanmak kullanılabilir kaynak otomatik olarak siler.</span><span class="sxs-lookup"><span data-stu-id="2dccd-107">When you exit the `Using` block, Visual Basic automatically disposes of the resource so that it is available for other code to use.</span></span> <span data-ttu-id="2dccd-108">Kaynak, yerel ve atılabilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2dccd-108">The resource must be local and disposable.</span></span> <span data-ttu-id="2dccd-109">Daha fazla bilgi için bkz: [kullanarak deyimi](../../../../visual-basic/language-reference/statements/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="2dccd-109">For more information, see [Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md).</span></span>  
  
## <a name="withend-with-construction"></a><span data-ttu-id="2dccd-110">İle... Yapı ile bitmelidir</span><span class="sxs-lookup"><span data-stu-id="2dccd-110">With...End With Construction</span></span>  
 <span data-ttu-id="2dccd-111">`With...End With` Yapım nesne başvurusu bir kez belirtmenize olanak sağlar ve bir dizi üyelerine erişim deyimi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="2dccd-111">The `With...End With` construction lets you specify an object reference once and then run a series of statements that access its members.</span></span> <span data-ttu-id="2dccd-112">Bu, kodunuzu basitleştiren ve Visual Basic başvurusu eriştiği her deyim için yeniden oluşturmak sahip olmadığından performansı.</span><span class="sxs-lookup"><span data-stu-id="2dccd-112">This can simplify your code and improve performance because Visual Basic does not have to re-establish the reference for each statement that accesses it.</span></span> <span data-ttu-id="2dccd-113">Daha fazla bilgi için bkz: [ile... End With deyimi](../../../../visual-basic/language-reference/statements/with-end-with-statement.md).</span><span class="sxs-lookup"><span data-stu-id="2dccd-113">For more information, see [With...End With Statement](../../../../visual-basic/language-reference/statements/with-end-with-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2dccd-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2dccd-114">See Also</span></span>  
 [<span data-ttu-id="2dccd-115">Denetim Akışı</span><span class="sxs-lookup"><span data-stu-id="2dccd-115">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)  
 [<span data-ttu-id="2dccd-116">Karar Yapıları</span><span class="sxs-lookup"><span data-stu-id="2dccd-116">Decision Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)  
 [<span data-ttu-id="2dccd-117">Döngü Yapıları</span><span class="sxs-lookup"><span data-stu-id="2dccd-117">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [<span data-ttu-id="2dccd-118">İç İçe Geçmiş Denetim Yapıları</span><span class="sxs-lookup"><span data-stu-id="2dccd-118">Nested Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [<span data-ttu-id="2dccd-119">Using Deyimi</span><span class="sxs-lookup"><span data-stu-id="2dccd-119">Using Statement</span></span>](../../../../visual-basic/language-reference/statements/using-statement.md)  
 [<span data-ttu-id="2dccd-120">With...End With Deyimi</span><span class="sxs-lookup"><span data-stu-id="2dccd-120">With...End With Statement</span></span>](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)
