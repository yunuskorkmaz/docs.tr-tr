---
title: Tek Aşamalı ve Çok Aşamalı İşlem Gerçekleştirme
description: .NET 'teki bir veya iki aşamada işlem yürütme hakkında bilgi edinin. İşlem birden fazla kaynak içeriyorsa, iki aşamalı bir işleme (2PC) gerçekleştirilmesi gerekir.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 694ea153-e4db-41ae-96ac-9ac66dcb69a9
ms.openlocfilehash: 2f4486998f347bf1db6d22433e6e48b553609c18
ms.sourcegitcommit: 6219b1e1feccb16d88656444210fed3297f5611e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/22/2020
ms.locfileid: "85141830"
---
# <a name="committing-a-transaction-in-single-phase-and-multi-phase"></a><span data-ttu-id="50845-104">Tek Aşamalı ve Çok Aşamalı İşlem Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="50845-104">Committing a Transaction in Single-Phase and Multi-Phase</span></span>
<span data-ttu-id="50845-105">Bir işlemde kullanılan her kaynak, eylemleri bir işlem Yöneticisi (TM) tarafından koordine edilen bir kaynak yöneticisi (RM) tarafından yönetilir.</span><span class="sxs-lookup"><span data-stu-id="50845-105">Each resource used in a transaction is managed by a resource manager (RM), whose actions are coordinated by a transaction manager (TM).</span></span> <span data-ttu-id="50845-106">[Kaynakları bir işlem konusunun katılımcıları olarak listelemek](enlisting-resources-as-participants-in-a-transaction.md) , bir kaynağın (veya birden fazla kaynağın) bir işlemde nasıl kaydedilebilir olduğunu tartışır.</span><span class="sxs-lookup"><span data-stu-id="50845-106">The [Enlisting Resources as Participants in a Transaction](enlisting-resources-as-participants-in-a-transaction.md) topic discusses how a resource (or multiple resources) can be enlisted in a transaction.</span></span> <span data-ttu-id="50845-107">Bu konu başlığı altında, işlem taahhüdünün kayıtlı kaynaklar arasında nasıl koordine edilebilir.</span><span class="sxs-lookup"><span data-stu-id="50845-107">This topic discusses how transaction commitment can be coordinated among enlisted resources.</span></span>  
  
 <span data-ttu-id="50845-108">İşlemin sonunda, uygulama, işlemi taahhüt veya geri alınacak şekilde ister.</span><span class="sxs-lookup"><span data-stu-id="50845-108">At the end of the transaction, the application requests the transaction to be either committed or rolled back.</span></span> <span data-ttu-id="50845-109">İşlem Yöneticisi, bazı kaynak yöneticilerinin işlemi geri almak için oylama yaparken yürütülmesi için oylama gibi riskleri ortadan kaldırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="50845-109">The transaction manager must eliminate risks like some resource managers voting to commit while others voting to roll back the transaction.</span></span>  
  
 <span data-ttu-id="50845-110">İşlem, birden fazla kaynak içeriyorsa, iki aşamalı bir işleme (2PC) uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="50845-110">If your transaction involves more than one resource, you must perform a two-phase commit (2PC).</span></span> <span data-ttu-id="50845-111">İki aşamalı tamamlama Protokolü (hazırlama aşaması ve yürütme aşaması), işlem sona erdiğinde tüm kaynaklardaki tüm değişikliklerin tamamen kaydedilmiş veya tam olarak geri alındığı durumlarda sağlar.</span><span class="sxs-lookup"><span data-stu-id="50845-111">The two-phase commit protocol (the prepare phase and the commit phase) ensures that when the transaction ends, all changes to all resources are either totally committed or fully rolled back.</span></span> <span data-ttu-id="50845-112">Tüm katılımcıları sonra sonucunu bildirilir.</span><span class="sxs-lookup"><span data-stu-id="50845-112">All the participants are then informed of the final result.</span></span> <span data-ttu-id="50845-113">İki aşamalı tamamlama protokolü hakkında ayrıntılı bir tartışma için lütfen "*Işlem işleme: kavramlar ve teknikler (veri yönetimi sistemlerdeki Morgan Kaumann serisi) ISBN: 1558601902*" adlı Jim Gray adlı kitaba bakın.</span><span class="sxs-lookup"><span data-stu-id="50845-113">For a detailed discussion of the two-phase commit protocol, please consult the book "*Transaction Processing : Concepts and Techniques (Morgan Kaufmann Series in Data Management Systems) ISBN:1558601902*" by Jim Gray.</span></span>  
  
 <span data-ttu-id="50845-114">Ayrıca, tek aşamalı Işleme protokolüne bir parça ayırarak işlem performansını iyileştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50845-114">You can also optimize your transaction's performance by taking part in the Single Phase Commit protocol.</span></span> <span data-ttu-id="50845-115">Daha fazla bilgi için bkz. [tek aşamalı tamamlama ve promotable tek aşamalı bildirimi kullanarak iyileştirme](optimization-spc-and-promotable-spn.md).</span><span class="sxs-lookup"><span data-stu-id="50845-115">For more information, see [Optimization using Single Phase Commit and Promotable Single Phase Notification](optimization-spc-and-promotable-spn.md).</span></span>  
  
 <span data-ttu-id="50845-116">Yalnızca bir işlemin sonucu hakkında bilgilendirilmek istiyorsanız ve oylama 'ye katılmak istemiyorsanız, olaya kaydolmanız gerekir <xref:System.Transactions.Transaction.TransactionCompleted> .</span><span class="sxs-lookup"><span data-stu-id="50845-116">If you just want to be informed of a transaction's outcome, and do not want to participate in voting, you should register for the <xref:System.Transactions.Transaction.TransactionCompleted> event.</span></span>  
  
## <a name="two-phase-commit-2pc"></a><span data-ttu-id="50845-117">İki aşamalı kayıt (2PC)</span><span class="sxs-lookup"><span data-stu-id="50845-117">Two-phase Commit (2PC)</span></span>  
 <span data-ttu-id="50845-118">İlk işlem aşamasında, işlem yöneticisi her bir işlemin kaydedilip edilmeyeceğini veya geri döndürülüp döndürülmeyeceğini anlamak için her bir kaynağı sorgular.</span><span class="sxs-lookup"><span data-stu-id="50845-118">In the first transaction phase, the transaction manager queries each resource to determine whether a transaction should be committed or rolled back.</span></span> <span data-ttu-id="50845-119">İkinci işlem aşamasında, işlem yöneticisi her bir kaynağa kendi sorgularının sonucunu bildirir ve gerekli temizleme işlemlerini gerçekleştirmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="50845-119">In the second transaction phase, the transaction manager notifies each resource of the outcome of its queries, allowing it to perform any necessary cleanup.</span></span>  
  
 <span data-ttu-id="50845-120">Bu tür bir işleme katılmak için bir kaynak yöneticisi, <xref:System.Transactions.IEnlistmentNotification> BIR 2PC SıRASıNDA TM olarak çağrılan yöntemler sağlayan arabirimini uygulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="50845-120">To participate in this kind of transaction, a resource manager must implement the <xref:System.Transactions.IEnlistmentNotification> interface, which provides methods that are called by the TM as notifications during a 2PC.</span></span>  <span data-ttu-id="50845-121">Aşağıdaki örnek, bu tür uygulaması örneği gösterir.</span><span class="sxs-lookup"><span data-stu-id="50845-121">The following sample shows an example of such implementation.</span></span>  
  
 [!code-csharp[Tx_Enlist#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/tx_enlist/cs/enlist.cs#2)]
 [!code-vb[Tx_Enlist#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/tx_enlist/vb/enlist.vb#2)]  
  
### <a name="prepare-phase-phase-1"></a><span data-ttu-id="50845-122">Aşama (Aşama 1) hazırla</span><span class="sxs-lookup"><span data-stu-id="50845-122">Prepare phase (Phase 1)</span></span>  
 <span data-ttu-id="50845-123">Uygulamadan bir istek alındıktan sonra <xref:System.Transactions.CommittableTransaction.Commit%2A> , işlem yöneticisi <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> her bir kaynağın işlem üzerindeki oylamasını elde etmek için, her bir kayıtlı kaynaktaki yöntemini çağırarak, tüm kayıtlı katılımcıların hazırlama aşamasına başlar.</span><span class="sxs-lookup"><span data-stu-id="50845-123">Upon receiving a <xref:System.Transactions.CommittableTransaction.Commit%2A> request from the application, the transaction manager begins the Prepare phase of all the enlisted participants by calling the <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> method on each enlisted resource, in order to obtain each resource's vote on the transaction.</span></span>  
  
 <span data-ttu-id="50845-124">Uygular, Kaynak Yöneticisi <xref:System.Transactions.IEnlistmentNotification> arabirimi ilk uygulayan <xref:System.Transactions.IEnlistmentNotification.Prepare%28System.Transactions.PreparingEnlistment%29> yöntemi aşağıdaki basit örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="50845-124">Your resource manager that implements the <xref:System.Transactions.IEnlistmentNotification> interface should first implement the <xref:System.Transactions.IEnlistmentNotification.Prepare%28System.Transactions.PreparingEnlistment%29> method as the following simple example shows.</span></span>  
  
```csharp
public void Prepare(PreparingEnlistment preparingEnlistment)  
{  
     Console.WriteLine("Prepare notification received");  
     //Perform work  
  
     Console.Write("reply with prepared? [Y|N] ");  
     c = Console.ReadKey();  
     Console.WriteLine();  
  
     //If work finished correctly, reply with prepared  
     if ((c.KeyChar == 'Y') || (c.KeyChar == 'y'))  
     {  
          preparingEnlistment.Prepared();  
          break;  
     }  
  
     // otherwise, do a ForceRollback  
     else if ((c.KeyChar == 'N') || (c.KeyChar == 'n'))  
     {  
          preparingEnlistment.ForceRollback();  
          break;  
     }  
}  
```  
  
 <span data-ttu-id="50845-125">Dayanıklı Kaynak Yöneticisi bu çağrıyı aldığında, işlemin kurtarma bilgilerini (özelliği alarak kullanılabilir <xref:System.Transactions.PreparingEnlistment.RecoveryInformation%2A> ) ve işleme sırasında işlemi tamamlamak için hangi bilgilerin gerekli olduğunu günlüğe kaydetmelidir.</span><span class="sxs-lookup"><span data-stu-id="50845-125">When the durable resource manager receives this call, it should log the transaction's recovery information (available by retrieving the <xref:System.Transactions.PreparingEnlistment.RecoveryInformation%2A> property) and whatever information is necessary to complete the transaction on commit.</span></span> <span data-ttu-id="50845-126">Bu içinde yapılması gerekmez <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> yöntemi olduğundan RM iş parçacığı üzerinde bunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50845-126">This does not need to be performed within the <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> method because the RM can do this on a worker thread.</span></span>  
  
 <span data-ttu-id="50845-127">RM bittiğinde kendi iş hazırlama, yürütme veya geri çağırarak için oy <xref:System.Transactions.PreparingEnlistment.Prepared%2A> veya <xref:System.Transactions.PreparingEnlistment.ForceRollback%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="50845-127">When the RM has finished its prepare work, it should vote to commit or roll back by calling the <xref:System.Transactions.PreparingEnlistment.Prepared%2A> or <xref:System.Transactions.PreparingEnlistment.ForceRollback%2A> method.</span></span> <span data-ttu-id="50845-128">Dikkat <xref:System.Transactions.PreparingEnlistment> sınıfından devralan bir <xref:System.Transactions.Enlistment.Done%2A> yönteminden <xref:System.Transactions.Enlistment> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="50845-128">Notice that the <xref:System.Transactions.PreparingEnlistment> class inherits a <xref:System.Transactions.Enlistment.Done%2A> method from the <xref:System.Transactions.Enlistment> class.</span></span> <span data-ttu-id="50845-129"><xref:System.Transactions.PreparingEnlistment>Hazırlama aşamasında bu yöntemi geri çağırmada çağırırsanız, TM 'ye bir salt okuma listesi olduğunu bildirir (yani, işlem korumalı verileri okuyabilen ancak güncelleştiremediğini belirten kaynak yöneticileri) ve RM, işlem yöneticisi 'nden, Aşama 2 ' deki işlemin sonucuna göre başka hiçbir bildirim almaz.</span><span class="sxs-lookup"><span data-stu-id="50845-129">If you call this method on the <xref:System.Transactions.PreparingEnlistment> callback during the Prepare phase, it informs the TM that it is a Read-Only enlistment (that is, resource managers that can read but cannot update transaction-protected data) and the RM receives no further notifications from the transaction manager as to the outcome of the transaction in phase 2.</span></span>  
  
 <span data-ttu-id="50845-130">Uygulama, tüm kaynak yöneticileri oyladıktan sonra işlemin başarılı taahhüdüne bildirilir <xref:System.Transactions.PreparingEnlistment.Prepared%2A> .</span><span class="sxs-lookup"><span data-stu-id="50845-130">The application is told of the successful commitment of the transaction after all the resource managers vote <xref:System.Transactions.PreparingEnlistment.Prepared%2A>.</span></span>  
  
### <a name="commit-phase-phase-2"></a><span data-ttu-id="50845-131">Aşama (Aşama 2) Kaydet</span><span class="sxs-lookup"><span data-stu-id="50845-131">Commit phase (Phase 2)</span></span>  
 <span data-ttu-id="50845-132">İşlemin ikinci aşamasında, işlem yöneticisi tüm kaynak yöneticilerinden başarılı bir şekilde alırsa (1. aşama sonunda tüm kaynak yöneticileri çağırılır <xref:System.Transactions.PreparingEnlistment.Prepared%2A> ), <xref:System.Transactions.IEnlistmentNotification.Commit%2A> her kaynak yöneticisi için yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="50845-132">In the second phase of the transaction, if the transaction manager receives successful prepares from all the resource managers (all the resource managers have invoked <xref:System.Transactions.PreparingEnlistment.Prepared%2A> at the end of phase 1), it invokes the <xref:System.Transactions.IEnlistmentNotification.Commit%2A> method for each resource manager.</span></span> <span data-ttu-id="50845-133">Kaynak yöneticileri ardından değişiklikleri kalıcı yapın ve yürütme tamamlayın.</span><span class="sxs-lookup"><span data-stu-id="50845-133">The resource managers can then make the changes durable and complete the commit.</span></span>  
  
 <span data-ttu-id="50845-134">Herhangi bir kaynak yöneticisi, 1. aşamada hazırlanmak üzere bir hata raporlamadıysanız, işlem yöneticisi <xref:System.Transactions.IEnlistmentNotification.Rollback%2A> her kaynak yöneticisi için yöntemini çağırır ve uygulamaya yapılan işleme başarısızlığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="50845-134">If any resource manager reported a failure to prepare in phase 1, the transaction manager invokes the <xref:System.Transactions.IEnlistmentNotification.Rollback%2A> method for each resource manager and indicates the failure of the commit to the application.</span></span>  
  
 <span data-ttu-id="50845-135">Bu nedenle, kaynak yöneticisi aşağıdaki yöntemleri uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="50845-135">Thus, your resource manager should implement the following methods.</span></span>  
  
```csharp
public void Commit (Enlistment enlistment)  
{  
     // Do any work necessary when commit notification is received  
  
     // Declare done on the enlistment  
     enlistment.Done();  
}  
  
public void Rollback (Enlistment enlistment)  
{  
     // Do any work necessary when rollback notification is received  
  
     // Declare done on the enlistment
     enlistment.Done();
}  
```  
  
 <span data-ttu-id="50845-136">RM, bildirim türüne bağlı olarak işlemi tamamlamak için gereken herhangi bir çalışmayı gerçekleştirmelidir ve bu öğeyi, parametresindeki yöntemi çağırarak, TM 'yi bilgilendirir <xref:System.Transactions.Enlistment.Done%2A> <xref:System.Transactions.Enlistment> .</span><span class="sxs-lookup"><span data-stu-id="50845-136">The RM should perform any work necessary to finish the transaction based on the notification type, and inform the TM that it has finished by calling <xref:System.Transactions.Enlistment.Done%2A> method on the <xref:System.Transactions.Enlistment> parameter.</span></span> <span data-ttu-id="50845-137">Bu iş iş parçacığı üzerinde yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="50845-137">This work can be done on a worker thread.</span></span> <span data-ttu-id="50845-138">Satır içi çağrılır aynı iş parçacığı üzerinde Aşama 2 bildirimleri oluşabilir Not <xref:System.Transactions.PreparingEnlistment.Prepared%2A> yönteminde Aşama 1.</span><span class="sxs-lookup"><span data-stu-id="50845-138">Note that the phase 2 notifications can happen inline on the same thread that called the <xref:System.Transactions.PreparingEnlistment.Prepared%2A> method in phase 1.</span></span> <span data-ttu-id="50845-139">Bu nedenle, sonra herhangi bir iş yapmanız gerektiğini değil <xref:System.Transactions.PreparingEnlistment.Prepared%2A> Aşama 2 bildirimleri almadan önce tamamladınız beklediğiniz araması (örneğin, serbest bırakma kilitler).</span><span class="sxs-lookup"><span data-stu-id="50845-139">As such, you should not do any work after the <xref:System.Transactions.PreparingEnlistment.Prepared%2A> call (for example, releasing locks) that you would expect to have completed before receiving the phase 2 notifications.</span></span>  
  
### <a name="implementing-indoubt"></a><span data-ttu-id="50845-140">Nin şüpheli işlemi olmadığından uygulama</span><span class="sxs-lookup"><span data-stu-id="50845-140">Implementing InDoubt</span></span>  
 <span data-ttu-id="50845-141">Son olarak, uygulamalıdır <xref:System.Transactions.IEnlistmentNotification.InDoubt%2A> geçici kaynak yöneticisi için yöntem.</span><span class="sxs-lookup"><span data-stu-id="50845-141">Finally, you should implement the <xref:System.Transactions.IEnlistmentNotification.InDoubt%2A> method for the volatile resource manager.</span></span> <span data-ttu-id="50845-142">İşlem Yöneticisi bir veya daha fazla katılımcı ile iletişim kesilirse, durumu bilinmiyor olarak bu yöntem çağrılır.</span><span class="sxs-lookup"><span data-stu-id="50845-142">This method is called if the transaction manager loses contact with one or more participants, so their status is unknown.</span></span> <span data-ttu-id="50845-143">Bu durumda, daha sonra işlem katılımcılarının herhangi birinin tutarsız bir durumda bırakılmış olup olmadığı araştırabilmeniz için bu olguyu günlüğe yazmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="50845-143">If this occurs, you should log this fact so that you can investigate later whether any of the transaction participants has been left in an inconsistent state.</span></span>  
  
```csharp
public void InDoubt (Enlistment enlistment)  
{  
     // log this  
     enlistment.Done();  
}  
```  
  
## <a name="single-phase-commit-optimization"></a><span data-ttu-id="50845-144">Tek aşaması yürütme en iyi hale getirme</span><span class="sxs-lookup"><span data-stu-id="50845-144">Single Phase Commit Optimization</span></span>  
 <span data-ttu-id="50845-145">Tüm güncelleştirmeleri herhangi bir açık işbirliği yapıldığından tek aşaması yürütme Protokolü çalışma zamanında daha etkilidir.</span><span class="sxs-lookup"><span data-stu-id="50845-145">The Single Phase Commit protocol is more efficient at run time because all updates are done without any explicit coordination.</span></span> <span data-ttu-id="50845-146">Bu protokol hakkında daha fazla bilgi için bkz. [tek aşamalı tamamlama ve promotable tek aşamalı bildirimi kullanarak iyileştirme](optimization-spc-and-promotable-spn.md).</span><span class="sxs-lookup"><span data-stu-id="50845-146">For more information on this protocol, see [Optimization using Single Phase Commit and Promotable Single Phase Notification](optimization-spc-and-promotable-spn.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50845-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="50845-147">See also</span></span>

- [<span data-ttu-id="50845-148">Tek Aşamalı İşleme ve Yükseltilebilir Tek Aşamalı Bildirim kullanarak en iyi duruma getirme</span><span class="sxs-lookup"><span data-stu-id="50845-148">Optimization using Single Phase Commit and Promotable Single Phase Notification</span></span>](optimization-spc-and-promotable-spn.md)
- [<span data-ttu-id="50845-149">Bir İşlemde Kaynakları Katılımcı Olarak Kaydetme</span><span class="sxs-lookup"><span data-stu-id="50845-149">Enlisting Resources as Participants in a Transaction</span></span>](enlisting-resources-as-participants-in-a-transaction.md)
