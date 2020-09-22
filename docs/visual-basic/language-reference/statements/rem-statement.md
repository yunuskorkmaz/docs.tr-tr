---
title: REM Deyimi
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
ms.openlocfilehash: 6161a9f7e589988882b5f76477bc069afd2b9b41
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90871956"
---
# <a name="rem-statement-visual-basic"></a><span data-ttu-id="a2c14-102">REM Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a2c14-102">REM Statement (Visual Basic)</span></span>

<span data-ttu-id="a2c14-103">Bir programın kaynak kodunda açıklayıcı açıklamalar eklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a2c14-103">Used to include explanatory remarks in the source code of a program.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2c14-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a2c14-104">Syntax</span></span>  
  
```vb  
REM comment  
' comment  
```  
  
## <a name="parts"></a><span data-ttu-id="a2c14-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="a2c14-105">Parts</span></span>  

 `comment`  
 <span data-ttu-id="a2c14-106">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="a2c14-106">Optional.</span></span> <span data-ttu-id="a2c14-107">Dahil etmek istediğiniz açıklamanın metni.</span><span class="sxs-lookup"><span data-stu-id="a2c14-107">The text of any comment you want to include.</span></span> <span data-ttu-id="a2c14-108">Anahtar sözcüğü ve arasında bir boşluk gereklidir `REM` `comment` .</span><span class="sxs-lookup"><span data-stu-id="a2c14-108">A space is required between the `REM` keyword and `comment`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a2c14-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a2c14-109">Remarks</span></span>  

 <span data-ttu-id="a2c14-110">Bir `REM` ifadeyi tek başına bir satıra koyabilirsiniz ya da başka bir deyimden sonraki bir satıra koyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a2c14-110">You can put a `REM` statement alone on a line, or you can put it on a line following another statement.</span></span> <span data-ttu-id="a2c14-111">`REM`Deyimin satırdaki son ifade olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a2c14-111">The `REM` statement must be the last statement on the line.</span></span> <span data-ttu-id="a2c14-112">Başka bir bildirime uygunsa, `REM` Bu deyimden bir boşluk ile ayrılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a2c14-112">If it follows another statement, the `REM` must be separated from that statement by a space.</span></span>  
  
 <span data-ttu-id="a2c14-113">Yerine tek tırnak işareti ( `'` ) kullanabilirsiniz `REM` .</span><span class="sxs-lookup"><span data-stu-id="a2c14-113">You can use a single quotation mark (`'`) instead of `REM`.</span></span> <span data-ttu-id="a2c14-114">Bu, yorumunuz aynı satırdaki başka bir deyime veya bir satırda tek başına oturduğunda geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="a2c14-114">This is true whether your comment follows another statement on the same line or sits alone on a line.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a2c14-115">Bir `REM` satır devamlılık sırası () kullanarak bir deyime devam edemezsiniz `_` .</span><span class="sxs-lookup"><span data-stu-id="a2c14-115">You cannot continue a `REM` statement by using a line-continuation sequence (`_`).</span></span> <span data-ttu-id="a2c14-116">Bir yorum başladıktan sonra derleyici, özel anlam için karakterleri denetlemez.</span><span class="sxs-lookup"><span data-stu-id="a2c14-116">Once a comment begins, the compiler does not examine the characters for special meaning.</span></span> <span data-ttu-id="a2c14-117">Birden çok satırlık bir açıklama için, `REM` her satırda başka bir ifade veya bir açıklama simgesi ( `'` ) kullanın.</span><span class="sxs-lookup"><span data-stu-id="a2c14-117">For a multiple-line comment, use another `REM` statement or a comment symbol (`'`) on each line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a2c14-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="a2c14-118">Example</span></span>  

 <span data-ttu-id="a2c14-119">Aşağıdaki örnek, `REM` bir programa açıklayıcı açıklamalar eklemek için kullanılan ifadesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a2c14-119">The following example illustrates the `REM` statement, which is used to include explanatory remarks in a program.</span></span> <span data-ttu-id="a2c14-120">Ayrıca, yerine tek tırnak işareti karakteri () kullanmanın alternatifini de gösterir `'` `REM` .</span><span class="sxs-lookup"><span data-stu-id="a2c14-120">It also shows the alternative of using the single quotation-mark character (`'`) instead of `REM`.</span></span>  
  
 [!code-vb[VbVbalrStatements#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="a2c14-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a2c14-121">See also</span></span>

- [<span data-ttu-id="a2c14-122">Kod Açıklamaları</span><span class="sxs-lookup"><span data-stu-id="a2c14-122">Comments in Code</span></span>](../../programming-guide/program-structure/comments-in-code.md)
- [<span data-ttu-id="a2c14-123">Nasıl yapılır: Kodda Deyimleri Bölme ve Birleştirme</span><span class="sxs-lookup"><span data-stu-id="a2c14-123">How to: Break and Combine Statements in Code</span></span>](../../programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
