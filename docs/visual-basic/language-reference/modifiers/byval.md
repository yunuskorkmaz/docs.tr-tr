---
title: ByVal (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ByVal
- ByVal
helpviewer_keywords:
- ByVal keyword [Visual Basic], contexts
- ByVal keyword [Visual Basic]
ms.assetid: 1eaf4e58-b305-4785-9e3d-e416b9c75598
ms.openlocfilehash: 5e534eac2300327d4c54c5ce93d8b2c6c538e794
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61801672"
---
# <a name="byval-visual-basic"></a><span data-ttu-id="0ddb5-102">ByVal (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0ddb5-102">ByVal (Visual Basic)</span></span>
<span data-ttu-id="0ddb5-103">Bağımsız değişken çağrılan yordam veya özellik çağıran koddaki bağımsız değişken arka plandaki bir değişkenin değerini değiştiremezsiniz şekilde geçirildiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0ddb5-103">Specifies that an argument is passed in such a way that the called procedure or property cannot change the value of a variable underlying the argument in the calling code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0ddb5-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0ddb5-104">Remarks</span></span>  
 <span data-ttu-id="0ddb5-105">`ByVal` Bu bağlamda değiştirici kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="0ddb5-105">The `ByVal` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="0ddb5-106">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="0ddb5-106">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="0ddb5-107">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="0ddb5-107">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="0ddb5-108">Operator Deyimi</span><span class="sxs-lookup"><span data-stu-id="0ddb5-108">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [<span data-ttu-id="0ddb5-109">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="0ddb5-109">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="0ddb5-110">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="0ddb5-110">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="example"></a><span data-ttu-id="0ddb5-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="0ddb5-111">Example</span></span>  
 <span data-ttu-id="0ddb5-112">Aşağıdaki örnek, kullanımını gösterir `ByVal` parametre mekanizması ile bir başvuru türü bağımsız değişkeni geçirme.</span><span class="sxs-lookup"><span data-stu-id="0ddb5-112">The following example demonstrates the use of the `ByVal` parameter passing mechanism with a reference type argument.</span></span> <span data-ttu-id="0ddb5-113">Örnekte, bağımsız değişken olan `c1`, sınıfının bir örneğini `Class1`.</span><span class="sxs-lookup"><span data-stu-id="0ddb5-113">In the example, the argument is `c1`, an instance of class `Class1`.</span></span> <span data-ttu-id="0ddb5-114">`ByVal` yordamları kodda başvuru bağımsız değişkeni, temel alınan değerini değiştirmesini engeller `c1`, ancak erişilebilir alanlarına ve özelliklerine korumaz `c1`.</span><span class="sxs-lookup"><span data-stu-id="0ddb5-114">`ByVal` prevents the code in the procedures from changing the underlying value of the reference argument, `c1`, but does not protect the accessible fields and properties of `c1`.</span></span>  
  
 [!code-vb[VbVbalrKeywords#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class5.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="0ddb5-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0ddb5-115">See also</span></span>

- [<span data-ttu-id="0ddb5-116">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="0ddb5-116">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="0ddb5-117">Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="0ddb5-117">Passing Arguments by Value and by Reference</span></span>](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
