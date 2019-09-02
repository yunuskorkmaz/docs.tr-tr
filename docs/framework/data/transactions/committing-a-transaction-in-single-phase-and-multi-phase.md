---
title: Tek Aşamalı ve Çok Aşamalı İşlem Gerçekleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 694ea153-e4db-41ae-96ac-9ac66dcb69a9
ms.openlocfilehash: 2abb9c13e9b0cb394546252e0e51e53c8ff9eefb
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70206003"
---
# <a name="committing-a-transaction-in-single-phase-and-multi-phase"></a><span data-ttu-id="55ede-102">Tek Aşamalı ve Çok Aşamalı İşlem Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="55ede-102">Committing a Transaction in Single-Phase and Multi-Phase</span></span>
<span data-ttu-id="55ede-103">Bir işlemde kullanılan her kaynak, eylemleri bir işlem Yöneticisi (TM) tarafından koordine edilen bir kaynak yöneticisi (RM) tarafından yönetilir.</span><span class="sxs-lookup"><span data-stu-id="55ede-103">Each resource used in a transaction is managed by a resource manager (RM), whose actions are coordinated by a transaction manager (TM).</span></span> <span data-ttu-id="55ede-104">[Kaynakları bir işlem konusunun katılımcıları olarak listelemek](enlisting-resources-as-participants-in-a-transaction.md) , bir kaynağın (veya birden fazla kaynağın) bir işlemde nasıl kaydedilebilir olduğunu tartışır.</span><span class="sxs-lookup"><span data-stu-id="55ede-104">The [Enlisting Resources as Participants in a Transaction](enlisting-resources-as-participants-in-a-transaction.md) topic discusses how a resource (or multiple resources) can be enlisted in a transaction.</span></span> <span data-ttu-id="55ede-105">Bu konu başlığı altında, işlem taahhüdünün kayıtlı kaynaklar arasında nasıl koordine edilebilir.</span><span class="sxs-lookup"><span data-stu-id="55ede-105">This topic discusses how transaction commitment can be coordinated among enlisted resources.</span></span>  
  
 <span data-ttu-id="55ede-106">İşlemin sonunda, uygulama, işlemi taahhüt veya geri alınacak şekilde ister.</span><span class="sxs-lookup"><span data-stu-id="55ede-106">At the end of the transaction, the application requests the transaction to be either committed or rolled back.</span></span> <span data-ttu-id="55ede-107">İşlem Yöneticisi, bazı kaynak yöneticilerinin işlemi geri almak için oylama yaparken yürütülmesi için oylama gibi riskleri ortadan kaldırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="55ede-107">The transaction manager must eliminate risks like some resource managers voting to commit while others voting to roll back the transaction.</span></span>  
  
 <span data-ttu-id="55ede-108">İşlem, birden fazla kaynak içeriyorsa, iki aşamalı bir işleme (2PC) uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="55ede-108">If your transaction involves more than one resource, you must perform a two-phase commit (2PC).</span></span> <span data-ttu-id="55ede-109">İki aşamalı tamamlama Protokolü (hazırlama aşaması ve yürütme aşaması), işlem sona erdiğinde tüm kaynaklardaki tüm değişikliklerin tamamen kaydedilmiş veya tam olarak geri alındığı durumlarda sağlar.</span><span class="sxs-lookup"><span data-stu-id="55ede-109">The two-phase commit protocol (the prepare phase and the commit phase) ensures that when the transaction ends, all changes to all resources are either totally committed or fully rolled back.</span></span> <span data-ttu-id="55ede-110">Tüm katılımcıları sonra sonucunu bildirilir.</span><span class="sxs-lookup"><span data-stu-id="55ede-110">All the participants are then informed of the final result.</span></span> <span data-ttu-id="55ede-111">İki aşamalı tamamlama protokolü hakkında ayrıntılı bir tartışma için lütfen "*işlem işleme: Kavramlar ve teknikler (veri yönetimi sistemlerde Morgan Kaumann serisi) ISBN: 1558601902*", Jim Gray tarafından yapılır.</span><span class="sxs-lookup"><span data-stu-id="55ede-111">For a detailed discussion of the two-phase commit protocol, please consult the book "*Transaction Processing : Concepts and Techniques (Morgan Kaufmann Series in Data Management Systems) ISBN:1558601902*" by Jim Gray.</span></span>  
  
 <span data-ttu-id="55ede-112">Ayrıca, tek aşamalı Işleme protokolüne bir parça ayırarak işlem performansını iyileştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="55ede-112">You can also optimize your transaction's performance by taking part in the Single Phase Commit protocol.</span></span> <span data-ttu-id="55ede-113">Daha fazla bilgi için bkz. [tek aşamalı tamamlama ve promotable tek aşamalı bildirimi kullanarak iyileştirme](optimization-spc-and-promotable-spn.md).</span><span class="sxs-lookup"><span data-stu-id="55ede-113">For more information, see [Optimization using Single Phase Commit and Promotable Single Phase Notification](optimization-spc-and-promotable-spn.md).</span></span>  
  
 <span data-ttu-id="55ede-114">Yalnızca bir işlemin sonucu hakkında bilgilendirilmek istiyorsanız ve oylama 'ye katılmak istemiyorsanız, <xref:System.Transactions.Transaction.TransactionCompleted> olaya kaydolmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="55ede-114">If you just want to be informed of a transaction's outcome, and do not want to participate in voting, you should register for the <xref:System.Transactions.Transaction.TransactionCompleted> event.</span></span>  
  
## <a name="two-phase-commit-2pc"></a><span data-ttu-id="55ede-115">İki aşamalı kayıt (2PC)</span><span class="sxs-lookup"><span data-stu-id="55ede-115">Two-phase Commit (2PC)</span></span>  
 <span data-ttu-id="55ede-116">İlk işlem aşamasında, işlem yöneticisi her bir işlemin kaydedilip edilmeyeceğini veya geri döndürülüp döndürülmeyeceğini anlamak için her bir kaynağı sorgular.</span><span class="sxs-lookup"><span data-stu-id="55ede-116">In the first transaction phase, the transaction manager queries each resource to determine whether a transaction should be committed or rolled back.</span></span> <span data-ttu-id="55ede-117">İkinci işlem aşamasında, işlem yöneticisi her bir kaynağa kendi sorgularının sonucunu bildirir ve gerekli temizleme işlemlerini gerçekleştirmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="55ede-117">In the second transaction phase, the transaction manager notifies each resource of the outcome of its queries, allowing it to perform any necessary cleanup.</span></span>  
  
 <span data-ttu-id="55ede-118">Bu tür bir işleme katılmak için bir kaynak yöneticisi, bir 2PC sırasında <xref:System.Transactions.IEnlistmentNotification> TM olarak çağrılan yöntemler sağlayan arabirimini uygulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="55ede-118">To participate in this kind of transaction, a resource manager must implement the <xref:System.Transactions.IEnlistmentNotification> interface, which provides methods that are called by the TM as notifications during a 2PC.</span></span>  <span data-ttu-id="55ede-119">Aşağıdaki örnek, bu tür uygulaması örneği gösterir.</span><span class="sxs-lookup"><span data-stu-id="55ede-119">The following sample shows an example of such implementation.</span></span>  
  
 [!code-csharp[Tx_Enlist#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/tx_enlist/cs/enlist.cs#2)]
 [!code-vb[Tx_Enlist#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/tx_enlist/vb/enlist.vb#2)]  
  
### <a name="prepare-phase-phase-1"></a><span data-ttu-id="55ede-120">Aşama (Aşama 1) hazırla</span><span class="sxs-lookup"><span data-stu-id="55ede-120">Prepare phase (Phase 1)</span></span>  
 <span data-ttu-id="55ede-121">Uygulamadan bir <xref:System.Transactions.CommittableTransaction.Commit%2A> istek alındıktan sonra, işlem yöneticisi her bir kaynağın üzerindeki oyunuzu almak için kaydedilen her bir kaynaktaki <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> yöntemini çağırarak her bir kayıtlı katılımcının hazırlama aşamasına başlar. işlem.</span><span class="sxs-lookup"><span data-stu-id="55ede-121">Upon receiving a <xref:System.Transactions.CommittableTransaction.Commit%2A> request from the application, the transaction manager begins the Prepare phase of all the enlisted participants by calling the <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> method on each enlisted resource, in order to obtain each resource's vote on the transaction.</span></span>  
  
 <span data-ttu-id="55ede-122">Uygular, Kaynak Yöneticisi <xref:System.Transactions.IEnlistmentNotification> arabirimi ilk uygulayan <xref:System.Transactions.IEnlistmentNotification.Prepare%28System.Transactions.PreparingEnlistment%29> yöntemi aşağıdaki basit örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="55ede-122">Your resource manager that implements the <xref:System.Transactions.IEnlistmentNotification> interface should first implement the <xref:System.Transactions.IEnlistmentNotification.Prepare%28System.Transactions.PreparingEnlistment%29> method as the following simple example shows.</span></span>  
  
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
  
 <span data-ttu-id="55ede-123">Dayanıklı Kaynak Yöneticisi bu çağrıyı aldığında, işlemin kurtarma bilgilerini ( <xref:System.Transactions.PreparingEnlistment.RecoveryInformation%2A> özelliği alarak kullanılabilir) ve işleme sırasında işlemi tamamlamak için hangi bilgilerin gerekli olduğunu günlüğe kaydetmelidir.</span><span class="sxs-lookup"><span data-stu-id="55ede-123">When the durable resource manager receives this call, it should log the transaction's recovery information (available by retrieving the <xref:System.Transactions.PreparingEnlistment.RecoveryInformation%2A> property) and whatever information is necessary to complete the transaction on commit.</span></span> <span data-ttu-id="55ede-124">Bu içinde yapılması gerekmez <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> yöntemi olduğundan RM iş parçacığı üzerinde bunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="55ede-124">This does not need to be performed within the <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> method because the RM can do this on a worker thread.</span></span>  
  
 <span data-ttu-id="55ede-125">RM bittiğinde kendi iş hazırlama, yürütme veya geri çağırarak için oy <xref:System.Transactions.PreparingEnlistment.Prepared%2A> veya <xref:System.Transactions.PreparingEnlistment.ForceRollback%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="55ede-125">When the RM has finished its prepare work, it should vote to commit or roll back by calling the <xref:System.Transactions.PreparingEnlistment.Prepared%2A> or <xref:System.Transactions.PreparingEnlistment.ForceRollback%2A> method.</span></span> <span data-ttu-id="55ede-126">Dikkat <xref:System.Transactions.PreparingEnlistment> sınıfından devralan bir <xref:System.Transactions.Enlistment.Done%2A> yönteminden <xref:System.Transactions.Enlistment> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="55ede-126">Notice that the <xref:System.Transactions.PreparingEnlistment> class inherits a <xref:System.Transactions.Enlistment.Done%2A> method from the <xref:System.Transactions.Enlistment> class.</span></span> <span data-ttu-id="55ede-127">Hazırlama aşamasında bu yöntemi <xref:System.Transactions.PreparingEnlistment> geri çağırmada çağırırsanız, TM 'ye bir salt okuma listesi olduğunu bildirir (diğer bir deyişle, işlem korumalı verileri okuyabilen ancak güncelleştireamayan kaynak yöneticileri) ve RM daha fazla bildirim almaz İşlem Yöneticisi 'nden, 2. aşama içindeki işlemin sonucuna göre.</span><span class="sxs-lookup"><span data-stu-id="55ede-127">If you call this method on the <xref:System.Transactions.PreparingEnlistment> callback during the Prepare phase, it informs the TM that it is a Read-Only enlistment (that is, resource managers that can read but cannot update transaction-protected data) and the RM receives no further notifications from the transaction manager as to the outcome of the transaction in phase 2.</span></span>  
  
 <span data-ttu-id="55ede-128">Uygulama, tüm kaynak yöneticileri oyladıktan <xref:System.Transactions.PreparingEnlistment.Prepared%2A>sonra işlemin başarılı taahhüdüne bildirilir.</span><span class="sxs-lookup"><span data-stu-id="55ede-128">The application is told of the successful commitment of the transaction after all the resource managers vote <xref:System.Transactions.PreparingEnlistment.Prepared%2A>.</span></span>  
  
### <a name="commit-phase-phase-2"></a><span data-ttu-id="55ede-129">Aşama (Aşama 2) Kaydet</span><span class="sxs-lookup"><span data-stu-id="55ede-129">Commit phase (Phase 2)</span></span>  
 <span data-ttu-id="55ede-130">İşlemin ikinci aşamasında, işlem yöneticisi tüm kaynak yöneticilerinden başarılı bir şekilde alırsa (1. aşama sonunda tüm kaynak yöneticileri çağırılır <xref:System.Transactions.PreparingEnlistment.Prepared%2A> ), her kaynak için <xref:System.Transactions.IEnlistmentNotification.Commit%2A> yöntemini çağırır Manager.</span><span class="sxs-lookup"><span data-stu-id="55ede-130">In the second phase of the transaction, if the transaction manager receives successful prepares from all the resource managers (all the resource managers have invoked <xref:System.Transactions.PreparingEnlistment.Prepared%2A> at the end of phase 1), it invokes the <xref:System.Transactions.IEnlistmentNotification.Commit%2A> method for each resource manager.</span></span> <span data-ttu-id="55ede-131">Kaynak yöneticileri ardından değişiklikleri kalıcı yapın ve yürütme tamamlayın.</span><span class="sxs-lookup"><span data-stu-id="55ede-131">The resource managers can then make the changes durable and complete the commit.</span></span>  
  
 <span data-ttu-id="55ede-132">Herhangi bir kaynak yöneticisi, 1. aşamada hazırlanmak üzere bir hata raporlamadıysanız, işlem <xref:System.Transactions.IEnlistmentNotification.Rollback%2A> Yöneticisi her kaynak yöneticisi için yöntemini çağırır ve uygulamaya yapılan işleme başarısızlığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="55ede-132">If any resource manager reported a failure to prepare in phase 1, the transaction manager invokes the <xref:System.Transactions.IEnlistmentNotification.Rollback%2A> method for each resource manager and indicates the failure of the commit to the application.</span></span>  
  
 <span data-ttu-id="55ede-133">Bu nedenle, kaynak yöneticisi aşağıdaki yöntemleri uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="55ede-133">Thus, your resource manager should implement the following methods.</span></span>  
  
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
  
 <span data-ttu-id="55ede-134">RM, bildirim türüne bağlı olarak işlemi tamamlamak için gereken herhangi bir çalışmayı gerçekleştirmelidir ve bu öğeyi, <xref:System.Transactions.Enlistment.Done%2A> <xref:System.Transactions.Enlistment> parametresindeki yöntemi çağırarak, TM 'yi bilgilendirir.</span><span class="sxs-lookup"><span data-stu-id="55ede-134">The RM should perform any work necessary to finish the transaction based on the notification type, and inform the TM that it has finished by calling <xref:System.Transactions.Enlistment.Done%2A> method on the <xref:System.Transactions.Enlistment> parameter.</span></span> <span data-ttu-id="55ede-135">Bu iş iş parçacığı üzerinde yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="55ede-135">This work can be done on a worker thread.</span></span> <span data-ttu-id="55ede-136">Satır içi çağrılır aynı iş parçacığı üzerinde Aşama 2 bildirimleri oluşabilir Not <xref:System.Transactions.PreparingEnlistment.Prepared%2A> yönteminde Aşama 1.</span><span class="sxs-lookup"><span data-stu-id="55ede-136">Note that the phase 2 notifications can happen inline on the same thread that called the <xref:System.Transactions.PreparingEnlistment.Prepared%2A> method in phase 1.</span></span> <span data-ttu-id="55ede-137">Bu nedenle, sonra herhangi bir iş yapmanız gerektiğini değil <xref:System.Transactions.PreparingEnlistment.Prepared%2A> Aşama 2 bildirimleri almadan önce tamamladınız beklediğiniz araması (örneğin, serbest bırakma kilitler).</span><span class="sxs-lookup"><span data-stu-id="55ede-137">As such, you should not do any work after the <xref:System.Transactions.PreparingEnlistment.Prepared%2A> call (for example, releasing locks) that you would expect to have completed before receiving the phase 2 notifications.</span></span>  
  
### <a name="implementing-indoubt"></a><span data-ttu-id="55ede-138">Nin şüpheli işlemi olmadığından uygulama</span><span class="sxs-lookup"><span data-stu-id="55ede-138">Implementing InDoubt</span></span>  
 <span data-ttu-id="55ede-139">Son olarak, uygulamalıdır <xref:System.Transactions.IEnlistmentNotification.InDoubt%2A> geçici kaynak yöneticisi için yöntem.</span><span class="sxs-lookup"><span data-stu-id="55ede-139">Finally, you should implement the <xref:System.Transactions.IEnlistmentNotification.InDoubt%2A> method for the volatile resource manager.</span></span> <span data-ttu-id="55ede-140">İşlem Yöneticisi bir veya daha fazla katılımcı ile iletişim kesilirse, durumu bilinmiyor olarak bu yöntem çağrılır.</span><span class="sxs-lookup"><span data-stu-id="55ede-140">This method is called if the transaction manager loses contact with one or more participants, so their status is unknown.</span></span> <span data-ttu-id="55ede-141">Bu durumda, daha sonra işlem katılımcılarının herhangi birinin tutarsız bir durumda bırakılmış olup olmadığı araştırabilmeniz için bu olguyu günlüğe yazmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="55ede-141">If this occurs, you should log this fact so that you can investigate later whether any of the transaction participants has been left in an inconsistent state.</span></span>  
  
```csharp
public void InDoubt (Enlistment enlistment)  
{  
     // log this  
     enlistment.Done();  
}  
```  
  
## <a name="single-phase-commit-optimization"></a><span data-ttu-id="55ede-142">Tek aşaması yürütme en iyi hale getirme</span><span class="sxs-lookup"><span data-stu-id="55ede-142">Single Phase Commit Optimization</span></span>  
 <span data-ttu-id="55ede-143">Tüm güncelleştirmeleri herhangi bir açık işbirliği yapıldığından tek aşaması yürütme Protokolü çalışma zamanında daha etkilidir.</span><span class="sxs-lookup"><span data-stu-id="55ede-143">The Single Phase Commit protocol is more efficient at run time because all updates are done without any explicit coordination.</span></span> <span data-ttu-id="55ede-144">Bu protokol hakkında daha fazla bilgi için bkz. [tek aşamalı tamamlama ve promotable tek aşamalı bildirimi kullanarak iyileştirme](optimization-spc-and-promotable-spn.md).</span><span class="sxs-lookup"><span data-stu-id="55ede-144">For more information on this protocol, see [Optimization using Single Phase Commit and Promotable Single Phase Notification](optimization-spc-and-promotable-spn.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55ede-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="55ede-145">See also</span></span>

- [<span data-ttu-id="55ede-146">Tek Aşamalı İşleme ve Yükseltilebilir Tek Aşamalı Bildirim kullanarak en iyi duruma getirme</span><span class="sxs-lookup"><span data-stu-id="55ede-146">Optimization using Single Phase Commit and Promotable Single Phase Notification</span></span>](optimization-spc-and-promotable-spn.md)
- [<span data-ttu-id="55ede-147">Bir İşlemde Kaynakları Katılımcı Olarak Kaydetme</span><span class="sxs-lookup"><span data-stu-id="55ede-147">Enlisting Resources as Participants in a Transaction</span></span>](enlisting-resources-as-participants-in-a-transaction.md)
