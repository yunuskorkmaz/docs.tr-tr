---
description: 'Daha fazla bilgi edinin: kurallı Işlevler'
title: Kurallı İşlevler
ms.date: 03/30/2017
ms.assetid: bbcc9928-36ea-4dff-9e31-96549ffed958
ms.openlocfilehash: 6e84c4b5199d38e2efac44cf7e69c72abb1663f6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99739514"
---
# <a name="canonical-functions"></a><span data-ttu-id="112d0-103">Kurallı İşlevler</span><span class="sxs-lookup"><span data-stu-id="112d0-103">Canonical Functions</span></span>

<span data-ttu-id="112d0-104">Bu bölümde tüm veri sağlayıcıları tarafından desteklenen ve tüm sorgulama teknolojileri tarafından kullanılabilen kurallı işlevler ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="112d0-104">This section discusses canonical functions that are supported by all data providers, and can be used by all querying technologies.</span></span> <span data-ttu-id="112d0-105">Kurallı işlevler bir sağlayıcı tarafından genişletilemez.</span><span class="sxs-lookup"><span data-stu-id="112d0-105">Canonical functions cannot be extended by a provider.</span></span>  
  
 <span data-ttu-id="112d0-106">Bu kurallı işlevler, sağlayıcı için karşılık gelen veri kaynağı işlevselliğine çevrilir.</span><span class="sxs-lookup"><span data-stu-id="112d0-106">These canonical functions will be translated to the corresponding data source functionality for the provider.</span></span> <span data-ttu-id="112d0-107">Bu, veri kaynakları genelinde ortak bir biçimde ifade edilen işlev etkinleştirmeleri için izin verir.</span><span class="sxs-lookup"><span data-stu-id="112d0-107">This allows for function invocations expressed in a common form across data sources.</span></span>  
  
 <span data-ttu-id="112d0-108">Bu kurallı işlevler veri kaynaklarından bağımsız olduğundan, kurallı işlevlerin bağımsız değişkeni ve dönüş türleri kavramsal modeldeki türler bakımından tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="112d0-108">Because these canonical functions are independent of data sources, argument and return types of canonical functions are defined in terms of types in the conceptual model.</span></span> <span data-ttu-id="112d0-109">Ancak, bazı veri kaynakları kavramsal modeldeki tüm türleri desteklemeyebilir.</span><span class="sxs-lookup"><span data-stu-id="112d0-109">However, some data sources might not support all types in the conceptual model.</span></span>  
  
 <span data-ttu-id="112d0-110">Sorguda kurallı işlevler kullanıldığında [!INCLUDE[esql](../../../../../../includes/esql-md.md)] , uygun işlev veri kaynağında çağrılır.</span><span class="sxs-lookup"><span data-stu-id="112d0-110">When canonical functions are used in an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query, the appropriate function will be called at the data source.</span></span>  
  
 <span data-ttu-id="112d0-111">Tüm kurallı işlevlerde hem null girişi davranışı hem de hata koşulları açıkça belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="112d0-111">All canonical functions have both null-input behavior and error conditions explicitly specified.</span></span> <span data-ttu-id="112d0-112">Mağaza sağlayıcılarının bu davranışla uyumlu olması gerekir, ancak Entity Framework bu davranışı zorlamaz.</span><span class="sxs-lookup"><span data-stu-id="112d0-112">Store providers should comply with that behavior, but Entity Framework does not enforce this behavior.</span></span>  
  
 <span data-ttu-id="112d0-113">LINQ senaryolarında Entity Framework karşı sorgular, CLR yöntemlerini temel alınan veri kaynağındaki yöntemlere eşlemeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="112d0-113">For LINQ scenarios, queries against the Entity Framework involve mapping CLR methods to methods in the underlying data source.</span></span> <span data-ttu-id="112d0-114">CLR yöntemleri kurallı işlevlere eşlenir, böylece veri kaynağından bağımsız olarak belirli bir yöntem kümesinin doğru şekilde eşlenmesi sağlanır.</span><span class="sxs-lookup"><span data-stu-id="112d0-114">The CLR methods map to canonical functions, so that a specific set of methods will correctly map, regardless of the data source.</span></span>  
  
## <a name="canonical-functions-namespace"></a><span data-ttu-id="112d0-115">Kurallı Işlevler ad alanı</span><span class="sxs-lookup"><span data-stu-id="112d0-115">Canonical Functions Namespace</span></span>  

 <span data-ttu-id="112d0-116">Kurallı işlev için ad alanı <xref:System.Data.Metadata.Edm> .</span><span class="sxs-lookup"><span data-stu-id="112d0-116">The namespace for canonical function is <xref:System.Data.Metadata.Edm>.</span></span> <span data-ttu-id="112d0-117"><xref:System.Data.Metadata.Edm>Ad alanı tüm sorgulara otomatik olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="112d0-117">The <xref:System.Data.Metadata.Edm> namespace is automatically included in all queries.</span></span> <span data-ttu-id="112d0-118">Ancak, kurallı bir işlevle aynı ada sahip bir işlev içeren başka bir ad alanı içeri aktarılmışsa ( <xref:System.Data.Metadata.Edm> ad alanında), ad alanını belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="112d0-118">However, if another namespace is imported that contains a function with the same name as a canonical function (in the <xref:System.Data.Metadata.Edm> namespace), you must specify the namespace.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="112d0-119">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="112d0-119">In This Section</span></span>  

 [<span data-ttu-id="112d0-120">Toplu Kurallı İşlevler</span><span class="sxs-lookup"><span data-stu-id="112d0-120">Aggregate Canonical Functions</span></span>](aggregate-canonical-functions.md)  
 <span data-ttu-id="112d0-121">Birleşik [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kurallı işlevleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="112d0-121">Discusses aggregate [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="112d0-122">Kurallı Matematik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="112d0-122">Math Canonical Functions</span></span>](math-canonical-functions.md)  
 <span data-ttu-id="112d0-123">Matematik [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kurallı işlevlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="112d0-123">Discusses math [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="112d0-124">Kurallı Dize İşlevleri</span><span class="sxs-lookup"><span data-stu-id="112d0-124">String Canonical Functions</span></span>](string-canonical-functions.md)  
 <span data-ttu-id="112d0-125">Kurallı dize [!INCLUDE[esql](../../../../../../includes/esql-md.md)] işlevlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="112d0-125">Discusses string [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="112d0-126">Kurallı Tarih ve Saat İşlevleri</span><span class="sxs-lookup"><span data-stu-id="112d0-126">Date and Time Canonical Functions</span></span>](date-and-time-canonical-functions.md)  
 <span data-ttu-id="112d0-127">Tarih ve saat [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kurallı işlevleri ele alır.</span><span class="sxs-lookup"><span data-stu-id="112d0-127">Discusses date and time [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="112d0-128">Bit Düzeyinde Kurallı İşlevler</span><span class="sxs-lookup"><span data-stu-id="112d0-128">Bitwise Canonical Functions</span></span>](bitwise-canonical-functions.md)  
 <span data-ttu-id="112d0-129">Bit düzeyinde [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kurallı işlevleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="112d0-129">Discusses bitwise [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="112d0-130">Uzamsal Işlevler</span><span class="sxs-lookup"><span data-stu-id="112d0-130">Spatial Functions</span></span>](spatial-functions.md)  
 <span data-ttu-id="112d0-131">Uzamsal [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kurallı işlevleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="112d0-131">Discusses Spatial [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="112d0-132">Diğer Kurallı İşlevler</span><span class="sxs-lookup"><span data-stu-id="112d0-132">Other Canonical Functions</span></span>](other-canonical-functions.md)  
 <span data-ttu-id="112d0-133">Bit düzeyinde, tarih/saat, dize, matematik veya toplama olarak sınıflandırılmayan işlevleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="112d0-133">Discusses functions not classified as bitwise, date/time, string, math, or aggregate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="112d0-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="112d0-134">See also</span></span>

- [<span data-ttu-id="112d0-135">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="112d0-135">Entity SQL Overview</span></span>](entity-sql-overview.md)
- [<span data-ttu-id="112d0-136">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="112d0-136">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="112d0-137">SQL Server İşlevleri ile Kurallı Kavramsal Model Eşlemesi</span><span class="sxs-lookup"><span data-stu-id="112d0-137">Conceptual Model Canonical to SQL Server Functions Mapping</span></span>](../conceptual-model-canonical-to-sql-server-functions-mapping.md)
- [<span data-ttu-id="112d0-138">Kullanıcı tanımlı Işlevler</span><span class="sxs-lookup"><span data-stu-id="112d0-138">User-Defined Functions</span></span>](user-defined-functions-entity-sql.md)
