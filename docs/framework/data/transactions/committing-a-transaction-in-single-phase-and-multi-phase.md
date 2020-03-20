---
title: Tek Aşamalı ve Çok Aşamalı İşlem Gerçekleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 694ea153-e4db-41ae-96ac-9ac66dcb69a9
ms.openlocfilehash: 8d6c51249f104d35573507a9477a24d66d770693
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174439"
---
# <a name="committing-a-transaction-in-single-phase-and-multi-phase"></a><span data-ttu-id="ef9ee-102">Tek Aşamalı ve Çok Aşamalı İşlem Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="ef9ee-102">Committing a Transaction in Single-Phase and Multi-Phase</span></span>
<span data-ttu-id="ef9ee-103">Bir işlemde kullanılan her kaynak, eylemleri bir işlem yöneticisi (TM) tarafından koordine edilen bir kaynak yöneticisi (RM) tarafından yönetilir.</span><span class="sxs-lookup"><span data-stu-id="ef9ee-103">Each resource used in a transaction is managed by a resource manager (RM), whose actions are coordinated by a transaction manager (TM).</span></span> <span data-ttu-id="ef9ee-104">Bir İşlem konusuna [Katılan Kaynaklar Olarak Kaydolun,](enlisting-resources-as-participants-in-a-transaction.md) bir kaynağın (veya birden çok kaynağın) bir işlemde nasıl kaydolabileceğini tartışır.</span><span class="sxs-lookup"><span data-stu-id="ef9ee-104">The [Enlisting Resources as Participants in a Transaction](enlisting-resources-as-participants-in-a-transaction.md) topic discusses how a resource (or multiple resources) can be enlisted in a transaction.</span></span> <span data-ttu-id="ef9ee-105">Bu konu, işlem taahhüdünün kayıtlı kaynaklar arasında nasıl koordine edilebildiğini tartışır.</span><span class="sxs-lookup"><span data-stu-id="ef9ee-105">This topic discusses how transaction commitment can be coordinated among enlisted resources.</span></span>  
  
 <span data-ttu-id="ef9ee-106">İşlemin sonunda, uygulama hareketin kaydedilmesini veya geri alınmasını ister.</span><span class="sxs-lookup"><span data-stu-id="ef9ee-106">At the end of the transaction, the application requests the transaction to be either committed or rolled back.</span></span> <span data-ttu-id="ef9ee-107">İşlem yöneticisi, bazı kaynak yöneticilerinin işlemek için oy kullanması, diğerlerinin ise hareketi geri almak için oy kullanması gibi riskleri ortadan kaldırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ef9ee-107">The transaction manager must eliminate risks like some resource managers voting to commit while others voting to roll back the transaction.</span></span>  
  
 <span data-ttu-id="ef9ee-108">İşleminiz birden fazla kaynak içeriyorsa, iki aşamalı bir commit (2PC) gerçekleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ef9ee-108">If your transaction involves more than one resource, you must perform a two-phase commit (2PC).</span></span> <span data-ttu-id="ef9ee-109">İki aşamalı taahhüt protokolü (hazırlama aşaması ve işleme aşaması) işlem sona erdiğinde tüm kaynaklardaki tüm değişikliklerin tamamen kaydedilmesini veya tamamen geri atıldığında olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="ef9ee-109">The two-phase commit protocol (the prepare phase and the commit phase) ensures that when the transaction ends, all changes to all resources are either totally committed or fully rolled back.</span></span> <span data-ttu-id="ef9ee-110">Tüm katılımcıları sonra sonucunu bildirilir.</span><span class="sxs-lookup"><span data-stu-id="ef9ee-110">All the participants are then informed of the final result.</span></span> <span data-ttu-id="ef9ee-111">İki aşamalı taahhüt protokolünün ayrıntılı bir tartışması için lütfen Jim Gray'in "*İşlem İşlemleme : Kavramlar ve Teknikler (Veri Yönetim Sistemlerinde Morgan Kaufmann Serisi) ISBN:1558601902*" kitabına başvurun.</span><span class="sxs-lookup"><span data-stu-id="ef9ee-111">For a detailed discussion of the two-phase commit protocol, please consult the book "*Transaction Processing : Concepts and Techniques (Morgan Kaufmann Series in Data Management Systems) ISBN:1558601902*" by Jim Gray.</span></span>  
  
 <span data-ttu-id="ef9ee-112">Ayrıca, Tek Aşamalı İşlem protokolüne katılarak işleminizin performansını optimize edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef9ee-112">You can also optimize your transaction's performance by taking part in the Single Phase Commit protocol.</span></span> <span data-ttu-id="ef9ee-113">Daha fazla bilgi için, [Tek Faz Commit ve Teşvik Edilebilir Tek Faz Bildirimi kullanarak Optimizasyon'a](optimization-spc-and-promotable-spn.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="ef9ee-113">For more information, see [Optimization using Single Phase Commit and Promotable Single Phase Notification](optimization-spc-and-promotable-spn.md).</span></span>  
  
 <span data-ttu-id="ef9ee-114">Bir işlemin sonucu hakkında bilgi almak istiyorsanız ve oylamaya katılmak istemiyorsanız, etkinliğe <xref:System.Transactions.Transaction.TransactionCompleted> kaydolmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ef9ee-114">If you just want to be informed of a transaction's outcome, and do not want to participate in voting, you should register for the <xref:System.Transactions.Transaction.TransactionCompleted> event.</span></span>  
  
## <a name="two-phase-commit-2pc"></a><span data-ttu-id="ef9ee-115">İki aşamalı kayıt (2PC)</span><span class="sxs-lookup"><span data-stu-id="ef9ee-115">Two-phase Commit (2PC)</span></span>  
 <span data-ttu-id="ef9ee-116">İlk işlem aşamasında, hareket yöneticisi bir işlemin kaydedilmesi mi yoksa geri alınması mı gerektiğini belirlemek için her kaynağı sorgular.</span><span class="sxs-lookup"><span data-stu-id="ef9ee-116">In the first transaction phase, the transaction manager queries each resource to determine whether a transaction should be committed or rolled back.</span></span> <span data-ttu-id="ef9ee-117">İkinci işlem aşamasında, işlem yöneticisi her kaynağı sorgularının sonucunu belirterek gerekli temizlemeişlemini gerçekleştirmesine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="ef9ee-117">In the second transaction phase, the transaction manager notifies each resource of the outcome of its queries, allowing it to perform any necessary cleanup.</span></span>  
  
 <span data-ttu-id="ef9ee-118">Bu tür bir işlemde yer almak için, bir kaynak yöneticisinin 2PC sırasında TM tarafından bildirim olarak adlandırılan yöntemleri sağlayan <xref:System.Transactions.IEnlistmentNotification> arabirimi uygulaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ef9ee-118">To participate in this kind of transaction, a resource manager must implement the <xref:System.Transactions.IEnlistmentNotification> interface, which provides methods that are called by the TM as notifications during a 2PC.</span></span>  <span data-ttu-id="ef9ee-119">Aşağıdaki örnek, bu tür uygulaması örneği gösterir.</span><span class="sxs-lookup"><span data-stu-id="ef9ee-119">The following sample shows an example of such implementation.</span></span>  
  
 [!code-csharp[Tx_Enlist#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/tx_enlist/cs/enlist.cs#2)]
 [!code-vb[Tx_Enlist#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/tx_enlist/vb/enlist.vb#2)]  
  
### <a name="prepare-phase-phase-1"></a><span data-ttu-id="ef9ee-120">Aşama (Aşama 1) hazırla</span><span class="sxs-lookup"><span data-stu-id="ef9ee-120">Prepare phase (Phase 1)</span></span>  
 <span data-ttu-id="ef9ee-121">Uygulamadan bir <xref:System.Transactions.CommittableTransaction.Commit%2A> istek aldıktan sonra, işlem yöneticisi, her bir kaynağın işlem <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> le ilgili oylarını almak için, kayıtlı her kaynak üzerindeki yöntemi arayarak tüm kayıtlı katılımcıların Hazırlama aşamasını başlatır.</span><span class="sxs-lookup"><span data-stu-id="ef9ee-121">Upon receiving a <xref:System.Transactions.CommittableTransaction.Commit%2A> request from the application, the transaction manager begins the Prepare phase of all the enlisted participants by calling the <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> method on each enlisted resource, in order to obtain each resource's vote on the transaction.</span></span>  
  
 <span data-ttu-id="ef9ee-122">Uygular, Kaynak Yöneticisi <xref:System.Transactions.IEnlistmentNotification> arabirimi ilk uygulayan <xref:System.Transactions.IEnlistmentNotification.Prepare%28System.Transactions.PreparingEnlistment%29> yöntemi aşağıdaki basit örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="ef9ee-122">Your resource manager that implements the <xref:System.Transactions.IEnlistmentNotification> interface should first implement the <xref:System.Transactions.IEnlistmentNotification.Prepare%28System.Transactions.PreparingEnlistment%29> method as the following simple example shows.</span></span>  
  
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
  
 <span data-ttu-id="ef9ee-123">Dayanıklı kaynak yöneticisi bu çağrıyı aldığında, işlemin kurtarma bilgilerini <xref:System.Transactions.PreparingEnlistment.RecoveryInformation%2A> (özelliği alarak kullanılabilir) ve işleme işlemini tamamlamak için gereken her türlü bilgiyi kaydetmelidir.</span><span class="sxs-lookup"><span data-stu-id="ef9ee-123">When the durable resource manager receives this call, it should log the transaction's recovery information (available by retrieving the <xref:System.Transactions.PreparingEnlistment.RecoveryInformation%2A> property) and whatever information is necessary to complete the transaction on commit.</span></span> <span data-ttu-id="ef9ee-124">Bu içinde yapılması gerekmez <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> yöntemi olduğundan RM iş parçacığı üzerinde bunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef9ee-124">This does not need to be performed within the <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> method because the RM can do this on a worker thread.</span></span>  
  
 <span data-ttu-id="ef9ee-125">RM bittiğinde kendi iş hazırlama, yürütme veya geri çağırarak için oy <xref:System.Transactions.PreparingEnlistment.Prepared%2A> veya <xref:System.Transactions.PreparingEnlistment.ForceRollback%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ef9ee-125">When the RM has finished its prepare work, it should vote to commit or roll back by calling the <xref:System.Transactions.PreparingEnlistment.Prepared%2A> or <xref:System.Transactions.PreparingEnlistment.ForceRollback%2A> method.</span></span> <span data-ttu-id="ef9ee-126">Dikkat <xref:System.Transactions.PreparingEnlistment> sınıfından devralan bir <xref:System.Transactions.Enlistment.Done%2A> yönteminden <xref:System.Transactions.Enlistment> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="ef9ee-126">Notice that the <xref:System.Transactions.PreparingEnlistment> class inherits a <xref:System.Transactions.Enlistment.Done%2A> method from the <xref:System.Transactions.Enlistment> class.</span></span> <span data-ttu-id="ef9ee-127">Bu yöntemi Hazırlama aşamasında <xref:System.Transactions.PreparingEnlistment> geri aramada ararsanız, TM'ye bunun Salt Okunur kaydı (diğer bir deyişle, işlem korumalı verileri okuyabilen ancak güncelleştiremeyen kaynak yöneticileri) olduğunu bildirir ve RM, işlem yöneticisinden 2.</span><span class="sxs-lookup"><span data-stu-id="ef9ee-127">If you call this method on the <xref:System.Transactions.PreparingEnlistment> callback during the Prepare phase, it informs the TM that it is a Read-Only enlistment (that is, resource managers that can read but cannot update transaction-protected data) and the RM receives no further notifications from the transaction manager as to the outcome of the transaction in phase 2.</span></span>  
  
 <span data-ttu-id="ef9ee-128">Uygulama tüm kaynak yöneticileri oy <xref:System.Transactions.PreparingEnlistment.Prepared%2A>sonra işlemin başarılı bağlılık anlatılır.</span><span class="sxs-lookup"><span data-stu-id="ef9ee-128">The application is told of the successful commitment of the transaction after all the resource managers vote <xref:System.Transactions.PreparingEnlistment.Prepared%2A>.</span></span>  
  
### <a name="commit-phase-phase-2"></a><span data-ttu-id="ef9ee-129">Aşama (Aşama 2) Kaydet</span><span class="sxs-lookup"><span data-stu-id="ef9ee-129">Commit phase (Phase 2)</span></span>  
 <span data-ttu-id="ef9ee-130">İşlemin ikinci aşamasında, işlem yöneticisi tüm kaynak yöneticilerinden (1. aşamanın sonunda çağrılan <xref:System.Transactions.PreparingEnlistment.Prepared%2A> tüm kaynak yöneticilerinin tümünün) <xref:System.Transactions.IEnlistmentNotification.Commit%2A> başarılı prepareları alırsa, her kaynak yöneticisi için yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="ef9ee-130">In the second phase of the transaction, if the transaction manager receives successful prepares from all the resource managers (all the resource managers have invoked <xref:System.Transactions.PreparingEnlistment.Prepared%2A> at the end of phase 1), it invokes the <xref:System.Transactions.IEnlistmentNotification.Commit%2A> method for each resource manager.</span></span> <span data-ttu-id="ef9ee-131">Kaynak yöneticileri ardından değişiklikleri kalıcı yapın ve yürütme tamamlayın.</span><span class="sxs-lookup"><span data-stu-id="ef9ee-131">The resource managers can then make the changes durable and complete the commit.</span></span>  
  
 <span data-ttu-id="ef9ee-132">Herhangi bir kaynak yöneticisi faz 1'de hazırlanmahatası bildirseydi, işlem yöneticisi her kaynak yöneticisi için <xref:System.Transactions.IEnlistmentNotification.Rollback%2A> yöntemi çağırır ve uygulamada commit'in başarısızlığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ef9ee-132">If any resource manager reported a failure to prepare in phase 1, the transaction manager invokes the <xref:System.Transactions.IEnlistmentNotification.Rollback%2A> method for each resource manager and indicates the failure of the commit to the application.</span></span>  
  
 <span data-ttu-id="ef9ee-133">Bu nedenle, kaynak yöneticisi aşağıdaki yöntemleri uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ef9ee-133">Thus, your resource manager should implement the following methods.</span></span>  
  
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
  
 <span data-ttu-id="ef9ee-134">RM, bildirim türüne göre işlemi bitirmek için gerekli her türlü çalışmayı yapmalı ve <xref:System.Transactions.Enlistment.Done%2A> <xref:System.Transactions.Enlistment> tm'ye parametredeki arama yöntemini çağırarak bitirdiğini bildirmelidir.</span><span class="sxs-lookup"><span data-stu-id="ef9ee-134">The RM should perform any work necessary to finish the transaction based on the notification type, and inform the TM that it has finished by calling <xref:System.Transactions.Enlistment.Done%2A> method on the <xref:System.Transactions.Enlistment> parameter.</span></span> <span data-ttu-id="ef9ee-135">Bu iş iş parçacığı üzerinde yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="ef9ee-135">This work can be done on a worker thread.</span></span> <span data-ttu-id="ef9ee-136">Satır içi çağrılır aynı iş parçacığı üzerinde Aşama 2 bildirimleri oluşabilir Not <xref:System.Transactions.PreparingEnlistment.Prepared%2A> yönteminde Aşama 1.</span><span class="sxs-lookup"><span data-stu-id="ef9ee-136">Note that the phase 2 notifications can happen inline on the same thread that called the <xref:System.Transactions.PreparingEnlistment.Prepared%2A> method in phase 1.</span></span> <span data-ttu-id="ef9ee-137">Bu nedenle, sonra herhangi bir iş yapmanız gerektiğini değil <xref:System.Transactions.PreparingEnlistment.Prepared%2A> Aşama 2 bildirimleri almadan önce tamamladınız beklediğiniz araması (örneğin, serbest bırakma kilitler).</span><span class="sxs-lookup"><span data-stu-id="ef9ee-137">As such, you should not do any work after the <xref:System.Transactions.PreparingEnlistment.Prepared%2A> call (for example, releasing locks) that you would expect to have completed before receiving the phase 2 notifications.</span></span>  
  
### <a name="implementing-indoubt"></a><span data-ttu-id="ef9ee-138">Nin şüpheli işlemi olmadığından uygulama</span><span class="sxs-lookup"><span data-stu-id="ef9ee-138">Implementing InDoubt</span></span>  
 <span data-ttu-id="ef9ee-139">Son olarak, uygulamalıdır <xref:System.Transactions.IEnlistmentNotification.InDoubt%2A> geçici kaynak yöneticisi için yöntem.</span><span class="sxs-lookup"><span data-stu-id="ef9ee-139">Finally, you should implement the <xref:System.Transactions.IEnlistmentNotification.InDoubt%2A> method for the volatile resource manager.</span></span> <span data-ttu-id="ef9ee-140">İşlem yöneticisi bir veya daha fazla katılımcıyla iletişimi kaybederse, durumları bilinmiyorsa bu yöntem edenir.</span><span class="sxs-lookup"><span data-stu-id="ef9ee-140">This method is called if the transaction manager loses contact with one or more participants, so their status is unknown.</span></span> <span data-ttu-id="ef9ee-141">Bu durumda, işlem katılımcılarından herhangi birinin tutarsız bir durumda bırakılıp bırakılmadığını daha sonra araştırabilmeniz için bu gerçeği günlüğe kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ef9ee-141">If this occurs, you should log this fact so that you can investigate later whether any of the transaction participants has been left in an inconsistent state.</span></span>  
  
```csharp
public void InDoubt (Enlistment enlistment)  
{  
     // log this  
     enlistment.Done();  
}  
```  
  
## <a name="single-phase-commit-optimization"></a><span data-ttu-id="ef9ee-142">Tek aşaması yürütme en iyi hale getirme</span><span class="sxs-lookup"><span data-stu-id="ef9ee-142">Single Phase Commit Optimization</span></span>  
 <span data-ttu-id="ef9ee-143">Tüm güncelleştirmeleri herhangi bir açık işbirliği yapıldığından tek aşaması yürütme Protokolü çalışma zamanında daha etkilidir.</span><span class="sxs-lookup"><span data-stu-id="ef9ee-143">The Single Phase Commit protocol is more efficient at run time because all updates are done without any explicit coordination.</span></span> <span data-ttu-id="ef9ee-144">Bu protokol hakkında daha fazla bilgi için, [Tek Faz Commit ve Teşvik Edilebilir Tek Faz Bildirimi kullanarak Optimizasyon'a](optimization-spc-and-promotable-spn.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="ef9ee-144">For more information on this protocol, see [Optimization using Single Phase Commit and Promotable Single Phase Notification](optimization-spc-and-promotable-spn.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef9ee-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ef9ee-145">See also</span></span>

- [<span data-ttu-id="ef9ee-146">Tek Aşamalı İşleme ve Yükseltilebilir Tek Aşamalı Bildirim kullanarak en iyi duruma getirme</span><span class="sxs-lookup"><span data-stu-id="ef9ee-146">Optimization using Single Phase Commit and Promotable Single Phase Notification</span></span>](optimization-spc-and-promotable-spn.md)
- [<span data-ttu-id="ef9ee-147">Bir İşlemde Kaynakları Katılımcı Olarak Kaydetme</span><span class="sxs-lookup"><span data-stu-id="ef9ee-147">Enlisting Resources as Participants in a Transaction</span></span>](enlisting-resources-as-participants-in-a-transaction.md)
