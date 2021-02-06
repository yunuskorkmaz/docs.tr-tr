---
description: 'Daha fazla bilgi edinin: Ilişkileri erteleme'
title: İlişkilerin Çıkarımını Yapma
ms.date: 03/30/2017
ms.assetid: 8fa86a9d-6545-4a9d-b1f5-58d9742179c7
ms.openlocfilehash: a117581d512c1427c638ea862169ab3c7623d783
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652152"
---
# <a name="inferring-relationships"></a><span data-ttu-id="a4fb0-103">İlişkilerin Çıkarımını Yapma</span><span class="sxs-lookup"><span data-stu-id="a4fb0-103">Inferring Relationships</span></span>

<span data-ttu-id="a4fb0-104">Tablo olarak gösterilen bir öğe, tablo olarak da gösterilen bir alt öğe içeriyorsa, <xref:System.Data.DataRelation> iki tablo arasında bir oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="a4fb0-104">If an element that is inferred as a table has a child element that is also inferred as a table, a <xref:System.Data.DataRelation> will be created between the two tables.</span></span> <span data-ttu-id="a4fb0-105">Üst öğe için oluşturulan tabloya ve alt öğe için oluşturulan tabloya **ParentTableName_Id** adlı yeni bir sütun eklenir.</span><span class="sxs-lookup"><span data-stu-id="a4fb0-105">A new column with a name of **ParentTableName_Id** will be added to both the table created for the parent element, and the table created for the child element.</span></span> <span data-ttu-id="a4fb0-106">Bu kimlik sütununun **ColumnMapping** özelliği **MappingType. Hidden** olarak ayarlanacak.</span><span class="sxs-lookup"><span data-stu-id="a4fb0-106">The **ColumnMapping** property of this identity column will be set to **MappingType.Hidden**.</span></span> <span data-ttu-id="a4fb0-107">Sütun üst tablo için otomatik olarak artan birincil anahtar olur ve iki tablo arasında **DataRelation** için kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="a4fb0-107">The column will be an auto-incrementing primary key for the parent table, and will be used for the **DataRelation** between the two tables.</span></span> <span data-ttu-id="a4fb0-108">Eklenen kimlik sütununun veri türü, System. **String** olan diğer tüm çıkartılan sütunların veri türünden farklı olarak **System. Int32** olacaktır.</span><span class="sxs-lookup"><span data-stu-id="a4fb0-108">The data type of the added identity column will be **System.Int32**, unlike the data type of all other inferred columns, which is **System.String**.</span></span> <span data-ttu-id="a4fb0-109"><xref:System.Data.ForeignKeyConstraint>   =  Hem üst hem de alt tablolardaki yeni sütun kullanılarak DeleteRule **Cascade** ile birlikte oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="a4fb0-109">A <xref:System.Data.ForeignKeyConstraint> with **DeleteRule** = **Cascade** will also be created using the new column in both the parent and child tables.</span></span>  
  
 <span data-ttu-id="a4fb0-110">Örneğin, aşağıdaki XML 'i göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="a4fb0-110">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1 attr1="value1" attr2="value2"/>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="a4fb0-111">Çıkarım işlemi iki tablo üretecektir: **Element1** ve **ChildElement1**.</span><span class="sxs-lookup"><span data-stu-id="a4fb0-111">The inference process will produce two tables: **Element1** and **ChildElement1**.</span></span>  
  
 <span data-ttu-id="a4fb0-112">**Element1** tablosunun iki sütunu olacaktır: **Element1_Id** ve **ChildElement2**.</span><span class="sxs-lookup"><span data-stu-id="a4fb0-112">The **Element1** table will have two columns: **Element1_Id** and **ChildElement2**.</span></span> <span data-ttu-id="a4fb0-113">**Element1_Id** sütununun **ColumnMapping** özelliği **MappingType. Hidden** olarak ayarlanacak.</span><span class="sxs-lookup"><span data-stu-id="a4fb0-113">The **ColumnMapping** property of the **Element1_Id** column will be set to **MappingType.Hidden**.</span></span> <span data-ttu-id="a4fb0-114">**ChildElement2** sütununun **ColumnMapping** özelliği **MappingType. element** olarak ayarlanacak.</span><span class="sxs-lookup"><span data-stu-id="a4fb0-114">The **ColumnMapping** property of the **ChildElement2** column will be set to **MappingType.Element**.</span></span> <span data-ttu-id="a4fb0-115">**Element1_Id** sütunu, **Element1** tablosunun birincil anahtarı olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="a4fb0-115">The **Element1_Id** column will be set as the primary key of the **Element1** table.</span></span>  
  
 <span data-ttu-id="a4fb0-116">**ChildElement1** tablosunda üç sütun olacak: **attr1**, **attr2** ve **Element1_Id**.</span><span class="sxs-lookup"><span data-stu-id="a4fb0-116">The **ChildElement1** table will have three columns: **attr1**, **attr2** and **Element1_Id**.</span></span> <span data-ttu-id="a4fb0-117">**Attr1** ve **attr2** sütunlarının **ColumnMapping** özelliği **MappingType. Attribute** olarak ayarlanacak.</span><span class="sxs-lookup"><span data-stu-id="a4fb0-117">The **ColumnMapping** property for the **attr1** and **attr2** columns will be set to **MappingType.Attribute**.</span></span> <span data-ttu-id="a4fb0-118">**Element1_Id** sütununun **ColumnMapping** özelliği **MappingType. Hidden** olarak ayarlanacak.</span><span class="sxs-lookup"><span data-stu-id="a4fb0-118">The **ColumnMapping** property of the **Element1_Id** column will be set to **MappingType.Hidden**.</span></span>  
  
 <span data-ttu-id="a4fb0-119">Bir **DataRelation** ve **ForeignKeyConstraint** , her iki tablodan **Element1_Id** sütunları kullanılarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="a4fb0-119">A **DataRelation** and **ForeignKeyConstraint** will be created using the **Element1_Id** columns from both tables.</span></span>  
  
 <span data-ttu-id="a4fb0-120">**Veri kümesi:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="a4fb0-120">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="a4fb0-121">**Tablo:** Element1</span><span class="sxs-lookup"><span data-stu-id="a4fb0-121">**Table:** Element1</span></span>  
  
|<span data-ttu-id="a4fb0-122">Element1_Id</span><span class="sxs-lookup"><span data-stu-id="a4fb0-122">Element1_Id</span></span>|<span data-ttu-id="a4fb0-123">ChildElement2</span><span class="sxs-lookup"><span data-stu-id="a4fb0-123">ChildElement2</span></span>|  
|------------------|-------------------|  
|<span data-ttu-id="a4fb0-124">0</span><span class="sxs-lookup"><span data-stu-id="a4fb0-124">0</span></span>|<span data-ttu-id="a4fb0-125">Metin2</span><span class="sxs-lookup"><span data-stu-id="a4fb0-125">Text2</span></span>|  
  
 <span data-ttu-id="a4fb0-126">**Tablo:** ChildElement1</span><span class="sxs-lookup"><span data-stu-id="a4fb0-126">**Table:** ChildElement1</span></span>  
  
|<span data-ttu-id="a4fb0-127">attr1</span><span class="sxs-lookup"><span data-stu-id="a4fb0-127">attr1</span></span>|<span data-ttu-id="a4fb0-128">attr2</span><span class="sxs-lookup"><span data-stu-id="a4fb0-128">attr2</span></span>|<span data-ttu-id="a4fb0-129">Element1_Id</span><span class="sxs-lookup"><span data-stu-id="a4fb0-129">Element1_Id</span></span>|  
|-----------|-----------|------------------|  
|<span data-ttu-id="a4fb0-130">value1</span><span class="sxs-lookup"><span data-stu-id="a4fb0-130">value1</span></span>|<span data-ttu-id="a4fb0-131">value2</span><span class="sxs-lookup"><span data-stu-id="a4fb0-131">value2</span></span>|<span data-ttu-id="a4fb0-132">0</span><span class="sxs-lookup"><span data-stu-id="a4fb0-132">0</span></span>|  
  
 <span data-ttu-id="a4fb0-133">**DataRelation:** Element1_ChildElement1</span><span class="sxs-lookup"><span data-stu-id="a4fb0-133">**DataRelation:** Element1_ChildElement1</span></span>  
  
 <span data-ttu-id="a4fb0-134">**ParentTable:** Element1</span><span class="sxs-lookup"><span data-stu-id="a4fb0-134">**ParentTable:** Element1</span></span>  
  
 <span data-ttu-id="a4fb0-135">**ParentColumn:** Element1_Id</span><span class="sxs-lookup"><span data-stu-id="a4fb0-135">**ParentColumn:** Element1_Id</span></span>  
  
 <span data-ttu-id="a4fb0-136">**ChildTable:** ChildElement1</span><span class="sxs-lookup"><span data-stu-id="a4fb0-136">**ChildTable:** ChildElement1</span></span>  
  
 <span data-ttu-id="a4fb0-137">**ChildColumn:** Element1_Id</span><span class="sxs-lookup"><span data-stu-id="a4fb0-137">**ChildColumn:** Element1_Id</span></span>  
  
 <span data-ttu-id="a4fb0-138">**Iç içe:** Değeri</span><span class="sxs-lookup"><span data-stu-id="a4fb0-138">**Nested:** True</span></span>  
  
 <span data-ttu-id="a4fb0-139">**ForeignKeyConstraint:** Element1_ChildElement1</span><span class="sxs-lookup"><span data-stu-id="a4fb0-139">**ForeignKeyConstraint:** Element1_ChildElement1</span></span>  
  
 <span data-ttu-id="a4fb0-140">**Sütun:** Element1_Id</span><span class="sxs-lookup"><span data-stu-id="a4fb0-140">**Column:** Element1_Id</span></span>  
  
 <span data-ttu-id="a4fb0-141">**ParentTable:** Element1</span><span class="sxs-lookup"><span data-stu-id="a4fb0-141">**ParentTable:** Element1</span></span>  
  
 <span data-ttu-id="a4fb0-142">**ChildTable:** ChildElement1</span><span class="sxs-lookup"><span data-stu-id="a4fb0-142">**ChildTable:** ChildElement1</span></span>  
  
 <span data-ttu-id="a4fb0-143">**DeleteRule:** Seçilemez</span><span class="sxs-lookup"><span data-stu-id="a4fb0-143">**DeleteRule:** Cascade</span></span>  
  
 <span data-ttu-id="a4fb0-144">**AcceptRejectRule:** Seçim</span><span class="sxs-lookup"><span data-stu-id="a4fb0-144">**AcceptRejectRule:** None</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4fb0-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a4fb0-145">See also</span></span>

- [<span data-ttu-id="a4fb0-146">XML’den DataSet İlişkisel Yapısını Çıkarma</span><span class="sxs-lookup"><span data-stu-id="a4fb0-146">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="a4fb0-147">XML’den DataSet Yükleme</span><span class="sxs-lookup"><span data-stu-id="a4fb0-147">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="a4fb0-148">XML’den DataSet Schema Bilgilerini Yükleme</span><span class="sxs-lookup"><span data-stu-id="a4fb0-148">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="a4fb0-149">DataRelations’ı İç İçe Yerleştirme</span><span class="sxs-lookup"><span data-stu-id="a4fb0-149">Nesting DataRelations</span></span>](nesting-datarelations.md)
- [<span data-ttu-id="a4fb0-150">DataSet içinde XML kullanma</span><span class="sxs-lookup"><span data-stu-id="a4fb0-150">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="a4fb0-151">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="a4fb0-151">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="a4fb0-152">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a4fb0-152">ADO.NET Overview</span></span>](../ado-net-overview.md)
