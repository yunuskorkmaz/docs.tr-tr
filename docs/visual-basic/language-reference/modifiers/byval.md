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
ms.openlocfilehash: 1fa4c1fa0a2def02dd56fa3728a8df4b5ff16b7f
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666854"
---
# <a name="byval-visual-basic"></a><span data-ttu-id="9a5e1-102">ByVal (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9a5e1-102">ByVal (Visual Basic)</span></span>
<span data-ttu-id="9a5e1-103">Çağrılan yordamın veya özelliğin, çağıran koddaki bağımsız değişkeni temel alan bir değişkenin değerini değiştirememesi için bir bağımsız değişkenin [değere göre](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)geçtiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9a5e1-103">Specifies that an argument is passed [by value](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md), so that the called procedure or property cannot change the value of a variable underlying the argument in the calling code.</span></span> <span data-ttu-id="9a5e1-104">Değiştirici belirtilmemişse, ByVal varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="9a5e1-104">If no modifier is specified, ByVal is the default.</span></span>

> [!NOTE]
> <span data-ttu-id="9a5e1-105">Varsayılan olduğu için, `ByVal` anahtar sözcüğünü Yöntem imzalarında açıkça belirtmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="9a5e1-105">Because it is the default, you do not have to explicitly specify the `ByVal` keyword in method signatures.</span></span> <span data-ttu-id="9a5e1-106">Gürültülü kod üretme eğilimi gösterir ve genellikle varsayılan `ByRef` olmayan anahtar kelimeye daha fazla bakmakta olur.</span><span class="sxs-lookup"><span data-stu-id="9a5e1-106">It tends to produce noisy code and often leads to the non-default `ByRef` keyword being overlooked.</span></span>

## <a name="remarks"></a><span data-ttu-id="9a5e1-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9a5e1-107">Remarks</span></span>
 <span data-ttu-id="9a5e1-108">`ByVal` Değiştirici şu bağlamlarda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="9a5e1-108">The `ByVal` modifier can be used in these contexts:</span></span>

 [<span data-ttu-id="9a5e1-109">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="9a5e1-109">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)

 [<span data-ttu-id="9a5e1-110">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="9a5e1-110">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
  
 [<span data-ttu-id="9a5e1-111">Operator Deyimi</span><span class="sxs-lookup"><span data-stu-id="9a5e1-111">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)
  
 [<span data-ttu-id="9a5e1-112">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="9a5e1-112">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
  
 [<span data-ttu-id="9a5e1-113">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="9a5e1-113">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)

## <a name="example"></a><span data-ttu-id="9a5e1-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="9a5e1-114">Example</span></span>
 <span data-ttu-id="9a5e1-115">Aşağıdaki örnek, bir başvuru türü bağımsız değişkeniyle `ByVal` parametre geçirme mekanizmasının kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="9a5e1-115">The following example demonstrates the use of the `ByVal` parameter passing mechanism with a reference type argument.</span></span> <span data-ttu-id="9a5e1-116">Örnekte, bağımsız değişkeni `c1`, sınıfının `Class1`bir örneğidir.</span><span class="sxs-lookup"><span data-stu-id="9a5e1-116">In the example, the argument is `c1`, an instance of class `Class1`.</span></span> <span data-ttu-id="9a5e1-117">`ByVal`yordamlardaki kodun başvuru bağımsız değişkeninin `c1`temel alınan değerini değiştirmesini önler, ancak erişilebilir alanları ve `c1`özellikleri korumaz.</span><span class="sxs-lookup"><span data-stu-id="9a5e1-117">`ByVal` prevents the code in the procedures from changing the underlying value of the reference argument, `c1`, but does not protect the accessible fields and properties of `c1`.</span></span>

 [!code-vb[VbVbalrKeywords#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class5.vb#10)]

## <a name="see-also"></a><span data-ttu-id="9a5e1-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9a5e1-118">See also</span></span>

- [<span data-ttu-id="9a5e1-119">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="9a5e1-119">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="9a5e1-120">Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="9a5e1-120">Passing Arguments by Value and by Reference</span></span>](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
