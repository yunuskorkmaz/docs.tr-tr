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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 543ea3d1a0f767a10b36e040155e7e9304aca5a9
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="transaction-support"></a><span data-ttu-id="657b0-102">İşlem desteği</span><span class="sxs-lookup"><span data-stu-id="657b0-102">Transaction Support</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="657b0-103">üç farklı işlem modeli destekler.</span><span class="sxs-lookup"><span data-stu-id="657b0-103"> supports three distinct transaction models.</span></span> <span data-ttu-id="657b0-104">Aşağıda bu modeller gerçekleştirilen denetimleri sırasına göre listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="657b0-104">The following lists these models in the order of checks performed.</span></span>  
  
## <a name="explicit-local-transaction"></a><span data-ttu-id="657b0-105">Açık bir yerel işlem</span><span class="sxs-lookup"><span data-stu-id="657b0-105">Explicit Local Transaction</span></span>  
 <span data-ttu-id="657b0-106">Zaman <xref:System.Data.Linq.DataContext.SubmitChanges%2A> gerekiyorsa denir <xref:System.Data.Linq.DataContext.Transaction%2A> özelliği ayarlanmış bir (`IDbTransaction`) işlem, <xref:System.Data.Linq.DataContext.SubmitChanges%2A> çağrısı aynı işlem bağlamında gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="657b0-106">When <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called, if the <xref:System.Data.Linq.DataContext.Transaction%2A> property is set to a (`IDbTransaction`) transaction, the <xref:System.Data.Linq.DataContext.SubmitChanges%2A> call is executed in the context of the same transaction.</span></span>  
  
 <span data-ttu-id="657b0-107">Yürütme veya geri alma işlem başarılı yürütme işleminin ardından, sorumluluğundadır.</span><span class="sxs-lookup"><span data-stu-id="657b0-107">It is your responsibility to commit or rollback the transaction after successful execution of the transaction.</span></span> <span data-ttu-id="657b0-108">İşlem için karşılık gelen bağlantı oluşturmak için kullanılan bağlantı eşleşmelidir <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="657b0-108">The connection corresponding to the transaction must match the connection used for constructing the <xref:System.Data.Linq.DataContext>.</span></span> <span data-ttu-id="657b0-109">Farklı bir bağlantı kullandıysanız özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="657b0-109">An exception is thrown if a different connection is used.</span></span>  
  
## <a name="explicit-distributable-transaction"></a><span data-ttu-id="657b0-110">Açık dağıtılabilir işlem</span><span class="sxs-lookup"><span data-stu-id="657b0-110">Explicit Distributable Transaction</span></span>  
 <span data-ttu-id="657b0-111">Çağırabilirsiniz [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] API'leri (ancak bunlarla sınırlı olmamak dahil olmak üzere <xref:System.Data.Linq.DataContext.SubmitChanges%2A>) etkin bir kapsamda <xref:System.Transactions.Transaction>.</span><span class="sxs-lookup"><span data-stu-id="657b0-111">You can call [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] APIs (including but not limited to <xref:System.Data.Linq.DataContext.SubmitChanges%2A>) in the scope of an active <xref:System.Transactions.Transaction>.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="657b0-112">çağrısı bir işlem kapsamı içinde olan ve yeni bir işlem oluşturmaz algılar.</span><span class="sxs-lookup"><span data-stu-id="657b0-112"> detects that the call is in the scope of a transaction and does not create a new transaction.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="657b0-113">Ayrıca bu durumda bağlantı kesiliyor önler.</span><span class="sxs-lookup"><span data-stu-id="657b0-113"> also avoids closing the connection in this case.</span></span> <span data-ttu-id="657b0-114">Sorgu gerçekleştirebilir ve <xref:System.Data.Linq.DataContext.SubmitChanges%2A> böyle bir işlem bağlamında yürütmeleri.</span><span class="sxs-lookup"><span data-stu-id="657b0-114">You can perform query and <xref:System.Data.Linq.DataContext.SubmitChanges%2A> executions in the context of such a transaction.</span></span>  
  
## <a name="implicit-transaction"></a><span data-ttu-id="657b0-115">Örtük işlem</span><span class="sxs-lookup"><span data-stu-id="657b0-115">Implicit Transaction</span></span>  
 <span data-ttu-id="657b0-116">Çağırdığınızda <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] çağrı kapsamında olup olmadığını görmek için denetimleri bir <xref:System.Transactions.Transaction> veya `Transaction` özelliği (`IDbTransaction`) kullanıcı başlatılmış bir yerel işlem ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="657b0-116">When you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] checks to see whether the call is in the scope of a <xref:System.Transactions.Transaction> or if the `Transaction` property (`IDbTransaction`) is set to a user-started local transaction.</span></span> <span data-ttu-id="657b0-117">Hiçbir işlem bulursa [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] yerel bir işlem başlatır (`IDbTransaction`) ve oluşturulan SQL komutlarını çalıştırmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="657b0-117">If it finds neither transaction, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] starts a local transaction (`IDbTransaction`) and uses it to execute the generated SQL commands.</span></span> <span data-ttu-id="657b0-118">Tüm SQL komutları başarıyla tamamladıktan sonra [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] yerel işlem kaydeder ve döndürür.</span><span class="sxs-lookup"><span data-stu-id="657b0-118">When all SQL commands have been successfully completed, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] commits the local transaction and returns.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="657b0-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="657b0-119">See Also</span></span>  
 [<span data-ttu-id="657b0-120">Arka Plan Bilgileri</span><span class="sxs-lookup"><span data-stu-id="657b0-120">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 [<span data-ttu-id="657b0-121">Nasıl yapılır: İşlemleri Kullanarak Veri Gönderimlerini Ayraç İçine Alma</span><span class="sxs-lookup"><span data-stu-id="657b0-121">How to: Bracket Data Submissions by Using Transactions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-bracket-data-submissions-by-using-transactions.md)
