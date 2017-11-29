---
title: "return (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- return_CSharpKeyword
- return
helpviewer_keywords:
- return statement [C#]
- return keyword [C#]
ms.assetid: 6da6e152-5b58-4448-8f3f-470dd0617ecd
caps.latest.revision: "18"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 90c84b51c6ee57864eac552bc488c9f9c15e9394
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="return-c-reference"></a><span data-ttu-id="71831-102">return (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="71831-102">return (C# Reference)</span></span>
<span data-ttu-id="71831-103">`return` Açıklamayı sonlandıran yürütme yönteminin, görünür ve denetim çağıran yönteme döndürür.</span><span class="sxs-lookup"><span data-stu-id="71831-103">The `return` statement terminates execution of the method in which it appears and returns control to the calling method.</span></span> <span data-ttu-id="71831-104">Ayrıca isteğe bağlı değeri geri dönebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="71831-104">It can also return an optional value.</span></span> <span data-ttu-id="71831-105">Yöntemi bir `void` türü, `return` deyimi etmeyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="71831-105">If the method is a `void` type, the `return` statement can be omitted.</span></span>  
  
 <span data-ttu-id="71831-106">Return deyimi içinde ise bir `try` bloğu `finally` bloğu, varsa, yürütülür önce çağıran yönteme denetimini döndürür.</span><span class="sxs-lookup"><span data-stu-id="71831-106">If the return statement is inside a `try` block, the `finally` block, if one exists, will be executed before control returns to the calling method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="71831-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="71831-107">Example</span></span>  
 <span data-ttu-id="71831-108">Aşağıdaki örnekte, yöntem `CalculateArea()` yerel değişken döndürür `area` olarak bir [çift](../../../csharp/language-reference/keywords/double.md) değeri.</span><span class="sxs-lookup"><span data-stu-id="71831-108">In the following example, the method `CalculateArea()` returns the local variable `area` as a [double](../../../csharp/language-reference/keywords/double.md) value.</span></span>  
  
 [!code-csharp[csrefKeywordsJump#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/return_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="71831-109">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="71831-109">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="71831-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="71831-110">See Also</span></span>  
 [<span data-ttu-id="71831-111">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="71831-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="71831-112">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="71831-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="71831-113">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="71831-113">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="71831-114">return deyimi</span><span class="sxs-lookup"><span data-stu-id="71831-114">return Statement</span></span>](/cpp/cpp/return-statement-cpp)  
 [<span data-ttu-id="71831-115">Atlama deyimleri</span><span class="sxs-lookup"><span data-stu-id="71831-115">Jump Statements</span></span>](../../../csharp/language-reference/keywords/jump-statements.md)
