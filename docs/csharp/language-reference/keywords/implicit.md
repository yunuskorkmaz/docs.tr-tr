---
title: implicit (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- implicit
- implicit_CSharpKeyword
helpviewer_keywords:
- implicit keyword [C#]
ms.assetid: 34db590e-eb3a-4f11-88d0-ffb3cd753dab
ms.openlocfilehash: 160d9f7c0d58abd685bf1d799b53cc96a26aebe8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33215023"
---
# <a name="implicit-c-reference"></a><span data-ttu-id="9e50f-102">implicit (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="9e50f-102">implicit (C# Reference)</span></span>
<span data-ttu-id="9e50f-103">`implicit` Anahtar sözcüğü bir örtük kullanıcı tanımlı tür dönüştürme işleci bildirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9e50f-103">The `implicit` keyword is used to declare an implicit user-defined type conversion operator.</span></span> <span data-ttu-id="9e50f-104">Dönüştürme veri kaybına neden değil garanti, kullanıcı tanımlı bir tür ve başka bir tür arasında örtük dönüşümler etkinleştirmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="9e50f-104">Use it to enable implicit conversions between a user-defined type and another type, if the conversion is guaranteed not to cause a loss of data.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9e50f-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="9e50f-105">Example</span></span>  
 [!code-csharp[csrefKeywordsConversion#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/implicit_1.cs)]  
  
 <span data-ttu-id="9e50f-106">Örtük dönüşümler gereksiz atamalar ortadan kaldırarak, kaynak kodun okunabilirliğini artırabilir.</span><span class="sxs-lookup"><span data-stu-id="9e50f-106">By eliminating unnecessary casts, implicit conversions can improve source code readability.</span></span> <span data-ttu-id="9e50f-107">Ancak, örtük dönüşümler açıkça bir türden diğerine dönüştürün programcıların gerektirmediği için beklenmeyen sonuçlara önlemek için dikkatli olunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9e50f-107">However, because implicit conversions do not require programmers to explicitly cast from one type to the other, care must be taken to prevent unexpected results.</span></span> <span data-ttu-id="9e50f-108">Genel olarak, örtük dönüşüm işleçleri hiçbir zaman özel durumlar oluşturma ve bu böylece Programcı tanıma güvenli bir şekilde kullanılabilir bilgileri hiçbir zaman kaybedersiniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="9e50f-108">In general, implicit conversion operators should never throw exceptions and never lose information so that they can be used safely without the programmer's awareness.</span></span> <span data-ttu-id="9e50f-109">Bir dönüşüm işleci Bu ölçütleri karşılayan olamaz, işaretlenmelidir `explicit`.</span><span class="sxs-lookup"><span data-stu-id="9e50f-109">If a conversion operator cannot meet those criteria, it should be marked `explicit`.</span></span> <span data-ttu-id="9e50f-110">Daha fazla bilgi için bkz: [dönüşüm işleçleri kullanma](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="9e50f-110">For more information, see [Using Conversion Operators](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="9e50f-111">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="9e50f-111">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9e50f-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9e50f-112">See Also</span></span>  
 [<span data-ttu-id="9e50f-113">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="9e50f-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="9e50f-114">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="9e50f-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="9e50f-115">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="9e50f-115">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="9e50f-116">explicit</span><span class="sxs-lookup"><span data-stu-id="9e50f-116">explicit</span></span>](../../../csharp/language-reference/keywords/explicit.md)  
 [<span data-ttu-id="9e50f-117">İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="9e50f-117">operator (C# Reference)</span></span>](../../../csharp/language-reference/keywords/operator.md)  
 [<span data-ttu-id="9e50f-118">Nasıl yapılır: Yapılar Arasında Kullanıcı Tanımlı Dönüştürmeler Uygulama</span><span class="sxs-lookup"><span data-stu-id="9e50f-118">How to: Implement User-Defined Conversions Between Structs</span></span>](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)
