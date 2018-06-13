---
title: 'Nasıl yapılır: Deyimler (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- colons (:)
- statements [Visual Basic], labels
- ': separator character'
- Visual Basic code, labeling statements
ms.assetid: 38f1ff43-2054-42cb-963b-1998e60c6ed4
ms.openlocfilehash: df368bdba73ca35dd70bdd2f4e88cc10af894b5a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650130"
---
# <a name="how-to-label-statements-visual-basic"></a><span data-ttu-id="6c791-102">Nasıl yapılır: Deyimler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6c791-102">How to: Label Statements (Visual Basic)</span></span>
<span data-ttu-id="6c791-103">Deyim blokları virgüllerle ayrılmış kod satırlarını oluşur.</span><span class="sxs-lookup"><span data-stu-id="6c791-103">Statement blocks are made up of lines of code delimited by colons.</span></span> <span data-ttu-id="6c791-104">Öncesinde bir tanımlayıcı string veya tamsayı kod satırlarını olmasını denirse *etiketli*.</span><span class="sxs-lookup"><span data-stu-id="6c791-104">Lines of code preceded by an identifying string or integer are said to be *labeled*.</span></span> <span data-ttu-id="6c791-105">Deyimi etiketleri kullanılmak üzere ifadelerle gibi tanımlamak için kod satırı işaretlemek için kullanılan `On Error Goto`.</span><span class="sxs-lookup"><span data-stu-id="6c791-105">Statement labels are used to mark a line of code to identify it for use with statements such as `On Error Goto`.</span></span>  
  
 <span data-ttu-id="6c791-106">Etiketleri ya da geçerli Visual Basic tanımlayıcıları olabilir — programlama öğeleri tanımlamak olanlar gibi — veya tamsayı değişmez değerleri.</span><span class="sxs-lookup"><span data-stu-id="6c791-106">Labels may be either valid Visual Basic identifiers—such as those that identify programming elements—or integer literals.</span></span> <span data-ttu-id="6c791-107">Bir etiket bir kaynak kod satırı başında görünmesi gerekir ve olup, aynı satırda bir deyimi tarafından izlenir bakılmaksızın bir iki nokta gelmelidir.</span><span class="sxs-lookup"><span data-stu-id="6c791-107">A label must appear at the beginning of a line of source code and must be followed by a colon, regardless of whether it is followed by a statement on the same line.</span></span>  
  
 <span data-ttu-id="6c791-108">Derleyici satırının başına, önceden tanımlanan bir tanımlayıcı eşleşip eşleşmediğini kontrol ederek etiketleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6c791-108">The compiler identifies labels by checking whether the beginning of the line matches any already-defined identifier.</span></span> <span data-ttu-id="6c791-109">Yoksa, derleyici bir etiket olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="6c791-109">If it does not, the compiler assumes it is a label.</span></span>  
  
 <span data-ttu-id="6c791-110">Etiketler kendi bildirimi alanınız ve diğer tanımlayıcıları ile engel olmaz.</span><span class="sxs-lookup"><span data-stu-id="6c791-110">Labels have their own declaration space and do not interfere with other identifiers.</span></span> <span data-ttu-id="6c791-111">Bir etiketin yönteminin gövdesi kapsamıdır.</span><span class="sxs-lookup"><span data-stu-id="6c791-111">A label's scope is the body of the method.</span></span> <span data-ttu-id="6c791-112">Etiket bildirimi herhangi bir belirsiz durumda önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="6c791-112">Label declaration takes precedence in any ambiguous situation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6c791-113">Etiketleri yalnızca executable deyimleri yöntemleri içinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6c791-113">Labels can be used only on executable statements inside methods.</span></span>  
  
### <a name="to-label-a-line-of-code"></a><span data-ttu-id="6c791-114">Etiket bir kod satırı</span><span class="sxs-lookup"><span data-stu-id="6c791-114">To label a line of code</span></span>  
  
-   <span data-ttu-id="6c791-115">Kaynak kodu satır başında, iki nokta arkasından bir tanımlayıcı yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="6c791-115">Place an identifier, followed by a colon, at the beginning of the line of source code.</span></span>  
  
     <span data-ttu-id="6c791-116">Örneğin, aşağıdaki kod satırlarını ile etiketlenir `Jump` ve `120`sırasıyla:</span><span class="sxs-lookup"><span data-stu-id="6c791-116">For example, the following lines of code are labeled with `Jump` and `120`, respectively:</span></span>  
  
     [!code-vb[VbVbalrStatements#708](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/how-to-label-statements_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="6c791-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6c791-117">See Also</span></span>  
 [<span data-ttu-id="6c791-118">Deyimler</span><span class="sxs-lookup"><span data-stu-id="6c791-118">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)  
 [<span data-ttu-id="6c791-119">Bildirilen Öğe Adları</span><span class="sxs-lookup"><span data-stu-id="6c791-119">Declared Element Names</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [<span data-ttu-id="6c791-120">Program Yapısı ve Kod Kuralları</span><span class="sxs-lookup"><span data-stu-id="6c791-120">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
