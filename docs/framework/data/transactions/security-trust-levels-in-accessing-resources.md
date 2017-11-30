---
title: "Kaynaklara erişimde güvenlik güven düzeyleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fb5be924-317d-4d69-b33a-3d18ecfb9d6e
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d4cefe74b745eb4a1c71124176985c548f9b1244
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="security-trust-levels-in-accessing-resources"></a><span data-ttu-id="14f41-102">Kaynaklara erişimde güvenlik güven düzeyleri</span><span class="sxs-lookup"><span data-stu-id="14f41-102">Security Trust Levels in Accessing Resources</span></span>
<span data-ttu-id="14f41-103">Bu konuda kaynak türleri sınırlı erişimi nasıl ele alınmıştır, <xref:System.Transactions> kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="14f41-103">This topic discusses how access is restricted on the types of resources that <xref:System.Transactions> exposes.</span></span>  
  
 <span data-ttu-id="14f41-104">Üç ana düzeyi için bir güven <xref:System.Transactions>.</span><span class="sxs-lookup"><span data-stu-id="14f41-104">There are three main levels of trust for <xref:System.Transactions>.</span></span> <span data-ttu-id="14f41-105">Güven düzeyleri kaynak türleri göre tanımlanır, <xref:System.Transactions> kullanıma sunar ve bu kaynaklara erişmek için gerekli güven düzeyi.</span><span class="sxs-lookup"><span data-stu-id="14f41-105">The trust levels are defined based on the types of resources that <xref:System.Transactions> exposes, and the level of trust that should be required to access those resources.</span></span> <span data-ttu-id="14f41-106">Kaynakları, <xref:System.Transactions> erişim sağlar sistem bellek, paylaşılan işlem geniş kaynakları ve uluslararası sistem kaynakları.</span><span class="sxs-lookup"><span data-stu-id="14f41-106">The resources that <xref:System.Transactions> provides access to are system memory, shared process wide resources, and system wide resources.</span></span> <span data-ttu-id="14f41-107">Düzeyleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="14f41-107">The levels are:</span></span>  
  
-   <span data-ttu-id="14f41-108">**AllowPartiallyTrustedCallers** (APTCA) işlemleri tek bir uygulama etki alanı içinde kullanan uygulamalar için.</span><span class="sxs-lookup"><span data-stu-id="14f41-108">**AllowPartiallyTrustedCallers** (APTCA) for applications using transactions within a single application domain.</span></span>  
  
-   <span data-ttu-id="14f41-109">**DistributedTransactionPermission** (DTP) dağıtılmış işlemler kullanan uygulamalar için.</span><span class="sxs-lookup"><span data-stu-id="14f41-109">**DistributedTransactionPermission** (DTP) for applications using distributed transactions.</span></span>  
  
-   <span data-ttu-id="14f41-110">Dayanıklı kaynakları, yapılandırma yönetimi uygulamaları ve eski birlikte çalışma uygulamaları için tam güven.</span><span class="sxs-lookup"><span data-stu-id="14f41-110">Full trust for durable resources, configuration management applications, and legacy interop applications.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="14f41-111">Herhangi bir Kimliğine bürünülen bağlamları olan liste arabirimler çağırmalıdır değil.</span><span class="sxs-lookup"><span data-stu-id="14f41-111">You should not call any of the enlistment interfaces with impersonated contexts.</span></span>  
  
## <a name="trust-levels"></a><span data-ttu-id="14f41-112">Güven düzeyleri</span><span class="sxs-lookup"><span data-stu-id="14f41-112">Trust Levels</span></span>  
  
### <a name="aptca-partial-trust"></a><span data-ttu-id="14f41-113">APTCA (kısmi güven)</span><span class="sxs-lookup"><span data-stu-id="14f41-113">APTCA (Partial Trust)</span></span>  
 <span data-ttu-id="14f41-114"><xref:System.Transactions> Derleme ile işaretlendiğinden kısmen güvenilen kod tarafından çağrılabilir **AllowPartiallyTrustedCallers** özniteliği (APTCA).</span><span class="sxs-lookup"><span data-stu-id="14f41-114">The <xref:System.Transactions> assembly can be called by partially trusted code because it has been marked with the **AllowPartiallyTrustedCallers** attribute (APTCA).</span></span> <span data-ttu-id="14f41-115">Bu öznitelik temelde örtük kaldırır <xref:System.Security.Permissions.SecurityAction.LinkDemand> için **FullTrust** diğer bir deyişle izni Aksi takdirde otomatik olarak yerleştirilen her türde genel olarak erişilebilir her yöntemin üzerinde.</span><span class="sxs-lookup"><span data-stu-id="14f41-115">This attribute essentially removes the implicit <xref:System.Security.Permissions.SecurityAction.LinkDemand> for the **FullTrust** permission set that is otherwise automatically placed on each publicly accessible method in each type.</span></span> <span data-ttu-id="14f41-116">Ancak, bazı türleri ve üyeleri hala daha güçlü izinleri gerektirir.</span><span class="sxs-lookup"><span data-stu-id="14f41-116">However, some types and members still require stronger permissions.</span></span>  
  
 <span data-ttu-id="14f41-117">APTCA özniteliği uygulamaların tek bir uygulama etki alanı içinde kısmi güvende işlemleri kullanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="14f41-117">The APTCA attribute enables applications to use transactions in partial trust within a single application domain.</span></span> <span data-ttu-id="14f41-118">Bu, ilerletilen olmayan işlemler ve hata işleme için kullanılan geçici listeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="14f41-118">This enables non-escalated transactions and volatile enlistments that can be used for error handling.</span></span> <span data-ttu-id="14f41-119">İşlenen karma tablo ve onu kullanan bir uygulama bu bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="14f41-119">One example of this is a transacted hash table and an application that uses it.</span></span> <span data-ttu-id="14f41-120">Veriler, eklenen ve tek bir işlem altında karma tablosundan kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="14f41-120">Data can be added to and removed from the hash table under a single transaction.</span></span> <span data-ttu-id="14f41-121">İşlem daha sonra geri alınması durumunda, karma tablo bu işlem altında yapılan tüm değişiklikler geri alınabilir.</span><span class="sxs-lookup"><span data-stu-id="14f41-121">If the transaction is later rolled back, all of the changes made to the hash table under that transaction can be undone.</span></span>  
  
### <a name="distributedtransactionpermission-dtp"></a><span data-ttu-id="14f41-122">DistributedTransactionPermission (DTP)</span><span class="sxs-lookup"><span data-stu-id="14f41-122">DistributedTransactionPermission (DTP)</span></span>  
 <span data-ttu-id="14f41-123">Zaman bir <xref:System.Transactions> MSDTC tarafından yönetilmek üzere işlem ilerletilen <xref:System.Transactions> taleplerini <xref:System.Transactions.DistributedTransactionPermission> dağıtılmış işlem oluşturmak için (DTP).</span><span class="sxs-lookup"><span data-stu-id="14f41-123">When a <xref:System.Transactions> transaction is escalated to be managed by MSDTC, <xref:System.Transactions> demands the <xref:System.Transactions.DistributedTransactionPermission> (DTP) to create the distributed transaction.</span></span> <span data-ttu-id="14f41-124">Bu işlemin ilerletilen neden kodu anlamına gelir (gibi seri hale getirme veya ek dayanıklı kayıtlar aracılığıyla) DTP verilmiş olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="14f41-124">This means that the code that causes the transaction to be escalated (such as through serialization or additional durable enlistments) would need to be granted DTP.</span></span> <span data-ttu-id="14f41-125">İlk olarak oluşturulan kodu <xref:System.Transactions> işlem mutlaka gerekmez bu izne sahip.</span><span class="sxs-lookup"><span data-stu-id="14f41-125">The code that originally created the <xref:System.Transactions> transaction does not necessarily need to possess this permission.</span></span>  
  
### <a name="fulltrust-link-demands"></a><span data-ttu-id="14f41-126">FullTrust bağlantı talepleri</span><span class="sxs-lookup"><span data-stu-id="14f41-126">FullTrust Link Demands</span></span>  
 <span data-ttu-id="14f41-127">Bu izin düzeyi dayanıklı kaynaklara yazma uygulamaları kısıtlamak için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="14f41-127">This permission level is intended to restrict applications that are writing to durable resources.</span></span> <span data-ttu-id="14f41-128">Başarısızlık durumunda, uygulama kalıcı veri güncelleştirebilmeniz için son işlem sonucunu belirlemek için işlem yöneticisi ile kurtarmanız mümkün olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="14f41-128">Upon failure, the application needs to be able to recover with the transaction manager to determine the final outcome of the transaction, so that it can update permanent data.</span></span> <span data-ttu-id="14f41-129">Bu tür bir uygulama, sağlam kaynak yöneticisi olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="14f41-129">This type of application is known as a durable source manager.</span></span> <span data-ttu-id="14f41-130">Bir Klasik bu tür bir uygulama SQL örnektir.</span><span class="sxs-lookup"><span data-stu-id="14f41-130">A classic example of this type of application is SQL.</span></span>  
  
 <span data-ttu-id="14f41-131">Kurtarmayı etkinleştirmek için bu tür bir uygulama kalıcı olarak sistem kaynaklarının kullanılmasına olanağı vardır.</span><span class="sxs-lookup"><span data-stu-id="14f41-131">To enable recovery, this type of application has the ability to permanently consume system resources.</span></span> <span data-ttu-id="14f41-132">Bu durum, kurtarılabilir işlem yöneticisi işlemde katılan tüm dayanıklı kaynak yöneticileri sonucu aldığınız onaylayabilirsiniz kadar taahhüt işlemler unutmamanız gerekir çünkü.</span><span class="sxs-lookup"><span data-stu-id="14f41-132">This is because the recoverable transaction manager must remember transactions that have committed until it can confirm that all durable resource managers that are participating in the transaction have received the outcome.</span></span> <span data-ttu-id="14f41-133">Bu nedenle, bu tür bir uygulama tam güven gerektiren ve sürece çalıştırılmamalıdır güven düzeyi verilmiş.</span><span class="sxs-lookup"><span data-stu-id="14f41-133">Therefore, this type of application requires full trust and should not be run unless that level of trust has been granted.</span></span>  
  
 <span data-ttu-id="14f41-134">Dayanıklı listeler ve kurtarma hakkında daha fazla bilgi için bkz: [kaydetme kaynakları bir işlemde katılımcı olarak](../../../../docs/framework/data/transactions/enlisting-resources-as-participants-in-a-transaction.md) ve [kurtarma gerçekleştirme](../../../../docs/framework/data/transactions/performing-recovery.md) Konular.</span><span class="sxs-lookup"><span data-stu-id="14f41-134">For more information on durable enlistments and recovery, see the [Enlisting Resources as Participants in a Transaction](../../../../docs/framework/data/transactions/enlisting-resources-as-participants-in-a-transaction.md) and [Performing Recovery](../../../../docs/framework/data/transactions/performing-recovery.md) topics.</span></span>  
  
 <span data-ttu-id="14f41-135">COM + ile birlikte çalışma eski iş gerçekleştiren uygulamalar da tam güven sağlamak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="14f41-135">Applications that perform legacy interop work with COM+ are also required to have full trust.</span></span>  
  
 <span data-ttu-id="14f41-136">Türlerinin bir listesi aşağıda verilmiştir ve kısmen tarafından çağrılabilir olmayan üyeler güvenilen kodu ile donatılmış olduğundan **FullTrust** bildirim temelli güvenlik özniteliği:</span><span class="sxs-lookup"><span data-stu-id="14f41-136">The following is a list of types and members that are not callable by partially trusted code because they are decorated with the **FullTrust** declarative security attribute:</span></span>  
  
 `PermissionSetAttribute(SecurityAction.LinkDemand, Name := "FullTrust")`  
  
-   <xref:System.Transactions.Transaction.EnlistDurable%2A?displayProperty=nameWithType>  
  
-   <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A>  
  
-   <xref:System.Transactions.TransactionInterop>  
  
-   <xref:System.Transactions.TransactionManager.DistributedTransactionStarted>  
  
-   <xref:System.Transactions.HostCurrentTransactionCallback>  
  
-   <xref:System.Transactions.TransactionManager.Reenlist%2A>  
  
-   <xref:System.Transactions.TransactionManager.RecoveryComplete%2A>  
  
-   <xref:System.Transactions.TransactionScope.%23ctor%28System.Transactions.TransactionScopeOption%2CSystem.Transactions.TransactionOptions%2CSystem.Transactions.EnterpriseServicesInteropOption%29>  
  
 <span data-ttu-id="14f41-137">Anında arayanlar sahip olması gerekmez, yalnızca **FullTrust** izni Ayarla yukarıdaki türleri veya yöntemleri kullanmak için.</span><span class="sxs-lookup"><span data-stu-id="14f41-137">Only the immediate caller is required to possess the **FullTrust** permission set to use the above types or methods.</span></span>
