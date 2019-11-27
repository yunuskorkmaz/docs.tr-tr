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
ms.openlocfilehash: 147345990b625e034e651e69b322bc098d0bd8de
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352792"
---
# <a name="throw-statement-visual-basic"></a><span data-ttu-id="2a09f-102">Throw Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2a09f-102">Throw Statement (Visual Basic)</span></span>

<span data-ttu-id="2a09f-103">Bir yordam içinde özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2a09f-103">Throws an exception within a procedure.</span></span>

## <a name="syntax"></a><span data-ttu-id="2a09f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2a09f-104">Syntax</span></span>

```vb
Throw [ expression ]
```

## <a name="part"></a><span data-ttu-id="2a09f-105">Bölümüyle</span><span class="sxs-lookup"><span data-stu-id="2a09f-105">Part</span></span>

`expression`\
<span data-ttu-id="2a09f-106">Oluşturulacak özel durum hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="2a09f-106">Provides information about the exception to be thrown.</span></span> <span data-ttu-id="2a09f-107">`Catch` bildiriminde bulunduğunda isteğe bağlı, aksi takdirde gereklidir.</span><span class="sxs-lookup"><span data-stu-id="2a09f-107">Optional when residing in a `Catch` statement, otherwise required.</span></span>

## <a name="remarks"></a><span data-ttu-id="2a09f-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2a09f-108">Remarks</span></span>

<span data-ttu-id="2a09f-109">`Throw` ifade, yapılandırılmış özel durum işleme kodu (`Try`...`Catch`...`Finally`) veya yapılandırılmamış özel durum işleme kodu (`On Error GoTo`) ile işleyebileceğiniz bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2a09f-109">The `Throw` statement throws an exception that you can handle with structured exception-handling code (`Try`...`Catch`...`Finally`) or unstructured exception-handling code (`On Error GoTo`).</span></span> <span data-ttu-id="2a09f-110">`Throw` deyiminizi, uygun özel durum işleme kodunu bulana kadar Visual Basic çağrı yığınını taşıdığından, kodunuzun içindeki hataları yakalamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2a09f-110">You can use the `Throw` statement to trap errors within your code because Visual Basic moves up the call stack until it finds the appropriate exception-handling code.</span></span>

<span data-ttu-id="2a09f-111">İfadesi olmayan bir `Throw` deyimi yalnızca bir `Catch` deyiminde kullanılabilir, bu durumda deyim `Catch` deyimi tarafından işlenmekte olan özel durumu yeniden oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2a09f-111">A `Throw` statement with no expression can only be used in a `Catch` statement, in which case the statement rethrows the exception currently being handled by the `Catch` statement.</span></span>

<span data-ttu-id="2a09f-112">`Throw` ifade, `expression` özel durumu için çağrı yığınını sıfırlar.</span><span class="sxs-lookup"><span data-stu-id="2a09f-112">The `Throw` statement resets the call stack for the `expression` exception.</span></span> <span data-ttu-id="2a09f-113">`expression` sağlanmazsa, çağrı yığını değişmeden bırakılır.</span><span class="sxs-lookup"><span data-stu-id="2a09f-113">If `expression` is not provided, the call stack is left unchanged.</span></span> <span data-ttu-id="2a09f-114">Özel durum için çağrı yığınına <xref:System.Exception.StackTrace%2A> özelliği aracılığıyla erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2a09f-114">You can access the call stack for the exception through the <xref:System.Exception.StackTrace%2A> property.</span></span>

## <a name="example"></a><span data-ttu-id="2a09f-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="2a09f-115">Example</span></span>

<span data-ttu-id="2a09f-116">Aşağıdaki kod bir özel durum oluşturmak için `Throw` ifadesini kullanır:</span><span class="sxs-lookup"><span data-stu-id="2a09f-116">The following code uses the `Throw` statement to throw an exception:</span></span>

[!code-vb[VbVbalrStatements#84](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#84)]

## <a name="see-also"></a><span data-ttu-id="2a09f-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2a09f-117">See also</span></span>

- [<span data-ttu-id="2a09f-118">Try...Catch...Finally Deyimi</span><span class="sxs-lookup"><span data-stu-id="2a09f-118">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="2a09f-119">On Error Deyimi</span><span class="sxs-lookup"><span data-stu-id="2a09f-119">On Error Statement</span></span>](../../../visual-basic/language-reference/statements/on-error-statement.md)
