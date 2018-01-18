---
title: "N katmanlı ve uzak uygulamalarla LINQ-SQL"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 854a1cdd-53cb-45f5-83ca-63962a9b3598
caps.latest.revision: "5"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 293ebf52b6179ec02f65c81112ee24c9b6322eae
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="n-tier-and-remote-applications-with-linq-to-sql"></a><span data-ttu-id="cd79c-102">N katmanlı ve uzak uygulamalarla LINQ-SQL</span><span class="sxs-lookup"><span data-stu-id="cd79c-102">N-Tier and Remote Applications with LINQ to SQL</span></span>
<span data-ttu-id="cd79c-103">Kullanan n katmanlı veya çok katmanlı uygulamalar oluşturabileceğiniz [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cd79c-103">You can create n-tier or multitier applications that use [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="cd79c-104">Genellikle, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] veri bağlamı, sınıflar ve sorgu oluşturma mantığı bulunur Orta katmanda (DAL) veri erişim katmanı.</span><span class="sxs-lookup"><span data-stu-id="cd79c-104">Typically, the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] data context, entity classes, and query construction logic are located on the middle tier as the data access layer (DAL).</span></span> <span data-ttu-id="cd79c-105">İş mantığı ve kalıcı olmayan veriler tamamen kısmi sınıflar ve yöntemler varlıkları ve veri bağlamı içinde uygulanabilir veya ayrı sınıflarda uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="cd79c-105">Business logic and any non-persistent data can be implemented completely in partial classes and methods of entities and the data context, or it can be implemented in separate classes.</span></span>  
  
 <span data-ttu-id="cd79c-106">İstemci veya sunu katmanı orta katman uzak arabirimde yöntemleri çağırır ve bu katmanda DAL sorgular veya eşlendiği saklı yordamlar yürütecek <xref:System.Data.Linq.DataContext> yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="cd79c-106">The client or presentation layer calls methods on the middle-tier's remote interface, and the DAL on that tier will execute queries or stored procedures that are mapped to <xref:System.Data.Linq.DataContext> methods.</span></span> <span data-ttu-id="cd79c-107">Orta katman veri istemcilere genellikle varlıklar veya proxy nesneleri XML gösterimlerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="cd79c-107">The middle tier returns the data to clients typically as XML representations of entities or proxy objects.</span></span>  
  
 <span data-ttu-id="cd79c-108">Orta katmanda varlıklar durumlarına izler ve ertelenmiş yüklenmesini ve değişiklikleri teslimini veritabanına yöneten veri bağlamı tarafından oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="cd79c-108">On the middle tier, entities are created by the data context, which tracks their state, and manages deferred loading from and submission of changes to the database.</span></span> <span data-ttu-id="cd79c-109">Bu varlıklar "bağlı" `DataContext`.</span><span class="sxs-lookup"><span data-stu-id="cd79c-109">These entities are "attached" to the `DataContext`.</span></span> <span data-ttu-id="cd79c-110">Varlıkları seri hale getirme yoluyla başka bir katmana gönderildikten sonra ancak başka bir deyişle, ayrılmış, olduklarında `DataContext` durumlarına artık izlemektir.</span><span class="sxs-lookup"><span data-stu-id="cd79c-110">However, after the entities are sent to another tier through serialization, they become detached, which means the `DataContext` is no longer tracking their state.</span></span> <span data-ttu-id="cd79c-111">İstemci güncelleştirmelerini geri gönderir varlıkları yeniden, önce veri bağlamı için [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] değişiklikler veritabanına gönderebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cd79c-111">Entities that the client sends back for updates must be reattached to the data context before [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] can submit the changes to the database.</span></span> <span data-ttu-id="cd79c-112">İstemci özgün değerler sağlamaktan sorumludur ve/veya bu iyimser eşzamanlılık denetimleri için gerekli olduğunda zaman damgaları orta katman yedekleyin.</span><span class="sxs-lookup"><span data-stu-id="cd79c-112">The client is responsible for providing original values and/or timestamps back to the middle tier if those are required for optimistic concurrency checks.</span></span>  
  
 <span data-ttu-id="cd79c-113">ASP.NET uygulamalarında <xref:System.Web.UI.WebControls.LinqDataSource> çoğu bu karmaşıklık yönetir.</span><span class="sxs-lookup"><span data-stu-id="cd79c-113">In ASP.NET applications, the <xref:System.Web.UI.WebControls.LinqDataSource> manages most of this complexity.</span></span> <span data-ttu-id="cd79c-114">Daha fazla bilgi için bkz: [NIB: LinqDataSource Web sunucusu denetimine genel bakış](http://msdn.microsoft.com/en-us/104cfc3f-7385-47d3-8a51-830dfa791136).</span><span class="sxs-lookup"><span data-stu-id="cd79c-114">For more information, see [NIB: LinqDataSource Web Server Control Overview](http://msdn.microsoft.com/en-us/104cfc3f-7385-47d3-8a51-830dfa791136).</span></span>  
  
## <a name="additional-resources"></a><span data-ttu-id="cd79c-115">Ek Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="cd79c-115">Additional Resources</span></span>  
 <span data-ttu-id="cd79c-116">Kullanan n katmanlı uygulamalar uygulama hakkında daha fazla bilgi için [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="cd79c-116">For more information about how to implement n-tier applications that use [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], see the following topics:</span></span>  
  
-   [<span data-ttu-id="cd79c-117">ASP.NET ile LINQ to SQL N Katmanı</span><span class="sxs-lookup"><span data-stu-id="cd79c-117">LINQ to SQL N-Tier with ASP.NET</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/linq-to-sql-n-tier-with-aspnet.md)  
  
-   [<span data-ttu-id="cd79c-118">Web Hizmetleri ile LINQ to SQL N Katmanı</span><span class="sxs-lookup"><span data-stu-id="cd79c-118">LINQ to SQL N-Tier with Web Services</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/linq-to-sql-n-tier-with-web-services.md)  
  
-   [<span data-ttu-id="cd79c-119">Sıkıca Bağlı İstemci-Sunucu Uygulamaları ile LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="cd79c-119">LINQ to SQL with Tightly-Coupled Client-Server Applications</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/linq-to-sql-with-tightly-coupled-client-server-applications.md)  
  
-   [<span data-ttu-id="cd79c-120">N Katmanı İş Mantığını Uygulama</span><span class="sxs-lookup"><span data-stu-id="cd79c-120">Implementing N-Tier Business Logic</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/implementing-business-logic-linq-to-sql.md)  
  
-   [<span data-ttu-id="cd79c-121">N Katmanı Uygulamalarında Veri Alma ve CUD İşlemleri (LINQ to SQL)</span><span class="sxs-lookup"><span data-stu-id="cd79c-121">Data Retrieval and CUD Operations in N-Tier Applications (LINQ to SQL)</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-retrieval-and-cud-operations-in-n-tier-applications.md)  
  
 <span data-ttu-id="cd79c-122">ADO.NET veri kümelerini kullanan n katmanlı uygulamalar hakkında daha fazla bilgi için bkz: [n katmanlı uygulamalarda veri kümeleriyle çalışmak](http://msdn.microsoft.com/library/f6ae2ee0-ea5f-4a79-8f4b-e21c115afb20).</span><span class="sxs-lookup"><span data-stu-id="cd79c-122">For more information about n-tier applications that use ADO.NET DataSets, see [Work with datasets in n-tier applications](http://msdn.microsoft.com/library/f6ae2ee0-ea5f-4a79-8f4b-e21c115afb20).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd79c-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cd79c-123">See Also</span></span>  
 [<span data-ttu-id="cd79c-124">Arka Plan Bilgileri</span><span class="sxs-lookup"><span data-stu-id="cd79c-124">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
