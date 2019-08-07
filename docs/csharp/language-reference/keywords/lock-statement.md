---
title: Lock deyimleri- C# başvuru
ms.custom: seodec18
description: İş parçacığı C# erişimini paylaşılan bir kaynağa eşleştirmek için Lock ifadesini kullanın
ms.date: 10/01/2018
f1_keywords:
- lock_CSharpKeyword
- lock
helpviewer_keywords:
- lock keyword [C#]
ms.assetid: 656da1a4-707e-4ef6-9c6e-6d13b646af42
ms.openlocfilehash: 96609264044e531bcc8671cb226a02fdc1b962b8
ms.sourcegitcommit: bbfcc913c275885381820be28f61efcf8e83eecc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/05/2019
ms.locfileid: "68796459"
---
# <a name="lock-statement-c-reference"></a><span data-ttu-id="a49e8-103">Lock deyimleri (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="a49e8-103">lock statement (C# reference)</span></span>

<span data-ttu-id="a49e8-104">`lock` İfade, belirli bir nesne için karşılıklı dışlama kilidi alır, bir ekstre bloğunu yürütür ve sonra kilidi serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="a49e8-104">The `lock` statement acquires the mutual-exclusion lock for a given object, executes a statement block, and then releases the lock.</span></span> <span data-ttu-id="a49e8-105">Kilit tutulurken, kilidi tutan iş parçacığı kilidi yeniden alabilir ve serbest bırakabilir.</span><span class="sxs-lookup"><span data-stu-id="a49e8-105">While a lock is held, the thread that holds the lock can again acquire and release the lock.</span></span> <span data-ttu-id="a49e8-106">Diğer herhangi bir iş parçacığının kilidi almak engellenir ve kilit serbest bırakılana kadar bekler.</span><span class="sxs-lookup"><span data-stu-id="a49e8-106">Any other thread is blocked from acquiring the lock and waits until the lock is released.</span></span>

<span data-ttu-id="a49e8-107">`lock` İfade şu biçimdedir</span><span class="sxs-lookup"><span data-stu-id="a49e8-107">The `lock` statement is of the form</span></span>

```csharp
lock (x)
{
    // Your code...
}
```

<span data-ttu-id="a49e8-108">, başvuru türünün bir ifadesidir. [](reference-types.md) `x`</span><span class="sxs-lookup"><span data-stu-id="a49e8-108">where `x` is an expression of a [reference type](reference-types.md).</span></span> <span data-ttu-id="a49e8-109">Tam olarak eşdeğerdir</span><span class="sxs-lookup"><span data-stu-id="a49e8-109">It's precisely equivalent to</span></span>

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

<span data-ttu-id="a49e8-110">Kod bir TRY kullandığından... [ finally](try-finally.md) bloğu, bir `lock` deyimin gövdesinde özel durum oluşturulursa bile kilit serbest bırakılır.</span><span class="sxs-lookup"><span data-stu-id="a49e8-110">Since the code uses a [try...finally](try-finally.md) block, the lock is released even if an exception is thrown within the body of a `lock` statement.</span></span>

<span data-ttu-id="a49e8-111">Bir`lock` deyimin gövdesinde [await](await.md) anahtar sözcüğünü kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="a49e8-111">You can't use the [await](await.md) keyword in the body of a `lock` statement.</span></span>

## <a name="remarks"></a><span data-ttu-id="a49e8-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a49e8-112">Remarks</span></span>

<span data-ttu-id="a49e8-113">İş parçacığı erişimini paylaşılan bir kaynağa eşitlediğinizde, ayrılmış bir nesne örneği üzerinde (örneğin, `private readonly object balanceLock = new object();`) veya kodun ilişkisiz parçaları tarafından kilit nesnesi olarak kullanılması olası bir örnek üzerinde kilit.</span><span class="sxs-lookup"><span data-stu-id="a49e8-113">When you synchronize thread access to a shared resource, lock on a dedicated object instance (for example, `private readonly object balanceLock = new object();`) or another instance that is unlikely to be used as a lock object by unrelated parts of the code.</span></span> <span data-ttu-id="a49e8-114">Farklı paylaşılan kaynaklar için aynı kilit nesnesi örneğini kullanmaktan kaçının, çünkü kilitlenme veya kilitleme çekişmesine yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="a49e8-114">Avoid using the same lock object instance for different shared resources, as it might result in deadlock or lock contention.</span></span> <span data-ttu-id="a49e8-115">Özellikle, Lock nesneleri olarak aşağıdakileri kullanmaktan kaçının:</span><span class="sxs-lookup"><span data-stu-id="a49e8-115">In particular, avoid using the following as lock objects:</span></span>

- <span data-ttu-id="a49e8-116">`this`, çünkü çağıranlar bir kilit olarak kullanılıyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="a49e8-116">`this`, as it might be used by the callers as a lock.</span></span>
- <span data-ttu-id="a49e8-117"><xref:System.Type>örnekler, [typeof](../operators/type-testing-and-conversion-operators.md#typeof-operator) işleci veya Reflection tarafından elde edilebilir.</span><span class="sxs-lookup"><span data-stu-id="a49e8-117"><xref:System.Type> instances, as those might be obtained by the [typeof](../operators/type-testing-and-conversion-operators.md#typeof-operator) operator or reflection.</span></span>
- <span data-ttu-id="a49e8-118">dize sabit değerleri de dahil olmak üzere dize örnekleri [birbirine](/dotnet/api/system.string.intern#remarks)bağlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="a49e8-118">string instances, including string literals, as those might be [interned](/dotnet/api/system.string.intern#remarks).</span></span>

## <a name="example"></a><span data-ttu-id="a49e8-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="a49e8-119">Example</span></span>

<span data-ttu-id="a49e8-120">Aşağıdaki örnek, adanmış `Account` `balanceLock` bir örnek üzerinde kilitleyerek özel `balance` alanına erişimi eşitleyen bir sınıfı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a49e8-120">The following example defines an `Account` class that synchronizes access to its private `balance` field by locking on a dedicated `balanceLock` instance.</span></span> <span data-ttu-id="a49e8-121">Kilitleme için aynı örneği kullanmak, `balance` alanın aynı anda `Debit` veya `Credit` yöntemlerini çağırmaya çalışan iki iş parçacığı tarafından aynı anda güncelleştirilememesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="a49e8-121">Using the same instance for locking ensures that the `balance` field cannot be updated simultaneously by two threads attempting to call the `Debit` or `Credit` methods simultaneously.</span></span>

[!code-csharp[lock-statement-example](~/samples/snippets/csharp/keywords/LockStatementExample.cs)]

## <a name="c-language-specification"></a><span data-ttu-id="a49e8-122">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="a49e8-122">C# language specification</span></span>

<span data-ttu-id="a49e8-123">Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [kilit bildirimi](~/_csharplang/spec/statements.md#the-lock-statement) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="a49e8-123">For more information, see [The lock statement](~/_csharplang/spec/statements.md#the-lock-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a49e8-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a49e8-124">See also</span></span>

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.SpinLock?displayProperty=nameWithType>
- <xref:System.Threading.Interlocked?displayProperty=nameWithType>
- [<span data-ttu-id="a49e8-125">C#başvurunun</span><span class="sxs-lookup"><span data-stu-id="a49e8-125">C# reference</span></span>](../index.md)
- [<span data-ttu-id="a49e8-126">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="a49e8-126">C# keywords</span></span>](index.md)
- [<span data-ttu-id="a49e8-127">Eşitleme temelleri 'ne genel bakış</span><span class="sxs-lookup"><span data-stu-id="a49e8-127">Overview of synchronization primitives</span></span>](../../../standard/threading/overview-of-synchronization-primitives.md)
