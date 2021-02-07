---
description: 'Daha fazla bilgi edinin: throw deyimleri (Visual Basic)'
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
ms.openlocfilehash: b7fa4183b5997e5dac8045502a8eed1afe66fc0d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99740944"
---
# <a name="throw-statement-visual-basic"></a><span data-ttu-id="7cbf1-103">Throw Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7cbf1-103">Throw Statement (Visual Basic)</span></span>

<span data-ttu-id="7cbf1-104">Bir yordam içinde özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7cbf1-104">Throws an exception within a procedure.</span></span>

## <a name="syntax"></a><span data-ttu-id="7cbf1-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="7cbf1-105">Syntax</span></span>

```vb
Throw [ expression ]
```

## <a name="part"></a><span data-ttu-id="7cbf1-106">Bölüm</span><span class="sxs-lookup"><span data-stu-id="7cbf1-106">Part</span></span>

`expression`\
<span data-ttu-id="7cbf1-107">Oluşturulacak özel durum hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="7cbf1-107">Provides information about the exception to be thrown.</span></span> <span data-ttu-id="7cbf1-108">Bir bildirimde bulunduğunda isteğe bağlı `Catch` , aksi takdirde gereklidir.</span><span class="sxs-lookup"><span data-stu-id="7cbf1-108">Optional when residing in a `Catch` statement, otherwise required.</span></span>

## <a name="remarks"></a><span data-ttu-id="7cbf1-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7cbf1-109">Remarks</span></span>

<span data-ttu-id="7cbf1-110">`Throw`Bu ifade, yapılandırılmış özel durum işleme kodu ( `Try` ... `Catch` ) ile işleyebileceğiniz bir özel durum oluşturur. ...`Finally`) ya da yapılandırılmamış özel durum işleme kodu ( `On Error GoTo` ).</span><span class="sxs-lookup"><span data-stu-id="7cbf1-110">The `Throw` statement throws an exception that you can handle with structured exception-handling code (`Try`...`Catch`...`Finally`) or unstructured exception-handling code (`On Error GoTo`).</span></span> <span data-ttu-id="7cbf1-111">`Throw`Bu ifadeyi, uygun özel durum işleme kodunu bulana kadar çağrı yığınını Visual Basic, kodunuzun içindeki hataları yakalamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7cbf1-111">You can use the `Throw` statement to trap errors within your code because Visual Basic moves up the call stack until it finds the appropriate exception-handling code.</span></span>

<span data-ttu-id="7cbf1-112">`Throw`İfadesi olmayan bir deyim yalnızca bir `Catch` deyimde kullanılabilir, bu durumda deyim deyim tarafından işlenmekte olan özel durumu yeniden oluşturur `Catch` .</span><span class="sxs-lookup"><span data-stu-id="7cbf1-112">A `Throw` statement with no expression can only be used in a `Catch` statement, in which case the statement rethrows the exception currently being handled by the `Catch` statement.</span></span>

<span data-ttu-id="7cbf1-113">`Throw`İfade, özel durum için çağrı yığınını sıfırlar `expression` .</span><span class="sxs-lookup"><span data-stu-id="7cbf1-113">The `Throw` statement resets the call stack for the `expression` exception.</span></span> <span data-ttu-id="7cbf1-114">`expression`Sağlanmazsa, çağrı yığını değişmeden bırakılır.</span><span class="sxs-lookup"><span data-stu-id="7cbf1-114">If `expression` is not provided, the call stack is left unchanged.</span></span> <span data-ttu-id="7cbf1-115">Özel durum için çağrı yığınına özelliği aracılığıyla erişebilirsiniz <xref:System.Exception.StackTrace%2A> .</span><span class="sxs-lookup"><span data-stu-id="7cbf1-115">You can access the call stack for the exception through the <xref:System.Exception.StackTrace%2A> property.</span></span>

## <a name="example"></a><span data-ttu-id="7cbf1-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="7cbf1-116">Example</span></span>

<span data-ttu-id="7cbf1-117">Aşağıdaki kod `Throw` bir özel durum oluşturmak için ifadesini kullanır:</span><span class="sxs-lookup"><span data-stu-id="7cbf1-117">The following code uses the `Throw` statement to throw an exception:</span></span>

[!code-vb[VbVbalrStatements#84](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#84)]

## <a name="see-also"></a><span data-ttu-id="7cbf1-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7cbf1-118">See also</span></span>

- [<span data-ttu-id="7cbf1-119">Try...Catch...Finally Deyimi</span><span class="sxs-lookup"><span data-stu-id="7cbf1-119">Try...Catch...Finally Statement</span></span>](try-catch-finally-statement.md)
- [<span data-ttu-id="7cbf1-120">On Error Deyimi</span><span class="sxs-lookup"><span data-stu-id="7cbf1-120">On Error Statement</span></span>](on-error-statement.md)
