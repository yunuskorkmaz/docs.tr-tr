---
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
ms.openlocfilehash: cc8706b95e0785459e36abe27ce915b5bab8711a
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875203"
---
# <a name="synclock-statement"></a><span data-ttu-id="71e4f-102">SyncLock Deyimi</span><span class="sxs-lookup"><span data-stu-id="71e4f-102">SyncLock Statement</span></span>

<span data-ttu-id="71e4f-103">Bloğu yürütmeden önce bir ifade bloğu için özel bir kilit elde edin.</span><span class="sxs-lookup"><span data-stu-id="71e4f-103">Acquires an exclusive lock for a statement block before executing the block.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71e4f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="71e4f-104">Syntax</span></span>  
  
```vb  
SyncLock lockobject  
    [ block ]  
End SyncLock  
```  
  
## <a name="parts"></a><span data-ttu-id="71e4f-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="71e4f-105">Parts</span></span>  

 `lockobject`  
 <span data-ttu-id="71e4f-106">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="71e4f-106">Required.</span></span> <span data-ttu-id="71e4f-107">Bir nesne başvurusunu değerlendiren ifade.</span><span class="sxs-lookup"><span data-stu-id="71e4f-107">Expression that evaluates to an object reference.</span></span>  
  
 `block`  
 <span data-ttu-id="71e4f-108">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="71e4f-108">Optional.</span></span> <span data-ttu-id="71e4f-109">Kilit elde edildiğinde yürütülecek deyimler bloğu.</span><span class="sxs-lookup"><span data-stu-id="71e4f-109">Block of statements that are to execute when the lock is acquired.</span></span>  
  
 `End SyncLock`  
 <span data-ttu-id="71e4f-110">Bir `SyncLock` bloğu sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="71e4f-110">Terminates a `SyncLock` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="71e4f-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="71e4f-111">Remarks</span></span>  

 <span data-ttu-id="71e4f-112">`SyncLock`İfade, birden çok iş parçacığının aynı anda ekstre bloğunu yürütmemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="71e4f-112">The `SyncLock` statement ensures that multiple threads do not execute the statement block at the same time.</span></span> <span data-ttu-id="71e4f-113">`SyncLock` başka bir iş parçacığı yürütülene kadar her bir iş parçacığının blok girmesini engeller.</span><span class="sxs-lookup"><span data-stu-id="71e4f-113">`SyncLock` prevents each thread from entering the block until no other thread is executing it.</span></span>  
  
 <span data-ttu-id="71e4f-114">En yaygın kullanımı, `SyncLock` verilerin birden fazla iş parçacığı tarafından aynı anda güncelleştirilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="71e4f-114">The most common use of `SyncLock` is to protect data from being updated by more than one thread simultaneously.</span></span> <span data-ttu-id="71e4f-115">Verileri işleyen deyimlerin kesinti olmadan tamamlanmasına gitmesi gerekiyorsa, bunları bir blok içine koyun `SyncLock` .</span><span class="sxs-lookup"><span data-stu-id="71e4f-115">If the statements that manipulate the data must go to completion without interruption, put them inside a `SyncLock` block.</span></span>  
  
 <span data-ttu-id="71e4f-116">Özel bir kilit tarafından korunan bir ifade bloğu bazen *kritik bir bölüm*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="71e4f-116">A statement block protected by an exclusive lock is sometimes called a *critical section*.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="71e4f-117">Kurallar</span><span class="sxs-lookup"><span data-stu-id="71e4f-117">Rules</span></span>  
  
- <span data-ttu-id="71e4f-118">Dallanma.</span><span class="sxs-lookup"><span data-stu-id="71e4f-118">Branching.</span></span> <span data-ttu-id="71e4f-119">Bloğunun dışından bir bloğa dallandırılamıyor `SyncLock` .</span><span class="sxs-lookup"><span data-stu-id="71e4f-119">You cannot branch into a `SyncLock` block from outside the block.</span></span>  
  
- <span data-ttu-id="71e4f-120">Nesne değerini kilitle.</span><span class="sxs-lookup"><span data-stu-id="71e4f-120">Lock Object Value.</span></span> <span data-ttu-id="71e4f-121">Değeri olamaz `lockobject` `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="71e4f-121">The value of `lockobject` cannot be `Nothing`.</span></span> <span data-ttu-id="71e4f-122">Bir ifadede kullanmadan önce Lock nesnesini oluşturmanız gerekir `SyncLock` .</span><span class="sxs-lookup"><span data-stu-id="71e4f-122">You must create the lock object before you use it in a `SyncLock` statement.</span></span>  
  
     <span data-ttu-id="71e4f-123">`lockobject`Bir blok yürütülürken değerini değiştiremezsiniz `SyncLock` .</span><span class="sxs-lookup"><span data-stu-id="71e4f-123">You cannot change the value of `lockobject` while executing a `SyncLock` block.</span></span> <span data-ttu-id="71e4f-124">Mekanizma, kilit nesnesinin değişmeden kalmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="71e4f-124">The mechanism requires that the lock object remain unchanged.</span></span>  
  
- <span data-ttu-id="71e4f-125">Bir blokta [await](../operators/await-operator.md) işlecini kullanamazsınız `SyncLock` .</span><span class="sxs-lookup"><span data-stu-id="71e4f-125">You can't use the [Await](../operators/await-operator.md) operator in a `SyncLock` block.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="71e4f-126">Davranış</span><span class="sxs-lookup"><span data-stu-id="71e4f-126">Behavior</span></span>  
  
- <span data-ttu-id="71e4f-127">Mekanizmadır.</span><span class="sxs-lookup"><span data-stu-id="71e4f-127">Mechanism.</span></span> <span data-ttu-id="71e4f-128">Bir iş parçacığı ifadeye ulaştığında `SyncLock` , ifadeyi değerlendirir `lockobject` ve ifadenin döndürdüğü nesne üzerinde dışlamalı bir kilit elde edene kadar yürütmeyi askıya alır.</span><span class="sxs-lookup"><span data-stu-id="71e4f-128">When a thread reaches the `SyncLock` statement, it evaluates the `lockobject` expression and suspends execution until it acquires an exclusive lock on the object returned by the expression.</span></span> <span data-ttu-id="71e4f-129">Başka bir iş parçacığı `SyncLock` ifadeye ulaştığında, ilk iş parçacığı ifadeyi çalıştırana kadar bir kilit almaz `End SyncLock` .</span><span class="sxs-lookup"><span data-stu-id="71e4f-129">When another thread reaches the `SyncLock` statement, it does not acquire a lock until the first thread executes the `End SyncLock` statement.</span></span>  
  
- <span data-ttu-id="71e4f-130">Korumalı veriler.</span><span class="sxs-lookup"><span data-stu-id="71e4f-130">Protected Data.</span></span> <span data-ttu-id="71e4f-131">`lockobject`Bir `Shared` değişkense, dışlamalı kilit, `SyncLock` başka bir iş parçacığı yürütülürken, sınıfın herhangi bir örneğindeki bir iş parçacığının bloğunu yürütmesini engeller.</span><span class="sxs-lookup"><span data-stu-id="71e4f-131">If `lockobject` is a `Shared` variable, the exclusive lock prevents a thread in any instance of the class from executing the `SyncLock` block while any other thread is executing it.</span></span> <span data-ttu-id="71e4f-132">Bu, tüm örnekler arasında paylaşılan verileri korur.</span><span class="sxs-lookup"><span data-stu-id="71e4f-132">This protects data that is shared among all the instances.</span></span>  
  
     <span data-ttu-id="71e4f-133">`lockobject`Bir örnek değişkenidir (değil `Shared` ), kilit, geçerli örnekte çalışan bir iş parçacığının `SyncLock` aynı anda aynı örnekteki başka bir iş parçacığı ile aynı zamanda yürütülmesini önler.</span><span class="sxs-lookup"><span data-stu-id="71e4f-133">If `lockobject` is an instance variable (not `Shared`), the lock prevents a thread running in the current instance from executing the `SyncLock` block at the same time as another thread in the same instance.</span></span> <span data-ttu-id="71e4f-134">Bu, bireysel örnek tarafından tutulan verileri korur.</span><span class="sxs-lookup"><span data-stu-id="71e4f-134">This protects data maintained by the individual instance.</span></span>  
  
- <span data-ttu-id="71e4f-135">Alma ve yayınlama.</span><span class="sxs-lookup"><span data-stu-id="71e4f-135">Acquisition and Release.</span></span> <span data-ttu-id="71e4f-136">Bir `SyncLock` blok `Try...Finally` , blok üzerinde özel bir kilit elde eden bir oluşturma gibi davranır `Try` `lockobject` ve `Finally` blok onu yayınlar.</span><span class="sxs-lookup"><span data-stu-id="71e4f-136">A `SyncLock` block behaves like a `Try...Finally` construction in which the `Try` block acquires an exclusive lock on `lockobject` and the `Finally` block releases it.</span></span> <span data-ttu-id="71e4f-137">Bu nedenle, bloğundan `SyncLock` çıktığınızda, blok kilidi garanti eder.</span><span class="sxs-lookup"><span data-stu-id="71e4f-137">Because of this, the `SyncLock` block guarantees release of the lock, no matter how you exit the block.</span></span> <span data-ttu-id="71e4f-138">Bu, işlenmemiş bir özel durum durumunda bile geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="71e4f-138">This is true even in the case of an unhandled exception.</span></span>  
  
- <span data-ttu-id="71e4f-139">Çerçeve çağrıları.</span><span class="sxs-lookup"><span data-stu-id="71e4f-139">Framework Calls.</span></span> <span data-ttu-id="71e4f-140">`SyncLock`Bloğu, `Enter` `Exit` `Monitor` ad alanındaki sınıfının ve yöntemlerini çağırarak dışlamalı kilidi alır ve serbest bırakır <xref:System.Threading> .</span><span class="sxs-lookup"><span data-stu-id="71e4f-140">The `SyncLock` block acquires and releases the exclusive lock by calling the `Enter` and `Exit` methods of the `Monitor` class in the <xref:System.Threading> namespace.</span></span>  
  
## <a name="programming-practices"></a><span data-ttu-id="71e4f-141">Programlama uygulamaları</span><span class="sxs-lookup"><span data-stu-id="71e4f-141">Programming Practices</span></span>  

 <span data-ttu-id="71e4f-142">`lockobject`İfade her zaman yalnızca kendi sınıfınıza ait olan bir nesne olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="71e4f-142">The `lockobject` expression should always evaluate to an object that belongs exclusively to your class.</span></span> <span data-ttu-id="71e4f-143">`Private`Geçerli örneğe ait verileri korumak için bir nesne değişkeni veya `Private Shared` tüm örneklerde ortak olan verileri korumak için bir nesne değişkeni bildirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="71e4f-143">You should declare a `Private` object variable to protect data belonging to the current instance, or a `Private Shared` object variable to protect data common to all instances.</span></span>  
  
 <span data-ttu-id="71e4f-144">`Me`Örnek verileri için bir kilit nesnesi sağlamak üzere anahtar sözcüğünü kullanmamalısınız.</span><span class="sxs-lookup"><span data-stu-id="71e4f-144">You should not use the `Me` keyword to provide a lock object for instance data.</span></span> <span data-ttu-id="71e4f-145">Sınıfınıza dış kod, sınıfınızın bir örneğine başvuru içeriyorsa, bu başvuruyu `SyncLock` kendi sizinkinden tamamen farklı, farklı verileri koruyan bir blok için bir kilit nesnesi olarak kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="71e4f-145">If code external to your class has a reference to an instance of your class, it could use that reference as a lock object for a `SyncLock` block completely different from yours, protecting different data.</span></span> <span data-ttu-id="71e4f-146">Bu şekilde, sınıfınız ve diğer sınıf, birbirini ilgisiz blokları yürütmelerini engelleyebilir `SyncLock` .</span><span class="sxs-lookup"><span data-stu-id="71e4f-146">In this way, your class and the other class could block each other from executing their unrelated `SyncLock` blocks.</span></span> <span data-ttu-id="71e4f-147">Aynı dizeyi kullanan işlemdeki diğer kodlar aynı kilidi paylaştığından, bir dizedeki aynı şekilde kilitleme sorunlu olabilir.</span><span class="sxs-lookup"><span data-stu-id="71e4f-147">Similarly locking on a string can be problematic since any other code in the process using the same string will share the same lock.</span></span>  
  
 <span data-ttu-id="71e4f-148">Ayrıca, `Me.GetType` paylaşılan veriler için bir kilit nesnesi sağlamak üzere metodunu kullanmamalısınız.</span><span class="sxs-lookup"><span data-stu-id="71e4f-148">You should also not use the `Me.GetType` method to provide a lock object for shared data.</span></span> <span data-ttu-id="71e4f-149">Bunun nedeni, `GetType` her zaman `Type` belirli bir sınıf adı için aynı nesneyi döndürmektedir.</span><span class="sxs-lookup"><span data-stu-id="71e4f-149">This is because `GetType` always returns the same `Type` object for a given class name.</span></span> <span data-ttu-id="71e4f-150">Dış kod `GetType` , sınıfınıza çağrı verebilir ve kullanmakta olduğunuz kilit nesnesini alabilir.</span><span class="sxs-lookup"><span data-stu-id="71e4f-150">External code could call `GetType` on your class and obtain the same lock object you are using.</span></span> <span data-ttu-id="71e4f-151">Bu, iki sınıfın bloklarından birbirini engellemesine neden olur `SyncLock` .</span><span class="sxs-lookup"><span data-stu-id="71e4f-151">This would result in the two classes blocking each other from their `SyncLock` blocks.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="71e4f-152">Örnekler</span><span class="sxs-lookup"><span data-stu-id="71e4f-152">Examples</span></span>  
  
### <a name="description"></a><span data-ttu-id="71e4f-153">Açıklama</span><span class="sxs-lookup"><span data-stu-id="71e4f-153">Description</span></span>  

 <span data-ttu-id="71e4f-154">Aşağıdaki örnek, bir ileti listesini tutan bir sınıfı gösterir.</span><span class="sxs-lookup"><span data-stu-id="71e4f-154">The following example shows a class that maintains a simple list of messages.</span></span> <span data-ttu-id="71e4f-155">Bir dizideki iletileri ve bu dizinin son kullanılan öğesini bir değişkende tutar.</span><span class="sxs-lookup"><span data-stu-id="71e4f-155">It holds the messages in an array and the last used element of that array in a variable.</span></span> <span data-ttu-id="71e4f-156">`addAnotherMessage`Yordam, son öğeyi artırır ve yeni iletiyi depolar.</span><span class="sxs-lookup"><span data-stu-id="71e4f-156">The `addAnotherMessage` procedure increments the last element and stores the new message.</span></span> <span data-ttu-id="71e4f-157">Bu iki işlem ve deyimleri tarafından korunur `SyncLock` `End SyncLock` , çünkü son öğe artdıktan sonra yeni ileti, diğer herhangi bir iş parçacığının son öğeyi yeniden artırılabilmesi için önce depolanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="71e4f-157">Those two operations are protected by the `SyncLock` and `End SyncLock` statements, because once the last element has been incremented, the new message must be stored before any other thread can increment the last element again.</span></span>  
  
 <span data-ttu-id="71e4f-158">Sınıf, `simpleMessageList` tüm örnekleri arasında bir ileti listesi paylaşmışsa, değişkenleri `messagesList` ve `messagesLast` olarak olarak bildirilenler `Shared` .</span><span class="sxs-lookup"><span data-stu-id="71e4f-158">If the `simpleMessageList` class shared one list of messages among all its instances, the variables `messagesList` and `messagesLast` would be declared as `Shared`.</span></span> <span data-ttu-id="71e4f-159">Bu durumda, değişken `messagesLock` de olmalıdır `Shared` , böylece her örnek tarafından kullanılan tek bir kilit nesnesi olur.</span><span class="sxs-lookup"><span data-stu-id="71e4f-159">In this case, the variable `messagesLock` should also be `Shared`, so that there would be a single lock object used by every instance.</span></span>  
  
### <a name="code"></a><span data-ttu-id="71e4f-160">Kod</span><span class="sxs-lookup"><span data-stu-id="71e4f-160">Code</span></span>  

 [!code-vb[VbVbalrThreading#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrThreading/VB/Class1.vb#1)]  
  
### <a name="description"></a><span data-ttu-id="71e4f-161">Açıklama</span><span class="sxs-lookup"><span data-stu-id="71e4f-161">Description</span></span>  

 <span data-ttu-id="71e4f-162">Aşağıdaki örnek, ve iş parçacıklarını kullanır `SyncLock` .</span><span class="sxs-lookup"><span data-stu-id="71e4f-162">The following example uses threads and `SyncLock`.</span></span> <span data-ttu-id="71e4f-163">Deyimin bulunduğu sürece `SyncLock` , ifade bloğu kritik bir bölümdür ve `balance` hiçbir zaman negatif bir sayı değildir.</span><span class="sxs-lookup"><span data-stu-id="71e4f-163">As long as the `SyncLock` statement is present, the statement block is a critical section and `balance` never becomes a negative number.</span></span> <span data-ttu-id="71e4f-164">`SyncLock` `End SyncLock` Anahtar sözcüğünü bırakma etkisini görmek için ve deyimlerini açıklama ekleyebilirsiniz `SyncLock` .</span><span class="sxs-lookup"><span data-stu-id="71e4f-164">You can comment out the `SyncLock` and `End SyncLock` statements to see the effect of leaving out the `SyncLock` keyword.</span></span>  
  
### <a name="code"></a><span data-ttu-id="71e4f-165">Kod</span><span class="sxs-lookup"><span data-stu-id="71e4f-165">Code</span></span>  

 [!code-vb[VbVbalrThreading#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrThreading/VB/class2.vb#21)]  
  
### <a name="comments"></a><span data-ttu-id="71e4f-166">Yorumlar</span><span class="sxs-lookup"><span data-stu-id="71e4f-166">Comments</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71e4f-167">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="71e4f-167">See also</span></span>

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.Interlocked?displayProperty=nameWithType>
- [<span data-ttu-id="71e4f-168">Eşitleme temellerine genel bakış</span><span class="sxs-lookup"><span data-stu-id="71e4f-168">Overview of synchronization primitives</span></span>](../../../standard/threading/overview-of-synchronization-primitives.md)
