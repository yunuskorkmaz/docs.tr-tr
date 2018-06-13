---
title: 'Nasıl yapılır: Yapılar Arasında Kullanıcı Tanımlı Dönüşümler Uygulama (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- user-defined conversions [C#]
ms.assetid: 97839aef-8fbc-40d5-9769-6b569bc2710b
ms.openlocfilehash: 178d9e2f92c5c1989253a16d866052a1fc42c10e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33339936"
---
# <a name="how-to-implement-user-defined-conversions-between-structs-c-programming-guide"></a><span data-ttu-id="07d3f-102">Nasıl yapılır: Yapılar Arasında Kullanıcı Tanımlı Dönüşümler Uygulama (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="07d3f-102">How to: Implement User-Defined Conversions Between Structs (C# Programming Guide)</span></span>
<span data-ttu-id="07d3f-103">Bu örnek iki yapılar tanımlar `RomanNumeral` ve `BinaryNumeral`, aralarında dönüşümleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="07d3f-103">This example defines two structs, `RomanNumeral` and `BinaryNumeral`, and demonstrates conversions between them.</span></span>  
  
## <a name="example"></a><span data-ttu-id="07d3f-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="07d3f-104">Example</span></span>  
 [!code-csharp[csProgGuideStatements#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-user-defined-conversions-between-structs_1.cs)]  
  
## <a name="robust-programming"></a><span data-ttu-id="07d3f-105">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="07d3f-105">Robust Programming</span></span>  
  
-   <span data-ttu-id="07d3f-106">Önceki örnekte, deyim:</span><span class="sxs-lookup"><span data-stu-id="07d3f-106">In the previous example, the statement:</span></span>  
  
     [!code-csharp[csProgGuideStatements#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-user-defined-conversions-between-structs_2.cs)]  
  
     <span data-ttu-id="07d3f-107">bir dönüştürme işlemini gerçekleştiren bir `RomanNumeral` için bir `BinaryNumeral`.</span><span class="sxs-lookup"><span data-stu-id="07d3f-107">performs a conversion from a `RomanNumeral` to a `BinaryNumeral`.</span></span> <span data-ttu-id="07d3f-108">Doğrudan dönüştürme yok olduğundan `RomanNumeral` için `BinaryNumeral`, bir cast dönüştürmek için kullanılan bir `RomanNumeral` için bir `int`ve dönüştürmek için başka bir cast bir `int` için bir `BinaryNumeral`.</span><span class="sxs-lookup"><span data-stu-id="07d3f-108">Because there is no direct conversion from `RomanNumeral` to `BinaryNumeral`, a cast is used to convert from a `RomanNumeral` to an `int`, and another cast to convert from an `int` to a `BinaryNumeral`.</span></span>  
  
-   <span data-ttu-id="07d3f-109">Ayrıca deyimi</span><span class="sxs-lookup"><span data-stu-id="07d3f-109">Also the statement</span></span>  
  
     [!code-csharp[csProgGuideStatements#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-user-defined-conversions-between-structs_3.cs)]  
  
     <span data-ttu-id="07d3f-110">bir dönüştürme işlemini gerçekleştiren bir `BinaryNumeral` için bir `RomanNumeral`.</span><span class="sxs-lookup"><span data-stu-id="07d3f-110">performs a conversion from a `BinaryNumeral` to a `RomanNumeral`.</span></span> <span data-ttu-id="07d3f-111">Çünkü `RomanNumeral` örtük bir dönüştürme tanımlar `BinaryNumeral`, tür atama yok gereklidir.</span><span class="sxs-lookup"><span data-stu-id="07d3f-111">Because `RomanNumeral` defines an implicit conversion from `BinaryNumeral`, no cast is required.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07d3f-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="07d3f-112">See Also</span></span>  
 [<span data-ttu-id="07d3f-113">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="07d3f-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="07d3f-114">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="07d3f-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="07d3f-115">Dönüştürme İşleçleri</span><span class="sxs-lookup"><span data-stu-id="07d3f-115">Conversion Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)
