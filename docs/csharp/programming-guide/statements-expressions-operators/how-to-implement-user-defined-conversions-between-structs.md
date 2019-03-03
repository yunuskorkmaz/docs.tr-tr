---
title: 'Nasıl yapılır: -Yapılar arasında kullanıcı tanımlı Dönüşümler Uygulama C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- user-defined conversions [C#]
ms.assetid: 97839aef-8fbc-40d5-9769-6b569bc2710b
ms.openlocfilehash: bc792562b4849d402e03328e50dedac030520011
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57201150"
---
# <a name="how-to-implement-user-defined-conversions-between-structs-c-programming-guide"></a><span data-ttu-id="a8273-102">Nasıl yapılır: Yapılar arasında kullanıcı tanımlı Dönüşümler Uygulama (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="a8273-102">How to: Implement User-Defined Conversions Between Structs (C# Programming Guide)</span></span>
<span data-ttu-id="a8273-103">Bu örnek iki yapıları tanımlar `RomanNumeral` ve `BinaryNumeral`ve bunlar arasında dönüştürmeler gösterir.</span><span class="sxs-lookup"><span data-stu-id="a8273-103">This example defines two structs, `RomanNumeral` and `BinaryNumeral`, and demonstrates conversions between them.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8273-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="a8273-104">Example</span></span>  
 [!code-csharp[csProgGuideStatements#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#13)]  
  
## <a name="robust-programming"></a><span data-ttu-id="a8273-105">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="a8273-105">Robust Programming</span></span>  
  
-   <span data-ttu-id="a8273-106">Önceki örnekte, deyim:</span><span class="sxs-lookup"><span data-stu-id="a8273-106">In the previous example, the statement:</span></span>  
  
     [!code-csharp[csProgGuideStatements#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#14)]  
  
     <span data-ttu-id="a8273-107">bir dönüştürme gerçekleştiren bir `RomanNumeral` için bir `BinaryNumeral`.</span><span class="sxs-lookup"><span data-stu-id="a8273-107">performs a conversion from a `RomanNumeral` to a `BinaryNumeral`.</span></span> <span data-ttu-id="a8273-108">Doğrudan dönüşüm yok olduğundan `RomanNumeral` için `BinaryNumeral`, bir yayın dönüştürmek için kullanılan bir `RomanNumeral` için bir `int`ve dönüştürmek için başka bir tür dönüştürme bir `int` için bir `BinaryNumeral`.</span><span class="sxs-lookup"><span data-stu-id="a8273-108">Because there is no direct conversion from `RomanNumeral` to `BinaryNumeral`, a cast is used to convert from a `RomanNumeral` to an `int`, and another cast to convert from an `int` to a `BinaryNumeral`.</span></span>  
  
-   <span data-ttu-id="a8273-109">Ayrıca deyimi</span><span class="sxs-lookup"><span data-stu-id="a8273-109">Also the statement</span></span>  
  
     [!code-csharp[csProgGuideStatements#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#15)]  
  
     <span data-ttu-id="a8273-110">bir dönüştürme gerçekleştiren bir `BinaryNumeral` için bir `RomanNumeral`.</span><span class="sxs-lookup"><span data-stu-id="a8273-110">performs a conversion from a `BinaryNumeral` to a `RomanNumeral`.</span></span> <span data-ttu-id="a8273-111">Çünkü `RomanNumeral` örtük bir dönüştürme tanımlar `BinaryNumeral`, atama gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a8273-111">Because `RomanNumeral` defines an implicit conversion from `BinaryNumeral`, no cast is required.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8273-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a8273-112">See also</span></span>

- [<span data-ttu-id="a8273-113">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="a8273-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="a8273-114">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="a8273-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="a8273-115">Dönüştürme İşleçleri</span><span class="sxs-lookup"><span data-stu-id="a8273-115">Conversion Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)
