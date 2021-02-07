---
description: 'Hakkında daha fazla bilgi: Isteğe bağlı (Visual Basic)'
title: İsteğe Bağlı
ms.date: 07/20/2015
f1_keywords:
- vb.Optional
- vb.optional
helpviewer_keywords:
- Optional keyword [Visual Basic], contexts
- Optional keyword [Visual Basic]
ms.assetid: 4571ce88-a539-4115-b230-54eb277c6aa7
ms.openlocfilehash: d9a61371364d87745203363dbc0a641cec9660a2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99666088"
---
# <a name="optional-visual-basic"></a><span data-ttu-id="5a377-103">İsteğe Bağlı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5a377-103">Optional (Visual Basic)</span></span>

<span data-ttu-id="5a377-104">Yordam çağrıldığında bir yordam bağımsız değişkeninin atlanabileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5a377-104">Specifies that a procedure argument can be omitted when the procedure is called.</span></span>

## <a name="remarks"></a><span data-ttu-id="5a377-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5a377-105">Remarks</span></span>

<span data-ttu-id="5a377-106">Her isteğe bağlı parametre için, bu parametrenin varsayılan değeri olarak bir sabit ifade belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="5a377-106">For each optional parameter, you must specify a constant expression as the default value of that parameter.</span></span> <span data-ttu-id="5a377-107">İfade [Nothing](../nothing.md)olarak değerlendirilirse, değer veri türünün varsayılan değeri parametrenin varsayılan değeri olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5a377-107">If the expression evaluates to [Nothing](../nothing.md), the default value of the value data type is used as the default value of the parameter.</span></span>

<span data-ttu-id="5a377-108">Parametre listesi isteğe bağlı bir parametre içeriyorsa, izleyen her parametrenin de isteğe bağlı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="5a377-108">If the parameter list contains an optional parameter, every parameter that follows it must also be optional.</span></span>

<span data-ttu-id="5a377-109">`Optional`Değiştirici şu bağlamlarda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="5a377-109">The `Optional` modifier can be used in these contexts:</span></span>

- [<span data-ttu-id="5a377-110">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="5a377-110">Declare Statement</span></span>](../statements/declare-statement.md)

- [<span data-ttu-id="5a377-111">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="5a377-111">Function Statement</span></span>](../statements/function-statement.md)

- [<span data-ttu-id="5a377-112">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="5a377-112">Property Statement</span></span>](../statements/property-statement.md)

- [<span data-ttu-id="5a377-113">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="5a377-113">Sub Statement</span></span>](../statements/sub-statement.md)

> [!NOTE]
> <span data-ttu-id="5a377-114">İsteğe bağlı parametreleri olan veya içermeyen bir yordamı çağırırken bağımsız değişkenleri konuma veya ada göre geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5a377-114">When calling a procedure with or without optional parameters, you can pass arguments by position or by name.</span></span> <span data-ttu-id="5a377-115">Daha fazla bilgi için bkz. [bağımsız değişkenleri konuma ve ada göre geçirme](../../programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md).</span><span class="sxs-lookup"><span data-stu-id="5a377-115">For more information, see [Passing Arguments by Position and by Name](../../programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md).</span></span>

> [!NOTE]
> <span data-ttu-id="5a377-116">Ayrıca, aşırı yükleme kullanarak isteğe bağlı parametrelerle bir yordam tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5a377-116">You can also define a procedure with optional parameters by using overloading.</span></span> <span data-ttu-id="5a377-117">İsteğe bağlı bir parametreye sahipseniz, yordamın parametresini kabul eden bir tane olan biri olan iki aşırı yüklenmiş sürümü tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5a377-117">If you have one optional parameter, you can define two overloaded versions of the procedure, one that accepts the parameter and one that doesn’t.</span></span> <span data-ttu-id="5a377-118">Daha fazla bilgi için bkz. [yordam aşırı yüklemesi](../../programming-guide/language-features/procedures/procedure-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="5a377-118">For more information, see [Procedure Overloading](../../programming-guide/language-features/procedures/procedure-overloading.md).</span></span>

## <a name="example"></a><span data-ttu-id="5a377-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="5a377-119">Example</span></span>

<span data-ttu-id="5a377-120">Aşağıdaki örnek, isteğe bağlı parametresine sahip bir yordamı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5a377-120">The following example defines a procedure that has an optional parameter.</span></span>

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

## <a name="example"></a><span data-ttu-id="5a377-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="5a377-121">Example</span></span>

<span data-ttu-id="5a377-122">Aşağıdaki örnek, konumundan geçirilen bağımsız değişkenlerle ve ad ile geçirilen bağımsız değişkenlerle bir yordamın nasıl çağrılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5a377-122">The following example demonstrates how to call a procedure with arguments passed by position and with arguments passed by name.</span></span> <span data-ttu-id="5a377-123">Yordamda iki isteğe bağlı parametre vardır.</span><span class="sxs-lookup"><span data-stu-id="5a377-123">The procedure has two optional parameters.</span></span>

[!code-vb[VbVbalrKeywords#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class8.vb#21)]

## <a name="see-also"></a><span data-ttu-id="5a377-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5a377-124">See also</span></span>

- [<span data-ttu-id="5a377-125">Parametre Listesi</span><span class="sxs-lookup"><span data-stu-id="5a377-125">Parameter List</span></span>](../statements/parameter-list.md)
- [<span data-ttu-id="5a377-126">İsteğe Bağlı Parametreler</span><span class="sxs-lookup"><span data-stu-id="5a377-126">Optional Parameters</span></span>](../../programming-guide/language-features/procedures/optional-parameters.md)
- [<span data-ttu-id="5a377-127">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="5a377-127">Keywords</span></span>](../keywords/index.md)
