---
description: 'Daha fazla bilgi edinin: ByVal (Visual Basic)'
title: ByVal
ms.date: 07/20/2015
f1_keywords:
- vb.ByVal
- ByVal
helpviewer_keywords:
- ByVal keyword [Visual Basic], contexts
- ByVal keyword [Visual Basic]
ms.assetid: 1eaf4e58-b305-4785-9e3d-e416b9c75598
ms.openlocfilehash: cd7116c0bcc3d263cc2bb6a9b95e46e8ff0cc116
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99774622"
---
# <a name="byval-visual-basic"></a><span data-ttu-id="9e4a7-103">ByVal (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9e4a7-103">ByVal (Visual Basic)</span></span>

<span data-ttu-id="9e4a7-104">Çağrılan yordamın veya özelliğin, çağıran koddaki bağımsız değişkeni temel alan bir değişkenin değerini değiştirememesi için bir bağımsız değişkenin [değere göre](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)geçtiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9e4a7-104">Specifies that an argument is passed [by value](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md), so that the called procedure or property cannot change the value of a variable underlying the argument in the calling code.</span></span> <span data-ttu-id="9e4a7-105">Değiştirici belirtilmemişse, ByVal varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="9e4a7-105">If no modifier is specified, ByVal is the default.</span></span>

> [!NOTE]
> <span data-ttu-id="9e4a7-106">Varsayılan olduğu için, `ByVal` anahtar sözcüğünü Yöntem imzalarında açıkça belirtmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="9e4a7-106">Because it is the default, you do not have to explicitly specify the `ByVal` keyword in method signatures.</span></span> <span data-ttu-id="9e4a7-107">Gürültülü kod üretme eğilimi gösterir ve genellikle varsayılan olmayan `ByRef` anahtar kelimeye daha fazla bakmakta olur.</span><span class="sxs-lookup"><span data-stu-id="9e4a7-107">It tends to produce noisy code and often leads to the non-default `ByRef` keyword being overlooked.</span></span>

## <a name="remarks"></a><span data-ttu-id="9e4a7-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9e4a7-108">Remarks</span></span>

 <span data-ttu-id="9e4a7-109">`ByVal`Değiştirici şu bağlamlarda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="9e4a7-109">The `ByVal` modifier can be used in these contexts:</span></span>

 [<span data-ttu-id="9e4a7-110">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="9e4a7-110">Declare Statement</span></span>](../statements/declare-statement.md)

 [<span data-ttu-id="9e4a7-111">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="9e4a7-111">Function Statement</span></span>](../statements/function-statement.md)
  
 [<span data-ttu-id="9e4a7-112">Operator Deyimi</span><span class="sxs-lookup"><span data-stu-id="9e4a7-112">Operator Statement</span></span>](../statements/operator-statement.md)
  
 [<span data-ttu-id="9e4a7-113">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="9e4a7-113">Property Statement</span></span>](../statements/property-statement.md)
  
 [<span data-ttu-id="9e4a7-114">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="9e4a7-114">Sub Statement</span></span>](../statements/sub-statement.md)

## <a name="example"></a><span data-ttu-id="9e4a7-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="9e4a7-115">Example</span></span>

 <span data-ttu-id="9e4a7-116">Aşağıdaki örnek, `ByVal` bir başvuru türü bağımsız değişkeniyle parametre geçirme mekanizmasının kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="9e4a7-116">The following example demonstrates the use of the `ByVal` parameter passing mechanism with a reference type argument.</span></span> <span data-ttu-id="9e4a7-117">Örnekte, bağımsız değişkeni `c1` , sınıfının bir örneğidir `Class1` .</span><span class="sxs-lookup"><span data-stu-id="9e4a7-117">In the example, the argument is `c1`, an instance of class `Class1`.</span></span> <span data-ttu-id="9e4a7-118">`ByVal` yordamlardaki kodun başvuru bağımsız değişkeninin temel alınan değerini değiştirmesini önler, `c1` ancak erişilebilir alanları ve özellikleri korumaz `c1` .</span><span class="sxs-lookup"><span data-stu-id="9e4a7-118">`ByVal` prevents the code in the procedures from changing the underlying value of the reference argument, `c1`, but does not protect the accessible fields and properties of `c1`.</span></span>

 [!code-vb[VbVbalrKeywords#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class5.vb#10)]

## <a name="see-also"></a><span data-ttu-id="9e4a7-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9e4a7-119">See also</span></span>

- [<span data-ttu-id="9e4a7-120">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="9e4a7-120">Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="9e4a7-121">Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="9e4a7-121">Passing Arguments by Value and by Reference</span></span>](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
