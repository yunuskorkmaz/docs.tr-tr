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
ms.openlocfilehash: cfa53b3585846da25711739fb7af4bde21746b29
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33602859"
---
# <a name="throw-statement-visual-basic"></a><span data-ttu-id="62240-102">Throw Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="62240-102">Throw Statement (Visual Basic)</span></span>
<span data-ttu-id="62240-103">Bir yordam içinde bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="62240-103">Throws an exception within a procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62240-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="62240-104">Syntax</span></span>  
  
```  
Throw [ expression ]  
```  
  
## <a name="part"></a><span data-ttu-id="62240-105">Bölümü</span><span class="sxs-lookup"><span data-stu-id="62240-105">Part</span></span>  
 `expression`  
 <span data-ttu-id="62240-106">Özel durum hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="62240-106">Provides information about the exception to be thrown.</span></span> <span data-ttu-id="62240-107">Bulunan, isteğe bağlı bir `Catch` deyimi, aksi takdirde gerekli.</span><span class="sxs-lookup"><span data-stu-id="62240-107">Optional when residing in a `Catch` statement, otherwise required.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="62240-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="62240-108">Remarks</span></span>  
 <span data-ttu-id="62240-109">`Throw` Deyimi ile yapılandırılmış özel durum işleme kod işleyebilecek bir özel durum oluşturur (`Try`... `Catch`... `Finally`) veya yapılandırılmamış özel durum işleme kod (`On Error GoTo`).</span><span class="sxs-lookup"><span data-stu-id="62240-109">The `Throw` statement throws an exception that you can handle with structured exception-handling code (`Try`...`Catch`...`Finally`) or unstructured exception-handling code (`On Error GoTo`).</span></span> <span data-ttu-id="62240-110">Kullanabileceğiniz `Throw` uygun özel durum işleme kodu bulana kadar Visual Basic çağrı yığınına taşıdığı için kodunuzu içindeki hataları yakalamak için deyimi.</span><span class="sxs-lookup"><span data-stu-id="62240-110">You can use the `Throw` statement to trap errors within your code because Visual Basic moves up the call stack until it finds the appropriate exception-handling code.</span></span>  
  
 <span data-ttu-id="62240-111">A `Throw` hiçbir ifade deyimiyle yalnızca kullanılabilir bir `Catch` durumda deyim şu anda tarafından işlenen özel durum bloğunu deyimi `Catch` deyimi.</span><span class="sxs-lookup"><span data-stu-id="62240-111">A `Throw` statement with no expression can only be used in a `Catch` statement, in which case the statement rethrows the exception currently being handled by the `Catch` statement.</span></span>  
  
 <span data-ttu-id="62240-112">`Throw` Deyimi için çağrı yığını sıfırlar `expression` özel durum.</span><span class="sxs-lookup"><span data-stu-id="62240-112">The `Throw` statement resets the call stack for the `expression` exception.</span></span> <span data-ttu-id="62240-113">Varsa `expression` sağlanmaz, çağrı yığını sol haliyle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="62240-113">If `expression` is not provided, the call stack is left unchanged.</span></span> <span data-ttu-id="62240-114">Çağrı yığını ile özel durum için erişim <xref:System.Exception.StackTrace%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="62240-114">You can access the call stack for the exception through the <xref:System.Exception.StackTrace%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="62240-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="62240-115">Example</span></span>  
 <span data-ttu-id="62240-116">Aşağıdaki kod `Throw` deyimi bir özel durum:</span><span class="sxs-lookup"><span data-stu-id="62240-116">The following code uses the `Throw` statement to throw an exception:</span></span>  
  
 [!code-vb[VbVbalrStatements#84](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/throw-statement_1.vb)]  
  
## <a name="requirements"></a><span data-ttu-id="62240-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="62240-117">Requirements</span></span>  
 <span data-ttu-id="62240-118">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="62240-118">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="62240-119">**Modülü:** `Interaction`</span><span class="sxs-lookup"><span data-stu-id="62240-119">**Module:** `Interaction`</span></span>  
  
 <span data-ttu-id="62240-120">**Derleme:** Visual Basic çalışma zamanı kitaplığı (Microsoft.VisualBasic.dll içinde)</span><span class="sxs-lookup"><span data-stu-id="62240-120">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62240-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="62240-121">See Also</span></span>  
 [<span data-ttu-id="62240-122">Try...Catch...Finally Deyimi</span><span class="sxs-lookup"><span data-stu-id="62240-122">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [<span data-ttu-id="62240-123">On Error Deyimi</span><span class="sxs-lookup"><span data-stu-id="62240-123">On Error Statement</span></span>](../../../visual-basic/language-reference/statements/on-error-statement.md)
