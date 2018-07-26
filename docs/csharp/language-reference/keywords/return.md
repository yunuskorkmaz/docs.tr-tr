---
title: return (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- return_CSharpKeyword
- return
helpviewer_keywords:
- return statement [C#]
- return keyword [C#]
ms.assetid: 6da6e152-5b58-4448-8f3f-470dd0617ecd
ms.openlocfilehash: 29d2b8e28ae6240b9d06b82695efe1736404c5cb
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/25/2018
ms.locfileid: "39244783"
---
# <a name="return-c-reference"></a><span data-ttu-id="9f9fd-102">return (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="9f9fd-102">return (C# Reference)</span></span>
<span data-ttu-id="9f9fd-103">`return` Deyimi yöntemin hangi görüntülenir ve çağıran Metoda döndürür denetim yürütülmesini sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-103">The `return` statement terminates execution of the method in which it appears and returns control to the calling method.</span></span> <span data-ttu-id="9f9fd-104">Ayrıca, isteğe bağlı bir değer de döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-104">It can also return an optional value.</span></span> <span data-ttu-id="9f9fd-105">Yöntem ise bir `void` türü `return` ifade atlanabilir.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-105">If the method is a `void` type, the `return` statement can be omitted.</span></span>  
  
 <span data-ttu-id="9f9fd-106">Return deyimi içinde ise bir `try` bloğu `finally` bloğu, varsa, yürütülecek önce denetimini çağıran Metoda döndürür.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-106">If the return statement is inside a `try` block, the `finally` block, if one exists, will be executed before control returns to the calling method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9f9fd-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="9f9fd-107">Example</span></span>  
 <span data-ttu-id="9f9fd-108">Aşağıdaki örnekte, yöntem `CalculateArea()` yerel değişkeni döndürür `area` olarak bir [çift](../../../csharp/language-reference/keywords/double.md) değeri.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-108">In the following example, the method `CalculateArea()` returns the local variable `area` as a [double](../../../csharp/language-reference/keywords/double.md) value.</span></span>  
  
 [!code-csharp[csrefKeywordsJump#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/return_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="9f9fd-109">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="9f9fd-109">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9f9fd-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-110">See Also</span></span>  
 [<span data-ttu-id="9f9fd-111">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="9f9fd-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="9f9fd-112">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="9f9fd-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="9f9fd-113">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="9f9fd-113">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="9f9fd-114">return Deyimi</span><span class="sxs-lookup"><span data-stu-id="9f9fd-114">return Statement</span></span>](/cpp/cpp/return-statement-cpp)  
 [<span data-ttu-id="9f9fd-115">Atlama Deyimleri</span><span class="sxs-lookup"><span data-stu-id="9f9fd-115">Jump Statements</span></span>](../../../csharp/language-reference/keywords/jump-statements.md)
