---
title: "Nasıl yapılır: Yapılar Arasında Kullanıcı Tanımlı Dönüşümler Uygulama (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- user-defined conversions [C#]
ms.assetid: 97839aef-8fbc-40d5-9769-6b569bc2710b
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7d86cbd48347e6951f6b6883a385d80d68697c9c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-user-defined-conversions-between-structs-c-programming-guide"></a><span data-ttu-id="4642c-102">Nasıl yapılır: Yapılar Arasında Kullanıcı Tanımlı Dönüşümler Uygulama (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="4642c-102">How to: Implement User-Defined Conversions Between Structs (C# Programming Guide)</span></span>
<span data-ttu-id="4642c-103">Bu örnek iki yapılar tanımlar `RomanNumeral` ve `BinaryNumeral`, aralarında dönüşümleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="4642c-103">This example defines two structs, `RomanNumeral` and `BinaryNumeral`, and demonstrates conversions between them.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4642c-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="4642c-104">Example</span></span>  
 [!code-csharp[csProgGuideStatements#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-user-defined-conversions-between-structs_1.cs)]  
  
## <a name="robust-programming"></a><span data-ttu-id="4642c-105">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="4642c-105">Robust Programming</span></span>  
  
-   <span data-ttu-id="4642c-106">Önceki örnekte, deyim:</span><span class="sxs-lookup"><span data-stu-id="4642c-106">In the previous example, the statement:</span></span>  
  
     [!code-csharp[csProgGuideStatements#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-user-defined-conversions-between-structs_2.cs)]  
  
     <span data-ttu-id="4642c-107">bir dönüştürme işlemini gerçekleştiren bir `RomanNumeral` için bir `BinaryNumeral`.</span><span class="sxs-lookup"><span data-stu-id="4642c-107">performs a conversion from a `RomanNumeral` to a `BinaryNumeral`.</span></span> <span data-ttu-id="4642c-108">Doğrudan dönüştürme yok olduğundan `RomanNumeral` için `BinaryNumeral`, bir cast dönüştürmek için kullanılan bir `RomanNumeral` için bir `int`ve dönüştürmek için başka bir cast bir `int` için bir `BinaryNumeral`.</span><span class="sxs-lookup"><span data-stu-id="4642c-108">Because there is no direct conversion from `RomanNumeral` to `BinaryNumeral`, a cast is used to convert from a `RomanNumeral` to an `int`, and another cast to convert from an `int` to a `BinaryNumeral`.</span></span>  
  
-   <span data-ttu-id="4642c-109">Ayrıca deyimi</span><span class="sxs-lookup"><span data-stu-id="4642c-109">Also the statement</span></span>  
  
     [!code-csharp[csProgGuideStatements#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-user-defined-conversions-between-structs_3.cs)]  
  
     <span data-ttu-id="4642c-110">bir dönüştürme işlemini gerçekleştiren bir `BinaryNumeral` için bir `RomanNumeral`.</span><span class="sxs-lookup"><span data-stu-id="4642c-110">performs a conversion from a `BinaryNumeral` to a `RomanNumeral`.</span></span> <span data-ttu-id="4642c-111">Çünkü `RomanNumeral` örtük bir dönüştürme tanımlar `BinaryNumeral`, tür atama yok gereklidir.</span><span class="sxs-lookup"><span data-stu-id="4642c-111">Because `RomanNumeral` defines an implicit conversion from `BinaryNumeral`, no cast is required.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4642c-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4642c-112">See Also</span></span>  
 [<span data-ttu-id="4642c-113">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="4642c-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="4642c-114">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="4642c-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="4642c-115">Dönüştürme işleçleri</span><span class="sxs-lookup"><span data-stu-id="4642c-115">Conversion Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)
