---
title: REM Deyimi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.'
- vb.Rem
- Rem
- "'"
helpviewer_keywords:
- REM statement [Visual Basic]
- comments, Visual Basic code
- code comments, Visual Basic
- Visual Basic code, comments
- "' comment marker character [Visual Basic]"
ms.assetid: 34126d7f-e0f9-476d-91e6-b31b398615dc
ms.openlocfilehash: 3c63c5613b40cb2014c77a0a996e3acb2cc304d4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58817025"
---
# <a name="rem-statement-visual-basic"></a><span data-ttu-id="8a52c-102">REM Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8a52c-102">REM Statement (Visual Basic)</span></span>
<span data-ttu-id="8a52c-103">Bir program kaynak kodunda açıklayıcı açıklamalar eklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8a52c-103">Used to include explanatory remarks in the source code of a program.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a52c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8a52c-104">Syntax</span></span>  
  
```  
REM comment  
' comment  
```  
  
## <a name="parts"></a><span data-ttu-id="8a52c-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="8a52c-105">Parts</span></span>  
 `comment`  
 <span data-ttu-id="8a52c-106">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="8a52c-106">Optional.</span></span> <span data-ttu-id="8a52c-107">Dahil etmek istediğiniz herhangi bir yorum metni.</span><span class="sxs-lookup"><span data-stu-id="8a52c-107">The text of any comment you want to include.</span></span> <span data-ttu-id="8a52c-108">Bir arasında gerekli bir alandır `REM` anahtar sözcüğü ve `comment`.</span><span class="sxs-lookup"><span data-stu-id="8a52c-108">A space is required between the `REM` keyword and `comment`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8a52c-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8a52c-109">Remarks</span></span>  
 <span data-ttu-id="8a52c-110">Koyabilirsiniz bir `REM` bir satır veya, tek başına bildirimi, başka bir deyiminin sonrasındaki bir satıra koyabilir.</span><span class="sxs-lookup"><span data-stu-id="8a52c-110">You can put a `REM` statement alone on a line, or you can put it on a line following another statement.</span></span> <span data-ttu-id="8a52c-111">`REM` Deyimi bir satırdaki son deyim olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8a52c-111">The `REM` statement must be the last statement on the line.</span></span> <span data-ttu-id="8a52c-112">Başka bir ifade izliyorsa `REM` bu deyiminden boşluk tarafından ayrılmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="8a52c-112">If it follows another statement, the `REM` must be separated from that statement by a space.</span></span>  
  
 <span data-ttu-id="8a52c-113">Tek tırnak işareti kullanabilirsiniz (`'`) yerine `REM`.</span><span class="sxs-lookup"><span data-stu-id="8a52c-113">You can use a single quotation mark (`'`) instead of `REM`.</span></span> <span data-ttu-id="8a52c-114">Bu, açıklamanızı aynı satırda başka bir ifade izleyen veya tek başına bir satırda yer alan geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="8a52c-114">This is true whether your comment follows another statement on the same line or sits alone on a line.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8a52c-115">Devam edemiyor bir `REM` satır devamlılığı sırası kullanarak deyimi (`_`).</span><span class="sxs-lookup"><span data-stu-id="8a52c-115">You cannot continue a `REM` statement by using a line-continuation sequence (`_`).</span></span> <span data-ttu-id="8a52c-116">Bir yorum başladıktan sonra derleyici karakterler için özel bir anlamı incelemez.</span><span class="sxs-lookup"><span data-stu-id="8a52c-116">Once a comment begins, the compiler does not examine the characters for special meaning.</span></span> <span data-ttu-id="8a52c-117">İçin birden çok satır yorum, başka kullanma `REM` deyimi veya bir yorum sembolü (`'`) her satırda.</span><span class="sxs-lookup"><span data-stu-id="8a52c-117">For a multiple-line comment, use another `REM` statement or a comment symbol (`'`) on each line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8a52c-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="8a52c-118">Example</span></span>  
 <span data-ttu-id="8a52c-119">Aşağıdaki örnekte gösterilmiştir `REM` deyimi bir programda açıklayıcı açıklamalar eklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8a52c-119">The following example illustrates the `REM` statement, which is used to include explanatory remarks in a program.</span></span> <span data-ttu-id="8a52c-120">Ayrıca, tek tırnak işareti karakteri kullanarak alternatif gösterir (`'`) yerine `REM`.</span><span class="sxs-lookup"><span data-stu-id="8a52c-120">It also shows the alternative of using the single quotation-mark character (`'`) instead of `REM`.</span></span>  
  
 [!code-vb[VbVbalrStatements#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="8a52c-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8a52c-121">See also</span></span>

- [<span data-ttu-id="8a52c-122">Code’daki Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8a52c-122">Comments in Code</span></span>](../../../visual-basic/programming-guide/program-structure/comments-in-code.md)
- [<span data-ttu-id="8a52c-123">Nasıl yapılır: Kodda Deyimleri Bölme ve Birleştirme</span><span class="sxs-lookup"><span data-stu-id="8a52c-123">How to: Break and Combine Statements in Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
