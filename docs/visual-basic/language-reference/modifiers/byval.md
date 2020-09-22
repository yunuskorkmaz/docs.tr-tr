---
title: ByVal
ms.date: 07/20/2015
f1_keywords:
- vb.ByVal
- ByVal
helpviewer_keywords:
- ByVal keyword [Visual Basic], contexts
- ByVal keyword [Visual Basic]
ms.assetid: 1eaf4e58-b305-4785-9e3d-e416b9c75598
ms.openlocfilehash: 8daf6600f59cea343e0d02b99632b92ce4bf3183
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875473"
---
# <a name="byval-visual-basic"></a><span data-ttu-id="f789c-102">ByVal (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f789c-102">ByVal (Visual Basic)</span></span>

<span data-ttu-id="f789c-103">Çağrılan yordamın veya özelliğin, çağıran koddaki bağımsız değişkeni temel alan bir değişkenin değerini değiştirememesi için bir bağımsız değişkenin [değere göre](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)geçtiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f789c-103">Specifies that an argument is passed [by value](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md), so that the called procedure or property cannot change the value of a variable underlying the argument in the calling code.</span></span> <span data-ttu-id="f789c-104">Değiştirici belirtilmemişse, ByVal varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="f789c-104">If no modifier is specified, ByVal is the default.</span></span>

> [!NOTE]
> <span data-ttu-id="f789c-105">Varsayılan olduğu için, `ByVal` anahtar sözcüğünü Yöntem imzalarında açıkça belirtmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="f789c-105">Because it is the default, you do not have to explicitly specify the `ByVal` keyword in method signatures.</span></span> <span data-ttu-id="f789c-106">Gürültülü kod üretme eğilimi gösterir ve genellikle varsayılan olmayan `ByRef` anahtar kelimeye daha fazla bakmakta olur.</span><span class="sxs-lookup"><span data-stu-id="f789c-106">It tends to produce noisy code and often leads to the non-default `ByRef` keyword being overlooked.</span></span>

## <a name="remarks"></a><span data-ttu-id="f789c-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f789c-107">Remarks</span></span>

 <span data-ttu-id="f789c-108">`ByVal`Değiştirici şu bağlamlarda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="f789c-108">The `ByVal` modifier can be used in these contexts:</span></span>

 [<span data-ttu-id="f789c-109">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="f789c-109">Declare Statement</span></span>](../statements/declare-statement.md)

 [<span data-ttu-id="f789c-110">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="f789c-110">Function Statement</span></span>](../statements/function-statement.md)
  
 [<span data-ttu-id="f789c-111">Operator Deyimi</span><span class="sxs-lookup"><span data-stu-id="f789c-111">Operator Statement</span></span>](../statements/operator-statement.md)
  
 [<span data-ttu-id="f789c-112">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="f789c-112">Property Statement</span></span>](../statements/property-statement.md)
  
 [<span data-ttu-id="f789c-113">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="f789c-113">Sub Statement</span></span>](../statements/sub-statement.md)

## <a name="example"></a><span data-ttu-id="f789c-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="f789c-114">Example</span></span>

 <span data-ttu-id="f789c-115">Aşağıdaki örnek, `ByVal` bir başvuru türü bağımsız değişkeniyle parametre geçirme mekanizmasının kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f789c-115">The following example demonstrates the use of the `ByVal` parameter passing mechanism with a reference type argument.</span></span> <span data-ttu-id="f789c-116">Örnekte, bağımsız değişkeni `c1` , sınıfının bir örneğidir `Class1` .</span><span class="sxs-lookup"><span data-stu-id="f789c-116">In the example, the argument is `c1`, an instance of class `Class1`.</span></span> <span data-ttu-id="f789c-117">`ByVal` yordamlardaki kodun başvuru bağımsız değişkeninin temel alınan değerini değiştirmesini önler, `c1` ancak erişilebilir alanları ve özellikleri korumaz `c1` .</span><span class="sxs-lookup"><span data-stu-id="f789c-117">`ByVal` prevents the code in the procedures from changing the underlying value of the reference argument, `c1`, but does not protect the accessible fields and properties of `c1`.</span></span>

 [!code-vb[VbVbalrKeywords#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class5.vb#10)]

## <a name="see-also"></a><span data-ttu-id="f789c-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f789c-118">See also</span></span>

- [<span data-ttu-id="f789c-119">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="f789c-119">Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="f789c-120">Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="f789c-120">Passing Arguments by Value and by Reference</span></span>](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
