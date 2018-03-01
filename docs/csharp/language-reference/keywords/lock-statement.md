---
title: "lock Deyimi (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- lock_CSharpKeyword
- lock
helpviewer_keywords:
- lock keyword [C#]
ms.assetid: 656da1a4-707e-4ef6-9c6e-6d13b646af42
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: eb48c2b1554ad2817406eaef42b4cb336ea46862
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="lock-statement-c-reference"></a><span data-ttu-id="fa726-102">lock Deyimi (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="fa726-102">lock Statement (C# Reference)</span></span>
<span data-ttu-id="fa726-103">`lock` Anahtar sözcüğü belirli nesne karşılıklı dışlama kilidi alma, bir deyimi yürütme ve kilidin açılması bu deyimi blok önemli bir bölümü işaretler.</span><span class="sxs-lookup"><span data-stu-id="fa726-103">The `lock` keyword marks a statement block as a critical section by obtaining the mutual-exclusion lock for a given object, executing a statement, and then releasing the lock.</span></span> <span data-ttu-id="fa726-104">Aşağıdaki örnek içeren bir `lock` deyimi.</span><span class="sxs-lookup"><span data-stu-id="fa726-104">The following example includes a `lock` statement.</span></span>  
  
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
  
 <span data-ttu-id="fa726-105">Daha fazla bilgi için bkz: [iş parçacığı eşitleme](../../programming-guide/concepts/threading/thread-synchronization.md).</span><span class="sxs-lookup"><span data-stu-id="fa726-105">For more information, see [Thread Synchronization](../../programming-guide/concepts/threading/thread-synchronization.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fa726-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fa726-106">Remarks</span></span>  
 <span data-ttu-id="fa726-107">`lock` Anahtar sözcüğü sağlar başka bir iş parçacığı kritik bölümünde olsa da bir iş parçacığı önemli bir bölümü kodunun geçmiyor.</span><span class="sxs-lookup"><span data-stu-id="fa726-107">The `lock` keyword ensures that one thread does not enter a critical section of code while another thread is in the critical section.</span></span> <span data-ttu-id="fa726-108">Başka bir iş parçacığı kilitli kodu girmek çalışırsa, bekler, nesne serbest kadar engelleyin.</span><span class="sxs-lookup"><span data-stu-id="fa726-108">If another thread tries to enter a locked code, it will wait, block, until the object is released.</span></span>  
  
 <span data-ttu-id="fa726-109">Bölüm [parçacıkları](../../programming-guide/concepts/threading/index.md) iş parçacığı oluşturma açıklanır.</span><span class="sxs-lookup"><span data-stu-id="fa726-109">The section [Threading](../../programming-guide/concepts/threading/index.md) discusses threading.</span></span>  
  
 <span data-ttu-id="fa726-110">`lock` Anahtar sözcüğü çağrıları <xref:System.Threading.Monitor.Enter%2A> bloğun başlangıcında ve <xref:System.Threading.Monitor.Exit%2A> bloğun sonunda.</span><span class="sxs-lookup"><span data-stu-id="fa726-110">The `lock` keyword calls <xref:System.Threading.Monitor.Enter%2A> at the start of the block and <xref:System.Threading.Monitor.Exit%2A> at the end of the block.</span></span> <span data-ttu-id="fa726-111">A <xref:System.Threading.ThreadInterruptedException> erişilirse durum <xref:System.Threading.Thread.Interrupt%2A> girmek için bekleyen bir iş parçacığı keser bir `lock` deyimi.</span><span class="sxs-lookup"><span data-stu-id="fa726-111">A <xref:System.Threading.ThreadInterruptedException> is thrown if <xref:System.Threading.Thread.Interrupt%2A> interrupts a thread that is waiting to enter a `lock` statement.</span></span>  
  
 <span data-ttu-id="fa726-112">Genel olarak, üzerinde kilitleme kaçının bir `public` türü ya da kodunuzu ait denetim ötesinde örnekleri.</span><span class="sxs-lookup"><span data-stu-id="fa726-112">In general, avoid locking on a `public` type, or instances beyond your code's control.</span></span> <span data-ttu-id="fa726-113">Ortak yapıları `lock (this)`, `lock (typeof (MyType))`, ve `lock ("myLock")` bu kılavuz ihlal:</span><span class="sxs-lookup"><span data-stu-id="fa726-113">The common constructs `lock (this)`, `lock (typeof (MyType))`, and `lock ("myLock")` violate this guideline:</span></span>  
  
-   <span data-ttu-id="fa726-114">`lock (this)`örnek genel olarak erişilebiliyorsa bir sorundur.</span><span class="sxs-lookup"><span data-stu-id="fa726-114">`lock (this)` is a problem if the instance can be accessed publicly.</span></span>  
  
-   <span data-ttu-id="fa726-115">`lock (typeof (MyType))`bir sorun ise `MyType` genel olarak erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="fa726-115">`lock (typeof (MyType))` is a problem if `MyType` is publicly accessible.</span></span>  
  
-   <span data-ttu-id="fa726-116">`lock("myLock")`aynı dize kullanarak işlemdeki başka bir kod paylaşır çünkü aynı kilit bir sorundur.</span><span class="sxs-lookup"><span data-stu-id="fa726-116">`lock("myLock")` is a problem because any other code in the process using the same string, will share the same lock.</span></span>  
  
 <span data-ttu-id="fa726-117">En iyi uygulamadır tanımlamak için bir `private` , kilitlemek için nesne veya `private static` için tüm örnekleri ortak verileri korumak için nesne değişkeni.</span><span class="sxs-lookup"><span data-stu-id="fa726-117">Best practice is to define a `private` object to lock on, or a `private static` object variable to protect data common to all instances.</span></span>  
  
 <span data-ttu-id="fa726-118">Kullanamazsınız [await](../../../csharp/language-reference/keywords/await.md) gövdesinde anahtar sözcüğü bir `lock` deyimi.</span><span class="sxs-lookup"><span data-stu-id="fa726-118">You can't use the [await](../../../csharp/language-reference/keywords/await.md) keyword in the body of a `lock` statement.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fa726-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="fa726-119">Example</span></span>  
 <span data-ttu-id="fa726-120">Aşağıdaki örnek, C# ' ta kilitlemeden basit bir iş parçacığı kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="fa726-120">The following sample shows a simple use of threads without locking in C#.</span></span>  
  
 [!code-csharp[csrefKeywordsFixedLock#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/lock-statement_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="fa726-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="fa726-121">Example</span></span>  
 <span data-ttu-id="fa726-122">Aşağıdaki örnek iş parçacığı kullanır ve `lock`.</span><span class="sxs-lookup"><span data-stu-id="fa726-122">The following sample uses threads and `lock`.</span></span> <span data-ttu-id="fa726-123">Sürece `lock` deyimi varsa, deyimi blok kritik bir bölümdür ve `balance` negatif bir sayı hiçbir zaman olur.</span><span class="sxs-lookup"><span data-stu-id="fa726-123">As long as the `lock` statement is present, the statement block is a critical section and `balance` will never become a negative number.</span></span>  
  
 [!code-csharp[csrefKeywordsFixedLock#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/lock-statement_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="fa726-124">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="fa726-124">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="fa726-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fa726-125">See Also</span></span>  
 <xref:System.Reflection.MethodImplAttributes>  
 <xref:System.Threading.Mutex>  
 [<span data-ttu-id="fa726-126">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="fa726-126">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="fa726-127">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="fa726-127">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="fa726-128">İş parçacığı oluşturma</span><span class="sxs-lookup"><span data-stu-id="fa726-128">Threading</span></span>](../../programming-guide/concepts/threading/index.md)  
 [<span data-ttu-id="fa726-129">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="fa726-129">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="fa726-130">Deyim anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="fa726-130">Statement Keywords</span></span>](../../../csharp/language-reference/keywords/statement-keywords.md)  
 <xref:System.Threading.Monitor>  
 [<span data-ttu-id="fa726-131">Birbirine kenetlenmiş işlemler</span><span class="sxs-lookup"><span data-stu-id="fa726-131">Interlocked Operations</span></span>](../../../standard/threading/interlocked-operations.md)  
 [<span data-ttu-id="fa726-132">AutoResetEvent</span><span class="sxs-lookup"><span data-stu-id="fa726-132">AutoResetEvent</span></span>](../../../standard/threading/autoresetevent.md)  
 [<span data-ttu-id="fa726-133">İş parçacığı eşitleme</span><span class="sxs-lookup"><span data-stu-id="fa726-133">Thread Synchronization</span></span>](../../programming-guide/concepts/threading/thread-synchronization.md)
