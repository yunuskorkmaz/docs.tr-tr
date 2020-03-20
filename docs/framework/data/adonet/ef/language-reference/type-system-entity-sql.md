---
title: Tip Sistemi (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 818a505b-a196-41dd-aaac-2ccd5f7a2f1a
ms.openlocfilehash: b8b721aff5b7886fdb897ecaa3dcc163ec94ae79
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149837"
---
# <a name="type-system-entity-sql"></a><span data-ttu-id="8781b-102">Tip Sistemi (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="8781b-102">Type System (Entity SQL)</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="8781b-103">bir dizi türü destekler:</span><span class="sxs-lookup"><span data-stu-id="8781b-103">supports a number of types:</span></span>  
  
- <span data-ttu-id="8781b-104">Gibi ilkel (basit) `Int32` türleri ve`String.`</span><span class="sxs-lookup"><span data-stu-id="8781b-104">Primitive (simple) types such as `Int32` and `String.`</span></span>  
  
- <span data-ttu-id="8781b-105">Şemada tanımlanan nominal türleri, gibi <xref:System.Data.Metadata.Edm.EntityType>, <xref:System.Data.Metadata.Edm.ComplexType>, <xref:System.Data.Metadata.Edm.RelationshipType>ve .</span><span class="sxs-lookup"><span data-stu-id="8781b-105">Nominal types that are defined in the schema, such as <xref:System.Data.Metadata.Edm.EntityType>, <xref:System.Data.Metadata.Edm.ComplexType>, and <xref:System.Data.Metadata.Edm.RelationshipType>.</span></span>  
  
- <span data-ttu-id="8781b-106">Şemada açıkça tanımlanmayan anonim türler: <xref:System.Data.Metadata.Edm.CollectionType> <xref:System.Data.Metadata.Edm.RowType>, <xref:System.Data.Metadata.Edm.RefType>, ve .</span><span class="sxs-lookup"><span data-stu-id="8781b-106">Anonymous types that are not defined in the schema explicitly: <xref:System.Data.Metadata.Edm.CollectionType>, <xref:System.Data.Metadata.Edm.RowType>, and <xref:System.Data.Metadata.Edm.RefType>.</span></span>  
  
 <span data-ttu-id="8781b-107">Bu bölümde, şemada açıkça tanımlanmayan ancak Entity SQL tarafından desteklenen anonim türleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8781b-107">This section discusses the anonymous types that are not defined in the schema explicitly but are supported by Entity SQL.</span></span> <span data-ttu-id="8781b-108">İlkel ve nominal türler hakkında bilgi için [Kavramsal Model Türleri (CSDL)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl)bakın.</span><span class="sxs-lookup"><span data-stu-id="8781b-108">For information on primitive and nominal types, see [Conceptual Model Types (CSDL)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl).</span></span>  
  
## <a name="rows"></a><span data-ttu-id="8781b-109">Satırlar</span><span class="sxs-lookup"><span data-stu-id="8781b-109">Rows</span></span>  
 <span data-ttu-id="8781b-110">Bir satırın yapısı, satırın oluştuğu yazılan ve adlandırılmış üyelerin sıralarına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="8781b-110">The structure of a row depends on the sequence of typed and named members that the row consists of.</span></span> <span data-ttu-id="8781b-111">Satır türü hiçbir kimliği vardır ve devralınamaz.</span><span class="sxs-lookup"><span data-stu-id="8781b-111">A row type has no identity and cannot be inherited from.</span></span> <span data-ttu-id="8781b-112">Üyeler sırasıyla eşdeğerse, aynı satır türündeki örnekler eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="8781b-112">Instances of the same row type are equivalent if the members are respectively equivalent.</span></span> <span data-ttu-id="8781b-113">Satırların yapısal eşdeğerliklerinin ötesinde hiçbir davranışı yoktur ve ortak dil çalışma zamanında eşdeğeri yoktur.</span><span class="sxs-lookup"><span data-stu-id="8781b-113">Rows have no behavior beyond their structural equivalence and have no equivalent in the common language runtime.</span></span> <span data-ttu-id="8781b-114">Sorgular satır veya satır koleksiyonları içeren yapılarneden olabilir.</span><span class="sxs-lookup"><span data-stu-id="8781b-114">Queries can result in structures that contain rows or collections of rows.</span></span> <span data-ttu-id="8781b-115">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] Sorgular ve ana bilgisayar dili arasındaki API bağlama, sonucu oluşturan sorguda satırların nasıl gerçekleştirildiğini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8781b-115">The API binding between the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries and the host language defines how rows are realized in the query that produced the result.</span></span> <span data-ttu-id="8781b-116">Satır örneğinin nasıl oluşturulabildiğini öğrenmek için [bkz.](constructing-types-entity-sql.md)</span><span class="sxs-lookup"><span data-stu-id="8781b-116">For information on how to construct a row instance, see [Constructing Types](constructing-types-entity-sql.md).</span></span>  
  
## <a name="collections"></a><span data-ttu-id="8781b-117">Koleksiyonlar</span><span class="sxs-lookup"><span data-stu-id="8781b-117">Collections</span></span>  
 <span data-ttu-id="8781b-118">Koleksiyon türleri diğer nesnelerin sıfır veya daha fazla örneğini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8781b-118">Collection types represent zero or more instances of other objects.</span></span> <span data-ttu-id="8781b-119">Koleksiyonun nasıl oluşturulabildiğini öğrenmek için [bkz.](constructing-types-entity-sql.md)</span><span class="sxs-lookup"><span data-stu-id="8781b-119">For information on how to construct collection, see [Constructing Types](constructing-types-entity-sql.md).</span></span>  
  
## <a name="references"></a><span data-ttu-id="8781b-120">Başvurular</span><span class="sxs-lookup"><span data-stu-id="8781b-120">References</span></span>  
 <span data-ttu-id="8781b-121">Başvuru, belirli bir varlık kümesindeki belirli bir varlığa mantıksal işaretçidir.</span><span class="sxs-lookup"><span data-stu-id="8781b-121">A reference is a logical pointer to a specific entity in a specific entity set.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="8781b-122">aşağıdaki işleçleri başvurular oluşturmak, yapısızlaştırılması ve gezinmek için destekler:</span><span class="sxs-lookup"><span data-stu-id="8781b-122">supports the following operators to construct, deconstruct, and navigate through references:</span></span>  
  
- [<span data-ttu-id="8781b-123">REF</span><span class="sxs-lookup"><span data-stu-id="8781b-123">REF</span></span>](ref-entity-sql.md)  
  
- [<span data-ttu-id="8781b-124">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="8781b-124">CREATEREF</span></span>](createref-entity-sql.md)  
  
- [<span data-ttu-id="8781b-125">Anahtar</span><span class="sxs-lookup"><span data-stu-id="8781b-125">KEY</span></span>](key-entity-sql.md)  
  
- [<span data-ttu-id="8781b-126">DEREF</span><span class="sxs-lookup"><span data-stu-id="8781b-126">DEREF</span></span>](deref-entity-sql.md)  
  
 <span data-ttu-id="8781b-127">Üye erişim (nokta)`.`işleci(nokta) operatörlerini kullanarak referans ta gezinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8781b-127">You can navigate through a reference by using the member access (dot) operator(`.`).</span></span> <span data-ttu-id="8781b-128">Aşağıdaki parçacık, r (reference) özelliğinde gezinerek Id özelliğini (Siparişin) ayıklar.</span><span class="sxs-lookup"><span data-stu-id="8781b-128">The following snippet extracts the Id property (of Order) by navigating through the r (reference) property.</span></span>  
  
```sql  
select o2.r.Id
from (select ref(o) as r from LOB.Orders as o) as o2
```  
  
 <span data-ttu-id="8781b-129">Başvuru değeri null ise veya başvurunun hedefi yoksa, sonuç null'dur.</span><span class="sxs-lookup"><span data-stu-id="8781b-129">If the reference value is null, or if the target of the reference does not exist, the result is null.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8781b-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8781b-130">See also</span></span>

- [<span data-ttu-id="8781b-131">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="8781b-131">Entity SQL Overview</span></span>](entity-sql-overview.md)
- [<span data-ttu-id="8781b-132">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="8781b-132">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="8781b-133">CAST</span><span class="sxs-lookup"><span data-stu-id="8781b-133">CAST</span></span>](cast-entity-sql.md)
- [<span data-ttu-id="8781b-134">CSDL, SSDL ve MSL Belirtimleri</span><span class="sxs-lookup"><span data-stu-id="8781b-134">CSDL, SSDL, and MSL Specifications</span></span>](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)
