---
title: override (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- override
- override_CSharpKeyword
helpviewer_keywords:
- override keyword [C#]
ms.assetid: dd1907a8-acf8-46d3-80b9-c2ca4febada8
ms.openlocfilehash: 8f692dfdf8bd34ddb62623d86ec3dadd2b8dead3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33280159"
---
# <a name="override-c-reference"></a><span data-ttu-id="f1378-102">override (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="f1378-102">override (C# Reference)</span></span>
<span data-ttu-id="f1378-103">`override` Genişletmek veya bir devralınan yöntemi, özelliği, dizin oluşturucu veya olay soyut veya sanal uyarlamasını değiştirmek için değiştiricisi gereklidir.</span><span class="sxs-lookup"><span data-stu-id="f1378-103">The `override` modifier is required to extend or modify the abstract or virtual implementation of an inherited method, property, indexer, or event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f1378-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="f1378-104">Example</span></span>  
 <span data-ttu-id="f1378-105">Bu örnekte, `Square` sınıfı geçersiz kılınan uygulaması sağlamalıdır `Area` çünkü `Area` Özet devralınan `ShapesClass`:</span><span class="sxs-lookup"><span data-stu-id="f1378-105">In this example, the `Square` class must provide an overridden implementation of `Area` because `Area` is inherited from the abstract `ShapesClass`:</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/override_1.cs)]  
  
 <span data-ttu-id="f1378-106">Bir `override` yöntemi bir taban sınıftan devralınan bir üyenin yeni bir uygulama sağlar.</span><span class="sxs-lookup"><span data-stu-id="f1378-106">An `override` method provides a new implementation of a member that is inherited from a base class.</span></span> <span data-ttu-id="f1378-107">Tarafından geçersiz kılınır yöntemi bir `override` bildirimi geçersiz kılınan temel yöntemi olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="f1378-107">The method that is overridden by an `override` declaration is known as the overridden base method.</span></span> <span data-ttu-id="f1378-108">Geçersiz kılınan temel yöntemi olarak aynı imzaya sahip olmalıdır `override` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f1378-108">The overridden base method must have the same signature as the `override` method.</span></span> <span data-ttu-id="f1378-109">Devralma hakkında daha fazla bilgi için bkz: [devralma](../../../csharp/programming-guide/classes-and-structs/inheritance.md).</span><span class="sxs-lookup"><span data-stu-id="f1378-109">For information about inheritance, see [Inheritance](../../../csharp/programming-guide/classes-and-structs/inheritance.md).</span></span>  
  
 <span data-ttu-id="f1378-110">Sanal olmayan veya statik yöntemi geçersiz kılamaz.</span><span class="sxs-lookup"><span data-stu-id="f1378-110">You cannot override a non-virtual or static method.</span></span> <span data-ttu-id="f1378-111">Geçersiz kılınan temel yöntemi olmalıdır `virtual`, `abstract`, veya `override`.</span><span class="sxs-lookup"><span data-stu-id="f1378-111">The overridden base method must be `virtual`, `abstract`, or `override`.</span></span>  
  
 <span data-ttu-id="f1378-112">Bir `override` bildirimi erişilebilirliğini değiştiremiyor `virtual` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f1378-112">An `override` declaration cannot change the accessibility of the `virtual` method.</span></span> <span data-ttu-id="f1378-113">Her iki `override` yöntemi ve `virtual` yöntemi aynı olması gerekir [erişim düzeyi değiştiricisi](../../../csharp/language-reference/keywords/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="f1378-113">Both the `override` method and the `virtual` method must have the same [access level modifier](../../../csharp/language-reference/keywords/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="f1378-114">Kullanamazsınız `new`, `static`, veya `virtual` değiştirmek için değiştiricileri bir `override` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f1378-114">You cannot use the `new`, `static`, or `virtual` modifiers to modify an `override` method.</span></span>  
  
 <span data-ttu-id="f1378-115">Bir geçersiz kılma özellik bildirimi tam olarak aynı erişim değiştiricisi, türü ve adı devralınan özelliği olarak belirtmeniz gerekir ve geçersiz kılınan özelliği olmalıdır `virtual`, `abstract`, veya `override`.</span><span class="sxs-lookup"><span data-stu-id="f1378-115">An overriding property declaration must specify exactly the same access modifier, type, and name as the inherited property, and the overridden property must be `virtual`, `abstract`, or `override`.</span></span>  
  
 <span data-ttu-id="f1378-116">Nasıl kullanılacağı hakkında daha fazla bilgi için `override` anahtar sözcüğü, bkz: [geçersiz kılma ve yeni anahtar sözcüklerle sürüm oluşturma](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) ve [geçersiz kılma ve yeni anahtar sözcüklerin ne zaman kullanılacağını bilme](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span><span class="sxs-lookup"><span data-stu-id="f1378-116">For more information about how to use the `override` keyword, see [Versioning with the Override and New Keywords](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) and [Knowing when to use Override and New Keywords](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f1378-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="f1378-117">Example</span></span>  
 <span data-ttu-id="f1378-118">Bu örnek adlı bir temel sınıf tanımlar `Employee`ve adlı türetilmiş bir sınıf `SalesEmployee`.</span><span class="sxs-lookup"><span data-stu-id="f1378-118">This example defines a base class named `Employee`, and a derived class named `SalesEmployee`.</span></span> <span data-ttu-id="f1378-119">`SalesEmployee` Sınıfı içeren bir ek özellik `salesbonus`ve yöntemini geçersiz kılar `CalculatePay` dikkate almanız için.</span><span class="sxs-lookup"><span data-stu-id="f1378-119">The `SalesEmployee` class includes an extra property, `salesbonus`, and overrides the method `CalculatePay` in order to take it into account.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/override_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="f1378-120">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="f1378-120">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f1378-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f1378-121">See Also</span></span>  
 [<span data-ttu-id="f1378-122">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="f1378-122">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="f1378-123">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="f1378-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f1378-124">Devralma</span><span class="sxs-lookup"><span data-stu-id="f1378-124">Inheritance</span></span>](../../../csharp/programming-guide/classes-and-structs/inheritance.md)  
 [<span data-ttu-id="f1378-125">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="f1378-125">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="f1378-126">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="f1378-126">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
 [<span data-ttu-id="f1378-127">abstract</span><span class="sxs-lookup"><span data-stu-id="f1378-127">abstract</span></span>](../../../csharp/language-reference/keywords/abstract.md)  
 [<span data-ttu-id="f1378-128">virtual</span><span class="sxs-lookup"><span data-stu-id="f1378-128">virtual</span></span>](../../../csharp/language-reference/keywords/virtual.md)  
 [<span data-ttu-id="f1378-129">new</span><span class="sxs-lookup"><span data-stu-id="f1378-129">new</span></span>](../../../csharp/language-reference/keywords/new.md)  
 [<span data-ttu-id="f1378-130">Çok biçimlilik</span><span class="sxs-lookup"><span data-stu-id="f1378-130">Polymorphism</span></span>](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)
