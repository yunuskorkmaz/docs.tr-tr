---
title: Tür sistemi (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 818a505b-a196-41dd-aaac-2ccd5f7a2f1a
ms.openlocfilehash: d86c97834b9cc6698da8664ff2a09ceda7cc0043
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64641226"
---
# <a name="type-system-entity-sql"></a><span data-ttu-id="e69f9-102">Tür sistemi (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="e69f9-102">Type System (Entity SQL)</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="e69f9-103">bir dizi türlerini destekler:</span><span class="sxs-lookup"><span data-stu-id="e69f9-103">supports a number of types:</span></span>  
  
- <span data-ttu-id="e69f9-104">(Basit) temel türler gibi `Int32` ve `String.`</span><span class="sxs-lookup"><span data-stu-id="e69f9-104">Primitive (simple) types such as `Int32` and `String.`</span></span>  
  
- <span data-ttu-id="e69f9-105">Şemada gibi tanımlı nominal türlerinden <xref:System.Data.Metadata.Edm.EntityType>, <xref:System.Data.Metadata.Edm.ComplexType>, ve <xref:System.Data.Metadata.Edm.RelationshipType>.</span><span class="sxs-lookup"><span data-stu-id="e69f9-105">Nominal types that are defined in the schema, such as <xref:System.Data.Metadata.Edm.EntityType>, <xref:System.Data.Metadata.Edm.ComplexType>, and <xref:System.Data.Metadata.Edm.RelationshipType>.</span></span>  
  
- <span data-ttu-id="e69f9-106">Şema içinde açıkça tanımlanmayan anonim türler: <xref:System.Data.Metadata.Edm.CollectionType>, <xref:System.Data.Metadata.Edm.RowType>, ve <xref:System.Data.Metadata.Edm.RefType>.</span><span class="sxs-lookup"><span data-stu-id="e69f9-106">Anonymous types that are not defined in the schema explicitly: <xref:System.Data.Metadata.Edm.CollectionType>, <xref:System.Data.Metadata.Edm.RowType>, and <xref:System.Data.Metadata.Edm.RefType>.</span></span>  
  
 <span data-ttu-id="e69f9-107">Bu bölümde, ancak varlık SQL tarafından desteklenen şema içinde açıkça tanımlanmayan anonim türler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e69f9-107">This section discusses the anonymous types that are not defined in the schema explicitly but are supported by Entity SQL.</span></span> <span data-ttu-id="e69f9-108">Basit ve nominal türleri hakkında daha fazla bilgi için bkz. [kavramsal Model türleri (CSDL)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl).</span><span class="sxs-lookup"><span data-stu-id="e69f9-108">For information on primitive and nominal types, see [Conceptual Model Types (CSDL)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl).</span></span>  
  
## <a name="rows"></a><span data-ttu-id="e69f9-109">Satırları</span><span class="sxs-lookup"><span data-stu-id="e69f9-109">Rows</span></span>  
 <span data-ttu-id="e69f9-110">Satır oluşan yazılı ve adlandırılmış üyelerinin sırasını bir satırı yapısını bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="e69f9-110">The structure of a row depends on the sequence of typed and named members that the row consists of.</span></span> <span data-ttu-id="e69f9-111">Satır türü kimliksiz sahiptir ve öğesinden devralınamaz.</span><span class="sxs-lookup"><span data-stu-id="e69f9-111">A row type has no identity and cannot be inherited from.</span></span> <span data-ttu-id="e69f9-112">Üye sırasıyla eşdeğer ise aynı satır türü örneklerini eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="e69f9-112">Instances of the same row type are equivalent if the members are respectively equivalent.</span></span> <span data-ttu-id="e69f9-113">Satırları, yapısal denklik ötesinde davranışı yok ve ortak dil çalışma zamanı'nda eşdeğeri sahiptir.</span><span class="sxs-lookup"><span data-stu-id="e69f9-113">Rows have no behavior beyond their structural equivalence and have no equivalent in the common language runtime.</span></span> <span data-ttu-id="e69f9-114">Satır veya satır koleksiyonu içeren yapıları, sorguları neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="e69f9-114">Queries can result in structures that contain rows or collections of rows.</span></span> <span data-ttu-id="e69f9-115">API bağlama arasında [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgular ve konak dil tanımlar satırları bir sonuç getirdi sorguda nasıl gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="e69f9-115">The API binding between the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries and the host language defines how rows are realized in the query that produced the result.</span></span> <span data-ttu-id="e69f9-116">Bir satır örneği oluşturma hakkında daha fazla bilgi için bkz: [oluşturma türleri](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="e69f9-116">For information on how to construct a row instance, see [Constructing Types](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).</span></span>  
  
## <a name="collections"></a><span data-ttu-id="e69f9-117">Koleksiyonlar</span><span class="sxs-lookup"><span data-stu-id="e69f9-117">Collections</span></span>  
 <span data-ttu-id="e69f9-118">Koleksiyon türleri, sıfır veya daha fazla diğer nesnelerin örneklerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e69f9-118">Collection types represent zero or more instances of other objects.</span></span> <span data-ttu-id="e69f9-119">Koleksiyon oluşturma hakkında daha fazla bilgi için bkz: [oluşturma türleri](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="e69f9-119">For information on how to construct collection, see [Constructing Types](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).</span></span>  
  
## <a name="references"></a><span data-ttu-id="e69f9-120">Referanslar</span><span class="sxs-lookup"><span data-stu-id="e69f9-120">References</span></span>  
 <span data-ttu-id="e69f9-121">Bir başvuru, bir özel varlık kümesinde belirli bir varlığa mantıksal bir işaretçisidir.</span><span class="sxs-lookup"><span data-stu-id="e69f9-121">A reference is a logical pointer to a specific entity in a specific entity set.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="e69f9-122">oluşturun, ayrıştırma ve başvurular arasında gitmek için aşağıdaki işleçleri destekler:</span><span class="sxs-lookup"><span data-stu-id="e69f9-122">supports the following operators to construct, deconstruct, and navigate through references:</span></span>  
  
- [<span data-ttu-id="e69f9-123">REF</span><span class="sxs-lookup"><span data-stu-id="e69f9-123">REF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)  
  
- [<span data-ttu-id="e69f9-124">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="e69f9-124">CREATEREF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)  
  
- [<span data-ttu-id="e69f9-125">KEY</span><span class="sxs-lookup"><span data-stu-id="e69f9-125">KEY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)  
  
- [<span data-ttu-id="e69f9-126">DEREF</span><span class="sxs-lookup"><span data-stu-id="e69f9-126">DEREF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)  
  
 <span data-ttu-id="e69f9-127">Üye erişim (nokta) işlecini kullanarak başvuru gidebilirsiniz (`.`).</span><span class="sxs-lookup"><span data-stu-id="e69f9-127">You can navigate through a reference by using the member access (dot) operator(`.`).</span></span> <span data-ttu-id="e69f9-128">Aşağıdaki kod parçacığı r (başvuru) özelliği üzerinden giderek (sıra), kimlik özelliği ayıklar.</span><span class="sxs-lookup"><span data-stu-id="e69f9-128">The following snippet extracts the Id property (of Order) by navigating through the r (reference) property.</span></span>  
  
```  
select o2.r.Id   
from (select ref(o) as r from LOB.Orders as o) as o2   
```  
  
 <span data-ttu-id="e69f9-129">Başvuru değeri null ise veya başvuru hedefinin yoksa sonuç NULL'dur.</span><span class="sxs-lookup"><span data-stu-id="e69f9-129">If the reference value is null, or if the target of the reference does not exist, the result is null.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e69f9-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e69f9-130">See also</span></span>

- [<span data-ttu-id="e69f9-131">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e69f9-131">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [<span data-ttu-id="e69f9-132">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="e69f9-132">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="e69f9-133">CAST</span><span class="sxs-lookup"><span data-stu-id="e69f9-133">CAST</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/cast-entity-sql.md)
- [<span data-ttu-id="e69f9-134">CSDL, SSDL ve MSL Belirtimleri</span><span class="sxs-lookup"><span data-stu-id="e69f9-134">CSDL, SSDL, and MSL Specifications</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/csdl-ssdl-and-msl-specifications.md)
