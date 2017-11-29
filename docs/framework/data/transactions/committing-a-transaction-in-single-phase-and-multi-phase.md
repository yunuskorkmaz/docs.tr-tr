---
title: "İşlemi tek aşamalı ve çok aşaması Tamamlanıyor"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 694ea153-e4db-41ae-96ac-9ac66dcb69a9
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 83a65f6973c64b14e17b701ba4b5562eab8641f4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="committing-a-transaction-in-single-phase-and-multi-phase"></a><span data-ttu-id="31644-102">İşlemi tek aşamalı ve çok aşaması Tamamlanıyor</span><span class="sxs-lookup"><span data-stu-id="31644-102">Committing a Transaction in Single-Phase and Multi-Phase</span></span>
<span data-ttu-id="31644-103">Bir işlem içinde kullanılan her bir kaynağın eylemlerini işlem yöneticisi (TM) tarafından düzenlenir Kaynak Yöneticisi (RM) tarafından yönetilir.</span><span class="sxs-lookup"><span data-stu-id="31644-103">Each resource used in a transaction is managed by a resource manager (RM), whose actions are coordinated by a transaction manager (TM).</span></span> <span data-ttu-id="31644-104">[Kaydetme kaynakları bir işlemde katılımcı olarak](../../../../docs/framework/data/transactions/enlisting-resources-as-participants-in-a-transaction.md) konuda ele alınmıştır bir kaynak (veya birden çok kaynak) bir işlem içinde nasıl kaydedilebilir.</span><span class="sxs-lookup"><span data-stu-id="31644-104">The [Enlisting Resources as Participants in a Transaction](../../../../docs/framework/data/transactions/enlisting-resources-as-participants-in-a-transaction.md) topic discusses how a resource (or multiple resources) can be enlisted in a transaction.</span></span> <span data-ttu-id="31644-105">Bu konuda ele alınmıştır nasıl işlem taahhüt kayıtlı kaynakları arasında Eşgüdümlü olabilir.</span><span class="sxs-lookup"><span data-stu-id="31644-105">This topic discusses how transaction commitment can be coordinated among enlisted resources.</span></span>  
  
 <span data-ttu-id="31644-106">İşlemin sonunda, uygulama işlemi ya da yürütülmeli veya geri ister.</span><span class="sxs-lookup"><span data-stu-id="31644-106">At the end of the transaction, the application requests the transaction to be either committed or rolled back.</span></span> <span data-ttu-id="31644-107">Başkalarının tamamlamaya oylama bazı kaynak yöneticileri while gibi işlem yöneticisi riskleri ortadan kaldırmanız gerekir işlemi geri oylama.</span><span class="sxs-lookup"><span data-stu-id="31644-107">The transaction manager must eliminate risks like some resource managers voting to commit while others voting to roll back the transaction.</span></span>  
  
 <span data-ttu-id="31644-108">İşleminiz birden fazla kaynak içeriyorsa, iki aşamalı kayıt (2PC) gerçekleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="31644-108">If your transaction involves more than one resource, you must perform a two-phase commit (2PC).</span></span> <span data-ttu-id="31644-109">İki aşamalı yürütme Protokolü (hazırlama aşamasında ve Tamamlama aşaması) işlem sona erdiğinde, tüm kaynakları yapılan tüm değişiklikler tamamen kaydedilen ya da tam olarak geri olduğunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="31644-109">The two-phase commit protocol (the prepare phase and the commit phase) ensures that when the transaction ends, all changes to all resources are either totally committed or fully rolled back.</span></span> <span data-ttu-id="31644-110">Tüm katılımcıları sonra sonucunu bildirilir.</span><span class="sxs-lookup"><span data-stu-id="31644-110">All the participants are then informed of the final result.</span></span> <span data-ttu-id="31644-111">İki aşamalı yürütme protokolü hakkında ayrıntılı bilgi için lütfen rehberi başvurun "*hareket işleme: kavramlar ve teknikler (Morgan Kaufmann dizide veri yönetim sistemleri) ISBN:1558601902*" Jim gri tarafından.</span><span class="sxs-lookup"><span data-stu-id="31644-111">For a detailed discussion of the two-phase commit protocol, please consult the book "*Transaction Processing : Concepts and Techniques (Morgan Kaufmann Series in Data Management Systems) ISBN:1558601902*" by Jim Gray.</span></span>  
  
 <span data-ttu-id="31644-112">Ayrıca, tek aşaması yürütme protokolünde bölümü gerçekleştirerek, işlemdeki performans iyi duruma getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="31644-112">You can also optimize your transaction's performance by taking part in the Single Phase Commit protocol.</span></span> <span data-ttu-id="31644-113">Daha fazla bilgi için bkz: [tek aşaması kaydetmek ve yükseltilebilir tek aşaması bildirim kullanarak en iyi duruma getirme](../../../../docs/framework/data/transactions/optimization-spc-and-promotable-spn.md).</span><span class="sxs-lookup"><span data-stu-id="31644-113">For more information, see [Optimization using Single Phase Commit and Promotable Single Phase Notification](../../../../docs/framework/data/transactions/optimization-spc-and-promotable-spn.md).</span></span>  
  
 <span data-ttu-id="31644-114">Yalnızca bir işlemdeki sonucunu bilgilendirilmek istiyorsanız ve oylamasına katılmasına istemediğiniz, için kaydedeceğini <xref:System.Transactions.Transaction.TransactionCompleted> olay.</span><span class="sxs-lookup"><span data-stu-id="31644-114">If you just want to be informed of a transaction's outcome, and do not want to participate in voting, you should register for the <xref:System.Transactions.Transaction.TransactionCompleted> event.</span></span>  
  
## <a name="two-phase-commit-2pc"></a><span data-ttu-id="31644-115">İki aşamalı kayıt (2PC)</span><span class="sxs-lookup"><span data-stu-id="31644-115">Two-phase Commit (2PC)</span></span>  
 <span data-ttu-id="31644-116">İlk işlem aşamasında, işlem yöneticisi bir işlem yürütülmeli veya geri olup olmadığını belirlemek için her bir kaynağın sorgular.</span><span class="sxs-lookup"><span data-stu-id="31644-116">In the first transaction phase, the transaction manager queries each resource to determine whether a transaction should be committed or rolled back.</span></span> <span data-ttu-id="31644-117">İkinci işlem aşamasında, işlem yöneticisi, kendi sorgu sonucunun her bir kaynağın tüm gerekli temizlenmesini izin veren bildirir.</span><span class="sxs-lookup"><span data-stu-id="31644-117">In the second transaction phase, the transaction manager notifies each resource of the outcome of its queries, allowing it to perform any necessary cleanup.</span></span>  
  
 <span data-ttu-id="31644-118">Bu tür bir işlem içinde katılmak için bir Kaynak Yöneticisi'ni uygulamalıdır <xref:System.Transactions.IEnlistmentNotification> tarafından TM 2PC sırasında bildirimleri olarak adlandırılır yöntemleri sağlayan arabirim.</span><span class="sxs-lookup"><span data-stu-id="31644-118">To participate in this kind of transaction, a resource manager must implement the <xref:System.Transactions.IEnlistmentNotification> interface, which provides methods that are called by the TM as notifications during a 2PC.</span></span>  <span data-ttu-id="31644-119">Aşağıdaki örnek, bu tür uygulaması örneği gösterir.</span><span class="sxs-lookup"><span data-stu-id="31644-119">The following sample shows an example of such implementation.</span></span>  
  
 [!code-csharp[Tx_Enlist#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/tx_enlist/cs/enlist.cs#2)]
 [!code-vb[Tx_Enlist#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/tx_enlist/vb/enlist.vb#2)]  
  
### <a name="prepare-phase-phase-1"></a><span data-ttu-id="31644-120">Aşama (Aşama 1) hazırla</span><span class="sxs-lookup"><span data-stu-id="31644-120">Prepare phase (Phase 1)</span></span>  
 <span data-ttu-id="31644-121">Alma sırasında bir <xref:System.Transactions.CommittableTransaction.Commit%2A> isteği uygulamadan işlem yöneticisi çağırarak tüm kayıtlı katılımcılar hazırlık aşamasında başlar <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> yöntemi her kaynak kayıtlı, her bir kaynağın almak için 's oy işlem.</span><span class="sxs-lookup"><span data-stu-id="31644-121">Upon receiving a <xref:System.Transactions.CommittableTransaction.Commit%2A> request from the application, the transaction manager begins the Prepare phase of all the enlisted participants by calling the <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> method on each enlisted resource, in order to obtain each resource's vote on the transaction.</span></span>  
  
 <span data-ttu-id="31644-122">Uygular, Kaynak Yöneticisi <xref:System.Transactions.IEnlistmentNotification> arabirimi ilk uygulayan <xref:System.Transactions.IEnlistmentNotification.Prepare%28System.Transactions.PreparingEnlistment%29> yöntemi aşağıdaki basit örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="31644-122">Your resource manager that implements the <xref:System.Transactions.IEnlistmentNotification> interface should first implement the <xref:System.Transactions.IEnlistmentNotification.Prepare%28System.Transactions.PreparingEnlistment%29> method as the following simple example shows.</span></span>  
  
```  
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
  
 <span data-ttu-id="31644-123">Sağlam kaynak yöneticisi bu çağrı aldığında, işlemdeki kurtarma bilgileri günlüğe (alarak kullanılabilir <xref:System.Transactions.PreparingEnlistment.RecoveryInformation%2A> özelliği) ve ne olursa olsun üzerinde yürütme işlemi tamamlamak gerekli bir bilgidir.</span><span class="sxs-lookup"><span data-stu-id="31644-123">When the durable resource manager receives this call, it should log the transaction's recovery information (available by retrieving the <xref:System.Transactions.PreparingEnlistment.RecoveryInformation%2A> property) and whatever information is necessary to complete the transaction on commit.</span></span> <span data-ttu-id="31644-124">Bu içinde yapılması gerekmez <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> yöntemi olduğundan RM iş parçacığı üzerinde bunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="31644-124">This does not need to be performed within the <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> method because the RM can do this on a worker thread.</span></span>  
  
 <span data-ttu-id="31644-125">RM bittiğinde kendi iş hazırlama, yürütme veya geri çağırarak için oy <xref:System.Transactions.PreparingEnlistment.Prepared%2A> veya <xref:System.Transactions.PreparingEnlistment.ForceRollback%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="31644-125">When the RM has finished its prepare work, it should vote to commit or roll back by calling the <xref:System.Transactions.PreparingEnlistment.Prepared%2A> or <xref:System.Transactions.PreparingEnlistment.ForceRollback%2A> method.</span></span> <span data-ttu-id="31644-126">Dikkat <xref:System.Transactions.PreparingEnlistment> sınıfından devralan bir <xref:System.Transactions.Enlistment.Done%2A> yönteminden <xref:System.Transactions.Enlistment> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="31644-126">Notice that the <xref:System.Transactions.PreparingEnlistment> class inherits a <xref:System.Transactions.Enlistment.Done%2A> method from the <xref:System.Transactions.Enlistment> class.</span></span> <span data-ttu-id="31644-127">Bu yöntem çağırırsanız <xref:System.Transactions.PreparingEnlistment> geri çağırma hazırlama aşamasında, sizi bilgilendirir TM salt okunur bir kaydı (okuyabilir, ancak işlem korunan verileri güncelleştirilemiyor diğer bir deyişle, kaynak yöneticileri) olduğunu ve başka hiçbir bildirim RM alır İşlem Yöneticisi'nden Aşama 2 işlemde sonucunu seçeceğine.</span><span class="sxs-lookup"><span data-stu-id="31644-127">If you call this method on the <xref:System.Transactions.PreparingEnlistment> callback during the Prepare phase, it informs the TM that it is a Read-Only enlistment (that is, resource managers that can read but cannot update transaction-protected data) and the RM receives no further notifications from the transaction manager as to the outcome of the transaction in phase 2.</span></span>  
  
 <span data-ttu-id="31644-128">Tüm kaynak yöneticileri oy sonra uygulama işlem başarılı taahhüt işe <xref:System.Transactions.PreparingEnlistment.Prepared%2A>.</span><span class="sxs-lookup"><span data-stu-id="31644-128">The application is told of the successful commitment of the transaction after all the resource managers vote <xref:System.Transactions.PreparingEnlistment.Prepared%2A>.</span></span>  
  
### <a name="commit-phase-phase-2"></a><span data-ttu-id="31644-129">Aşama (Aşama 2) Kaydet</span><span class="sxs-lookup"><span data-stu-id="31644-129">Commit phase (Phase 2)</span></span>  
 <span data-ttu-id="31644-130">İkinci aşama hareketin işlem yöneticisi başarılı alırsa, tüm kaynak yöneticileri hazırlar (tüm kaynak yöneticileri çağrılan <xref:System.Transactions.PreparingEnlistment.Prepared%2A> Aşama 1 sonunda), onu çağırır <xref:System.Transactions.IEnlistmentNotification.Commit%2A> her kaynak için yöntemi Yöneticisi.</span><span class="sxs-lookup"><span data-stu-id="31644-130">In the second phase of the transaction, if the transaction manager receives successful prepares from all the resource managers (all the resource managers have invoked <xref:System.Transactions.PreparingEnlistment.Prepared%2A> at the end of phase 1), it invokes the <xref:System.Transactions.IEnlistmentNotification.Commit%2A> method for each resource manager.</span></span> <span data-ttu-id="31644-131">Kaynak yöneticileri ardından değişiklikleri kalıcı yapın ve yürütme tamamlayın.</span><span class="sxs-lookup"><span data-stu-id="31644-131">The resource managers can then make the changes durable and complete the commit.</span></span>  
  
 <span data-ttu-id="31644-132">Herhangi bir kaynak yöneticisi Aşama 1 hazırlamak için bir hata bildirdi, İşlem Yöneticisi'ni çağırır <xref:System.Transactions.IEnlistmentNotification.Rollback%2A> her kaynak yöneticisi için yöntem ve uygulamaya yürütme başarısızlığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="31644-132">If any resource manager reported a failure to prepare in phase 1, the transaction manager invokes the <xref:System.Transactions.IEnlistmentNotification.Rollback%2A> method for each resource manager and indicates the failure of the commit to the application.</span></span>  
  
 <span data-ttu-id="31644-133">Bu nedenle, kaynak yöneticisi aşağıdaki yöntemleri uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="31644-133">Thus, your resource manager should implement the following methods.</span></span>  
  
```  
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
  
 <span data-ttu-id="31644-134">RM bildirim türüne göre hareket tamamlamak gerekli herhangi bir iş gerçekleştirin ve çağırarak bitirdi TM bildirmek <xref:System.Transactions.Enlistment.Done%2A> yöntemi <xref:System.Transactions.Enlistment> parametresi.</span><span class="sxs-lookup"><span data-stu-id="31644-134">The RM should perform any work necessary to finish the transaction based on the notification type, and inform the TM that it has finished by calling <xref:System.Transactions.Enlistment.Done%2A> method on the <xref:System.Transactions.Enlistment> parameter.</span></span> <span data-ttu-id="31644-135">Bu iş iş parçacığı üzerinde yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="31644-135">This work can be done on a worker thread.</span></span> <span data-ttu-id="31644-136">Satır içi çağrılır aynı iş parçacığı üzerinde Aşama 2 bildirimleri oluşabilir Not <xref:System.Transactions.PreparingEnlistment.Prepared%2A> yönteminde Aşama 1.</span><span class="sxs-lookup"><span data-stu-id="31644-136">Note that the phase 2 notifications can happen inline on the same thread that called the <xref:System.Transactions.PreparingEnlistment.Prepared%2A> method in phase 1.</span></span> <span data-ttu-id="31644-137">Bu nedenle, sonra herhangi bir iş yapmanız gerektiğini değil <xref:System.Transactions.PreparingEnlistment.Prepared%2A> Aşama 2 bildirimleri almadan önce tamamladınız beklediğiniz araması (örneğin, serbest bırakma kilitler).</span><span class="sxs-lookup"><span data-stu-id="31644-137">As such, you should not do any work after the <xref:System.Transactions.PreparingEnlistment.Prepared%2A> call (for example, releasing locks) that you would expect to have completed before receiving the phase 2 notifications.</span></span>  
  
### <a name="implementing-indoubt"></a><span data-ttu-id="31644-138">Nin şüpheli işlemi olmadığından uygulama</span><span class="sxs-lookup"><span data-stu-id="31644-138">Implementing InDoubt</span></span>  
 <span data-ttu-id="31644-139">Son olarak, uygulamalıdır <xref:System.Transactions.IEnlistmentNotification.InDoubt%2A> geçici kaynak yöneticisi için yöntem.</span><span class="sxs-lookup"><span data-stu-id="31644-139">Finally, you should implement the <xref:System.Transactions.IEnlistmentNotification.InDoubt%2A> method for the volatile resource manager.</span></span> <span data-ttu-id="31644-140">Durumları bilinmiyor şekilde işlem yöneticisi bir veya daha fazla katılımcı ile ilgili kişi kaybederse, bu yöntem çağrılır.</span><span class="sxs-lookup"><span data-stu-id="31644-140">This method is called if the transaction manager loses contact with one or more participants, so their status is unknown.</span></span> <span data-ttu-id="31644-141">Bu gerçekleşirse, böylece herhangi bir işlem katılımcının sola mı tutarsız bir durumda daha sonra araştırabilir olgunun oturum açmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="31644-141">If this occurs, you should log this fact so that you can investigate later whether any of the transaction participants has been left in an inconsistent state.</span></span>  
  
```  
public void InDoubt (Enlistment enlistment)  
{  
     // log this  
     enlistment.Done();  
}  
```  
  
## <a name="single-phase-commit-optimization"></a><span data-ttu-id="31644-142">Tek aşaması yürütme en iyi hale getirme</span><span class="sxs-lookup"><span data-stu-id="31644-142">Single Phase Commit Optimization</span></span>  
 <span data-ttu-id="31644-143">Tüm güncelleştirmeleri herhangi bir açık işbirliği yapıldığından tek aşaması yürütme Protokolü çalışma zamanında daha etkilidir.</span><span class="sxs-lookup"><span data-stu-id="31644-143">The Single Phase Commit protocol is more efficient at run time because all updates are done without any explicit coordination.</span></span> <span data-ttu-id="31644-144">Bu protokol, daha fazla bilgi için bkz [tek aşaması kaydetmek ve yükseltilebilir tek aşaması bildirim kullanarak en iyi duruma getirme](../../../../docs/framework/data/transactions/optimization-spc-and-promotable-spn.md).</span><span class="sxs-lookup"><span data-stu-id="31644-144">For more information on this protocol, see [Optimization using Single Phase Commit and Promotable Single Phase Notification](../../../../docs/framework/data/transactions/optimization-spc-and-promotable-spn.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31644-145">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="31644-145">See Also</span></span>  
 [<span data-ttu-id="31644-146">Tek aşaması kaydetmek ve yükseltilebilir tek aşaması bildirim kullanarak en iyi duruma getirme</span><span class="sxs-lookup"><span data-stu-id="31644-146">Optimization using Single Phase Commit and Promotable Single Phase Notification</span></span>](../../../../docs/framework/data/transactions/optimization-spc-and-promotable-spn.md)  
 [<span data-ttu-id="31644-147">Bir işlemde katılımcı olarak kaynakları kaydetme</span><span class="sxs-lookup"><span data-stu-id="31644-147">Enlisting Resources as Participants in a Transaction</span></span>](../../../../docs/framework/data/transactions/enlisting-resources-as-participants-in-a-transaction.md)
