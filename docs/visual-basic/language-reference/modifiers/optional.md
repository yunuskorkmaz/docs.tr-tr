---
title: İsteğe Bağlı (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Optional
- vb.optional
helpviewer_keywords:
- Optional keyword [Visual Basic], contexts
- Optional keyword [Visual Basic]
ms.assetid: 4571ce88-a539-4115-b230-54eb277c6aa7
ms.openlocfilehash: f88020c7407fb9c91e06bc2ee177773171e344fe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33599310"
---
# <a name="optional-visual-basic"></a><span data-ttu-id="a50e4-102">İsteğe Bağlı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a50e4-102">Optional (Visual Basic)</span></span>
<span data-ttu-id="a50e4-103">Yordam çağrıldığında bir yordam bağımsız değişkenini atlanabilir belirtir.</span><span class="sxs-lookup"><span data-stu-id="a50e4-103">Specifies that a procedure argument can be omitted when the procedure is called.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a50e4-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a50e4-104">Remarks</span></span>  
 <span data-ttu-id="a50e4-105">İsteğe bağlı her parametre için bir sabit ifadesine bu parametrenin varsayılan değeri olarak belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a50e4-105">For each optional parameter, you must specify a constant expression as the default value of that parameter.</span></span> <span data-ttu-id="a50e4-106">İfade değerlendirilirse [hiçbir şey](../../../visual-basic/language-reference/nothing.md), değer veri türünün varsayılan değeri parametresinin varsayılan değeri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a50e4-106">If the expression evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), the default value of the value data type is used as the default value of the parameter.</span></span>  
  
 <span data-ttu-id="a50e4-107">Parametre listesi isteğe bağlı bir parametre içeriyorsa, kendisini izleyen her parametre ayrıca isteğe bağlı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a50e4-107">If the parameter list contains an optional parameter, every parameter that follows it must also be optional.</span></span>  
  
 <span data-ttu-id="a50e4-108">`Optional` Değiştiricisi bu bağlamlarında kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="a50e4-108">The `Optional` modifier can be used in these contexts:</span></span>  
  
-   [<span data-ttu-id="a50e4-109">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="a50e4-109">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
-   [<span data-ttu-id="a50e4-110">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="a50e4-110">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
-   [<span data-ttu-id="a50e4-111">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="a50e4-111">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
-   [<span data-ttu-id="a50e4-112">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="a50e4-112">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
> [!NOTE]
>  <span data-ttu-id="a50e4-113">İle veya isteğe bağlı parametreler olmadan bir yordamı çağrılırken, konuma göre veya ada göre bağımsız değişkenler geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a50e4-113">When calling a procedure with or without optional parameters, you can pass arguments by position or by name.</span></span> <span data-ttu-id="a50e4-114">Daha fazla bilgi için bkz: [geçirme bağımsız değişkenleri konuma ve ada göre](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md).</span><span class="sxs-lookup"><span data-stu-id="a50e4-114">For more information, see [Passing Arguments by Position and by Name](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a50e4-115">İsteğe bağlı parametreleri olan bir yordamı aşırı yükleme kullanarak da tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a50e4-115">You can also define a procedure with optional parameters by using overloading.</span></span> <span data-ttu-id="a50e4-116">İsteğe bağlı bir parametre varsa, iki aşırı yüklenmiş yordamı, bir parametre kabul eden ve sürümleri olmayan bir tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a50e4-116">If you have one optional parameter, you can define two overloaded versions of the procedure, one that accepts the parameter and one that doesn’t.</span></span> <span data-ttu-id="a50e4-117">Daha fazla bilgi için bkz: [yordam aşırı yüklemesi](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="a50e4-117">For more information, see [Procedure Overloading](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a50e4-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="a50e4-118">Example</span></span>  
 <span data-ttu-id="a50e4-119">Aşağıdaki örnek, isteğe bağlı bir parametre olan bir yordam tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a50e4-119">The following example defines a procedure that has an optional parameter.</span></span>  
  
```  
Public Function FindMatches(ByRef values As List(Of String),  
                            ByVal searchString As String,  
                            Optional ByVal matchCase As Boolean = False) As List(Of String)  
  
    Dim results As IEnumerable(Of String)  
  
    If matchCase Then  
        results = From v In values  
                  Where v.Contains(searchString)  
    Else  
        results = From v In values  
                  Where UCase(v).Contains(UCase(searchString))  
    End If  
  
    Return results.ToList()  
End Function  
```  
  
## <a name="example"></a><span data-ttu-id="a50e4-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="a50e4-120">Example</span></span>  
 <span data-ttu-id="a50e4-121">Aşağıdaki örnek, konuma göre geçirilen bağımsız değişkenlerle ve ada göre geçirilen bağımsız değişkenlerle bir yordam çağırma gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="a50e4-121">The following example demonstrates how to call a procedure with arguments passed by position and with arguments passed by name.</span></span> <span data-ttu-id="a50e4-122">Yordamın iki isteğe bağlı parametreye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="a50e4-122">The procedure has two optional parameters.</span></span>  
  
 [!code-vb[VbVbalrKeywords#21](../../../visual-basic/language-reference/codesnippet/VisualBasic/optional_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="a50e4-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a50e4-123">See Also</span></span>  
 [<span data-ttu-id="a50e4-124">Parametre Listesi</span><span class="sxs-lookup"><span data-stu-id="a50e4-124">Parameter List</span></span>](../../../visual-basic/language-reference/statements/parameter-list.md)  
 [<span data-ttu-id="a50e4-125">İsteğe Bağlı Parametreler</span><span class="sxs-lookup"><span data-stu-id="a50e4-125">Optional Parameters</span></span>](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)  
 [<span data-ttu-id="a50e4-126">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="a50e4-126">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
