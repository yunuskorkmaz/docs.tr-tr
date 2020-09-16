---
title: Temsilciler-C# Programlama Kılavuzu
description: C# ' deki bir temsilci, bir parametre listesi ve dönüş türü olan yöntemlere başvuran bir türdür. Temsilciler, yöntemleri bağımsız değişkenler olarak diğer yöntemlere geçirmek için kullanılır.
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, delegates
- delegates [C#]
ms.assetid: 97de039b-c76b-4b9c-a27d-8c1e1c8d93da
ms.openlocfilehash: cf6b90a606d13e3196e3114e84971451a9a322c9
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90553577"
---
# <a name="delegates-c-programming-guide"></a><span data-ttu-id="c7560-104">Temsilciler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="c7560-104">Delegates (C# Programming Guide)</span></span>
<span data-ttu-id="c7560-105">[Temsilci](../../language-reference/builtin-types/reference-types.md) , belirli bir parametre listesi ve dönüş türü olan yöntemlere yapılan başvuruları temsil eden bir türdür.</span><span class="sxs-lookup"><span data-stu-id="c7560-105">A [delegate](../../language-reference/builtin-types/reference-types.md) is a type that represents references to methods with a particular parameter list and return type.</span></span> <span data-ttu-id="c7560-106">Bir temsilci oluşturduğunuzda, örneğini uyumlu bir imza ve dönüş türü içeren herhangi bir yöntemle ilişkilendirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7560-106">When you instantiate a delegate, you can associate its instance with any method with a compatible signature and return type.</span></span> <span data-ttu-id="c7560-107">Yöntemi, temsilci örneği aracılığıyla çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7560-107">You can invoke (or call) the method through the delegate instance.</span></span>  
  
 <span data-ttu-id="c7560-108">Temsilciler, yöntemleri bağımsız değişkenler olarak diğer yöntemlere geçirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c7560-108">Delegates are used to pass methods as arguments to other methods.</span></span> <span data-ttu-id="c7560-109">Olay işleyicileri, temsilciler aracılığıyla çağrılan yöntemlerden başka bir şey değildir.</span><span class="sxs-lookup"><span data-stu-id="c7560-109">Event handlers are nothing more than methods that are invoked through delegates.</span></span> <span data-ttu-id="c7560-110">Özel bir yöntem oluşturabilirsiniz ve bir pencere denetimi gibi bir sınıf, belirli bir olay olduğunda yönteminizi çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="c7560-110">You create a custom method, and a class such as a windows control can call your method when a certain event occurs.</span></span> <span data-ttu-id="c7560-111">Aşağıdaki örnek, bir temsilci bildirimini gösterir:</span><span class="sxs-lookup"><span data-stu-id="c7560-111">The following example shows a delegate declaration:</span></span>  
  
 [!code-csharp[csProgGuideDelegates#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#20)]  
  
 <span data-ttu-id="c7560-112">Temsilci türüyle eşleşen herhangi bir erişilebilir sınıf veya yapıdan alınan herhangi bir yöntem temsilciye atanabilir.</span><span class="sxs-lookup"><span data-stu-id="c7560-112">Any method from any accessible class or struct that matches the delegate type can be assigned to the delegate.</span></span> <span data-ttu-id="c7560-113">Yöntem, statik veya örnek bir yöntem olabilir.</span><span class="sxs-lookup"><span data-stu-id="c7560-113">The method can be either static or an instance method.</span></span> <span data-ttu-id="c7560-114">Bu, yöntem çağrılarını programatik olarak değiştirmeyi ve varolan sınıflara yeni kod eklemeyi olanaklı kılar.</span><span class="sxs-lookup"><span data-stu-id="c7560-114">This makes it possible to programmatically change method calls, and also plug new code into existing classes.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c7560-115">Yöntem aşırı yükü bağlamında, yöntemin imzası dönüş değeri içermez.</span><span class="sxs-lookup"><span data-stu-id="c7560-115">In the context of method overloading, the signature of a method does not include the return value.</span></span> <span data-ttu-id="c7560-116">Ancak, temsilciler bağlamında, imza dönüş değerini içermez.</span><span class="sxs-lookup"><span data-stu-id="c7560-116">But in the context of delegates, the signature does include the return value.</span></span> <span data-ttu-id="c7560-117">Başka bir deyişle, bir yöntemin dönüş türü temsilciyle aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c7560-117">In other words, a method must have the same return type as the delegate.</span></span>  
  
 <span data-ttu-id="c7560-118">Bir yönteme bir parametre olarak başvurma yeteneği, temsilciyi geri çağırma yöntemleri için ideal hale getirir.</span><span class="sxs-lookup"><span data-stu-id="c7560-118">This ability to refer to a method as a parameter makes delegates ideal for defining callback methods.</span></span> <span data-ttu-id="c7560-119">Örneğin, iki nesneyi karşılaştıran bir yönteme yapılan bir başvuru, bir sıralama algoritmasına bir bağımsız değişken olarak geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="c7560-119">For example, a reference to a method that compares two objects could be passed as an argument to a sort algorithm.</span></span> <span data-ttu-id="c7560-120">Karşılaştırma kodu ayrı bir yordamda olduğundan, sıralama algoritması daha genel bir şekilde yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="c7560-120">Because the comparison code is in a separate procedure, the sort algorithm can be written in a more general way.</span></span>  
  
## <a name="delegates-overview"></a><span data-ttu-id="c7560-121">Temsilcilere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c7560-121">Delegates Overview</span></span>  
 <span data-ttu-id="c7560-122">Temsilciler aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="c7560-122">Delegates have the following properties:</span></span>  
  
- <span data-ttu-id="c7560-123">Temsilciler C++ işlev işaretçilerine benzerdir, ancak temsilciler tam nesne yönelimli olarak ve üye işlevlerine C++ işaretçilerine benzemekle birlikte, temsilciler hem bir nesne örneğini hem de bir yöntemi kapsüller.</span><span class="sxs-lookup"><span data-stu-id="c7560-123">Delegates are similar to C++ function pointers, but delegates are fully object-oriented, and unlike C++ pointers to member functions, delegates encapsulate both an object instance and a method.</span></span>
  
- <span data-ttu-id="c7560-124">Temsilciler, yöntemlerin parametre olarak geçirilmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="c7560-124">Delegates allow methods to be passed as parameters.</span></span>  
  
- <span data-ttu-id="c7560-125">Temsilciler, geri çağırma yöntemlerini tanımlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c7560-125">Delegates can be used to define callback methods.</span></span>  
  
- <span data-ttu-id="c7560-126">Temsilciler birlikte zincirleme yapılabilir; Örneğin, tek bir olay üzerine birden çok yöntem çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="c7560-126">Delegates can be chained together; for example, multiple methods can be called on a single event.</span></span>  
  
- <span data-ttu-id="c7560-127">Yöntemlerin temsilci türüyle tam olarak eşleşmesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="c7560-127">Methods do not have to match the delegate type exactly.</span></span> <span data-ttu-id="c7560-128">Daha fazla bilgi için bkz. [Temsilcilerde varyans kullanma](../concepts/covariance-contravariance/using-variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="c7560-128">For more information, see [Using Variance in Delegates](../concepts/covariance-contravariance/using-variance-in-delegates.md).</span></span>  
  
- <span data-ttu-id="c7560-129">C# sürüm 2,0, kod bloklarının ayrı olarak tanımlanmış bir yöntem yerine parametre olarak geçirilmesine izin veren [Anonim yöntemler](../../language-reference/operators/delegate-operator.md)kavramını sunmuştur.</span><span class="sxs-lookup"><span data-stu-id="c7560-129">C# version 2.0 introduced the concept of [anonymous methods](../../language-reference/operators/delegate-operator.md), which allow code blocks to be passed as parameters in place of a separately defined method.</span></span> <span data-ttu-id="c7560-130">C# 3.0, satır içi kod blokları yazmak için daha kısa bir yol olarak lambda ifadelerini kullanmaya başladı.</span><span class="sxs-lookup"><span data-stu-id="c7560-130">C# 3.0 introduced lambda expressions as a more concise way of writing inline code blocks.</span></span> <span data-ttu-id="c7560-131">Hem anonim yöntemler hem de lambda ifadeleri (belirli bağlamlarda) temsilci türleri olarak derlenir.</span><span class="sxs-lookup"><span data-stu-id="c7560-131">Both anonymous methods and lambda expressions (in certain contexts) are compiled to delegate types.</span></span> <span data-ttu-id="c7560-132">Birlikte, bu özellikler artık anonim işlevler olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="c7560-132">Together, these features are now known as anonymous functions.</span></span> <span data-ttu-id="c7560-133">Lambda ifadeleri hakkında daha fazla bilgi için bkz. [lambda ifadeleri](../../language-reference/operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="c7560-133">For more information about lambda expressions, see [Lambda expressions](../../language-reference/operators/lambda-expressions.md).</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="c7560-134">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="c7560-134">In This Section</span></span>  
  
- [<span data-ttu-id="c7560-135">Temsilcileri Kullanma</span><span class="sxs-lookup"><span data-stu-id="c7560-135">Using Delegates</span></span>](./using-delegates.md)  
  
- <span data-ttu-id="c7560-136">[Arabirimler yerine temsilcilerin ne zaman kullanılacağı (C# Programlama Kılavuzu)](/previous-versions/visualstudio/visual-studio-2010/ms173173(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="c7560-136">[When to Use Delegates Instead of Interfaces (C# Programming Guide)](/previous-versions/visualstudio/visual-studio-2010/ms173173(v=vs.100))</span></span>  
  
- [<span data-ttu-id="c7560-137">Temsilcilerin Adlandırılmış ve Anonim Yöntemler</span><span class="sxs-lookup"><span data-stu-id="c7560-137">Delegates with Named vs. Anonymous Methods</span></span>](./delegates-with-named-vs-anonymous-methods.md)  
  
- [<span data-ttu-id="c7560-138">Temsilcilerde Varyans Kullanma</span><span class="sxs-lookup"><span data-stu-id="c7560-138">Using Variance in Delegates</span></span>](../concepts/covariance-contravariance/using-variance-in-delegates.md)  
  
- [<span data-ttu-id="c7560-139">Temsilcileri birleştirme (çok noktaya yayın temsilcileri)</span><span class="sxs-lookup"><span data-stu-id="c7560-139">How to combine delegates (Multicast Delegates)</span></span>](./how-to-combine-delegates-multicast-delegates.md)  
  
- [<span data-ttu-id="c7560-140">Temsilci bildirme, oluşturma ve kullanma</span><span class="sxs-lookup"><span data-stu-id="c7560-140">How to declare, instantiate, and use a delegate</span></span>](./how-to-declare-instantiate-and-use-a-delegate.md)

## <a name="c-language-specification"></a><span data-ttu-id="c7560-141">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="c7560-141">C# Language Specification</span></span>  

<span data-ttu-id="c7560-142">Daha fazla bilgi için bkz. [C# dil belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [Temsilciler](~/_csharplang/spec/delegates.md) .</span><span class="sxs-lookup"><span data-stu-id="c7560-142">For more information, see [Delegates](~/_csharplang/spec/delegates.md) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="c7560-143">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="c7560-143">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="featured-book-chapters"></a><span data-ttu-id="c7560-144">Özel Kitap Bölümleri</span><span class="sxs-lookup"><span data-stu-id="c7560-144">Featured Book Chapters</span></span>  
 <span data-ttu-id="c7560-145">C# 3,0 tanımlama kitabı, üçüncü sürüm 'de [Temsilciler, olaylar ve lambda ifadeleri](/previous-versions/visualstudio/visual-studio-2008/ff518994(v=orm.10)) [: c# 3,0 programcıları için 250 ' den fazla çözüm](/previous-versions/visualstudio/visual-studio-2008/ff518995(v=orm.10))</span><span class="sxs-lookup"><span data-stu-id="c7560-145">[Delegates, Events, and Lambda Expressions](/previous-versions/visualstudio/visual-studio-2008/ff518994(v=orm.10)) in [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](/previous-versions/visualstudio/visual-studio-2008/ff518995(v=orm.10))</span></span>  
  
 <span data-ttu-id="c7560-146">Öğreniminde [Temsilciler ve olaylar](/previous-versions/visualstudio/visual-studio-2008/ff652490(v=orm.10)) [c# 3,0: C# 3,0 temelleri ana](/previous-versions/visualstudio/visual-studio-2008/ff652493(v=orm.10))</span><span class="sxs-lookup"><span data-stu-id="c7560-146">[Delegates and Events](/previous-versions/visualstudio/visual-studio-2008/ff652490(v=orm.10)) in [Learning C# 3.0: Master the fundamentals of C# 3.0](/previous-versions/visualstudio/visual-studio-2008/ff652493(v=orm.10))</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7560-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c7560-147">See also</span></span>

- <xref:System.Delegate>
- [<span data-ttu-id="c7560-148">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="c7560-148">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="c7560-149">Ekinlikler</span><span class="sxs-lookup"><span data-stu-id="c7560-149">Events</span></span>](../events/index.md)
