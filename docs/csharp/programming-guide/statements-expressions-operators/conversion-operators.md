---
title: "Dönüşüm İşleçleri (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- C# language, conversion operators
- conversion operators [C#]
- operators [C#], conversion
- user-defined conversions [C#]
ms.assetid: c5ad73a3-d57b-4d2b-b4c9-24e3c2856efc
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 056971dcd648208d77573c180df28ffdd46788c5
ms.sourcegitcommit: 22a48b64a0150a60b00b4fc4d8c62cde7f1670c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2018
---
# <a name="conversion-operators-c-programming-guide"></a><span data-ttu-id="52d37-102">Dönüşüm İşleçleri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="52d37-102">Conversion Operators (C# Programming Guide)</span></span>
<span data-ttu-id="52d37-103">C# programcıları sınıfları veya yapılar ve/veya diğer sınıflar yapılar veya temel türleri dönüştürülebilir böylece dönüşümleri sınıfları veya yapılar bildirmek etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="52d37-103">C# enables programmers to declare conversions on classes or structs so that classes or structs can be converted to and/or from other classes or structs, or basic types.</span></span> <span data-ttu-id="52d37-104">Dönüşümler like işleçleri tanımlanır ve bunlar dönüştürme türü için adlı.</span><span class="sxs-lookup"><span data-stu-id="52d37-104">Conversions are defined like operators and are named for the type to which they convert.</span></span> <span data-ttu-id="52d37-105">Dönüştürülecek bağımsız değişken türü veya dönüştürme, ancak ikisini birlikte, sonucu türünü içeren türde olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="52d37-105">Either the type of the argument to be converted, or the type of the result of the conversion, but not both, must be the containing type.</span></span>  
  
 [!code-csharp[csProgGuideStatements#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/conversion-operators_1.cs)]  
  
## <a name="conversion-operators-overview"></a><span data-ttu-id="52d37-106">Dönüştürme İşleçlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="52d37-106">Conversion Operators Overview</span></span>  
 <span data-ttu-id="52d37-107">Dönüştürme işleçleri aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="52d37-107">Conversion operators have the following properties:</span></span>  
  
-   <span data-ttu-id="52d37-108">Dönüşümler bildirilen `implicit` gerekli olduğunda otomatik olarak gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="52d37-108">Conversions declared as `implicit` occur automatically when it is required.</span></span>  
  
-   <span data-ttu-id="52d37-109">Dönüşümler bildirilen `explicit` çağrılacak bir cast gerektirir.</span><span class="sxs-lookup"><span data-stu-id="52d37-109">Conversions declared as `explicit` require a cast to be called.</span></span>  
  
-   <span data-ttu-id="52d37-110">Tüm dönüşümler olarak bildirilmelidir `static`.</span><span class="sxs-lookup"><span data-stu-id="52d37-110">All conversions must be declared as `static`.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="52d37-111">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="52d37-111">Related Sections</span></span>  
 <span data-ttu-id="52d37-112">Daha fazla bilgi için:</span><span class="sxs-lookup"><span data-stu-id="52d37-112">For more information:</span></span>  
  
-   [<span data-ttu-id="52d37-113">Dönüştürme İşleçleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="52d37-113">Using Conversion Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md)  
  
-   [<span data-ttu-id="52d37-114">Tür Değiştirme ve Tür Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="52d37-114">Casting and Type Conversions</span></span>](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
  
-   [<span data-ttu-id="52d37-115">Nasıl yapılır: Yapılar Arasında Kullanıcı Tanımlı Dönüştürmeler Uygulama</span><span class="sxs-lookup"><span data-stu-id="52d37-115">How to: Implement User-Defined Conversions Between Structs</span></span>](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
  
-   [<span data-ttu-id="52d37-116">explicit</span><span class="sxs-lookup"><span data-stu-id="52d37-116">explicit</span></span>](../../../csharp/language-reference/keywords/explicit.md)  
  
-   [<span data-ttu-id="52d37-117">implicit</span><span class="sxs-lookup"><span data-stu-id="52d37-117">implicit</span></span>](../../../csharp/language-reference/keywords/implicit.md)  
  
-   [<span data-ttu-id="52d37-118">static</span><span class="sxs-lookup"><span data-stu-id="52d37-118">static</span></span>](../../../csharp/language-reference/keywords/static.md)  
  
## <a name="see-also"></a><span data-ttu-id="52d37-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="52d37-119">See Also</span></span>  
 <xref:System.Convert>  
 [<span data-ttu-id="52d37-120">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="52d37-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="52d37-121">Kullanıcı tanımlı zincirleme açık dönüşümler C#</span><span class="sxs-lookup"><span data-stu-id="52d37-121">Chained user-defined explicit conversions in C#</span></span>](https://blogs.msdn.microsoft.com/ericlippert/2007/04/16/chained-user-defined-explicit-conversions-in-c/)
