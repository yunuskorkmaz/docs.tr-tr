---
title: İlişkileri çıkarımını yapma
ms.date: 03/30/2017
ms.assetid: 8fa86a9d-6545-4a9d-b1f5-58d9742179c7
ms.openlocfilehash: 9833966fa5a16bef70a6ae2b9ca618fde0e05fbb
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32759042"
---
# <a name="inferring-relationships"></a><span data-ttu-id="0ec0b-102">İlişkileri çıkarımını yapma</span><span class="sxs-lookup"><span data-stu-id="0ec0b-102">Inferring Relationships</span></span>
<span data-ttu-id="0ec0b-103">Ayrıca bir tablo olarak algılanır bir alt öğesi bir tablo çıkarımı yapılan bir öğe varsa, bir <xref:System.Data.DataRelation> iki tablo arasında oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="0ec0b-103">If an element that is inferred as a table has a child element that is also inferred as a table, a <xref:System.Data.DataRelation> will be created between the two tables.</span></span> <span data-ttu-id="0ec0b-104">Yeni bir sütun adıyla **ParentTableName_Id** üst öğe için oluşturulan tablo hem alt öğe için oluşturulan tablo eklenir.</span><span class="sxs-lookup"><span data-stu-id="0ec0b-104">A new column with a name of **ParentTableName_Id** will be added to both the table created for the parent element, and the table created for the child element.</span></span> <span data-ttu-id="0ec0b-105">**ColumnMapping** bu kimlik sütunu özelliği ayarlanacak **MappingType.Hidden**.</span><span class="sxs-lookup"><span data-stu-id="0ec0b-105">The **ColumnMapping** property of this identity column will be set to **MappingType.Hidden**.</span></span> <span data-ttu-id="0ec0b-106">Sütunu bir otomatik artan tablo için birincil anahtar üst olacaktır ve kullanılacak **DataRelation** iki tablo arasında.</span><span class="sxs-lookup"><span data-stu-id="0ec0b-106">The column will be an auto-incrementing primary key for the parent table, and will be used for the **DataRelation** between the two tables.</span></span> <span data-ttu-id="0ec0b-107">Eklenen kimlik sütununun veri türü olacaktır **System.Int32**, diğer tüm çıkarsanan sütun veri türü olan **System.String**.</span><span class="sxs-lookup"><span data-stu-id="0ec0b-107">The data type of the added identity column will be **System.Int32**, unlike the data type of all other inferred columns, which is **System.String**.</span></span> <span data-ttu-id="0ec0b-108">A <xref:System.Data.ForeignKeyConstraint> ile **DeleteRule** = **Cascade** da yeni bir sütun üst ve alt tablolarda kullanılarak oluşturulacak.</span><span class="sxs-lookup"><span data-stu-id="0ec0b-108">A <xref:System.Data.ForeignKeyConstraint> with **DeleteRule** = **Cascade** will also be created using the new column in both the parent and child tables.</span></span>  
  
 <span data-ttu-id="0ec0b-109">Örneğin, aşağıdaki XML göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="0ec0b-109">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1 attr1="value1" attr2="value2"/>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="0ec0b-110">Çıkarma işlemi iki tablo oluşturur: **Element1** ve **ChildElement1**.</span><span class="sxs-lookup"><span data-stu-id="0ec0b-110">The inference process will produce two tables: **Element1** and **ChildElement1**.</span></span>  
  
 <span data-ttu-id="0ec0b-111">**Element1** tablosu iki sütuna sahip: **Element1_Id** ve **ChildElement2**.</span><span class="sxs-lookup"><span data-stu-id="0ec0b-111">The **Element1** table will have two columns: **Element1_Id** and **ChildElement2**.</span></span> <span data-ttu-id="0ec0b-112">**ColumnMapping** özelliği **Element1_Id** sütun ayarlanacak **MappingType.Hidden**.</span><span class="sxs-lookup"><span data-stu-id="0ec0b-112">The **ColumnMapping** property of the **Element1_Id** column will be set to **MappingType.Hidden**.</span></span> <span data-ttu-id="0ec0b-113">**ColumnMapping** özelliği **ChildElement2** sütun ayarlanacak **MappingType.Element**.</span><span class="sxs-lookup"><span data-stu-id="0ec0b-113">The **ColumnMapping** property of the **ChildElement2** column will be set to **MappingType.Element**.</span></span> <span data-ttu-id="0ec0b-114">**Element1_Id** sütun birincil anahtarı olarak ayarlanacak **Element1** tablo.</span><span class="sxs-lookup"><span data-stu-id="0ec0b-114">The **Element1_Id** column will be set as the primary key of the **Element1** table.</span></span>  
  
 <span data-ttu-id="0ec0b-115">**ChildElement1** tablo üç sütun bulunur: **attr1**, **attr2** ve **Element1_Id**.</span><span class="sxs-lookup"><span data-stu-id="0ec0b-115">The **ChildElement1** table will have three columns: **attr1**, **attr2** and **Element1_Id**.</span></span> <span data-ttu-id="0ec0b-116">**ColumnMapping** özelliği için **attr1** ve **attr2** sütunlar ayarlanacak **MappingType.Attribute**.</span><span class="sxs-lookup"><span data-stu-id="0ec0b-116">The **ColumnMapping** property for the **attr1** and **attr2** columns will be set to **MappingType.Attribute**.</span></span> <span data-ttu-id="0ec0b-117">**ColumnMapping** özelliği **Element1_Id** sütun ayarlanacak **MappingType.Hidden**.</span><span class="sxs-lookup"><span data-stu-id="0ec0b-117">The **ColumnMapping** property of the **Element1_Id** column will be set to **MappingType.Hidden**.</span></span>  
  
 <span data-ttu-id="0ec0b-118">A **DataRelation** ve **ForeignKeyConstraint** kullanılarak oluşturulan **Element1_Id** her iki tablodan sütun.</span><span class="sxs-lookup"><span data-stu-id="0ec0b-118">A **DataRelation** and **ForeignKeyConstraint** will be created using the **Element1_Id** columns from both tables.</span></span>  
  
 <span data-ttu-id="0ec0b-119">**Veri kümesi:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="0ec0b-119">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="0ec0b-120">**Tablo:** Element1</span><span class="sxs-lookup"><span data-stu-id="0ec0b-120">**Table:** Element1</span></span>  
  
|<span data-ttu-id="0ec0b-121">Element1_Id</span><span class="sxs-lookup"><span data-stu-id="0ec0b-121">Element1_Id</span></span>|<span data-ttu-id="0ec0b-122">ChildElement2</span><span class="sxs-lookup"><span data-stu-id="0ec0b-122">ChildElement2</span></span>|  
|------------------|-------------------|  
|<span data-ttu-id="0ec0b-123">0</span><span class="sxs-lookup"><span data-stu-id="0ec0b-123">0</span></span>|<span data-ttu-id="0ec0b-124">Metin2</span><span class="sxs-lookup"><span data-stu-id="0ec0b-124">Text2</span></span>|  
  
 <span data-ttu-id="0ec0b-125">**Tablo:** ChildElement1</span><span class="sxs-lookup"><span data-stu-id="0ec0b-125">**Table:** ChildElement1</span></span>  
  
|<span data-ttu-id="0ec0b-126">attr1</span><span class="sxs-lookup"><span data-stu-id="0ec0b-126">attr1</span></span>|<span data-ttu-id="0ec0b-127">attr2</span><span class="sxs-lookup"><span data-stu-id="0ec0b-127">attr2</span></span>|<span data-ttu-id="0ec0b-128">Element1_Id</span><span class="sxs-lookup"><span data-stu-id="0ec0b-128">Element1_Id</span></span>|  
|-----------|-----------|------------------|  
|<span data-ttu-id="0ec0b-129">Değer1</span><span class="sxs-lookup"><span data-stu-id="0ec0b-129">value1</span></span>|<span data-ttu-id="0ec0b-130">Value2</span><span class="sxs-lookup"><span data-stu-id="0ec0b-130">value2</span></span>|<span data-ttu-id="0ec0b-131">0</span><span class="sxs-lookup"><span data-stu-id="0ec0b-131">0</span></span>|  
  
 <span data-ttu-id="0ec0b-132">**DataRelation:** Element1_ChildElement1</span><span class="sxs-lookup"><span data-stu-id="0ec0b-132">**DataRelation:** Element1_ChildElement1</span></span>  
  
 <span data-ttu-id="0ec0b-133">**ParentTable:** Element1</span><span class="sxs-lookup"><span data-stu-id="0ec0b-133">**ParentTable:** Element1</span></span>  
  
 <span data-ttu-id="0ec0b-134">**ParentColumn:** Element1_Id</span><span class="sxs-lookup"><span data-stu-id="0ec0b-134">**ParentColumn:** Element1_Id</span></span>  
  
 <span data-ttu-id="0ec0b-135">**Geldiği:** ChildElement1</span><span class="sxs-lookup"><span data-stu-id="0ec0b-135">**ChildTable:** ChildElement1</span></span>  
  
 <span data-ttu-id="0ec0b-136">**ChildColumn:** Element1_Id</span><span class="sxs-lookup"><span data-stu-id="0ec0b-136">**ChildColumn:** Element1_Id</span></span>  
  
 <span data-ttu-id="0ec0b-137">**İç içe:** True</span><span class="sxs-lookup"><span data-stu-id="0ec0b-137">**Nested:** True</span></span>  
  
 <span data-ttu-id="0ec0b-138">**ForeignKeyConstraint:** Element1_ChildElement1</span><span class="sxs-lookup"><span data-stu-id="0ec0b-138">**ForeignKeyConstraint:** Element1_ChildElement1</span></span>  
  
 <span data-ttu-id="0ec0b-139">**Sütun:** Element1_Id</span><span class="sxs-lookup"><span data-stu-id="0ec0b-139">**Column:** Element1_Id</span></span>  
  
 <span data-ttu-id="0ec0b-140">**ParentTable:** Element1</span><span class="sxs-lookup"><span data-stu-id="0ec0b-140">**ParentTable:** Element1</span></span>  
  
 <span data-ttu-id="0ec0b-141">**Geldiği:** ChildElement1</span><span class="sxs-lookup"><span data-stu-id="0ec0b-141">**ChildTable:** ChildElement1</span></span>  
  
 <span data-ttu-id="0ec0b-142">**DeleteRule:** Cascade</span><span class="sxs-lookup"><span data-stu-id="0ec0b-142">**DeleteRule:** Cascade</span></span>  
  
 <span data-ttu-id="0ec0b-143">**AcceptRejectRule:** yok</span><span class="sxs-lookup"><span data-stu-id="0ec0b-143">**AcceptRejectRule:** None</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ec0b-144">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0ec0b-144">See Also</span></span>  
 [<span data-ttu-id="0ec0b-145">XML’den DataSet İlişkisel Yapısını Çıkarma</span><span class="sxs-lookup"><span data-stu-id="0ec0b-145">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [<span data-ttu-id="0ec0b-146">XML’den DataSet Yükleme</span><span class="sxs-lookup"><span data-stu-id="0ec0b-146">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [<span data-ttu-id="0ec0b-147">XML’den DataSet Schema Bilgilerini Yükleme</span><span class="sxs-lookup"><span data-stu-id="0ec0b-147">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [<span data-ttu-id="0ec0b-148">DataRelations’ı İç İçe Yerleştirme</span><span class="sxs-lookup"><span data-stu-id="0ec0b-148">Nesting DataRelations</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)  
 [<span data-ttu-id="0ec0b-149">DataSet içinde XML kullanma</span><span class="sxs-lookup"><span data-stu-id="0ec0b-149">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [<span data-ttu-id="0ec0b-150">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="0ec0b-150">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="0ec0b-151">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="0ec0b-151">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
