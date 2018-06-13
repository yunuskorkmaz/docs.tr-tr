---
title: Kesin türü belirtilmiş temsilciler
description: Genel temsilci türleri temsilciler gerektiren bir özellik oluştururken, özel türler bildirmek için nasıl kullanılacağını öğrenin.
ms.date: 06/20/2016
ms.assetid: 564a683d-352b-4e57-8bac-b466529daf6b
ms.openlocfilehash: 2e4cc1c7bfa0aaa90f3aaefa0da64c5486a9d10f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33215170"
---
# <a name="strongly-typed-delegates"></a><span data-ttu-id="2a7af-103">Kesin türü belirtilmiş temsilciler</span><span class="sxs-lookup"><span data-stu-id="2a7af-103">Strongly Typed Delegates</span></span>

[<span data-ttu-id="2a7af-104">Önceki</span><span class="sxs-lookup"><span data-stu-id="2a7af-104">Previous</span></span>](delegate-class.md)

<span data-ttu-id="2a7af-105">Önceki makalede belirli temsilci kullanarak türleri oluşturmak gördüğünüz `delegate` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="2a7af-105">In the previous article, you saw that you create specific delegate types using the `delegate` keyword.</span></span> 

<span data-ttu-id="2a7af-106">Özet temsilci sınıf gevşek bağlantı ve çağırma için altyapı sağlar.</span><span class="sxs-lookup"><span data-stu-id="2a7af-106">The abstract Delegate class provide the infrastructure for loose coupling and invocation.</span></span> <span data-ttu-id="2a7af-107">Somut temsilci türleri kucaklamakta ve tür güvenliği için temsilci nesnesini çağırma listesine eklenen yöntemleri için zorlamayı göre çok daha yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="2a7af-107">Concrete Delegate types become much more useful by embracing and enforcing type safety for the methods that are added to the invocation list for a delegate object.</span></span> <span data-ttu-id="2a7af-108">Kullandığınızda `delegate` anahtar sözcüğü ve somut temsilci türünü tanımlayın, bu yöntemleri derleyici oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2a7af-108">When you use the `delegate` keyword and define a concrete delegate type, the compiler generates those methods.</span></span>

<span data-ttu-id="2a7af-109">Uygulamada, bu farklı yöntem imzası gereksinim duyduğunuzda, yeni temsilci türleri oluşturmak için yol açar.</span><span class="sxs-lookup"><span data-stu-id="2a7af-109">In practice, this would lead to creating new delegate types whenever you need a different method signature.</span></span> <span data-ttu-id="2a7af-110">Bir süre sonra bu işi sıkıcı.</span><span class="sxs-lookup"><span data-stu-id="2a7af-110">This work could get tedious after a time.</span></span> <span data-ttu-id="2a7af-111">Her yeni özellik, yeni temsilci türleri gerektirir.</span><span class="sxs-lookup"><span data-stu-id="2a7af-111">Every new feature requires new delegate types.</span></span>

<span data-ttu-id="2a7af-112">Thankfully, bu gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="2a7af-112">Thankfully, this isn't necessary.</span></span> <span data-ttu-id="2a7af-113">.NET Core framework türleri temsilci olduğunda yeniden kullanabilir birkaç türlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="2a7af-113">The .NET Core framework contains several types that you can reuse whenever you need delegate types.</span></span> <span data-ttu-id="2a7af-114">Bunlar [genel](programming-guide/generics/index.md) yeni yöntem bildirimleri gerektiğinde özelleştirmeleri bildirebilir şekilde tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2a7af-114">These are [generic](programming-guide/generics/index.md) definitions so you can declare customizations when you need new method declarations.</span></span> 

<span data-ttu-id="2a7af-115">Bu tür ilk <xref:System.Action> türü ve birkaç Çeşitlemeler:</span><span class="sxs-lookup"><span data-stu-id="2a7af-115">The first of these types is the <xref:System.Action> type, and several variations:</span></span>

```csharp
public delegate void Action();
public delegate void Action<in T>(T arg);
public delegate void Action<in T1, in T2>(T1 arg1, T2 arg2);
// Other variations removed for brevity.
```

<span data-ttu-id="2a7af-116">`in` Genel tür bağımsız değişkeni değiştiricisi Kovaryans makalede ele alınan.</span><span class="sxs-lookup"><span data-stu-id="2a7af-116">The `in` modifier on the generic type argument is covered in the article on covariance.</span></span>

<span data-ttu-id="2a7af-117">Çeşidi vardır `Action` en fazla 16 bağımsız değişkenler gibi içeren temsilci <xref:System.Action%6016>.</span><span class="sxs-lookup"><span data-stu-id="2a7af-117">There are variations of the `Action` delegate that contain up to 16 arguments such as <xref:System.Action%6016>.</span></span>
<span data-ttu-id="2a7af-118">Bu tanımları farklı genel değişkenleri temsilci değişkenin her biri için kullanın önemli: Bu, en büyük esnekliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="2a7af-118">It's important that these definitions use different generic arguments for each of the delegate arguments: That gives you maximum flexibility.</span></span> <span data-ttu-id="2a7af-119">Yöntem bağımsız değişkenleri olmaması, ancak olabilir, aynı türde.</span><span class="sxs-lookup"><span data-stu-id="2a7af-119">The method arguments need not be, but may be, the same type.</span></span>

<span data-ttu-id="2a7af-120">Aşağıdakilerden birini kullanmak `Action` türleri için geçersiz bir dönüş türüne sahip herhangi bir temsilci türü.</span><span class="sxs-lookup"><span data-stu-id="2a7af-120">Use one of the `Action` types for any delegate type that has a void return type.</span></span>

<span data-ttu-id="2a7af-121">Framework de dönüş değerleri temsilci türleri için kullanabileceğiniz birkaç genel temsilci türleri içerir:</span><span class="sxs-lookup"><span data-stu-id="2a7af-121">The framework also includes several generic delegate types that you can use for delegate types that return values:</span></span>

```csharp
public delegate TResult Func<out TResult>();
public delegate TResult Func<in T1, out TResult>(T1 arg);
public delegate TResult Func<in T1, in T2, out TResult>(T1 arg1, T2 arg2);
// Other variations removed for brevity
```

<span data-ttu-id="2a7af-122">`out` Sonuç genel tür bağımsız değişkeni değiştiricisi Kovaryans makalede ele alınan.</span><span class="sxs-lookup"><span data-stu-id="2a7af-122">The `out` modifier on the result generic type argument is covered in the article on covariance.</span></span>

<span data-ttu-id="2a7af-123">Çeşidi vardır `Func` en fazla 16 giriş bağımsız değişkeni ile gibi temsilci <xref:System.Func%6017>.</span><span class="sxs-lookup"><span data-stu-id="2a7af-123">There are variations of the `Func` delegate with up to 16 input arguments such as <xref:System.Func%6017>.</span></span>
<span data-ttu-id="2a7af-124">Sonuç türü her zaman son türü tüm parametredir `Func` kural tarafından bildirimleri.</span><span class="sxs-lookup"><span data-stu-id="2a7af-124">The type of the result is always the last type parameter in all the `Func` declarations, by convention.</span></span>

<span data-ttu-id="2a7af-125">Aşağıdakilerden birini kullanmak `Func` türleri için bir değer döndürür herhangi bir temsilci türü.</span><span class="sxs-lookup"><span data-stu-id="2a7af-125">Use one of the `Func` types for any delegate type that returns a value.</span></span>

<span data-ttu-id="2a7af-126">Yoktur ayrıca özel <xref:System.Predicate%601> türü bir test üzerinde tek bir değer döndüren bir temsilci için:</span><span class="sxs-lookup"><span data-stu-id="2a7af-126">There's also a specialized <xref:System.Predicate%601> type for a delegate that returns a test on a single value:</span></span>

```csharp
public delegate bool Predicate<in T>(T obj);
```

<span data-ttu-id="2a7af-127">Sizin için değiştiğini görebilirsiniz `Predicate` türü, yapısal olarak eşdeğer `Func` türü mevcut örneğin:</span><span class="sxs-lookup"><span data-stu-id="2a7af-127">You may notice that for any `Predicate` type, a structurally equivalent `Func` type exists For example:</span></span>

```csharp
Func<string, bool> TestForString;
Predicate<string> AnotherTestForString;
```

<span data-ttu-id="2a7af-128">Bu iki tür eşdeğer düşünebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2a7af-128">You might think these two types are equivalent.</span></span> <span data-ttu-id="2a7af-129">Bunlar değildir.</span><span class="sxs-lookup"><span data-stu-id="2a7af-129">They are not.</span></span>
<span data-ttu-id="2a7af-130">Bu iki değişken birbirinin yerine kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="2a7af-130">These two variables cannot be used interchangeably.</span></span> <span data-ttu-id="2a7af-131">Bir türde bir değişken diğer tür atanamaz.</span><span class="sxs-lookup"><span data-stu-id="2a7af-131">A variable of one type cannot be assigned the other type.</span></span> <span data-ttu-id="2a7af-132">C# tür sistemi yapısı tanımlı türlerinin adlarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="2a7af-132">The C# type system uses the names of the defined types, not the structure.</span></span>

<span data-ttu-id="2a7af-133">.NET Core kitaplığı tanımlarında herhangi bir yeni özellik için yeni bir temsilci türü tanımlamanız gerekmez anlamına Bu temsilci türü temsilciler gerektiren oluşturun.</span><span class="sxs-lookup"><span data-stu-id="2a7af-133">All these delegate type definitions in the .NET Core Library should mean that you do not need to define a new delegate type for any new feature you create that requires delegates.</span></span> <span data-ttu-id="2a7af-134">Bu genel tanımları tüm temsilci altında çoğu durumlar gereken türleri sağlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="2a7af-134">These generic definitions should provide all the delegate types you need under most situations.</span></span> <span data-ttu-id="2a7af-135">Yalnızca gerekli tür parametreleri ile şu türlerden birine örneğini oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2a7af-135">You can simply instantiate one of these types with the required type parameters.</span></span> <span data-ttu-id="2a7af-136">Genel hale getirilebilir algoritmaları söz konusu olduğunda, bu temsilciler genel türleri olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2a7af-136">In the case of algorithms that can be made generic, these delegates can be used as generic types.</span></span> 

<span data-ttu-id="2a7af-137">Bu zamandan tasarruf ve temsilciler ile çalışması için oluşturmanıza gerek yeni türleri sayısını en aza indirin.</span><span class="sxs-lookup"><span data-stu-id="2a7af-137">This should save time, and minimize the number of new types that you need to create in order to work with delegates.</span></span>

<span data-ttu-id="2a7af-138">Sonraki makalede temsilciler uygulamada çalışmak için birkaç ortak desenler görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="2a7af-138">In the next article, you'll see several common patterns for working with delegates in practice.</span></span>

[<span data-ttu-id="2a7af-139">Next</span><span class="sxs-lookup"><span data-stu-id="2a7af-139">Next</span></span>](delegates-patterns.md)
