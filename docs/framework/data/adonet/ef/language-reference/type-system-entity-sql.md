---
title: Tür sistemi (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 818a505b-a196-41dd-aaac-2ccd5f7a2f1a
ms.openlocfilehash: 0f7dae9e57132929737d752c67694cd369b79d9e
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319231"
---
# <a name="type-system-entity-sql"></a><span data-ttu-id="15b14-102">Tür sistemi (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="15b14-102">Type System (Entity SQL)</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="15b14-103">, bir dizi türü destekler:</span><span class="sxs-lookup"><span data-stu-id="15b14-103">supports a number of types:</span></span>  
  
- <span data-ttu-id="15b14-104">@No__t-0 ve `String.` gibi basit (basit) türler</span><span class="sxs-lookup"><span data-stu-id="15b14-104">Primitive (simple) types such as `Int32` and `String.`</span></span>  
  
- <span data-ttu-id="15b14-105">Şemada tanımlanan, örneğin <xref:System.Data.Metadata.Edm.EntityType>, <xref:System.Data.Metadata.Edm.ComplexType> ve <xref:System.Data.Metadata.Edm.RelationshipType> gibi türler kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="15b14-105">Nominal types that are defined in the schema, such as <xref:System.Data.Metadata.Edm.EntityType>, <xref:System.Data.Metadata.Edm.ComplexType>, and <xref:System.Data.Metadata.Edm.RelationshipType>.</span></span>  
  
- <span data-ttu-id="15b14-106">Şemada açıkça tanımlanmayan anonim türler: <xref:System.Data.Metadata.Edm.CollectionType>, <xref:System.Data.Metadata.Edm.RowType> ve <xref:System.Data.Metadata.Edm.RefType>.</span><span class="sxs-lookup"><span data-stu-id="15b14-106">Anonymous types that are not defined in the schema explicitly: <xref:System.Data.Metadata.Edm.CollectionType>, <xref:System.Data.Metadata.Edm.RowType>, and <xref:System.Data.Metadata.Edm.RefType>.</span></span>  
  
 <span data-ttu-id="15b14-107">Bu bölümde, şemada açıkça tanımlanmayan ancak Entity SQL tarafından desteklenen anonim türler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="15b14-107">This section discusses the anonymous types that are not defined in the schema explicitly but are supported by Entity SQL.</span></span> <span data-ttu-id="15b14-108">İlkel ve nominal türler hakkında bilgi için bkz. [kavramsal model türleri (csdl)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl).</span><span class="sxs-lookup"><span data-stu-id="15b14-108">For information on primitive and nominal types, see [Conceptual Model Types (CSDL)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl).</span></span>  
  
## <a name="rows"></a><span data-ttu-id="15b14-109">Sütunları</span><span class="sxs-lookup"><span data-stu-id="15b14-109">Rows</span></span>  
 <span data-ttu-id="15b14-110">Bir satırın yapısı, yazılan ve satırın içerdiği adlandırılmış üyelerin dizisine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="15b14-110">The structure of a row depends on the sequence of typed and named members that the row consists of.</span></span> <span data-ttu-id="15b14-111">Bir satır türünün kimliği yok ve öğesinden devralınamıyor.</span><span class="sxs-lookup"><span data-stu-id="15b14-111">A row type has no identity and cannot be inherited from.</span></span> <span data-ttu-id="15b14-112">Aynı satır türünün örnekleri, Üyeler sırasıyla eşdeğer olduğunda eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="15b14-112">Instances of the same row type are equivalent if the members are respectively equivalent.</span></span> <span data-ttu-id="15b14-113">Satırlarda yapısal denklik değerinin ötesinde hiçbir davranış yoktur ve ortak dil çalışma zamanına denk değildir.</span><span class="sxs-lookup"><span data-stu-id="15b14-113">Rows have no behavior beyond their structural equivalence and have no equivalent in the common language runtime.</span></span> <span data-ttu-id="15b14-114">Sorgular, satırları veya satır koleksiyonlarını içeren yapılara yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="15b14-114">Queries can result in structures that contain rows or collections of rows.</span></span> <span data-ttu-id="15b14-115">@No__t-0 sorguları ile ana bilgisayar dili arasındaki API bağlama, sonuçları üreten sorguda satırların nasıl yapıldığını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="15b14-115">The API binding between the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries and the host language defines how rows are realized in the query that produced the result.</span></span> <span data-ttu-id="15b14-116">Satır örneği oluşturma hakkında daha fazla bilgi için bkz. [tür](constructing-types-entity-sql.md)oluşturma.</span><span class="sxs-lookup"><span data-stu-id="15b14-116">For information on how to construct a row instance, see [Constructing Types](constructing-types-entity-sql.md).</span></span>  
  
## <a name="collections"></a><span data-ttu-id="15b14-117">Koleksiyonlar</span><span class="sxs-lookup"><span data-stu-id="15b14-117">Collections</span></span>  
 <span data-ttu-id="15b14-118">Koleksiyon türleri, diğer nesnelerin sıfır veya daha fazla örneğini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="15b14-118">Collection types represent zero or more instances of other objects.</span></span> <span data-ttu-id="15b14-119">Koleksiyon oluşturma hakkında daha fazla bilgi için bkz. [tür](constructing-types-entity-sql.md)oluşturma.</span><span class="sxs-lookup"><span data-stu-id="15b14-119">For information on how to construct collection, see [Constructing Types](constructing-types-entity-sql.md).</span></span>  
  
## <a name="references"></a><span data-ttu-id="15b14-120">Referanslar</span><span class="sxs-lookup"><span data-stu-id="15b14-120">References</span></span>  
 <span data-ttu-id="15b14-121">Başvuru, belirli bir varlık kümesindeki belirli bir varlığa yönelik mantıksal bir işaretçisidir.</span><span class="sxs-lookup"><span data-stu-id="15b14-121">A reference is a logical pointer to a specific entity in a specific entity set.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="15b14-122">, başvuruları oluşturmak, oluşturmak ve bunlar arasında gezinmek için aşağıdaki işleçleri destekler:</span><span class="sxs-lookup"><span data-stu-id="15b14-122">supports the following operators to construct, deconstruct, and navigate through references:</span></span>  
  
- [<span data-ttu-id="15b14-123">REF</span><span class="sxs-lookup"><span data-stu-id="15b14-123">REF</span></span>](ref-entity-sql.md)  
  
- [<span data-ttu-id="15b14-124">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="15b14-124">CREATEREF</span></span>](createref-entity-sql.md)  
  
- [<span data-ttu-id="15b14-125">KEY</span><span class="sxs-lookup"><span data-stu-id="15b14-125">KEY</span></span>](key-entity-sql.md)  
  
- [<span data-ttu-id="15b14-126">DEREF</span><span class="sxs-lookup"><span data-stu-id="15b14-126">DEREF</span></span>](deref-entity-sql.md)  
  
 <span data-ttu-id="15b14-127">Üye erişimi (nokta) işlecini (`.`) kullanarak bir başvuruya gidebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="15b14-127">You can navigate through a reference by using the member access (dot) operator(`.`).</span></span> <span data-ttu-id="15b14-128">Aşağıdaki kod parçacığı, r (Reference) özelliğinde gezinerek ID özelliğini (sıra) ayıklar.</span><span class="sxs-lookup"><span data-stu-id="15b14-128">The following snippet extracts the Id property (of Order) by navigating through the r (reference) property.</span></span>  
  
```sql  
select o2.r.Id   
from (select ref(o) as r from LOB.Orders as o) as o2   
```  
  
 <span data-ttu-id="15b14-129">Başvuru değeri null ise veya başvurunun hedefi yoksa sonuç null olur.</span><span class="sxs-lookup"><span data-stu-id="15b14-129">If the reference value is null, or if the target of the reference does not exist, the result is null.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15b14-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="15b14-130">See also</span></span>

- [<span data-ttu-id="15b14-131">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="15b14-131">Entity SQL Overview</span></span>](entity-sql-overview.md)
- [<span data-ttu-id="15b14-132">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="15b14-132">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="15b14-133">CAST</span><span class="sxs-lookup"><span data-stu-id="15b14-133">CAST</span></span>](cast-entity-sql.md)
- [<span data-ttu-id="15b14-134">CSDL, SSDL ve MSL Belirtimleri</span><span class="sxs-lookup"><span data-stu-id="15b14-134">CSDL, SSDL, and MSL Specifications</span></span>](csdl-ssdl-and-msl-specifications.md)
