---
title: Kesin Tür Belirtilmiş Temsilciler
description: Temsilci gerektiren bir özellik oluştururken özel türler bildirmek için genel temsilci türlerini nasıl kullanacağınızı öğrenin.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: 564a683d-352b-4e57-8bac-b466529daf6b
ms.openlocfilehash: efdbef39d0e6bf2f07cde2c9621cec173e921752
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73037356"
---
# <a name="strongly-typed-delegates"></a><span data-ttu-id="f01ad-103">Kesin Tür Belirtilmiş Temsilciler</span><span class="sxs-lookup"><span data-stu-id="f01ad-103">Strongly Typed Delegates</span></span>

[<span data-ttu-id="f01ad-104">Öncekini</span><span class="sxs-lookup"><span data-stu-id="f01ad-104">Previous</span></span>](delegate-class.md)

<span data-ttu-id="f01ad-105">Önceki makalede, `delegate` anahtar sözcüğünü kullanarak belirli temsilci türleri oluşturduğunuz gördünüz.</span><span class="sxs-lookup"><span data-stu-id="f01ad-105">In the previous article, you saw that you create specific delegate types using the `delegate` keyword.</span></span> 

<span data-ttu-id="f01ad-106">Soyut temsilci sınıfı, gevşek bağlantısı ve çağırma için altyapıyı sağlar.</span><span class="sxs-lookup"><span data-stu-id="f01ad-106">The abstract Delegate class provide the infrastructure for loose coupling and invocation.</span></span> <span data-ttu-id="f01ad-107">Somut temsilci türleri, bir temsilci nesnesi için çağırma listesine eklenen yöntemler için tür güvenliğini benimseme ve zorlama açısından çok daha yararlı hale gelir.</span><span class="sxs-lookup"><span data-stu-id="f01ad-107">Concrete Delegate types become much more useful by embracing and enforcing type safety for the methods that are added to the invocation list for a delegate object.</span></span> <span data-ttu-id="f01ad-108">`delegate` anahtar sözcüğünü kullandığınızda ve somut bir temsilci türü tanımladığınızda, derleyici bu yöntemleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f01ad-108">When you use the `delegate` keyword and define a concrete delegate type, the compiler generates those methods.</span></span>

<span data-ttu-id="f01ad-109">Uygulamada, bu, farklı bir yöntem imzasına ihtiyacınız olduğunda yeni temsilci türleri oluşturulmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="f01ad-109">In practice, this would lead to creating new delegate types whenever you need a different method signature.</span></span> <span data-ttu-id="f01ad-110">Bu iş bir süre sonra sıkıcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="f01ad-110">This work could get tedious after a time.</span></span> <span data-ttu-id="f01ad-111">Her yeni özellik yeni temsilci türleri gerektirir.</span><span class="sxs-lookup"><span data-stu-id="f01ad-111">Every new feature requires new delegate types.</span></span>

<span data-ttu-id="f01ad-112">Ktam, bu gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="f01ad-112">Thankfully, this isn't necessary.</span></span> <span data-ttu-id="f01ad-113">.NET Core Framework, temsilci türlerine ihtiyacınız olduğunda yeniden kullanabileceğiniz çeşitli türler içerir.</span><span class="sxs-lookup"><span data-stu-id="f01ad-113">The .NET Core framework contains several types that you can reuse whenever you need delegate types.</span></span> <span data-ttu-id="f01ad-114">Bunlar, yeni yöntem bildirimlerine ihtiyacınız olduğunda özelleştirmeler bildirebilmeniz için [genel](programming-guide/generics/index.md) tanımlardır.</span><span class="sxs-lookup"><span data-stu-id="f01ad-114">These are [generic](programming-guide/generics/index.md) definitions so you can declare customizations when you need new method declarations.</span></span> 

<span data-ttu-id="f01ad-115">Bu türlerin ilki <xref:System.Action> türüdür ve çeşitli çeşitlerdir:</span><span class="sxs-lookup"><span data-stu-id="f01ad-115">The first of these types is the <xref:System.Action> type, and several variations:</span></span>

```csharp
public delegate void Action();
public delegate void Action<in T>(T arg);
public delegate void Action<in T1, in T2>(T1 arg1, T2 arg2);
// Other variations removed for brevity.
```

<span data-ttu-id="f01ad-116">Genel tür bağımsız değişkeninde `in` değiştirici, Kovaryans hakkındaki makalede ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="f01ad-116">The `in` modifier on the generic type argument is covered in the article on covariance.</span></span>

<span data-ttu-id="f01ad-117"><xref:System.Action%6016>gibi 16 ' ya kadar bağımsız değişken içeren `Action` temsilcisinin çeşitlemeleri vardır.</span><span class="sxs-lookup"><span data-stu-id="f01ad-117">There are variations of the `Action` delegate that contain up to 16 arguments such as <xref:System.Action%6016>.</span></span>
<span data-ttu-id="f01ad-118">Bu tanımların her bir temsilci bağımsız değişkeni için farklı genel bağımsız değişkenler kullanması önemlidir: Bu, size en fazla esneklik sağlar.</span><span class="sxs-lookup"><span data-stu-id="f01ad-118">It's important that these definitions use different generic arguments for each of the delegate arguments: That gives you maximum flexibility.</span></span> <span data-ttu-id="f01ad-119">Yöntem bağımsız değişkenlerinin aynı olması gerekir, ancak aynı türde olabilir.</span><span class="sxs-lookup"><span data-stu-id="f01ad-119">The method arguments need not be, but may be, the same type.</span></span>

<span data-ttu-id="f01ad-120">Void dönüş türüne sahip herhangi bir temsilci türü için `Action` türlerinden birini kullanın.</span><span class="sxs-lookup"><span data-stu-id="f01ad-120">Use one of the `Action` types for any delegate type that has a void return type.</span></span>

<span data-ttu-id="f01ad-121">Framework Ayrıca değer döndüren temsilci türleri için kullanabileceğiniz çeşitli genel temsilci türleri içerir:</span><span class="sxs-lookup"><span data-stu-id="f01ad-121">The framework also includes several generic delegate types that you can use for delegate types that return values:</span></span>

```csharp
public delegate TResult Func<out TResult>();
public delegate TResult Func<in T1, out TResult>(T1 arg);
public delegate TResult Func<in T1, in T2, out TResult>(T1 arg1, T2 arg2);
// Other variations removed for brevity
```

<span data-ttu-id="f01ad-122">Sonuç genel tür bağımsız değişkeninde `out` değiştirici, Kovaryans hakkındaki makalede ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="f01ad-122">The `out` modifier on the result generic type argument is covered in the article on covariance.</span></span>

<span data-ttu-id="f01ad-123"><xref:System.Func%6017>gibi 16 ' ya kadar giriş bağımsız değişkeni olan `Func` temsilcisinin çeşitlemeleri vardır.</span><span class="sxs-lookup"><span data-stu-id="f01ad-123">There are variations of the `Func` delegate with up to 16 input arguments such as <xref:System.Func%6017>.</span></span>
<span data-ttu-id="f01ad-124">Sonucun türü her zaman kuralına göre tüm `Func` bildirimlerinde son tür parametresidir.</span><span class="sxs-lookup"><span data-stu-id="f01ad-124">The type of the result is always the last type parameter in all the `Func` declarations, by convention.</span></span>

<span data-ttu-id="f01ad-125">Bir değer döndüren herhangi bir temsilci türü için `Func` türlerinden birini kullanın.</span><span class="sxs-lookup"><span data-stu-id="f01ad-125">Use one of the `Func` types for any delegate type that returns a value.</span></span>

<span data-ttu-id="f01ad-126">Ayrıca özelleştirilmiş bir <xref:System.Predicate%601></span><span class="sxs-lookup"><span data-stu-id="f01ad-126">There's also a specialized <xref:System.Predicate%601></span></span> 
<span data-ttu-id="f01ad-127">tek bir değer üzerinde bir test döndüren temsilcinin türü:</span><span class="sxs-lookup"><span data-stu-id="f01ad-127">type for a delegate that returns a test on a single value:</span></span>

```csharp
public delegate bool Predicate<in T>(T obj);
```

<span data-ttu-id="f01ad-128">Herhangi bir `Predicate` türü için yapısal olarak eşdeğer `Func` türünün var olduğunu fark edebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f01ad-128">You may notice that for any `Predicate` type, a structurally equivalent `Func` type exists For example:</span></span>

```csharp
Func<string, bool> TestForString;
Predicate<string> AnotherTestForString;
```

<span data-ttu-id="f01ad-129">Bu iki tür denk olduğunu düşünebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f01ad-129">You might think these two types are equivalent.</span></span> <span data-ttu-id="f01ad-130">Bunlar değildir.</span><span class="sxs-lookup"><span data-stu-id="f01ad-130">They are not.</span></span>
<span data-ttu-id="f01ad-131">Bu iki değişken birbirlerinin yerine kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="f01ad-131">These two variables cannot be used interchangeably.</span></span> <span data-ttu-id="f01ad-132">Bir tür değişkenine diğer tür atanamaz.</span><span class="sxs-lookup"><span data-stu-id="f01ad-132">A variable of one type cannot be assigned the other type.</span></span> <span data-ttu-id="f01ad-133">C# Tür sistemi, yapıyı değil, tanımlı türlerin adlarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="f01ad-133">The C# type system uses the names of the defined types, not the structure.</span></span>

<span data-ttu-id="f01ad-134">.NET Core kitaplığındaki tüm bu temsilci türü tanımları, oluşturduğunuz ve temsilci gerektiren yeni bir özellik için yeni bir temsilci türü tanımlamanız gerekmeyen anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="f01ad-134">All these delegate type definitions in the .NET Core Library should mean that you do not need to define a new delegate type for any new feature you create that requires delegates.</span></span> <span data-ttu-id="f01ad-135">Bu genel tanımlar çoğu durumda ihtiyacınız olan tüm temsilci türlerini sağlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="f01ad-135">These generic definitions should provide all the delegate types you need under most situations.</span></span> <span data-ttu-id="f01ad-136">Gerekli tür parametreleriyle bu türlerden birini basitçe örnekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f01ad-136">You can simply instantiate one of these types with the required type parameters.</span></span> <span data-ttu-id="f01ad-137">Genel hale getirilebilir algoritmalar söz konusu olduğunda, bu Temsilciler genel türler olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f01ad-137">In the case of algorithms that can be made generic, these delegates can be used as generic types.</span></span> 

<span data-ttu-id="f01ad-138">Bu süre zamandan tasarruf etmelidir ve temsilcilerle çalışmak için oluşturmanız gereken yeni tür sayısını en aza indirir.</span><span class="sxs-lookup"><span data-stu-id="f01ad-138">This should save time, and minimize the number of new types that you need to create in order to work with delegates.</span></span>

<span data-ttu-id="f01ad-139">Sonraki makalede, uygulama ortamında temsilcilerle çalışmaya yönelik birkaç ortak desen görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="f01ad-139">In the next article, you'll see several common patterns for working with delegates in practice.</span></span>

[<span data-ttu-id="f01ad-140">Next</span><span class="sxs-lookup"><span data-stu-id="f01ad-140">Next</span></span>](delegates-patterns.md)
