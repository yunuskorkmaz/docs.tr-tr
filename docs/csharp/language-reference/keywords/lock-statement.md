---
title: kilit deyimi - C# başvurusu
description: İş parçacığı erişimini paylaşılan bir kaynağa eşitlemek için C# kilit deyimini kullanma
ms.date: 04/02/2020
f1_keywords:
- lock_CSharpKeyword
- lock
helpviewer_keywords:
- lock keyword [C#]
ms.assetid: 656da1a4-707e-4ef6-9c6e-6d13b646af42
ms.openlocfilehash: 2f2d42ae02a07a5e1b82cefd004f4d03b2a16dff
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635388"
---
# <a name="lock-statement-c-reference"></a><span data-ttu-id="25544-103">kilit deyimi (C# başvurusu)</span><span class="sxs-lookup"><span data-stu-id="25544-103">lock statement (C# reference)</span></span>

<span data-ttu-id="25544-104">Deyim, `lock` belirli bir nesne için karşılıklı dışlama kilidi kazanır, bir deyim bloğunu yürütür ve kilidi serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="25544-104">The `lock` statement acquires the mutual-exclusion lock for a given object, executes a statement block, and then releases the lock.</span></span> <span data-ttu-id="25544-105">Kilit tutulurken, kilidi tutan iş parçacığı kilidi yeniden alabilir ve serbest bırakabilir.</span><span class="sxs-lookup"><span data-stu-id="25544-105">While a lock is held, the thread that holds the lock can again acquire and release the lock.</span></span> <span data-ttu-id="25544-106">Başka bir iş parçacığı kilidi edinme engellenir ve kilit serbest bırakılınyana kadar bekler.</span><span class="sxs-lookup"><span data-stu-id="25544-106">Any other thread is blocked from acquiring the lock and waits until the lock is released.</span></span>

<span data-ttu-id="25544-107">İfade `lock` formu</span><span class="sxs-lookup"><span data-stu-id="25544-107">The `lock` statement is of the form</span></span>

```csharp
lock (x)
{
    // Your code...
}
```

<span data-ttu-id="25544-108">nerede `x` bir başvuru [türünün](reference-types.md)bir ifadesidir.</span><span class="sxs-lookup"><span data-stu-id="25544-108">where `x` is an expression of a [reference type](reference-types.md).</span></span> <span data-ttu-id="25544-109">Tam olarak eşdeğer.</span><span class="sxs-lookup"><span data-stu-id="25544-109">It's precisely equivalent to</span></span>

```csharp
object __lockObj = x;
bool __lockWasTaken = false;
try
{
    System.Threading.Monitor.Enter(__lockObj, ref __lockWasTaken);
    // Your code...
}
finally
{
    if (__lockWasTaken) System.Threading.Monitor.Exit(__lockObj);
}
```

<span data-ttu-id="25544-110">Kod bir [deneyin kullandığından... son olarak](try-finally.md) blok, bir özel durum bir `lock` ifadenin gövdesi içinde atılmış olsa bile kilit serbest bırakılır.</span><span class="sxs-lookup"><span data-stu-id="25544-110">Since the code uses a [try...finally](try-finally.md) block, the lock is released even if an exception is thrown within the body of a `lock` statement.</span></span>

<span data-ttu-id="25544-111">[Bir](../operators/await.md) `lock` deyimin gövdesinde bekleyen operatörü kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="25544-111">You can't use the [await operator](../operators/await.md) in the body of a `lock` statement.</span></span>

## <a name="guidelines"></a><span data-ttu-id="25544-112">Yönergeler</span><span class="sxs-lookup"><span data-stu-id="25544-112">Guidelines</span></span>

<span data-ttu-id="25544-113">İş parçacığı erişimini paylaşılan bir kaynağa eşitlediğinizde, özel bir `private readonly object balanceLock = new object();`nesne örneğini (örneğin,) veya kodun ilgisiz bölümleri tarafından kilit nesnesi olarak kullanılma olasılığı düşük başka bir örneği kilitleyin.</span><span class="sxs-lookup"><span data-stu-id="25544-113">When you synchronize thread access to a shared resource, lock on a dedicated object instance (for example, `private readonly object balanceLock = new object();`) or another instance that is unlikely to be used as a lock object by unrelated parts of the code.</span></span> <span data-ttu-id="25544-114">Kilitlenme veya kilit çekişmesi neden olabileceğinden, farklı paylaşılan kaynaklar için aynı kilit nesnesi örneğini kullanmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="25544-114">Avoid using the same lock object instance for different shared resources, as it might result in deadlock or lock contention.</span></span> <span data-ttu-id="25544-115">Özellikle, aşağıdakileri kilit nesneleri olarak kullanmaktan kaçının:</span><span class="sxs-lookup"><span data-stu-id="25544-115">In particular, avoid using the following as lock objects:</span></span>

- <span data-ttu-id="25544-116">`this`, arayanlar tarafından kilit olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="25544-116">`this`, as it might be used by the callers as a lock.</span></span>
- <span data-ttu-id="25544-117"><xref:System.Type>örnekler, bu işleç veya yansıma [türü](../operators/type-testing-and-cast.md#typeof-operator) tarafından elde edilebilir gibi.</span><span class="sxs-lookup"><span data-stu-id="25544-117"><xref:System.Type> instances, as those might be obtained by the [typeof](../operators/type-testing-and-cast.md#typeof-operator) operator or reflection.</span></span>
- <span data-ttu-id="25544-118">dize örnekleri, dize literals de dahil olmak üzere, bu [interned](/dotnet/api/system.string.intern#remarks)olabilir gibi .</span><span class="sxs-lookup"><span data-stu-id="25544-118">string instances, including string literals, as those might be [interned](/dotnet/api/system.string.intern#remarks).</span></span>

<span data-ttu-id="25544-119">Kilit çekişmesini azaltmak için kilidi mümkün olduğunca kısa bir süre tutun.</span><span class="sxs-lookup"><span data-stu-id="25544-119">Hold a lock for as short time as possible to reduce lock contention.</span></span>

## <a name="example"></a><span data-ttu-id="25544-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="25544-120">Example</span></span>

<span data-ttu-id="25544-121">Aşağıdaki örnek, özel `Account` `balanceLock` bir örneği kilitleyerek özel `balance` alanına erişimi eşitleyen bir sınıf tanımlar.</span><span class="sxs-lookup"><span data-stu-id="25544-121">The following example defines an `Account` class that synchronizes access to its private `balance` field by locking on a dedicated `balanceLock` instance.</span></span> <span data-ttu-id="25544-122">Kilitleme için aynı örneğin kullanılması, `balance` alanın aynı anda veya `Debit` `Credit` yöntemleri aynı anda çağırmaya çalışan iki iş parçacığı tarafından güncelleştirilememesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="25544-122">Using the same instance for locking ensures that the `balance` field cannot be updated simultaneously by two threads attempting to call the `Debit` or `Credit` methods simultaneously.</span></span>

[!code-csharp[lock-statement-example](~/samples/snippets/csharp/keywords/LockStatementExample.cs)]

## <a name="c-language-specification"></a><span data-ttu-id="25544-123">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="25544-123">C# language specification</span></span>

<span data-ttu-id="25544-124">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [kilit deyimi](~/_csharplang/spec/statements.md#the-lock-statement) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="25544-124">For more information, see [The lock statement](~/_csharplang/spec/statements.md#the-lock-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="25544-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="25544-125">See also</span></span>

- [<span data-ttu-id="25544-126">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="25544-126">C# reference</span></span>](../index.md)
- [<span data-ttu-id="25544-127">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="25544-127">C# keywords</span></span>](index.md)
- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.SpinLock?displayProperty=nameWithType>
- <xref:System.Threading.Interlocked?displayProperty=nameWithType>
- [<span data-ttu-id="25544-128">Eşitleme temellerine genel bakış</span><span class="sxs-lookup"><span data-stu-id="25544-128">Overview of synchronization primitives</span></span>](../../../standard/threading/overview-of-synchronization-primitives.md)
