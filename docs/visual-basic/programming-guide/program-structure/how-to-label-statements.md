---
description: ': Nasıl yapılır: Label deyimleri (Visual Basic) hakkında daha fazla bilgi'
title: 'Nasıl yapılır: Etiket Deyimleri'
ms.date: 07/20/2015
helpviewer_keywords:
- colons (:)
- statements [Visual Basic], labels
- ': separator character'
- Visual Basic code, labeling statements
ms.assetid: 38f1ff43-2054-42cb-963b-1998e60c6ed4
ms.openlocfilehash: 4efb320dad7d52f6e9b94f6e6f81730f94b5966b
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100433258"
---
# <a name="how-to-label-statements-visual-basic"></a><span data-ttu-id="0a98a-103">Nasıl yapılır: Deyimler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0a98a-103">How to: Label Statements (Visual Basic)</span></span>

<span data-ttu-id="0a98a-104">Ekstre blokları, iki nokta üst üste ile ayrılmış kod satırlarından oluşur.</span><span class="sxs-lookup"><span data-stu-id="0a98a-104">Statement blocks are made up of lines of code delimited by colons.</span></span> <span data-ttu-id="0a98a-105">Bir tanımlayıcı dize veya tamsayının önünde bulunan kod satırları *etiketlenecek* şekilde söylenir.</span><span class="sxs-lookup"><span data-stu-id="0a98a-105">Lines of code preceded by an identifying string or integer are said to be *labeled*.</span></span> <span data-ttu-id="0a98a-106">Deyim etiketleri, bir kod satırını, gibi deyimlerle kullanılmak üzere belirlemek üzere işaretlemek için kullanılır `On Error Goto` .</span><span class="sxs-lookup"><span data-stu-id="0a98a-106">Statement labels are used to mark a line of code to identify it for use with statements such as `On Error Goto`.</span></span>

<span data-ttu-id="0a98a-107">Etiketler, programlama öğelerini tanımlayan ya da tamsayı değişmez değerleri gibi geçerli Visual Basic tanımlayıcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="0a98a-107">Labels may be either valid Visual Basic identifiers—such as those that identify programming elements—or integer literals.</span></span> <span data-ttu-id="0a98a-108">Bir etiket, kaynak kodu satırının başında görünmelidir ve bunun ardından iki nokta üst üste gelmelidir ve bunun ardından aynı satırdaki bir deyimin takip edilip edilmeyeceğini dikkate alınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0a98a-108">A label must appear at the beginning of a line of source code and must be followed by a colon, regardless of whether it is followed by a statement on the same line.</span></span>

<span data-ttu-id="0a98a-109">Derleyici, satırın başlangıcının önceden tanımlanmış tanımlayıcıyla eşleşip eşleşmediğini denetleyerek etiketleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0a98a-109">The compiler identifies labels by checking whether the beginning of the line matches any already-defined identifier.</span></span> <span data-ttu-id="0a98a-110">Değilse, derleyici bir etiket olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="0a98a-110">If it does not, the compiler assumes it is a label.</span></span>

<span data-ttu-id="0a98a-111">Etiketler kendi bildirim alanına sahiptir ve diğer tanımlayıcılarla karışmaz.</span><span class="sxs-lookup"><span data-stu-id="0a98a-111">Labels have their own declaration space and do not interfere with other identifiers.</span></span> <span data-ttu-id="0a98a-112">Etiketin kapsamı yöntemin gövdesidir.</span><span class="sxs-lookup"><span data-stu-id="0a98a-112">A label's scope is the body of the method.</span></span> <span data-ttu-id="0a98a-113">Etiket bildirimi herhangi bir belirsiz durumda önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="0a98a-113">Label declaration takes precedence in any ambiguous situation.</span></span>

> [!NOTE]
> <span data-ttu-id="0a98a-114">Etiketler yalnızca yöntemlerin içindeki yürütülebilir deyimlerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0a98a-114">Labels can be used only on executable statements inside methods.</span></span>

## <a name="to-label-a-line-of-code"></a><span data-ttu-id="0a98a-115">Bir kod satırını etiketlemek için</span><span class="sxs-lookup"><span data-stu-id="0a98a-115">To label a line of code</span></span>

<span data-ttu-id="0a98a-116">Kaynak kodu satırının başında bir tanımlayıcı ve sonra iki nokta üst üste koyun.</span><span class="sxs-lookup"><span data-stu-id="0a98a-116">Place an identifier, followed by a colon, at the beginning of the line of source code.</span></span>

<span data-ttu-id="0a98a-117">Örneğin, aşağıdaki kod satırları sırasıyla ve ile etiketlidir `Jump` `120` :</span><span class="sxs-lookup"><span data-stu-id="0a98a-117">For example, the following lines of code are labeled with `Jump` and `120`, respectively:</span></span>

[!code-vb[VbVbalrStatements#708](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#708)]

## <a name="see-also"></a><span data-ttu-id="0a98a-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0a98a-118">See also</span></span>

- [<span data-ttu-id="0a98a-119">Deyimler</span><span class="sxs-lookup"><span data-stu-id="0a98a-119">Statements</span></span>](../language-features/statements.md)
- [<span data-ttu-id="0a98a-120">Bildirilen Öğe Adları</span><span class="sxs-lookup"><span data-stu-id="0a98a-120">Declared Element Names</span></span>](../language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="0a98a-121">Program yapısı ve kod kuralları</span><span class="sxs-lookup"><span data-stu-id="0a98a-121">Program Structure and Code Conventions</span></span>](program-structure-and-code-conventions.md)
