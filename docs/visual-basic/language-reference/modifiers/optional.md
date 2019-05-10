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
ms.openlocfilehash: 40605d4843bfccf9d2819b3ec6f2ef65f9e9cf9a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64661321"
---
# <a name="optional-visual-basic"></a><span data-ttu-id="859ee-102">İsteğe Bağlı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="859ee-102">Optional (Visual Basic)</span></span>
<span data-ttu-id="859ee-103">Yordam çağrıldığında bir yordam bağımsız değişkeninin atlanabileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="859ee-103">Specifies that a procedure argument can be omitted when the procedure is called.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="859ee-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="859ee-104">Remarks</span></span>  
 <span data-ttu-id="859ee-105">İsteğe bağlı her parametre için bir sabit ifade bu parametrenin varsayılan değeri olarak belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="859ee-105">For each optional parameter, you must specify a constant expression as the default value of that parameter.</span></span> <span data-ttu-id="859ee-106">İfade değerlendirme sonucu [hiçbir şey](../../../visual-basic/language-reference/nothing.md), değer veri türünün varsayılan değeri, parametrenin varsayılan değeri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="859ee-106">If the expression evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), the default value of the value data type is used as the default value of the parameter.</span></span>  
  
 <span data-ttu-id="859ee-107">Parametre listesi isteğe bağlı bir parametre içeriyorsa, onu takip eden her parametre de isteğe bağlı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="859ee-107">If the parameter list contains an optional parameter, every parameter that follows it must also be optional.</span></span>  
  
 <span data-ttu-id="859ee-108">`Optional` Bu bağlamda değiştirici kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="859ee-108">The `Optional` modifier can be used in these contexts:</span></span>  
  
- [<span data-ttu-id="859ee-109">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="859ee-109">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
- [<span data-ttu-id="859ee-110">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="859ee-110">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
- [<span data-ttu-id="859ee-111">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="859ee-111">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
- [<span data-ttu-id="859ee-112">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="859ee-112">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
> [!NOTE]
>  <span data-ttu-id="859ee-113">İsteğe bağlı parametrelerle veya parametresiz bir yordamı çağrılırken, konuma veya ada göre bağımsız değişkenler geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="859ee-113">When calling a procedure with or without optional parameters, you can pass arguments by position or by name.</span></span> <span data-ttu-id="859ee-114">Daha fazla bilgi için [geçirmeden bağımsız değişkenleri konuma ve ada göre](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md).</span><span class="sxs-lookup"><span data-stu-id="859ee-114">For more information, see [Passing Arguments by Position and by Name](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="859ee-115">İsteğe bağlı parametreler içeren bir yordamı aşırı yükleme kullanarak da tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="859ee-115">You can also define a procedure with optional parameters by using overloading.</span></span> <span data-ttu-id="859ee-116">İsteğe bağlı bir parametre varsa, iki aşırı yüklenmiş yordamı, bir parametreyi kabul eden ve sürümleri olmayan bir tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="859ee-116">If you have one optional parameter, you can define two overloaded versions of the procedure, one that accepts the parameter and one that doesn’t.</span></span> <span data-ttu-id="859ee-117">Daha fazla bilgi için [yordam aşırı yüklemesi](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="859ee-117">For more information, see [Procedure Overloading](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="859ee-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="859ee-118">Example</span></span>  
 <span data-ttu-id="859ee-119">Aşağıdaki örnek, bir isteğe bağlı parametresi olan bir yordam tanımlar.</span><span class="sxs-lookup"><span data-stu-id="859ee-119">The following example defines a procedure that has an optional parameter.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="859ee-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="859ee-120">Example</span></span>  
 <span data-ttu-id="859ee-121">Aşağıdaki örnek, ada göre geçirilen bağımsız değişkenler ve konuma göre geçirilen bağımsız değişkenler ile bir yordam çağırma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="859ee-121">The following example demonstrates how to call a procedure with arguments passed by position and with arguments passed by name.</span></span> <span data-ttu-id="859ee-122">Yordamı, iki isteğe bağlı parametreye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="859ee-122">The procedure has two optional parameters.</span></span>  
  
 [!code-vb[VbVbalrKeywords#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class8.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="859ee-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="859ee-123">See also</span></span>

- [<span data-ttu-id="859ee-124">Parametre Listesi</span><span class="sxs-lookup"><span data-stu-id="859ee-124">Parameter List</span></span>](../../../visual-basic/language-reference/statements/parameter-list.md)
- [<span data-ttu-id="859ee-125">İsteğe Bağlı Parametreler</span><span class="sxs-lookup"><span data-stu-id="859ee-125">Optional Parameters</span></span>](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)
- [<span data-ttu-id="859ee-126">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="859ee-126">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
