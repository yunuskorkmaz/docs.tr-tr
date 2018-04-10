---
title: goto (C# Başvurusu)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- goto_CSharpKeyword
- goto
helpviewer_keywords:
- goto keyword [C#]
ms.assetid: 2c03c9c1-8119-44ef-b740-fb3d287a42fe
caps.latest.revision: 22
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: aa12a7547cfcd4a2076b5b0a308139f8a823f482
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="goto-c-reference"></a><span data-ttu-id="ba01c-102">goto (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="ba01c-102">goto (C# Reference)</span></span>
<span data-ttu-id="ba01c-103">`goto` Deyimi doğrudan etiketli deyim için program denetimini aktarır.</span><span class="sxs-lookup"><span data-stu-id="ba01c-103">The `goto` statement transfers the program control directly to a labeled statement.</span></span>  
  
 <span data-ttu-id="ba01c-104">Yaygın kullanımı `goto` belirli bir anahtar durumu etiket veya varsayılan etiket denetimi aktarmak için bir `switch` deyimi.</span><span class="sxs-lookup"><span data-stu-id="ba01c-104">A common use of `goto` is to transfer control to a specific switch-case label or the default label in a `switch` statement.</span></span>  
  
 <span data-ttu-id="ba01c-105">`goto` Deyimi dışında iç içe döngüler almak yararlı de.</span><span class="sxs-lookup"><span data-stu-id="ba01c-105">The `goto` statement is also useful to get out of deeply nested loops.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ba01c-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="ba01c-106">Example</span></span>  
 <span data-ttu-id="ba01c-107">Aşağıdaki örnek, kullanma gösterir `goto` içinde bir [geçiş](../../../csharp/language-reference/keywords/switch.md) deyimi.</span><span class="sxs-lookup"><span data-stu-id="ba01c-107">The following example demonstrates using `goto` in a [switch](../../../csharp/language-reference/keywords/switch.md) statement.</span></span>  
  
 [!code-csharp[csrefKeywordsJump#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/goto_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="ba01c-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="ba01c-108">Example</span></span>  
 <span data-ttu-id="ba01c-109">Aşağıdaki örnek, kullanma gösterir `goto` iç içe geçmiş döngüler başlama için.</span><span class="sxs-lookup"><span data-stu-id="ba01c-109">The following example demonstrates using `goto` to break out from nested loops.</span></span>  
  
 [!code-csharp[csrefKeywordsJump#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/goto_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="ba01c-110">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="ba01c-110">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ba01c-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ba01c-111">See Also</span></span>  
 [<span data-ttu-id="ba01c-112">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="ba01c-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="ba01c-113">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="ba01c-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="ba01c-114">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="ba01c-114">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="ba01c-115">goto deyimi</span><span class="sxs-lookup"><span data-stu-id="ba01c-115">goto Statement</span></span>](/cpp/cpp/goto-statement-cpp)  
 [<span data-ttu-id="ba01c-116">Atlama deyimleri</span><span class="sxs-lookup"><span data-stu-id="ba01c-116">Jump Statements</span></span>](../../../csharp/language-reference/keywords/jump-statements.md)
