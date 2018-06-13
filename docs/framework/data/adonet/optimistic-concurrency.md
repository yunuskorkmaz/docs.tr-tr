---
title: İyimser eşzamanlılık
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e380edac-da67-4276-80a5-b64decae4947
ms.openlocfilehash: b1395c3bd81f7f9d2f12d5b1ea2ec4b784f7aab9
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32766234"
---
# <a name="optimistic-concurrency"></a><span data-ttu-id="f2111-102">İyimser eşzamanlılık</span><span class="sxs-lookup"><span data-stu-id="f2111-102">Optimistic Concurrency</span></span>
<span data-ttu-id="f2111-103">Çok kullanıcılı bir ortamda bir veritabanındaki verileri güncelleştirmek için iki model vardır: iyimser eşzamanlılık ve eşzamanlılık.</span><span class="sxs-lookup"><span data-stu-id="f2111-103">In a multiuser environment, there are two models for updating data in a database: optimistic concurrency and pessimistic concurrency.</span></span> <span data-ttu-id="f2111-104"><xref:System.Data.DataSet> Nesne remoting veri ve veri ile etkileşim gibi uzun süre çalışan etkinlikleri için iyimser eşzamanlılık kullanımını teşvik şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="f2111-104">The <xref:System.Data.DataSet> object is designed to encourage the use of optimistic concurrency for long-running activities, such as remoting data and interacting with data.</span></span>  
  
 <span data-ttu-id="f2111-105">Eşzamanlılık satırları diğer kullanıcıların verileri geçerli kullanıcının etkileyen şekilde değiştirmesini engellemek için veri kaynağında kilitleme içerir.</span><span class="sxs-lookup"><span data-stu-id="f2111-105">Pessimistic concurrency involves locking rows at the data source to prevent other users from modifying data in a way that affects the current user.</span></span> <span data-ttu-id="f2111-106">Bir kullanıcı uygulanması için bir kilit neden olan bir eylem gerçekleştirir kötümser modelinde, diğer kullanıcıların kilit sahibi bırakması kadar kilidiyle çakışabilir işlemleri gerçekleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="f2111-106">In a pessimistic model, when a user performs an action that causes a lock to be applied, other users cannot perform actions that would conflict with the lock until the lock owner releases it.</span></span> <span data-ttu-id="f2111-107">Bu model, öncelikle ortamlarda kullanılır söz konusu olduğunda, veriler için yoğun Çekişme böylece kilitleri ile verileri koruma maliyeti eşzamanlılık çakışma meydana gelirse işlemleri geri maliyetini'dan küçük.</span><span class="sxs-lookup"><span data-stu-id="f2111-107">This model is primarily used in environments where there is heavy contention for data, so that the cost of protecting data with locks is less than the cost of rolling back transactions if concurrency conflicts occur.</span></span>  
  
 <span data-ttu-id="f2111-108">Bu nedenle, bir eşzamanlılık modelde kilit bir satır güncelleştirmeleri bir kullanıcı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f2111-108">Therefore, in a pessimistic concurrency model, a user who updates a row establishes a lock.</span></span> <span data-ttu-id="f2111-109">Kullanıcı güncelleştirme tamamlandı ve kilidi serbest kadar hiç kimsenin satır değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f2111-109">Until the user has finished the update and released the lock, no one else can change that row.</span></span> <span data-ttu-id="f2111-110">Kilit kez kısa, kayıtları programlı işlenmesini olduğu gibi, bu nedenle, en iyi eşzamanlılık uygulanır.</span><span class="sxs-lookup"><span data-stu-id="f2111-110">For this reason, pessimistic concurrency is best implemented when lock times will be short, as in programmatic processing of records.</span></span> <span data-ttu-id="f2111-111">Kullanıcılar veri ile etkileşim ve kayıtları görece büyük süreyle kilitlenmesine neden eşzamanlılık ölçeklenebilir bir seçenek değil.</span><span class="sxs-lookup"><span data-stu-id="f2111-111">Pessimistic concurrency is not a scalable option when users are interacting with data and causing records to be locked for relatively large periods of time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f2111-112">Aynı işlemde birden çok satır güncellemeniz gerekiyorsa, bir işlem oluşturma kötümser kilitleme kullanmaktan daha ölçeklenebilir bir seçenektir.</span><span class="sxs-lookup"><span data-stu-id="f2111-112">If you need to update multiple rows in the same operation, then creating a transaction is a more scalable option than using pessimistic locking.</span></span>  
  
 <span data-ttu-id="f2111-113">Bunun aksine, iyimser eşzamanlılık kullanan kullanıcılar bir satır onu okunurken kilit yok.</span><span class="sxs-lookup"><span data-stu-id="f2111-113">By contrast, users who use optimistic concurrency do not lock a row when reading it.</span></span> <span data-ttu-id="f2111-114">Bir kullanıcı bir satırı güncelleştirme istediğinde, uygulamayı başka bir kullanıcı bunu okunuşundan bu yana satır değişip değişmediğini belirlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f2111-114">When a user wants to update a row, the application must determine whether another user has changed the row since it was read.</span></span> <span data-ttu-id="f2111-115">İyimser eşzamanlılık genellikle düşük bir çakışma ile ortamlarda veriler için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f2111-115">Optimistic concurrency is generally used in environments with a low contention for data.</span></span> <span data-ttu-id="f2111-116">İyimser eşzamanlılık hiçbir kayıtları kilitleme gereklidir ve kayıtları kilitleme ek sunucu kaynakları gerekir çünkü performansı artırır.</span><span class="sxs-lookup"><span data-stu-id="f2111-116">Optimistic concurrency improves performance because no locking of records is required, and locking of records requires additional server resources.</span></span> <span data-ttu-id="f2111-117">Ayrıca, kayıt kilitleri korumak için veritabanı sunucusu kalıcı bir bağlantı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="f2111-117">Also, in order to maintain record locks, a persistent connection to the database server is required.</span></span> <span data-ttu-id="f2111-118">İyimser eşzamanlılık modeli durumda olmadığından sunucusuna bağlantılarda daha kısa sürede çok sayıda istemciler hizmet ücretsizdir.</span><span class="sxs-lookup"><span data-stu-id="f2111-118">Because this is not the case in an optimistic concurrency model, connections to the server are free to serve a larger number of clients in less time.</span></span>  
  
 <span data-ttu-id="f2111-119">İyimser eşzamanlılık modelinde, bir ihlali kullanıcı veritabanından bir değer aldıktan sonra ilk kullanıcı bunu değiştirmeye çalıştı önce başka bir kullanıcı değeri değiştirirse, oluşmuş kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="f2111-119">In an optimistic concurrency model, a violation is considered to have occurred if, after a user receives a value from the database, another user modifies the value before the first user has attempted to modify it.</span></span> <span data-ttu-id="f2111-120">Sunucu bir eşzamanlılık ihlali nasıl çözümlediği aşağıdaki örnekte açıklayarak en iyi şekilde gösterilir.</span><span class="sxs-lookup"><span data-stu-id="f2111-120">How the server resolves a concurrency violation is best shown by first describing the following example.</span></span>  
  
 <span data-ttu-id="f2111-121">Aşağıdaki tablolarda iyimser eşzamanlılık örneği izleyin.</span><span class="sxs-lookup"><span data-stu-id="f2111-121">The following tables follow an example of optimistic concurrency.</span></span>  
  
 <span data-ttu-id="f2111-122">1: 00'da, Kullanıcı1 veritabanı aşağıdaki değerlere sahip bir satır okur:</span><span class="sxs-lookup"><span data-stu-id="f2111-122">At 1:00 p.m., User1 reads a row from the database with the following values:</span></span>  
  
 <span data-ttu-id="f2111-123">**CustId Soyadı adı**</span><span class="sxs-lookup"><span data-stu-id="f2111-123">**CustID     LastName     FirstName**</span></span>  
  
 <span data-ttu-id="f2111-124">101 Smith Bob</span><span class="sxs-lookup"><span data-stu-id="f2111-124">101          Smith             Bob</span></span>  
  
|<span data-ttu-id="f2111-125">Sütun adı</span><span class="sxs-lookup"><span data-stu-id="f2111-125">Column name</span></span>|<span data-ttu-id="f2111-126">Özgün değeri</span><span class="sxs-lookup"><span data-stu-id="f2111-126">Original value</span></span>|<span data-ttu-id="f2111-127">Geçerli değer</span><span class="sxs-lookup"><span data-stu-id="f2111-127">Current value</span></span>|<span data-ttu-id="f2111-128">Veritabanında değeri</span><span class="sxs-lookup"><span data-stu-id="f2111-128">Value in database</span></span>|  
|-----------------|--------------------|-------------------|-----------------------|  
|<span data-ttu-id="f2111-129">CustId</span><span class="sxs-lookup"><span data-stu-id="f2111-129">CustID</span></span>|<span data-ttu-id="f2111-130">101</span><span class="sxs-lookup"><span data-stu-id="f2111-130">101</span></span>|<span data-ttu-id="f2111-131">101</span><span class="sxs-lookup"><span data-stu-id="f2111-131">101</span></span>|<span data-ttu-id="f2111-132">101</span><span class="sxs-lookup"><span data-stu-id="f2111-132">101</span></span>|  
|<span data-ttu-id="f2111-133">Soyadı</span><span class="sxs-lookup"><span data-stu-id="f2111-133">LastName</span></span>|<span data-ttu-id="f2111-134">Smith</span><span class="sxs-lookup"><span data-stu-id="f2111-134">Smith</span></span>|<span data-ttu-id="f2111-135">Smith</span><span class="sxs-lookup"><span data-stu-id="f2111-135">Smith</span></span>|<span data-ttu-id="f2111-136">Smith</span><span class="sxs-lookup"><span data-stu-id="f2111-136">Smith</span></span>|  
|<span data-ttu-id="f2111-137">FirstName</span><span class="sxs-lookup"><span data-stu-id="f2111-137">FirstName</span></span>|<span data-ttu-id="f2111-138">Bob</span><span class="sxs-lookup"><span data-stu-id="f2111-138">Bob</span></span>|<span data-ttu-id="f2111-139">Bob</span><span class="sxs-lookup"><span data-stu-id="f2111-139">Bob</span></span>|<span data-ttu-id="f2111-140">Bob</span><span class="sxs-lookup"><span data-stu-id="f2111-140">Bob</span></span>|  
  
 <span data-ttu-id="f2111-141">1: 01'de, aynı satır kullanıcı2 okur.</span><span class="sxs-lookup"><span data-stu-id="f2111-141">At 1:01 p.m., User2 reads the same row.</span></span>  
  
 <span data-ttu-id="f2111-142">Kullanıcı2: 03 p.M'de, 1 değiştirir **FirstName** "Robert" için "Bob" den ve veritabanını güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="f2111-142">At 1:03 p.m., User2 changes **FirstName** from "Bob" to "Robert" and updates the database.</span></span>  
  
|<span data-ttu-id="f2111-143">Sütun adı</span><span class="sxs-lookup"><span data-stu-id="f2111-143">Column name</span></span>|<span data-ttu-id="f2111-144">Özgün değeri</span><span class="sxs-lookup"><span data-stu-id="f2111-144">Original value</span></span>|<span data-ttu-id="f2111-145">Geçerli değer</span><span class="sxs-lookup"><span data-stu-id="f2111-145">Current value</span></span>|<span data-ttu-id="f2111-146">Veritabanında değeri</span><span class="sxs-lookup"><span data-stu-id="f2111-146">Value in database</span></span>|  
|-----------------|--------------------|-------------------|-----------------------|  
|<span data-ttu-id="f2111-147">CustId</span><span class="sxs-lookup"><span data-stu-id="f2111-147">CustID</span></span>|<span data-ttu-id="f2111-148">101</span><span class="sxs-lookup"><span data-stu-id="f2111-148">101</span></span>|<span data-ttu-id="f2111-149">101</span><span class="sxs-lookup"><span data-stu-id="f2111-149">101</span></span>|<span data-ttu-id="f2111-150">101</span><span class="sxs-lookup"><span data-stu-id="f2111-150">101</span></span>|  
|<span data-ttu-id="f2111-151">Soyadı</span><span class="sxs-lookup"><span data-stu-id="f2111-151">LastName</span></span>|<span data-ttu-id="f2111-152">Smith</span><span class="sxs-lookup"><span data-stu-id="f2111-152">Smith</span></span>|<span data-ttu-id="f2111-153">Smith</span><span class="sxs-lookup"><span data-stu-id="f2111-153">Smith</span></span>|<span data-ttu-id="f2111-154">Smith</span><span class="sxs-lookup"><span data-stu-id="f2111-154">Smith</span></span>|  
|<span data-ttu-id="f2111-155">FirstName</span><span class="sxs-lookup"><span data-stu-id="f2111-155">FirstName</span></span>|<span data-ttu-id="f2111-156">Bob</span><span class="sxs-lookup"><span data-stu-id="f2111-156">Bob</span></span>|<span data-ttu-id="f2111-157">Robert</span><span class="sxs-lookup"><span data-stu-id="f2111-157">Robert</span></span>|<span data-ttu-id="f2111-158">Bob</span><span class="sxs-lookup"><span data-stu-id="f2111-158">Bob</span></span>|  
  
 <span data-ttu-id="f2111-159">Güncelleştirme zaman veritabanındaki değerleri kullanıcı2 sahip özgün değerler eşleştiğinden Güncelleştirme başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="f2111-159">The update succeeds because the values in the database at the time of update match the original values that User2 has.</span></span>  
  
 <span data-ttu-id="f2111-160">1: p.M'de 05, Kullanıcı1 "Bob" ın adını "Can" değiştirir ve satır güncelleştirmeyi dener.</span><span class="sxs-lookup"><span data-stu-id="f2111-160">At 1:05 p.m., User1 changes "Bob"'s first name to "James" and tries to update the row.</span></span>  
  
|<span data-ttu-id="f2111-161">Sütun adı</span><span class="sxs-lookup"><span data-stu-id="f2111-161">Column name</span></span>|<span data-ttu-id="f2111-162">Özgün değeri</span><span class="sxs-lookup"><span data-stu-id="f2111-162">Original value</span></span>|<span data-ttu-id="f2111-163">Geçerli değer</span><span class="sxs-lookup"><span data-stu-id="f2111-163">Current value</span></span>|<span data-ttu-id="f2111-164">Veritabanında değeri</span><span class="sxs-lookup"><span data-stu-id="f2111-164">Value in database</span></span>|  
|-----------------|--------------------|-------------------|-----------------------|  
|<span data-ttu-id="f2111-165">CustId</span><span class="sxs-lookup"><span data-stu-id="f2111-165">CustID</span></span>|<span data-ttu-id="f2111-166">101</span><span class="sxs-lookup"><span data-stu-id="f2111-166">101</span></span>|<span data-ttu-id="f2111-167">101</span><span class="sxs-lookup"><span data-stu-id="f2111-167">101</span></span>|<span data-ttu-id="f2111-168">101</span><span class="sxs-lookup"><span data-stu-id="f2111-168">101</span></span>|  
|<span data-ttu-id="f2111-169">Soyadı</span><span class="sxs-lookup"><span data-stu-id="f2111-169">LastName</span></span>|<span data-ttu-id="f2111-170">Smith</span><span class="sxs-lookup"><span data-stu-id="f2111-170">Smith</span></span>|<span data-ttu-id="f2111-171">Smith</span><span class="sxs-lookup"><span data-stu-id="f2111-171">Smith</span></span>|<span data-ttu-id="f2111-172">Smith</span><span class="sxs-lookup"><span data-stu-id="f2111-172">Smith</span></span>|  
|<span data-ttu-id="f2111-173">FirstName</span><span class="sxs-lookup"><span data-stu-id="f2111-173">FirstName</span></span>|<span data-ttu-id="f2111-174">Bob</span><span class="sxs-lookup"><span data-stu-id="f2111-174">Bob</span></span>|<span data-ttu-id="f2111-175">Ahmet</span><span class="sxs-lookup"><span data-stu-id="f2111-175">James</span></span>|<span data-ttu-id="f2111-176">Robert</span><span class="sxs-lookup"><span data-stu-id="f2111-176">Robert</span></span>|  
  
 <span data-ttu-id="f2111-177">Bu noktada, Kullanıcı1 ("Kemal") bekliyordu özgün değeri ("Robert") veritabanındaki değerle artık eşleştiğinden Kullanıcı1 iyimser eşzamanlılık ihlali karşılaşır.</span><span class="sxs-lookup"><span data-stu-id="f2111-177">At this point, User1 encounters an optimistic concurrency violation because the value in the database ("Robert") no longer matches the original value that User1 was expecting ("Bob").</span></span> <span data-ttu-id="f2111-178">Eşzamanlılık ihlali basitçe, güncelleştirmenin başarısız olduğunu bilmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="f2111-178">The concurrency violation simply lets you know that the update failed.</span></span> <span data-ttu-id="f2111-179">Karar şimdi mi, yoksa Kullanıcı1 tarafından sağlanan değişikliklerle kullanıcı2 tarafından sağlanan değişikliklerin üzerine yazmak için değişiklikleri iptal etmek için Kullanıcı1 tarafından yapılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f2111-179">The decision now needs to be made whether to overwrite the changes supplied by User2 with the changes supplied by User1, or to cancel the changes by User1.</span></span>  
  
## <a name="testing-for-optimistic-concurrency-violations"></a><span data-ttu-id="f2111-180">İyimser eşzamanlılık ihlali test etme</span><span class="sxs-lookup"><span data-stu-id="f2111-180">Testing for Optimistic Concurrency Violations</span></span>  
 <span data-ttu-id="f2111-181">İyimser eşzamanlılık ihlali için test etmek için birçok tekniği vardır.</span><span class="sxs-lookup"><span data-stu-id="f2111-181">There are several techniques for testing for an optimistic concurrency violation.</span></span> <span data-ttu-id="f2111-182">Bir tabloda bir zaman damgası sütunu dahil olmak üzere içerir.</span><span class="sxs-lookup"><span data-stu-id="f2111-182">One involves including a timestamp column in the table.</span></span> <span data-ttu-id="f2111-183">Veritabanları, genellikle kayıt en son güncelleştirildiği saat ve tarihi tanımlamak için kullanılan zaman damgası işlevsellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="f2111-183">Databases commonly provide timestamp functionality that can be used to identify the date and time when the record was last updated.</span></span> <span data-ttu-id="f2111-184">Bu teknik kullanılarak, bir zaman damgası sütunu tablo tanımı dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="f2111-184">Using this technique, a timestamp column is included in the table definition.</span></span> <span data-ttu-id="f2111-185">Kayıt güncelleştirildiğinde, zaman damgası geçerli tarih ve saat yansıtacak şekilde güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="f2111-185">Whenever the record is updated, the timestamp is updated to reflect the current date and time.</span></span> <span data-ttu-id="f2111-186">İyimser eşzamanlılık ihlalleri için bir test, zaman damgası sütunu tablonun içeriği herhangi bir sorgu ile döndürülür.</span><span class="sxs-lookup"><span data-stu-id="f2111-186">In a test for optimistic concurrency violations, the timestamp column is returned with any query of the contents of the table.</span></span> <span data-ttu-id="f2111-187">Bir güncelleştirme çalışırken zaman damgası değerini veritabanında değişiklik satır içinde yer alan ilk zaman damgası değeri karşılaştırılır.</span><span class="sxs-lookup"><span data-stu-id="f2111-187">When an update is attempted, the timestamp value in the database is compared to the original timestamp value contained in the modified row.</span></span> <span data-ttu-id="f2111-188">Eşleşirlerse, güncelleştirme gerçekleştirilir ve zaman damgası sütunu geçerli zamanla güncelleştirmesini yansıtacak şekilde güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="f2111-188">If they match, the update is performed and the timestamp column is updated with the current time to reflect the update.</span></span> <span data-ttu-id="f2111-189">Bunlar eşleşmiyorsa iyimser eşzamanlılık ihlali oluştu.</span><span class="sxs-lookup"><span data-stu-id="f2111-189">If they do not match, an optimistic concurrency violation has occurred.</span></span>  
  
 <span data-ttu-id="f2111-190">İyimser eşzamanlılık ihlali için test etmek için başka bir teknik bir satır tüm özgün sütun değerleri hala veritabanında bulunan eşleştiğinden doğrulamaktır.</span><span class="sxs-lookup"><span data-stu-id="f2111-190">Another technique for testing for an optimistic concurrency violation is to verify that all the original column values in a row still match those found in the database.</span></span> <span data-ttu-id="f2111-191">Örneğin, aşağıdaki sorguyu göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="f2111-191">For example, consider the following query:</span></span>  
  
```  
SELECT Col1, Col2, Col3 FROM Table1  
```  
  
 <span data-ttu-id="f2111-192">İyimser eşzamanlılık ihlali için bir satır güncelleştirirken test etmek için **tablo1**, aşağıdaki güncelleştirme deyimini vermek:</span><span class="sxs-lookup"><span data-stu-id="f2111-192">To test for an optimistic concurrency violation when updating a row in **Table1**, you would issue the following UPDATE statement:</span></span>  
  
```  
UPDATE Table1 Set Col1 = @NewCol1Value,  
              Set Col2 = @NewCol2Value,  
              Set Col3 = @NewCol3Value  
WHERE Col1 = @OldCol1Value AND  
      Col2 = @OldCol2Value AND  
      Col3 = @OldCol3Value  
```  
  
 <span data-ttu-id="f2111-193">Veritabanındaki değerleri özgün değerler eşleştiği sürece güncelleştirme gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="f2111-193">As long as the original values match the values in the database, the update is performed.</span></span> <span data-ttu-id="f2111-194">Bir değer değiştirilirse güncelleştirme satır olduğundan değiştirmez WHERE yan tümcesi bir eşleşme bulamaz.</span><span class="sxs-lookup"><span data-stu-id="f2111-194">If a value has been modified, the update will not modify the row because the WHERE clause will not find a match.</span></span>  
  
 <span data-ttu-id="f2111-195">Her zaman sorgunuzda benzersiz bir birincil anahtar değeri döndürmek için önerilen unutmayın.</span><span class="sxs-lookup"><span data-stu-id="f2111-195">Note that it is recommended to always return a unique primary key value in your query.</span></span> <span data-ttu-id="f2111-196">Aksi takdirde, önceki güncelleştirme bildirimini maksadınızı olmayabilir birden fazla satır güncelleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="f2111-196">Otherwise, the preceding UPDATE statement may update more than one row, which might not be your intent.</span></span>  
  
 <span data-ttu-id="f2111-197">Veri kaynağı bir sütunu null değerlere izin veriyorsa, eşleşen bir null başvuru yerel tablonuz ve veri kaynağında denetlemek için WHERE yan tümcesinde uzatma gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="f2111-197">If a column at your data source allows nulls, you may need to extend your WHERE clause to check for a matching null reference in your local table and at the data source.</span></span> <span data-ttu-id="f2111-198">Örneğin, aşağıdaki güncelleştirme deyimini yerel satırda null bir başvuru hala bir null başvuru veri kaynağında eşleşiyor veya yerel satır değeri hala veri kaynağı değerinde eşleştiğini doğrular.</span><span class="sxs-lookup"><span data-stu-id="f2111-198">For example, the following UPDATE statement verifies that a null reference in the local row still matches a null reference at the data source, or that the value in the local row still matches the value at the data source.</span></span>  
  
```  
UPDATE Table1 Set Col1 = @NewVal1  
  WHERE (@OldVal1 IS NULL AND Col1 IS NULL) OR Col1 = @OldVal1  
```  
  
 <span data-ttu-id="f2111-199">İyimser eşzamanlılık modeli kullanılırken daha az kısıtlayıcı bir ölçüt uygulamak seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f2111-199">You may also choose to apply less restrictive criteria when using an optimistic concurrency model.</span></span> <span data-ttu-id="f2111-200">Örneğin, WHERE yan tümcesi verilerin diğer sütunların itibaren son sorgu olup güncelleştirildi bağımsız olarak üzerine yazılmasına neden olur, yalnızca birincil anahtar sütunlarını kullanarak.</span><span class="sxs-lookup"><span data-stu-id="f2111-200">For example, using only the primary key columns in the WHERE clause causes the data to be overwritten regardless of whether the other columns have been updated since the last query.</span></span> <span data-ttu-id="f2111-201">WHERE yan tümcesi yalnızca belirli sütunlar için en son sorgulanan bu yana belirli alanları güncelleştirilmiş sürece üzerine yazmaya verilerde kaynaklanan de uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f2111-201">You can also apply a WHERE clause only to specific columns, resulting in data being overwritten unless particular fields have been updated since they were last queried.</span></span>  
  
### <a name="the-dataadapterrowupdated-event"></a><span data-ttu-id="f2111-202">DataAdapter.RowUpdated olayı</span><span class="sxs-lookup"><span data-stu-id="f2111-202">The DataAdapter.RowUpdated Event</span></span>  
 <span data-ttu-id="f2111-203">**RowUpdated** olayı <xref:System.Data.Common.DataAdapter> nesne iyimser eşzamanlılık ihlallerinin uygulamanıza bildirim sağlamak için daha önce açıklanan teknikleri ile birlikte kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f2111-203">The **RowUpdated** event of the <xref:System.Data.Common.DataAdapter> object can be used in conjunction with the techniques described earlier, to provide notification to your application of optimistic concurrency violations.</span></span> <span data-ttu-id="f2111-204">**RowUpdated** güncelleştirmek için her girişiminden sonra gerçekleşir bir **değiştirilen** öğesinden satır bir **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="f2111-204">**RowUpdated** occurs after each attempt to update a **Modified** row from a **DataSet**.</span></span> <span data-ttu-id="f2111-205">Bu özel durum oluştuğunda işleme, özel hata bilgilerini ekleme, yeniden deneme mantığı ekleme de dahil olmak üzere özel işleme kodu eklemenizi ve benzeri sağlar.</span><span class="sxs-lookup"><span data-stu-id="f2111-205">This enables you to add special handling code, including processing when an exception occurs, adding custom error information, adding retry logic, and so on.</span></span> <span data-ttu-id="f2111-206"><xref:System.Data.Common.RowUpdatedEventArgs> Nesnesi döndürür bir **RecordsAffected** bir tablodaki değiştirilmiş bir satır için belirli bir güncelleştirme komutu tarafından etkilenen satırların sayısını içeren özellik.</span><span class="sxs-lookup"><span data-stu-id="f2111-206">The <xref:System.Data.Common.RowUpdatedEventArgs> object returns a **RecordsAffected** property containing the number of rows affected by a particular update command for a modified row in a table.</span></span> <span data-ttu-id="f2111-207">İyimser eşzamanlılık için test etmek için güncelleştirme komutu ayarlayarak **RecordsAffected** özelliği sonuç olarak, döndürecektir 0 değeri iyimser eşzamanlılık ihlali oluştu, hiçbir kayıt güncelleştirilmediğinden.</span><span class="sxs-lookup"><span data-stu-id="f2111-207">By setting the update command to test for optimistic concurrency, the **RecordsAffected** property will, as a result, return a value of 0 when an optimistic concurrency violation has occurred, because no records were updated.</span></span> <span data-ttu-id="f2111-208">Bu durumda, bir özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="f2111-208">If this is the case, an exception is thrown.</span></span> <span data-ttu-id="f2111-209">**RowUpdated** olay sağlar, bu oluşumu işlemek ve uygun bir ayarlayarak özel durumu önlemek **RowUpdatedEventArgs.Status** gibi değerini  **UpdateStatus.SkipCurrentRow**.</span><span class="sxs-lookup"><span data-stu-id="f2111-209">The **RowUpdated** event enables you to handle this occurrence and avoid the exception by setting an appropriate **RowUpdatedEventArgs.Status** value, such as **UpdateStatus.SkipCurrentRow**.</span></span> <span data-ttu-id="f2111-210">Hakkında daha fazla bilgi için **RowUpdated** olayı bkz [olaylarını işleme](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).</span><span class="sxs-lookup"><span data-stu-id="f2111-210">For more information about the **RowUpdated** event, see [Handling DataAdapter Events](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).</span></span>  
  
 <span data-ttu-id="f2111-211">İsteğe bağlı olarak, ayarlayabileceğiniz **DataAdapter.ContinueUpdateOnError** için **true**, çağırmadan önce **güncelleştirme**ve depolananhatabilgileriniyanıtlar**RowError** belirli bir özellik satır **güncelleştirme** tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="f2111-211">Optionally, you can set **DataAdapter.ContinueUpdateOnError** to **true**, before calling **Update**, and respond to the error information stored in the **RowError** property of a particular row when the **Update** is completed.</span></span> <span data-ttu-id="f2111-212">Daha fazla bilgi için bkz: [satır hata bilgilerini](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-error-information.md).</span><span class="sxs-lookup"><span data-stu-id="f2111-212">For more information, see [Row Error Information](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-error-information.md).</span></span>  
  
## <a name="optimistic-concurrency-example"></a><span data-ttu-id="f2111-213">İyimser eşzamanlılık örneği</span><span class="sxs-lookup"><span data-stu-id="f2111-213">Optimistic Concurrency Example</span></span>  
 <span data-ttu-id="f2111-214">Aşağıdaki ayarlar basit bir örnektir **UpdateCommand** , bir **DataAdapter** iyimser eşzamanlılık için test etmek ve ardından **RowUpdated** sınamak için olay İyimser eşzamanlılık ihlali.</span><span class="sxs-lookup"><span data-stu-id="f2111-214">The following is a simple example that sets the **UpdateCommand** of a **DataAdapter** to test for optimistic concurrency, and then uses the **RowUpdated** event to test for optimistic concurrency violations.</span></span> <span data-ttu-id="f2111-215">İyimser eşzamanlılık ihlali karşılaşıldığında, uygulama ayarlar **RowError** güncelleştirme iyimser eşzamanlılık ihlali yansıtacak şekilde için verilmiş satır.</span><span class="sxs-lookup"><span data-stu-id="f2111-215">When an optimistic concurrency violation is encountered, the application sets the **RowError** of the row that the update was issued for to reflect an optimistic concurrency violation.</span></span>  
  
 <span data-ttu-id="f2111-216">GÜNCELLEŞTİRME komutu WHERE yan tümcesi geçirilen parametre değerlerini eşlendiği Not **özgün** ilgili sütun değerleri de.</span><span class="sxs-lookup"><span data-stu-id="f2111-216">Note that the parameter values passed to the WHERE clause of the UPDATE command are mapped to the **Original** values of their respective columns.</span></span>  
  
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
Dim parameter As SqlParameter = dataSet.UpdateCommand.Parameters.Add( _  
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
   "WHERE CustomerID = @oldCustomerID AND CompanyName = @oldCompanyName, connection);  
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
  
## <a name="see-also"></a><span data-ttu-id="f2111-217">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f2111-217">See Also</span></span>  
 [<span data-ttu-id="f2111-218">ADO.NET’te Veri Alma ve Değiştirme</span><span class="sxs-lookup"><span data-stu-id="f2111-218">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="f2111-219">Veri Kaynaklarını DataAdapters ile Güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="f2111-219">Updating Data Sources with DataAdapters</span></span>](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 [<span data-ttu-id="f2111-220">Satır Hatası Bilgileri</span><span class="sxs-lookup"><span data-stu-id="f2111-220">Row Error Information</span></span>](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-error-information.md)  
 [<span data-ttu-id="f2111-221">İşlemler ve Eşzamanlılık</span><span class="sxs-lookup"><span data-stu-id="f2111-221">Transactions and Concurrency</span></span>](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 [<span data-ttu-id="f2111-222">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="f2111-222">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
