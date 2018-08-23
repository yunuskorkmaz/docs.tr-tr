---
title: lock deyimi (C# Başvurusu)
description: 'Lock anahtar sözcüğü iş parçacığı içinde kullanılır. '
ms.date: 07/20/2015
f1_keywords:
- lock_CSharpKeyword
- lock
helpviewer_keywords:
- lock keyword [C#]
ms.assetid: 656da1a4-707e-4ef6-9c6e-6d13b646af42
ms.openlocfilehash: 6ed46837482642dfd7e1a96cd120fc18023c5e9f
ms.sourcegitcommit: a1e35d4e94edab384a63406c0a5438306873031b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2018
ms.locfileid: "42753981"
---
# <a name="lock-statement-c-reference"></a><span data-ttu-id="d6dd1-103">lock deyimi (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="d6dd1-103">lock statement (C# Reference)</span></span>

<span data-ttu-id="d6dd1-104">`lock` Anahtar sözcük belirli bir nesne için karşılıklı dışlama kilidini alma, deyimi yürütüp ve sonra kilidi bırakarak bu bir deyim bloğunu kritik bir bölüm olarak işaretler.</span><span class="sxs-lookup"><span data-stu-id="d6dd1-104">The `lock` keyword marks a statement block as a critical section by obtaining the mutual-exclusion lock for a given object, executing a statement, and then releasing the lock.</span></span> <span data-ttu-id="d6dd1-105">Aşağıdaki örnek içeren bir `lock` deyimi.</span><span class="sxs-lookup"><span data-stu-id="d6dd1-105">The following example includes a `lock` statement.</span></span>

```csharp
class Account
{
    decimal balance;
    private Object thisLock = new Object();

    public void Withdraw(decimal amount)
    {
        lock (thisLock)
        {
            if (amount > balance)
            {
                throw new Exception("Insufficient funds");
            }
            balance -= amount;
        }
    }
}
```

<span data-ttu-id="d6dd1-106">Daha fazla bilgi için [iş parçacığı eşitleme](../../programming-guide/concepts/threading/thread-synchronization.md).</span><span class="sxs-lookup"><span data-stu-id="d6dd1-106">For more information, see [Thread Synchronization](../../programming-guide/concepts/threading/thread-synchronization.md).</span></span>

## <a name="remarks"></a><span data-ttu-id="d6dd1-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d6dd1-107">Remarks</span></span>

<span data-ttu-id="d6dd1-108">`lock` Anahtar sözcüğü, başka bir iş parçacığı kritik bölümünde olsa da bir iş parçacığı kodun önemli bir bölümünü geçmiyor sağlar.</span><span class="sxs-lookup"><span data-stu-id="d6dd1-108">The `lock` keyword ensures that one thread does not enter a critical section of code while another thread is in the critical section.</span></span> <span data-ttu-id="d6dd1-109">Kilitli bir kodu girmek başka bir iş parçacığı çalışırsa, bekler, nesne yayımlanana kadar engelleyin.</span><span class="sxs-lookup"><span data-stu-id="d6dd1-109">If another thread tries to enter a locked code, it will wait, block, until the object is released.</span></span>

<span data-ttu-id="d6dd1-110">Bölüm [parçacıkları](../../programming-guide/concepts/threading/index.md) iş parçacığı oluşturma açıklanır.</span><span class="sxs-lookup"><span data-stu-id="d6dd1-110">The section [Threading](../../programming-guide/concepts/threading/index.md) discusses threading.</span></span>

<span data-ttu-id="d6dd1-111">`lock` Anahtar sözcüğü çağrıları <xref:System.Threading.Monitor.Enter%2A> bloğun başlangıcında ve <xref:System.Threading.Monitor.Exit%2A> bloğunun sonunda.</span><span class="sxs-lookup"><span data-stu-id="d6dd1-111">The `lock` keyword calls <xref:System.Threading.Monitor.Enter%2A> at the start of the block and <xref:System.Threading.Monitor.Exit%2A> at the end of the block.</span></span> <span data-ttu-id="d6dd1-112">A <xref:System.Threading.ThreadInterruptedException> oluşturulur <xref:System.Threading.Thread.Interrupt%2A> girmek için bekleyen bir iş parçacığı kesmeleri bir `lock` deyimi.</span><span class="sxs-lookup"><span data-stu-id="d6dd1-112">A <xref:System.Threading.ThreadInterruptedException> is thrown if <xref:System.Threading.Thread.Interrupt%2A> interrupts a thread that is waiting to enter a `lock` statement.</span></span>

<span data-ttu-id="d6dd1-113">Genel olarak, üzerinde kilitleme kaçının bir `public` türü veya kodunuzun kontrolü örnekleri.</span><span class="sxs-lookup"><span data-stu-id="d6dd1-113">In general, avoid locking on a `public` type, or instances beyond your code's control.</span></span> <span data-ttu-id="d6dd1-114">Ortak Yapılar `lock (this)`, `lock (typeof (MyType))`, ve `lock ("myLock")` bu anlayışın ihlal:</span><span class="sxs-lookup"><span data-stu-id="d6dd1-114">The common constructs `lock (this)`, `lock (typeof (MyType))`, and `lock ("myLock")` violate this guideline:</span></span>

- <span data-ttu-id="d6dd1-115">`lock (this)` Örneğin genel olarak erişilebilen bir sorun ise.</span><span class="sxs-lookup"><span data-stu-id="d6dd1-115">`lock (this)` is a problem if the instance can be accessed publicly.</span></span>

- <span data-ttu-id="d6dd1-116">`lock (typeof (MyType))` bir sorun ise `MyType` genel olarak erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="d6dd1-116">`lock (typeof (MyType))` is a problem if `MyType` is publicly accessible.</span></span>

- <span data-ttu-id="d6dd1-117">`lock("myLock")` aynı dize kullanarak işlemindeki herhangi bir kod paylaştığından aynı kilit bir sorundur.</span><span class="sxs-lookup"><span data-stu-id="d6dd1-117">`lock("myLock")` is a problem because any other code in the process using the same string, will share the same lock.</span></span>

<span data-ttu-id="d6dd1-118">En iyi uygulamadır tanımlamak için bir `private` , kilitlemek için nesne veya `private static` için tüm örnekleri ortak verileri korumak için nesne değişkeni.</span><span class="sxs-lookup"><span data-stu-id="d6dd1-118">Best practice is to define a `private` object to lock on, or a `private static` object variable to protect data common to all instances.</span></span>

<span data-ttu-id="d6dd1-119">Kullanamazsınız [await](await.md) gövdesinde anahtar sözcüğü bir `lock` deyimi.</span><span class="sxs-lookup"><span data-stu-id="d6dd1-119">You can't use the [await](await.md) keyword in the body of a `lock` statement.</span></span>

## <a name="example---threads-without-locking"></a><span data-ttu-id="d6dd1-120">Örnek - kilitlemeden iş parçacıkları</span><span class="sxs-lookup"><span data-stu-id="d6dd1-120">Example - Threads without locking</span></span>

<span data-ttu-id="d6dd1-121">Aşağıdaki örnek, C# dilinde kilitlemeden basit bir iş parçacığı kullanımı gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="d6dd1-121">The following sample shows a simple use of threads without locking in C#:</span></span>

[!code-csharp[csrefKeywordsFixedLock#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsFixedLock/CS/csrefKeywordsFixedLock.cs#5)]

## <a name="example---threads-using-locking"></a><span data-ttu-id="d6dd1-122">Örnek - iş parçacıklarını kilitleme kullanma</span><span class="sxs-lookup"><span data-stu-id="d6dd1-122">Example - Threads using locking</span></span>

<span data-ttu-id="d6dd1-123">Aşağıdaki örnek iş parçacığı kullanır ve `lock`.</span><span class="sxs-lookup"><span data-stu-id="d6dd1-123">The following sample uses threads and `lock`.</span></span> <span data-ttu-id="d6dd1-124">Sürece `lock` deyimi, deyim bloğunu kritik bir bölümdür ve `balance` hiçbir zaman negatif bir sayı olur:</span><span class="sxs-lookup"><span data-stu-id="d6dd1-124">As long as the `lock` statement is present, the statement block is a critical section and `balance` will never become a negative number:</span></span>

[!code-csharp[csrefKeywordsFixedLock#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsFixedLock/CS/csrefKeywordsFixedLock.cs#6)]

## <a name="c-language-specification"></a><span data-ttu-id="d6dd1-125">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="d6dd1-125">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="d6dd1-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d6dd1-126">See also</span></span>

- <xref:System.Reflection.MethodImplAttributes>
- <xref:System.Threading.Mutex>
- <xref:System.Threading.Monitor>
- [<span data-ttu-id="d6dd1-127">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="d6dd1-127">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="d6dd1-128">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="d6dd1-128">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="d6dd1-129">İş parçacığı oluşturma</span><span class="sxs-lookup"><span data-stu-id="d6dd1-129">Threading</span></span>](../../programming-guide/concepts/threading/index.md)
- [<span data-ttu-id="d6dd1-130">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="d6dd1-130">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="d6dd1-131">Deyim Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="d6dd1-131">Statement Keywords</span></span>](statement-keywords.md)
- [<span data-ttu-id="d6dd1-132">Birbirine Kenetlenmiş İşlemler</span><span class="sxs-lookup"><span data-stu-id="d6dd1-132">Interlocked Operations</span></span>](../../../standard/threading/interlocked-operations.md)
- [<span data-ttu-id="d6dd1-133">AutoResetEvent</span><span class="sxs-lookup"><span data-stu-id="d6dd1-133">AutoResetEvent</span></span>](../../../standard/threading/autoresetevent.md)
- [<span data-ttu-id="d6dd1-134">İş Parçacığı Eşitleme</span><span class="sxs-lookup"><span data-stu-id="d6dd1-134">Thread Synchronization</span></span>](../../programming-guide/concepts/threading/thread-synchronization.md)