---
title: "break (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- break
- break_CSharpKeyword
helpviewer_keywords: break keyword [C#]
ms.assetid: be2571ed-efb0-4965-b122-81e5b09db0b9
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b533d325be41683ed6f56e9e63b3c11ddde9cb17
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="break-c-reference"></a><span data-ttu-id="515a8-102">break (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="515a8-102">break (C# Reference)</span></span>
<span data-ttu-id="515a8-103">`break` Açıklamayı sonlandıran en yakın kapsayan bir döngü veya [geçiş](../../../csharp/language-reference/keywords/switch.md) göründüğü deyimi.</span><span class="sxs-lookup"><span data-stu-id="515a8-103">The `break` statement terminates the closest enclosing loop or [switch](../../../csharp/language-reference/keywords/switch.md) statement in which it appears.</span></span> <span data-ttu-id="515a8-104">Denetim sonlandırılan deyimi aşağıdaki deyim varsa geçirilir.</span><span class="sxs-lookup"><span data-stu-id="515a8-104">Control is passed to the statement that follows the terminated statement, if any.</span></span>  
  
## <a name="example"></a><span data-ttu-id="515a8-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="515a8-105">Example</span></span>  
 <span data-ttu-id="515a8-106">Bu örnekte, koşullu ifade 1'den 100'e saymak için beklenen sayaç içerir; Ancak, `break` açıklamayı sonlandıran döngü sonra 4 sayar.</span><span class="sxs-lookup"><span data-stu-id="515a8-106">In this example, the conditional statement contains a counter that is supposed to count from 1 to 100; however, the `break` statement terminates the loop after 4 counts.</span></span>  
  
 [!code-csharp[csrefKeywordsJump#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/break_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="515a8-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="515a8-107">Example</span></span>  
 <span data-ttu-id="515a8-108">Bu örnekte, `break` deyimi dışında bir iç iç içe geçmiş döngüsünü kesmek ve denetim için dış döngü döndürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="515a8-108">In this example, the `break` statement is used to break out of an inner nested loop, and return control to the outer loop.</span></span>  
  
 [!code-csharp[csrefKeywordsJump#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/break_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="515a8-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="515a8-109">Example</span></span>  
 <span data-ttu-id="515a8-110">Bu örnek kullanımını gösteren `break` içinde bir [geçiş](../../../csharp/language-reference/keywords/switch.md) deyimi.</span><span class="sxs-lookup"><span data-stu-id="515a8-110">This example demonstrates the use of `break` in a [switch](../../../csharp/language-reference/keywords/switch.md) statement.</span></span>  
  
 [!code-csharp[csrefKeywordsJump#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/break_3.cs)]  
  
 <span data-ttu-id="515a8-111">Girerseniz `4`, çıktı aşağıdaki gibi olur:</span><span class="sxs-lookup"><span data-stu-id="515a8-111">If you entered `4`, the output would be:</span></span>  
  
```  
Enter your selection (1, 2, or 3): 4  
Sorry, invalid selection.  
```  
  
## <a name="c-language-specification"></a><span data-ttu-id="515a8-112">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="515a8-112">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="515a8-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="515a8-113">See Also</span></span>  
 [<span data-ttu-id="515a8-114">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="515a8-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="515a8-115">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="515a8-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="515a8-116">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="515a8-116">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="515a8-117">geçiş</span><span class="sxs-lookup"><span data-stu-id="515a8-117">switch</span></span>](../../../csharp/language-reference/keywords/switch.md)  
 [<span data-ttu-id="515a8-118">Atlama deyimleri</span><span class="sxs-lookup"><span data-stu-id="515a8-118">Jump Statements</span></span>](../../../csharp/language-reference/keywords/jump-statements.md)  
 [<span data-ttu-id="515a8-119">Yineleme deyimleri</span><span class="sxs-lookup"><span data-stu-id="515a8-119">Iteration Statements</span></span>](../../../csharp/language-reference/keywords/iteration-statements.md)
