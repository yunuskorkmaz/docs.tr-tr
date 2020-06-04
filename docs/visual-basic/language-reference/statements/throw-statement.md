---
title: Throw Deyimi
ms.date: 07/20/2015
f1_keywords:
- vb.Throw
helpviewer_keywords:
- structured exception handling, throw statements
- try-catch exception handling, throw statements
- throw statement [Visual Basic], about throw statements
- throwing exceptions, throw statement
- exception handling, throw statement
- On Error statement [Visual Basic], throwing exceptions
- throwing exceptions
- exception handling, unstructured
- throw statement [Visual Basic]
ms.assetid: a6e07406-5c8a-4498-87a2-8339f3651d62
ms.openlocfilehash: 95572b1739490e90f53da6b6ec283bfb532c46d3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404141"
---
# <a name="throw-statement-visual-basic"></a><span data-ttu-id="06ad7-102">Throw Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="06ad7-102">Throw Statement (Visual Basic)</span></span>

<span data-ttu-id="06ad7-103">Bir yordam içinde özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="06ad7-103">Throws an exception within a procedure.</span></span>

## <a name="syntax"></a><span data-ttu-id="06ad7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="06ad7-104">Syntax</span></span>

```vb
Throw [ expression ]
```

## <a name="part"></a><span data-ttu-id="06ad7-105">Bölüm</span><span class="sxs-lookup"><span data-stu-id="06ad7-105">Part</span></span>

`expression`\
<span data-ttu-id="06ad7-106">Oluşturulacak özel durum hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="06ad7-106">Provides information about the exception to be thrown.</span></span> <span data-ttu-id="06ad7-107">Bir bildirimde bulunduğunda isteğe bağlı `Catch` , aksi takdirde gereklidir.</span><span class="sxs-lookup"><span data-stu-id="06ad7-107">Optional when residing in a `Catch` statement, otherwise required.</span></span>

## <a name="remarks"></a><span data-ttu-id="06ad7-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="06ad7-108">Remarks</span></span>

<span data-ttu-id="06ad7-109">`Throw`Bu ifade, yapılandırılmış özel durum işleme kodu ( `Try` ... `Catch` ) ile işleyebileceğiniz bir özel durum oluşturur. ...`Finally`) ya da yapılandırılmamış özel durum işleme kodu ( `On Error GoTo` ).</span><span class="sxs-lookup"><span data-stu-id="06ad7-109">The `Throw` statement throws an exception that you can handle with structured exception-handling code (`Try`...`Catch`...`Finally`) or unstructured exception-handling code (`On Error GoTo`).</span></span> <span data-ttu-id="06ad7-110">`Throw`Bu ifadeyi, uygun özel durum işleme kodunu bulana kadar çağrı yığınını Visual Basic, kodunuzun içindeki hataları yakalamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="06ad7-110">You can use the `Throw` statement to trap errors within your code because Visual Basic moves up the call stack until it finds the appropriate exception-handling code.</span></span>

<span data-ttu-id="06ad7-111">`Throw`İfadesi olmayan bir deyim yalnızca bir `Catch` deyimde kullanılabilir, bu durumda deyim deyim tarafından işlenmekte olan özel durumu yeniden oluşturur `Catch` .</span><span class="sxs-lookup"><span data-stu-id="06ad7-111">A `Throw` statement with no expression can only be used in a `Catch` statement, in which case the statement rethrows the exception currently being handled by the `Catch` statement.</span></span>

<span data-ttu-id="06ad7-112">`Throw`İfade, özel durum için çağrı yığınını sıfırlar `expression` .</span><span class="sxs-lookup"><span data-stu-id="06ad7-112">The `Throw` statement resets the call stack for the `expression` exception.</span></span> <span data-ttu-id="06ad7-113">`expression`Sağlanmazsa, çağrı yığını değişmeden bırakılır.</span><span class="sxs-lookup"><span data-stu-id="06ad7-113">If `expression` is not provided, the call stack is left unchanged.</span></span> <span data-ttu-id="06ad7-114">Özel durum için çağrı yığınına özelliği aracılığıyla erişebilirsiniz <xref:System.Exception.StackTrace%2A> .</span><span class="sxs-lookup"><span data-stu-id="06ad7-114">You can access the call stack for the exception through the <xref:System.Exception.StackTrace%2A> property.</span></span>

## <a name="example"></a><span data-ttu-id="06ad7-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="06ad7-115">Example</span></span>

<span data-ttu-id="06ad7-116">Aşağıdaki kod `Throw` bir özel durum oluşturmak için ifadesini kullanır:</span><span class="sxs-lookup"><span data-stu-id="06ad7-116">The following code uses the `Throw` statement to throw an exception:</span></span>

[!code-vb[VbVbalrStatements#84](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#84)]

## <a name="see-also"></a><span data-ttu-id="06ad7-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="06ad7-117">See also</span></span>

- [<span data-ttu-id="06ad7-118">Try...Catch...Finally Deyimi</span><span class="sxs-lookup"><span data-stu-id="06ad7-118">Try...Catch...Finally Statement</span></span>](try-catch-finally-statement.md)
- [<span data-ttu-id="06ad7-119">On Error Deyimi</span><span class="sxs-lookup"><span data-stu-id="06ad7-119">On Error Statement</span></span>](on-error-statement.md)
