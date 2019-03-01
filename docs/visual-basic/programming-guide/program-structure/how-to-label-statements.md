---
title: 'Nasıl yapılır: Etiket ifadeleri (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- colons (:)
- statements [Visual Basic], labels
- ': separator character'
- Visual Basic code, labeling statements
ms.assetid: 38f1ff43-2054-42cb-963b-1998e60c6ed4
ms.openlocfilehash: 2f6f0362fcec170e677d153ad9f936a5c2e55ad7
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56981211"
---
# <a name="how-to-label-statements-visual-basic"></a><span data-ttu-id="87c3a-102">Nasıl yapılır: Etiket ifadeleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="87c3a-102">How to: Label Statements (Visual Basic)</span></span>
<span data-ttu-id="87c3a-103">Deyim blokları virgüllerle ayrılmış kod satırlarının oluşur.</span><span class="sxs-lookup"><span data-stu-id="87c3a-103">Statement blocks are made up of lines of code delimited by colons.</span></span> <span data-ttu-id="87c3a-104">Öncesinde tanımlayan bir dize veya tamsayı kod satırlarını söylenebilir olmasını *etiketli*.</span><span class="sxs-lookup"><span data-stu-id="87c3a-104">Lines of code preceded by an identifying string or integer are said to be *labeled*.</span></span> <span data-ttu-id="87c3a-105">Deyim etiketleri kullanmak için ifadelerle gibi tanımlamak için kod satırını işaretlemek için kullanılan `On Error Goto`.</span><span class="sxs-lookup"><span data-stu-id="87c3a-105">Statement labels are used to mark a line of code to identify it for use with statements such as `On Error Goto`.</span></span>  
  
 <span data-ttu-id="87c3a-106">Etiketler, geçerli ya da Visual Basic tanımlayıcıları olabilir — programlama öğeleri tanımlayan olanlar gibi — veya tamsayı sabit değerlerinde.</span><span class="sxs-lookup"><span data-stu-id="87c3a-106">Labels may be either valid Visual Basic identifiers—such as those that identify programming elements—or integer literals.</span></span> <span data-ttu-id="87c3a-107">Bir etiket, kaynak kod satırının başında yer almalıdır ve, aynı satırdaki bir deyimi tarafından olup izlenir bakılmaksızın, bir virgül gelmelidir.</span><span class="sxs-lookup"><span data-stu-id="87c3a-107">A label must appear at the beginning of a line of source code and must be followed by a colon, regardless of whether it is followed by a statement on the same line.</span></span>  
  
 <span data-ttu-id="87c3a-108">Derleyici, satırın başına zaten tanımlı herhangi bir tanımlayıcı ile eşleşip eşleşmediğini kontrol ederek etiketleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="87c3a-108">The compiler identifies labels by checking whether the beginning of the line matches any already-defined identifier.</span></span> <span data-ttu-id="87c3a-109">Kullanmıyorsa, derleyici bir etiket olduğu varsayılır.</span><span class="sxs-lookup"><span data-stu-id="87c3a-109">If it does not, the compiler assumes it is a label.</span></span>  
  
 <span data-ttu-id="87c3a-110">Etiketler, kendi bildirim alanına sahip ve diğer tanımlayıcıları ile müdahale etmez.</span><span class="sxs-lookup"><span data-stu-id="87c3a-110">Labels have their own declaration space and do not interfere with other identifiers.</span></span> <span data-ttu-id="87c3a-111">Bir etiketin, yöntemin gövdesi kapsamıdır.</span><span class="sxs-lookup"><span data-stu-id="87c3a-111">A label's scope is the body of the method.</span></span> <span data-ttu-id="87c3a-112">Etiket bildirimi herhangi bir belirsiz durumda daha önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="87c3a-112">Label declaration takes precedence in any ambiguous situation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="87c3a-113">Etiketleri yalnızca yürütülebilir deyimleri yöntem içinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="87c3a-113">Labels can be used only on executable statements inside methods.</span></span>  
  
### <a name="to-label-a-line-of-code"></a><span data-ttu-id="87c3a-114">Etiket için bir kod satırı</span><span class="sxs-lookup"><span data-stu-id="87c3a-114">To label a line of code</span></span>  
  
-   <span data-ttu-id="87c3a-115">Kaynak kod satırının başında, iki nokta arkasından bir tanımlayıcı yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="87c3a-115">Place an identifier, followed by a colon, at the beginning of the line of source code.</span></span>  
  
     <span data-ttu-id="87c3a-116">Örneğin, aşağıdaki kod satırlarını ile etiketlenmiş `Jump` ve `120`sırasıyla:</span><span class="sxs-lookup"><span data-stu-id="87c3a-116">For example, the following lines of code are labeled with `Jump` and `120`, respectively:</span></span>  
  
     [!code-vb[VbVbalrStatements#708](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#708)]  
  
## <a name="see-also"></a><span data-ttu-id="87c3a-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="87c3a-117">See also</span></span>
- [<span data-ttu-id="87c3a-118">Deyimler</span><span class="sxs-lookup"><span data-stu-id="87c3a-118">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
- [<span data-ttu-id="87c3a-119">Bildirilen Öğe Adları</span><span class="sxs-lookup"><span data-stu-id="87c3a-119">Declared Element Names</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="87c3a-120">Program Yapısı ve Kod Kuralları</span><span class="sxs-lookup"><span data-stu-id="87c3a-120">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
