---
title: SyncLock deyimi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.SyncLock
- SyncLock
helpviewer_keywords:
- threading [Visual Basic], locks
- SyncLock statement [Visual Basic]
- locks, threads
ms.assetid: 14501703-298f-4d43-b139-c4b6366af176
ms.openlocfilehash: 6f5a89ebe359ca2fdae1d5545192dc2dcecca6a2
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43529820"
---
# <a name="synclock-statement"></a><span data-ttu-id="7622d-102">SyncLock Deyimi</span><span class="sxs-lookup"><span data-stu-id="7622d-102">SyncLock Statement</span></span>
<span data-ttu-id="7622d-103">Bir deyim bloğunu için özel bir kilit bloğu yürütmeden önce alır.</span><span class="sxs-lookup"><span data-stu-id="7622d-103">Acquires an exclusive lock for a statement block before executing the block.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7622d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7622d-104">Syntax</span></span>  
  
```  
SyncLock lockobject  
    [ block ]  
End SyncLock  
```  
  
## <a name="parts"></a><span data-ttu-id="7622d-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="7622d-105">Parts</span></span>  
 `lockobject`  
 <span data-ttu-id="7622d-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="7622d-106">Required.</span></span> <span data-ttu-id="7622d-107">Bir nesne başvurusu için değerlendirilen bir ifade.</span><span class="sxs-lookup"><span data-stu-id="7622d-107">Expression that evaluates to an object reference.</span></span>  
  
 `block`  
 <span data-ttu-id="7622d-108">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="7622d-108">Optional.</span></span> <span data-ttu-id="7622d-109">Kilit alınıncaya sonra yürütülecek olan bir deyimler bloğunu.</span><span class="sxs-lookup"><span data-stu-id="7622d-109">Block of statements that are to execute when the lock is acquired.</span></span>  
  
 `End SyncLock`  
 <span data-ttu-id="7622d-110">Sonlandıran bir `SyncLock` blok.</span><span class="sxs-lookup"><span data-stu-id="7622d-110">Terminates a `SyncLock` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7622d-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7622d-111">Remarks</span></span>  
 <span data-ttu-id="7622d-112">`SyncLock` Bildirimi birden çok iş parçacığı deyim bloğunu aynı anda yürütmemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="7622d-112">The `SyncLock` statement ensures that multiple threads do not execute the statement block at the same time.</span></span> <span data-ttu-id="7622d-113">`SyncLock` Her iş parçacığı başka bir iş parçacığında yürütülen kadar blok girmesini engeller.</span><span class="sxs-lookup"><span data-stu-id="7622d-113">`SyncLock` prevents each thread from entering the block until no other thread is executing it.</span></span>  
  
 <span data-ttu-id="7622d-114">En yaygın kullanımı `SyncLock` birden fazla iş parçacığı tarafından aynı anda güncelleştirilmesini verilerin korunmasını sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="7622d-114">The most common use of `SyncLock` is to protect data from being updated by more than one thread simultaneously.</span></span> <span data-ttu-id="7622d-115">Verileri işlemek için ifadeleri kesintisiz tamamlanması için geçmesi gereken, bunları içine yerleştirebilirsiniz bir `SyncLock` blok.</span><span class="sxs-lookup"><span data-stu-id="7622d-115">If the statements that manipulate the data must go to completion without interruption, put them inside a `SyncLock` block.</span></span>  
  
 <span data-ttu-id="7622d-116">Özel bir kilit tarafından korunan bir deyim bloğunu adlandırılan bir *kritik bölüm*.</span><span class="sxs-lookup"><span data-stu-id="7622d-116">A statement block protected by an exclusive lock is sometimes called a *critical section*.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="7622d-117">Kurallar</span><span class="sxs-lookup"><span data-stu-id="7622d-117">Rules</span></span>  
  
-   <span data-ttu-id="7622d-118">Dal oluşturma.</span><span class="sxs-lookup"><span data-stu-id="7622d-118">Branching.</span></span> <span data-ttu-id="7622d-119">Dal oluşturamazsınız bir `SyncLock` blok dışındaysa önleyin.</span><span class="sxs-lookup"><span data-stu-id="7622d-119">You cannot branch into a `SyncLock` block from outside the block.</span></span>  
  
-   <span data-ttu-id="7622d-120">Kilit nesne değeri.</span><span class="sxs-lookup"><span data-stu-id="7622d-120">Lock Object Value.</span></span> <span data-ttu-id="7622d-121">Değerini `lockobject` olamaz `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="7622d-121">The value of `lockobject` cannot be `Nothing`.</span></span> <span data-ttu-id="7622d-122">İçinde kullanmadan önce nesnesi kilitlenemedi oluşturmalısınız bir `SyncLock` deyimi.</span><span class="sxs-lookup"><span data-stu-id="7622d-122">You must create the lock object before you use it in a `SyncLock` statement.</span></span>  
  
     <span data-ttu-id="7622d-123">Değerini değiştiremezsiniz `lockobject` yürütülürken bir `SyncLock` blok.</span><span class="sxs-lookup"><span data-stu-id="7622d-123">You cannot change the value of `lockobject` while executing a `SyncLock` block.</span></span> <span data-ttu-id="7622d-124">Mekanizması nesnesi kilitlenemedi değişmeden kalmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="7622d-124">The mechanism requires that the lock object remain unchanged.</span></span>  
  
-   <span data-ttu-id="7622d-125">Kullanamazsınız [Await](../../../visual-basic/language-reference/operators/await-operator.md) işlecinde bir `SyncLock` blok.</span><span class="sxs-lookup"><span data-stu-id="7622d-125">You can't use the [Await](../../../visual-basic/language-reference/operators/await-operator.md) operator in a `SyncLock` block.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="7622d-126">Davranış</span><span class="sxs-lookup"><span data-stu-id="7622d-126">Behavior</span></span>  
  
-   <span data-ttu-id="7622d-127">Mekanizması.</span><span class="sxs-lookup"><span data-stu-id="7622d-127">Mechanism.</span></span> <span data-ttu-id="7622d-128">Bir iş parçacığı ulaştığında `SyncLock` deyimi olarak değerlendirilir `lockobject` deyim ve ifade tarafından döndürülen nesne üzerinde özel bir kilit alması kadar yürütmeyi askıya alır.</span><span class="sxs-lookup"><span data-stu-id="7622d-128">When a thread reaches the `SyncLock` statement, it evaluates the `lockobject` expression and suspends execution until it acquires an exclusive lock on the object returned by the expression.</span></span> <span data-ttu-id="7622d-129">Başka bir iş parçacığı ulaştığında `SyncLock` deyimi, onu değil bir kilit alınması ilk iş parçacığında yürütülene kadar `End SyncLock` deyimi.</span><span class="sxs-lookup"><span data-stu-id="7622d-129">When another thread reaches the `SyncLock` statement, it does not acquire a lock until the first thread executes the `End SyncLock` statement.</span></span>  
  
-   <span data-ttu-id="7622d-130">Korunan veriler.</span><span class="sxs-lookup"><span data-stu-id="7622d-130">Protected Data.</span></span> <span data-ttu-id="7622d-131">Varsa `lockobject` olduğu bir `Shared` değişken, özel bir kilit herhangi bir sınıfın örneğini bir iş parçacığında yürütülmesini engeller `SyncLock` başka bir iş parçacığı yürütülürken engelleyin.</span><span class="sxs-lookup"><span data-stu-id="7622d-131">If `lockobject` is a `Shared` variable, the exclusive lock prevents a thread in any instance of the class from executing the `SyncLock` block while any other thread is executing it.</span></span> <span data-ttu-id="7622d-132">Bu, tüm örnekler arasında paylaşılan verileri korur.</span><span class="sxs-lookup"><span data-stu-id="7622d-132">This protects data that is shared among all the instances.</span></span>  
  
     <span data-ttu-id="7622d-133">Varsa `lockobject` bir örneği değişkenidir (değil `Shared`), kilit yürütülmesini geçerli örneğinde çalışan iş parçacığı engeller `SyncLock` başka bir iş parçacığıyla aynı örneğinde aynı anda blok.</span><span class="sxs-lookup"><span data-stu-id="7622d-133">If `lockobject` is an instance variable (not `Shared`), the lock prevents a thread running in the current instance from executing the `SyncLock` block at the same time as another thread in the same instance.</span></span> <span data-ttu-id="7622d-134">Bu, tek bir örnek tarafından tutulan verileri korur.</span><span class="sxs-lookup"><span data-stu-id="7622d-134">This protects data maintained by the individual instance.</span></span>  
  
-   <span data-ttu-id="7622d-135">Alım ve yayın.</span><span class="sxs-lookup"><span data-stu-id="7622d-135">Acquisition and Release.</span></span> <span data-ttu-id="7622d-136">A `SyncLock` blok davranacağını gibi bir `Try...Finally` oluşturma, hangi `Try` blok üzerinde özel bir kilit alması `lockobject` ve `Finally` blok yayımlar.</span><span class="sxs-lookup"><span data-stu-id="7622d-136">A `SyncLock` block behaves like a `Try...Finally` construction in which the `Try` block acquires an exclusive lock on `lockobject` and the `Finally` block releases it.</span></span> <span data-ttu-id="7622d-137">Bu nedenle, `SyncLock` blok blok çıkış ne olursa olsun kilit, yayın garanti eder.</span><span class="sxs-lookup"><span data-stu-id="7622d-137">Because of this, the `SyncLock` block guarantees release of the lock, no matter how you exit the block.</span></span> <span data-ttu-id="7622d-138">İşlenmeyen özel durum söz konusu olduğunda bile bu geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="7622d-138">This is true even in the case of an unhandled exception.</span></span>  
  
-   <span data-ttu-id="7622d-139">Framework çağırır.</span><span class="sxs-lookup"><span data-stu-id="7622d-139">Framework Calls.</span></span> <span data-ttu-id="7622d-140">`SyncLock` Blok edinme ve özel bir kilit çağırarak serbest `Enter` ve `Exit` yöntemlerinin `Monitor` sınıfını <xref:System.Threading> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="7622d-140">The `SyncLock` block acquires and releases the exclusive lock by calling the `Enter` and `Exit` methods of the `Monitor` class in the <xref:System.Threading> namespace.</span></span>  
  
## <a name="programming-practices"></a><span data-ttu-id="7622d-141">Programlama yöntemler</span><span class="sxs-lookup"><span data-stu-id="7622d-141">Programming Practices</span></span>  
 <span data-ttu-id="7622d-142">`lockobject` İfade her zaman özel olarak, sınıfın ait olduğu bir nesneye değerlendirin.</span><span class="sxs-lookup"><span data-stu-id="7622d-142">The `lockobject` expression should always evaluate to an object that belongs exclusively to your class.</span></span> <span data-ttu-id="7622d-143">Size bildirmelidir bir `Private` geçerli örneğine ait verileri korumak için nesne değişkeni veya bir `Private Shared` için tüm örnekleri ortak verileri korumak için nesne değişkeni.</span><span class="sxs-lookup"><span data-stu-id="7622d-143">You should declare a `Private` object variable to protect data belonging to the current instance, or a `Private Shared` object variable to protect data common to all instances.</span></span>  
  
 <span data-ttu-id="7622d-144">Kullanmamalısınız `Me` anahtar sözcüğü bir kilit sağlamak için nesne örneği için veri.</span><span class="sxs-lookup"><span data-stu-id="7622d-144">You should not use the `Me` keyword to provide a lock object for instance data.</span></span> <span data-ttu-id="7622d-145">Kodu sınıfınıza dış bir başvuru sınıfının bir örneği varsa, bunun için bir kilit nesnesi olarak bu başvuruyu kullanabilir bir `SyncLock` blok sizinkinden, tamamen farklı farklı veri koruma.</span><span class="sxs-lookup"><span data-stu-id="7622d-145">If code external to your class has a reference to an instance of your class, it could use that reference as a lock object for a `SyncLock` block completely different from yours, protecting different data.</span></span> <span data-ttu-id="7622d-146">Bu şekilde, sınıfınıza ve diğer sınıf birbiriyle ilgisiz kendi yürütülmesini engelleyebilecek `SyncLock` engeller.</span><span class="sxs-lookup"><span data-stu-id="7622d-146">In this way, your class and the other class could block each other from executing their unrelated `SyncLock` blocks.</span></span> <span data-ttu-id="7622d-147">Aynı kilit işlemi kullanarak aynı dize içindeki diğer kodlardan paylaşacak beri benzer şekilde bir dizesine kilitleme sorunlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="7622d-147">Similarly locking on a string can be problematic since any other code in the process using the same string will share the same lock.</span></span>  
  
 <span data-ttu-id="7622d-148">Ayrıca kullanmamalısınız `Me.GetType` yöntemi için bir kilit nesnesi sağlamak için paylaşılan veri.</span><span class="sxs-lookup"><span data-stu-id="7622d-148">You should also not use the `Me.GetType` method to provide a lock object for shared data.</span></span> <span data-ttu-id="7622d-149">Bunun nedeni, `GetType` her zaman aynı döndürür `Type` nesne için belirli bir sınıf adı.</span><span class="sxs-lookup"><span data-stu-id="7622d-149">This is because `GetType` always returns the same `Type` object for a given class name.</span></span> <span data-ttu-id="7622d-150">Dış kod arama `GetType` sınıfınızın ve kullanmakta olduğunuz aynı kilit nesnesini alın.</span><span class="sxs-lookup"><span data-stu-id="7622d-150">External code could call `GetType` on your class and obtain the same lock object you are using.</span></span> <span data-ttu-id="7622d-151">Bu iki sınıf birbirinden engelleme neden olur, `SyncLock` engeller.</span><span class="sxs-lookup"><span data-stu-id="7622d-151">This would result in the two classes blocking each other from their `SyncLock` blocks.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="7622d-152">Örnekler</span><span class="sxs-lookup"><span data-stu-id="7622d-152">Examples</span></span>  
  
### <a name="description"></a><span data-ttu-id="7622d-153">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7622d-153">Description</span></span>  
 <span data-ttu-id="7622d-154">Aşağıdaki örnek, basit bir iletiler listesini tutar bir sınıfı gösterir.</span><span class="sxs-lookup"><span data-stu-id="7622d-154">The following example shows a class that maintains a simple list of messages.</span></span> <span data-ttu-id="7622d-155">Bir dizide iletileri tutar ve son öğe, dizinin bir değişkende kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7622d-155">It holds the messages in an array and the last used element of that array in a variable.</span></span> <span data-ttu-id="7622d-156">`addAnotherMessage` Yordam son öğeyi artırır ve yeni iletinin depolar.</span><span class="sxs-lookup"><span data-stu-id="7622d-156">The `addAnotherMessage` procedure increments the last element and stores the new message.</span></span> <span data-ttu-id="7622d-157">Bu iki işlem tarafından korunan `SyncLock` ve `End SyncLock` deyimleri, çünkü son öğeyi artırıldıktan sonra başka bir iş parçacığı son öğeyi yeniden artırabilirsiniz önce yeni iletinin depolanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="7622d-157">Those two operations are protected by the `SyncLock` and `End SyncLock` statements, because once the last element has been incremented, the new message must be stored before any other thread can increment the last element again.</span></span>  
  
 <span data-ttu-id="7622d-158">Varsa `simpleMessageList` sınıfın tüm örnekleri, değişkenleri arasında iletilerinin bir listesini paylaşılan `messagesList` ve `messagesLast` olarak bildirilmesi `Shared`.</span><span class="sxs-lookup"><span data-stu-id="7622d-158">If the `simpleMessageList` class shared one list of messages among all its instances, the variables `messagesList` and `messagesLast` would be declared as `Shared`.</span></span> <span data-ttu-id="7622d-159">Bu durumda, değişken `messagesLock` ayrıca olmalıdır `Shared`, her örnek için kullanılan tek kilit nesnesi böylece olacaktır.</span><span class="sxs-lookup"><span data-stu-id="7622d-159">In this case, the variable `messagesLock` should also be `Shared`, so that there would be a single lock object used by every instance.</span></span>  
  
### <a name="code"></a><span data-ttu-id="7622d-160">Kod</span><span class="sxs-lookup"><span data-stu-id="7622d-160">Code</span></span>  
 [!code-vb[VbVbalrThreading#1](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/synclock-statement_1.vb)]  
  
### <a name="description"></a><span data-ttu-id="7622d-161">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7622d-161">Description</span></span>  
 <span data-ttu-id="7622d-162">Aşağıdaki örnek, iş parçacığı kullanır ve `SyncLock`.</span><span class="sxs-lookup"><span data-stu-id="7622d-162">The following example uses threads and `SyncLock`.</span></span> <span data-ttu-id="7622d-163">Sürece `SyncLock` deyimi, deyim bloğunu kritik bir bölümdür ve `balance` hiçbir zaman negatif bir sayı olur.</span><span class="sxs-lookup"><span data-stu-id="7622d-163">As long as the `SyncLock` statement is present, the statement block is a critical section and `balance` never becomes a negative number.</span></span> <span data-ttu-id="7622d-164">Açıklama `SyncLock` ve `End SyncLock` bırakarak etkisini görmek için ifadeleri `SyncLock` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="7622d-164">You can comment out the `SyncLock` and `End SyncLock` statements to see the effect of leaving out the `SyncLock` keyword.</span></span>  
  
### <a name="code"></a><span data-ttu-id="7622d-165">Kod</span><span class="sxs-lookup"><span data-stu-id="7622d-165">Code</span></span>  
 [!code-vb[VbVbalrThreading#21](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/synclock-statement_2.vb)]  
  
### <a name="comments"></a><span data-ttu-id="7622d-166">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7622d-166">Comments</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7622d-167">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7622d-167">See Also</span></span>  
 <xref:System.Threading>  
 <xref:System.Threading.Monitor>  
 [<span data-ttu-id="7622d-168">İş Parçacığı Eşitleme</span><span class="sxs-lookup"><span data-stu-id="7622d-168">Thread Synchronization</span></span>](../../programming-guide/concepts/threading/thread-synchronization.md)  
 [<span data-ttu-id="7622d-169">İş parçacığı oluşturma</span><span class="sxs-lookup"><span data-stu-id="7622d-169">Threading</span></span>](../../programming-guide/concepts/threading/index.md)
