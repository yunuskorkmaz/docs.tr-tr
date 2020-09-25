---
title: 'Nasıl yapılır: Veritabanına Değişiklikleri Gönderme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c7cba174-9d40-491d-b32c-f2d73b7e9eab
ms.openlocfilehash: 5952cce5469d7a7e13e8b896f91ea1279fd62d8b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197046"
---
# <a name="how-to-submit-changes-to-the-database"></a><span data-ttu-id="8c4f4-102">Nasıl yapılır: Veritabanına Değişiklikleri Gönderme</span><span class="sxs-lookup"><span data-stu-id="8c4f4-102">How to: Submit Changes to the Database</span></span>

<span data-ttu-id="8c4f4-103">Nesneleriniz üzerinde kaç değişiklik yaptığınız fark olursa olsun, değişiklikler yalnızca bellek içi çoğaltmalar için yapılır.</span><span class="sxs-lookup"><span data-stu-id="8c4f4-103">Regardless of how many changes you make to your objects, changes are made only to in-memory replicas.</span></span> <span data-ttu-id="8c4f4-104">Veritabanındaki gerçek verilerde değişiklik yapulaştınız.</span><span class="sxs-lookup"><span data-stu-id="8c4f4-104">You have made no changes to the actual data in the database.</span></span> <span data-ttu-id="8c4f4-105">Üzerinde açıkça çağrı yapana kadar değişiklikleriniz sunucuya aktarılmaz <xref:System.Data.Linq.DataContext.SubmitChanges%2A> <xref:System.Data.Linq.DataContext> .</span><span class="sxs-lookup"><span data-stu-id="8c4f4-105">Your changes are not transmitted to the server until you explicitly call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> on the <xref:System.Data.Linq.DataContext>.</span></span>  
  
 <span data-ttu-id="8c4f4-106">Bu çağrıyı yaptığınızda, <xref:System.Data.Linq.DataContext> değişikliklerinizi eşdeğer SQL komutlarına çevirmeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="8c4f4-106">When you make this call, the <xref:System.Data.Linq.DataContext> tries to translate your changes into equivalent SQL commands.</span></span> <span data-ttu-id="8c4f4-107">Bu eylemleri geçersiz kılmak için kendi özel mantığınızı kullanabilirsiniz, ancak gönderim sırası <xref:System.Data.Linq.DataContext> *değişiklik işlemcisi*olarak bilinen bir hizmet tarafından düzenlenir.</span><span class="sxs-lookup"><span data-stu-id="8c4f4-107">You can use your own custom logic to override these actions, but the order of submission is orchestrated by a service of the <xref:System.Data.Linq.DataContext> known as the *change processor*.</span></span> <span data-ttu-id="8c4f4-108">Olayların sırası aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="8c4f4-108">The sequence of events is as follows:</span></span>  
  
1. <span data-ttu-id="8c4f4-109"><xref:System.Data.Linq.DataContext.SubmitChanges%2A>' İ çağırdığınızda, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] yeni örneklerin eklenmiş olup olmadığını anlamak için bilinen nesneler kümesini inceler.</span><span class="sxs-lookup"><span data-stu-id="8c4f4-109">When you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] examines the set of known objects to determine whether new instances have been attached to them.</span></span> <span data-ttu-id="8c4f4-110">Varsa, bu yeni örnekler izlenen nesneler kümesine eklenir.</span><span class="sxs-lookup"><span data-stu-id="8c4f4-110">If they have, these new instances are added to the set of tracked objects.</span></span>  
  
2. <span data-ttu-id="8c4f4-111">Bekleyen değişiklikleri olan tüm nesneler, aralarındaki bağımlılıklara göre nesneler dizisine göre sıralanır.</span><span class="sxs-lookup"><span data-stu-id="8c4f4-111">All objects that have pending changes are ordered into a sequence of objects based on the dependencies between them.</span></span> <span data-ttu-id="8c4f4-112">Değişiklikleri diğer nesnelere bağımlı olan nesneler bağımlılıklarından sonra sıralı.</span><span class="sxs-lookup"><span data-stu-id="8c4f4-112">Objects whose changes depend on other objects are sequenced after their dependencies.</span></span>  
  
3. <span data-ttu-id="8c4f4-113">Herhangi bir fiili değişiklik iletilmeden hemen önce, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] bireysel komutların serisini kapsüllemek için bir işlem başlatır.</span><span class="sxs-lookup"><span data-stu-id="8c4f4-113">Immediately before any actual changes are transmitted, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] starts a transaction to encapsulate the series of individual commands.</span></span>  
  
4. <span data-ttu-id="8c4f4-114">Nesnelerdeki değişiklikler tek bir SQL komutlarına çevrilir ve sunucusuna gönderilir.</span><span class="sxs-lookup"><span data-stu-id="8c4f4-114">The changes to the objects are translated one by one to SQL commands and sent to the server.</span></span>  
  
 <span data-ttu-id="8c4f4-115">Bu noktada, veritabanı tarafından algılanan tüm hatalar gönderim işleminin durdurulmasına neden olur ve bir özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="8c4f4-115">At this point, any errors detected by the database cause the submission process to stop, and an exception is raised.</span></span> <span data-ttu-id="8c4f4-116">Veritabanında yapılan tüm değişiklikler, hiçbir gönderenle gerçekleşmediği için geri alınır.</span><span class="sxs-lookup"><span data-stu-id="8c4f4-116">All changes to the database are rolled back as if no submissions ever occurred.</span></span> <span data-ttu-id="8c4f4-117"><xref:System.Data.Linq.DataContext>Hala tüm değişikliklerin tam kaydına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="8c4f4-117">The <xref:System.Data.Linq.DataContext> still has a full recording of all changes.</span></span> <span data-ttu-id="8c4f4-118">Bu nedenle, <xref:System.Data.Linq.DataContext.SubmitChanges%2A> Aşağıdaki kod örneğinde olduğu gibi sorunu düzeltmeyi ve yeniden aramayı deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8c4f4-118">You can therefore try to correct the problem and call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> again, as in the code example that follows.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8c4f4-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="8c4f4-119">Example</span></span>  

 <span data-ttu-id="8c4f4-120">Gönderim etrafındaki işlem başarıyla tamamlandığında, <xref:System.Data.Linq.DataContext> değişiklik izleme bilgilerini yoksayarak nesnelerdeki değişiklikleri kabul eder.</span><span class="sxs-lookup"><span data-stu-id="8c4f4-120">When the transaction around the submission is completed successfully, the <xref:System.Data.Linq.DataContext> accepts the changes to the objects by ignoring the change-tracking information.</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#1)]
 [!code-vb[DLinqSubmittingChanges#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="8c4f4-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8c4f4-121">See also</span></span>

- [<span data-ttu-id="8c4f4-122">Nasıl yapılır: Çakışan Gönderimleri Algılama ve Çözümleme</span><span class="sxs-lookup"><span data-stu-id="8c4f4-122">How to: Detect and Resolve Conflicting Submissions</span></span>](how-to-detect-and-resolve-conflicting-submissions.md)
- [<span data-ttu-id="8c4f4-123">Nasıl yapılır: Değişiklik Çakışmalarını Yönetme</span><span class="sxs-lookup"><span data-stu-id="8c4f4-123">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
- [<span data-ttu-id="8c4f4-124">Örnek Veritabanları İndirme</span><span class="sxs-lookup"><span data-stu-id="8c4f4-124">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
- [<span data-ttu-id="8c4f4-125">Veri Değişiklikleri Yapma ve Gönderme</span><span class="sxs-lookup"><span data-stu-id="8c4f4-125">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)
