---
title: Deyimler, İfadeler ve İşleçler (C# Programlama Kılavuzu)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- expressions [C#]
- operators [C#]
- C# language, statements
- C# language, operators
- C# language, expressions
- statements [C#]
ms.assetid: 20f8469d-5a6a-4084-ad90-0856b7e97e45
caps.latest.revision: 22
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b7c634cb0c0e5f86e324999360d2bc64a457d5da
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="statements-expressions-and-operators-c-programming-guide"></a><span data-ttu-id="be9a9-102">Deyimler, İfadeler ve İşleçler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="be9a9-102">Statements, Expressions, and Operators (C# Programming Guide)</span></span>
<span data-ttu-id="be9a9-103">Bir uygulama oluşur C# kodu anahtar sözcükler, ifadeler ve işleçler oluşan bilgilerinin oluşur.</span><span class="sxs-lookup"><span data-stu-id="be9a9-103">The C# code that comprises an application consists of statements made up of keywords, expressions and operators.</span></span> <span data-ttu-id="be9a9-104">Bu bölüm, C# programının temel bu öğeler ile ilgili bilgiler içerir.</span><span class="sxs-lookup"><span data-stu-id="be9a9-104">This section contains information regarding these fundamental elements of a C# program.</span></span>  
  
 <span data-ttu-id="be9a9-105">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="be9a9-105">For more information, see:</span></span>  
  
-   [<span data-ttu-id="be9a9-106">Deyimleri</span><span class="sxs-lookup"><span data-stu-id="be9a9-106">Statements</span></span>](../../../csharp/programming-guide/statements-expressions-operators/statements.md)  
  
-   [<span data-ttu-id="be9a9-107">İfadeler</span><span class="sxs-lookup"><span data-stu-id="be9a9-107">Expressions</span></span>](../../../csharp/programming-guide/statements-expressions-operators/expressions.md)  
  
    -   [<span data-ttu-id="be9a9-108">İfade bodied üyeleri</span><span class="sxs-lookup"><span data-stu-id="be9a9-108">Expression-bodied members</span></span>](expression-bodied-members.md)
 
-   [<span data-ttu-id="be9a9-109">İşleçler</span><span class="sxs-lookup"><span data-stu-id="be9a9-109">Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/operators.md)  
  
-   [<span data-ttu-id="be9a9-110">Anonim İşlevler</span><span class="sxs-lookup"><span data-stu-id="be9a9-110">Anonymous Functions</span></span>](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)  
  
-   [<span data-ttu-id="be9a9-111">Fazla yüklenebilir işleçler</span><span class="sxs-lookup"><span data-stu-id="be9a9-111">Overloadable Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/overloadable-operators.md)  
  
-   [<span data-ttu-id="be9a9-112">Dönüştürme işleçleri</span><span class="sxs-lookup"><span data-stu-id="be9a9-112">Conversion Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)  
  
    -   [<span data-ttu-id="be9a9-113">Dönüşüm işleçleri kullanma</span><span class="sxs-lookup"><span data-stu-id="be9a9-113">Using Conversion Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md)  
  
    -   [<span data-ttu-id="be9a9-114">Nasıl yapılır: yapılar arasında kullanıcı tanımlı dönüşümler</span><span class="sxs-lookup"><span data-stu-id="be9a9-114">How to: Implement User-Defined Conversions Between Structs</span></span>](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
  
-   [<span data-ttu-id="be9a9-115">Nasıl yapılır: karmaşık sayı sınıfı oluşturmak için işleç aşırı yüklemesi kullanma</span><span class="sxs-lookup"><span data-stu-id="be9a9-115">How to: Use Operator Overloading to Create a Complex Number Class</span></span>](../../../csharp/programming-guide/statements-expressions-operators/how-to-use-operator-overloading-to-create-a-complex-number-class.md)  
  
-   [<span data-ttu-id="be9a9-116">Eşitlik karşılaştırmaları</span><span class="sxs-lookup"><span data-stu-id="be9a9-116">Equality Comparisons</span></span>](../../../csharp/programming-guide/statements-expressions-operators/equality-comparisons.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="be9a9-117">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="be9a9-117">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="be9a9-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="be9a9-118">See Also</span></span>  
 [<span data-ttu-id="be9a9-119">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="be9a9-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="be9a9-120">Atama ve tür dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="be9a9-120">Casting and Type Conversions</span></span>](../../../csharp/programming-guide/types/casting-and-type-conversions.md)
