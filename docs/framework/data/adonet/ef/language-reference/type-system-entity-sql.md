---
title: "Tür sistemi (varlık SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 818a505b-a196-41dd-aaac-2ccd5f7a2f1a
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: b951a51c4a9daee44ba55aa3589900ca4cad188a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="type-system-entity-sql"></a><span data-ttu-id="8df9e-102">Tür sistemi (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="8df9e-102">Type System (Entity SQL)</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="8df9e-103">bir dizi türlerini destekler:</span><span class="sxs-lookup"><span data-stu-id="8df9e-103"> supports a number of types:</span></span>  
  
-   <span data-ttu-id="8df9e-104">Primitive (Basit) türleri gibi `Int32` ve`String.`</span><span class="sxs-lookup"><span data-stu-id="8df9e-104">Primitive (simple) types such as `Int32` and `String.`</span></span>  
  
-   <span data-ttu-id="8df9e-105">Şemada tanımlanan gibi nominal türleri <xref:System.Data.Metadata.Edm.EntityType>, <xref:System.Data.Metadata.Edm.ComplexType>, ve <xref:System.Data.Metadata.Edm.RelationshipType>.</span><span class="sxs-lookup"><span data-stu-id="8df9e-105">Nominal types that are defined in the schema, such as <xref:System.Data.Metadata.Edm.EntityType>, <xref:System.Data.Metadata.Edm.ComplexType>, and <xref:System.Data.Metadata.Edm.RelationshipType>.</span></span>  
  
-   <span data-ttu-id="8df9e-106">Şemada açıkça tanımlanmayan anonim türler: <xref:System.Data.Metadata.Edm.CollectionType>, <xref:System.Data.Metadata.Edm.RowType>, ve <xref:System.Data.Metadata.Edm.RefType>.</span><span class="sxs-lookup"><span data-stu-id="8df9e-106">Anonymous types that are not defined in the schema explicitly: <xref:System.Data.Metadata.Edm.CollectionType>, <xref:System.Data.Metadata.Edm.RowType>, and <xref:System.Data.Metadata.Edm.RefType>.</span></span>  
  
 <span data-ttu-id="8df9e-107">Bu bölümde yer alan şemada açıkça tanımlanmayan ancak tarafından desteklenen anonim türleri açıklanmaktadır [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8df9e-107">This section discusses the anonymous types that are not defined in the schema explicitly but are supported by [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span> <span data-ttu-id="8df9e-108">Basit ve nominal türleri hakkında daha fazla bilgi için bkz: [kavramsal Model türü (CSDL)](http://msdn.microsoft.com/en-us/987b995f-e429-4569-9559-b4146744def4).</span><span class="sxs-lookup"><span data-stu-id="8df9e-108">For information on primitive and nominal types, see [Conceptual Model Types (CSDL)](http://msdn.microsoft.com/en-us/987b995f-e429-4569-9559-b4146744def4).</span></span>  
  
## <a name="rows"></a><span data-ttu-id="8df9e-109">Satırları</span><span class="sxs-lookup"><span data-stu-id="8df9e-109">Rows</span></span>  
 <span data-ttu-id="8df9e-110">Bir satır yapısını satır oluşan yazılan ve adlandırılmış üyeleri bir dizi bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="8df9e-110">The structure of a row depends on the sequence of typed and named members that the row consists of.</span></span> <span data-ttu-id="8df9e-111">Satır türü yok kimliği vardır ve kaynağından devralındı olamaz.</span><span class="sxs-lookup"><span data-stu-id="8df9e-111">A row type has no identity and cannot be inherited from.</span></span> <span data-ttu-id="8df9e-112">Aynı satır türü örnekleri sırasıyla eşdeğer üyeleriyse eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="8df9e-112">Instances of the same row type are equivalent if the members are respectively equivalent.</span></span> <span data-ttu-id="8df9e-113">Satırları kendi yapısal eşdeğer ötesinde davranışı yok ve ortak dil çalışma zamanı'nda eşdeğeri sahiptir.</span><span class="sxs-lookup"><span data-stu-id="8df9e-113">Rows have no behavior beyond their structural equivalence and have no equivalent in the common language runtime.</span></span> <span data-ttu-id="8df9e-114">Sorgu satırları veya satır koleksiyonları içeren yapılarını neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="8df9e-114">Queries can result in structures that contain rows or collections of rows.</span></span> <span data-ttu-id="8df9e-115">API bağlama arasında [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgular ve ana bilgisayar dil tanımlar satırları sonuç getirdi sorguda nasıl gerçekleştirilirler.</span><span class="sxs-lookup"><span data-stu-id="8df9e-115">The API binding between the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries and the host language defines how rows are realized in the query that produced the result.</span></span> <span data-ttu-id="8df9e-116">Bir satır örneği oluşturma hakkında daha fazla bilgi için bkz: [oluşturma türleri](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="8df9e-116">For information on how to construct a row instance, see [Constructing Types](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).</span></span>  
  
## <a name="collections"></a><span data-ttu-id="8df9e-117">Koleksiyonlar</span><span class="sxs-lookup"><span data-stu-id="8df9e-117">Collections</span></span>  
 <span data-ttu-id="8df9e-118">Koleksiyon türleri diğer nesneleri sıfır veya daha fazla örneğini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8df9e-118">Collection types represent zero or more instances of other objects.</span></span> <span data-ttu-id="8df9e-119">Koleksiyon oluşturma hakkında daha fazla bilgi için bkz: [oluşturma türleri](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="8df9e-119">For information on how to construct collection, see [Constructing Types](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).</span></span>  
  
## <a name="references"></a><span data-ttu-id="8df9e-120">Referanslar</span><span class="sxs-lookup"><span data-stu-id="8df9e-120">References</span></span>  
 <span data-ttu-id="8df9e-121">Bir başvuru, belirli bir varlık kümesinde belirli bir varlık için mantıksal bir işaretçidir.</span><span class="sxs-lookup"><span data-stu-id="8df9e-121">A reference is a logical pointer to a specific entity in a specific entity set.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="8df9e-122">oluşturun, deconstruct ve başvurular arasında gezinmek için aşağıdaki işleçleri destekler:</span><span class="sxs-lookup"><span data-stu-id="8df9e-122"> supports the following operators to construct, deconstruct, and navigate through references:</span></span>  
  
-   [<span data-ttu-id="8df9e-123">REF</span><span class="sxs-lookup"><span data-stu-id="8df9e-123">REF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)  
  
-   [<span data-ttu-id="8df9e-124">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="8df9e-124">CREATEREF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)  
  
-   [<span data-ttu-id="8df9e-125">ANAHTARI</span><span class="sxs-lookup"><span data-stu-id="8df9e-125">KEY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)  
  
-   [<span data-ttu-id="8df9e-126">DEREF</span><span class="sxs-lookup"><span data-stu-id="8df9e-126">DEREF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)  
  
 <span data-ttu-id="8df9e-127">Üye erişim (nokta) işlecini kullanarak bir başvuru gezinebilirsiniz (`.`).</span><span class="sxs-lookup"><span data-stu-id="8df9e-127">You can navigate through a reference by using the member access (dot) operator(`.`).</span></span> <span data-ttu-id="8df9e-128">Aşağıdaki kod parçacığında, r (başvuru) özelliği üzerinden giderek kimliği özelliği (sırası) ayıklar.</span><span class="sxs-lookup"><span data-stu-id="8df9e-128">The following snippet extracts the Id property (of Order) by navigating through the r (reference) property.</span></span>  
  
```  
select o2.r.Id   
from (select ref(o) as r from LOB.Orders as o) as o2   
```  
  
 <span data-ttu-id="8df9e-129">Başvuru değer null ise veya başvuru hedef için yoksa sonuç NULL'dur.</span><span class="sxs-lookup"><span data-stu-id="8df9e-129">If the reference value is null, or if the target of the reference does not exist, the result is null.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8df9e-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8df9e-130">See Also</span></span>  
 [<span data-ttu-id="8df9e-131">Varlık SQL genel bakış</span><span class="sxs-lookup"><span data-stu-id="8df9e-131">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [<span data-ttu-id="8df9e-132">Varlık SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="8df9e-132">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="8df9e-133">ATAMA</span><span class="sxs-lookup"><span data-stu-id="8df9e-133">CAST</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/cast-entity-sql.md)  
 [<span data-ttu-id="8df9e-134">CSDL, SSDL ve MSL belirtimleri</span><span class="sxs-lookup"><span data-stu-id="8df9e-134">CSDL, SSDL, and MSL Specifications</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/csdl-ssdl-and-msl-specifications.md)
