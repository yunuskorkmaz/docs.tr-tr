---
title: "İşlem desteği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8cceb26e-8d36-4365-8967-58e2e89e0187
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 7c1d438a83f090795a158ade1dfdbb7d2b2df863
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="transaction-support"></a><span data-ttu-id="aed12-102">İşlem desteği</span><span class="sxs-lookup"><span data-stu-id="aed12-102">Transaction Support</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="aed12-103">üç farklı işlem modeli destekler.</span><span class="sxs-lookup"><span data-stu-id="aed12-103"> supports three distinct transaction models.</span></span> <span data-ttu-id="aed12-104">Aşağıda bu modeller gerçekleştirilen denetimleri sırasına göre listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="aed12-104">The following lists these models in the order of checks performed.</span></span>  
  
## <a name="explicit-local-transaction"></a><span data-ttu-id="aed12-105">Açık bir yerel işlem</span><span class="sxs-lookup"><span data-stu-id="aed12-105">Explicit Local Transaction</span></span>  
 <span data-ttu-id="aed12-106">Zaman <xref:System.Data.Linq.DataContext.SubmitChanges%2A> gerekiyorsa denir <xref:System.Data.Linq.DataContext.Transaction%2A> özelliği ayarlanmış bir (`IDbTransaction`) işlem, <xref:System.Data.Linq.DataContext.SubmitChanges%2A> çağrısı aynı işlem bağlamında gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="aed12-106">When <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called, if the <xref:System.Data.Linq.DataContext.Transaction%2A> property is set to a (`IDbTransaction`) transaction, the <xref:System.Data.Linq.DataContext.SubmitChanges%2A> call is executed in the context of the same transaction.</span></span>  
  
 <span data-ttu-id="aed12-107">Yürütme veya geri alma işlem başarılı yürütme işleminin ardından, sorumluluğundadır.</span><span class="sxs-lookup"><span data-stu-id="aed12-107">It is your responsibility to commit or rollback the transaction after successful execution of the transaction.</span></span> <span data-ttu-id="aed12-108">İşlem için karşılık gelen bağlantı oluşturmak için kullanılan bağlantı eşleşmelidir <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="aed12-108">The connection corresponding to the transaction must match the connection used for constructing the <xref:System.Data.Linq.DataContext>.</span></span> <span data-ttu-id="aed12-109">Farklı bir bağlantı kullandıysanız özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="aed12-109">An exception is thrown if a different connection is used.</span></span>  
  
## <a name="explicit-distributable-transaction"></a><span data-ttu-id="aed12-110">Açık dağıtılabilir işlem</span><span class="sxs-lookup"><span data-stu-id="aed12-110">Explicit Distributable Transaction</span></span>  
 <span data-ttu-id="aed12-111">Çağırabilirsiniz [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] API'leri (ancak bunlarla sınırlı olmamak dahil olmak üzere <xref:System.Data.Linq.DataContext.SubmitChanges%2A>) etkin bir kapsamda <xref:System.Transactions.Transaction>.</span><span class="sxs-lookup"><span data-stu-id="aed12-111">You can call [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] APIs (including but not limited to <xref:System.Data.Linq.DataContext.SubmitChanges%2A>) in the scope of an active <xref:System.Transactions.Transaction>.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="aed12-112">çağrısı bir işlem kapsamı içinde olan ve yeni bir işlem oluşturmaz algılar.</span><span class="sxs-lookup"><span data-stu-id="aed12-112"> detects that the call is in the scope of a transaction and does not create a new transaction.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="aed12-113">Ayrıca bu durumda bağlantı kesiliyor önler.</span><span class="sxs-lookup"><span data-stu-id="aed12-113"> also avoids closing the connection in this case.</span></span> <span data-ttu-id="aed12-114">Sorgu gerçekleştirebilir ve <xref:System.Data.Linq.DataContext.SubmitChanges%2A> böyle bir işlem bağlamında yürütmeleri.</span><span class="sxs-lookup"><span data-stu-id="aed12-114">You can perform query and <xref:System.Data.Linq.DataContext.SubmitChanges%2A> executions in the context of such a transaction.</span></span>  
  
## <a name="implicit-transaction"></a><span data-ttu-id="aed12-115">Örtük işlem</span><span class="sxs-lookup"><span data-stu-id="aed12-115">Implicit Transaction</span></span>  
 <span data-ttu-id="aed12-116">Çağırdığınızda <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] çağrı kapsamında olup olmadığını görmek için denetimleri bir <xref:System.Transactions.Transaction> veya `Transaction` özelliği (`IDbTransaction`) kullanıcı başlatılmış bir yerel işlem ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="aed12-116">When you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] checks to see whether the call is in the scope of a <xref:System.Transactions.Transaction> or if the `Transaction` property (`IDbTransaction`) is set to a user-started local transaction.</span></span> <span data-ttu-id="aed12-117">Hiçbir işlem bulursa [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] yerel bir işlem başlatır (`IDbTransaction`) ve oluşturulan SQL komutlarını çalıştırmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="aed12-117">If it finds neither transaction, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] starts a local transaction (`IDbTransaction`) and uses it to execute the generated SQL commands.</span></span> <span data-ttu-id="aed12-118">Tüm SQL komutları başarıyla tamamladıktan sonra [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] yerel işlem kaydeder ve döndürür.</span><span class="sxs-lookup"><span data-stu-id="aed12-118">When all SQL commands have been successfully completed, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] commits the local transaction and returns.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aed12-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="aed12-119">See Also</span></span>  
 [<span data-ttu-id="aed12-120">Arka plan bilgileri</span><span class="sxs-lookup"><span data-stu-id="aed12-120">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 [<span data-ttu-id="aed12-121">Nasıl yapılır: veri gönderimleri işlemleri kullanarak köşeli ayraç</span><span class="sxs-lookup"><span data-stu-id="aed12-121">How to: Bracket Data Submissions by Using Transactions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-bracket-data-submissions-by-using-transactions.md)
