---
title: SyncLock Deyimi
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.SyncLock
- SyncLock
helpviewer_keywords:
- threading [Visual Basic], locks
- SyncLock statement [Visual Basic]
- locks, threads
ms.assetid: 14501703-298f-4d43-b139-c4b6366af176
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c0c826e1ba592dfc4f2899a26102466d2e7df54f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="synclock-statement"></a><span data-ttu-id="26690-102">SyncLock Deyimi</span><span class="sxs-lookup"><span data-stu-id="26690-102">SyncLock Statement</span></span>
<span data-ttu-id="26690-103">Özel bir kilit deyimi bloğu için blok yürütmeden önce devralır.</span><span class="sxs-lookup"><span data-stu-id="26690-103">Acquires an exclusive lock for a statement block before executing the block.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26690-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="26690-104">Syntax</span></span>  
  
```  
SyncLock lockobject  
    [ block ]  
End SyncLock  
```  
  
## <a name="parts"></a><span data-ttu-id="26690-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="26690-105">Parts</span></span>  
 `lockobject`  
 <span data-ttu-id="26690-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="26690-106">Required.</span></span> <span data-ttu-id="26690-107">Bir nesne başvurusu veren ifade.</span><span class="sxs-lookup"><span data-stu-id="26690-107">Expression that evaluates to an object reference.</span></span>  
  
 `block`  
 <span data-ttu-id="26690-108">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="26690-108">Optional.</span></span> <span data-ttu-id="26690-109">Kilit alındığında yürütmek üzere olduğunuz deyimleri bloğu.</span><span class="sxs-lookup"><span data-stu-id="26690-109">Block of statements that are to execute when the lock is acquired.</span></span>  
  
 `End SyncLock`  
 <span data-ttu-id="26690-110">Sonlandırır bir `SyncLock` bloğu.</span><span class="sxs-lookup"><span data-stu-id="26690-110">Terminates a `SyncLock` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="26690-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="26690-111">Remarks</span></span>  
 <span data-ttu-id="26690-112">`SyncLock` Deyimi sağlar birden çok iş parçacığı aynı anda deyimi blok yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="26690-112">The `SyncLock` statement ensures that multiple threads do not execute the statement block at the same time.</span></span> <span data-ttu-id="26690-113">`SyncLock`Her iş parçacığı, başka bir iş parçacığı, yürütülmekte olduğu kadar blok geçmesini engeller.</span><span class="sxs-lookup"><span data-stu-id="26690-113">`SyncLock` prevents each thread from entering the block until no other thread is executing it.</span></span>  
  
 <span data-ttu-id="26690-114">En yaygın kullanımı `SyncLock` verileri birden çok iş parçacığı tarafından eşzamanlı olarak güncelleştirilmesini korumaktır.</span><span class="sxs-lookup"><span data-stu-id="26690-114">The most common use of `SyncLock` is to protect data from being updated by more than one thread simultaneously.</span></span> <span data-ttu-id="26690-115">Verileri işlemek deyimleri kesintisiz tamamlama gerekir giderseniz, bunları içine yerleştirin bir `SyncLock` bloğu.</span><span class="sxs-lookup"><span data-stu-id="26690-115">If the statements that manipulate the data must go to completion without interruption, put them inside a `SyncLock` block.</span></span>  
  
 <span data-ttu-id="26690-116">Özel bir kilit tarafından korunan bir ifade bloğu adlandırılan bir *kritik bölüm*.</span><span class="sxs-lookup"><span data-stu-id="26690-116">A statement block protected by an exclusive lock is sometimes called a *critical section*.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="26690-117">Kurallar</span><span class="sxs-lookup"><span data-stu-id="26690-117">Rules</span></span>  
  
-   <span data-ttu-id="26690-118">Dal oluşturma.</span><span class="sxs-lookup"><span data-stu-id="26690-118">Branching.</span></span> <span data-ttu-id="26690-119">İçine dallanamıyor bir `SyncLock` dışında blok önleyin.</span><span class="sxs-lookup"><span data-stu-id="26690-119">You cannot branch into a `SyncLock` block from outside the block.</span></span>  
  
-   <span data-ttu-id="26690-120">Kilit nesne değeri.</span><span class="sxs-lookup"><span data-stu-id="26690-120">Lock Object Value.</span></span> <span data-ttu-id="26690-121">Değeri `lockobject` olamaz `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="26690-121">The value of `lockobject` cannot be `Nothing`.</span></span> <span data-ttu-id="26690-122">İçinde kullanmadan önce kilit nesnesi oluşturmanız gerekir bir `SyncLock` deyimi.</span><span class="sxs-lookup"><span data-stu-id="26690-122">You must create the lock object before you use it in a `SyncLock` statement.</span></span>  
  
     <span data-ttu-id="26690-123">Değeri değiştiremezsiniz `lockobject` yürütülürken bir `SyncLock` bloğu.</span><span class="sxs-lookup"><span data-stu-id="26690-123">You cannot change the value of `lockobject` while executing a `SyncLock` block.</span></span> <span data-ttu-id="26690-124">Kilit nesnesi değişmeden mekanizması gerektirir.</span><span class="sxs-lookup"><span data-stu-id="26690-124">The mechanism requires that the lock object remain unchanged.</span></span>  
  
-   <span data-ttu-id="26690-125">Kullanamazsınız [bekleme](../../../visual-basic/language-reference/operators/await-operator.md) işlecinde bir `SyncLock` bloğu.</span><span class="sxs-lookup"><span data-stu-id="26690-125">You can't use the [Await](../../../visual-basic/language-reference/operators/await-operator.md) operator in a `SyncLock` block.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="26690-126">Davranış</span><span class="sxs-lookup"><span data-stu-id="26690-126">Behavior</span></span>  
  
-   <span data-ttu-id="26690-127">Mekanizması.</span><span class="sxs-lookup"><span data-stu-id="26690-127">Mechanism.</span></span> <span data-ttu-id="26690-128">Bir iş parçacığı ulaştığında `SyncLock` deyimi, bu hesaplar `lockobject` ifade ve özel bir kilit ifadesi tarafından döndürülen nesne üzerinde edinir kadar yürütme askıya alır.</span><span class="sxs-lookup"><span data-stu-id="26690-128">When a thread reaches the `SyncLock` statement, it evaluates the `lockobject` expression and suspends execution until it acquires an exclusive lock on the object returned by the expression.</span></span> <span data-ttu-id="26690-129">Başka bir iş parçacığı ulaştığında `SyncLock` deyimi, onu olmayan bir kilit alınması ilk iş parçacığı yürütür kadar `End SyncLock` deyimi.</span><span class="sxs-lookup"><span data-stu-id="26690-129">When another thread reaches the `SyncLock` statement, it does not acquire a lock until the first thread executes the `End SyncLock` statement.</span></span>  
  
-   <span data-ttu-id="26690-130">Korunan veriler.</span><span class="sxs-lookup"><span data-stu-id="26690-130">Protected Data.</span></span> <span data-ttu-id="26690-131">Varsa `lockobject` olan bir `Shared` değişken, özel kullanım kilidi sınıfının bir örneğini bir iş parçacığında yürütülmesini engeller `SyncLock` başka bir iş parçacığı yürütülürken engelleyin.</span><span class="sxs-lookup"><span data-stu-id="26690-131">If `lockobject` is a `Shared` variable, the exclusive lock prevents a thread in any instance of the class from executing the `SyncLock` block while any other thread is executing it.</span></span> <span data-ttu-id="26690-132">Bu, tüm örnekler arasında paylaşılan verileri korur.</span><span class="sxs-lookup"><span data-stu-id="26690-132">This protects data that is shared among all the instances.</span></span>  
  
     <span data-ttu-id="26690-133">Varsa `lockobject` bir örnek değişkeni (değil `Shared`), kilit yürütülmesini geçerli örneğinde çalışan iş parçacığı engeller `SyncLock` başka bir iş parçacığı aynı örneğinde aynı zamanda bloğu.</span><span class="sxs-lookup"><span data-stu-id="26690-133">If `lockobject` is an instance variable (not `Shared`), the lock prevents a thread running in the current instance from executing the `SyncLock` block at the same time as another thread in the same instance.</span></span> <span data-ttu-id="26690-134">Bu, tek tek örneği tarafından tutulan verileri korur.</span><span class="sxs-lookup"><span data-stu-id="26690-134">This protects data maintained by the individual instance.</span></span>  
  
-   <span data-ttu-id="26690-135">Edinme ve sürüm.</span><span class="sxs-lookup"><span data-stu-id="26690-135">Acquisition and Release.</span></span> <span data-ttu-id="26690-136">A `SyncLock` engelleme davranacağını gibi bir `Try...Finally` yapım, `Try` blok üzerinde özel bir kilit edinir `lockobject` ve `Finally` blok yayımlar.</span><span class="sxs-lookup"><span data-stu-id="26690-136">A `SyncLock` block behaves like a `Try...Finally` construction in which the `Try` block acquires an exclusive lock on `lockobject` and the `Finally` block releases it.</span></span> <span data-ttu-id="26690-137">Bu nedenle, `SyncLock` blok blok çıkmak nasıl olsun kilidi sürümü güvence altına alır.</span><span class="sxs-lookup"><span data-stu-id="26690-137">Because of this, the `SyncLock` block guarantees release of the lock, no matter how you exit the block.</span></span> <span data-ttu-id="26690-138">Bu, hatta işlenmeyen bir özel durum söz konusu olduğunda geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="26690-138">This is true even in the case of an unhandled exception.</span></span>  
  
-   <span data-ttu-id="26690-139">Framework çağırır.</span><span class="sxs-lookup"><span data-stu-id="26690-139">Framework Calls.</span></span> <span data-ttu-id="26690-140">`SyncLock` Bloğu edinir ve çağırarak özel kullanım kilidi serbest `Enter` ve `Exit` yöntemlerinin `Monitor` sınıfını <xref:System.Threading> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="26690-140">The `SyncLock` block acquires and releases the exclusive lock by calling the `Enter` and `Exit` methods of the `Monitor` class in the <xref:System.Threading> namespace.</span></span>  
  
## <a name="programming-practices"></a><span data-ttu-id="26690-141">Programlama yöntemler</span><span class="sxs-lookup"><span data-stu-id="26690-141">Programming Practices</span></span>  
 <span data-ttu-id="26690-142">`lockobject` İfade her zaman özel olarak sınıfa ait bir nesneye değerlendirin.</span><span class="sxs-lookup"><span data-stu-id="26690-142">The `lockobject` expression should always evaluate to an object that belongs exclusively to your class.</span></span> <span data-ttu-id="26690-143">Bildirmeniz gerekir bir `Private` geçerli örneğine ait olan verileri korumak için nesne değişkeni veya `Private Shared` için tüm örnekleri ortak verileri korumak için nesne değişkeni.</span><span class="sxs-lookup"><span data-stu-id="26690-143">You should declare a `Private` object variable to protect data belonging to the current instance, or a `Private Shared` object variable to protect data common to all instances.</span></span>  
  
 <span data-ttu-id="26690-144">Kullanılamaz `Me` anahtar sözcüğü bir kilit sağlamak için nesne örneği için veri.</span><span class="sxs-lookup"><span data-stu-id="26690-144">You should not use the `Me` keyword to provide a lock object for instance data.</span></span> <span data-ttu-id="26690-145">Kodu sınıfınıza dış sınıfının bir örneğine başvuru varsa, bunun için bir kilit nesnesi olarak bu başvuruyu kullanabilir bir `SyncLock` blok sizin tamamen farklı farklı veri koruma.</span><span class="sxs-lookup"><span data-stu-id="26690-145">If code external to your class has a reference to an instance of your class, it could use that reference as a lock object for a `SyncLock` block completely different from yours, protecting different data.</span></span> <span data-ttu-id="26690-146">Bu şekilde, sizin ve diğer sınıf birbiriyle ilgisiz kendi yürütülmesini engelleyin `SyncLock` engeller.</span><span class="sxs-lookup"><span data-stu-id="26690-146">In this way, your class and the other class could block each other from executing their unrelated `SyncLock` blocks.</span></span> <span data-ttu-id="26690-147">Aynı dize kullanarak işlemdeki başka bir kod aynı kilit paylaşacak beri benzer şekilde bir dizesine kilitleme sorunlu olabilir.</span><span class="sxs-lookup"><span data-stu-id="26690-147">Similarly locking on a string can be problematic since any other code in the process using the same string will share the same lock.</span></span>  
  
 <span data-ttu-id="26690-148">Ayrıca kullanılamaz `Me.GetType` yöntemi için bir kilit nesnesi sağlamak için paylaşılan veri.</span><span class="sxs-lookup"><span data-stu-id="26690-148">You should also not use the `Me.GetType` method to provide a lock object for shared data.</span></span> <span data-ttu-id="26690-149">Bunun nedeni, `GetType` her zaman aynı döndürür `Type` nesne belirtilen sınıf adı.</span><span class="sxs-lookup"><span data-stu-id="26690-149">This is because `GetType` always returns the same `Type` object for a given class name.</span></span> <span data-ttu-id="26690-150">Harici kod çağrısı `GetType` sınıfınızın ve kullandığınız aynı kilit nesnesini alın.</span><span class="sxs-lookup"><span data-stu-id="26690-150">External code could call `GetType` on your class and obtain the same lock object you are using.</span></span> <span data-ttu-id="26690-151">Bu birbirinden engelleme iki sınıf ile sonuçlandı kendi `SyncLock` engeller.</span><span class="sxs-lookup"><span data-stu-id="26690-151">This would result in the two classes blocking each other from their `SyncLock` blocks.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="26690-152">Örnekler</span><span class="sxs-lookup"><span data-stu-id="26690-152">Examples</span></span>  
  
### <a name="description"></a><span data-ttu-id="26690-153">Açıklama</span><span class="sxs-lookup"><span data-stu-id="26690-153">Description</span></span>  
 <span data-ttu-id="26690-154">Aşağıdaki örnekte basit iletilerin listesini tutar bir sınıfı gösterir.</span><span class="sxs-lookup"><span data-stu-id="26690-154">The following example shows a class that maintains a simple list of messages.</span></span> <span data-ttu-id="26690-155">Bir dizi iletileri tutar ve son bu dizinin öğesi bir değişkende kullanılır.</span><span class="sxs-lookup"><span data-stu-id="26690-155">It holds the messages in an array and the last used element of that array in a variable.</span></span> <span data-ttu-id="26690-156">`addAnotherMessage` Yordamı son öğe artırır ve yeni ileti depolar.</span><span class="sxs-lookup"><span data-stu-id="26690-156">The `addAnotherMessage` procedure increments the last element and stores the new message.</span></span> <span data-ttu-id="26690-157">Bu iki işlemler tarafından korunan `SyncLock` ve `End SyncLock` deyimleri, son öğe artar sonra başka bir iş parçacığı son öğe yeniden artırabilirsiniz önce yeni ileti depolanması gerekir çünkü.</span><span class="sxs-lookup"><span data-stu-id="26690-157">Those two operations are protected by the `SyncLock` and `End SyncLock` statements, because once the last element has been incremented, the new message must be stored before any other thread can increment the last element again.</span></span>  
  
 <span data-ttu-id="26690-158">Varsa `simpleMessageList` sınıfı paylaşılan tüm örneklerini, değişkenleri arasında iletilerinin bir listesini `messagesList` ve `messagesLast` olarak bildirilmesi `Shared`.</span><span class="sxs-lookup"><span data-stu-id="26690-158">If the `simpleMessageList` class shared one list of messages among all its instances, the variables `messagesList` and `messagesLast` would be declared as `Shared`.</span></span> <span data-ttu-id="26690-159">Bu durumda, değişkeni `messagesLock` ayrıca olmalıdır `Shared`her örneği tarafından kullanılan tek kilit nesnesi böylece bulunmaz.</span><span class="sxs-lookup"><span data-stu-id="26690-159">In this case, the variable `messagesLock` should also be `Shared`, so that there would be a single lock object used by every instance.</span></span>  
  
### <a name="code"></a><span data-ttu-id="26690-160">Kod</span><span class="sxs-lookup"><span data-stu-id="26690-160">Code</span></span>  
 [!code-vb[VbVbalrThreading#1](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/synclock-statement_1.vb)]  
  
### <a name="description"></a><span data-ttu-id="26690-161">Açıklama</span><span class="sxs-lookup"><span data-stu-id="26690-161">Description</span></span>  
 <span data-ttu-id="26690-162">Aşağıdaki örnek, iş parçacığı kullanır ve `SyncLock`.</span><span class="sxs-lookup"><span data-stu-id="26690-162">The following example uses threads and `SyncLock`.</span></span> <span data-ttu-id="26690-163">Sürece `SyncLock` deyimi varsa, deyimi blok kritik bir bölümdür ve `balance` hiçbir zaman negatif bir sayı olur.</span><span class="sxs-lookup"><span data-stu-id="26690-163">As long as the `SyncLock` statement is present, the statement block is a critical section and `balance` never becomes a negative number.</span></span> <span data-ttu-id="26690-164">Out açıklama `SyncLock` ve `End SyncLock` bırakarak etkisini görmek için deyimleri `SyncLock` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="26690-164">You can comment out the `SyncLock` and `End SyncLock` statements to see the effect of leaving out the `SyncLock` keyword.</span></span>  
  
### <a name="code"></a><span data-ttu-id="26690-165">Kod</span><span class="sxs-lookup"><span data-stu-id="26690-165">Code</span></span>  
 [!code-vb[VbVbalrThreading#21](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/synclock-statement_2.vb)]  
  
### <a name="comments"></a><span data-ttu-id="26690-166">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="26690-166">Comments</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26690-167">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="26690-167">See Also</span></span>  
 <xref:System.Threading>  
 <xref:System.Threading.Monitor>  
 [<span data-ttu-id="26690-168">İş parçacığı eşitleme</span><span class="sxs-lookup"><span data-stu-id="26690-168">Thread Synchronization</span></span>](http://msdn.microsoft.com/library/413e1f28-a2c5-4eec-8338-aa43e7982ff4)  
 [<span data-ttu-id="26690-169">İş parçacığı oluşturma</span><span class="sxs-lookup"><span data-stu-id="26690-169">Threading</span></span>](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c)
