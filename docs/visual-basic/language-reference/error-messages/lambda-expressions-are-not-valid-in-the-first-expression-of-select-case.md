---
description: "Hakkında daha fazla bilgi edinin: BC36635: lambda ifadeleri bir ' Select Case ' deyiminin ilk ifadesinde geçerli değildir"
title: Bir 'Select Case' deyiminin ilk ifadesinde lambda ifadeleri geçerli değildir
ms.date: 07/20/2015
f1_keywords:
- bc36635
- vbc36635
helpviewer_keywords:
- BC36635
ms.assetid: 74609979-9c03-4864-bbce-f588aa2e0917
ms.openlocfilehash: e0c388db7164f6c9f99ba917109593a796f7b23b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795943"
---
# <a name="bc36635-lambda-expressions-are-not-valid-in-the-first-expression-of-a-select-case-statement"></a><span data-ttu-id="1011d-103">BC36635: lambda ifadeleri bir ' Select Case ' deyiminin ilk ifadesinde geçerli değildir</span><span class="sxs-lookup"><span data-stu-id="1011d-103">BC36635: Lambda expressions are not valid in the first expression of a 'Select Case' statement</span></span>

<span data-ttu-id="1011d-104">Bir deyimde test ifadesi için lambda ifadesi kullanamazsınız `Select Case` .</span><span class="sxs-lookup"><span data-stu-id="1011d-104">You cannot use a lambda expression for the test expression in a `Select Case` statement.</span></span> <span data-ttu-id="1011d-105">Lambda ifade tanımları dönüş işlevleri ve bir deyimin test ifadesi bir `Select Case` Öğesel veri türü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1011d-105">Lambda expression definitions return functions, and the test expression of a `Select Case` statement must be an elementary data type.</span></span>

 <span data-ttu-id="1011d-106">Aşağıdaki kod bu hataya neden olur:</span><span class="sxs-lookup"><span data-stu-id="1011d-106">The following code causes this error:</span></span>

```vb
' Select Case (Function(arg) arg Is Nothing)
    ' List of the cases.
' End Select
```

 <span data-ttu-id="1011d-107">**Hata kimliği:** BC36635</span><span class="sxs-lookup"><span data-stu-id="1011d-107">**Error ID:** BC36635</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="1011d-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="1011d-108">To correct this error</span></span>

- <span data-ttu-id="1011d-109">Bir bildirim gibi farklı bir koşullu oluşturma sizin için çalışıp çalışmadığını anlamak için kodunuzu inceleyin `If...Then...Else` .</span><span class="sxs-lookup"><span data-stu-id="1011d-109">Examine your code to determine whether a different conditional construction, such as an `If...Then...Else` statement, would work for you.</span></span>

- <span data-ttu-id="1011d-110">Aşağıdaki kodda gösterildiği gibi, işlevini çağırmanız istenebilir:</span><span class="sxs-lookup"><span data-stu-id="1011d-110">You may have intended to call the function, as shown in the following code:</span></span>

```vb
Dim num? As Integer
Select Case ((Function(arg? As Integer) arg Is Nothing)(num))
    ' List of the cases
End Select
```

## <a name="see-also"></a><span data-ttu-id="1011d-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1011d-111">See also</span></span>

- [<span data-ttu-id="1011d-112">Lambda Ifadeleri</span><span class="sxs-lookup"><span data-stu-id="1011d-112">Lambda Expressions</span></span>](../../programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="1011d-113">If...Then...Else Deyimi</span><span class="sxs-lookup"><span data-stu-id="1011d-113">If...Then...Else Statement</span></span>](../statements/if-then-else-statement.md)
- [<span data-ttu-id="1011d-114">Select...Case Deyimi</span><span class="sxs-lookup"><span data-stu-id="1011d-114">Select...Case Statement</span></span>](../statements/select-case-statement.md)
