---
title: "İsteğe Bağlı (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Optional
- vb.optional
helpviewer_keywords:
- Optional keyword [Visual Basic], contexts
- Optional keyword [Visual Basic]
ms.assetid: 4571ce88-a539-4115-b230-54eb277c6aa7
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3aa01c2c1ae731c8fe00fdee24521760db69e624
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="optional-visual-basic"></a><span data-ttu-id="608f2-102">İsteğe Bağlı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="608f2-102">Optional (Visual Basic)</span></span>
<span data-ttu-id="608f2-103">Yordam çağrıldığında bir yordam bağımsız değişkenini atlanabilir belirtir.</span><span class="sxs-lookup"><span data-stu-id="608f2-103">Specifies that a procedure argument can be omitted when the procedure is called.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="608f2-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="608f2-104">Remarks</span></span>  
 <span data-ttu-id="608f2-105">İsteğe bağlı her parametre için bir sabit ifadesine bu parametrenin varsayılan değeri olarak belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="608f2-105">For each optional parameter, you must specify a constant expression as the default value of that parameter.</span></span> <span data-ttu-id="608f2-106">İfade değerlendirilirse [hiçbir şey](../../../visual-basic/language-reference/nothing.md), değer veri türünün varsayılan değeri parametresinin varsayılan değeri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="608f2-106">If the expression evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), the default value of the value data type is used as the default value of the parameter.</span></span>  
  
 <span data-ttu-id="608f2-107">Parametre listesi isteğe bağlı bir parametre içeriyorsa, kendisini izleyen her parametre ayrıca isteğe bağlı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="608f2-107">If the parameter list contains an optional parameter, every parameter that follows it must also be optional.</span></span>  
  
 <span data-ttu-id="608f2-108">`Optional` Değiştiricisi bu bağlamlarında kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="608f2-108">The `Optional` modifier can be used in these contexts:</span></span>  
  
-   [<span data-ttu-id="608f2-109">Declare deyimi</span><span class="sxs-lookup"><span data-stu-id="608f2-109">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
-   [<span data-ttu-id="608f2-110">Function deyimi</span><span class="sxs-lookup"><span data-stu-id="608f2-110">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
-   [<span data-ttu-id="608f2-111">Property deyimi</span><span class="sxs-lookup"><span data-stu-id="608f2-111">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
-   [<span data-ttu-id="608f2-112">Sub deyimi</span><span class="sxs-lookup"><span data-stu-id="608f2-112">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
> [!NOTE]
>  <span data-ttu-id="608f2-113">İle veya isteğe bağlı parametreler olmadan bir yordamı çağrılırken, konuma göre veya ada göre bağımsız değişkenler geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="608f2-113">When calling a procedure with or without optional parameters, you can pass arguments by position or by name.</span></span> <span data-ttu-id="608f2-114">Daha fazla bilgi için bkz: [geçirme bağımsız değişkenleri konuma ve ada göre](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md).</span><span class="sxs-lookup"><span data-stu-id="608f2-114">For more information, see [Passing Arguments by Position and by Name](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="608f2-115">İsteğe bağlı parametreleri olan bir yordamı aşırı yükleme kullanarak da tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="608f2-115">You can also define a procedure with optional parameters by using overloading.</span></span> <span data-ttu-id="608f2-116">İsteğe bağlı bir parametre varsa, iki aşırı yüklenmiş yordamı, bir parametre kabul eden ve sürümleri olmayan bir tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="608f2-116">If you have one optional parameter, you can define two overloaded versions of the procedure, one that accepts the parameter and one that doesn’t.</span></span> <span data-ttu-id="608f2-117">Daha fazla bilgi için bkz: [yordam aşırı yüklemesi](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="608f2-117">For more information, see [Procedure Overloading](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="608f2-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="608f2-118">Example</span></span>  
 <span data-ttu-id="608f2-119">Aşağıdaki örnek, isteğe bağlı bir parametre olan bir yordam tanımlar.</span><span class="sxs-lookup"><span data-stu-id="608f2-119">The following example defines a procedure that has an optional parameter.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="608f2-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="608f2-120">Example</span></span>  
 <span data-ttu-id="608f2-121">Aşağıdaki örnek, konuma göre geçirilen bağımsız değişkenlerle ve ada göre geçirilen bağımsız değişkenlerle bir yordam çağırma gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="608f2-121">The following example demonstrates how to call a procedure with arguments passed by position and with arguments passed by name.</span></span> <span data-ttu-id="608f2-122">Yordamın iki isteğe bağlı parametreye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="608f2-122">The procedure has two optional parameters.</span></span>  
  
 [!code-vb[VbVbalrKeywords#21](../../../visual-basic/language-reference/codesnippet/VisualBasic/optional_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="608f2-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="608f2-123">See Also</span></span>  
 [<span data-ttu-id="608f2-124">Parametre listesi</span><span class="sxs-lookup"><span data-stu-id="608f2-124">Parameter List</span></span>](../../../visual-basic/language-reference/statements/parameter-list.md)  
 [<span data-ttu-id="608f2-125">İsteğe bağlı parametreler</span><span class="sxs-lookup"><span data-stu-id="608f2-125">Optional Parameters</span></span>](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)  
 [<span data-ttu-id="608f2-126">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="608f2-126">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
