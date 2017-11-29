---
title: "Nasıl yapılır: Deyimler (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- colons (:)
- statements [Visual Basic], labels
- ': separator character'
- Visual Basic code, labeling statements
ms.assetid: 38f1ff43-2054-42cb-963b-1998e60c6ed4
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 190ec9fc2392e6e4adae9b2b612edd69d73cedfd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-label-statements-visual-basic"></a><span data-ttu-id="3ce3d-102">Nasıl yapılır: Deyimler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3ce3d-102">How to: Label Statements (Visual Basic)</span></span>
<span data-ttu-id="3ce3d-103">Deyim blokları virgüllerle ayrılmış kod satırlarını oluşur.</span><span class="sxs-lookup"><span data-stu-id="3ce3d-103">Statement blocks are made up of lines of code delimited by colons.</span></span> <span data-ttu-id="3ce3d-104">Öncesinde bir tanımlayıcı string veya tamsayı kod satırlarını olmasını denirse *etiketli*.</span><span class="sxs-lookup"><span data-stu-id="3ce3d-104">Lines of code preceded by an identifying string or integer are said to be *labeled*.</span></span> <span data-ttu-id="3ce3d-105">Deyimi etiketleri kullanılmak üzere ifadelerle gibi tanımlamak için kod satırı işaretlemek için kullanılan `On Error Goto`.</span><span class="sxs-lookup"><span data-stu-id="3ce3d-105">Statement labels are used to mark a line of code to identify it for use with statements such as `On Error Goto`.</span></span>  
  
 <span data-ttu-id="3ce3d-106">Etiketleri ya da geçerli Visual Basic tanımlayıcıları olabilir — programlama öğeleri tanımlamak olanlar gibi — veya tamsayı değişmez değerleri.</span><span class="sxs-lookup"><span data-stu-id="3ce3d-106">Labels may be either valid Visual Basic identifiers—such as those that identify programming elements—or integer literals.</span></span> <span data-ttu-id="3ce3d-107">Bir etiket bir kaynak kod satırı başında görünmesi gerekir ve olup, aynı satırda bir deyimi tarafından izlenir bakılmaksızın bir iki nokta gelmelidir.</span><span class="sxs-lookup"><span data-stu-id="3ce3d-107">A label must appear at the beginning of a line of source code and must be followed by a colon, regardless of whether it is followed by a statement on the same line.</span></span>  
  
 <span data-ttu-id="3ce3d-108">Derleyici satırının başına, önceden tanımlanan bir tanımlayıcı eşleşip eşleşmediğini kontrol ederek etiketleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3ce3d-108">The compiler identifies labels by checking whether the beginning of the line matches any already-defined identifier.</span></span> <span data-ttu-id="3ce3d-109">Yoksa, derleyici bir etiket olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="3ce3d-109">If it does not, the compiler assumes it is a label.</span></span>  
  
 <span data-ttu-id="3ce3d-110">Etiketler kendi bildirimi alanınız ve diğer tanımlayıcıları ile engel olmaz.</span><span class="sxs-lookup"><span data-stu-id="3ce3d-110">Labels have their own declaration space and do not interfere with other identifiers.</span></span> <span data-ttu-id="3ce3d-111">Bir etiketin yönteminin gövdesi kapsamıdır.</span><span class="sxs-lookup"><span data-stu-id="3ce3d-111">A label's scope is the body of the method.</span></span> <span data-ttu-id="3ce3d-112">Etiket bildirimi herhangi bir belirsiz durumda önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="3ce3d-112">Label declaration takes precedence in any ambiguous situation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3ce3d-113">Etiketleri yalnızca executable deyimleri yöntemleri içinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3ce3d-113">Labels can be used only on executable statements inside methods.</span></span>  
  
### <a name="to-label-a-line-of-code"></a><span data-ttu-id="3ce3d-114">Etiket bir kod satırı</span><span class="sxs-lookup"><span data-stu-id="3ce3d-114">To label a line of code</span></span>  
  
-   <span data-ttu-id="3ce3d-115">Kaynak kodu satır başında, iki nokta arkasından bir tanımlayıcı yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="3ce3d-115">Place an identifier, followed by a colon, at the beginning of the line of source code.</span></span>  
  
     <span data-ttu-id="3ce3d-116">Örneğin, aşağıdaki kod satırlarını ile etiketlenir `Jump` ve `120`sırasıyla:</span><span class="sxs-lookup"><span data-stu-id="3ce3d-116">For example, the following lines of code are labeled with `Jump` and `120`, respectively:</span></span>  
  
     [!code-vb[VbVbalrStatements#708](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/how-to-label-statements_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="3ce3d-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3ce3d-117">See Also</span></span>  
 [<span data-ttu-id="3ce3d-118">Deyimleri</span><span class="sxs-lookup"><span data-stu-id="3ce3d-118">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)  
 [<span data-ttu-id="3ce3d-119">Bildirilen öğe adları</span><span class="sxs-lookup"><span data-stu-id="3ce3d-119">Declared Element Names</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [<span data-ttu-id="3ce3d-120">Program yapısı ve kod kuralları</span><span class="sxs-lookup"><span data-stu-id="3ce3d-120">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
