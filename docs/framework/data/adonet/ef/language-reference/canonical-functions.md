---
title: Kurallı İşlevler
ms.date: 03/30/2017
ms.assetid: bbcc9928-36ea-4dff-9e31-96549ffed958
ms.openlocfilehash: f8ca9e2027e82db89e91287fda02d2014d53f325
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854519"
---
# <a name="canonical-functions"></a><span data-ttu-id="b7f12-102">Kurallı İşlevler</span><span class="sxs-lookup"><span data-stu-id="b7f12-102">Canonical Functions</span></span>
<span data-ttu-id="b7f12-103">Bu bölümde tüm veri sağlayıcıları tarafından desteklenen ve tüm sorgulama teknolojileri tarafından kullanılabilen kurallı işlevler ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b7f12-103">This section discusses canonical functions that are supported by all data providers, and can be used by all querying technologies.</span></span> <span data-ttu-id="b7f12-104">Kurallı işlevler bir sağlayıcı tarafından genişletilemez.</span><span class="sxs-lookup"><span data-stu-id="b7f12-104">Canonical functions cannot be extended by a provider.</span></span>  
  
 <span data-ttu-id="b7f12-105">Bu kurallı işlevler, sağlayıcı için karşılık gelen veri kaynağı işlevselliğine çevrilir.</span><span class="sxs-lookup"><span data-stu-id="b7f12-105">These canonical functions will be translated to the corresponding data source functionality for the provider.</span></span> <span data-ttu-id="b7f12-106">Bu, veri kaynakları genelinde ortak bir biçimde ifade edilen işlev etkinleştirmeleri için izin verir.</span><span class="sxs-lookup"><span data-stu-id="b7f12-106">This allows for function invocations expressed in a common form across data sources.</span></span>  
  
 <span data-ttu-id="b7f12-107">Bu kurallı işlevler veri kaynaklarından bağımsız olduğundan, kurallı işlevlerin bağımsız değişkeni ve dönüş türleri kavramsal modeldeki türler bakımından tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="b7f12-107">Because these canonical functions are independent of data sources, argument and return types of canonical functions are defined in terms of types in the conceptual model.</span></span> <span data-ttu-id="b7f12-108">Ancak, bazı veri kaynakları kavramsal modeldeki tüm türleri desteklemeyebilir.</span><span class="sxs-lookup"><span data-stu-id="b7f12-108">However, some data sources might not support all types in the conceptual model.</span></span>  
  
 <span data-ttu-id="b7f12-109">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] Sorguda kurallı işlevler kullanıldığında, uygun işlev veri kaynağında çağrılır.</span><span class="sxs-lookup"><span data-stu-id="b7f12-109">When canonical functions are used in an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query, the appropriate function will be called at the data source.</span></span>  
  
 <span data-ttu-id="b7f12-110">Tüm kurallı işlevlerde hem null girişi davranışı hem de hata koşulları açıkça belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b7f12-110">All canonical functions have both null-input behavior and error conditions explicitly specified.</span></span> <span data-ttu-id="b7f12-111">Mağaza sağlayıcılarının bu davranışla uyumlu olması gerekir, ancak Entity Framework bu davranışı zorlamaz.</span><span class="sxs-lookup"><span data-stu-id="b7f12-111">Store providers should comply with that behavior, but Entity Framework does not enforce this behavior.</span></span>  
  
 <span data-ttu-id="b7f12-112">LINQ senaryolarında Entity Framework karşı sorgular, CLR yöntemlerini temel alınan veri kaynağındaki yöntemlere eşlemeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="b7f12-112">For LINQ scenarios, queries against the Entity Framework involve mapping CLR methods to methods in the underlying data source.</span></span> <span data-ttu-id="b7f12-113">CLR yöntemleri kurallı işlevlere eşlenir, böylece veri kaynağından bağımsız olarak belirli bir yöntem kümesinin doğru şekilde eşlenmesi sağlanır.</span><span class="sxs-lookup"><span data-stu-id="b7f12-113">The CLR methods map to canonical functions, so that a specific set of methods will correctly map, regardless of the data source.</span></span>  
  
## <a name="canonical-functions-namespace"></a><span data-ttu-id="b7f12-114">Kurallı Işlevler ad alanı</span><span class="sxs-lookup"><span data-stu-id="b7f12-114">Canonical Functions Namespace</span></span>  
 <span data-ttu-id="b7f12-115">Kurallı işlev <xref:System.Data.Metadata.Edm>için ad alanı.</span><span class="sxs-lookup"><span data-stu-id="b7f12-115">The namespace for canonical function is <xref:System.Data.Metadata.Edm>.</span></span> <span data-ttu-id="b7f12-116"><xref:System.Data.Metadata.Edm> Ad alanı tüm sorgulara otomatik olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="b7f12-116">The <xref:System.Data.Metadata.Edm> namespace is automatically included in all queries.</span></span> <span data-ttu-id="b7f12-117">Ancak, kurallı bir işlevle aynı ada sahip bir işlev içeren başka bir ad alanı içeri aktarılmışsa ( <xref:System.Data.Metadata.Edm> ad alanında), ad alanını belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b7f12-117">However, if another namespace is imported that contains a function with the same name as a canonical function (in the <xref:System.Data.Metadata.Edm> namespace), you must specify the namespace.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b7f12-118">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="b7f12-118">In This Section</span></span>  
 [<span data-ttu-id="b7f12-119">Toplu Kurallı İşlevler</span><span class="sxs-lookup"><span data-stu-id="b7f12-119">Aggregate Canonical Functions</span></span>](aggregate-canonical-functions.md)  
 <span data-ttu-id="b7f12-120">Birleşik [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kurallı işlevleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="b7f12-120">Discusses aggregate [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="b7f12-121">Kurallı Matematik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="b7f12-121">Math Canonical Functions</span></span>](math-canonical-functions.md)  
 <span data-ttu-id="b7f12-122">Matematik [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kurallı işlevlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="b7f12-122">Discusses math [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="b7f12-123">Kurallı Dize İşlevleri</span><span class="sxs-lookup"><span data-stu-id="b7f12-123">String Canonical Functions</span></span>](string-canonical-functions.md)  
 <span data-ttu-id="b7f12-124">Kurallı dize [!INCLUDE[esql](../../../../../../includes/esql-md.md)] işlevlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="b7f12-124">Discusses string [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="b7f12-125">Kurallı Tarih ve Saat İşlevleri</span><span class="sxs-lookup"><span data-stu-id="b7f12-125">Date and Time Canonical Functions</span></span>](date-and-time-canonical-functions.md)  
 <span data-ttu-id="b7f12-126">Tarih ve saat [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kurallı işlevleri ele alır.</span><span class="sxs-lookup"><span data-stu-id="b7f12-126">Discusses date and time [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="b7f12-127">Bit Düzeyinde Kurallı İşlevler</span><span class="sxs-lookup"><span data-stu-id="b7f12-127">Bitwise Canonical Functions</span></span>](bitwise-canonical-functions.md)  
 <span data-ttu-id="b7f12-128">Bit düzeyinde [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kurallı işlevleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="b7f12-128">Discusses bitwise [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="b7f12-129">Uzamsal İşlevler</span><span class="sxs-lookup"><span data-stu-id="b7f12-129">Spatial Functions</span></span>](spatial-functions.md)  
 <span data-ttu-id="b7f12-130">Uzamsal [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kurallı işlevleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="b7f12-130">Discusses Spatial [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="b7f12-131">Diğer Kurallı İşlevler</span><span class="sxs-lookup"><span data-stu-id="b7f12-131">Other Canonical Functions</span></span>](other-canonical-functions.md)  
 <span data-ttu-id="b7f12-132">Bit düzeyinde, tarih/saat, dize, matematik veya toplama olarak sınıflandırılmayan işlevleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="b7f12-132">Discusses functions not classified as bitwise, date/time, string, math, or aggregate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7f12-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b7f12-133">See also</span></span>

- [<span data-ttu-id="b7f12-134">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b7f12-134">Entity SQL Overview</span></span>](entity-sql-overview.md)
- [<span data-ttu-id="b7f12-135">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="b7f12-135">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="b7f12-136">SQL Server İşlevleri ile Kurallı Kavramsal Model Eşlemesi</span><span class="sxs-lookup"><span data-stu-id="b7f12-136">Conceptual Model Canonical to SQL Server Functions Mapping</span></span>](../conceptual-model-canonical-to-sql-server-functions-mapping.md)
- [<span data-ttu-id="b7f12-137">Kullanıcı Tanımlı İşlevler</span><span class="sxs-lookup"><span data-stu-id="b7f12-137">User-Defined Functions</span></span>](user-defined-functions-entity-sql.md)
