---
title: İlişkilerin Çıkarımını Yapma
ms.date: 03/30/2017
ms.assetid: 8fa86a9d-6545-4a9d-b1f5-58d9742179c7
ms.openlocfilehash: f8a9aba493dfe82466608ea60932ddfec5ef64f1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59127887"
---
# <a name="inferring-relationships"></a><span data-ttu-id="89677-102">İlişkilerin Çıkarımını Yapma</span><span class="sxs-lookup"><span data-stu-id="89677-102">Inferring Relationships</span></span>
<span data-ttu-id="89677-103">Tablo olarak ortaya çıkan bir öğe ayrıca bir tablo olarak ortaya çıkan bir alt öğe varsa bir <xref:System.Data.DataRelation> iki tablo arasında oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="89677-103">If an element that is inferred as a table has a child element that is also inferred as a table, a <xref:System.Data.DataRelation> will be created between the two tables.</span></span> <span data-ttu-id="89677-104">Yeni bir sütun adıyla **ParentTableName_Id** üst öğe için oluşturulan tabloyu hem alt öğe için oluşturulan tabloyu eklenir.</span><span class="sxs-lookup"><span data-stu-id="89677-104">A new column with a name of **ParentTableName_Id** will be added to both the table created for the parent element, and the table created for the child element.</span></span> <span data-ttu-id="89677-105">**Columnmapping'in** bu kimlik sütununun özellik ayarlanacak **MappingType.Hidden**.</span><span class="sxs-lookup"><span data-stu-id="89677-105">The **ColumnMapping** property of this identity column will be set to **MappingType.Hidden**.</span></span> <span data-ttu-id="89677-106">Sütun üst tablo için otomatik artırma birincil anahtarı olacaktır ve kullanılacak **DataRelation** iki tablo arasında.</span><span class="sxs-lookup"><span data-stu-id="89677-106">The column will be an auto-incrementing primary key for the parent table, and will be used for the **DataRelation** between the two tables.</span></span> <span data-ttu-id="89677-107">Eklenen kimlik sütununun veri türünün **System.Int32**, veri türü diğer tüm çıkarsanan sütun olduğu **System.String**.</span><span class="sxs-lookup"><span data-stu-id="89677-107">The data type of the added identity column will be **System.Int32**, unlike the data type of all other inferred columns, which is **System.String**.</span></span> <span data-ttu-id="89677-108">A <xref:System.Data.ForeignKeyConstraint> ile **DeleteRule** = **Cascade** ayrıca yeni bir sütun üst ve alt tablolarında kullanılarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="89677-108">A <xref:System.Data.ForeignKeyConstraint> with **DeleteRule** = **Cascade** will also be created using the new column in both the parent and child tables.</span></span>  
  
 <span data-ttu-id="89677-109">Örneğin, aşağıdaki XML göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="89677-109">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1 attr1="value1" attr2="value2"/>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="89677-110">Çıkarma işlemi, iki tablo oluşturur: **Element1** ve **ChildElement1**.</span><span class="sxs-lookup"><span data-stu-id="89677-110">The inference process will produce two tables: **Element1** and **ChildElement1**.</span></span>  
  
 <span data-ttu-id="89677-111">**Element1** tablo iki sütun vardır: **Element1_Id** ve **ChildElement2**.</span><span class="sxs-lookup"><span data-stu-id="89677-111">The **Element1** table will have two columns: **Element1_Id** and **ChildElement2**.</span></span> <span data-ttu-id="89677-112">**Columnmapping'in** özelliği **Element1_Id** sütun ayarlanacak **MappingType.Hidden**.</span><span class="sxs-lookup"><span data-stu-id="89677-112">The **ColumnMapping** property of the **Element1_Id** column will be set to **MappingType.Hidden**.</span></span> <span data-ttu-id="89677-113">**Columnmapping'in** özelliği **ChildElement2** sütun ayarlanacak **MappingType.Element**.</span><span class="sxs-lookup"><span data-stu-id="89677-113">The **ColumnMapping** property of the **ChildElement2** column will be set to **MappingType.Element**.</span></span> <span data-ttu-id="89677-114">**Element1_Id** sütun birincil anahtarı olarak ayarlanacak **Element1** tablo.</span><span class="sxs-lookup"><span data-stu-id="89677-114">The **Element1_Id** column will be set as the primary key of the **Element1** table.</span></span>  
  
 <span data-ttu-id="89677-115">**ChildElement1** tablo üç sütun vardır: **attr1**, **attr2** ve **Element1_Id**.</span><span class="sxs-lookup"><span data-stu-id="89677-115">The **ChildElement1** table will have three columns: **attr1**, **attr2** and **Element1_Id**.</span></span> <span data-ttu-id="89677-116">**Columnmapping'in** özelliği **attr1** ve **attr2** sütunları ayarlanacak **MappingType.Attribute**.</span><span class="sxs-lookup"><span data-stu-id="89677-116">The **ColumnMapping** property for the **attr1** and **attr2** columns will be set to **MappingType.Attribute**.</span></span> <span data-ttu-id="89677-117">**Columnmapping'in** özelliği **Element1_Id** sütun ayarlanacak **MappingType.Hidden**.</span><span class="sxs-lookup"><span data-stu-id="89677-117">The **ColumnMapping** property of the **Element1_Id** column will be set to **MappingType.Hidden**.</span></span>  
  
 <span data-ttu-id="89677-118">A **DataRelation** ve **ForeignKeyConstraint** kullanılarak oluşturulan **Element1_Id** her iki tablonun sütunlarından.</span><span class="sxs-lookup"><span data-stu-id="89677-118">A **DataRelation** and **ForeignKeyConstraint** will be created using the **Element1_Id** columns from both tables.</span></span>  
  
 <span data-ttu-id="89677-119">**Veri kümesi:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="89677-119">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="89677-120">**Tablo:** Element1</span><span class="sxs-lookup"><span data-stu-id="89677-120">**Table:** Element1</span></span>  
  
|<span data-ttu-id="89677-121">Element1_Id</span><span class="sxs-lookup"><span data-stu-id="89677-121">Element1_Id</span></span>|<span data-ttu-id="89677-122">ChildElement2</span><span class="sxs-lookup"><span data-stu-id="89677-122">ChildElement2</span></span>|  
|------------------|-------------------|  
|<span data-ttu-id="89677-123">0</span><span class="sxs-lookup"><span data-stu-id="89677-123">0</span></span>|<span data-ttu-id="89677-124">Text2</span><span class="sxs-lookup"><span data-stu-id="89677-124">Text2</span></span>|  
  
 <span data-ttu-id="89677-125">**Tablo:** ChildElement1</span><span class="sxs-lookup"><span data-stu-id="89677-125">**Table:** ChildElement1</span></span>  
  
|<span data-ttu-id="89677-126">attr1</span><span class="sxs-lookup"><span data-stu-id="89677-126">attr1</span></span>|<span data-ttu-id="89677-127">attr2</span><span class="sxs-lookup"><span data-stu-id="89677-127">attr2</span></span>|<span data-ttu-id="89677-128">Element1_Id</span><span class="sxs-lookup"><span data-stu-id="89677-128">Element1_Id</span></span>|  
|-----------|-----------|------------------|  
|<span data-ttu-id="89677-129">Değer1</span><span class="sxs-lookup"><span data-stu-id="89677-129">value1</span></span>|<span data-ttu-id="89677-130">Value2</span><span class="sxs-lookup"><span data-stu-id="89677-130">value2</span></span>|<span data-ttu-id="89677-131">0</span><span class="sxs-lookup"><span data-stu-id="89677-131">0</span></span>|  
  
 <span data-ttu-id="89677-132">**DataRelation:** Element1_ChildElement1</span><span class="sxs-lookup"><span data-stu-id="89677-132">**DataRelation:** Element1_ChildElement1</span></span>  
  
 <span data-ttu-id="89677-133">**ParentTable:** Element1</span><span class="sxs-lookup"><span data-stu-id="89677-133">**ParentTable:** Element1</span></span>  
  
 <span data-ttu-id="89677-134">**ParentColumn:** Element1_Id</span><span class="sxs-lookup"><span data-stu-id="89677-134">**ParentColumn:** Element1_Id</span></span>  
  
 <span data-ttu-id="89677-135">**Geldiği:** ChildElement1</span><span class="sxs-lookup"><span data-stu-id="89677-135">**ChildTable:** ChildElement1</span></span>  
  
 <span data-ttu-id="89677-136">**ChildColumn:** Element1_Id</span><span class="sxs-lookup"><span data-stu-id="89677-136">**ChildColumn:** Element1_Id</span></span>  
  
 <span data-ttu-id="89677-137">**İç içe geçmiş:** Doğru</span><span class="sxs-lookup"><span data-stu-id="89677-137">**Nested:** True</span></span>  
  
 <span data-ttu-id="89677-138">**ForeignKeyConstraint:** Element1_ChildElement1</span><span class="sxs-lookup"><span data-stu-id="89677-138">**ForeignKeyConstraint:** Element1_ChildElement1</span></span>  
  
 <span data-ttu-id="89677-139">**Sütun:** Element1_Id</span><span class="sxs-lookup"><span data-stu-id="89677-139">**Column:** Element1_Id</span></span>  
  
 <span data-ttu-id="89677-140">**ParentTable:** Element1</span><span class="sxs-lookup"><span data-stu-id="89677-140">**ParentTable:** Element1</span></span>  
  
 <span data-ttu-id="89677-141">**Geldiği:** ChildElement1</span><span class="sxs-lookup"><span data-stu-id="89677-141">**ChildTable:** ChildElement1</span></span>  
  
 <span data-ttu-id="89677-142">**DeleteRule:** Basamakla</span><span class="sxs-lookup"><span data-stu-id="89677-142">**DeleteRule:** Cascade</span></span>  
  
 <span data-ttu-id="89677-143">**AcceptRejectRule:** Yok.</span><span class="sxs-lookup"><span data-stu-id="89677-143">**AcceptRejectRule:** None</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89677-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="89677-144">See also</span></span>

- [<span data-ttu-id="89677-145">XML’den DataSet İlişkisel Yapısını Çıkarma</span><span class="sxs-lookup"><span data-stu-id="89677-145">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="89677-146">XML’den DataSet Yükleme</span><span class="sxs-lookup"><span data-stu-id="89677-146">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)
- [<span data-ttu-id="89677-147">XML’den DataSet Schema Bilgilerini Yükleme</span><span class="sxs-lookup"><span data-stu-id="89677-147">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="89677-148">DataRelations’ı İç İçe Yerleştirme</span><span class="sxs-lookup"><span data-stu-id="89677-148">Nesting DataRelations</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)
- [<span data-ttu-id="89677-149">DataSet içinde XML kullanma</span><span class="sxs-lookup"><span data-stu-id="89677-149">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
- [<span data-ttu-id="89677-150">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="89677-150">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [<span data-ttu-id="89677-151">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="89677-151">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
