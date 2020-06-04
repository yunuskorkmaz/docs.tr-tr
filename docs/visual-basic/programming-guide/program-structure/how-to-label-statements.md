---
title: 'Nasıl yapılır: Etiket Deyimleri'
ms.date: 07/20/2015
helpviewer_keywords:
- colons (:)
- statements [Visual Basic], labels
- ': separator character'
- Visual Basic code, labeling statements
ms.assetid: 38f1ff43-2054-42cb-963b-1998e60c6ed4
ms.openlocfilehash: 8f04d592c51b6a0630bfe623fd3574555aef9ff8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403219"
---
# <a name="how-to-label-statements-visual-basic"></a><span data-ttu-id="05650-102">Nasıl yapılır: Deyimler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="05650-102">How to: Label Statements (Visual Basic)</span></span>

<span data-ttu-id="05650-103">Ekstre blokları, iki nokta üst üste ile ayrılmış kod satırlarından oluşur.</span><span class="sxs-lookup"><span data-stu-id="05650-103">Statement blocks are made up of lines of code delimited by colons.</span></span> <span data-ttu-id="05650-104">Bir tanımlayıcı dize veya tamsayının önünde bulunan kod satırları *etiketlenecek*şekilde söylenir.</span><span class="sxs-lookup"><span data-stu-id="05650-104">Lines of code preceded by an identifying string or integer are said to be *labeled*.</span></span> <span data-ttu-id="05650-105">Deyim etiketleri, bir kod satırını, gibi deyimlerle kullanılmak üzere belirlemek üzere işaretlemek için kullanılır `On Error Goto` .</span><span class="sxs-lookup"><span data-stu-id="05650-105">Statement labels are used to mark a line of code to identify it for use with statements such as `On Error Goto`.</span></span>

<span data-ttu-id="05650-106">Etiketler, programlama öğelerini tanımlayan ya da tamsayı değişmez değerleri gibi geçerli Visual Basic tanımlayıcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="05650-106">Labels may be either valid Visual Basic identifiers—such as those that identify programming elements—or integer literals.</span></span> <span data-ttu-id="05650-107">Bir etiket, kaynak kodu satırının başında görünmelidir ve bunun ardından iki nokta üst üste gelmelidir ve bunun ardından aynı satırdaki bir deyimin takip edilip edilmeyeceğini dikkate alınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="05650-107">A label must appear at the beginning of a line of source code and must be followed by a colon, regardless of whether it is followed by a statement on the same line.</span></span>

<span data-ttu-id="05650-108">Derleyici, satırın başlangıcının önceden tanımlanmış tanımlayıcıyla eşleşip eşleşmediğini denetleyerek etiketleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="05650-108">The compiler identifies labels by checking whether the beginning of the line matches any already-defined identifier.</span></span> <span data-ttu-id="05650-109">Değilse, derleyici bir etiket olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="05650-109">If it does not, the compiler assumes it is a label.</span></span>

<span data-ttu-id="05650-110">Etiketler kendi bildirim alanına sahiptir ve diğer tanımlayıcılarla karışmaz.</span><span class="sxs-lookup"><span data-stu-id="05650-110">Labels have their own declaration space and do not interfere with other identifiers.</span></span> <span data-ttu-id="05650-111">Etiketin kapsamı yöntemin gövdesidir.</span><span class="sxs-lookup"><span data-stu-id="05650-111">A label's scope is the body of the method.</span></span> <span data-ttu-id="05650-112">Etiket bildirimi herhangi bir belirsiz durumda önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="05650-112">Label declaration takes precedence in any ambiguous situation.</span></span>

> [!NOTE]
> <span data-ttu-id="05650-113">Etiketler yalnızca yöntemlerin içindeki yürütülebilir deyimlerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="05650-113">Labels can be used only on executable statements inside methods.</span></span>

## <a name="to-label-a-line-of-code"></a><span data-ttu-id="05650-114">Bir kod satırını etiketlemek için</span><span class="sxs-lookup"><span data-stu-id="05650-114">To label a line of code</span></span>

<span data-ttu-id="05650-115">Kaynak kodu satırının başında bir tanımlayıcı ve sonra iki nokta üst üste koyun.</span><span class="sxs-lookup"><span data-stu-id="05650-115">Place an identifier, followed by a colon, at the beginning of the line of source code.</span></span>

<span data-ttu-id="05650-116">Örneğin, aşağıdaki kod satırları sırasıyla ve ile etiketlidir `Jump` `120` :</span><span class="sxs-lookup"><span data-stu-id="05650-116">For example, the following lines of code are labeled with `Jump` and `120`, respectively:</span></span>

[!code-vb[VbVbalrStatements#708](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#708)]

## <a name="see-also"></a><span data-ttu-id="05650-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="05650-117">See also</span></span>

- [<span data-ttu-id="05650-118">Deyimler</span><span class="sxs-lookup"><span data-stu-id="05650-118">Statements</span></span>](../language-features/statements.md)
- [<span data-ttu-id="05650-119">Bildirilen Öğe Adları</span><span class="sxs-lookup"><span data-stu-id="05650-119">Declared Element Names</span></span>](../language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="05650-120">Program yapısı ve kod kuralları</span><span class="sxs-lookup"><span data-stu-id="05650-120">Program Structure and Code Conventions</span></span>](program-structure-and-code-conventions.md)
