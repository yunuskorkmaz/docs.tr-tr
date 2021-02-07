---
description: 'Daha fazla bilgi edinin: tür sistemi (Entity SQL)'
title: Tür sistemi (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 818a505b-a196-41dd-aaac-2ccd5f7a2f1a
ms.openlocfilehash: 8d0d50a2c82a309a6a496642836aabe23b6bb9bd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99673394"
---
# <a name="type-system-entity-sql"></a><span data-ttu-id="985af-103">Tür sistemi (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="985af-103">Type System (Entity SQL)</span></span>

[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="985af-104">bir dizi türü destekler:</span><span class="sxs-lookup"><span data-stu-id="985af-104">supports a number of types:</span></span>  
  
- <span data-ttu-id="985af-105">Ve gibi temel (basit) türler `Int32``String.`</span><span class="sxs-lookup"><span data-stu-id="985af-105">Primitive (simple) types such as `Int32` and `String.`</span></span>  
  
- <span data-ttu-id="985af-106">Şemasında tanımlanan,, ve gibi değerler nominal türler <xref:System.Data.Metadata.Edm.EntityType> <xref:System.Data.Metadata.Edm.ComplexType> <xref:System.Data.Metadata.Edm.RelationshipType> .</span><span class="sxs-lookup"><span data-stu-id="985af-106">Nominal types that are defined in the schema, such as <xref:System.Data.Metadata.Edm.EntityType>, <xref:System.Data.Metadata.Edm.ComplexType>, and <xref:System.Data.Metadata.Edm.RelationshipType>.</span></span>  
  
- <span data-ttu-id="985af-107">Şemada tanımlanmamış anonim türler açıkça: <xref:System.Data.Metadata.Edm.CollectionType> , <xref:System.Data.Metadata.Edm.RowType> , ve <xref:System.Data.Metadata.Edm.RefType> .</span><span class="sxs-lookup"><span data-stu-id="985af-107">Anonymous types that are not defined in the schema explicitly: <xref:System.Data.Metadata.Edm.CollectionType>, <xref:System.Data.Metadata.Edm.RowType>, and <xref:System.Data.Metadata.Edm.RefType>.</span></span>  
  
 <span data-ttu-id="985af-108">Bu bölümde, şemada açıkça tanımlanmayan ancak Entity SQL tarafından desteklenen anonim türler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="985af-108">This section discusses the anonymous types that are not defined in the schema explicitly but are supported by Entity SQL.</span></span> <span data-ttu-id="985af-109">İlkel ve nominal türler hakkında bilgi için bkz. [kavramsal model türleri (csdl)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl).</span><span class="sxs-lookup"><span data-stu-id="985af-109">For information on primitive and nominal types, see [Conceptual Model Types (CSDL)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl).</span></span>  
  
## <a name="rows"></a><span data-ttu-id="985af-110">Satırlar</span><span class="sxs-lookup"><span data-stu-id="985af-110">Rows</span></span>  

 <span data-ttu-id="985af-111">Bir satırın yapısı, yazılan ve satırın içerdiği adlandırılmış üyelerin dizisine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="985af-111">The structure of a row depends on the sequence of typed and named members that the row consists of.</span></span> <span data-ttu-id="985af-112">Bir satır türünün kimliği yok ve öğesinden devralınamıyor.</span><span class="sxs-lookup"><span data-stu-id="985af-112">A row type has no identity and cannot be inherited from.</span></span> <span data-ttu-id="985af-113">Aynı satır türünün örnekleri, Üyeler sırasıyla eşdeğer olduğunda eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="985af-113">Instances of the same row type are equivalent if the members are respectively equivalent.</span></span> <span data-ttu-id="985af-114">Satırlarda yapısal denklik değerinin ötesinde hiçbir davranış yoktur ve ortak dil çalışma zamanına denk değildir.</span><span class="sxs-lookup"><span data-stu-id="985af-114">Rows have no behavior beyond their structural equivalence and have no equivalent in the common language runtime.</span></span> <span data-ttu-id="985af-115">Sorgular, satırları veya satır koleksiyonlarını içeren yapılara yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="985af-115">Queries can result in structures that contain rows or collections of rows.</span></span> <span data-ttu-id="985af-116">[!INCLUDE[esql](../../../../../../includes/esql-md.md)]Sorgular ve ana bilgisayar dili ARASıNDAKI API bağı, sonuçları üreten sorguda satırların nasıl yapıldığını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="985af-116">The API binding between the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries and the host language defines how rows are realized in the query that produced the result.</span></span> <span data-ttu-id="985af-117">Satır örneği oluşturma hakkında daha fazla bilgi için bkz. [tür](constructing-types-entity-sql.md)oluşturma.</span><span class="sxs-lookup"><span data-stu-id="985af-117">For information on how to construct a row instance, see [Constructing Types](constructing-types-entity-sql.md).</span></span>  
  
## <a name="collections"></a><span data-ttu-id="985af-118">Koleksiyonlar</span><span class="sxs-lookup"><span data-stu-id="985af-118">Collections</span></span>  

 <span data-ttu-id="985af-119">Koleksiyon türleri, diğer nesnelerin sıfır veya daha fazla örneğini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="985af-119">Collection types represent zero or more instances of other objects.</span></span> <span data-ttu-id="985af-120">Koleksiyon oluşturma hakkında daha fazla bilgi için bkz. [tür](constructing-types-entity-sql.md)oluşturma.</span><span class="sxs-lookup"><span data-stu-id="985af-120">For information on how to construct collection, see [Constructing Types](constructing-types-entity-sql.md).</span></span>  
  
## <a name="references"></a><span data-ttu-id="985af-121">Başvurular</span><span class="sxs-lookup"><span data-stu-id="985af-121">References</span></span>  

 <span data-ttu-id="985af-122">Başvuru, belirli bir varlık kümesindeki belirli bir varlığa yönelik mantıksal bir işaretçisidir.</span><span class="sxs-lookup"><span data-stu-id="985af-122">A reference is a logical pointer to a specific entity in a specific entity set.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="985af-123">, başvuruları oluşturmak, oluşturmak ve bunlar arasında gezinmek için aşağıdaki işleçleri destekler:</span><span class="sxs-lookup"><span data-stu-id="985af-123">supports the following operators to construct, deconstruct, and navigate through references:</span></span>  
  
- [<span data-ttu-id="985af-124">REF</span><span class="sxs-lookup"><span data-stu-id="985af-124">REF</span></span>](ref-entity-sql.md)  
  
- [<span data-ttu-id="985af-125">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="985af-125">CREATEREF</span></span>](createref-entity-sql.md)  
  
- [<span data-ttu-id="985af-126">ANAHTAR</span><span class="sxs-lookup"><span data-stu-id="985af-126">KEY</span></span>](key-entity-sql.md)  
  
- [<span data-ttu-id="985af-127">DEREF</span><span class="sxs-lookup"><span data-stu-id="985af-127">DEREF</span></span>](deref-entity-sql.md)  
  
 <span data-ttu-id="985af-128">Üye erişimi (nokta) işlecini () kullanarak bir başvuruya gidebilirsiniz `.` .</span><span class="sxs-lookup"><span data-stu-id="985af-128">You can navigate through a reference by using the member access (dot) operator(`.`).</span></span> <span data-ttu-id="985af-129">Aşağıdaki kod parçacığı, r (Reference) özelliğinde gezinerek ID özelliğini (sıra) ayıklar.</span><span class="sxs-lookup"><span data-stu-id="985af-129">The following snippet extracts the Id property (of Order) by navigating through the r (reference) property.</span></span>  
  
```sql  
select o2.r.Id
from (select ref(o) as r from LOB.Orders as o) as o2
```  
  
 <span data-ttu-id="985af-130">Başvuru değeri null ise veya başvurunun hedefi yoksa sonuç null olur.</span><span class="sxs-lookup"><span data-stu-id="985af-130">If the reference value is null, or if the target of the reference does not exist, the result is null.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="985af-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="985af-131">See also</span></span>

- [<span data-ttu-id="985af-132">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="985af-132">Entity SQL Overview</span></span>](entity-sql-overview.md)
- [<span data-ttu-id="985af-133">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="985af-133">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="985af-134">CAST</span><span class="sxs-lookup"><span data-stu-id="985af-134">CAST</span></span>](cast-entity-sql.md)
- [<span data-ttu-id="985af-135">CSDL, SSDL ve MSL Belirtimleri</span><span class="sxs-lookup"><span data-stu-id="985af-135">CSDL, SSDL, and MSL Specifications</span></span>](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)
