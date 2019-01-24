---
title: Tek aşamalı ve çok aşamalı bir işlem Sistemi'ne
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 694ea153-e4db-41ae-96ac-9ac66dcb69a9
ms.openlocfilehash: e90a2f9c5681ffddb2a3ca0312bdd2f3f4078328
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54589525"
---
# <a name="committing-a-transaction-in-single-phase-and-multi-phase"></a><span data-ttu-id="0b8e0-102">Tek aşamalı ve çok aşamalı bir işlem Sistemi'ne</span><span class="sxs-lookup"><span data-stu-id="0b8e0-102">Committing a Transaction in Single-Phase and Multi-Phase</span></span>
<span data-ttu-id="0b8e0-103">Bir işlemde kullanılan her kaynak eylemlerini bir işlem yöneticisi (TM) düzenlenir Kaynak Yöneticisi (RM) tarafından yönetilir.</span><span class="sxs-lookup"><span data-stu-id="0b8e0-103">Each resource used in a transaction is managed by a resource manager (RM), whose actions are coordinated by a transaction manager (TM).</span></span> <span data-ttu-id="0b8e0-104">[Katılımcı bir işlemde kaynakları kaydetme](../../../../docs/framework/data/transactions/enlisting-resources-as-participants-in-a-transaction.md) konu açıklar bir kaynak (veya birden fazla kaynak) bir işlemde nasıl kaydedilebilir.</span><span class="sxs-lookup"><span data-stu-id="0b8e0-104">The [Enlisting Resources as Participants in a Transaction](../../../../docs/framework/data/transactions/enlisting-resources-as-participants-in-a-transaction.md) topic discusses how a resource (or multiple resources) can be enlisted in a transaction.</span></span> <span data-ttu-id="0b8e0-105">Bu konu nasıl işlem taahhüt kayıtlı kaynakları arasında Eşgüdümlü olabileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="0b8e0-105">This topic discusses how transaction commitment can be coordinated among enlisted resources.</span></span>  
  
 <span data-ttu-id="0b8e0-106">İşlemin sonunda, uygulama ya da kaydedilmiş veya geri için işlem ister.</span><span class="sxs-lookup"><span data-stu-id="0b8e0-106">At the end of the transaction, the application requests the transaction to be either committed or rolled back.</span></span> <span data-ttu-id="0b8e0-107">Bazı kaynak yöneticileri tamamlamaya oylama başkalarının çalışırken gibi hareket yöneticisi riskleri ortadan işlem geri dönmek için işaretleme.</span><span class="sxs-lookup"><span data-stu-id="0b8e0-107">The transaction manager must eliminate risks like some resource managers voting to commit while others voting to roll back the transaction.</span></span>  
  
 <span data-ttu-id="0b8e0-108">İşlem birden fazla kaynak içeriyorsa, iki aşamalı bir kayıt (2PC) gerçekleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="0b8e0-108">If your transaction involves more than one resource, you must perform a two-phase commit (2PC).</span></span> <span data-ttu-id="0b8e0-109">İki aşamalı tamamlama Protokolü (Hazırlık aşaması ve Tamamlama aşaması) işlem sona erdiğinde, tüm değişiklikleri tüm kaynaklara ya da tamamen kaydedilmiş veya tam döndürülmesine sağlar.</span><span class="sxs-lookup"><span data-stu-id="0b8e0-109">The two-phase commit protocol (the prepare phase and the commit phase) ensures that when the transaction ends, all changes to all resources are either totally committed or fully rolled back.</span></span> <span data-ttu-id="0b8e0-110">Tüm katılımcıları sonra sonucunu bildirilir.</span><span class="sxs-lookup"><span data-stu-id="0b8e0-110">All the participants are then informed of the final result.</span></span> <span data-ttu-id="0b8e0-111">İki aşamalı tamamlama protokolü hakkında ayrıntılı bilgi için lütfen kitap başvurun "*işlem: Kavramları ve teknikleri (Morgan Kaufmann dizide veri yönetim sistemleri) ISBN: 1558601902*"Jim gri tarafından.</span><span class="sxs-lookup"><span data-stu-id="0b8e0-111">For a detailed discussion of the two-phase commit protocol, please consult the book "*Transaction Processing : Concepts and Techniques (Morgan Kaufmann Series in Data Management Systems) ISBN:1558601902*" by Jim Gray.</span></span>  
  
 <span data-ttu-id="0b8e0-112">Ayrıca, tek aşaması yürütme Protokolü bölümü gerçekleştirerek, hareketin performans iyileştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0b8e0-112">You can also optimize your transaction's performance by taking part in the Single Phase Commit protocol.</span></span> <span data-ttu-id="0b8e0-113">Daha fazla bilgi için [tek aşamalı işleme ve yükseltilebilir tek aşamalı bildirim kullanarak en iyi duruma getirme](../../../../docs/framework/data/transactions/optimization-spc-and-promotable-spn.md).</span><span class="sxs-lookup"><span data-stu-id="0b8e0-113">For more information, see [Optimization using Single Phase Commit and Promotable Single Phase Notification](../../../../docs/framework/data/transactions/optimization-spc-and-promotable-spn.md).</span></span>  
  
 <span data-ttu-id="0b8e0-114">Yalnızca bir hareketin sonucu haberdar olmak istiyor ve oylama katılmak istiyor musunuz, kaydedin <xref:System.Transactions.Transaction.TransactionCompleted> olay.</span><span class="sxs-lookup"><span data-stu-id="0b8e0-114">If you just want to be informed of a transaction's outcome, and do not want to participate in voting, you should register for the <xref:System.Transactions.Transaction.TransactionCompleted> event.</span></span>  
  
## <a name="two-phase-commit-2pc"></a><span data-ttu-id="0b8e0-115">İki aşamalı kayıt (2PC)</span><span class="sxs-lookup"><span data-stu-id="0b8e0-115">Two-phase Commit (2PC)</span></span>  
 <span data-ttu-id="0b8e0-116">İlk işlem aşamasında hareket yöneticisi bir hareketin kaydedilmiş veya geri olup olmadığını belirlemek için her kaynak sorgular.</span><span class="sxs-lookup"><span data-stu-id="0b8e0-116">In the first transaction phase, the transaction manager queries each resource to determine whether a transaction should be committed or rolled back.</span></span> <span data-ttu-id="0b8e0-117">İkinci işlem aşamasında, gerekli tüm temizlemesi gerçekleştirin izin veren hareket yöneticisi her kaynak kendi sorgu sonucunun uyarır.</span><span class="sxs-lookup"><span data-stu-id="0b8e0-117">In the second transaction phase, the transaction manager notifies each resource of the outcome of its queries, allowing it to perform any necessary cleanup.</span></span>  
  
 <span data-ttu-id="0b8e0-118">Bu tür bir işlem katılmak için bir kaynak yöneticisi uygulamalıdır <xref:System.Transactions.IEnlistmentNotification> arabirimi, tarafından TM sırasında bir 2PC bildirimleri olarak adlandırılır yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="0b8e0-118">To participate in this kind of transaction, a resource manager must implement the <xref:System.Transactions.IEnlistmentNotification> interface, which provides methods that are called by the TM as notifications during a 2PC.</span></span>  <span data-ttu-id="0b8e0-119">Aşağıdaki örnek, bu tür uygulaması örneği gösterir.</span><span class="sxs-lookup"><span data-stu-id="0b8e0-119">The following sample shows an example of such implementation.</span></span>  
  
 [!code-csharp[Tx_Enlist#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/tx_enlist/cs/enlist.cs#2)]
 [!code-vb[Tx_Enlist#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/tx_enlist/vb/enlist.vb#2)]  
  
### <a name="prepare-phase-phase-1"></a><span data-ttu-id="0b8e0-120">Aşama (Aşama 1) hazırla</span><span class="sxs-lookup"><span data-stu-id="0b8e0-120">Prepare phase (Phase 1)</span></span>  
 <span data-ttu-id="0b8e0-121">Alma bağlı bir <xref:System.Transactions.CommittableTransaction.Commit%2A> istek uygulamadan hareket yöneticisi çağırarak kayıtlı tüm katılımcıları hazırla aşaması başlar <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> yöntemi her kayıtlı kaynak, her kaynak almak için kullanıcının oy kullanın işlem.</span><span class="sxs-lookup"><span data-stu-id="0b8e0-121">Upon receiving a <xref:System.Transactions.CommittableTransaction.Commit%2A> request from the application, the transaction manager begins the Prepare phase of all the enlisted participants by calling the <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> method on each enlisted resource, in order to obtain each resource's vote on the transaction.</span></span>  
  
 <span data-ttu-id="0b8e0-122">Uygular, Kaynak Yöneticisi <xref:System.Transactions.IEnlistmentNotification> arabirimi ilk uygulayan <xref:System.Transactions.IEnlistmentNotification.Prepare%28System.Transactions.PreparingEnlistment%29> yöntemi aşağıdaki basit örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="0b8e0-122">Your resource manager that implements the <xref:System.Transactions.IEnlistmentNotification> interface should first implement the <xref:System.Transactions.IEnlistmentNotification.Prepare%28System.Transactions.PreparingEnlistment%29> method as the following simple example shows.</span></span>  
  
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
  
 <span data-ttu-id="0b8e0-123">Kalıcı kaynak yöneticisi bu çağrı aldığında, hareketin kurtarma bilgilerini kapatması gerekir (alarak kullanılabilir <xref:System.Transactions.PreparingEnlistment.RecoveryInformation%2A> özelliği) ve hangi bilgileri üzerindeki kaydetme işlemi tamamlamak gereklidir.</span><span class="sxs-lookup"><span data-stu-id="0b8e0-123">When the durable resource manager receives this call, it should log the transaction's recovery information (available by retrieving the <xref:System.Transactions.PreparingEnlistment.RecoveryInformation%2A> property) and whatever information is necessary to complete the transaction on commit.</span></span> <span data-ttu-id="0b8e0-124">Bu içinde yapılması gerekmez <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> yöntemi olduğundan RM iş parçacığı üzerinde bunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0b8e0-124">This does not need to be performed within the <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> method because the RM can do this on a worker thread.</span></span>  
  
 <span data-ttu-id="0b8e0-125">RM bittiğinde kendi iş hazırlama, yürütme veya geri çağırarak için oy <xref:System.Transactions.PreparingEnlistment.Prepared%2A> veya <xref:System.Transactions.PreparingEnlistment.ForceRollback%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0b8e0-125">When the RM has finished its prepare work, it should vote to commit or roll back by calling the <xref:System.Transactions.PreparingEnlistment.Prepared%2A> or <xref:System.Transactions.PreparingEnlistment.ForceRollback%2A> method.</span></span> <span data-ttu-id="0b8e0-126">Dikkat <xref:System.Transactions.PreparingEnlistment> sınıfından devralan bir <xref:System.Transactions.Enlistment.Done%2A> yönteminden <xref:System.Transactions.Enlistment> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="0b8e0-126">Notice that the <xref:System.Transactions.PreparingEnlistment> class inherits a <xref:System.Transactions.Enlistment.Done%2A> method from the <xref:System.Transactions.Enlistment> class.</span></span> <span data-ttu-id="0b8e0-127">Bu yöntem çağırırsanız <xref:System.Transactions.PreparingEnlistment> geri çağırma hazırla aşamasında, onu bildiren TM salt okunur bir liste (okuyabilirsiniz ancak işlem korunan verileri güncelleştiremiyor diğer bir deyişle, kaynak yöneticileri) olduğunu ve daha fazla bildirim RM alır İşlem Yöneticisi'nden işlem sırasında Aşama 2 sonucunu için farklı.</span><span class="sxs-lookup"><span data-stu-id="0b8e0-127">If you call this method on the <xref:System.Transactions.PreparingEnlistment> callback during the Prepare phase, it informs the TM that it is a Read-Only enlistment (that is, resource managers that can read but cannot update transaction-protected data) and the RM receives no further notifications from the transaction manager as to the outcome of the transaction in phase 2.</span></span>  
  
 <span data-ttu-id="0b8e0-128">Tüm kaynak yöneticileri oy sonra uygulama işlemin başarılı taahhüt bildirilir <xref:System.Transactions.PreparingEnlistment.Prepared%2A>.</span><span class="sxs-lookup"><span data-stu-id="0b8e0-128">The application is told of the successful commitment of the transaction after all the resource managers vote <xref:System.Transactions.PreparingEnlistment.Prepared%2A>.</span></span>  
  
### <a name="commit-phase-phase-2"></a><span data-ttu-id="0b8e0-129">Aşama (Aşama 2) Kaydet</span><span class="sxs-lookup"><span data-stu-id="0b8e0-129">Commit phase (Phase 2)</span></span>  
 <span data-ttu-id="0b8e0-130">İkinci aşaması hareketin hareket yöneticisi başarılı alırsa, tüm kaynak yöneticileri hazırlar (tüm kaynak yöneticileri çağrılır <xref:System.Transactions.PreparingEnlistment.Prepared%2A> Aşama 1 sonunda), onu çağırır <xref:System.Transactions.IEnlistmentNotification.Commit%2A> her kaynağın yöntemi Yöneticisi.</span><span class="sxs-lookup"><span data-stu-id="0b8e0-130">In the second phase of the transaction, if the transaction manager receives successful prepares from all the resource managers (all the resource managers have invoked <xref:System.Transactions.PreparingEnlistment.Prepared%2A> at the end of phase 1), it invokes the <xref:System.Transactions.IEnlistmentNotification.Commit%2A> method for each resource manager.</span></span> <span data-ttu-id="0b8e0-131">Kaynak yöneticileri ardından değişiklikleri kalıcı yapın ve yürütme tamamlayın.</span><span class="sxs-lookup"><span data-stu-id="0b8e0-131">The resource managers can then make the changes durable and complete the commit.</span></span>  
  
 <span data-ttu-id="0b8e0-132">Herhangi bir kaynak yöneticisi raporlanan 1 aşamasında hazırlamak için bir hata varsa hareket yöneticisi çağırır <xref:System.Transactions.IEnlistmentNotification.Rollback%2A> her kaynak yöneticisi için yöntem ve uygulama için yürütme başarısız gösterir.</span><span class="sxs-lookup"><span data-stu-id="0b8e0-132">If any resource manager reported a failure to prepare in phase 1, the transaction manager invokes the <xref:System.Transactions.IEnlistmentNotification.Rollback%2A> method for each resource manager and indicates the failure of the commit to the application.</span></span>  
  
 <span data-ttu-id="0b8e0-133">Bu nedenle, kaynak yöneticisi aşağıdaki yöntemleri uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0b8e0-133">Thus, your resource manager should implement the following methods.</span></span>  
  
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
  
 <span data-ttu-id="0b8e0-134">RM bildirim türüne göre işlemi tamamlamak için gerekli olan herhangi bir çalışma gerçekleştirme ve çağırarak bitirdi TM bildirmek <xref:System.Transactions.Enlistment.Done%2A> metodunda <xref:System.Transactions.Enlistment> parametresi.</span><span class="sxs-lookup"><span data-stu-id="0b8e0-134">The RM should perform any work necessary to finish the transaction based on the notification type, and inform the TM that it has finished by calling <xref:System.Transactions.Enlistment.Done%2A> method on the <xref:System.Transactions.Enlistment> parameter.</span></span> <span data-ttu-id="0b8e0-135">Bu iş iş parçacığı üzerinde yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="0b8e0-135">This work can be done on a worker thread.</span></span> <span data-ttu-id="0b8e0-136">Satır içi çağrılır aynı iş parçacığı üzerinde Aşama 2 bildirimleri oluşabilir Not <xref:System.Transactions.PreparingEnlistment.Prepared%2A> yönteminde Aşama 1.</span><span class="sxs-lookup"><span data-stu-id="0b8e0-136">Note that the phase 2 notifications can happen inline on the same thread that called the <xref:System.Transactions.PreparingEnlistment.Prepared%2A> method in phase 1.</span></span> <span data-ttu-id="0b8e0-137">Bu nedenle, sonra herhangi bir iş yapmanız gerektiğini değil <xref:System.Transactions.PreparingEnlistment.Prepared%2A> Aşama 2 bildirimleri almadan önce tamamladınız beklediğiniz araması (örneğin, serbest bırakma kilitler).</span><span class="sxs-lookup"><span data-stu-id="0b8e0-137">As such, you should not do any work after the <xref:System.Transactions.PreparingEnlistment.Prepared%2A> call (for example, releasing locks) that you would expect to have completed before receiving the phase 2 notifications.</span></span>  
  
### <a name="implementing-indoubt"></a><span data-ttu-id="0b8e0-138">Nin şüpheli işlemi olmadığından uygulama</span><span class="sxs-lookup"><span data-stu-id="0b8e0-138">Implementing InDoubt</span></span>  
 <span data-ttu-id="0b8e0-139">Son olarak, uygulamalıdır <xref:System.Transactions.IEnlistmentNotification.InDoubt%2A> geçici kaynak yöneticisi için yöntem.</span><span class="sxs-lookup"><span data-stu-id="0b8e0-139">Finally, you should implement the <xref:System.Transactions.IEnlistmentNotification.InDoubt%2A> method for the volatile resource manager.</span></span> <span data-ttu-id="0b8e0-140">Durumları bilinmiyor şekilde hareket yöneticisi bir veya daha fazla katılımcılarıyla iletişim kaybolursa, bu yöntem çağrılır.</span><span class="sxs-lookup"><span data-stu-id="0b8e0-140">This method is called if the transaction manager loses contact with one or more participants, so their status is unknown.</span></span> <span data-ttu-id="0b8e0-141">Bu meydana gelirse, daha sonra herhangi bir işlem katılımcıları sola mı tutarsız bir durumda inceleyebilirsiniz bu olgu oturum açmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0b8e0-141">If this occurs, you should log this fact so that you can investigate later whether any of the transaction participants has been left in an inconsistent state.</span></span>  
  
```csharp
public void InDoubt (Enlistment enlistment)  
{  
     // log this  
     enlistment.Done();  
}  
```  
  
## <a name="single-phase-commit-optimization"></a><span data-ttu-id="0b8e0-142">Tek aşaması yürütme en iyi hale getirme</span><span class="sxs-lookup"><span data-stu-id="0b8e0-142">Single Phase Commit Optimization</span></span>  
 <span data-ttu-id="0b8e0-143">Tüm güncelleştirmeleri herhangi bir açık işbirliği yapıldığından tek aşaması yürütme Protokolü çalışma zamanında daha etkilidir.</span><span class="sxs-lookup"><span data-stu-id="0b8e0-143">The Single Phase Commit protocol is more efficient at run time because all updates are done without any explicit coordination.</span></span> <span data-ttu-id="0b8e0-144">Bu protokol hakkında daha fazla bilgi için bkz. [tek aşamalı işleme ve yükseltilebilir tek aşamalı bildirim kullanarak en iyi duruma getirme](../../../../docs/framework/data/transactions/optimization-spc-and-promotable-spn.md).</span><span class="sxs-lookup"><span data-stu-id="0b8e0-144">For more information on this protocol, see [Optimization using Single Phase Commit and Promotable Single Phase Notification](../../../../docs/framework/data/transactions/optimization-spc-and-promotable-spn.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b8e0-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0b8e0-145">See also</span></span>
- [<span data-ttu-id="0b8e0-146">Tek Aşamalı İşleme ve Yükseltilebilir Tek Aşamalı Bildirim kullanarak en iyi duruma getirme</span><span class="sxs-lookup"><span data-stu-id="0b8e0-146">Optimization using Single Phase Commit and Promotable Single Phase Notification</span></span>](../../../../docs/framework/data/transactions/optimization-spc-and-promotable-spn.md)
- [<span data-ttu-id="0b8e0-147">Bir İşlemde Kaynakları Katılımcı Olarak Kaydetme</span><span class="sxs-lookup"><span data-stu-id="0b8e0-147">Enlisting Resources as Participants in a Transaction</span></span>](../../../../docs/framework/data/transactions/enlisting-resources-as-participants-in-a-transaction.md)
