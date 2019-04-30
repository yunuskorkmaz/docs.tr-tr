---
title: Kesin tür belirtilmiş temsilciler
description: Özel türler temsilciler gerektiren bir özellik oluştururken bildirmek için genel temsilci türleriyle kullanmayı öğrenin.
ms.date: 06/20/2016
ms.assetid: 564a683d-352b-4e57-8bac-b466529daf6b
ms.openlocfilehash: 2e4cc1c7bfa0aaa90f3aaefa0da64c5486a9d10f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61646666"
---
# <a name="strongly-typed-delegates"></a><span data-ttu-id="43926-103">Kesin tür belirtilmiş temsilciler</span><span class="sxs-lookup"><span data-stu-id="43926-103">Strongly Typed Delegates</span></span>

[<span data-ttu-id="43926-104">Önceki</span><span class="sxs-lookup"><span data-stu-id="43926-104">Previous</span></span>](delegate-class.md)

<span data-ttu-id="43926-105">Önceki makalede türleri kullanarak belirli bir temsilci oluşturmak, gördüğünüz `delegate` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="43926-105">In the previous article, you saw that you create specific delegate types using the `delegate` keyword.</span></span> 

<span data-ttu-id="43926-106">Soyut temsilci sınıfı gevşek eşleştirme ve çağırma için altyapı sağlar.</span><span class="sxs-lookup"><span data-stu-id="43926-106">The abstract Delegate class provide the infrastructure for loose coupling and invocation.</span></span> <span data-ttu-id="43926-107">Somut temsilci türleri benimsemenin ve tür güvenliği için bir temsilci nesnesini çağırma listesine eklenen yöntemleri için zorlama göre çok daha kullanışlı olur.</span><span class="sxs-lookup"><span data-stu-id="43926-107">Concrete Delegate types become much more useful by embracing and enforcing type safety for the methods that are added to the invocation list for a delegate object.</span></span> <span data-ttu-id="43926-108">Kullanırken `delegate` anahtar sözcüğü ve bir somut bir temsilci türü tanımlamak, derleyici bu yöntemleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="43926-108">When you use the `delegate` keyword and define a concrete delegate type, the compiler generates those methods.</span></span>

<span data-ttu-id="43926-109">Uygulamada, bu farklı yöntem imzası ihtiyaç duyduğunuzda, yeni temsilci türlerini oluşturmak için yol açar.</span><span class="sxs-lookup"><span data-stu-id="43926-109">In practice, this would lead to creating new delegate types whenever you need a different method signature.</span></span> <span data-ttu-id="43926-110">Bir süre sonra bu iş sıkıcı.</span><span class="sxs-lookup"><span data-stu-id="43926-110">This work could get tedious after a time.</span></span> <span data-ttu-id="43926-111">Her yeni özellik, yeni temsilci türleri gerektirir.</span><span class="sxs-lookup"><span data-stu-id="43926-111">Every new feature requires new delegate types.</span></span>

<span data-ttu-id="43926-112">Ne bu gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="43926-112">Thankfully, this isn't necessary.</span></span> <span data-ttu-id="43926-113">.NET Core framework temsilci türleri olduğunda yeniden kullanabileceğiniz çeşitli türleri içerir.</span><span class="sxs-lookup"><span data-stu-id="43926-113">The .NET Core framework contains several types that you can reuse whenever you need delegate types.</span></span> <span data-ttu-id="43926-114">Bunlar [genel](programming-guide/generics/index.md) yeni yöntem bildirimleri gerektiğinde özelleştirmeleri bildirebilirsiniz şekilde tanımlar.</span><span class="sxs-lookup"><span data-stu-id="43926-114">These are [generic](programming-guide/generics/index.md) definitions so you can declare customizations when you need new method declarations.</span></span> 

<span data-ttu-id="43926-115">Bu türlerinin ilki <xref:System.Action> türü ve çeşitli kullanımları tercih edilebilir:</span><span class="sxs-lookup"><span data-stu-id="43926-115">The first of these types is the <xref:System.Action> type, and several variations:</span></span>

```csharp
public delegate void Action();
public delegate void Action<in T>(T arg);
public delegate void Action<in T1, in T2>(T1 arg1, T2 arg2);
// Other variations removed for brevity.
```

<span data-ttu-id="43926-116">`in` Makalede Kovaryans genel tür bağımsız değişkeni değiştiricisi alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="43926-116">The `in` modifier on the generic type argument is covered in the article on covariance.</span></span>

<span data-ttu-id="43926-117">Çeşidi vardır `Action` gibi en fazla 16 bağımsız değişkenleri içeren bir temsilci <xref:System.Action%6016>.</span><span class="sxs-lookup"><span data-stu-id="43926-117">There are variations of the `Action` delegate that contain up to 16 arguments such as <xref:System.Action%6016>.</span></span>
<span data-ttu-id="43926-118">Bu tanımları temsilci değişkenin her biri için farklı genel bağımsız değişkenleri kullanmak önemlidir: Bu, en yüksek esnekliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="43926-118">It's important that these definitions use different generic arguments for each of the delegate arguments: That gives you maximum flexibility.</span></span> <span data-ttu-id="43926-119">Yöntem bağımsız değişkenleri olmaması, ancak olabilir, aynı türde.</span><span class="sxs-lookup"><span data-stu-id="43926-119">The method arguments need not be, but may be, the same type.</span></span>

<span data-ttu-id="43926-120">Birini `Action` türleri için dönüş türü void olan herhangi bir temsilci türü.</span><span class="sxs-lookup"><span data-stu-id="43926-120">Use one of the `Action` types for any delegate type that has a void return type.</span></span>

<span data-ttu-id="43926-121">Framework, dönüş değerleri temsilci türleri için kullanabileceğiniz çeşitli genel temsilci türleriyle de içerir:</span><span class="sxs-lookup"><span data-stu-id="43926-121">The framework also includes several generic delegate types that you can use for delegate types that return values:</span></span>

```csharp
public delegate TResult Func<out TResult>();
public delegate TResult Func<in T1, out TResult>(T1 arg);
public delegate TResult Func<in T1, in T2, out TResult>(T1 arg1, T2 arg2);
// Other variations removed for brevity
```

<span data-ttu-id="43926-122">`out` Sonucu genel tür bağımsız değişkeni değiştiricisi Kovaryans makalede ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="43926-122">The `out` modifier on the result generic type argument is covered in the article on covariance.</span></span>

<span data-ttu-id="43926-123">Çeşidi vardır `Func` gibi en fazla 16 giriş bağımsız değişkeni ile temsilci <xref:System.Func%6017>.</span><span class="sxs-lookup"><span data-stu-id="43926-123">There are variations of the `Func` delegate with up to 16 input arguments such as <xref:System.Func%6017>.</span></span>
<span data-ttu-id="43926-124">Sonuç türü her zaman son tür parametresinde tüm olan `Func` bildirimleri, kural tarafından.</span><span class="sxs-lookup"><span data-stu-id="43926-124">The type of the result is always the last type parameter in all the `Func` declarations, by convention.</span></span>

<span data-ttu-id="43926-125">Birini `Func` türleri için bir değer döndüren bir temsilci türü.</span><span class="sxs-lookup"><span data-stu-id="43926-125">Use one of the `Func` types for any delegate type that returns a value.</span></span>

<span data-ttu-id="43926-126">Var. Ayrıca özelleştirilmiş <xref:System.Predicate%601></span><span class="sxs-lookup"><span data-stu-id="43926-126">There's also a specialized <xref:System.Predicate%601></span></span> 
<span data-ttu-id="43926-127">bir test üzerinde tek bir değer döndüren bir temsilci için şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="43926-127">type for a delegate that returns a test on a single value:</span></span>

```csharp
public delegate bool Predicate<in T>(T obj);
```

<span data-ttu-id="43926-128">Sizin için değiştiğini görebilirsiniz `Predicate` türü, yapısal olarak eşdeğer `Func` türü mevcut örneğin:</span><span class="sxs-lookup"><span data-stu-id="43926-128">You may notice that for any `Predicate` type, a structurally equivalent `Func` type exists For example:</span></span>

```csharp
Func<string, bool> TestForString;
Predicate<string> AnotherTestForString;
```

<span data-ttu-id="43926-129">Bu iki tür eşdeğerdir düşünebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="43926-129">You might think these two types are equivalent.</span></span> <span data-ttu-id="43926-130">Değiller.</span><span class="sxs-lookup"><span data-stu-id="43926-130">They are not.</span></span>
<span data-ttu-id="43926-131">Bu iki değişken birbirinin yerine kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="43926-131">These two variables cannot be used interchangeably.</span></span> <span data-ttu-id="43926-132">Bir değişken, bir tür diğer türden atanamaz.</span><span class="sxs-lookup"><span data-stu-id="43926-132">A variable of one type cannot be assigned the other type.</span></span> <span data-ttu-id="43926-133">C# Tür sistemi yapısı tanımlanmış türlerinin adlarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="43926-133">The C# type system uses the names of the defined types, not the structure.</span></span>

<span data-ttu-id="43926-134">.NET Core kitaplığı'nda tanımları herhangi bir yeni özellik için yeni bir temsilci türü tanımlayan gerekmez anlamına Bu temsilci türü temsilciler gerektiren oluşturun.</span><span class="sxs-lookup"><span data-stu-id="43926-134">All these delegate type definitions in the .NET Core Library should mean that you do not need to define a new delegate type for any new feature you create that requires delegates.</span></span> <span data-ttu-id="43926-135">Bu genel tanımları tüm temsilci türleri çoğu durumlarda ihtiyacınız sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="43926-135">These generic definitions should provide all the delegate types you need under most situations.</span></span> <span data-ttu-id="43926-136">Yalnızca gerekli tür parametreleri ile şu türlerden birinde örneği oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="43926-136">You can simply instantiate one of these types with the required type parameters.</span></span> <span data-ttu-id="43926-137">Genel hale getirilebilir algoritmaları söz konusu olduğunda, bu temsilcileri genel türleri olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="43926-137">In the case of algorithms that can be made generic, these delegates can be used as generic types.</span></span> 

<span data-ttu-id="43926-138">Bu zamandan tasarruf edin ve temsilciler ile çalışmak için oluşturmanız gereken yeni türleri sayısını en aza indirin.</span><span class="sxs-lookup"><span data-stu-id="43926-138">This should save time, and minimize the number of new types that you need to create in order to work with delegates.</span></span>

<span data-ttu-id="43926-139">Sonraki makalede, temsilciler uygulamada çalışmaya yönelik birçok ortak deseni görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="43926-139">In the next article, you'll see several common patterns for working with delegates in practice.</span></span>

[<span data-ttu-id="43926-140">Next</span><span class="sxs-lookup"><span data-stu-id="43926-140">Next</span></span>](delegates-patterns.md)
