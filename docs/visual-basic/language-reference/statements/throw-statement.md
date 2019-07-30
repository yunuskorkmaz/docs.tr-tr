---
title: Throw Deyimi (Visual Basic)
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
ms.openlocfilehash: a6d10982cf199e9285334e0d72e6622275d51b4d
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68626200"
---
# <a name="throw-statement-visual-basic"></a><span data-ttu-id="7432e-102">Throw Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7432e-102">Throw Statement (Visual Basic)</span></span>
<span data-ttu-id="7432e-103">Bir yordam içinde özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7432e-103">Throws an exception within a procedure.</span></span>

## <a name="syntax"></a><span data-ttu-id="7432e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7432e-104">Syntax</span></span>

```vb
Throw [ expression ]
```

## <a name="part"></a><span data-ttu-id="7432e-105">Bölümüyle</span><span class="sxs-lookup"><span data-stu-id="7432e-105">Part</span></span>
 <span data-ttu-id="7432e-106">`expression`Oluşturulacak özel durum hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="7432e-106">`expression` Provides information about the exception to be thrown.</span></span> <span data-ttu-id="7432e-107">Bir `Catch` bildirimde bulunduğunda isteğe bağlı, aksi takdirde gereklidir.</span><span class="sxs-lookup"><span data-stu-id="7432e-107">Optional when residing in a `Catch` statement, otherwise required.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="7432e-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7432e-108">Remarks</span></span>
 <span data-ttu-id="7432e-109">Bu `Throw` ifade, yapılandırılmış özel durum işleme kodu (`Try`...) ile işleyebileceğiniz bir özel durum oluşturur. `Catch`... ) veya yapılandırılmamış özel durum işleme kodu (`On Error GoTo`). `Finally`</span><span class="sxs-lookup"><span data-stu-id="7432e-109">The `Throw` statement throws an exception that you can handle with structured exception-handling code (`Try`...`Catch`...`Finally`) or unstructured exception-handling code (`On Error GoTo`).</span></span> <span data-ttu-id="7432e-110">Bu ifadeyi, `Throw` uygun özel durum işleme kodunu bulana kadar çağrı yığınını Visual Basic, kodunuzun içindeki hataları yakalamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7432e-110">You can use the `Throw` statement to trap errors within your code because Visual Basic moves up the call stack until it finds the appropriate exception-handling code.</span></span>
 
 <span data-ttu-id="7432e-111">İfadesi `Throw` olmayan bir deyim yalnızca bir `Catch` deyimde kullanılabilir, bu durumda deyim deyim tarafından `Catch` işlenmekte olan özel durumu yeniden oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7432e-111">A `Throw` statement with no expression can only be used in a `Catch` statement, in which case the statement rethrows the exception currently being handled by the `Catch` statement.</span></span>

 <span data-ttu-id="7432e-112">İfade, `expression` özel durum için çağrı yığınını sıfırlar. `Throw`</span><span class="sxs-lookup"><span data-stu-id="7432e-112">The `Throw` statement resets the call stack for the `expression` exception.</span></span> <span data-ttu-id="7432e-113">`expression` Sağlanmazsa, çağrı yığını değişmeden bırakılır.</span><span class="sxs-lookup"><span data-stu-id="7432e-113">If `expression` is not provided, the call stack is left unchanged.</span></span> <span data-ttu-id="7432e-114">Özel durum için çağrı yığınına <xref:System.Exception.StackTrace%2A> özelliği aracılığıyla erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7432e-114">You can access the call stack for the exception through the <xref:System.Exception.StackTrace%2A> property.</span></span>

## <a name="example"></a><span data-ttu-id="7432e-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="7432e-115">Example</span></span>
 <span data-ttu-id="7432e-116">Aşağıdaki kod bir özel durum `Throw` oluşturmak için ifadesini kullanır:</span><span class="sxs-lookup"><span data-stu-id="7432e-116">The following code uses the `Throw` statement to throw an exception:</span></span>
 
 [!code-vb[VbVbalrStatements#84](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#84)]

  
## <a name="see-also"></a><span data-ttu-id="7432e-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7432e-117">See also</span></span>

- [<span data-ttu-id="7432e-118">Try...Catch...Finally Deyimi</span><span class="sxs-lookup"><span data-stu-id="7432e-118">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="7432e-119">On Error Deyimi</span><span class="sxs-lookup"><span data-stu-id="7432e-119">On Error Statement</span></span>](../../../visual-basic/language-reference/statements/on-error-statement.md)
