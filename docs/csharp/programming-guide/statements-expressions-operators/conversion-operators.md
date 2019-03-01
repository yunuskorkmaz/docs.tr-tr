---
title: Dönüştürme işleçleri - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, conversion operators
- conversion operators [C#]
- operators [C#], conversion
- user-defined conversions [C#]
ms.assetid: c5ad73a3-d57b-4d2b-b4c9-24e3c2856efc
ms.openlocfilehash: 539a554da2ea2f785a54bd7e5ff81d09b908c9e4
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965221"
---
# <a name="conversion-operators-c-programming-guide"></a><span data-ttu-id="2d571-102">Dönüşüm işleçleri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="2d571-102">Conversion operators (C# Programming Guide)</span></span>

<span data-ttu-id="2d571-103">C# programcıları, böylece sınıflar veya yapılar için ve/veya diğer sınıflar veya yapılar veya temel türleri dönüştürülebilir sınıflar veya yapılar üzerinde dönüştürmeler bildirmek etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="2d571-103">C# enables programmers to declare conversions on classes or structs so that classes or structs can be converted to and/or from other classes or structs, or basic types.</span></span> <span data-ttu-id="2d571-104">Dönüştürme işleçleri gibi tanımlanır ve dönüştürme, türü adlandırılmış.</span><span class="sxs-lookup"><span data-stu-id="2d571-104">Conversions are defined like operators and are named for the type to which they convert.</span></span> <span data-ttu-id="2d571-105">Dönüştürülecek bağımsız değişken türünü veya dönüştürme, ancak iki değil, sonuç türü kapsayan tür olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2d571-105">Either the type of the argument to be converted, or the type of the result of the conversion, but not both, must be the containing type.</span></span>  
  
 [!code-csharp[csProgGuideStatements#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#10)]  
  
## <a name="conversion-operators-overview"></a><span data-ttu-id="2d571-106">Dönüştürme işleçlerine genel bakış</span><span class="sxs-lookup"><span data-stu-id="2d571-106">Conversion operators overview</span></span>

 <span data-ttu-id="2d571-107">Dönüştürme işleçleri aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="2d571-107">Conversion operators have the following properties:</span></span>  
  
-   <span data-ttu-id="2d571-108">Olarak bildirilen dönüştürmeler `implicit` gerekli olduğunda otomatik olarak gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="2d571-108">Conversions declared as `implicit` occur automatically when it is required.</span></span>  
  
-   <span data-ttu-id="2d571-109">Olarak bildirilen dönüştürmeler `explicit` çağrılacak bir yayın gerektirir.</span><span class="sxs-lookup"><span data-stu-id="2d571-109">Conversions declared as `explicit` require a cast to be called.</span></span>  
  
-   <span data-ttu-id="2d571-110">Tüm dönüştürmeler olarak bildirilmelidir `static`.</span><span class="sxs-lookup"><span data-stu-id="2d571-110">All conversions must be declared as `static`.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="2d571-111">İlgili bölümler</span><span class="sxs-lookup"><span data-stu-id="2d571-111">Related sections</span></span>

 <span data-ttu-id="2d571-112">Daha fazla bilgi için:</span><span class="sxs-lookup"><span data-stu-id="2d571-112">For more information:</span></span>  
  
-   [<span data-ttu-id="2d571-113">Dönüştürme İşleçleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="2d571-113">Using Conversion Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md)  
  
-   [<span data-ttu-id="2d571-114">Tür Değiştirme ve Tür Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="2d571-114">Casting and Type Conversions</span></span>](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
  
-   [<span data-ttu-id="2d571-115">Nasıl yapılır: Yapılar arasında kullanıcı tanımlı Dönüşümler Uygulama</span><span class="sxs-lookup"><span data-stu-id="2d571-115">How to: Implement User-Defined Conversions Between Structs</span></span>](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
  
-   [<span data-ttu-id="2d571-116">explicit</span><span class="sxs-lookup"><span data-stu-id="2d571-116">explicit</span></span>](../../../csharp/language-reference/keywords/explicit.md)  
  
-   [<span data-ttu-id="2d571-117">implicit</span><span class="sxs-lookup"><span data-stu-id="2d571-117">implicit</span></span>](../../../csharp/language-reference/keywords/implicit.md)  
  
-   [<span data-ttu-id="2d571-118">static</span><span class="sxs-lookup"><span data-stu-id="2d571-118">static</span></span>](../../../csharp/language-reference/keywords/static.md)  
  
## <a name="see-also"></a><span data-ttu-id="2d571-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2d571-119">See also</span></span>

- <xref:System.Convert>
- [<span data-ttu-id="2d571-120">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="2d571-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="2d571-121">Kullanıcı tanımlı C# ' de açık dönüştürmeler zincirleme</span><span class="sxs-lookup"><span data-stu-id="2d571-121">Chained user-defined explicit conversions in C#</span></span>](https://blogs.msdn.microsoft.com/ericlippert/2007/04/16/chained-user-defined-explicit-conversions-in-c/)
