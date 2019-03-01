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
ms.openlocfilehash: c17adc6df0f8cf94f06547b48a32b2ffb8f303ca
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56973489"
---
# <a name="throw-statement-visual-basic"></a><span data-ttu-id="8bef5-102">Throw Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8bef5-102">Throw Statement (Visual Basic)</span></span>
<span data-ttu-id="8bef5-103">Bir yordam içinde özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8bef5-103">Throws an exception within a procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8bef5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8bef5-104">Syntax</span></span>  
  
```  
Throw [ expression ]  
```  
  
## <a name="part"></a><span data-ttu-id="8bef5-105">Bölümü</span><span class="sxs-lookup"><span data-stu-id="8bef5-105">Part</span></span>  
 `expression`  
 <span data-ttu-id="8bef5-106">Özel durum oluşturulmasına hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="8bef5-106">Provides information about the exception to be thrown.</span></span> <span data-ttu-id="8bef5-107">Bulunan, isteğe bağlı bir `Catch` deyimi, aksi takdirde gereklidir.</span><span class="sxs-lookup"><span data-stu-id="8bef5-107">Optional when residing in a `Catch` statement, otherwise required.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8bef5-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8bef5-108">Remarks</span></span>  
 <span data-ttu-id="8bef5-109">`Throw` Deyimi, yapılandırılmış özel durum işleme kodu ile işleyebilmeniz bir özel durum oluşturur (`Try`... `Catch`... `Finally`) ya da yapılandırılmamış özel durum işleme kodunu (`On Error GoTo`).</span><span class="sxs-lookup"><span data-stu-id="8bef5-109">The `Throw` statement throws an exception that you can handle with structured exception-handling code (`Try`...`Catch`...`Finally`) or unstructured exception-handling code (`On Error GoTo`).</span></span> <span data-ttu-id="8bef5-110">Kullanabileceğiniz `Throw` uygun özel durum işleme kodu bulana kadar Visual Basic çağrı yığınında yukarı taşır. çünkü, kod içindeki hataları yakalamak için deyimi.</span><span class="sxs-lookup"><span data-stu-id="8bef5-110">You can use the `Throw` statement to trap errors within your code because Visual Basic moves up the call stack until it finds the appropriate exception-handling code.</span></span>  
  
 <span data-ttu-id="8bef5-111">A `Throw` herhangi bir ifade deyimi yalnızca kullanılabilir bir `Catch` deyimi, case deyiminde tarafından işlenmekte olan özel durum beklerseniz `Catch` deyimi.</span><span class="sxs-lookup"><span data-stu-id="8bef5-111">A `Throw` statement with no expression can only be used in a `Catch` statement, in which case the statement rethrows the exception currently being handled by the `Catch` statement.</span></span>  
  
 <span data-ttu-id="8bef5-112">`Throw` Deyimi için çağrı yığınını sıfırlar `expression` özel durum.</span><span class="sxs-lookup"><span data-stu-id="8bef5-112">The `Throw` statement resets the call stack for the `expression` exception.</span></span> <span data-ttu-id="8bef5-113">Varsa `expression` sağlanmadı, çağrı yığını sol değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="8bef5-113">If `expression` is not provided, the call stack is left unchanged.</span></span> <span data-ttu-id="8bef5-114">Bir özel durum için çağrı yığınını erişebileceğiniz <xref:System.Exception.StackTrace%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="8bef5-114">You can access the call stack for the exception through the <xref:System.Exception.StackTrace%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8bef5-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="8bef5-115">Example</span></span>  
 <span data-ttu-id="8bef5-116">Aşağıdaki kod `Throw` deyimi bir özel durum:</span><span class="sxs-lookup"><span data-stu-id="8bef5-116">The following code uses the `Throw` statement to throw an exception:</span></span>  
  
 [!code-vb[VbVbalrStatements#84](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#84)]  
  
## <a name="requirements"></a><span data-ttu-id="8bef5-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8bef5-117">Requirements</span></span>  
 <span data-ttu-id="8bef5-118">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="8bef5-118">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="8bef5-119">**Modül:** `Interaction`</span><span class="sxs-lookup"><span data-stu-id="8bef5-119">**Module:** `Interaction`</span></span>  
  
 <span data-ttu-id="8bef5-120">**Derleme:** Visual Basic Çalışma Zamanı Kitaplığı (Microsoft.VisualBasic.dll içinde)</span><span class="sxs-lookup"><span data-stu-id="8bef5-120">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bef5-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8bef5-121">See also</span></span>
- [<span data-ttu-id="8bef5-122">Try...Catch...Finally Deyimi</span><span class="sxs-lookup"><span data-stu-id="8bef5-122">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="8bef5-123">On Error Deyimi</span><span class="sxs-lookup"><span data-stu-id="8bef5-123">On Error Statement</span></span>](../../../visual-basic/language-reference/statements/on-error-statement.md)
