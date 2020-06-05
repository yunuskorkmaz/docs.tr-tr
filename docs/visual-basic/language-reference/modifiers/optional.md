---
title: İsteğe Bağlı
ms.date: 07/20/2015
f1_keywords:
- vb.Optional
- vb.optional
helpviewer_keywords:
- Optional keyword [Visual Basic], contexts
- Optional keyword [Visual Basic]
ms.assetid: 4571ce88-a539-4115-b230-54eb277c6aa7
ms.openlocfilehash: c46d06dba61158d7362d736731161be306af3f10
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392151"
---
# <a name="optional-visual-basic"></a><span data-ttu-id="285e1-102">İsteğe Bağlı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="285e1-102">Optional (Visual Basic)</span></span>

<span data-ttu-id="285e1-103">Yordam çağrıldığında bir yordam bağımsız değişkeninin atlanabileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="285e1-103">Specifies that a procedure argument can be omitted when the procedure is called.</span></span>

## <a name="remarks"></a><span data-ttu-id="285e1-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="285e1-104">Remarks</span></span>

<span data-ttu-id="285e1-105">Her isteğe bağlı parametre için, bu parametrenin varsayılan değeri olarak bir sabit ifade belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="285e1-105">For each optional parameter, you must specify a constant expression as the default value of that parameter.</span></span> <span data-ttu-id="285e1-106">İfade [Nothing](../nothing.md)olarak değerlendirilirse, değer veri türünün varsayılan değeri parametrenin varsayılan değeri olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="285e1-106">If the expression evaluates to [Nothing](../nothing.md), the default value of the value data type is used as the default value of the parameter.</span></span>

<span data-ttu-id="285e1-107">Parametre listesi isteğe bağlı bir parametre içeriyorsa, izleyen her parametrenin de isteğe bağlı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="285e1-107">If the parameter list contains an optional parameter, every parameter that follows it must also be optional.</span></span>

<span data-ttu-id="285e1-108">`Optional`Değiştirici şu bağlamlarda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="285e1-108">The `Optional` modifier can be used in these contexts:</span></span>

- [<span data-ttu-id="285e1-109">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="285e1-109">Declare Statement</span></span>](../statements/declare-statement.md)

- [<span data-ttu-id="285e1-110">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="285e1-110">Function Statement</span></span>](../statements/function-statement.md)

- [<span data-ttu-id="285e1-111">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="285e1-111">Property Statement</span></span>](../statements/property-statement.md)

- [<span data-ttu-id="285e1-112">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="285e1-112">Sub Statement</span></span>](../statements/sub-statement.md)

> [!NOTE]
> <span data-ttu-id="285e1-113">İsteğe bağlı parametreleri olan veya içermeyen bir yordamı çağırırken bağımsız değişkenleri konuma veya ada göre geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="285e1-113">When calling a procedure with or without optional parameters, you can pass arguments by position or by name.</span></span> <span data-ttu-id="285e1-114">Daha fazla bilgi için bkz. [bağımsız değişkenleri konuma ve ada göre geçirme](../../programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md).</span><span class="sxs-lookup"><span data-stu-id="285e1-114">For more information, see [Passing Arguments by Position and by Name](../../programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md).</span></span>

> [!NOTE]
> <span data-ttu-id="285e1-115">Ayrıca, aşırı yükleme kullanarak isteğe bağlı parametrelerle bir yordam tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="285e1-115">You can also define a procedure with optional parameters by using overloading.</span></span> <span data-ttu-id="285e1-116">İsteğe bağlı bir parametreye sahipseniz, yordamın parametresini kabul eden bir tane olan biri olan iki aşırı yüklenmiş sürümü tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="285e1-116">If you have one optional parameter, you can define two overloaded versions of the procedure, one that accepts the parameter and one that doesn’t.</span></span> <span data-ttu-id="285e1-117">Daha fazla bilgi için bkz. [yordam aşırı yüklemesi](../../programming-guide/language-features/procedures/procedure-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="285e1-117">For more information, see [Procedure Overloading](../../programming-guide/language-features/procedures/procedure-overloading.md).</span></span>

## <a name="example"></a><span data-ttu-id="285e1-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="285e1-118">Example</span></span>

<span data-ttu-id="285e1-119">Aşağıdaki örnek, isteğe bağlı parametresine sahip bir yordamı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="285e1-119">The following example defines a procedure that has an optional parameter.</span></span>

```vb
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

## <a name="example"></a><span data-ttu-id="285e1-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="285e1-120">Example</span></span>

<span data-ttu-id="285e1-121">Aşağıdaki örnek, konumundan geçirilen bağımsız değişkenlerle ve ad ile geçirilen bağımsız değişkenlerle bir yordamın nasıl çağrılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="285e1-121">The following example demonstrates how to call a procedure with arguments passed by position and with arguments passed by name.</span></span> <span data-ttu-id="285e1-122">Yordamda iki isteğe bağlı parametre vardır.</span><span class="sxs-lookup"><span data-stu-id="285e1-122">The procedure has two optional parameters.</span></span>

[!code-vb[VbVbalrKeywords#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class8.vb#21)]

## <a name="see-also"></a><span data-ttu-id="285e1-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="285e1-123">See also</span></span>

- [<span data-ttu-id="285e1-124">Parametre Listesi</span><span class="sxs-lookup"><span data-stu-id="285e1-124">Parameter List</span></span>](../statements/parameter-list.md)
- [<span data-ttu-id="285e1-125">İsteğe Bağlı Parametreler</span><span class="sxs-lookup"><span data-stu-id="285e1-125">Optional Parameters</span></span>](../../programming-guide/language-features/procedures/optional-parameters.md)
- [<span data-ttu-id="285e1-126">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="285e1-126">Keywords</span></span>](../keywords/index.md)
