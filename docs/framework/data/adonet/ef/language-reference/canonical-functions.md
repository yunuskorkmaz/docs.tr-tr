---
title: "Kurallı işlevleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bbcc9928-36ea-4dff-9e31-96549ffed958
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 1f676c88691f0ba80ca682d720adf649ab612cfb
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="canonical-functions"></a><span data-ttu-id="1146f-102">Kurallı işlevleri</span><span class="sxs-lookup"><span data-stu-id="1146f-102">Canonical Functions</span></span>
<span data-ttu-id="1146f-103">Bu bölümde, tüm veri sağlayıcıları tarafından desteklenir ve tüm sorgulanırken teknolojiler tarafından kullanılan kurallı işlevleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1146f-103">This section discusses canonical functions that are supported by all data providers, and can be used by all querying technologies.</span></span> <span data-ttu-id="1146f-104">Kurallı işlevleri bir sağlayıcı tarafından genişletilemez.</span><span class="sxs-lookup"><span data-stu-id="1146f-104">Canonical functions cannot be extended by a provider.</span></span>  
  
 <span data-ttu-id="1146f-105">Kurallı bu işlevler sağlayıcı için karşılık gelen bir veri kaynağı işlevi çevrilir.</span><span class="sxs-lookup"><span data-stu-id="1146f-105">These canonical functions will be translated to the corresponding data source functionality for the provider.</span></span> <span data-ttu-id="1146f-106">Bu veri kaynakları arasında bir ortak biçiminde ifade işlev çağrılarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="1146f-106">This allows for function invocations expressed in a common form across data sources.</span></span>  
  
 <span data-ttu-id="1146f-107">Kurallı bu işlevler veri kaynaklarından bağımsız olduğundan, kurallı işlevleri bağımsız değişkeni ve dönüş türleri kavramsal modelde türleri açısından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="1146f-107">Because these canonical functions are independent of data sources, argument and return types of canonical functions are defined in terms of types in the conceptual model.</span></span> <span data-ttu-id="1146f-108">Ancak, bazı veri kaynakları, kavramsal modelde tüm türleri desteklemeyebilir.</span><span class="sxs-lookup"><span data-stu-id="1146f-108">However, some data sources might not support all types in the conceptual model.</span></span>  
  
 <span data-ttu-id="1146f-109">Ne zaman kurallı işlevleri kullanıldığı bir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu, uygun işlevi veri kaynağında çağrılır.</span><span class="sxs-lookup"><span data-stu-id="1146f-109">When canonical functions are used in an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query, the appropriate function will be called at the data source.</span></span>  
  
 <span data-ttu-id="1146f-110">Null giriş davranış ve hata koşullarını açıkça belirtilen tüm kurallı işlevleri vardır.</span><span class="sxs-lookup"><span data-stu-id="1146f-110">All canonical functions have both null-input behavior and error conditions explicitly specified.</span></span> <span data-ttu-id="1146f-111">Depo sağlayıcıları uyumlu bu davranışı olması gerekir, ancak [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] Bu davranış zorlamaz.</span><span class="sxs-lookup"><span data-stu-id="1146f-111">Store providers should comply with that behavior, but [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] does not enforce this behavior.</span></span>  
  
 <span data-ttu-id="1146f-112">Karşı LINQ senaryoları için sorgular [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] temel alınan veri kaynağında yöntemlerine eşleme CLR yöntemlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="1146f-112">For LINQ scenarios, queries against the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] involve mapping CLR methods to methods in the underlying data source.</span></span> <span data-ttu-id="1146f-113">Kurallı İşlevler, CLR yöntemleri eşlemeye belirli bir yöntemlerini oluşturmak doğru harita, bağımsız olarak veri kaynağı.</span><span class="sxs-lookup"><span data-stu-id="1146f-113">The CLR methods map to canonical functions, so that a specific set of methods will correctly map, regardless of the data source.</span></span>  
  
## <a name="canonical-functions-namespace"></a><span data-ttu-id="1146f-114">Kurallı işlevleri Namespace</span><span class="sxs-lookup"><span data-stu-id="1146f-114">Canonical Functions Namespace</span></span>  
 <span data-ttu-id="1146f-115">Kurallı işlevi için ad alanı <xref:System.Data.Metadata.Edm>.</span><span class="sxs-lookup"><span data-stu-id="1146f-115">The namespace for canonical function is <xref:System.Data.Metadata.Edm>.</span></span> <span data-ttu-id="1146f-116"><xref:System.Data.Metadata.Edm> Ad alanındaki tüm sorgular otomatik olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="1146f-116">The <xref:System.Data.Metadata.Edm> namespace is automatically included in all queries.</span></span> <span data-ttu-id="1146f-117">Ancak, başka bir ad alanı içe aktarılırsa kurallı işlevi olarak aynı ada sahip bir işlevi içeren (içinde <xref:System.Data.Metadata.Edm> ad alanı), ad alanı belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="1146f-117">However, if another namespace is imported that contains a function with the same name as a canonical function (in the <xref:System.Data.Metadata.Edm> namespace), you must specify the namespace.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1146f-118">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="1146f-118">In This Section</span></span>  
 [<span data-ttu-id="1146f-119">Toplu Kurallı İşlevler</span><span class="sxs-lookup"><span data-stu-id="1146f-119">Aggregate Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)  
 <span data-ttu-id="1146f-120">Toplama anlatılmaktadır [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kurallı işlevleri.</span><span class="sxs-lookup"><span data-stu-id="1146f-120">Discusses aggregate [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="1146f-121">Kurallı Matematik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="1146f-121">Math Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/math-canonical-functions.md)  
 <span data-ttu-id="1146f-122">Matematik anlatılmaktadır [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kurallı işlevleri.</span><span class="sxs-lookup"><span data-stu-id="1146f-122">Discusses math [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="1146f-123">Kurallı Dize İşlevleri</span><span class="sxs-lookup"><span data-stu-id="1146f-123">String Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)  
 <span data-ttu-id="1146f-124">Dize anlatılmaktadır [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kurallı işlevleri.</span><span class="sxs-lookup"><span data-stu-id="1146f-124">Discusses string [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="1146f-125">Kurallı Tarih ve Saat İşlevleri</span><span class="sxs-lookup"><span data-stu-id="1146f-125">Date and Time Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)  
 <span data-ttu-id="1146f-126">Tarih ve saat anlatılmaktadır [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kurallı işlevleri.</span><span class="sxs-lookup"><span data-stu-id="1146f-126">Discusses date and time [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="1146f-127">Bit Düzeyinde Kurallı İşlevler</span><span class="sxs-lookup"><span data-stu-id="1146f-127">Bitwise Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/bitwise-canonical-functions.md)  
 <span data-ttu-id="1146f-128">Bit düzeyinde ele [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kurallı işlevleri.</span><span class="sxs-lookup"><span data-stu-id="1146f-128">Discusses bitwise [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="1146f-129">Uzamsal İşlevler</span><span class="sxs-lookup"><span data-stu-id="1146f-129">Spatial Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/spatial-functions.md)  
 <span data-ttu-id="1146f-130">Spatial ele [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kurallı işlevleri.</span><span class="sxs-lookup"><span data-stu-id="1146f-130">Discusses Spatial [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="1146f-131">Diğer Kurallı İşlevler</span><span class="sxs-lookup"><span data-stu-id="1146f-131">Other Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/other-canonical-functions.md)  
 <span data-ttu-id="1146f-132">Bit düzeyinde, tarih, dize, matematik veya toplu olarak sınıflandırılan değil işlevleri açıklanır.</span><span class="sxs-lookup"><span data-stu-id="1146f-132">Discusses functions not classified as bitwise, date/time, string, math, or aggregate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1146f-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1146f-133">See Also</span></span>  
 [<span data-ttu-id="1146f-134">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="1146f-134">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [<span data-ttu-id="1146f-135">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="1146f-135">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="1146f-136">SQL Server İşlevleri ile Kurallı Kavramsal Model Eşlemesi</span><span class="sxs-lookup"><span data-stu-id="1146f-136">Conceptual Model Canonical to SQL Server Functions Mapping</span></span>](../../../../../../docs/framework/data/adonet/ef/conceptual-model-canonical-to-sql-server-functions-mapping.md)  
 [<span data-ttu-id="1146f-137">Kullanıcı Tanımlı İşlevler</span><span class="sxs-lookup"><span data-stu-id="1146f-137">User-Defined Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md)
