---
title: 'Nasıl yapılır: Label deyimleri (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- colons (:)
- statements [Visual Basic], labels
- ': separator character'
- Visual Basic code, labeling statements
ms.assetid: 38f1ff43-2054-42cb-963b-1998e60c6ed4
ms.openlocfilehash: 6b442b5a0ad731cfc490a7387c78ac9279dddaf0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69961331"
---
# <a name="how-to-label-statements-visual-basic"></a><span data-ttu-id="8fc22-102">Nasıl yapılır: Label deyimleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8fc22-102">How to: Label Statements (Visual Basic)</span></span>
<span data-ttu-id="8fc22-103">Ekstre blokları, iki nokta üst üste ile ayrılmış kod satırlarından oluşur.</span><span class="sxs-lookup"><span data-stu-id="8fc22-103">Statement blocks are made up of lines of code delimited by colons.</span></span> <span data-ttu-id="8fc22-104">Bir tanımlayıcı dize veya tamsayının önünde bulunan kod satırları etiketlenecek şekilde söylenir.</span><span class="sxs-lookup"><span data-stu-id="8fc22-104">Lines of code preceded by an identifying string or integer are said to be *labeled*.</span></span> <span data-ttu-id="8fc22-105">Deyim etiketleri, bir kod satırını, gibi deyimlerle `On Error Goto`kullanılmak üzere belirlemek üzere işaretlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8fc22-105">Statement labels are used to mark a line of code to identify it for use with statements such as `On Error Goto`.</span></span>  
  
 <span data-ttu-id="8fc22-106">Etiketler, programlama öğelerini tanımlayan ya da tamsayı değişmez değerleri gibi geçerli Visual Basic tanımlayıcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="8fc22-106">Labels may be either valid Visual Basic identifiers—such as those that identify programming elements—or integer literals.</span></span> <span data-ttu-id="8fc22-107">Bir etiket, kaynak kodu satırının başında görünmelidir ve bunun ardından iki nokta üst üste gelmelidir ve bunun ardından aynı satırdaki bir deyimin takip edilip edilmeyeceğini dikkate alınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8fc22-107">A label must appear at the beginning of a line of source code and must be followed by a colon, regardless of whether it is followed by a statement on the same line.</span></span>  
  
 <span data-ttu-id="8fc22-108">Derleyici, satırın başlangıcının önceden tanımlanmış tanımlayıcıyla eşleşip eşleşmediğini denetleyerek etiketleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8fc22-108">The compiler identifies labels by checking whether the beginning of the line matches any already-defined identifier.</span></span> <span data-ttu-id="8fc22-109">Değilse, derleyici bir etiket olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="8fc22-109">If it does not, the compiler assumes it is a label.</span></span>  
  
 <span data-ttu-id="8fc22-110">Etiketler kendi bildirim alanına sahiptir ve diğer tanımlayıcılarla karışmaz.</span><span class="sxs-lookup"><span data-stu-id="8fc22-110">Labels have their own declaration space and do not interfere with other identifiers.</span></span> <span data-ttu-id="8fc22-111">Etiketin kapsamı yöntemin gövdesidir.</span><span class="sxs-lookup"><span data-stu-id="8fc22-111">A label's scope is the body of the method.</span></span> <span data-ttu-id="8fc22-112">Etiket bildirimi herhangi bir belirsiz durumda önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="8fc22-112">Label declaration takes precedence in any ambiguous situation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8fc22-113">Etiketler yalnızca yöntemlerin içindeki yürütülebilir deyimlerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8fc22-113">Labels can be used only on executable statements inside methods.</span></span>  
  
### <a name="to-label-a-line-of-code"></a><span data-ttu-id="8fc22-114">Bir kod satırını etiketlemek için</span><span class="sxs-lookup"><span data-stu-id="8fc22-114">To label a line of code</span></span>  
  
- <span data-ttu-id="8fc22-115">Kaynak kodu satırının başında bir tanımlayıcı ve sonra iki nokta üst üste koyun.</span><span class="sxs-lookup"><span data-stu-id="8fc22-115">Place an identifier, followed by a colon, at the beginning of the line of source code.</span></span>  
  
     <span data-ttu-id="8fc22-116">Örneğin, aşağıdaki kod satırları sırasıyla ve `Jump` `120`ile etiketlidir:</span><span class="sxs-lookup"><span data-stu-id="8fc22-116">For example, the following lines of code are labeled with `Jump` and `120`, respectively:</span></span>  
  
     [!code-vb[VbVbalrStatements#708](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#708)]  
  
## <a name="see-also"></a><span data-ttu-id="8fc22-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8fc22-117">See also</span></span>

- [<span data-ttu-id="8fc22-118">Deyimler</span><span class="sxs-lookup"><span data-stu-id="8fc22-118">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
- [<span data-ttu-id="8fc22-119">Bildirilen Öğe Adları</span><span class="sxs-lookup"><span data-stu-id="8fc22-119">Declared Element Names</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="8fc22-120">Program Yapısı ve Kod Kuralları</span><span class="sxs-lookup"><span data-stu-id="8fc22-120">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
