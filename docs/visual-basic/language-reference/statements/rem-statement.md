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
ms.openlocfilehash: 16149ce42e3476cf07a62298f83734fee9ec7253
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957766"
---
# <a name="rem-statement-visual-basic"></a><span data-ttu-id="6e847-102">REM Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6e847-102">REM Statement (Visual Basic)</span></span>
<span data-ttu-id="6e847-103">Bir programın kaynak kodunda açıklayıcı açıklamalar eklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6e847-103">Used to include explanatory remarks in the source code of a program.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e847-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6e847-104">Syntax</span></span>  
  
```  
REM comment  
' comment  
```  
  
## <a name="parts"></a><span data-ttu-id="6e847-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="6e847-105">Parts</span></span>  
 `comment`  
 <span data-ttu-id="6e847-106">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="6e847-106">Optional.</span></span> <span data-ttu-id="6e847-107">Dahil etmek istediğiniz açıklamanın metni.</span><span class="sxs-lookup"><span data-stu-id="6e847-107">The text of any comment you want to include.</span></span> <span data-ttu-id="6e847-108">`REM` Anahtar sözcüğü ve `comment`arasında bir boşluk gereklidir.</span><span class="sxs-lookup"><span data-stu-id="6e847-108">A space is required between the `REM` keyword and `comment`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6e847-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6e847-109">Remarks</span></span>  
 <span data-ttu-id="6e847-110">Bir `REM` ifadeyi tek başına bir satıra koyabilirsiniz ya da başka bir deyimden sonraki bir satıra koyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6e847-110">You can put a `REM` statement alone on a line, or you can put it on a line following another statement.</span></span> <span data-ttu-id="6e847-111">`REM` Deyimin satırdaki son ifade olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6e847-111">The `REM` statement must be the last statement on the line.</span></span> <span data-ttu-id="6e847-112">Başka bir bildirime `REM` uygunsa, bu deyimden bir boşluk ile ayrılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6e847-112">If it follows another statement, the `REM` must be separated from that statement by a space.</span></span>  
  
 <span data-ttu-id="6e847-113">Yerine tek tırnak işareti (`'`) kullanabilirsiniz. `REM`</span><span class="sxs-lookup"><span data-stu-id="6e847-113">You can use a single quotation mark (`'`) instead of `REM`.</span></span> <span data-ttu-id="6e847-114">Bu, yorumunuz aynı satırdaki başka bir deyime veya bir satırda tek başına oturduğunda geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="6e847-114">This is true whether your comment follows another statement on the same line or sits alone on a line.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6e847-115">Bir satır devamlılık `REM` sırası (`_`) kullanarak bir deyime devam edemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="6e847-115">You cannot continue a `REM` statement by using a line-continuation sequence (`_`).</span></span> <span data-ttu-id="6e847-116">Bir yorum başladıktan sonra derleyici, özel anlam için karakterleri denetlemez.</span><span class="sxs-lookup"><span data-stu-id="6e847-116">Once a comment begins, the compiler does not examine the characters for special meaning.</span></span> <span data-ttu-id="6e847-117">Birden çok satırlık bir açıklama için, her satırda `REM` başka bir ifade veya bir açıklama`'`simgesi () kullanın.</span><span class="sxs-lookup"><span data-stu-id="6e847-117">For a multiple-line comment, use another `REM` statement or a comment symbol (`'`) on each line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6e847-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="6e847-118">Example</span></span>  
 <span data-ttu-id="6e847-119">Aşağıdaki örnek, bir programa `REM` açıklayıcı açıklamalar eklemek için kullanılan ifadesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="6e847-119">The following example illustrates the `REM` statement, which is used to include explanatory remarks in a program.</span></span> <span data-ttu-id="6e847-120">Ayrıca,`'` `REM`yerine tek tırnak işareti karakteri () kullanmanın alternatifini de gösterir.</span><span class="sxs-lookup"><span data-stu-id="6e847-120">It also shows the alternative of using the single quotation-mark character (`'`) instead of `REM`.</span></span>  
  
 [!code-vb[VbVbalrStatements#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="6e847-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6e847-121">See also</span></span>

- [<span data-ttu-id="6e847-122">Code’daki Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6e847-122">Comments in Code</span></span>](../../../visual-basic/programming-guide/program-structure/comments-in-code.md)
- [<span data-ttu-id="6e847-123">Nasıl yapılır: Kodda Deyimleri Bölme ve Birleştirme</span><span class="sxs-lookup"><span data-stu-id="6e847-123">How to: Break and Combine Statements in Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
