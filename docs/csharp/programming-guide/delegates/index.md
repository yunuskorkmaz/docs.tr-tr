---
title: Temsilciler (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, delegates
- delegates [C#]
ms.assetid: 97de039b-c76b-4b9c-a27d-8c1e1c8d93da
ms.openlocfilehash: 3924d070ea012faf33f1d808b92b1328626ef567
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43805461"
---
# <a name="delegates-c-programming-guide"></a><span data-ttu-id="3c9c1-102">Temsilciler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="3c9c1-102">Delegates (C# Programming Guide)</span></span>
<span data-ttu-id="3c9c1-103">A [temsilci](../../../csharp/language-reference/keywords/delegate.md) belirli bir parametre listesi olan yöntemlere başvuruları temsil eden bir tür ve dönüş türü.</span><span class="sxs-lookup"><span data-stu-id="3c9c1-103">A [delegate](../../../csharp/language-reference/keywords/delegate.md) is a type that represents references to methods with a particular parameter list and return type.</span></span> <span data-ttu-id="3c9c1-104">Bir temsilci oluşturduğunuzda, örneğini uyumlu bir imza ve dönüş türü içeren herhangi bir yöntemle ilişkilendirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3c9c1-104">When you instantiate a delegate, you can associate its instance with any method with a compatible signature and return type.</span></span> <span data-ttu-id="3c9c1-105">Yöntemi, temsilci örneği aracılığıyla çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3c9c1-105">You can invoke (or call) the method through the delegate instance.</span></span>  
  
 <span data-ttu-id="3c9c1-106">Temsilciler, yöntemleri bağımsız değişkenler olarak diğer yöntemlere geçirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3c9c1-106">Delegates are used to pass methods as arguments to other methods.</span></span> <span data-ttu-id="3c9c1-107">Olay işleyicileri, temsilciler aracılığıyla çağrılan yöntemlerden başka bir şey değildir.</span><span class="sxs-lookup"><span data-stu-id="3c9c1-107">Event handlers are nothing more than methods that are invoked through delegates.</span></span> <span data-ttu-id="3c9c1-108">Özel bir yöntem oluşturabilirsiniz ve bir pencere denetimi gibi bir sınıf, belirli bir olay olduğunda yönteminizi çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="3c9c1-108">You create a custom method, and a class such as a windows control can call your method when a certain event occurs.</span></span> <span data-ttu-id="3c9c1-109">Aşağıdaki örnek, bir temsilci bildirimini gösterir:</span><span class="sxs-lookup"><span data-stu-id="3c9c1-109">The following example shows a delegate declaration:</span></span>  
  
 [!code-csharp[csProgGuideDelegates#20](../../../csharp/programming-guide/delegates/codesnippet/CSharp/index_1.cs)]  
  
 <span data-ttu-id="3c9c1-110">Temsilci türüyle eşleşen herhangi bir erişilebilir sınıf veya yapıdan alınan herhangi bir yöntem temsilciye atanabilir.</span><span class="sxs-lookup"><span data-stu-id="3c9c1-110">Any method from any accessible class or struct that matches the delegate type can be assigned to the delegate.</span></span> <span data-ttu-id="3c9c1-111">Yöntem, statik veya örnek bir yöntem olabilir.</span><span class="sxs-lookup"><span data-stu-id="3c9c1-111">The method can be either static or an instance method.</span></span> <span data-ttu-id="3c9c1-112">Bu, yöntem çağrılarını programatik olarak değiştirmeyi ve varolan sınıflara yeni kod eklemeyi olanaklı kılar.</span><span class="sxs-lookup"><span data-stu-id="3c9c1-112">This makes it possible to programmatically change method calls, and also plug new code into existing classes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3c9c1-113">Yöntem aşırı yükü bağlamında, yöntemin imzası dönüş değeri içermez.</span><span class="sxs-lookup"><span data-stu-id="3c9c1-113">In the context of method overloading, the signature of a method does not include the return value.</span></span> <span data-ttu-id="3c9c1-114">Ancak, temsilciler bağlamında, imza dönüş değerini içermez.</span><span class="sxs-lookup"><span data-stu-id="3c9c1-114">But in the context of delegates, the signature does include the return value.</span></span> <span data-ttu-id="3c9c1-115">Başka bir deyişle, bir yöntemin dönüş türü temsilciyle aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3c9c1-115">In other words, a method must have the same return type as the delegate.</span></span>  
  
 <span data-ttu-id="3c9c1-116">Bir yönteme bir parametre olarak başvurma yeteneği, temsilciyi geri çağırma yöntemleri için ideal hale getirir.</span><span class="sxs-lookup"><span data-stu-id="3c9c1-116">This ability to refer to a method as a parameter makes delegates ideal for defining callback methods.</span></span> <span data-ttu-id="3c9c1-117">Örneğin, iki nesneyi karşılaştıran bir yönteme yapılan bir başvuru, bir sıralama algoritmasına bir bağımsız değişken olarak geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="3c9c1-117">For example, a reference to a method that compares two objects could be passed as an argument to a sort algorithm.</span></span> <span data-ttu-id="3c9c1-118">Karşılaştırma kodu ayrı bir yordamda olduğundan, sıralama algoritması daha genel bir şekilde yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="3c9c1-118">Because the comparison code is in a separate procedure, the sort algorithm can be written in a more general way.</span></span>  
  
## <a name="delegates-overview"></a><span data-ttu-id="3c9c1-119">Temsilcilere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="3c9c1-119">Delegates Overview</span></span>  
 <span data-ttu-id="3c9c1-120">Temsilciler aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="3c9c1-120">Delegates have the following properties:</span></span>  
  
-   <span data-ttu-id="3c9c1-121">Temsilciler C++ işlev işaretçileri gibidir, fakat tür bakımından güvenlidir.</span><span class="sxs-lookup"><span data-stu-id="3c9c1-121">Delegates are like C++ function pointers but are type safe.</span></span>  
  
-   <span data-ttu-id="3c9c1-122">Temsilciler, yöntemlerin parametre olarak geçirilmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="3c9c1-122">Delegates allow methods to be passed as parameters.</span></span>  
  
-   <span data-ttu-id="3c9c1-123">Temsilciler, geri çağırma yöntemlerini tanımlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3c9c1-123">Delegates can be used to define callback methods.</span></span>  
  
-   <span data-ttu-id="3c9c1-124">Temsilciler birlikte zincirleme yapılabilir; Örneğin, tek bir olay üzerine birden çok yöntem çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="3c9c1-124">Delegates can be chained together; for example, multiple methods can be called on a single event.</span></span>  
  
-   <span data-ttu-id="3c9c1-125">Yöntemlerin temsilci türüyle tam olarak eşleşmesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="3c9c1-125">Methods do not have to match the delegate type exactly.</span></span> <span data-ttu-id="3c9c1-126">Daha fazla bilgi için [kullanarak Temsilcilerde varyans](../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="3c9c1-126">For more information, see [Using Variance in Delegates](../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span></span>  
  
-   <span data-ttu-id="3c9c1-127">C# sürüm 2.0 kavramını kullanıma sundu [anonim yöntemler](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md), kod bloklarının ayrı olarak tanımlanan bir yöntem yerine parametre olarak geçirilmesine izin verin.</span><span class="sxs-lookup"><span data-stu-id="3c9c1-127">C# version 2.0 introduced the concept of [Anonymous Methods](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md), which allow code blocks to be passed as parameters in place of a separately defined method.</span></span> <span data-ttu-id="3c9c1-128">C# 3.0, satır içi kod blokları yazmak için daha kısa bir yol olarak lambda ifadelerini kullanmaya başladı.</span><span class="sxs-lookup"><span data-stu-id="3c9c1-128">C# 3.0 introduced lambda expressions as a more concise way of writing inline code blocks.</span></span> <span data-ttu-id="3c9c1-129">Hem anonim yöntemler hem de lambda ifadeleri (belirli bağlamlarda) temsilci türleri olarak derlenir.</span><span class="sxs-lookup"><span data-stu-id="3c9c1-129">Both anonymous methods and lambda expressions (in certain contexts) are compiled to delegate types.</span></span> <span data-ttu-id="3c9c1-130">Birlikte, bu özellikler artık anonim işlevler olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="3c9c1-130">Together, these features are now known as anonymous functions.</span></span> <span data-ttu-id="3c9c1-131">Lambda ifadeleri hakkında daha fazla bilgi için bkz. [anonim işlevler](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).</span><span class="sxs-lookup"><span data-stu-id="3c9c1-131">For more information about lambda expressions, see [Anonymous Functions](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3c9c1-132">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="3c9c1-132">In This Section</span></span>  
  
-   [<span data-ttu-id="3c9c1-133">Temsilcileri Kullanma</span><span class="sxs-lookup"><span data-stu-id="3c9c1-133">Using Delegates</span></span>](../../../csharp/programming-guide/delegates/using-delegates.md)  
  
-   [<span data-ttu-id="3c9c1-134">Arabirimler (C# programlama Kılavuzu) yerine temsilciler ne zaman kullanılır?</span><span class="sxs-lookup"><span data-stu-id="3c9c1-134">When to Use Delegates Instead of Interfaces (C# Programming Guide)</span></span>](https://msdn.microsoft.com/library/2e759bdf-7ca4-4005-8597-af92edf6d8f0)  
  
-   [<span data-ttu-id="3c9c1-135">Temsilcilerin Adlandırılmış ve Anonim Yöntemlerde Karşılaştırılması</span><span class="sxs-lookup"><span data-stu-id="3c9c1-135">Delegates with Named vs. Anonymous Methods</span></span>](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)  
  
-   [<span data-ttu-id="3c9c1-136">Anonim Metotlar</span><span class="sxs-lookup"><span data-stu-id="3c9c1-136">Anonymous Methods</span></span>](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
  
-   [<span data-ttu-id="3c9c1-137">Temsilcilerde Varyans Kullanma</span><span class="sxs-lookup"><span data-stu-id="3c9c1-137">Using Variance in Delegates</span></span>](../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md)  
  
-   [<span data-ttu-id="3c9c1-138">Nasıl yapılır: temsilcileri (çok noktaya yayın temsilcileri) birleştirme</span><span class="sxs-lookup"><span data-stu-id="3c9c1-138">How to: Combine Delegates (Multicast Delegates)</span></span>](../../../csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)  
  
-   [<span data-ttu-id="3c9c1-139">Nasıl yapılır: Temsilci Bildirme, Oluşturma ve Kullanma</span><span class="sxs-lookup"><span data-stu-id="3c9c1-139">How to: Declare, Instantiate, and Use a Delegate</span></span>](../../../csharp/programming-guide/delegates/how-to-declare-instantiate-and-use-a-delegate.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="3c9c1-140">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="3c9c1-140">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="featured-book-chapters"></a><span data-ttu-id="3c9c1-141">Özel Kitap Bölümleri</span><span class="sxs-lookup"><span data-stu-id="3c9c1-141">Featured Book Chapters</span></span>  
 <span data-ttu-id="3c9c1-142">[Temsilciler, olayları ve Lambda ifadeleri](https://msdn.microsoft.com/library/orm-9780596516109-03-09.aspx) içinde [C# 3.0 Cookbook, Third Edition: C# 3.0 programcıları için 250'den fazla çözüm](https://msdn.microsoft.com/library/orm-9780596516109-03.aspx)</span><span class="sxs-lookup"><span data-stu-id="3c9c1-142">[Delegates, Events, and Lambda Expressions](https://msdn.microsoft.com/library/orm-9780596516109-03-09.aspx) in [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](https://msdn.microsoft.com/library/orm-9780596516109-03.aspx)</span></span>  
  
 <span data-ttu-id="3c9c1-143">[Temsilciler ve olaylar](https://msdn.microsoft.com/library/orm-9780596521066-01-17.aspx) içinde [Learning C# 3.0: Master the fundamentals of C# 3.0](https://msdn.microsoft.com/library/orm-9780596521066-01.aspx)</span><span class="sxs-lookup"><span data-stu-id="3c9c1-143">[Delegates and Events](https://msdn.microsoft.com/library/orm-9780596521066-01-17.aspx) in [Learning C# 3.0: Master the fundamentals of C# 3.0](https://msdn.microsoft.com/library/orm-9780596521066-01.aspx)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c9c1-144">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3c9c1-144">See Also</span></span>

- <xref:System.Delegate>  
- [<span data-ttu-id="3c9c1-145">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="3c9c1-145">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="3c9c1-146">Olaylar</span><span class="sxs-lookup"><span data-stu-id="3c9c1-146">Events</span></span>](../../../csharp/programming-guide/events/index.md)
