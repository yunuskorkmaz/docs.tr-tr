---
description: 'Daha fazla bilgi edinin: SyncLock ekstresi'
title: SyncLock Deyimi
ms.date: 07/20/2015
f1_keywords:
- vb.SyncLock
- SyncLock
helpviewer_keywords:
- threading [Visual Basic], locks
- SyncLock statement [Visual Basic]
- locks, threads
ms.assetid: 14501703-298f-4d43-b139-c4b6366af176
ms.openlocfilehash: 206c10c8bca85a496345576d0d5f9ff260db82e3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99740983"
---
# <a name="synclock-statement"></a><span data-ttu-id="8f44c-103">SyncLock Deyimi</span><span class="sxs-lookup"><span data-stu-id="8f44c-103">SyncLock Statement</span></span>

<span data-ttu-id="8f44c-104">Bloğu yürütmeden önce bir ifade bloğu için özel bir kilit elde edin.</span><span class="sxs-lookup"><span data-stu-id="8f44c-104">Acquires an exclusive lock for a statement block before executing the block.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f44c-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="8f44c-105">Syntax</span></span>  
  
```vb  
SyncLock lockobject  
    [ block ]  
End SyncLock  
```  
  
## <a name="parts"></a><span data-ttu-id="8f44c-106">Bölümler</span><span class="sxs-lookup"><span data-stu-id="8f44c-106">Parts</span></span>  

 `lockobject`  
 <span data-ttu-id="8f44c-107">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="8f44c-107">Required.</span></span> <span data-ttu-id="8f44c-108">Bir nesne başvurusunu değerlendiren ifade.</span><span class="sxs-lookup"><span data-stu-id="8f44c-108">Expression that evaluates to an object reference.</span></span>  
  
 `block`  
 <span data-ttu-id="8f44c-109">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="8f44c-109">Optional.</span></span> <span data-ttu-id="8f44c-110">Kilit elde edildiğinde yürütülecek deyimler bloğu.</span><span class="sxs-lookup"><span data-stu-id="8f44c-110">Block of statements that are to execute when the lock is acquired.</span></span>  
  
 `End SyncLock`  
 <span data-ttu-id="8f44c-111">Bir `SyncLock` bloğu sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="8f44c-111">Terminates a `SyncLock` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8f44c-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8f44c-112">Remarks</span></span>  

 <span data-ttu-id="8f44c-113">`SyncLock`İfade, birden çok iş parçacığının aynı anda ekstre bloğunu yürütmemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="8f44c-113">The `SyncLock` statement ensures that multiple threads do not execute the statement block at the same time.</span></span> <span data-ttu-id="8f44c-114">`SyncLock` başka bir iş parçacığı yürütülene kadar her bir iş parçacığının blok girmesini engeller.</span><span class="sxs-lookup"><span data-stu-id="8f44c-114">`SyncLock` prevents each thread from entering the block until no other thread is executing it.</span></span>  
  
 <span data-ttu-id="8f44c-115">En yaygın kullanımı, `SyncLock` verilerin birden fazla iş parçacığı tarafından aynı anda güncelleştirilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="8f44c-115">The most common use of `SyncLock` is to protect data from being updated by more than one thread simultaneously.</span></span> <span data-ttu-id="8f44c-116">Verileri işleyen deyimlerin kesinti olmadan tamamlanmasına gitmesi gerekiyorsa, bunları bir blok içine koyun `SyncLock` .</span><span class="sxs-lookup"><span data-stu-id="8f44c-116">If the statements that manipulate the data must go to completion without interruption, put them inside a `SyncLock` block.</span></span>  
  
 <span data-ttu-id="8f44c-117">Özel bir kilit tarafından korunan bir ifade bloğu bazen *kritik bir bölüm* olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="8f44c-117">A statement block protected by an exclusive lock is sometimes called a *critical section*.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="8f44c-118">Kurallar</span><span class="sxs-lookup"><span data-stu-id="8f44c-118">Rules</span></span>  
  
- <span data-ttu-id="8f44c-119">Dallanma.</span><span class="sxs-lookup"><span data-stu-id="8f44c-119">Branching.</span></span> <span data-ttu-id="8f44c-120">Bloğunun dışından bir bloğa dallandırılamıyor `SyncLock` .</span><span class="sxs-lookup"><span data-stu-id="8f44c-120">You cannot branch into a `SyncLock` block from outside the block.</span></span>  
  
- <span data-ttu-id="8f44c-121">Nesne değerini kilitle.</span><span class="sxs-lookup"><span data-stu-id="8f44c-121">Lock Object Value.</span></span> <span data-ttu-id="8f44c-122">Değeri olamaz `lockobject` `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="8f44c-122">The value of `lockobject` cannot be `Nothing`.</span></span> <span data-ttu-id="8f44c-123">Bir ifadede kullanmadan önce Lock nesnesini oluşturmanız gerekir `SyncLock` .</span><span class="sxs-lookup"><span data-stu-id="8f44c-123">You must create the lock object before you use it in a `SyncLock` statement.</span></span>  
  
     <span data-ttu-id="8f44c-124">`lockobject`Bir blok yürütülürken değerini değiştiremezsiniz `SyncLock` .</span><span class="sxs-lookup"><span data-stu-id="8f44c-124">You cannot change the value of `lockobject` while executing a `SyncLock` block.</span></span> <span data-ttu-id="8f44c-125">Mekanizma, kilit nesnesinin değişmeden kalmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="8f44c-125">The mechanism requires that the lock object remain unchanged.</span></span>  
  
- <span data-ttu-id="8f44c-126">Bir blokta [await](../operators/await-operator.md) işlecini kullanamazsınız `SyncLock` .</span><span class="sxs-lookup"><span data-stu-id="8f44c-126">You can't use the [Await](../operators/await-operator.md) operator in a `SyncLock` block.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="8f44c-127">Davranış</span><span class="sxs-lookup"><span data-stu-id="8f44c-127">Behavior</span></span>  
  
- <span data-ttu-id="8f44c-128">Mekanizmadır.</span><span class="sxs-lookup"><span data-stu-id="8f44c-128">Mechanism.</span></span> <span data-ttu-id="8f44c-129">Bir iş parçacığı ifadeye ulaştığında `SyncLock` , ifadeyi değerlendirir `lockobject` ve ifadenin döndürdüğü nesne üzerinde dışlamalı bir kilit elde edene kadar yürütmeyi askıya alır.</span><span class="sxs-lookup"><span data-stu-id="8f44c-129">When a thread reaches the `SyncLock` statement, it evaluates the `lockobject` expression and suspends execution until it acquires an exclusive lock on the object returned by the expression.</span></span> <span data-ttu-id="8f44c-130">Başka bir iş parçacığı `SyncLock` ifadeye ulaştığında, ilk iş parçacığı ifadeyi çalıştırana kadar bir kilit almaz `End SyncLock` .</span><span class="sxs-lookup"><span data-stu-id="8f44c-130">When another thread reaches the `SyncLock` statement, it does not acquire a lock until the first thread executes the `End SyncLock` statement.</span></span>  
  
- <span data-ttu-id="8f44c-131">Korumalı veriler.</span><span class="sxs-lookup"><span data-stu-id="8f44c-131">Protected Data.</span></span> <span data-ttu-id="8f44c-132">`lockobject`Bir `Shared` değişkense, dışlamalı kilit, `SyncLock` başka bir iş parçacığı yürütülürken, sınıfın herhangi bir örneğindeki bir iş parçacığının bloğunu yürütmesini engeller.</span><span class="sxs-lookup"><span data-stu-id="8f44c-132">If `lockobject` is a `Shared` variable, the exclusive lock prevents a thread in any instance of the class from executing the `SyncLock` block while any other thread is executing it.</span></span> <span data-ttu-id="8f44c-133">Bu, tüm örnekler arasında paylaşılan verileri korur.</span><span class="sxs-lookup"><span data-stu-id="8f44c-133">This protects data that is shared among all the instances.</span></span>  
  
     <span data-ttu-id="8f44c-134">`lockobject`Bir örnek değişkenidir (değil `Shared` ), kilit, geçerli örnekte çalışan bir iş parçacığının `SyncLock` aynı anda aynı örnekteki başka bir iş parçacığı ile aynı zamanda yürütülmesini önler.</span><span class="sxs-lookup"><span data-stu-id="8f44c-134">If `lockobject` is an instance variable (not `Shared`), the lock prevents a thread running in the current instance from executing the `SyncLock` block at the same time as another thread in the same instance.</span></span> <span data-ttu-id="8f44c-135">Bu, bireysel örnek tarafından tutulan verileri korur.</span><span class="sxs-lookup"><span data-stu-id="8f44c-135">This protects data maintained by the individual instance.</span></span>  
  
- <span data-ttu-id="8f44c-136">Alma ve yayınlama.</span><span class="sxs-lookup"><span data-stu-id="8f44c-136">Acquisition and Release.</span></span> <span data-ttu-id="8f44c-137">Bir `SyncLock` blok `Try...Finally` , blok üzerinde özel bir kilit elde eden bir oluşturma gibi davranır `Try` `lockobject` ve `Finally` blok onu yayınlar.</span><span class="sxs-lookup"><span data-stu-id="8f44c-137">A `SyncLock` block behaves like a `Try...Finally` construction in which the `Try` block acquires an exclusive lock on `lockobject` and the `Finally` block releases it.</span></span> <span data-ttu-id="8f44c-138">Bu nedenle, bloğundan `SyncLock` çıktığınızda, blok kilidi garanti eder.</span><span class="sxs-lookup"><span data-stu-id="8f44c-138">Because of this, the `SyncLock` block guarantees release of the lock, no matter how you exit the block.</span></span> <span data-ttu-id="8f44c-139">Bu, işlenmemiş bir özel durum durumunda bile geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="8f44c-139">This is true even in the case of an unhandled exception.</span></span>  
  
- <span data-ttu-id="8f44c-140">Çerçeve çağrıları.</span><span class="sxs-lookup"><span data-stu-id="8f44c-140">Framework Calls.</span></span> <span data-ttu-id="8f44c-141">`SyncLock`Bloğu, `Enter` `Exit` `Monitor` ad alanındaki sınıfının ve yöntemlerini çağırarak dışlamalı kilidi alır ve serbest bırakır <xref:System.Threading> .</span><span class="sxs-lookup"><span data-stu-id="8f44c-141">The `SyncLock` block acquires and releases the exclusive lock by calling the `Enter` and `Exit` methods of the `Monitor` class in the <xref:System.Threading> namespace.</span></span>  
  
## <a name="programming-practices"></a><span data-ttu-id="8f44c-142">Programlama uygulamaları</span><span class="sxs-lookup"><span data-stu-id="8f44c-142">Programming Practices</span></span>  

 <span data-ttu-id="8f44c-143">`lockobject`İfade her zaman yalnızca kendi sınıfınıza ait olan bir nesne olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="8f44c-143">The `lockobject` expression should always evaluate to an object that belongs exclusively to your class.</span></span> <span data-ttu-id="8f44c-144">`Private`Geçerli örneğe ait verileri korumak için bir nesne değişkeni veya `Private Shared` tüm örneklerde ortak olan verileri korumak için bir nesne değişkeni bildirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="8f44c-144">You should declare a `Private` object variable to protect data belonging to the current instance, or a `Private Shared` object variable to protect data common to all instances.</span></span>  
  
 <span data-ttu-id="8f44c-145">`Me`Örnek verileri için bir kilit nesnesi sağlamak üzere anahtar sözcüğünü kullanmamalısınız.</span><span class="sxs-lookup"><span data-stu-id="8f44c-145">You should not use the `Me` keyword to provide a lock object for instance data.</span></span> <span data-ttu-id="8f44c-146">Sınıfınıza dış kod, sınıfınızın bir örneğine başvuru içeriyorsa, bu başvuruyu `SyncLock` kendi sizinkinden tamamen farklı, farklı verileri koruyan bir blok için bir kilit nesnesi olarak kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="8f44c-146">If code external to your class has a reference to an instance of your class, it could use that reference as a lock object for a `SyncLock` block completely different from yours, protecting different data.</span></span> <span data-ttu-id="8f44c-147">Bu şekilde, sınıfınız ve diğer sınıf, birbirini ilgisiz blokları yürütmelerini engelleyebilir `SyncLock` .</span><span class="sxs-lookup"><span data-stu-id="8f44c-147">In this way, your class and the other class could block each other from executing their unrelated `SyncLock` blocks.</span></span> <span data-ttu-id="8f44c-148">Aynı dizeyi kullanan işlemdeki diğer kodlar aynı kilidi paylaştığından, bir dizedeki aynı şekilde kilitleme sorunlu olabilir.</span><span class="sxs-lookup"><span data-stu-id="8f44c-148">Similarly locking on a string can be problematic since any other code in the process using the same string will share the same lock.</span></span>  
  
 <span data-ttu-id="8f44c-149">Ayrıca, `Me.GetType` paylaşılan veriler için bir kilit nesnesi sağlamak üzere metodunu kullanmamalısınız.</span><span class="sxs-lookup"><span data-stu-id="8f44c-149">You should also not use the `Me.GetType` method to provide a lock object for shared data.</span></span> <span data-ttu-id="8f44c-150">Bunun nedeni, `GetType` her zaman `Type` belirli bir sınıf adı için aynı nesneyi döndürmektedir.</span><span class="sxs-lookup"><span data-stu-id="8f44c-150">This is because `GetType` always returns the same `Type` object for a given class name.</span></span> <span data-ttu-id="8f44c-151">Dış kod `GetType` , sınıfınıza çağrı verebilir ve kullanmakta olduğunuz kilit nesnesini alabilir.</span><span class="sxs-lookup"><span data-stu-id="8f44c-151">External code could call `GetType` on your class and obtain the same lock object you are using.</span></span> <span data-ttu-id="8f44c-152">Bu, iki sınıfın bloklarından birbirini engellemesine neden olur `SyncLock` .</span><span class="sxs-lookup"><span data-stu-id="8f44c-152">This would result in the two classes blocking each other from their `SyncLock` blocks.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="8f44c-153">Örnekler</span><span class="sxs-lookup"><span data-stu-id="8f44c-153">Examples</span></span>  
  
### <a name="description"></a><span data-ttu-id="8f44c-154">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8f44c-154">Description</span></span>  

 <span data-ttu-id="8f44c-155">Aşağıdaki örnek, bir ileti listesini tutan bir sınıfı gösterir.</span><span class="sxs-lookup"><span data-stu-id="8f44c-155">The following example shows a class that maintains a simple list of messages.</span></span> <span data-ttu-id="8f44c-156">Bir dizideki iletileri ve bu dizinin son kullanılan öğesini bir değişkende tutar.</span><span class="sxs-lookup"><span data-stu-id="8f44c-156">It holds the messages in an array and the last used element of that array in a variable.</span></span> <span data-ttu-id="8f44c-157">`addAnotherMessage`Yordam, son öğeyi artırır ve yeni iletiyi depolar.</span><span class="sxs-lookup"><span data-stu-id="8f44c-157">The `addAnotherMessage` procedure increments the last element and stores the new message.</span></span> <span data-ttu-id="8f44c-158">Bu iki işlem ve deyimleri tarafından korunur `SyncLock` `End SyncLock` , çünkü son öğe artdıktan sonra yeni ileti, diğer herhangi bir iş parçacığının son öğeyi yeniden artırılabilmesi için önce depolanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8f44c-158">Those two operations are protected by the `SyncLock` and `End SyncLock` statements, because once the last element has been incremented, the new message must be stored before any other thread can increment the last element again.</span></span>  
  
 <span data-ttu-id="8f44c-159">Sınıf, `simpleMessageList` tüm örnekleri arasında bir ileti listesi paylaşmışsa, değişkenleri `messagesList` ve `messagesLast` olarak olarak bildirilenler `Shared` .</span><span class="sxs-lookup"><span data-stu-id="8f44c-159">If the `simpleMessageList` class shared one list of messages among all its instances, the variables `messagesList` and `messagesLast` would be declared as `Shared`.</span></span> <span data-ttu-id="8f44c-160">Bu durumda, değişken `messagesLock` de olmalıdır `Shared` , böylece her örnek tarafından kullanılan tek bir kilit nesnesi olur.</span><span class="sxs-lookup"><span data-stu-id="8f44c-160">In this case, the variable `messagesLock` should also be `Shared`, so that there would be a single lock object used by every instance.</span></span>  
  
### <a name="code"></a><span data-ttu-id="8f44c-161">Kod</span><span class="sxs-lookup"><span data-stu-id="8f44c-161">Code</span></span>  

 [!code-vb[VbVbalrThreading#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrThreading/VB/Class1.vb#1)]  
  
### <a name="description"></a><span data-ttu-id="8f44c-162">Description</span><span class="sxs-lookup"><span data-stu-id="8f44c-162">Description</span></span>  

 <span data-ttu-id="8f44c-163">Aşağıdaki örnek, ve iş parçacıklarını kullanır `SyncLock` .</span><span class="sxs-lookup"><span data-stu-id="8f44c-163">The following example uses threads and `SyncLock`.</span></span> <span data-ttu-id="8f44c-164">Deyimin bulunduğu sürece `SyncLock` , ifade bloğu kritik bir bölümdür ve `balance` hiçbir zaman negatif bir sayı değildir.</span><span class="sxs-lookup"><span data-stu-id="8f44c-164">As long as the `SyncLock` statement is present, the statement block is a critical section and `balance` never becomes a negative number.</span></span> <span data-ttu-id="8f44c-165">`SyncLock` `End SyncLock` Anahtar sözcüğünü bırakma etkisini görmek için ve deyimlerini açıklama ekleyebilirsiniz `SyncLock` .</span><span class="sxs-lookup"><span data-stu-id="8f44c-165">You can comment out the `SyncLock` and `End SyncLock` statements to see the effect of leaving out the `SyncLock` keyword.</span></span>  
  
### <a name="code"></a><span data-ttu-id="8f44c-166">Kod</span><span class="sxs-lookup"><span data-stu-id="8f44c-166">Code</span></span>  

 [!code-vb[VbVbalrThreading#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrThreading/VB/class2.vb#21)]  
  
### <a name="comments"></a><span data-ttu-id="8f44c-167">Yorumlar</span><span class="sxs-lookup"><span data-stu-id="8f44c-167">Comments</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f44c-168">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8f44c-168">See also</span></span>

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.Interlocked?displayProperty=nameWithType>
- [<span data-ttu-id="8f44c-169">Eşitleme temellerine genel bakış</span><span class="sxs-lookup"><span data-stu-id="8f44c-169">Overview of synchronization primitives</span></span>](../../../standard/threading/overview-of-synchronization-primitives.md)
