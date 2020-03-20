---
title: İyimser Eşzamanlılık
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e380edac-da67-4276-80a5-b64decae4947
ms.openlocfilehash: e8d24a3998ca97fdf45e647bc40c1f7d6018ec20
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149459"
---
# <a name="optimistic-concurrency"></a><span data-ttu-id="8fc39-102">İyimser Eşzamanlılık</span><span class="sxs-lookup"><span data-stu-id="8fc39-102">Optimistic Concurrency</span></span>
<span data-ttu-id="8fc39-103">Çok kullanıcılı bir ortamda, veritabanındaki verileri güncelleştirmek için iki model vardır: iyimser eşzamanlılık ve kötümser eşzamanlılık.</span><span class="sxs-lookup"><span data-stu-id="8fc39-103">In a multiuser environment, there are two models for updating data in a database: optimistic concurrency and pessimistic concurrency.</span></span> <span data-ttu-id="8fc39-104">Nesne, <xref:System.Data.DataSet> verileri remoting ve verilerle etkileşim gibi uzun süren etkinlikler için iyimser eşzamanlılık kullanımını teşvik etmek üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="8fc39-104">The <xref:System.Data.DataSet> object is designed to encourage the use of optimistic concurrency for long-running activities, such as remoting data and interacting with data.</span></span>  
  
 <span data-ttu-id="8fc39-105">Kötümser eşzamanlılık, diğer kullanıcıların verileri geçerli kullanıcıyı etkileyecek şekilde değiştirmesini önlemek için veri kaynağındaki satırları kilitlemeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="8fc39-105">Pessimistic concurrency involves locking rows at the data source to prevent other users from modifying data in a way that affects the current user.</span></span> <span data-ttu-id="8fc39-106">Kötümser bir modelde, bir kullanıcı kilidin uygulanmasına neden olan bir eylem gerçekleştirdiğinde, diğer kullanıcılar kilit sahibi onu serbest bırakana kadar kilitle çakışacak eylemleri gerçekleştiremez.</span><span class="sxs-lookup"><span data-stu-id="8fc39-106">In a pessimistic model, when a user performs an action that causes a lock to be applied, other users cannot perform actions that would conflict with the lock until the lock owner releases it.</span></span> <span data-ttu-id="8fc39-107">Bu model, öncelikle veriler için ağır çekişmelerin olduğu ortamlarda kullanılır, böylece eşzamanlılık çakışmaları meydana geldiğinde verileri kilitlerle koruma nın maliyeti hareketleri geri alma maliyetinden daha az olur.</span><span class="sxs-lookup"><span data-stu-id="8fc39-107">This model is primarily used in environments where there is heavy contention for data, so that the cost of protecting data with locks is less than the cost of rolling back transactions if concurrency conflicts occur.</span></span>  
  
 <span data-ttu-id="8fc39-108">Bu nedenle, kötümser bir eşzamanlılık modelinde, bir satırı güncelleyen bir kullanıcı kilit oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8fc39-108">Therefore, in a pessimistic concurrency model, a user who updates a row establishes a lock.</span></span> <span data-ttu-id="8fc39-109">Kullanıcı güncelleştirmeyi bitirip kilidi yayımlayana kadar, başka hiç kimse bu satırı değiştiremez.</span><span class="sxs-lookup"><span data-stu-id="8fc39-109">Until the user has finished the update and released the lock, no one else can change that row.</span></span> <span data-ttu-id="8fc39-110">Bu nedenle, kötümser eşzamanlılık en iyi kilit süreleri kısa olacak, kayıtların programlı işleme olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="8fc39-110">For this reason, pessimistic concurrency is best implemented when lock times will be short, as in programmatic processing of records.</span></span> <span data-ttu-id="8fc39-111">Kötümser eşzamanlılık, kullanıcılar verilerle etkileşimde yken ve kayıtların nispeten büyük bir süre için kilitlenmelerine neden olduğunda ölçeklenebilir bir seçenek değildir.</span><span class="sxs-lookup"><span data-stu-id="8fc39-111">Pessimistic concurrency is not a scalable option when users are interacting with data and causing records to be locked for relatively large periods of time.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8fc39-112">Aynı işlemde birden çok satırı güncelleştirmeniz gerekiyorsa, işlem oluşturmak kötümser kilitleme kullanmaktan daha ölçeklenebilir bir seçenektir.</span><span class="sxs-lookup"><span data-stu-id="8fc39-112">If you need to update multiple rows in the same operation, then creating a transaction is a more scalable option than using pessimistic locking.</span></span>  
  
 <span data-ttu-id="8fc39-113">Bunun aksine, iyimser eşzamanlılık kullanan kullanıcılar okurken bir satırı kilitlemez.</span><span class="sxs-lookup"><span data-stu-id="8fc39-113">By contrast, users who use optimistic concurrency do not lock a row when reading it.</span></span> <span data-ttu-id="8fc39-114">Bir kullanıcı bir satırı güncelleştirmek istediğinde, uygulamanın okunduğundan beri başka bir kullanıcının satırı değiştirip değiştirmediğini belirlemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="8fc39-114">When a user wants to update a row, the application must determine whether another user has changed the row since it was read.</span></span> <span data-ttu-id="8fc39-115">İyimser eşzamanlılık genellikle veri için düşük çekişmeli ortamlarda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8fc39-115">Optimistic concurrency is generally used in environments with a low contention for data.</span></span> <span data-ttu-id="8fc39-116">İyimser eşzamanlılık, kayıtların kilitlenmesi gerekmedığından ve kayıtların kilitlemesi ek sunucu kaynakları gerektirdiğinden performansı artırır.</span><span class="sxs-lookup"><span data-stu-id="8fc39-116">Optimistic concurrency improves performance because no locking of records is required, and locking of records requires additional server resources.</span></span> <span data-ttu-id="8fc39-117">Ayrıca, kayıt kilitlerini korumak için veritabanı sunucusuna kalıcı bir bağlantı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="8fc39-117">Also, in order to maintain record locks, a persistent connection to the database server is required.</span></span> <span data-ttu-id="8fc39-118">İyimser bir eşzamanlılık modelinde durum böyle olmadığından, sunucuya bağlantılar daha kısa sürede daha fazla sayıda istemciye hizmet vermekte serbesttir.</span><span class="sxs-lookup"><span data-stu-id="8fc39-118">Because this is not the case in an optimistic concurrency model, connections to the server are free to serve a larger number of clients in less time.</span></span>  
  
 <span data-ttu-id="8fc39-119">İyimser bir eşzamanlılık modelinde, bir kullanıcı veritabanından bir değer aldıktan sonra, ilk kullanıcı onu değiştirmeye çalıştıönce değeri değiştirirse, bir ihlal meydana gelmiş olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="8fc39-119">In an optimistic concurrency model, a violation is considered to have occurred if, after a user receives a value from the database, another user modifies the value before the first user has attempted to modify it.</span></span> <span data-ttu-id="8fc39-120">Sunucunun eşzamanlılık ihlalini nasıl çözeceği en iyi şekilde ilk olarak aşağıdaki örnek açıklanır.</span><span class="sxs-lookup"><span data-stu-id="8fc39-120">How the server resolves a concurrency violation is best shown by first describing the following example.</span></span>  
  
 <span data-ttu-id="8fc39-121">Aşağıdaki tablolar iyimser eşzamanlılık bir örnek izleyin.</span><span class="sxs-lookup"><span data-stu-id="8fc39-121">The following tables follow an example of optimistic concurrency.</span></span>  
  
 <span data-ttu-id="8fc39-122">Saat 13:00'te User1 veritabanından aşağıdaki değerlerle bir satır okur:</span><span class="sxs-lookup"><span data-stu-id="8fc39-122">At 1:00 p.m., User1 reads a row from the database with the following values:</span></span>  
  
 <span data-ttu-id="8fc39-123">**CustID Soyadı Ad soyad**</span><span class="sxs-lookup"><span data-stu-id="8fc39-123">**CustID     LastName     FirstName**</span></span>  
  
 <span data-ttu-id="8fc39-124">101 Smith Bob</span><span class="sxs-lookup"><span data-stu-id="8fc39-124">101          Smith             Bob</span></span>  
  
|<span data-ttu-id="8fc39-125">Sütun adı</span><span class="sxs-lookup"><span data-stu-id="8fc39-125">Column name</span></span>|<span data-ttu-id="8fc39-126">Orijinal değer</span><span class="sxs-lookup"><span data-stu-id="8fc39-126">Original value</span></span>|<span data-ttu-id="8fc39-127">Geçerli değer</span><span class="sxs-lookup"><span data-stu-id="8fc39-127">Current value</span></span>|<span data-ttu-id="8fc39-128">Veritabanındaki değer</span><span class="sxs-lookup"><span data-stu-id="8fc39-128">Value in database</span></span>|  
|-----------------|--------------------|-------------------|-----------------------|  
|<span data-ttu-id="8fc39-129">CustID</span><span class="sxs-lookup"><span data-stu-id="8fc39-129">CustID</span></span>|<span data-ttu-id="8fc39-130">101</span><span class="sxs-lookup"><span data-stu-id="8fc39-130">101</span></span>|<span data-ttu-id="8fc39-131">101</span><span class="sxs-lookup"><span data-stu-id="8fc39-131">101</span></span>|<span data-ttu-id="8fc39-132">101</span><span class="sxs-lookup"><span data-stu-id="8fc39-132">101</span></span>|  
|<span data-ttu-id="8fc39-133">LastName</span><span class="sxs-lookup"><span data-stu-id="8fc39-133">LastName</span></span>|<span data-ttu-id="8fc39-134">Smith</span><span class="sxs-lookup"><span data-stu-id="8fc39-134">Smith</span></span>|<span data-ttu-id="8fc39-135">Smith</span><span class="sxs-lookup"><span data-stu-id="8fc39-135">Smith</span></span>|<span data-ttu-id="8fc39-136">Smith</span><span class="sxs-lookup"><span data-stu-id="8fc39-136">Smith</span></span>|  
|<span data-ttu-id="8fc39-137">FirstName</span><span class="sxs-lookup"><span data-stu-id="8fc39-137">FirstName</span></span>|<span data-ttu-id="8fc39-138">Bob</span><span class="sxs-lookup"><span data-stu-id="8fc39-138">Bob</span></span>|<span data-ttu-id="8fc39-139">Bob</span><span class="sxs-lookup"><span data-stu-id="8fc39-139">Bob</span></span>|<span data-ttu-id="8fc39-140">Bob</span><span class="sxs-lookup"><span data-stu-id="8fc39-140">Bob</span></span>|  
  
 <span data-ttu-id="8fc39-141">Saat 13:01'de User2 aynı satırı okur.</span><span class="sxs-lookup"><span data-stu-id="8fc39-141">At 1:01 p.m., User2 reads the same row.</span></span>  
  
 <span data-ttu-id="8fc39-142">Saat 13:03'te **User2, FirstName'i** "Bob"dan "Robert" olarak değiştirir ve veritabanını güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="8fc39-142">At 1:03 p.m., User2 changes **FirstName** from "Bob" to "Robert" and updates the database.</span></span>  
  
|<span data-ttu-id="8fc39-143">Sütun adı</span><span class="sxs-lookup"><span data-stu-id="8fc39-143">Column name</span></span>|<span data-ttu-id="8fc39-144">Orijinal değer</span><span class="sxs-lookup"><span data-stu-id="8fc39-144">Original value</span></span>|<span data-ttu-id="8fc39-145">Geçerli değer</span><span class="sxs-lookup"><span data-stu-id="8fc39-145">Current value</span></span>|<span data-ttu-id="8fc39-146">Veritabanındaki değer</span><span class="sxs-lookup"><span data-stu-id="8fc39-146">Value in database</span></span>|  
|-----------------|--------------------|-------------------|-----------------------|  
|<span data-ttu-id="8fc39-147">CustID</span><span class="sxs-lookup"><span data-stu-id="8fc39-147">CustID</span></span>|<span data-ttu-id="8fc39-148">101</span><span class="sxs-lookup"><span data-stu-id="8fc39-148">101</span></span>|<span data-ttu-id="8fc39-149">101</span><span class="sxs-lookup"><span data-stu-id="8fc39-149">101</span></span>|<span data-ttu-id="8fc39-150">101</span><span class="sxs-lookup"><span data-stu-id="8fc39-150">101</span></span>|  
|<span data-ttu-id="8fc39-151">LastName</span><span class="sxs-lookup"><span data-stu-id="8fc39-151">LastName</span></span>|<span data-ttu-id="8fc39-152">Smith</span><span class="sxs-lookup"><span data-stu-id="8fc39-152">Smith</span></span>|<span data-ttu-id="8fc39-153">Smith</span><span class="sxs-lookup"><span data-stu-id="8fc39-153">Smith</span></span>|<span data-ttu-id="8fc39-154">Smith</span><span class="sxs-lookup"><span data-stu-id="8fc39-154">Smith</span></span>|  
|<span data-ttu-id="8fc39-155">FirstName</span><span class="sxs-lookup"><span data-stu-id="8fc39-155">FirstName</span></span>|<span data-ttu-id="8fc39-156">Bob</span><span class="sxs-lookup"><span data-stu-id="8fc39-156">Bob</span></span>|<span data-ttu-id="8fc39-157">Robert</span><span class="sxs-lookup"><span data-stu-id="8fc39-157">Robert</span></span>|<span data-ttu-id="8fc39-158">Bob</span><span class="sxs-lookup"><span data-stu-id="8fc39-158">Bob</span></span>|  
  
 <span data-ttu-id="8fc39-159">Güncelleştirme sırasında veritabanındaki değerler User2'nin sahip olduğu özgün değerlerle eşleştirdiği için güncelleştirme başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="8fc39-159">The update succeeds because the values in the database at the time of update match the original values that User2 has.</span></span>  
  
 <span data-ttu-id="8fc39-160">Saat 13:05'te User1, "Bob"un ilk adını "James" olarak değiştirir ve satırı güncelleştirmeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="8fc39-160">At 1:05 p.m., User1 changes "Bob"'s first name to "James" and tries to update the row.</span></span>  
  
|<span data-ttu-id="8fc39-161">Sütun adı</span><span class="sxs-lookup"><span data-stu-id="8fc39-161">Column name</span></span>|<span data-ttu-id="8fc39-162">Orijinal değer</span><span class="sxs-lookup"><span data-stu-id="8fc39-162">Original value</span></span>|<span data-ttu-id="8fc39-163">Geçerli değer</span><span class="sxs-lookup"><span data-stu-id="8fc39-163">Current value</span></span>|<span data-ttu-id="8fc39-164">Veritabanındaki değer</span><span class="sxs-lookup"><span data-stu-id="8fc39-164">Value in database</span></span>|  
|-----------------|--------------------|-------------------|-----------------------|  
|<span data-ttu-id="8fc39-165">CustID</span><span class="sxs-lookup"><span data-stu-id="8fc39-165">CustID</span></span>|<span data-ttu-id="8fc39-166">101</span><span class="sxs-lookup"><span data-stu-id="8fc39-166">101</span></span>|<span data-ttu-id="8fc39-167">101</span><span class="sxs-lookup"><span data-stu-id="8fc39-167">101</span></span>|<span data-ttu-id="8fc39-168">101</span><span class="sxs-lookup"><span data-stu-id="8fc39-168">101</span></span>|  
|<span data-ttu-id="8fc39-169">LastName</span><span class="sxs-lookup"><span data-stu-id="8fc39-169">LastName</span></span>|<span data-ttu-id="8fc39-170">Smith</span><span class="sxs-lookup"><span data-stu-id="8fc39-170">Smith</span></span>|<span data-ttu-id="8fc39-171">Smith</span><span class="sxs-lookup"><span data-stu-id="8fc39-171">Smith</span></span>|<span data-ttu-id="8fc39-172">Smith</span><span class="sxs-lookup"><span data-stu-id="8fc39-172">Smith</span></span>|  
|<span data-ttu-id="8fc39-173">FirstName</span><span class="sxs-lookup"><span data-stu-id="8fc39-173">FirstName</span></span>|<span data-ttu-id="8fc39-174">Bob</span><span class="sxs-lookup"><span data-stu-id="8fc39-174">Bob</span></span>|<span data-ttu-id="8fc39-175">James</span><span class="sxs-lookup"><span data-stu-id="8fc39-175">James</span></span>|<span data-ttu-id="8fc39-176">Robert</span><span class="sxs-lookup"><span data-stu-id="8fc39-176">Robert</span></span>|  
  
 <span data-ttu-id="8fc39-177">Bu noktada, Kullanıcı1 iyimser bir eşzamanlılık ihlaliyle karşılaşır, çünkü veritabanındaki değer ("Robert") artık User1'in beklediği orijinal değerle ("Bob") eşleşemez.</span><span class="sxs-lookup"><span data-stu-id="8fc39-177">At this point, User1 encounters an optimistic concurrency violation because the value in the database ("Robert") no longer matches the original value that User1 was expecting ("Bob").</span></span> <span data-ttu-id="8fc39-178">Eşzamanlılık ihlali yalnızca güncelleştirmenin başarısız olduğunu bilmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="8fc39-178">The concurrency violation simply lets you know that the update failed.</span></span> <span data-ttu-id="8fc39-179">Kullanıcı1 tarafından sağlanan değişikliklerle User2 tarafından sağlanan değişikliklerin üzerine yazımının veya Kullanıcı1 tarafından yapılan değişikliklerin iptal edilmesine karar verilmesi gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="8fc39-179">The decision now needs to be made whether to overwrite the changes supplied by User2 with the changes supplied by User1, or to cancel the changes by User1.</span></span>  
  
## <a name="testing-for-optimistic-concurrency-violations"></a><span data-ttu-id="8fc39-180">İyimser Eşzamanlılık İhlalleri Için Test</span><span class="sxs-lookup"><span data-stu-id="8fc39-180">Testing for Optimistic Concurrency Violations</span></span>  
 <span data-ttu-id="8fc39-181">İyimser bir eşzamanlılık ihlali için test etmek için çeşitli teknikler vardır.</span><span class="sxs-lookup"><span data-stu-id="8fc39-181">There are several techniques for testing for an optimistic concurrency violation.</span></span> <span data-ttu-id="8fc39-182">Bir tabloda bir zaman damgası sütun dahil içerir.</span><span class="sxs-lookup"><span data-stu-id="8fc39-182">One involves including a timestamp column in the table.</span></span> <span data-ttu-id="8fc39-183">Veritabanları genellikle kaydın en son güncelleştirildiğinde tarih ve saati tanımlamak için kullanılabilecek zaman damgası işlevselliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="8fc39-183">Databases commonly provide timestamp functionality that can be used to identify the date and time when the record was last updated.</span></span> <span data-ttu-id="8fc39-184">Bu teknik kullanılarak, tablo tanımına bir zaman damgası sütunu eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="8fc39-184">Using this technique, a timestamp column is included in the table definition.</span></span> <span data-ttu-id="8fc39-185">Kayıt güncelleştirildiğinde, zaman damgası geçerli tarih ve saati yansıtacak şekilde güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="8fc39-185">Whenever the record is updated, the timestamp is updated to reflect the current date and time.</span></span> <span data-ttu-id="8fc39-186">İyimser eşzamanlılık ihlalleri için yapılan bir testte, zaman damgası sütunu tablonun içeriğinin sorgusuyla birlikte döndürülür.</span><span class="sxs-lookup"><span data-stu-id="8fc39-186">In a test for optimistic concurrency violations, the timestamp column is returned with any query of the contents of the table.</span></span> <span data-ttu-id="8fc39-187">Bir güncelleştirme denendiğinde, veritabanındaki zaman damgası değeri değiştirilen satırda bulunan özgün zaman damgası değeriyle karşılaştırılır.</span><span class="sxs-lookup"><span data-stu-id="8fc39-187">When an update is attempted, the timestamp value in the database is compared to the original timestamp value contained in the modified row.</span></span> <span data-ttu-id="8fc39-188">Eşleşirlerse, güncelleştirme gerçekleştirilir ve zaman damgası sütunu güncelleştirmeyi yansıtacak geçerli saatle güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="8fc39-188">If they match, the update is performed and the timestamp column is updated with the current time to reflect the update.</span></span> <span data-ttu-id="8fc39-189">Eşleşmezlerse, iyimser bir eşzamanlılık ihlali meydana geldi.</span><span class="sxs-lookup"><span data-stu-id="8fc39-189">If they do not match, an optimistic concurrency violation has occurred.</span></span>  
  
 <span data-ttu-id="8fc39-190">İyimser bir eşzamanlılık ihlalini test etmek için başka bir teknik, bir satırdaki tüm özgün sütun değerlerinin hala veritabanında bulunanlarla eşleşindiğini doğrulamaktır.</span><span class="sxs-lookup"><span data-stu-id="8fc39-190">Another technique for testing for an optimistic concurrency violation is to verify that all the original column values in a row still match those found in the database.</span></span> <span data-ttu-id="8fc39-191">Örneğin, aşağıdaki sorguyu göz önüne alın:</span><span class="sxs-lookup"><span data-stu-id="8fc39-191">For example, consider the following query:</span></span>  
  
```sql
SELECT Col1, Col2, Col3 FROM Table1  
```  
  
 <span data-ttu-id="8fc39-192">**Tablo1'deki**bir satırı güncellerken iyimser bir eşzamanlılık ihlalini test etmek için aşağıdaki UPDATE deyimini yayınlayayım:</span><span class="sxs-lookup"><span data-stu-id="8fc39-192">To test for an optimistic concurrency violation when updating a row in **Table1**, you would issue the following UPDATE statement:</span></span>  
  
```sql
UPDATE Table1 Set Col1 = @NewCol1Value,  
              Set Col2 = @NewCol2Value,  
              Set Col3 = @NewCol3Value  
WHERE Col1 = @OldCol1Value AND  
      Col2 = @OldCol2Value AND  
      Col3 = @OldCol3Value  
```  
  
 <span data-ttu-id="8fc39-193">Özgün değerler veritabanındaki değerlerle eşleşince güncelleştirme gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="8fc39-193">As long as the original values match the values in the database, the update is performed.</span></span> <span data-ttu-id="8fc39-194">Bir değer değiştirildiyse, WHERE yan tümcesi eşleşme bulmayacağı için güncelleştirme satırı değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="8fc39-194">If a value has been modified, the update will not modify the row because the WHERE clause will not find a match.</span></span>  
  
 <span data-ttu-id="8fc39-195">Sorgunuzda her zaman benzersiz bir birincil anahtar değeri döndürmeniz in tavsiye edilir.</span><span class="sxs-lookup"><span data-stu-id="8fc39-195">Note that it is recommended to always return a unique primary key value in your query.</span></span> <span data-ttu-id="8fc39-196">Aksi takdirde, önceki UPDATE deyimi birden fazla satırı güncelleyebilir ve bu da amacınız olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="8fc39-196">Otherwise, the preceding UPDATE statement may update more than one row, which might not be your intent.</span></span>  
  
 <span data-ttu-id="8fc39-197">Veri kaynağınızdaki bir sütun nulls'a izin veriyorsa, yerel tablonuzda ve veri kaynağınızda eşleşen bir null başvurusu denetlemek için WHERE yan tümcenizi genişletmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="8fc39-197">If a column at your data source allows nulls, you may need to extend your WHERE clause to check for a matching null reference in your local table and at the data source.</span></span> <span data-ttu-id="8fc39-198">Örneğin, aşağıdaki UPDATE deyimi, yerel satırdaki null bir başvurunun hala veri kaynağındaki null başvurusuyla eşleştiğini veya yerel satırdaki değerin veri kaynağındaki değerle eşleşmesini doğrular.</span><span class="sxs-lookup"><span data-stu-id="8fc39-198">For example, the following UPDATE statement verifies that a null reference in the local row still matches a null reference at the data source, or that the value in the local row still matches the value at the data source.</span></span>  
  
```sql
UPDATE Table1 Set Col1 = @NewVal1  
  WHERE (@OldVal1 IS NULL AND Col1 IS NULL) OR Col1 = @OldVal1  
```  
  
 <span data-ttu-id="8fc39-199">Ayrıca, iyimser bir eşzamanlılık modeli kullanırken daha az kısıtlayıcı ölçütuygulamayı da seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8fc39-199">You may also choose to apply less restrictive criteria when using an optimistic concurrency model.</span></span> <span data-ttu-id="8fc39-200">Örneğin, WHERE yan tümcesi'ndeki yalnızca birincil anahtar sütunlarını kullanmak, diğer sütunların son sorgudan beri güncelleştirilip güncelleştirilmediğine bakılmaksızın verilerin üzerine yazılmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="8fc39-200">For example, using only the primary key columns in the WHERE clause causes the data to be overwritten regardless of whether the other columns have been updated since the last query.</span></span> <span data-ttu-id="8fc39-201">Ayrıca, belirli alanlar son sorgulandıktan sonra güncelleştirilmedikçe verilerin üzerine yazılmasıyla sonuçlanan bir WHERE yan tümcesi yalnızca belirli sütunlara da uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8fc39-201">You can also apply a WHERE clause only to specific columns, resulting in data being overwritten unless particular fields have been updated since they were last queried.</span></span>  
  
### <a name="the-dataadapterrowupdated-event"></a><span data-ttu-id="8fc39-202">DataAdapter.RowUpdated Olay</span><span class="sxs-lookup"><span data-stu-id="8fc39-202">The DataAdapter.RowUpdated Event</span></span>  
 <span data-ttu-id="8fc39-203">Nesnenin <xref:System.Data.Common.DataAdapter> **RowUpdated** olayı, iyimser eşzamanlılık ihlalleri uygulamanıza bildirim sağlamak için daha önce açıklanan tekniklerle birlikte kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8fc39-203">The **RowUpdated** event of the <xref:System.Data.Common.DataAdapter> object can be used in conjunction with the techniques described earlier, to provide notification to your application of optimistic concurrency violations.</span></span> <span data-ttu-id="8fc39-204">**RowUpdate,** **Bir DataSet'ten** **Değiştirilen** satırı güncelleştirmeye yönelik her denemeden sonra oluşur.</span><span class="sxs-lookup"><span data-stu-id="8fc39-204">**RowUpdated** occurs after each attempt to update a **Modified** row from a **DataSet**.</span></span> <span data-ttu-id="8fc39-205">Bu, özel hata bilgileri ekleme, yeniden deneme mantığı ekleme ve benzeri özel hata bilgileri ekleme gibi özel işleme kodu eklemenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="8fc39-205">This enables you to add special handling code, including processing when an exception occurs, adding custom error information, adding retry logic, and so on.</span></span> <span data-ttu-id="8fc39-206">Nesne, <xref:System.Data.Common.RowUpdatedEventArgs> tablodaki değiştirilmiş bir satır için belirli bir güncelleştirme komutundan etkilenen satır sayısını içeren **RecordsAffected** özelliğini döndürür.</span><span class="sxs-lookup"><span data-stu-id="8fc39-206">The <xref:System.Data.Common.RowUpdatedEventArgs> object returns a **RecordsAffected** property containing the number of rows affected by a particular update command for a modified row in a table.</span></span> <span data-ttu-id="8fc39-207">İyimser eşzamanlılık için güncelleştirme komutunu ayarlayarak, **RecordsAffected** özelliği, sonuç olarak, iyimser bir eşzamanlılık ihlali oluştuğunda, hiçbir kayıt güncelleştirildiğinden 0 değerini döndürecektir.</span><span class="sxs-lookup"><span data-stu-id="8fc39-207">By setting the update command to test for optimistic concurrency, the **RecordsAffected** property will, as a result, return a value of 0 when an optimistic concurrency violation has occurred, because no records were updated.</span></span> <span data-ttu-id="8fc39-208">Bu durumda, bir özel durum atılır.</span><span class="sxs-lookup"><span data-stu-id="8fc39-208">If this is the case, an exception is thrown.</span></span> <span data-ttu-id="8fc39-209">**RowUpdate** olayı, **updatestatus.SkipCurrentRow**gibi uygun bir **RowUpdateEventArgs.Status** değeri ayarlayarak bu oluşumu işlemek ve özel durum önlemek sağlar.</span><span class="sxs-lookup"><span data-stu-id="8fc39-209">The **RowUpdated** event enables you to handle this occurrence and avoid the exception by setting an appropriate **RowUpdatedEventArgs.Status** value, such as **UpdateStatus.SkipCurrentRow**.</span></span> <span data-ttu-id="8fc39-210">**RowUpdated** olayı hakkında daha fazla bilgi için [DataAdapter Olaylarını işleme](handling-dataadapter-events.md)konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="8fc39-210">For more information about the **RowUpdated** event, see [Handling DataAdapter Events](handling-dataadapter-events.md).</span></span>  
  
 <span data-ttu-id="8fc39-211">İsteğe bağlı olarak, Update'i aramadan önce **DataAdapter.ContinueUpdateOnError'ı** **doğru**olarak ayarlayabilir ve **Güncelleştirme**tamamlandığında **Update** belirli bir satırın **RowError** özelliğinde depolanan hata bilgilerine yanıt verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8fc39-211">Optionally, you can set **DataAdapter.ContinueUpdateOnError** to **true**, before calling **Update**, and respond to the error information stored in the **RowError** property of a particular row when the **Update** is completed.</span></span> <span data-ttu-id="8fc39-212">Daha fazla bilgi için [Satır Hata Bilgileri'ne](./dataset-datatable-dataview/row-error-information.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="8fc39-212">For more information, see [Row Error Information](./dataset-datatable-dataview/row-error-information.md).</span></span>  
  
## <a name="optimistic-concurrency-example"></a><span data-ttu-id="8fc39-213">İyimser Eşzamanlılık Örneği</span><span class="sxs-lookup"><span data-stu-id="8fc39-213">Optimistic Concurrency Example</span></span>  
 <span data-ttu-id="8fc39-214">Aşağıda, bir **DataAdapter'ın** **UpdateCommand'ını** iyimser eşzamanlılık için test etmek üzere ayarlayan ve daha sonra iyimser eşzamanlılık ihlallerini sınamak için **RowUpdate** olayını kullanan basit bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="8fc39-214">The following is a simple example that sets the **UpdateCommand** of a **DataAdapter** to test for optimistic concurrency, and then uses the **RowUpdated** event to test for optimistic concurrency violations.</span></span> <span data-ttu-id="8fc39-215">İyimser bir eşzamanlılık ihlaliyle karşılaşıldığında, uygulama güncelleştirmenin iyimser bir eşzamanlılık ihlalini yansıtacak şekilde verildiği satırın **Satır Hatasını** ayarlar.</span><span class="sxs-lookup"><span data-stu-id="8fc39-215">When an optimistic concurrency violation is encountered, the application sets the **RowError** of the row that the update was issued for to reflect an optimistic concurrency violation.</span></span>  
  
 <span data-ttu-id="8fc39-216">UPDATE komutunun WHERE yan tümcesine geçirilen parametre değerlerinin ilgili sütunlarının **Özgün** değerlerine eşlendiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="8fc39-216">Note that the parameter values passed to the WHERE clause of the UPDATE command are mapped to the **Original** values of their respective columns.</span></span>  
  
```vb  
' Assumes connection is a valid SqlConnection.  
Dim adapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT CustomerID, CompanyName FROM Customers ORDER BY CustomerID", _  
  connection)  
  
' The Update command checks for optimistic concurrency violations  
' in the WHERE clause.  
adapter.UpdateCommand = New SqlCommand("UPDATE Customers " &  
  "(CustomerID, CompanyName) VALUES(@CustomerID, @CompanyName) " & _  
  "WHERE CustomerID = @oldCustomerID AND CompanyName = " &  
  "@oldCompanyName", connection)  
adapter.UpdateCommand.Parameters.Add( _  
  "@CustomerID", SqlDbType.NChar, 5, "CustomerID")  
adapter.UpdateCommand.Parameters.Add( _  
  "@CompanyName", SqlDbType.NVarChar, 30, "CompanyName")  
  
' Pass the original values to the WHERE clause parameters.  
Dim parameter As SqlParameter = adapter.UpdateCommand.Parameters.Add( _  
  "@oldCustomerID", SqlDbType.NChar, 5, "CustomerID")  
parameter.SourceVersion = DataRowVersion.Original  
parameter = adapter.UpdateCommand.Parameters.Add( _  
  "@oldCompanyName", SqlDbType.NVarChar, 30, "CompanyName")  
parameter.SourceVersion = DataRowVersion.Original  
  
' Add the RowUpdated event handler.  
AddHandler adapter.RowUpdated, New SqlRowUpdatedEventHandler( _  
  AddressOf OnRowUpdated)  
  
Dim dataSet As DataSet = New DataSet()  
adapter.Fill(dataSet, "Customers")  
  
' Modify the DataSet contents.  
adapter.Update(dataSet, "Customers")  
  
Dim dataRow As DataRow  
  
For Each dataRow In dataSet.Tables("Customers").Rows  
    If dataRow.HasErrors Then
       Console.WriteLine(dataRow (0) & vbCrLf & dataRow.RowError)  
    End If  
Next  
  
Private Shared Sub OnRowUpdated( _  
  sender As object, args As SqlRowUpdatedEventArgs)  
   If args.RecordsAffected = 0  
      args.Row.RowError = "Optimistic Concurrency Violation!"  
      args.Status = UpdateStatus.SkipCurrentRow  
   End If  
End Sub  
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
SqlDataAdapter adapter = new SqlDataAdapter(  
  "SELECT CustomerID, CompanyName FROM Customers ORDER BY CustomerID",  
  connection);  
  
// The Update command checks for optimistic concurrency violations  
// in the WHERE clause.  
adapter.UpdateCommand = new SqlCommand("UPDATE Customers Set CustomerID = @CustomerID, CompanyName = @CompanyName " +  
   "WHERE CustomerID = @oldCustomerID AND CompanyName = @oldCompanyName", connection);  
adapter.UpdateCommand.Parameters.Add(  
  "@CustomerID", SqlDbType.NChar, 5, "CustomerID");  
adapter.UpdateCommand.Parameters.Add(  
  "@CompanyName", SqlDbType.NVarChar, 30, "CompanyName");  
  
// Pass the original values to the WHERE clause parameters.  
SqlParameter parameter = adapter.UpdateCommand.Parameters.Add(  
  "@oldCustomerID", SqlDbType.NChar, 5, "CustomerID");  
parameter.SourceVersion = DataRowVersion.Original;  
parameter = adapter.UpdateCommand.Parameters.Add(  
  "@oldCompanyName", SqlDbType.NVarChar, 30, "CompanyName");  
parameter.SourceVersion = DataRowVersion.Original;  
  
// Add the RowUpdated event handler.  
adapter.RowUpdated += new SqlRowUpdatedEventHandler(OnRowUpdated);  
  
DataSet dataSet = new DataSet();  
adapter.Fill(dataSet, "Customers");  
  
// Modify the DataSet contents.  
  
adapter.Update(dataSet, "Customers");  
  
foreach (DataRow dataRow in dataSet.Tables["Customers"].Rows)  
{  
    if (dataRow.HasErrors)  
       Console.WriteLine(dataRow [0] + "\n" + dataRow.RowError);  
}  
  
protected static void OnRowUpdated(object sender, SqlRowUpdatedEventArgs args)  
{  
  if (args.RecordsAffected == 0)
  {  
    args.Row.RowError = "Optimistic Concurrency Violation Encountered";  
    args.Status = UpdateStatus.SkipCurrentRow;  
  }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="8fc39-217">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8fc39-217">See also</span></span>

- [<span data-ttu-id="8fc39-218">ADO.NET’te Veri Alma ve Değiştirme</span><span class="sxs-lookup"><span data-stu-id="8fc39-218">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
- [<span data-ttu-id="8fc39-219">Veri Kaynaklarını DataAdapters ile Güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="8fc39-219">Updating Data Sources with DataAdapters</span></span>](updating-data-sources-with-dataadapters.md)
- [<span data-ttu-id="8fc39-220">Satır Hatası Bilgileri</span><span class="sxs-lookup"><span data-stu-id="8fc39-220">Row Error Information</span></span>](./dataset-datatable-dataview/row-error-information.md)
- [<span data-ttu-id="8fc39-221">İşlemler ve Eşzamanlılık</span><span class="sxs-lookup"><span data-stu-id="8fc39-221">Transactions and Concurrency</span></span>](transactions-and-concurrency.md)
- [<span data-ttu-id="8fc39-222">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="8fc39-222">ADO.NET Overview</span></span>](ado-net-overview.md)
