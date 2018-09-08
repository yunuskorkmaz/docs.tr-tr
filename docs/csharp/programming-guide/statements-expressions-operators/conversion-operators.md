---
title: Dönüşüm İşleçleri (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, conversion operators
- conversion operators [C#]
- operators [C#], conversion
- user-defined conversions [C#]
ms.assetid: c5ad73a3-d57b-4d2b-b4c9-24e3c2856efc
ms.openlocfilehash: cbf6a83d43a1b3a69e82a35d5d0875f62422cd3f
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44183320"
---
# <a name="conversion-operators-c-programming-guide"></a><span data-ttu-id="59da8-102">Dönüşüm İşleçleri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="59da8-102">Conversion Operators (C# Programming Guide)</span></span>
<span data-ttu-id="59da8-103">C# programcıları, böylece sınıflar veya yapılar için ve/veya diğer sınıflar veya yapılar veya temel türleri dönüştürülebilir sınıflar veya yapılar üzerinde dönüştürmeler bildirmek etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="59da8-103">C# enables programmers to declare conversions on classes or structs so that classes or structs can be converted to and/or from other classes or structs, or basic types.</span></span> <span data-ttu-id="59da8-104">Dönüştürme işleçleri gibi tanımlanır ve dönüştürme, türü adlandırılmış.</span><span class="sxs-lookup"><span data-stu-id="59da8-104">Conversions are defined like operators and are named for the type to which they convert.</span></span> <span data-ttu-id="59da8-105">Dönüştürülecek bağımsız değişken türünü veya dönüştürme, ancak iki değil, sonuç türü kapsayan tür olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="59da8-105">Either the type of the argument to be converted, or the type of the result of the conversion, but not both, must be the containing type.</span></span>  
  
 [!code-csharp[csProgGuideStatements#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/conversion-operators_1.cs)]  
  
## <a name="conversion-operators-overview"></a><span data-ttu-id="59da8-106">Dönüştürme İşleçlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="59da8-106">Conversion Operators Overview</span></span>  
 <span data-ttu-id="59da8-107">Dönüştürme işleçleri aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="59da8-107">Conversion operators have the following properties:</span></span>  
  
-   <span data-ttu-id="59da8-108">Olarak bildirilen dönüştürmeler `implicit` gerekli olduğunda otomatik olarak gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="59da8-108">Conversions declared as `implicit` occur automatically when it is required.</span></span>  
  
-   <span data-ttu-id="59da8-109">Olarak bildirilen dönüştürmeler `explicit` çağrılacak bir yayın gerektirir.</span><span class="sxs-lookup"><span data-stu-id="59da8-109">Conversions declared as `explicit` require a cast to be called.</span></span>  
  
-   <span data-ttu-id="59da8-110">Tüm dönüştürmeler olarak bildirilmelidir `static`.</span><span class="sxs-lookup"><span data-stu-id="59da8-110">All conversions must be declared as `static`.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="59da8-111">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="59da8-111">Related Sections</span></span>  
 <span data-ttu-id="59da8-112">Daha fazla bilgi için:</span><span class="sxs-lookup"><span data-stu-id="59da8-112">For more information:</span></span>  
  
-   [<span data-ttu-id="59da8-113">Dönüştürme İşleçleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="59da8-113">Using Conversion Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md)  
  
-   [<span data-ttu-id="59da8-114">Tür Değiştirme ve Tür Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="59da8-114">Casting and Type Conversions</span></span>](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
  
-   [<span data-ttu-id="59da8-115">Nasıl yapılır: Yapılar Arasında Kullanıcı Tanımlı Dönüştürmeler Uygulama</span><span class="sxs-lookup"><span data-stu-id="59da8-115">How to: Implement User-Defined Conversions Between Structs</span></span>](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
  
-   [<span data-ttu-id="59da8-116">explicit</span><span class="sxs-lookup"><span data-stu-id="59da8-116">explicit</span></span>](../../../csharp/language-reference/keywords/explicit.md)  
  
-   [<span data-ttu-id="59da8-117">implicit</span><span class="sxs-lookup"><span data-stu-id="59da8-117">implicit</span></span>](../../../csharp/language-reference/keywords/implicit.md)  
  
-   [<span data-ttu-id="59da8-118">static</span><span class="sxs-lookup"><span data-stu-id="59da8-118">static</span></span>](../../../csharp/language-reference/keywords/static.md)  
  
## <a name="see-also"></a><span data-ttu-id="59da8-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="59da8-119">See Also</span></span>

- <xref:System.Convert>  
- [<span data-ttu-id="59da8-120">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="59da8-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="59da8-121">Kullanıcı tanımlı C# ' de açık dönüştürmeler zincirleme</span><span class="sxs-lookup"><span data-stu-id="59da8-121">Chained user-defined explicit conversions in C#</span></span>](https://blogs.msdn.microsoft.com/ericlippert/2007/04/16/chained-user-defined-explicit-conversions-in-c/)
