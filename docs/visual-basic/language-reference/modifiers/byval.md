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
ms.openlocfilehash: abfe1489cb7e0d06b03c308e0704ce6f69ee55da
ms.sourcegitcommit: 1e7ac70be1b4d89708c0d9552897515f2cbf52c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68433808"
---
# <a name="byval-visual-basic"></a><span data-ttu-id="17f30-102">ByVal (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="17f30-102">ByVal (Visual Basic)</span></span>
<span data-ttu-id="17f30-103">Çağrılan yordamın veya özelliğin, çağıran koddaki bağımsız değişkeni temel alan bir değişkenin değerini değiştirememesi için bir bağımsız değişkenin [değere göre](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)geçtiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="17f30-103">Specifies that an argument is passed [by value](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md), so that the called procedure or property cannot change the value of a variable underlying the argument in the calling code.</span></span> <span data-ttu-id="17f30-104">Değiştirici belirtilmemişse, ByVal varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="17f30-104">If no modifier is specified, ByVal is the default.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="17f30-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="17f30-105">Remarks</span></span>  
 <span data-ttu-id="17f30-106">`ByVal` Değiştirici şu bağlamlarda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="17f30-106">The `ByVal` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="17f30-107">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="17f30-107">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="17f30-108">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="17f30-108">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="17f30-109">Operator Deyimi</span><span class="sxs-lookup"><span data-stu-id="17f30-109">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [<span data-ttu-id="17f30-110">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="17f30-110">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="17f30-111">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="17f30-111">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="example"></a><span data-ttu-id="17f30-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="17f30-112">Example</span></span>  
 <span data-ttu-id="17f30-113">Aşağıdaki örnek, bir başvuru türü bağımsız değişkeniyle `ByVal` parametre geçirme mekanizmasının kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="17f30-113">The following example demonstrates the use of the `ByVal` parameter passing mechanism with a reference type argument.</span></span> <span data-ttu-id="17f30-114">Örnekte, bağımsız değişkeni `c1`, sınıfının `Class1`bir örneğidir.</span><span class="sxs-lookup"><span data-stu-id="17f30-114">In the example, the argument is `c1`, an instance of class `Class1`.</span></span> <span data-ttu-id="17f30-115">`ByVal`yordamlardaki kodun başvuru bağımsız değişkeninin `c1`temel alınan değerini değiştirmesini önler, ancak erişilebilir alanları ve `c1`özellikleri korumaz.</span><span class="sxs-lookup"><span data-stu-id="17f30-115">`ByVal` prevents the code in the procedures from changing the underlying value of the reference argument, `c1`, but does not protect the accessible fields and properties of `c1`.</span></span>  
  
 [!code-vb[VbVbalrKeywords#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class5.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="17f30-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="17f30-116">See also</span></span>

- [<span data-ttu-id="17f30-117">anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="17f30-117">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="17f30-118">Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="17f30-118">Passing Arguments by Value and by Reference</span></span>](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
