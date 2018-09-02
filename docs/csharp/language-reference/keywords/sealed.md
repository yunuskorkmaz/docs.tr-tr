---
title: sealed (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- sealed
- sealed_CSharpKeyword
helpviewer_keywords:
- sealed keyword [C#]
ms.assetid: 8e4ed5d3-10be-47db-9488-0da2008e6f3f
ms.openlocfilehash: 674c7e1cd87b95318f739ab22876f4bfe5ae73d8
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43386646"
---
# <a name="sealed-c-reference"></a><span data-ttu-id="953c4-102">sealed (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="953c4-102">sealed (C# Reference)</span></span>
<span data-ttu-id="953c4-103">Bir sınıfa uygulandığında `sealed` değiştiricisi kullananların devralmasını diğer sınıflar engeller.</span><span class="sxs-lookup"><span data-stu-id="953c4-103">When applied to a class, the `sealed` modifier prevents other classes from inheriting from it.</span></span> <span data-ttu-id="953c4-104">Aşağıdaki örnekte, sınıf `B` sınıfından devralan `A`, ancak hiçbir sınıf sınıfı devralabilirsiniz `B`.</span><span class="sxs-lookup"><span data-stu-id="953c4-104">In the following example, class `B` inherits from class `A`, but no class can inherit from class `B`.</span></span>  
  
```csharp  
class A {}      
sealed class B : A {}  
```  
  
 <span data-ttu-id="953c4-105">Ayrıca `sealed` bir yöntem veya sanal bir yöntemi geçersiz kılan özellik veya bir temel sınıf özelliği değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="953c4-105">You can also use the `sealed` modifier on a method or property that overrides a virtual method or property in a base class.</span></span> <span data-ttu-id="953c4-106">Bu izin, sınıfından türetilir ve bunları belirli sanal yöntemleri veya özellikleri geçersiz kılmasını önlemek için sınıflar sağlar.</span><span class="sxs-lookup"><span data-stu-id="953c4-106">This enables you to allow classes to derive from your class and prevent them from overriding specific virtual methods or properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="953c4-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="953c4-107">Example</span></span>  
 <span data-ttu-id="953c4-108">Aşağıdaki örnekte, `Z` devraldığı `Y` ancak `Z` sanal işlevini geçersiz kılamaz `F` dosyasında bildirilen `X` hem de korumalı `Y`.</span><span class="sxs-lookup"><span data-stu-id="953c4-108">In the following example, `Z` inherits from `Y` but `Z` cannot override the virtual function `F` that is declared in `X` and sealed in `Y`.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/sealed_1.cs)]  
  
 <span data-ttu-id="953c4-109">Bir sınıfta yeni yöntemleri veya özellikleri tanımladığınızda, türetilen sınıflar olarak bildirerek değil önlemiş engelleyebilir [sanal](../../../csharp/language-reference/keywords/virtual.md).</span><span class="sxs-lookup"><span data-stu-id="953c4-109">When you define new methods or properties in a class, you can prevent deriving classes from overriding them by not declaring them as [virtual](../../../csharp/language-reference/keywords/virtual.md).</span></span>  
  
 <span data-ttu-id="953c4-110">Kullanılacak bir hata olduğunu [soyut](../../../csharp/language-reference/keywords/abstract.md) değiştiricisi kapalı bir sınıf ile soyut bir sınıf soyut yöntemleri veya özellikleri uygulaması sağlayan bir sınıf tarafından devralınan gerekir çünkü.</span><span class="sxs-lookup"><span data-stu-id="953c4-110">It is an error to use the [abstract](../../../csharp/language-reference/keywords/abstract.md) modifier with a sealed class, because an abstract class must be inherited by a class that provides an implementation of the abstract methods or properties.</span></span>  
  
 <span data-ttu-id="953c4-111">Bir yöntemi veya özelliği uygulandığında `sealed` değiştiricisi her zaman kullanılması gerektiğini ile [geçersiz kılma](../../../csharp/language-reference/keywords/override.md).</span><span class="sxs-lookup"><span data-stu-id="953c4-111">When applied to a method or property, the `sealed` modifier must always be used with [override](../../../csharp/language-reference/keywords/override.md).</span></span>  
  
 <span data-ttu-id="953c4-112">Yapılardan türetme çünkü bunlar devralınamaz.</span><span class="sxs-lookup"><span data-stu-id="953c4-112">Because structs are implicitly sealed, they cannot be inherited.</span></span>  
  
 <span data-ttu-id="953c4-113">Daha fazla bilgi için [devralma](../../../csharp/programming-guide/classes-and-structs/inheritance.md).</span><span class="sxs-lookup"><span data-stu-id="953c4-113">For more information, see [Inheritance](../../../csharp/programming-guide/classes-and-structs/inheritance.md).</span></span>  
  
 <span data-ttu-id="953c4-114">Daha fazla örnek için bkz. [soyut ve korumalı sınıflar ve sınıf üyeleri](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="953c4-114">For more examples, see [Abstract and Sealed Classes and Class Members](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="953c4-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="953c4-115">Example</span></span>  
 [!code-csharp[csrefKeywordsModifiers#17](../../../csharp/language-reference/keywords/codesnippet/CSharp/sealed_2.cs)]  
  
 <span data-ttu-id="953c4-116">Önceki örnekte, aşağıdaki deyimi kullanarak korumalı sınıfından devralmak deneyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="953c4-116">In the previous example, you might try to inherit from the sealed class by using the following statement:</span></span>  
  
 `class MyDerivedC: SealedClass {}   // Error`  
  
 <span data-ttu-id="953c4-117">Sonucu bir hata iletisi oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="953c4-117">The result is an error message:</span></span>  
  
 `'MyDerivedC': cannot derive from sealed type 'SealedClass'`  
  
## <a name="c-language-specification"></a><span data-ttu-id="953c4-118">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="953c4-118">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="remarks"></a><span data-ttu-id="953c4-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="953c4-119">Remarks</span></span>  
 <span data-ttu-id="953c4-120">Bir sınıf, yöntem veya özellik mühürlenecek belirlemek için genellikle iki aşağıdaki noktaları dikkate almanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="953c4-120">To determine whether to seal a class, method, or property, you should generally consider the following two points:</span></span>  
  
-   <span data-ttu-id="953c4-121">Olası faydaları sınıflardan türetme sınıfınıza özelleştirme olanağı elde edebilir.</span><span class="sxs-lookup"><span data-stu-id="953c4-121">The potential benefits that deriving classes might gain through the ability to customize your class.</span></span>  
  
-   <span data-ttu-id="953c4-122">Olası sınıflardan türetme gibi sınıflarınızdaki değiştirebilir, bunlar artık doğru şekilde çalışması veya olarak bir yöntem bekleniyor.</span><span class="sxs-lookup"><span data-stu-id="953c4-122">The potential that deriving classes could modify your classes in such a way that they would no longer work correctly or as expected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="953c4-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="953c4-123">See Also</span></span>

- [<span data-ttu-id="953c4-124">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="953c4-124">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="953c4-125">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="953c4-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="953c4-126">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="953c4-126">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="953c4-127">Statik Sınıflar ve Statik Sınıf Üyeleri</span><span class="sxs-lookup"><span data-stu-id="953c4-127">Static Classes and Static Class Members</span></span>](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)  
- [<span data-ttu-id="953c4-128">Soyut ve Korumalı Sınıflar ve Sınıf Üyeleri</span><span class="sxs-lookup"><span data-stu-id="953c4-128">Abstract and Sealed Classes and Class Members</span></span>](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)  
- [<span data-ttu-id="953c4-129">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="953c4-129">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
- [<span data-ttu-id="953c4-130">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="953c4-130">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
- [<span data-ttu-id="953c4-131">override</span><span class="sxs-lookup"><span data-stu-id="953c4-131">override</span></span>](../../../csharp/language-reference/keywords/override.md)  
- [<span data-ttu-id="953c4-132">virtual</span><span class="sxs-lookup"><span data-stu-id="953c4-132">virtual</span></span>](../../../csharp/language-reference/keywords/virtual.md)
