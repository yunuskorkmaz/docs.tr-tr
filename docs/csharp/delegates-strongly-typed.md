---
title: "Kesin türü belirtilmiş temsilciler"
description: "Genel temsilci türleri temsilciler gerektiren bir özellik oluştururken, özel türler bildirmek için nasıl kullanılacağını öğrenin."
keywords: .NET, .NET core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 564a683d-352b-4e57-8bac-b466529daf6b
ms.openlocfilehash: 467ba18f8e032b9b3b8f480d4b10c92d0d7ba3b9
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/21/2017
---
# <a name="strongly-typed-delegates"></a><span data-ttu-id="a5ef7-104">Kesin türü belirtilmiş temsilciler</span><span class="sxs-lookup"><span data-stu-id="a5ef7-104">Strongly Typed Delegates</span></span>

[<span data-ttu-id="a5ef7-105">Önceki</span><span class="sxs-lookup"><span data-stu-id="a5ef7-105">Previous</span></span>](delegate-class.md)

<span data-ttu-id="a5ef7-106">Önceki makalede belirli temsilci kullanarak türleri oluşturmak gördüğünüz `delegate` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="a5ef7-106">In the previous article, you saw that you create specific delegate types using the `delegate` keyword.</span></span> 

<span data-ttu-id="a5ef7-107">Özet temsilci sınıf gevşek bağlantı ve çağırma için altyapı sağlar.</span><span class="sxs-lookup"><span data-stu-id="a5ef7-107">The abstract Delegate class provide the infrastructure for loose coupling and invocation.</span></span> <span data-ttu-id="a5ef7-108">Somut temsilci türleri kucaklamakta ve tür güvenliği için temsilci nesnesini çağırma listesine eklenen yöntemleri için zorlamayı göre çok daha yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="a5ef7-108">Concrete Delegate types become much more useful by embracing and enforcing type safety for the methods that are added to the invocation list for a delegate object.</span></span> <span data-ttu-id="a5ef7-109">Kullandığınızda `delegate` anahtar sözcüğü ve somut temsilci türünü tanımlayın, bu yöntemleri derleyici oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a5ef7-109">When you use the `delegate` keyword and define a concrete delegate type, the compiler generates those methods.</span></span>

<span data-ttu-id="a5ef7-110">Uygulamada, bu farklı yöntem imzası gereksinim duyduğunuzda, yeni temsilci türleri oluşturmak için yol açar.</span><span class="sxs-lookup"><span data-stu-id="a5ef7-110">In practice, this would lead to creating new delegate types whenever you need a different method signature.</span></span> <span data-ttu-id="a5ef7-111">Bir süre sonra bu işi sıkıcı.</span><span class="sxs-lookup"><span data-stu-id="a5ef7-111">This work could get tedious after a time.</span></span> <span data-ttu-id="a5ef7-112">Her yeni özellik, yeni temsilci türleri gerektirir.</span><span class="sxs-lookup"><span data-stu-id="a5ef7-112">Every new feature requires new delegate types.</span></span>

<span data-ttu-id="a5ef7-113">Thankfully, bu gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="a5ef7-113">Thankfully, this isn't necessary.</span></span> <span data-ttu-id="a5ef7-114">.NET Core framework türleri temsilci olduğunda yeniden kullanabilir birkaç türlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="a5ef7-114">The .NET Core framework contains several types that you can reuse whenever you need delegate types.</span></span> <span data-ttu-id="a5ef7-115">Bunlar [genel](programming-guide/generics/index.md) yeni yöntem bildirimleri gerektiğinde özelleştirmeleri bildirebilir şekilde tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a5ef7-115">These are [generic](programming-guide/generics/index.md) definitions so you can declare customizations when you need new method declarations.</span></span> 

<span data-ttu-id="a5ef7-116">Bu tür ilk <xref:System.Action> türü ve birkaç Çeşitlemeler:</span><span class="sxs-lookup"><span data-stu-id="a5ef7-116">The first of these types is the <xref:System.Action> type, and several variations:</span></span>

```csharp
public delegate void Action();
public delegate void Action<in T>(T arg);
public delegate void Action<in T1, in T2>(T1 arg1, T2 arg2);
// Other variations removed for brevity.
```

<span data-ttu-id="a5ef7-117">`in` Genel tür bağımsız değişkeni değiştiricisi Kovaryans makalede ele alınan.</span><span class="sxs-lookup"><span data-stu-id="a5ef7-117">The `in` modifier on the generic type argument is covered in the article on covariance.</span></span>

<span data-ttu-id="a5ef7-118">Çeşidi vardır `Action` en fazla 16 bağımsız değişkenler gibi içeren temsilci <xref:System.Action%6016>.</span><span class="sxs-lookup"><span data-stu-id="a5ef7-118">There are variations of the `Action` delegate that contain up to 16 arguments such as <xref:System.Action%6016>.</span></span>
<span data-ttu-id="a5ef7-119">Bu tanımları farklı genel değişkenleri temsilci değişkenin her biri için kullanın önemli: Bu, en büyük esnekliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="a5ef7-119">It's important that these definitions use different generic arguments for each of the delegate arguments: That gives you maximum flexibility.</span></span> <span data-ttu-id="a5ef7-120">Yöntem bağımsız değişkenleri olmaması, ancak olabilir, aynı türde.</span><span class="sxs-lookup"><span data-stu-id="a5ef7-120">The method arguments need not be, but may be, the same type.</span></span>

<span data-ttu-id="a5ef7-121">Aşağıdakilerden birini kullanmak `Action` türleri için geçersiz bir dönüş türüne sahip herhangi bir temsilci türü.</span><span class="sxs-lookup"><span data-stu-id="a5ef7-121">Use one of the `Action` types for any delegate type that has a void return type.</span></span>

<span data-ttu-id="a5ef7-122">Framework de dönüş değerleri temsilci türleri için kullanabileceğiniz birkaç genel temsilci türleri içerir:</span><span class="sxs-lookup"><span data-stu-id="a5ef7-122">The framework also includes several generic delegate types that you can use for delegate types that return values:</span></span>

```csharp
public delegate TResult Func<out TResult>();
public delegate TResult Func<in T1, out TResult>(T1 arg);
public delegate TResult Func<in T1, in T2, out TResult>(T1 arg1, T2 arg2);
// Other variations removed for brevity
```

<span data-ttu-id="a5ef7-123">`out` Sonuç genel tür bağımsız değişkeni değiştiricisi Kovaryans makalede ele alınan.</span><span class="sxs-lookup"><span data-stu-id="a5ef7-123">The `out` modifier on the result generic type argument is covered in the article on covariance.</span></span>

<span data-ttu-id="a5ef7-124">Çeşidi vardır `Func` en fazla 16 giriş bağımsız değişkeni ile gibi temsilci <xref:System.Func%6017>.</span><span class="sxs-lookup"><span data-stu-id="a5ef7-124">There are variations of the `Func` delegate with up to 16 input arguments such as <xref:System.Func%6017>.</span></span>
<span data-ttu-id="a5ef7-125">Sonuç türü her zaman son türü tüm parametredir `Func` kural tarafından bildirimleri.</span><span class="sxs-lookup"><span data-stu-id="a5ef7-125">The type of the result is always the last type parameter in all the `Func` declarations, by convention.</span></span>

<span data-ttu-id="a5ef7-126">Aşağıdakilerden birini kullanmak `Func` türleri için bir değer döndürür herhangi bir temsilci türü.</span><span class="sxs-lookup"><span data-stu-id="a5ef7-126">Use one of the `Func` types for any delegate type that returns a value.</span></span>

<span data-ttu-id="a5ef7-127">Yoktur ayrıca özel <xref:System.Predicate%601> türü bir test üzerinde tek bir değer döndüren bir temsilci için:</span><span class="sxs-lookup"><span data-stu-id="a5ef7-127">There's also a specialized <xref:System.Predicate%601> type for a delegate that returns a test on a single value:</span></span>

```csharp
public delegate bool Predicate<in T>(T obj);
```

<span data-ttu-id="a5ef7-128">Sizin için değiştiğini görebilirsiniz `Predicate` türü, yapısal olarak eşdeğer `Func` türü mevcut örneğin:</span><span class="sxs-lookup"><span data-stu-id="a5ef7-128">You may notice that for any `Predicate` type, a structurally equivalent `Func` type exists For example:</span></span>

```csharp
Func<string, bool> TestForString;
Predicate<string> AnotherTestForString;
```

<span data-ttu-id="a5ef7-129">Bu iki tür eşdeğer düşünebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a5ef7-129">You might think these two types are equivalent.</span></span> <span data-ttu-id="a5ef7-130">Bunlar değildir.</span><span class="sxs-lookup"><span data-stu-id="a5ef7-130">They are not.</span></span>
<span data-ttu-id="a5ef7-131">Bu iki değişken birbirinin yerine kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="a5ef7-131">These two variables cannot be used interchangeably.</span></span> <span data-ttu-id="a5ef7-132">Bir türde bir değişken diğer tür atanamaz.</span><span class="sxs-lookup"><span data-stu-id="a5ef7-132">A variable of one type cannot be assigned the other type.</span></span> <span data-ttu-id="a5ef7-133">C# tür sistemi yapısı tanımlı türlerinin adlarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="a5ef7-133">The C# type system uses the names of the defined types, not the structure.</span></span>

<span data-ttu-id="a5ef7-134">.NET Core kitaplığı tanımlarında herhangi bir yeni özellik için yeni bir temsilci türü tanımlamanız gerekmez anlamına Bu temsilci türü temsilciler gerektiren oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a5ef7-134">All these delegate type definitions in the .NET Core Library should mean that you do not need to define a new delegate type for any new feature you create that requires delegates.</span></span> <span data-ttu-id="a5ef7-135">Bu genel tanımları tüm temsilci altında çoğu durumlar gereken türleri sağlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="a5ef7-135">These generic definitions should provide all the delegate types you need under most situations.</span></span> <span data-ttu-id="a5ef7-136">Yalnızca gerekli tür parametreleri ile şu türlerden birine örneğini oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a5ef7-136">You can simply instantiate one of these types with the required type parameters.</span></span> <span data-ttu-id="a5ef7-137">Genel hale getirilebilir algoritmaları söz konusu olduğunda, bu temsilciler genel türleri olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a5ef7-137">In the case of algorithms that can be made generic, these delegates can be used as generic types.</span></span> 

<span data-ttu-id="a5ef7-138">Bu zamandan tasarruf ve temsilciler ile çalışması için oluşturmanıza gerek yeni türleri sayısını en aza indirin.</span><span class="sxs-lookup"><span data-stu-id="a5ef7-138">This should save time, and minimize the number of new types that you need to create in order to work with delegates.</span></span>

<span data-ttu-id="a5ef7-139">Sonraki makalede temsilciler uygulamada çalışmak için birkaç ortak desenler görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="a5ef7-139">In the next article, you'll see several common patterns for working with delegates in practice.</span></span>

[<span data-ttu-id="a5ef7-140">Sonraki</span><span class="sxs-lookup"><span data-stu-id="a5ef7-140">Next</span></span>](delegates-patterns.md)
