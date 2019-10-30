---
title: İyimser Eşzamanlılık
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e380edac-da67-4276-80a5-b64decae4947
ms.openlocfilehash: ddb53c9224d56803c3528d79c5ccdf5534b9ab03
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039812"
---
# <a name="optimistic-concurrency"></a><span data-ttu-id="f5dfc-102">İyimser Eşzamanlılık</span><span class="sxs-lookup"><span data-stu-id="f5dfc-102">Optimistic Concurrency</span></span>
<span data-ttu-id="f5dfc-103">Çok kullanıcılı bir ortamda, veritabanındaki verileri güncelleştirmek için iki model vardır: iyimser eşzamanlılık ve Kötümser eşzamanlılık.</span><span class="sxs-lookup"><span data-stu-id="f5dfc-103">In a multiuser environment, there are two models for updating data in a database: optimistic concurrency and pessimistic concurrency.</span></span> <span data-ttu-id="f5dfc-104"><xref:System.Data.DataSet> nesnesi, verilerin uzaktan iletişimini ve verilerle etkileşimde bulunmak gibi uzun süreli etkinlikler için iyimser eşzamanlılık kullanımını teşvik etmek üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="f5dfc-104">The <xref:System.Data.DataSet> object is designed to encourage the use of optimistic concurrency for long-running activities, such as remoting data and interacting with data.</span></span>  
  
 <span data-ttu-id="f5dfc-105">Kötümser eşzamanlılık, diğer kullanıcıların verileri geçerli kullanıcıyı etkileyecek şekilde değiştirmesini engellemek için veri kaynağındaki satırları kilitlemeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="f5dfc-105">Pessimistic concurrency involves locking rows at the data source to prevent other users from modifying data in a way that affects the current user.</span></span> <span data-ttu-id="f5dfc-106">Bir kötümser modelde, bir Kullanıcı bir kilidin uygulanmasına neden olan bir eylem gerçekleştirdiğinde, diğer kullanıcılar kilit sahibi tarafından serbest gelinceye kadar kilit ile çakışacak eylemler gerçekleştiremez.</span><span class="sxs-lookup"><span data-stu-id="f5dfc-106">In a pessimistic model, when a user performs an action that causes a lock to be applied, other users cannot perform actions that would conflict with the lock until the lock owner releases it.</span></span> <span data-ttu-id="f5dfc-107">Bu model öncelikle veriler için ağır çekişme olduğu ortamlarda kullanılır. böylece, kilitleri olan verileri koruma maliyetinin eşzamanlılık çakışmalarının oluşması durumunda işlem geri alma maliyetinden daha az olması sağlanır.</span><span class="sxs-lookup"><span data-stu-id="f5dfc-107">This model is primarily used in environments where there is heavy contention for data, so that the cost of protecting data with locks is less than the cost of rolling back transactions if concurrency conflicts occur.</span></span>  
  
 <span data-ttu-id="f5dfc-108">Bu nedenle, Kötümser eşzamanlılık modelinde bir satırı güncelleştiren bir Kullanıcı bir kilit oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f5dfc-108">Therefore, in a pessimistic concurrency model, a user who updates a row establishes a lock.</span></span> <span data-ttu-id="f5dfc-109">Kullanıcı güncelleştirmeyi tamamlayana ve kilidi serbest bırakılana kadar, başka hiç kimse bu satırı değiştiremez.</span><span class="sxs-lookup"><span data-stu-id="f5dfc-109">Until the user has finished the update and released the lock, no one else can change that row.</span></span> <span data-ttu-id="f5dfc-110">Bu nedenle, kayıt işlemleri için programlı işleme gibi kilit süreleri kısa olduğunda, Kötümser eşzamanlılık en iyi şekilde uygulanır.</span><span class="sxs-lookup"><span data-stu-id="f5dfc-110">For this reason, pessimistic concurrency is best implemented when lock times will be short, as in programmatic processing of records.</span></span> <span data-ttu-id="f5dfc-111">Kullanıcılar verilerle etkileşim kurarken ve kayıtların görece büyük süreler boyunca kilitlenmesine neden olan Kötümser eşzamanlılık, ölçeklenebilir bir seçenek değildir.</span><span class="sxs-lookup"><span data-stu-id="f5dfc-111">Pessimistic concurrency is not a scalable option when users are interacting with data and causing records to be locked for relatively large periods of time.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f5dfc-112">Aynı işlemde birden çok satırı güncelleştirmeniz gerekiyorsa, bir işlem oluşturmak, kötümser kilitlemeyi kullanmaktan daha ölçeklenebilir bir seçenektir.</span><span class="sxs-lookup"><span data-stu-id="f5dfc-112">If you need to update multiple rows in the same operation, then creating a transaction is a more scalable option than using pessimistic locking.</span></span>  
  
 <span data-ttu-id="f5dfc-113">Buna karşılık, iyimser eşzamanlılık kullanan kullanıcılar, okurken bir satırı kilitlemez.</span><span class="sxs-lookup"><span data-stu-id="f5dfc-113">By contrast, users who use optimistic concurrency do not lock a row when reading it.</span></span> <span data-ttu-id="f5dfc-114">Bir Kullanıcı bir satırı güncelleştirmek istediğinde, uygulamanın, okuduğundan bu yana başka bir kullanıcının satırı değiştirip değiştirilmediğini belirlemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="f5dfc-114">When a user wants to update a row, the application must determine whether another user has changed the row since it was read.</span></span> <span data-ttu-id="f5dfc-115">İyimser eşzamanlılık genellikle veriler için düşük çekişme olan ortamlarda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f5dfc-115">Optimistic concurrency is generally used in environments with a low contention for data.</span></span> <span data-ttu-id="f5dfc-116">Kayıt kilitleme gerekli olmadığından ve kayıt kilitlemesi ek sunucu kaynakları gerektirdiğinden iyimser eşzamanlılık performansı geliştirir.</span><span class="sxs-lookup"><span data-stu-id="f5dfc-116">Optimistic concurrency improves performance because no locking of records is required, and locking of records requires additional server resources.</span></span> <span data-ttu-id="f5dfc-117">Ayrıca, kayıt kilitlerini sürdürmek için veritabanı sunucusuna kalıcı bir bağlantı gerekir.</span><span class="sxs-lookup"><span data-stu-id="f5dfc-117">Also, in order to maintain record locks, a persistent connection to the database server is required.</span></span> <span data-ttu-id="f5dfc-118">Bu durum bir iyimser eşzamanlılık modelinde olduğu için sunucu bağlantıları, daha az sayıda istemciye daha az zaman sunmaya ücretsizdir.</span><span class="sxs-lookup"><span data-stu-id="f5dfc-118">Because this is not the case in an optimistic concurrency model, connections to the server are free to serve a larger number of clients in less time.</span></span>  
  
 <span data-ttu-id="f5dfc-119">Bir iyimser eşzamanlılık modelinde, bir kullanıcı veritabanından bir değer aldıktan sonra, ilk Kullanıcı onu değiştirmeye çalışmadan önce değeri değiştirdiğinde, bir ihlalin oluştuğu kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="f5dfc-119">In an optimistic concurrency model, a violation is considered to have occurred if, after a user receives a value from the database, another user modifies the value before the first user has attempted to modify it.</span></span> <span data-ttu-id="f5dfc-120">Sunucu bir eşzamanlılık ihlalinin nasıl çözümlendiğine göre en iyi şekilde aşağıdaki örnek açıklanarak gösterilir.</span><span class="sxs-lookup"><span data-stu-id="f5dfc-120">How the server resolves a concurrency violation is best shown by first describing the following example.</span></span>  
  
 <span data-ttu-id="f5dfc-121">Aşağıdaki tablolar, iyimser eşzamanlılık örneğini izler.</span><span class="sxs-lookup"><span data-stu-id="f5dfc-121">The following tables follow an example of optimistic concurrency.</span></span>  
  
 <span data-ttu-id="f5dfc-122">Kullanıcı1 1:00:00 ' da aşağıdaki değerlere sahip bir satırı veritabanından okur:</span><span class="sxs-lookup"><span data-stu-id="f5dfc-122">At 1:00 p.m., User1 reads a row from the database with the following values:</span></span>  
  
 <span data-ttu-id="f5dfc-123">**CustId LastName adı**</span><span class="sxs-lookup"><span data-stu-id="f5dfc-123">**CustID     LastName     FirstName**</span></span>  
  
 <span data-ttu-id="f5dfc-124">101 Smith Bob</span><span class="sxs-lookup"><span data-stu-id="f5dfc-124">101          Smith             Bob</span></span>  
  
|<span data-ttu-id="f5dfc-125">Sütun adı</span><span class="sxs-lookup"><span data-stu-id="f5dfc-125">Column name</span></span>|<span data-ttu-id="f5dfc-126">Özgün değer</span><span class="sxs-lookup"><span data-stu-id="f5dfc-126">Original value</span></span>|<span data-ttu-id="f5dfc-127">Geçerli değer</span><span class="sxs-lookup"><span data-stu-id="f5dfc-127">Current value</span></span>|<span data-ttu-id="f5dfc-128">Veritabanındaki değer</span><span class="sxs-lookup"><span data-stu-id="f5dfc-128">Value in database</span></span>|  
|-----------------|--------------------|-------------------|-----------------------|  
|<span data-ttu-id="f5dfc-129">CustId</span><span class="sxs-lookup"><span data-stu-id="f5dfc-129">CustID</span></span>|<span data-ttu-id="f5dfc-130">101</span><span class="sxs-lookup"><span data-stu-id="f5dfc-130">101</span></span>|<span data-ttu-id="f5dfc-131">101</span><span class="sxs-lookup"><span data-stu-id="f5dfc-131">101</span></span>|<span data-ttu-id="f5dfc-132">101</span><span class="sxs-lookup"><span data-stu-id="f5dfc-132">101</span></span>|  
|<span data-ttu-id="f5dfc-133">Soyadı</span><span class="sxs-lookup"><span data-stu-id="f5dfc-133">LastName</span></span>|<span data-ttu-id="f5dfc-134">Uludağ</span><span class="sxs-lookup"><span data-stu-id="f5dfc-134">Smith</span></span>|<span data-ttu-id="f5dfc-135">Uludağ</span><span class="sxs-lookup"><span data-stu-id="f5dfc-135">Smith</span></span>|<span data-ttu-id="f5dfc-136">Uludağ</span><span class="sxs-lookup"><span data-stu-id="f5dfc-136">Smith</span></span>|  
|<span data-ttu-id="f5dfc-137">firstName</span><span class="sxs-lookup"><span data-stu-id="f5dfc-137">FirstName</span></span>|<span data-ttu-id="f5dfc-138">Olduğundan</span><span class="sxs-lookup"><span data-stu-id="f5dfc-138">Bob</span></span>|<span data-ttu-id="f5dfc-139">Olduğundan</span><span class="sxs-lookup"><span data-stu-id="f5dfc-139">Bob</span></span>|<span data-ttu-id="f5dfc-140">Olduğundan</span><span class="sxs-lookup"><span data-stu-id="f5dfc-140">Bob</span></span>|  
  
 <span data-ttu-id="f5dfc-141">Kullanıcı2, 1:01:00 ' da aynı satırı okur.</span><span class="sxs-lookup"><span data-stu-id="f5dfc-141">At 1:01 p.m., User2 reads the same row.</span></span>  
  
 <span data-ttu-id="f5dfc-142">Kullanıcı2 1:03, "Bob" **iken "** Robert" olarak değiştirilir ve veritabanını günceller.</span><span class="sxs-lookup"><span data-stu-id="f5dfc-142">At 1:03 p.m., User2 changes **FirstName** from "Bob" to "Robert" and updates the database.</span></span>  
  
|<span data-ttu-id="f5dfc-143">Sütun adı</span><span class="sxs-lookup"><span data-stu-id="f5dfc-143">Column name</span></span>|<span data-ttu-id="f5dfc-144">Özgün değer</span><span class="sxs-lookup"><span data-stu-id="f5dfc-144">Original value</span></span>|<span data-ttu-id="f5dfc-145">Geçerli değer</span><span class="sxs-lookup"><span data-stu-id="f5dfc-145">Current value</span></span>|<span data-ttu-id="f5dfc-146">Veritabanındaki değer</span><span class="sxs-lookup"><span data-stu-id="f5dfc-146">Value in database</span></span>|  
|-----------------|--------------------|-------------------|-----------------------|  
|<span data-ttu-id="f5dfc-147">CustId</span><span class="sxs-lookup"><span data-stu-id="f5dfc-147">CustID</span></span>|<span data-ttu-id="f5dfc-148">101</span><span class="sxs-lookup"><span data-stu-id="f5dfc-148">101</span></span>|<span data-ttu-id="f5dfc-149">101</span><span class="sxs-lookup"><span data-stu-id="f5dfc-149">101</span></span>|<span data-ttu-id="f5dfc-150">101</span><span class="sxs-lookup"><span data-stu-id="f5dfc-150">101</span></span>|  
|<span data-ttu-id="f5dfc-151">Soyadı</span><span class="sxs-lookup"><span data-stu-id="f5dfc-151">LastName</span></span>|<span data-ttu-id="f5dfc-152">Uludağ</span><span class="sxs-lookup"><span data-stu-id="f5dfc-152">Smith</span></span>|<span data-ttu-id="f5dfc-153">Uludağ</span><span class="sxs-lookup"><span data-stu-id="f5dfc-153">Smith</span></span>|<span data-ttu-id="f5dfc-154">Uludağ</span><span class="sxs-lookup"><span data-stu-id="f5dfc-154">Smith</span></span>|  
|<span data-ttu-id="f5dfc-155">firstName</span><span class="sxs-lookup"><span data-stu-id="f5dfc-155">FirstName</span></span>|<span data-ttu-id="f5dfc-156">Olduğundan</span><span class="sxs-lookup"><span data-stu-id="f5dfc-156">Bob</span></span>|<span data-ttu-id="f5dfc-157">Can</span><span class="sxs-lookup"><span data-stu-id="f5dfc-157">Robert</span></span>|<span data-ttu-id="f5dfc-158">Olduğundan</span><span class="sxs-lookup"><span data-stu-id="f5dfc-158">Bob</span></span>|  
  
 <span data-ttu-id="f5dfc-159">Güncelleştirme sırasında veritabanındaki değerler, kullanıcı2 'nin özgün değerleriyle eşleştiği için güncelleştirme başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="f5dfc-159">The update succeeds because the values in the database at the time of update match the original values that User2 has.</span></span>  
  
 <span data-ttu-id="f5dfc-160">Kullanıcı1 1:05, "Bob" adının adını "James" olarak değiştirir ve satırı güncelleştirmeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="f5dfc-160">At 1:05 p.m., User1 changes "Bob"'s first name to "James" and tries to update the row.</span></span>  
  
|<span data-ttu-id="f5dfc-161">Sütun adı</span><span class="sxs-lookup"><span data-stu-id="f5dfc-161">Column name</span></span>|<span data-ttu-id="f5dfc-162">Özgün değer</span><span class="sxs-lookup"><span data-stu-id="f5dfc-162">Original value</span></span>|<span data-ttu-id="f5dfc-163">Geçerli değer</span><span class="sxs-lookup"><span data-stu-id="f5dfc-163">Current value</span></span>|<span data-ttu-id="f5dfc-164">Veritabanındaki değer</span><span class="sxs-lookup"><span data-stu-id="f5dfc-164">Value in database</span></span>|  
|-----------------|--------------------|-------------------|-----------------------|  
|<span data-ttu-id="f5dfc-165">CustId</span><span class="sxs-lookup"><span data-stu-id="f5dfc-165">CustID</span></span>|<span data-ttu-id="f5dfc-166">101</span><span class="sxs-lookup"><span data-stu-id="f5dfc-166">101</span></span>|<span data-ttu-id="f5dfc-167">101</span><span class="sxs-lookup"><span data-stu-id="f5dfc-167">101</span></span>|<span data-ttu-id="f5dfc-168">101</span><span class="sxs-lookup"><span data-stu-id="f5dfc-168">101</span></span>|  
|<span data-ttu-id="f5dfc-169">Soyadı</span><span class="sxs-lookup"><span data-stu-id="f5dfc-169">LastName</span></span>|<span data-ttu-id="f5dfc-170">Uludağ</span><span class="sxs-lookup"><span data-stu-id="f5dfc-170">Smith</span></span>|<span data-ttu-id="f5dfc-171">Uludağ</span><span class="sxs-lookup"><span data-stu-id="f5dfc-171">Smith</span></span>|<span data-ttu-id="f5dfc-172">Uludağ</span><span class="sxs-lookup"><span data-stu-id="f5dfc-172">Smith</span></span>|  
|<span data-ttu-id="f5dfc-173">firstName</span><span class="sxs-lookup"><span data-stu-id="f5dfc-173">FirstName</span></span>|<span data-ttu-id="f5dfc-174">Olduğundan</span><span class="sxs-lookup"><span data-stu-id="f5dfc-174">Bob</span></span>|<span data-ttu-id="f5dfc-175">James</span><span class="sxs-lookup"><span data-stu-id="f5dfc-175">James</span></span>|<span data-ttu-id="f5dfc-176">Can</span><span class="sxs-lookup"><span data-stu-id="f5dfc-176">Robert</span></span>|  
  
 <span data-ttu-id="f5dfc-177">Bu noktada, veritabanındaki değer ("Robert") artık Kullanıcı1 'in beklediği orijinal değerle ("emre") eşleşmediği için Kullanıcı1 bir iyimser eşzamanlılık ihlaline rastlandı.</span><span class="sxs-lookup"><span data-stu-id="f5dfc-177">At this point, User1 encounters an optimistic concurrency violation because the value in the database ("Robert") no longer matches the original value that User1 was expecting ("Bob").</span></span> <span data-ttu-id="f5dfc-178">Eşzamanlılık ihlali, güncelleştirmenin başarısız olduğunu bilmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="f5dfc-178">The concurrency violation simply lets you know that the update failed.</span></span> <span data-ttu-id="f5dfc-179">Artık kararların, Kullanıcı1 tarafından sağlanan değişikliklerle ilgili olarak belirtilen değişikliklerin üzerine yazılıp yazılmayacağı veya Kullanıcı1 tarafından yapılan değişiklikleri iptal edilip edilmeyeceğini yazmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f5dfc-179">The decision now needs to be made whether to overwrite the changes supplied by User2 with the changes supplied by User1, or to cancel the changes by User1.</span></span>  
  
## <a name="testing-for-optimistic-concurrency-violations"></a><span data-ttu-id="f5dfc-180">Iyimser eşzamanlılık Ihlalleri için test etme</span><span class="sxs-lookup"><span data-stu-id="f5dfc-180">Testing for Optimistic Concurrency Violations</span></span>  
 <span data-ttu-id="f5dfc-181">İyimser eşzamanlılık ihlalinin test edilmesi için çeşitli teknikler vardır.</span><span class="sxs-lookup"><span data-stu-id="f5dfc-181">There are several techniques for testing for an optimistic concurrency violation.</span></span> <span data-ttu-id="f5dfc-182">Biri, tabloya bir zaman damgası sütunu dahil içerir.</span><span class="sxs-lookup"><span data-stu-id="f5dfc-182">One involves including a timestamp column in the table.</span></span> <span data-ttu-id="f5dfc-183">Veritabanları genellikle kaydın en son güncelleştirildiği tarih ve saati belirlemek için kullanılan zaman damgası işlevlerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="f5dfc-183">Databases commonly provide timestamp functionality that can be used to identify the date and time when the record was last updated.</span></span> <span data-ttu-id="f5dfc-184">Bu tekniği kullanarak, tablo tanımına bir zaman damgası sütunu eklenir.</span><span class="sxs-lookup"><span data-stu-id="f5dfc-184">Using this technique, a timestamp column is included in the table definition.</span></span> <span data-ttu-id="f5dfc-185">Kayıt her güncelleştirildiğinde, zaman damgası geçerli tarih ve saati yansıtacak şekilde güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="f5dfc-185">Whenever the record is updated, the timestamp is updated to reflect the current date and time.</span></span> <span data-ttu-id="f5dfc-186">İyimser eşzamanlılık ihlallerine yönelik bir testte, zaman damgası sütunu tablo içeriğinin herhangi bir sorgusuyla döndürülür.</span><span class="sxs-lookup"><span data-stu-id="f5dfc-186">In a test for optimistic concurrency violations, the timestamp column is returned with any query of the contents of the table.</span></span> <span data-ttu-id="f5dfc-187">Bir güncelleştirme denendiğinde, veritabanındaki zaman damgası değeri, değiştirilen satırda yer alan özgün zaman damgası değeriyle karşılaştırılır.</span><span class="sxs-lookup"><span data-stu-id="f5dfc-187">When an update is attempted, the timestamp value in the database is compared to the original timestamp value contained in the modified row.</span></span> <span data-ttu-id="f5dfc-188">Eşleşiyorsa, güncelleştirme gerçekleştirilir ve zaman damgası sütunu, güncelleştirmenin yansıtılması için geçerli zaman ile güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="f5dfc-188">If they match, the update is performed and the timestamp column is updated with the current time to reflect the update.</span></span> <span data-ttu-id="f5dfc-189">Eşleşmiyorsa, iyimser eşzamanlılık ihlali meydana geldi.</span><span class="sxs-lookup"><span data-stu-id="f5dfc-189">If they do not match, an optimistic concurrency violation has occurred.</span></span>  
  
 <span data-ttu-id="f5dfc-190">İyimser eşzamanlılık ihlalinin test edilmesine yönelik başka bir teknik de, bir satırdaki tüm özgün sütun değerlerinin veritabanında bulunan olanlarla aynı olduğunu doğrulamadır.</span><span class="sxs-lookup"><span data-stu-id="f5dfc-190">Another technique for testing for an optimistic concurrency violation is to verify that all the original column values in a row still match those found in the database.</span></span> <span data-ttu-id="f5dfc-191">Örneğin, aşağıdaki sorguyu göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="f5dfc-191">For example, consider the following query:</span></span>  
  
```sql
SELECT Col1, Col2, Col3 FROM Table1  
```  
  
 <span data-ttu-id="f5dfc-192">**Table1**içinde bir satırı güncelleştirirken iyimser eşzamanlılık ihlalini sınamak IÇIN aşağıdaki güncelleştirme ifadesini verirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f5dfc-192">To test for an optimistic concurrency violation when updating a row in **Table1**, you would issue the following UPDATE statement:</span></span>  
  
```sql
UPDATE Table1 Set Col1 = @NewCol1Value,  
              Set Col2 = @NewCol2Value,  
              Set Col3 = @NewCol3Value  
WHERE Col1 = @OldCol1Value AND  
      Col2 = @OldCol2Value AND  
      Col3 = @OldCol3Value  
```  
  
 <span data-ttu-id="f5dfc-193">Özgün değerler veritabanındaki değerlerle eşleştiği sürece, güncelleştirme gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="f5dfc-193">As long as the original values match the values in the database, the update is performed.</span></span> <span data-ttu-id="f5dfc-194">Bir değer değiştirildiyse güncelleştirme satırı değiştirmez çünkü WHERE yan tümcesi bir eşleşme bulamaz.</span><span class="sxs-lookup"><span data-stu-id="f5dfc-194">If a value has been modified, the update will not modify the row because the WHERE clause will not find a match.</span></span>  
  
 <span data-ttu-id="f5dfc-195">Sorgunuzda her zaman benzersiz bir birincil anahtar değeri döndürülmesi önerildiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="f5dfc-195">Note that it is recommended to always return a unique primary key value in your query.</span></span> <span data-ttu-id="f5dfc-196">Aksi halde, önceki UPDATE deyimleri birden fazla satırı güncelleştirebilir, bu, sizin amacınız olabilir.</span><span class="sxs-lookup"><span data-stu-id="f5dfc-196">Otherwise, the preceding UPDATE statement may update more than one row, which might not be your intent.</span></span>  
  
 <span data-ttu-id="f5dfc-197">Veri kaynağınızdaki bir sütun null değerlere izin veriyorsa, yerel tablonuzda ve veri kaynağında eşleşen bir null başvurusu denetlemek için WHERE yan tümcesini genişletmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="f5dfc-197">If a column at your data source allows nulls, you may need to extend your WHERE clause to check for a matching null reference in your local table and at the data source.</span></span> <span data-ttu-id="f5dfc-198">Örneğin, aşağıdaki UPDATE bildiriminde, yerel satırdaki null başvurusunun, veri kaynağında null başvurusuyla hala eşleştiğini veya yerel satırdaki değerin hala veri kaynağındaki değerle eşleştiğini doğrular.</span><span class="sxs-lookup"><span data-stu-id="f5dfc-198">For example, the following UPDATE statement verifies that a null reference in the local row still matches a null reference at the data source, or that the value in the local row still matches the value at the data source.</span></span>  
  
```sql
UPDATE Table1 Set Col1 = @NewVal1  
  WHERE (@OldVal1 IS NULL AND Col1 IS NULL) OR Col1 = @OldVal1  
```  
  
 <span data-ttu-id="f5dfc-199">İyimser eşzamanlılık modeli kullanırken daha az kısıtlayıcı ölçütler uygulamayı da tercih edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f5dfc-199">You may also choose to apply less restrictive criteria when using an optimistic concurrency model.</span></span> <span data-ttu-id="f5dfc-200">Örneğin, WHERE yan tümcesindeki birincil anahtar sütunlarının kullanılması, diğer sütunların son sorgudan bu yana güncelleştirilip güncelleştirilmediğini ne olursa olsun verilerin üzerine yazılmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="f5dfc-200">For example, using only the primary key columns in the WHERE clause causes the data to be overwritten regardless of whether the other columns have been updated since the last query.</span></span> <span data-ttu-id="f5dfc-201">Yalnızca belirli sütunlara bir WHERE yan tümcesi uygulayabilirsiniz ve belirli alanlar son sorgulandıktan sonra güncellenmemişse verilerin üzerine yazılmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="f5dfc-201">You can also apply a WHERE clause only to specific columns, resulting in data being overwritten unless particular fields have been updated since they were last queried.</span></span>  
  
### <a name="the-dataadapterrowupdated-event"></a><span data-ttu-id="f5dfc-202">DataAdapter. RowUpdated olayı</span><span class="sxs-lookup"><span data-stu-id="f5dfc-202">The DataAdapter.RowUpdated Event</span></span>  
 <span data-ttu-id="f5dfc-203"><xref:System.Data.Common.DataAdapter> nesnesinin **RowUpdated** olayı, daha önce açıklanan tekniklerle birlikte kullanılarak iyimser eşzamanlılık ihlallerinin uygulamanıza yönelik bildirim sağlar.</span><span class="sxs-lookup"><span data-stu-id="f5dfc-203">The **RowUpdated** event of the <xref:System.Data.Common.DataAdapter> object can be used in conjunction with the techniques described earlier, to provide notification to your application of optimistic concurrency violations.</span></span> <span data-ttu-id="f5dfc-204">**RowUpdated** , bir **veri kümesinden** **değiştirilen** bir satırı güncelleştirme denemesinden sonra oluşur.</span><span class="sxs-lookup"><span data-stu-id="f5dfc-204">**RowUpdated** occurs after each attempt to update a **Modified** row from a **DataSet**.</span></span> <span data-ttu-id="f5dfc-205">Bu, bir özel durum oluştuğunda işleme, özel hata bilgileri ekleme, yeniden deneme mantığı ekleme vb. gibi özel işleme kodu eklemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="f5dfc-205">This enables you to add special handling code, including processing when an exception occurs, adding custom error information, adding retry logic, and so on.</span></span> <span data-ttu-id="f5dfc-206"><xref:System.Data.Common.RowUpdatedEventArgs> nesnesi, bir tablodaki değiştirilmiş bir satır için belirli bir Update komutundan etkilenen satır sayısını içeren bir **Recordsamısson** özelliği döndürür.</span><span class="sxs-lookup"><span data-stu-id="f5dfc-206">The <xref:System.Data.Common.RowUpdatedEventArgs> object returns a **RecordsAffected** property containing the number of rows affected by a particular update command for a modified row in a table.</span></span> <span data-ttu-id="f5dfc-207">Güncelleştirme komutunu iyimser eşzamanlılık için test edecek şekilde ayarlayarak, **Recordsaetkilenmeyen** özelliği, bir sonuç olarak bir iyimser eşzamanlılık ihlali meydana geldiğinde 0 değerini döndürür, çünkü hiçbir kayıt güncelleştirilmemiş.</span><span class="sxs-lookup"><span data-stu-id="f5dfc-207">By setting the update command to test for optimistic concurrency, the **RecordsAffected** property will, as a result, return a value of 0 when an optimistic concurrency violation has occurred, because no records were updated.</span></span> <span data-ttu-id="f5dfc-208">Bu durumda, bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="f5dfc-208">If this is the case, an exception is thrown.</span></span> <span data-ttu-id="f5dfc-209">**RowUpdated** olayı, bu oluşumu idare etmenizi ve **UpdateStatus. SkipCurrentRow**gibi uygun bir **RowUpdatedEventArgs. Status** değeri ayarlayarak özel durumu önlemenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="f5dfc-209">The **RowUpdated** event enables you to handle this occurrence and avoid the exception by setting an appropriate **RowUpdatedEventArgs.Status** value, such as **UpdateStatus.SkipCurrentRow**.</span></span> <span data-ttu-id="f5dfc-210">**RowUpdated** olayı hakkında daha fazla bilgi için bkz. [DataAdapter olaylarını işleme](handling-dataadapter-events.md).</span><span class="sxs-lookup"><span data-stu-id="f5dfc-210">For more information about the **RowUpdated** event, see [Handling DataAdapter Events](handling-dataadapter-events.md).</span></span>  
  
 <span data-ttu-id="f5dfc-211">İsteğe bağlı olarak, **Güncelleştir**' i çağırmadan önce **DataAdapter. devam updateıse** 'yi **true**olarak ayarlayabilir ve **güncelleştirme** tamamlandığında belirli bir satırın **RowError** özelliğinde depolanan hata bilgilerine yanıt verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f5dfc-211">Optionally, you can set **DataAdapter.ContinueUpdateOnError** to **true**, before calling **Update**, and respond to the error information stored in the **RowError** property of a particular row when the **Update** is completed.</span></span> <span data-ttu-id="f5dfc-212">Daha fazla bilgi için bkz. [satır hata bilgileri](./dataset-datatable-dataview/row-error-information.md).</span><span class="sxs-lookup"><span data-stu-id="f5dfc-212">For more information, see [Row Error Information](./dataset-datatable-dataview/row-error-information.md).</span></span>  
  
## <a name="optimistic-concurrency-example"></a><span data-ttu-id="f5dfc-213">İyimser eşzamanlılık örneği</span><span class="sxs-lookup"><span data-stu-id="f5dfc-213">Optimistic Concurrency Example</span></span>  
 <span data-ttu-id="f5dfc-214">Aşağıda, bir **DataAdapter** 'ın **UpdateCommand** öğesini iyimser eşzamanlılık için test etmek üzere ayarlayan ve ardından iyimser eşzamanlılık Ihlallerini test etmek için **RowUpdated** olayını kullanan basit bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f5dfc-214">The following is a simple example that sets the **UpdateCommand** of a **DataAdapter** to test for optimistic concurrency, and then uses the **RowUpdated** event to test for optimistic concurrency violations.</span></span> <span data-ttu-id="f5dfc-215">İyimser eşzamanlılık ihlaliyle karşılaşıldığında, uygulama güncelleştirmenin verildiği satırın **RowError hatasını** bir iyimser eşzamanlılık ihlalini yansıtacak şekilde ayarlar.</span><span class="sxs-lookup"><span data-stu-id="f5dfc-215">When an optimistic concurrency violation is encountered, the application sets the **RowError** of the row that the update was issued for to reflect an optimistic concurrency violation.</span></span>  
  
 <span data-ttu-id="f5dfc-216">UPDATE komutunun WHERE yan tümcesine geçirilen parametre değerlerinin kendi sütunlarının **özgün** değerleriyle eşlendiğine unutmayın.</span><span class="sxs-lookup"><span data-stu-id="f5dfc-216">Note that the parameter values passed to the WHERE clause of the UPDATE command are mapped to the **Original** values of their respective columns.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f5dfc-217">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f5dfc-217">See also</span></span>

- [<span data-ttu-id="f5dfc-218">ADO.NET’te Veri Alma ve Değiştirme</span><span class="sxs-lookup"><span data-stu-id="f5dfc-218">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
- [<span data-ttu-id="f5dfc-219">Veri Kaynaklarını DataAdapters ile Güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="f5dfc-219">Updating Data Sources with DataAdapters</span></span>](updating-data-sources-with-dataadapters.md)
- [<span data-ttu-id="f5dfc-220">Satır Hatası Bilgileri</span><span class="sxs-lookup"><span data-stu-id="f5dfc-220">Row Error Information</span></span>](./dataset-datatable-dataview/row-error-information.md)
- [<span data-ttu-id="f5dfc-221">İşlemler ve Eşzamanlılık</span><span class="sxs-lookup"><span data-stu-id="f5dfc-221">Transactions and Concurrency</span></span>](transactions-and-concurrency.md)
- [<span data-ttu-id="f5dfc-222">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f5dfc-222">ADO.NET Overview</span></span>](ado-net-overview.md)
