---
title: lock deyimi - C# başvurusu
ms.custom: seodec18
description: İş parçacığı paylaşılan bir kaynağa erişimi eşitlemek için C# lock deyiminin kullanın
ms.date: 10/01/2018
f1_keywords:
- lock_CSharpKeyword
- lock
helpviewer_keywords:
- lock keyword [C#]
ms.assetid: 656da1a4-707e-4ef6-9c6e-6d13b646af42
ms.openlocfilehash: 6bf53cba73c4d7331b2a1c68bf7187c13281d844
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633446"
---
# <a name="lock-statement-c-reference"></a><span data-ttu-id="aa392-103">lock deyimi (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="aa392-103">lock statement (C# Reference)</span></span>

<span data-ttu-id="aa392-104">`lock` Deyimi belirli bir nesne için karşılıklı dışlama kilidini alır, bir deyim bloğunu yürütür ve ardından kilidi serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="aa392-104">The `lock` statement acquires the mutual-exclusion lock for a given object, executes a statement block, and then releases the lock.</span></span> <span data-ttu-id="aa392-105">Kilidi açık tutulduğu sürece kilidi tutan iş parçacığı yeniden almak ve kilidi serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="aa392-105">While a lock is held, the thread that holds the lock can again acquire and release the lock.</span></span> <span data-ttu-id="aa392-106">Başka bir iş parçacığı kilit alınırken gelen engellenir ve kilidi serbest bırakılıncaya kadar bekler.</span><span class="sxs-lookup"><span data-stu-id="aa392-106">Any other thread is blocked from acquiring the lock and waits until the lock is released.</span></span>

<span data-ttu-id="aa392-107">`lock` Deyimdir biçimi</span><span class="sxs-lookup"><span data-stu-id="aa392-107">The `lock` statement is of the form</span></span>

```csharp
lock (x)
{
    // Your code...
}
```

<span data-ttu-id="aa392-108">Burada `x` bir ifade olan bir [başvuru türüne](reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="aa392-108">where `x` is an expression of a [reference type](reference-types.md).</span></span> <span data-ttu-id="aa392-109">Tam olarak eşdeğerdir</span><span class="sxs-lookup"><span data-stu-id="aa392-109">It's precisely equivalent to</span></span>

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

<span data-ttu-id="aa392-110">Kod kullandığından bir [try... finally](try-finally.md) bloğu kilidi serbest gövdesi içinde bir özel durum olsa bile bir `lock` deyimi.</span><span class="sxs-lookup"><span data-stu-id="aa392-110">Since the code uses a [try...finally](try-finally.md) block, the lock is released even if an exception is thrown within the body of a `lock` statement.</span></span>

<span data-ttu-id="aa392-111">Kullanamazsınız [await](await.md) gövdesinde anahtar sözcüğü bir `lock` deyimi.</span><span class="sxs-lookup"><span data-stu-id="aa392-111">You can't use the [await](await.md) keyword in the body of a `lock` statement.</span></span>

## <a name="remarks"></a><span data-ttu-id="aa392-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="aa392-112">Remarks</span></span>

<span data-ttu-id="aa392-113">İş parçacığı paylaşılan bir kaynağa erişmeye eşitlediğinizde, adanmış Pro instanci objektu kilitleme (örneğin, `private readonly object balanceLock = new object();`) ya da bir kilit nesnesi olarak kodun ilgisiz parçaları tarafından kullanılmak üzere düşüktür, başka bir örneği.</span><span class="sxs-lookup"><span data-stu-id="aa392-113">When you synchronize thread access to a shared resource, lock on a dedicated object instance (for example, `private readonly object balanceLock = new object();`) or another instance that is unlikely to be used as a lock object by unrelated parts of the code.</span></span> <span data-ttu-id="aa392-114">Kilitlenme veya kilit Çekişme neden olabilir, farklı paylaşılan kaynaklar için aynı kilit nesne örneğini kullanarak kaçının.</span><span class="sxs-lookup"><span data-stu-id="aa392-114">Avoid using the same lock object instance for different shared resources, as it might result in deadlock or lock contention.</span></span> <span data-ttu-id="aa392-115">Özellikle, aşağıdaki nesneleri Kilitle kullanmaktan kaçının:</span><span class="sxs-lookup"><span data-stu-id="aa392-115">In particular, avoid using the following as lock objects:</span></span>

- <span data-ttu-id="aa392-116">`this`, gibi bir kilit çağıranlar tarafından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="aa392-116">`this`, as it might be used by the callers as a lock.</span></span>
- <span data-ttu-id="aa392-117"><xref:System.Type> örnekler olanlar tarafından alınabilir olarak [typeof](typeof.md) işleci veya yansıma.</span><span class="sxs-lookup"><span data-stu-id="aa392-117"><xref:System.Type> instances, as those might be obtained by the [typeof](typeof.md) operator or reflection.</span></span>
- <span data-ttu-id="aa392-118">dize değişmez değerleri, bu durumda olabileceğinden dahil olmak üzere örnekleri, dize [interned](/dotnet/api/system.string.intern#remarks).</span><span class="sxs-lookup"><span data-stu-id="aa392-118">string instances, including string literals, as those might be [interned](/dotnet/api/system.string.intern#remarks).</span></span>

## <a name="example"></a><span data-ttu-id="aa392-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="aa392-119">Example</span></span>

<span data-ttu-id="aa392-120">Aşağıdaki örnekte tanımlayan bir `Account` özel erişimi eşitler sınıfı `balance` üzerinde adanmış bir kilitleme alanı `balanceLock` örneği.</span><span class="sxs-lookup"><span data-stu-id="aa392-120">The following example defines an `Account` class that synchronizes access to its private `balance` field by locking on a dedicated `balanceLock` instance.</span></span> <span data-ttu-id="aa392-121">Kilitleme sağlar için aynı örneği kullanarak `balance` alanı güncelleştirilemiyor aynı anda arama girişimi iki iş parçacığı tarafından `Debit` veya `Credit` yöntemleri aynı anda.</span><span class="sxs-lookup"><span data-stu-id="aa392-121">Using the same instance for locking ensures that the `balance` field cannot be updated simultaneously by two threads attempting to call the `Debit` or `Credit` methods simultaneously.</span></span>

[!code-csharp[lock-statement-example](~/samples/snippets/csharp/keywords/LockStatementExample.cs)]

## <a name="c-language-specification"></a><span data-ttu-id="aa392-122">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="aa392-122">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="aa392-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aa392-123">See also</span></span>

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.SpinLock?displayProperty=nameWithType>
- <xref:System.Threading.Interlocked?displayProperty=nameWithType>
- [<span data-ttu-id="aa392-124">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="aa392-124">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="aa392-125">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="aa392-125">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="aa392-126">Deyim Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="aa392-126">Statement Keywords</span></span>](statement-keywords.md)
- [<span data-ttu-id="aa392-127">Eşitleme temellerine genel bakış</span><span class="sxs-lookup"><span data-stu-id="aa392-127">Overview of synchronization primitives</span></span>](../../../standard/threading/overview-of-synchronization-primitives.md)
