---
title: SyncLock ekstresi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.SyncLock
- SyncLock
helpviewer_keywords:
- threading [Visual Basic], locks
- SyncLock statement [Visual Basic]
- locks, threads
ms.assetid: 14501703-298f-4d43-b139-c4b6366af176
ms.openlocfilehash: e981ee727b66ecda392014fd3ee8ca6f1526cd2e
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72578893"
---
# <a name="synclock-statement"></a><span data-ttu-id="a7094-102">SyncLock Deyimi</span><span class="sxs-lookup"><span data-stu-id="a7094-102">SyncLock Statement</span></span>
<span data-ttu-id="a7094-103">Bloğu yürütmeden önce bir ifade bloğu için özel bir kilit elde edin.</span><span class="sxs-lookup"><span data-stu-id="a7094-103">Acquires an exclusive lock for a statement block before executing the block.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7094-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a7094-104">Syntax</span></span>  
  
```vb  
SyncLock lockobject  
    [ block ]  
End SyncLock  
```  
  
## <a name="parts"></a><span data-ttu-id="a7094-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="a7094-105">Parts</span></span>  
 `lockobject`  
 <span data-ttu-id="a7094-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="a7094-106">Required.</span></span> <span data-ttu-id="a7094-107">Bir nesne başvurusunu değerlendiren ifade.</span><span class="sxs-lookup"><span data-stu-id="a7094-107">Expression that evaluates to an object reference.</span></span>  
  
 `block`  
 <span data-ttu-id="a7094-108">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="a7094-108">Optional.</span></span> <span data-ttu-id="a7094-109">Kilit elde edildiğinde yürütülecek deyimler bloğu.</span><span class="sxs-lookup"><span data-stu-id="a7094-109">Block of statements that are to execute when the lock is acquired.</span></span>  
  
 `End SyncLock`  
 <span data-ttu-id="a7094-110">Bir `SyncLock` bloğunu sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="a7094-110">Terminates a `SyncLock` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a7094-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a7094-111">Remarks</span></span>  
 <span data-ttu-id="a7094-112">@No__t_0 deyimleri, birden çok iş parçacığının aynı anda ekstre bloğunu yürütmemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="a7094-112">The `SyncLock` statement ensures that multiple threads do not execute the statement block at the same time.</span></span> <span data-ttu-id="a7094-113">`SyncLock`, başka bir iş parçacığı yürütülene kadar her bir iş parçacığının blok girmesini önler.</span><span class="sxs-lookup"><span data-stu-id="a7094-113">`SyncLock` prevents each thread from entering the block until no other thread is executing it.</span></span>  
  
 <span data-ttu-id="a7094-114">@No__t_0 en yaygın kullanımı, verilerin birden fazla iş parçacığı tarafından aynı anda güncelleştirilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="a7094-114">The most common use of `SyncLock` is to protect data from being updated by more than one thread simultaneously.</span></span> <span data-ttu-id="a7094-115">Verileri işleyen deyimlerin kesintiye uğramadan tamamlanması gerekiyorsa, bunları bir `SyncLock` bloğunun içine koyun.</span><span class="sxs-lookup"><span data-stu-id="a7094-115">If the statements that manipulate the data must go to completion without interruption, put them inside a `SyncLock` block.</span></span>  
  
 <span data-ttu-id="a7094-116">Özel bir kilit tarafından korunan bir ifade bloğu bazen *kritik bir bölüm*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="a7094-116">A statement block protected by an exclusive lock is sometimes called a *critical section*.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="a7094-117">Kurallar</span><span class="sxs-lookup"><span data-stu-id="a7094-117">Rules</span></span>  
  
- <span data-ttu-id="a7094-118">Dallanma.</span><span class="sxs-lookup"><span data-stu-id="a7094-118">Branching.</span></span> <span data-ttu-id="a7094-119">Bloğunun dışından bir `SyncLock` bloğuna dallandırılamıyor.</span><span class="sxs-lookup"><span data-stu-id="a7094-119">You cannot branch into a `SyncLock` block from outside the block.</span></span>  
  
- <span data-ttu-id="a7094-120">Nesne değerini kilitle.</span><span class="sxs-lookup"><span data-stu-id="a7094-120">Lock Object Value.</span></span> <span data-ttu-id="a7094-121">@No__t_0 değeri `Nothing` olamaz.</span><span class="sxs-lookup"><span data-stu-id="a7094-121">The value of `lockobject` cannot be `Nothing`.</span></span> <span data-ttu-id="a7094-122">Kilit nesnesini bir `SyncLock` ifadesinde kullanmadan önce oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a7094-122">You must create the lock object before you use it in a `SyncLock` statement.</span></span>  
  
     <span data-ttu-id="a7094-123">@No__t_1 bloğunu yürütürken `lockobject` değerini değiştiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="a7094-123">You cannot change the value of `lockobject` while executing a `SyncLock` block.</span></span> <span data-ttu-id="a7094-124">Mekanizma, kilit nesnesinin değişmeden kalmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="a7094-124">The mechanism requires that the lock object remain unchanged.</span></span>  
  
- <span data-ttu-id="a7094-125">@No__t_1 bloğunda [await](../../../visual-basic/language-reference/operators/await-operator.md) işlecini kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="a7094-125">You can't use the [Await](../../../visual-basic/language-reference/operators/await-operator.md) operator in a `SyncLock` block.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="a7094-126">Davranış</span><span class="sxs-lookup"><span data-stu-id="a7094-126">Behavior</span></span>  
  
- <span data-ttu-id="a7094-127">Mekanizmadır.</span><span class="sxs-lookup"><span data-stu-id="a7094-127">Mechanism.</span></span> <span data-ttu-id="a7094-128">Bir iş parçacığı `SyncLock` deyimine ulaştığında, `lockobject` ifadesini değerlendirir ve ifadenin döndürdüğü nesne üzerinde dışlamalı bir kilit elde edene kadar yürütmeyi askıya alır.</span><span class="sxs-lookup"><span data-stu-id="a7094-128">When a thread reaches the `SyncLock` statement, it evaluates the `lockobject` expression and suspends execution until it acquires an exclusive lock on the object returned by the expression.</span></span> <span data-ttu-id="a7094-129">Başka bir iş parçacığı `SyncLock` ifadesine ulaştığında, ilk iş parçacığı `End SyncLock` ifadesini çalıştırana kadar bir kilit almaz.</span><span class="sxs-lookup"><span data-stu-id="a7094-129">When another thread reaches the `SyncLock` statement, it does not acquire a lock until the first thread executes the `End SyncLock` statement.</span></span>  
  
- <span data-ttu-id="a7094-130">Korumalı veriler.</span><span class="sxs-lookup"><span data-stu-id="a7094-130">Protected Data.</span></span> <span data-ttu-id="a7094-131">@No__t_0 bir `Shared` değişkense, dışlamalı kilit, herhangi bir iş parçacığı yürütülürken sınıfın herhangi bir örneğindeki bir iş parçacığının `SyncLock` bloğunu yürütmesini engeller.</span><span class="sxs-lookup"><span data-stu-id="a7094-131">If `lockobject` is a `Shared` variable, the exclusive lock prevents a thread in any instance of the class from executing the `SyncLock` block while any other thread is executing it.</span></span> <span data-ttu-id="a7094-132">Bu, tüm örnekler arasında paylaşılan verileri korur.</span><span class="sxs-lookup"><span data-stu-id="a7094-132">This protects data that is shared among all the instances.</span></span>  
  
     <span data-ttu-id="a7094-133">@No__t_0 bir örnek değişkenidir (`Shared` değil), kilit, geçerli örnekte çalışan bir iş parçacığının aynı anda aynı örnekteki diğer bir iş parçacığıyla `SyncLock` bloğunu yürütmesini engeller.</span><span class="sxs-lookup"><span data-stu-id="a7094-133">If `lockobject` is an instance variable (not `Shared`), the lock prevents a thread running in the current instance from executing the `SyncLock` block at the same time as another thread in the same instance.</span></span> <span data-ttu-id="a7094-134">Bu, bireysel örnek tarafından tutulan verileri korur.</span><span class="sxs-lookup"><span data-stu-id="a7094-134">This protects data maintained by the individual instance.</span></span>  
  
- <span data-ttu-id="a7094-135">Alma ve yayınlama.</span><span class="sxs-lookup"><span data-stu-id="a7094-135">Acquisition and Release.</span></span> <span data-ttu-id="a7094-136">@No__t_0 bloğu, `Try` bloğunun `lockobject` üzerinde dışlamalı bir kilit elde `Try...Finally` oluşturma gibi davranır ve `Finally` bloğu bunu serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="a7094-136">A `SyncLock` block behaves like a `Try...Finally` construction in which the `Try` block acquires an exclusive lock on `lockobject` and the `Finally` block releases it.</span></span> <span data-ttu-id="a7094-137">Bu nedenle, bloğundan nasıl çıktığınızda bağımsız olarak `SyncLock` bloğu kilit sürümünü garanti eder.</span><span class="sxs-lookup"><span data-stu-id="a7094-137">Because of this, the `SyncLock` block guarantees release of the lock, no matter how you exit the block.</span></span> <span data-ttu-id="a7094-138">Bu, işlenmemiş bir özel durum durumunda bile geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="a7094-138">This is true even in the case of an unhandled exception.</span></span>  
  
- <span data-ttu-id="a7094-139">Çerçeve çağrıları.</span><span class="sxs-lookup"><span data-stu-id="a7094-139">Framework Calls.</span></span> <span data-ttu-id="a7094-140">@No__t_0 bloğu, <xref:System.Threading> ad alanındaki `Monitor` sınıfının `Enter` ve `Exit` yöntemlerini çağırarak dışlamalı kilidi alır ve yayınlar.</span><span class="sxs-lookup"><span data-stu-id="a7094-140">The `SyncLock` block acquires and releases the exclusive lock by calling the `Enter` and `Exit` methods of the `Monitor` class in the <xref:System.Threading> namespace.</span></span>  
  
## <a name="programming-practices"></a><span data-ttu-id="a7094-141">Programlama uygulamaları</span><span class="sxs-lookup"><span data-stu-id="a7094-141">Programming Practices</span></span>  
 <span data-ttu-id="a7094-142">@No__t_0 ifadesi her zaman yalnızca sınıfınıza ait olan bir nesne olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="a7094-142">The `lockobject` expression should always evaluate to an object that belongs exclusively to your class.</span></span> <span data-ttu-id="a7094-143">Geçerli örneğe ait verileri korumak için bir `Private` nesne değişkeni veya tüm örneklerde ortak olan verileri korumak için bir `Private Shared` nesne değişkeni bildirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a7094-143">You should declare a `Private` object variable to protect data belonging to the current instance, or a `Private Shared` object variable to protect data common to all instances.</span></span>  
  
 <span data-ttu-id="a7094-144">Örnek verileri için bir kilit nesnesi sağlamak üzere `Me` anahtar sözcüğünü kullanmamalısınız.</span><span class="sxs-lookup"><span data-stu-id="a7094-144">You should not use the `Me` keyword to provide a lock object for instance data.</span></span> <span data-ttu-id="a7094-145">Sınıfınıza dış kod, sınıfınızın bir örneğine başvuru içeriyorsa, bu başvuruyu sizinki farklı verileri koruyan bir `SyncLock` bloğu için bir kilit nesnesi olarak kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="a7094-145">If code external to your class has a reference to an instance of your class, it could use that reference as a lock object for a `SyncLock` block completely different from yours, protecting different data.</span></span> <span data-ttu-id="a7094-146">Bu şekilde, sınıfınız ve diğer sınıfı birbirini ilgisiz `SyncLock` bloklarını yürütmelerini engelleyebilir.</span><span class="sxs-lookup"><span data-stu-id="a7094-146">In this way, your class and the other class could block each other from executing their unrelated `SyncLock` blocks.</span></span> <span data-ttu-id="a7094-147">Aynı dizeyi kullanan işlemdeki diğer kodlar aynı kilidi paylaştığından, bir dizedeki aynı şekilde kilitleme sorunlu olabilir.</span><span class="sxs-lookup"><span data-stu-id="a7094-147">Similarly locking on a string can be problematic since any other code in the process using the same string will share the same lock.</span></span>  
  
 <span data-ttu-id="a7094-148">Ayrıca, paylaşılan veriler için bir kilit nesnesi sağlamak üzere `Me.GetType` metodunu kullanmamalısınız.</span><span class="sxs-lookup"><span data-stu-id="a7094-148">You should also not use the `Me.GetType` method to provide a lock object for shared data.</span></span> <span data-ttu-id="a7094-149">Bunun nedeni, `GetType` her zaman belirli bir sınıf adı için aynı `Type` nesnesini döndürmektedir.</span><span class="sxs-lookup"><span data-stu-id="a7094-149">This is because `GetType` always returns the same `Type` object for a given class name.</span></span> <span data-ttu-id="a7094-150">Dış kod, sınıfınıza `GetType` çağırabilir ve kullanmakta olduğunuz kilit nesnesini alabilir.</span><span class="sxs-lookup"><span data-stu-id="a7094-150">External code could call `GetType` on your class and obtain the same lock object you are using.</span></span> <span data-ttu-id="a7094-151">Bu, iki sınıfın `SyncLock` bloklarında birbirini engellemesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="a7094-151">This would result in the two classes blocking each other from their `SyncLock` blocks.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="a7094-152">Örnekler</span><span class="sxs-lookup"><span data-stu-id="a7094-152">Examples</span></span>  
  
### <a name="description"></a><span data-ttu-id="a7094-153">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a7094-153">Description</span></span>  
 <span data-ttu-id="a7094-154">Aşağıdaki örnek, bir ileti listesini tutan bir sınıfı gösterir.</span><span class="sxs-lookup"><span data-stu-id="a7094-154">The following example shows a class that maintains a simple list of messages.</span></span> <span data-ttu-id="a7094-155">Bir dizideki iletileri ve bu dizinin son kullanılan öğesini bir değişkende tutar.</span><span class="sxs-lookup"><span data-stu-id="a7094-155">It holds the messages in an array and the last used element of that array in a variable.</span></span> <span data-ttu-id="a7094-156">@No__t_0 yordamı son öğeyi artırır ve yeni iletiyi depolar.</span><span class="sxs-lookup"><span data-stu-id="a7094-156">The `addAnotherMessage` procedure increments the last element and stores the new message.</span></span> <span data-ttu-id="a7094-157">Bu iki işlem `SyncLock` ve `End SyncLock` deyimleri tarafından korunur, çünkü son öğe artdıktan sonra yeni ileti, diğer herhangi bir iş parçacığının son öğeyi yeniden artırılabilmesi için önce depolanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a7094-157">Those two operations are protected by the `SyncLock` and `End SyncLock` statements, because once the last element has been incremented, the new message must be stored before any other thread can increment the last element again.</span></span>  
  
 <span data-ttu-id="a7094-158">@No__t_0 sınıfı tüm örnekleri arasında bir ileti listesi paylaşmışsa, `messagesList` ve `messagesLast` değişkenleri `Shared` olarak bildirilebilecek.</span><span class="sxs-lookup"><span data-stu-id="a7094-158">If the `simpleMessageList` class shared one list of messages among all its instances, the variables `messagesList` and `messagesLast` would be declared as `Shared`.</span></span> <span data-ttu-id="a7094-159">Bu durumda, değişken `messagesLock`, her örnek tarafından kullanılan tek bir kilit nesnesi olacak şekilde `Shared` de olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a7094-159">In this case, the variable `messagesLock` should also be `Shared`, so that there would be a single lock object used by every instance.</span></span>  
  
### <a name="code"></a><span data-ttu-id="a7094-160">Kod</span><span class="sxs-lookup"><span data-stu-id="a7094-160">Code</span></span>  
 [!code-vb[VbVbalrThreading#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrThreading/VB/Class1.vb#1)]  
  
### <a name="description"></a><span data-ttu-id="a7094-161">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a7094-161">Description</span></span>  
 <span data-ttu-id="a7094-162">Aşağıdaki örnek, iş parçacıklarını ve `SyncLock` kullanır.</span><span class="sxs-lookup"><span data-stu-id="a7094-162">The following example uses threads and `SyncLock`.</span></span> <span data-ttu-id="a7094-163">@No__t_0 deyimin bulunduğu sürece, ifade bloğu kritik bir bölümdür ve `balance` hiçbir zaman negatif bir sayı haline geçmez.</span><span class="sxs-lookup"><span data-stu-id="a7094-163">As long as the `SyncLock` statement is present, the statement block is a critical section and `balance` never becomes a negative number.</span></span> <span data-ttu-id="a7094-164">@No__t_2 anahtar sözcüğünü bırakma etkisini görmek için `SyncLock` ve `End SyncLock` deyimlerini açıklama ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a7094-164">You can comment out the `SyncLock` and `End SyncLock` statements to see the effect of leaving out the `SyncLock` keyword.</span></span>  
  
### <a name="code"></a><span data-ttu-id="a7094-165">Kod</span><span class="sxs-lookup"><span data-stu-id="a7094-165">Code</span></span>  
 [!code-vb[VbVbalrThreading#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrThreading/VB/class2.vb#21)]  
  
### <a name="comments"></a><span data-ttu-id="a7094-166">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a7094-166">Comments</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7094-167">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a7094-167">See also</span></span>

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.Interlocked?displayProperty=nameWithType>
- [<span data-ttu-id="a7094-168">Eşitleme temelleri 'ne genel bakış</span><span class="sxs-lookup"><span data-stu-id="a7094-168">Overview of synchronization primitives</span></span>](../../../standard/threading/overview-of-synchronization-primitives.md)
