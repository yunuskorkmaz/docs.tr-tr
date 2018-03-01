---
title: "implicit (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- implicit
- implicit_CSharpKeyword
helpviewer_keywords:
- implicit keyword [C#]
ms.assetid: 34db590e-eb3a-4f11-88d0-ffb3cd753dab
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c893c7a9afbdc6f715010d537e9ccaf66c5785c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="implicit-c-reference"></a><span data-ttu-id="9798d-102">implicit (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="9798d-102">implicit (C# Reference)</span></span>
<span data-ttu-id="9798d-103">`implicit` Anahtar sözcüğü bir örtük kullanıcı tanımlı tür dönüştürme işleci bildirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9798d-103">The `implicit` keyword is used to declare an implicit user-defined type conversion operator.</span></span> <span data-ttu-id="9798d-104">Dönüştürme veri kaybına neden değil garanti, kullanıcı tanımlı bir tür ve başka bir tür arasında örtük dönüşümler etkinleştirmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="9798d-104">Use it to enable implicit conversions between a user-defined type and another type, if the conversion is guaranteed not to cause a loss of data.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9798d-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="9798d-105">Example</span></span>  
 [!code-csharp[csrefKeywordsConversion#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/implicit_1.cs)]  
  
 <span data-ttu-id="9798d-106">Örtük dönüşümler gereksiz atamalar ortadan kaldırarak, kaynak kodun okunabilirliğini artırabilir.</span><span class="sxs-lookup"><span data-stu-id="9798d-106">By eliminating unnecessary casts, implicit conversions can improve source code readability.</span></span> <span data-ttu-id="9798d-107">Ancak, örtük dönüşümler açıkça bir türden diğerine dönüştürün programcıların gerektirmediği için beklenmeyen sonuçlara önlemek için dikkatli olunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9798d-107">However, because implicit conversions do not require programmers to explicitly cast from one type to the other, care must be taken to prevent unexpected results.</span></span> <span data-ttu-id="9798d-108">Genel olarak, örtük dönüşüm işleçleri hiçbir zaman özel durumlar oluşturma ve bu böylece Programcı tanıma güvenli bir şekilde kullanılabilir bilgileri hiçbir zaman kaybedersiniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="9798d-108">In general, implicit conversion operators should never throw exceptions and never lose information so that they can be used safely without the programmer's awareness.</span></span> <span data-ttu-id="9798d-109">Bir dönüşüm işleci Bu ölçütleri karşılayan olamaz, işaretlenmelidir `explicit`.</span><span class="sxs-lookup"><span data-stu-id="9798d-109">If a conversion operator cannot meet those criteria, it should be marked `explicit`.</span></span> <span data-ttu-id="9798d-110">Daha fazla bilgi için bkz: [dönüşüm işleçleri kullanma](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="9798d-110">For more information, see [Using Conversion Operators](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="9798d-111">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="9798d-111">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9798d-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9798d-112">See Also</span></span>  
 [<span data-ttu-id="9798d-113">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="9798d-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="9798d-114">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="9798d-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="9798d-115">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="9798d-115">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="9798d-116">açık</span><span class="sxs-lookup"><span data-stu-id="9798d-116">explicit</span></span>](../../../csharp/language-reference/keywords/explicit.md)  
 [<span data-ttu-id="9798d-117">işleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="9798d-117">operator (C# Reference)</span></span>](../../../csharp/language-reference/keywords/operator.md)  
 [<span data-ttu-id="9798d-118">Nasıl yapılır: yapılar arasında kullanıcı tanımlı dönüşümler</span><span class="sxs-lookup"><span data-stu-id="9798d-118">How to: Implement User-Defined Conversions Between Structs</span></span>](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)
