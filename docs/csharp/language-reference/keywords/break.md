---
title: break (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- break
- break_CSharpKeyword
helpviewer_keywords:
- break keyword [C#]
ms.assetid: be2571ed-efb0-4965-b122-81e5b09db0b9
ms.openlocfilehash: 0cfe722bfefc1befd8a453f4454b05b3e4a0da76
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33215056"
---
# <a name="break-c-reference"></a><span data-ttu-id="83fea-102">break (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="83fea-102">break (C# Reference)</span></span>
<span data-ttu-id="83fea-103">`break` Açıklamayı sonlandıran en yakın kapsayan bir döngü veya [geçiş](../../../csharp/language-reference/keywords/switch.md) göründüğü deyimi.</span><span class="sxs-lookup"><span data-stu-id="83fea-103">The `break` statement terminates the closest enclosing loop or [switch](../../../csharp/language-reference/keywords/switch.md) statement in which it appears.</span></span> <span data-ttu-id="83fea-104">Denetim sonlandırılan deyimi aşağıdaki deyim varsa geçirilir.</span><span class="sxs-lookup"><span data-stu-id="83fea-104">Control is passed to the statement that follows the terminated statement, if any.</span></span>  
  
## <a name="example"></a><span data-ttu-id="83fea-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="83fea-105">Example</span></span>  
 <span data-ttu-id="83fea-106">Bu örnekte, koşullu ifade 1'den 100'e saymak için beklenen sayaç içerir; Ancak, `break` açıklamayı sonlandıran döngü sonra 4 sayar.</span><span class="sxs-lookup"><span data-stu-id="83fea-106">In this example, the conditional statement contains a counter that is supposed to count from 1 to 100; however, the `break` statement terminates the loop after 4 counts.</span></span>  
  
 [!code-csharp[csrefKeywordsJump#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/break_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="83fea-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="83fea-107">Example</span></span>  
 <span data-ttu-id="83fea-108">Bu örnekte, `break` deyimi dışında bir iç iç içe geçmiş döngüsünü kesmek ve denetim için dış döngü döndürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="83fea-108">In this example, the `break` statement is used to break out of an inner nested loop, and return control to the outer loop.</span></span>  
  
 [!code-csharp[csrefKeywordsJump#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/break_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="83fea-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="83fea-109">Example</span></span>  
 <span data-ttu-id="83fea-110">Bu örnek kullanımını gösteren `break` içinde bir [geçiş](../../../csharp/language-reference/keywords/switch.md) deyimi.</span><span class="sxs-lookup"><span data-stu-id="83fea-110">This example demonstrates the use of `break` in a [switch](../../../csharp/language-reference/keywords/switch.md) statement.</span></span>  
  
 [!code-csharp[csrefKeywordsJump#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/break_3.cs)]  
  
 <span data-ttu-id="83fea-111">Girerseniz `4`, çıktı aşağıdaki gibi olur:</span><span class="sxs-lookup"><span data-stu-id="83fea-111">If you entered `4`, the output would be:</span></span>  
  
```  
Enter your selection (1, 2, or 3): 4  
Sorry, invalid selection.  
```  
  
## <a name="c-language-specification"></a><span data-ttu-id="83fea-112">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="83fea-112">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="83fea-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="83fea-113">See Also</span></span>  
 [<span data-ttu-id="83fea-114">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="83fea-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="83fea-115">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="83fea-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="83fea-116">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="83fea-116">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="83fea-117">switch</span><span class="sxs-lookup"><span data-stu-id="83fea-117">switch</span></span>](../../../csharp/language-reference/keywords/switch.md)  
 [<span data-ttu-id="83fea-118">Atlama Deyimleri</span><span class="sxs-lookup"><span data-stu-id="83fea-118">Jump Statements</span></span>](../../../csharp/language-reference/keywords/jump-statements.md)  
 [<span data-ttu-id="83fea-119">Yineleme Deyimleri</span><span class="sxs-lookup"><span data-stu-id="83fea-119">Iteration Statements</span></span>](../../../csharp/language-reference/keywords/iteration-statements.md)
