---
title: Tür sistemi (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 818a505b-a196-41dd-aaac-2ccd5f7a2f1a
ms.openlocfilehash: f99d63bd526981c4a9f079c25851dc9bbd89cf7c
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738468"
---
# <a name="type-system-entity-sql"></a><span data-ttu-id="8171f-102">Tür sistemi (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="8171f-102">Type System (Entity SQL)</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="8171f-103">birçok türü destekler:</span><span class="sxs-lookup"><span data-stu-id="8171f-103">supports a number of types:</span></span>  
  
- <span data-ttu-id="8171f-104">`Int32` ve `String.` gibi basit (basit) türler</span><span class="sxs-lookup"><span data-stu-id="8171f-104">Primitive (simple) types such as `Int32` and `String.`</span></span>  
  
- <span data-ttu-id="8171f-105">Şemada tanımlanan, örneğin <xref:System.Data.Metadata.Edm.EntityType>, <xref:System.Data.Metadata.Edm.ComplexType> ve <xref:System.Data.Metadata.Edm.RelationshipType> gibi türler kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="8171f-105">Nominal types that are defined in the schema, such as <xref:System.Data.Metadata.Edm.EntityType>, <xref:System.Data.Metadata.Edm.ComplexType>, and <xref:System.Data.Metadata.Edm.RelationshipType>.</span></span>  
  
- <span data-ttu-id="8171f-106">Şemada açıkça tanımlanmayan anonim türler: <xref:System.Data.Metadata.Edm.CollectionType>, <xref:System.Data.Metadata.Edm.RowType> ve <xref:System.Data.Metadata.Edm.RefType>.</span><span class="sxs-lookup"><span data-stu-id="8171f-106">Anonymous types that are not defined in the schema explicitly: <xref:System.Data.Metadata.Edm.CollectionType>, <xref:System.Data.Metadata.Edm.RowType>, and <xref:System.Data.Metadata.Edm.RefType>.</span></span>  
  
 <span data-ttu-id="8171f-107">Bu bölümde, şemada açıkça tanımlanmayan ancak Entity SQL tarafından desteklenen anonim türler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8171f-107">This section discusses the anonymous types that are not defined in the schema explicitly but are supported by Entity SQL.</span></span> <span data-ttu-id="8171f-108">İlkel ve nominal türler hakkında bilgi için bkz. [kavramsal model türleri (csdl)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl).</span><span class="sxs-lookup"><span data-stu-id="8171f-108">For information on primitive and nominal types, see [Conceptual Model Types (CSDL)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl).</span></span>  
  
## <a name="rows"></a><span data-ttu-id="8171f-109">Sütunları</span><span class="sxs-lookup"><span data-stu-id="8171f-109">Rows</span></span>  
 <span data-ttu-id="8171f-110">Bir satırın yapısı, yazılan ve satırın içerdiği adlandırılmış üyelerin dizisine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="8171f-110">The structure of a row depends on the sequence of typed and named members that the row consists of.</span></span> <span data-ttu-id="8171f-111">Bir satır türünün kimliği yok ve öğesinden devralınamıyor.</span><span class="sxs-lookup"><span data-stu-id="8171f-111">A row type has no identity and cannot be inherited from.</span></span> <span data-ttu-id="8171f-112">Aynı satır türünün örnekleri, Üyeler sırasıyla eşdeğer olduğunda eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="8171f-112">Instances of the same row type are equivalent if the members are respectively equivalent.</span></span> <span data-ttu-id="8171f-113">Satırlarda yapısal denklik değerinin ötesinde hiçbir davranış yoktur ve ortak dil çalışma zamanına denk değildir.</span><span class="sxs-lookup"><span data-stu-id="8171f-113">Rows have no behavior beyond their structural equivalence and have no equivalent in the common language runtime.</span></span> <span data-ttu-id="8171f-114">Sorgular, satırları veya satır koleksiyonlarını içeren yapılara yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="8171f-114">Queries can result in structures that contain rows or collections of rows.</span></span> <span data-ttu-id="8171f-115">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorguları ile ana bilgisayar dili arasındaki API bağlama, sonuçları üreten sorguda satırların nasıl yapıldığını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8171f-115">The API binding between the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries and the host language defines how rows are realized in the query that produced the result.</span></span> <span data-ttu-id="8171f-116">Satır örneği oluşturma hakkında daha fazla bilgi için bkz. [tür](constructing-types-entity-sql.md)oluşturma.</span><span class="sxs-lookup"><span data-stu-id="8171f-116">For information on how to construct a row instance, see [Constructing Types](constructing-types-entity-sql.md).</span></span>  
  
## <a name="collections"></a><span data-ttu-id="8171f-117">Koleksiyonlar</span><span class="sxs-lookup"><span data-stu-id="8171f-117">Collections</span></span>  
 <span data-ttu-id="8171f-118">Koleksiyon türleri, diğer nesnelerin sıfır veya daha fazla örneğini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8171f-118">Collection types represent zero or more instances of other objects.</span></span> <span data-ttu-id="8171f-119">Koleksiyon oluşturma hakkında daha fazla bilgi için bkz. [tür](constructing-types-entity-sql.md)oluşturma.</span><span class="sxs-lookup"><span data-stu-id="8171f-119">For information on how to construct collection, see [Constructing Types](constructing-types-entity-sql.md).</span></span>  
  
## <a name="references"></a><span data-ttu-id="8171f-120">Referanslar</span><span class="sxs-lookup"><span data-stu-id="8171f-120">References</span></span>  
 <span data-ttu-id="8171f-121">Başvuru, belirli bir varlık kümesindeki belirli bir varlığa yönelik mantıksal bir işaretçisidir.</span><span class="sxs-lookup"><span data-stu-id="8171f-121">A reference is a logical pointer to a specific entity in a specific entity set.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="8171f-122">, başvuruları oluşturmak, oluşturmak ve bunlar arasında gezinmek için aşağıdaki işleçleri destekler:</span><span class="sxs-lookup"><span data-stu-id="8171f-122">supports the following operators to construct, deconstruct, and navigate through references:</span></span>  
  
- [<span data-ttu-id="8171f-123">REF</span><span class="sxs-lookup"><span data-stu-id="8171f-123">REF</span></span>](ref-entity-sql.md)  
  
- [<span data-ttu-id="8171f-124">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="8171f-124">CREATEREF</span></span>](createref-entity-sql.md)  
  
- [<span data-ttu-id="8171f-125">KEY</span><span class="sxs-lookup"><span data-stu-id="8171f-125">KEY</span></span>](key-entity-sql.md)  
  
- [<span data-ttu-id="8171f-126">DEREF</span><span class="sxs-lookup"><span data-stu-id="8171f-126">DEREF</span></span>](deref-entity-sql.md)  
  
 <span data-ttu-id="8171f-127">Üye erişimi (nokta) işlecini (`.`) kullanarak bir başvuruya gidebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8171f-127">You can navigate through a reference by using the member access (dot) operator(`.`).</span></span> <span data-ttu-id="8171f-128">Aşağıdaki kod parçacığı, r (Reference) özelliğinde gezinerek ID özelliğini (sıra) ayıklar.</span><span class="sxs-lookup"><span data-stu-id="8171f-128">The following snippet extracts the Id property (of Order) by navigating through the r (reference) property.</span></span>  
  
```sql  
select o2.r.Id   
from (select ref(o) as r from LOB.Orders as o) as o2   
```  
  
 <span data-ttu-id="8171f-129">Başvuru değeri null ise veya başvurunun hedefi yoksa sonuç null olur.</span><span class="sxs-lookup"><span data-stu-id="8171f-129">If the reference value is null, or if the target of the reference does not exist, the result is null.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8171f-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8171f-130">See also</span></span>

- [<span data-ttu-id="8171f-131">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="8171f-131">Entity SQL Overview</span></span>](entity-sql-overview.md)
- [<span data-ttu-id="8171f-132">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="8171f-132">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="8171f-133">CAST</span><span class="sxs-lookup"><span data-stu-id="8171f-133">CAST</span></span>](cast-entity-sql.md)
- [<span data-ttu-id="8171f-134">CSDL, SSDL ve MSL Belirtimleri</span><span class="sxs-lookup"><span data-stu-id="8171f-134">CSDL, SSDL, and MSL Specifications</span></span>](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)
