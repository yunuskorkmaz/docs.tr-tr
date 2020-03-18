---
title: Kesin Tür Belirtilmiş Temsilciler
description: Temsilci gerektiren bir özellik oluştururken özel türleri bildirmek için genel temsilci türlerini nasıl kullanacağınızı öğrenin.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: 564a683d-352b-4e57-8bac-b466529daf6b
ms.openlocfilehash: 798e8b597389bc99d10e587ec417a4e717f28abc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146209"
---
# <a name="strongly-typed-delegates"></a><span data-ttu-id="5bb29-103">Kesin Tür Belirtilmiş Temsilciler</span><span class="sxs-lookup"><span data-stu-id="5bb29-103">Strongly Typed Delegates</span></span>

[<span data-ttu-id="5bb29-104">Önceki</span><span class="sxs-lookup"><span data-stu-id="5bb29-104">Previous</span></span>](delegate-class.md)

<span data-ttu-id="5bb29-105">Önceki makalede, anahtar kelimeyi kullanarak belirli temsilci `delegate` türleri oluşturduğunuzu gördünuz.</span><span class="sxs-lookup"><span data-stu-id="5bb29-105">In the previous article, you saw that you create specific delegate types using the `delegate` keyword.</span></span>

<span data-ttu-id="5bb29-106">Soyut Temsilci sınıfı gevşek bağlantı ve çağırma için altyapı sağlar.</span><span class="sxs-lookup"><span data-stu-id="5bb29-106">The abstract Delegate class provide the infrastructure for loose coupling and invocation.</span></span> <span data-ttu-id="5bb29-107">Somut Temsilci türleri, bir temsilci nesnesi için çağırma listesine eklenen yöntemler için tür güvenliğini kucaklayarak ve uygulayarak çok daha kullanışlı hale gelir.</span><span class="sxs-lookup"><span data-stu-id="5bb29-107">Concrete Delegate types become much more useful by embracing and enforcing type safety for the methods that are added to the invocation list for a delegate object.</span></span> <span data-ttu-id="5bb29-108">Anahtar sözcüğü `delegate` kullandığınızda ve somut bir temsilci türü tanımladığınızda, derleyici bu yöntemleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5bb29-108">When you use the `delegate` keyword and define a concrete delegate type, the compiler generates those methods.</span></span>

<span data-ttu-id="5bb29-109">Uygulamada, bu farklı bir yöntem imzası gerektiğinde yeni temsilci türleri oluşturmaya yol açar.</span><span class="sxs-lookup"><span data-stu-id="5bb29-109">In practice, this would lead to creating new delegate types whenever you need a different method signature.</span></span> <span data-ttu-id="5bb29-110">Bu iş bir süre sonra sıkıcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="5bb29-110">This work could get tedious after a time.</span></span> <span data-ttu-id="5bb29-111">Her yeni özellik yeni temsilci türleri gerektirir.</span><span class="sxs-lookup"><span data-stu-id="5bb29-111">Every new feature requires new delegate types.</span></span>

<span data-ttu-id="5bb29-112">Neyse ki buna gerek yok.</span><span class="sxs-lookup"><span data-stu-id="5bb29-112">Thankfully, this isn't necessary.</span></span> <span data-ttu-id="5bb29-113">.NET Core çerçevesi, temsilci türlerine ihtiyacınız olduğunda yeniden kullanabileceğiniz birkaç tür içerir.</span><span class="sxs-lookup"><span data-stu-id="5bb29-113">The .NET Core framework contains several types that you can reuse whenever you need delegate types.</span></span> <span data-ttu-id="5bb29-114">Bunlar [genel](programming-guide/generics/index.md) tanımlardır, böylece yeni yöntem bildirimlerine ihtiyaç duyduğunuzda özelleştirmeleri bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5bb29-114">These are [generic](programming-guide/generics/index.md) definitions so you can declare customizations when you need new method declarations.</span></span>

<span data-ttu-id="5bb29-115">Bu türlerden <xref:System.Action> ilki tür ve çeşitli varyasyonları:</span><span class="sxs-lookup"><span data-stu-id="5bb29-115">The first of these types is the <xref:System.Action> type, and several variations:</span></span>

```csharp
public delegate void Action();
public delegate void Action<in T>(T arg);
public delegate void Action<in T1, in T2>(T1 arg1, T2 arg2);
// Other variations removed for brevity.
```

<span data-ttu-id="5bb29-116">Genel `in` tür bağımsız değişkeninde değiştirici covariance makalede ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="5bb29-116">The `in` modifier on the generic type argument is covered in the article on covariance.</span></span>

<span data-ttu-id="5bb29-117">Temsilcinin `Action` 16'ya kadar bağımsız değişken içeren <xref:System.Action%6016>varyasyonları vardır.</span><span class="sxs-lookup"><span data-stu-id="5bb29-117">There are variations of the `Action` delegate that contain up to 16 arguments such as <xref:System.Action%6016>.</span></span>
<span data-ttu-id="5bb29-118">Bu tanımların her bir temsilci bağımsız değişkeni için farklı genel bağımsız değişkenler kullanması önemlidir: Bu size maksimum esneklik sağlar.</span><span class="sxs-lookup"><span data-stu-id="5bb29-118">It's important that these definitions use different generic arguments for each of the delegate arguments: That gives you maximum flexibility.</span></span> <span data-ttu-id="5bb29-119">Yöntem bağımsız değişkenleri gerek meç, ancak olabilir, aynı türde.</span><span class="sxs-lookup"><span data-stu-id="5bb29-119">The method arguments need not be, but may be, the same type.</span></span>

<span data-ttu-id="5bb29-120">Geçersiz dönüş `Action` türü olan herhangi bir temsilci türü için türlerden birini kullanın.</span><span class="sxs-lookup"><span data-stu-id="5bb29-120">Use one of the `Action` types for any delegate type that has a void return type.</span></span>

<span data-ttu-id="5bb29-121">Çerçeve, değerleri döndüren temsilci türleri için kullanabileceğiniz birkaç genel temsilci türü de içerir:</span><span class="sxs-lookup"><span data-stu-id="5bb29-121">The framework also includes several generic delegate types that you can use for delegate types that return values:</span></span>

```csharp
public delegate TResult Func<out TResult>();
public delegate TResult Func<in T1, out TResult>(T1 arg);
public delegate TResult Func<in T1, in T2, out TResult>(T1 arg1, T2 arg2);
// Other variations removed for brevity
```

<span data-ttu-id="5bb29-122">Sonuç `out` genel türü bağımsız değişkeninde değiştirici, tutarlılık makalesinde ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="5bb29-122">The `out` modifier on the result generic type argument is covered in the article on covariance.</span></span>

<span data-ttu-id="5bb29-123">`Func` 'ye kadar 16 giriş bağımsız değişkeni olan <xref:System.Func%6017>temsilcinin varyasyonları vardır.</span><span class="sxs-lookup"><span data-stu-id="5bb29-123">There are variations of the `Func` delegate with up to 16 input arguments such as <xref:System.Func%6017>.</span></span>
<span data-ttu-id="5bb29-124">Sonucun türü, tüm `Func` bildirimlerdeki son tür parametresi, konvansiyona göre her zaman dır.</span><span class="sxs-lookup"><span data-stu-id="5bb29-124">The type of the result is always the last type parameter in all the `Func` declarations, by convention.</span></span>

<span data-ttu-id="5bb29-125">Bir değer `Func` döndüren herhangi bir temsilci türü için türlerden birini kullanın.</span><span class="sxs-lookup"><span data-stu-id="5bb29-125">Use one of the `Func` types for any delegate type that returns a value.</span></span>

<span data-ttu-id="5bb29-126">Ayrıca özel bir<xref:System.Predicate%601></span><span class="sxs-lookup"><span data-stu-id="5bb29-126">There's also a specialized <xref:System.Predicate%601></span></span>
<span data-ttu-id="5bb29-127">tek bir değer üzerinde bir test döndüren bir temsilci için yazın:</span><span class="sxs-lookup"><span data-stu-id="5bb29-127">type for a delegate that returns a test on a single value:</span></span>

```csharp
public delegate bool Predicate<in T>(T obj);
```

<span data-ttu-id="5bb29-128">Herhangi bir `Predicate` tür için, yapısal olarak `Func` eşdeğer bir tür örneğin var fark edebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5bb29-128">You may notice that for any `Predicate` type, a structurally equivalent `Func` type exists For example:</span></span>

```csharp
Func<string, bool> TestForString;
Predicate<string> AnotherTestForString;
```

<span data-ttu-id="5bb29-129">Bu iki tür eşdeğer olduğunu düşünebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5bb29-129">You might think these two types are equivalent.</span></span> <span data-ttu-id="5bb29-130">Değiller.</span><span class="sxs-lookup"><span data-stu-id="5bb29-130">They are not.</span></span>
<span data-ttu-id="5bb29-131">Bu iki değişken birbirinin yerine kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="5bb29-131">These two variables cannot be used interchangeably.</span></span> <span data-ttu-id="5bb29-132">Bir türden bir değişken diğer türe atanamaz.</span><span class="sxs-lookup"><span data-stu-id="5bb29-132">A variable of one type cannot be assigned the other type.</span></span> <span data-ttu-id="5bb29-133">C# türü sistem, yapıyı değil, tanımlanan türlerin adlarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="5bb29-133">The C# type system uses the names of the defined types, not the structure.</span></span>

<span data-ttu-id="5bb29-134">.NET Core Kitaplığı'ndaki tüm bu temsilci türü tanımları, oluşturduğunuz herhangi bir yeni özellik için temsilci gerektiren yeni bir temsilci türü tanımlamanız gerekolmadığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="5bb29-134">All these delegate type definitions in the .NET Core Library should mean that you do not need to define a new delegate type for any new feature you create that requires delegates.</span></span> <span data-ttu-id="5bb29-135">Bu genel tanımlar, çoğu durumda gereksinim duyduğunuz tüm temsilci türlerini sağlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="5bb29-135">These generic definitions should provide all the delegate types you need under most situations.</span></span> <span data-ttu-id="5bb29-136">Bu türlerden birini gerekli tür parametreleri ile anında kolayca anlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5bb29-136">You can simply instantiate one of these types with the required type parameters.</span></span> <span data-ttu-id="5bb29-137">Genel yapIlebilen algoritmalar söz konusu olduğunda, bu temsilciler genel türler olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5bb29-137">In the case of algorithms that can be made generic, these delegates can be used as generic types.</span></span>

<span data-ttu-id="5bb29-138">Bu, zamandan tasarruf etmeli ve temsilcilerle çalışmak için oluşturmanız gereken yeni türlerin sayısını en aza indirir.</span><span class="sxs-lookup"><span data-stu-id="5bb29-138">This should save time, and minimize the number of new types that you need to create in order to work with delegates.</span></span>

<span data-ttu-id="5bb29-139">Sonraki makalede, uygulamada temsilcilerle çalışmak için çeşitli ortak desenler görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="5bb29-139">In the next article, you'll see several common patterns for working with delegates in practice.</span></span>

[<span data-ttu-id="5bb29-140">Sonraki</span><span class="sxs-lookup"><span data-stu-id="5bb29-140">Next</span></span>](delegates-patterns.md)
