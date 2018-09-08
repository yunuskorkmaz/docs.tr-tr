---
title: 'Nasıl yapılır: Yapılar Arasında Kullanıcı Tanımlı Dönüşümler Uygulama (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- user-defined conversions [C#]
ms.assetid: 97839aef-8fbc-40d5-9769-6b569bc2710b
ms.openlocfilehash: cff85d60c1b59f4d1ca028f8fc02fee5728fa3d6
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44136530"
---
# <a name="how-to-implement-user-defined-conversions-between-structs-c-programming-guide"></a><span data-ttu-id="8afcd-102">Nasıl yapılır: Yapılar Arasında Kullanıcı Tanımlı Dönüşümler Uygulama (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="8afcd-102">How to: Implement User-Defined Conversions Between Structs (C# Programming Guide)</span></span>
<span data-ttu-id="8afcd-103">Bu örnek iki yapıları tanımlar `RomanNumeral` ve `BinaryNumeral`ve bunlar arasında dönüştürmeler gösterir.</span><span class="sxs-lookup"><span data-stu-id="8afcd-103">This example defines two structs, `RomanNumeral` and `BinaryNumeral`, and demonstrates conversions between them.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8afcd-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="8afcd-104">Example</span></span>  
 [!code-csharp[csProgGuideStatements#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-user-defined-conversions-between-structs_1.cs)]  
  
## <a name="robust-programming"></a><span data-ttu-id="8afcd-105">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="8afcd-105">Robust Programming</span></span>  
  
-   <span data-ttu-id="8afcd-106">Önceki örnekte, deyim:</span><span class="sxs-lookup"><span data-stu-id="8afcd-106">In the previous example, the statement:</span></span>  
  
     [!code-csharp[csProgGuideStatements#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-user-defined-conversions-between-structs_2.cs)]  
  
     <span data-ttu-id="8afcd-107">bir dönüştürme gerçekleştiren bir `RomanNumeral` için bir `BinaryNumeral`.</span><span class="sxs-lookup"><span data-stu-id="8afcd-107">performs a conversion from a `RomanNumeral` to a `BinaryNumeral`.</span></span> <span data-ttu-id="8afcd-108">Doğrudan dönüşüm yok olduğundan `RomanNumeral` için `BinaryNumeral`, bir yayın dönüştürmek için kullanılan bir `RomanNumeral` için bir `int`ve dönüştürmek için başka bir tür dönüştürme bir `int` için bir `BinaryNumeral`.</span><span class="sxs-lookup"><span data-stu-id="8afcd-108">Because there is no direct conversion from `RomanNumeral` to `BinaryNumeral`, a cast is used to convert from a `RomanNumeral` to an `int`, and another cast to convert from an `int` to a `BinaryNumeral`.</span></span>  
  
-   <span data-ttu-id="8afcd-109">Ayrıca deyimi</span><span class="sxs-lookup"><span data-stu-id="8afcd-109">Also the statement</span></span>  
  
     [!code-csharp[csProgGuideStatements#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-user-defined-conversions-between-structs_3.cs)]  
  
     <span data-ttu-id="8afcd-110">bir dönüştürme gerçekleştiren bir `BinaryNumeral` için bir `RomanNumeral`.</span><span class="sxs-lookup"><span data-stu-id="8afcd-110">performs a conversion from a `BinaryNumeral` to a `RomanNumeral`.</span></span> <span data-ttu-id="8afcd-111">Çünkü `RomanNumeral` örtük bir dönüştürme tanımlar `BinaryNumeral`, atama gereklidir.</span><span class="sxs-lookup"><span data-stu-id="8afcd-111">Because `RomanNumeral` defines an implicit conversion from `BinaryNumeral`, no cast is required.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8afcd-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8afcd-112">See Also</span></span>

- [<span data-ttu-id="8afcd-113">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="8afcd-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="8afcd-114">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="8afcd-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="8afcd-115">Dönüştürme İşleçleri</span><span class="sxs-lookup"><span data-stu-id="8afcd-115">Conversion Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)
