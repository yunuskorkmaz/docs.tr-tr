---
title: "operator (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- operator_CSharpKeyword
- operator
helpviewer_keywords: operator keyword [C#]
ms.assetid: 59218cce-e90e-42f6-a6bb-30300981b86a
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8fae5487d5daa5ada52d45919598d1abd217aee9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="operator-c-reference"></a><span data-ttu-id="8e26b-102">operator (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="8e26b-102">operator (C# Reference)</span></span>
<span data-ttu-id="8e26b-103">Kullanım `operator` anahtar sözcüğü bir yerleşik işleci aşırı yükleme veya kullanıcı tanımlı bir sınıf veya yapı bildirimi dönüştürmede sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="8e26b-103">Use the `operator` keyword to overload a built-in operator or to provide a user-defined conversion in a class or struct declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8e26b-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="8e26b-104">Example</span></span>  
 <span data-ttu-id="8e26b-105">Kesirli sayılar için oldukça basitleştirilmiş bir sınıf verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="8e26b-105">The following is a very simplified class for fractional numbers.</span></span> <span data-ttu-id="8e26b-106">Bunu overloads + ve * kesirli toplama ve çarpma gerçekleştirmek için işleçler ve ayrıca bir kesir türü çift türüne dönüştürür bir dönüşüm işleci sağlar.</span><span class="sxs-lookup"><span data-stu-id="8e26b-106">It overloads the + and * operators to perform fractional addition and multiplication, and also provides a conversion operator that converts a Fraction type to a double type.</span></span>  
  
 [!code-csharp[csrefKeywordsConversion#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/operator_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="8e26b-107">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="8e26b-107">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8e26b-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8e26b-108">See Also</span></span>  
 [<span data-ttu-id="8e26b-109">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="8e26b-109">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="8e26b-110">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="8e26b-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="8e26b-111">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="8e26b-111">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="8e26b-112">örtük</span><span class="sxs-lookup"><span data-stu-id="8e26b-112">implicit</span></span>](../../../csharp/language-reference/keywords/implicit.md)  
 [<span data-ttu-id="8e26b-113">açık</span><span class="sxs-lookup"><span data-stu-id="8e26b-113">explicit</span></span>](../../../csharp/language-reference/keywords/explicit.md)  
 [<span data-ttu-id="8e26b-114">Nasıl yapılır: yapılar arasında kullanıcı tanımlı dönüşümler</span><span class="sxs-lookup"><span data-stu-id="8e26b-114">How to: Implement User-Defined Conversions Between Structs</span></span>](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)
