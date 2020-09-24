---
title: İlişkilerin Çıkarımını Yapma
ms.date: 03/30/2017
ms.assetid: 8fa86a9d-6545-4a9d-b1f5-58d9742179c7
ms.openlocfilehash: ee691eee95c34afdb6374cdd7448d4b44ece3055
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177572"
---
# <a name="inferring-relationships"></a><span data-ttu-id="fcbb7-102">İlişkilerin Çıkarımını Yapma</span><span class="sxs-lookup"><span data-stu-id="fcbb7-102">Inferring Relationships</span></span>

<span data-ttu-id="fcbb7-103">Tablo olarak gösterilen bir öğe, tablo olarak da gösterilen bir alt öğe içeriyorsa, <xref:System.Data.DataRelation> iki tablo arasında bir oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="fcbb7-103">If an element that is inferred as a table has a child element that is also inferred as a table, a <xref:System.Data.DataRelation> will be created between the two tables.</span></span> <span data-ttu-id="fcbb7-104">Üst öğe için oluşturulan tabloya ve alt öğe için oluşturulan tabloya **ParentTableName_Id** adlı yeni bir sütun eklenir.</span><span class="sxs-lookup"><span data-stu-id="fcbb7-104">A new column with a name of **ParentTableName_Id** will be added to both the table created for the parent element, and the table created for the child element.</span></span> <span data-ttu-id="fcbb7-105">Bu kimlik sütununun **ColumnMapping** özelliği **MappingType. Hidden**olarak ayarlanacak.</span><span class="sxs-lookup"><span data-stu-id="fcbb7-105">The **ColumnMapping** property of this identity column will be set to **MappingType.Hidden**.</span></span> <span data-ttu-id="fcbb7-106">Sütun üst tablo için otomatik olarak artan birincil anahtar olur ve iki tablo arasında **DataRelation** için kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="fcbb7-106">The column will be an auto-incrementing primary key for the parent table, and will be used for the **DataRelation** between the two tables.</span></span> <span data-ttu-id="fcbb7-107">Eklenen kimlik sütununun veri türü, System. **String**olan diğer tüm çıkartılan sütunların veri türünden farklı olarak **System. Int32**olacaktır.</span><span class="sxs-lookup"><span data-stu-id="fcbb7-107">The data type of the added identity column will be **System.Int32**, unlike the data type of all other inferred columns, which is **System.String**.</span></span> <span data-ttu-id="fcbb7-108"><xref:System.Data.ForeignKeyConstraint> **DeleteRule**  =  Hem üst hem de alt tablolardaki yeni sütun kullanılarak DeleteRule**Cascade** ile birlikte oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="fcbb7-108">A <xref:System.Data.ForeignKeyConstraint> with **DeleteRule** = **Cascade** will also be created using the new column in both the parent and child tables.</span></span>  
  
 <span data-ttu-id="fcbb7-109">Örneğin, aşağıdaki XML 'i göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="fcbb7-109">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1 attr1="value1" attr2="value2"/>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="fcbb7-110">Çıkarım işlemi iki tablo üretecektir: **Element1** ve **ChildElement1**.</span><span class="sxs-lookup"><span data-stu-id="fcbb7-110">The inference process will produce two tables: **Element1** and **ChildElement1**.</span></span>  
  
 <span data-ttu-id="fcbb7-111">**Element1** tablosunun iki sütunu olacaktır: **Element1_Id** ve **ChildElement2**.</span><span class="sxs-lookup"><span data-stu-id="fcbb7-111">The **Element1** table will have two columns: **Element1_Id** and **ChildElement2**.</span></span> <span data-ttu-id="fcbb7-112">**Element1_Id** sütununun **ColumnMapping** özelliği **MappingType. Hidden**olarak ayarlanacak.</span><span class="sxs-lookup"><span data-stu-id="fcbb7-112">The **ColumnMapping** property of the **Element1_Id** column will be set to **MappingType.Hidden**.</span></span> <span data-ttu-id="fcbb7-113">**ChildElement2** sütununun **ColumnMapping** özelliği **MappingType. element**olarak ayarlanacak.</span><span class="sxs-lookup"><span data-stu-id="fcbb7-113">The **ColumnMapping** property of the **ChildElement2** column will be set to **MappingType.Element**.</span></span> <span data-ttu-id="fcbb7-114">**Element1_Id** sütunu, **Element1** tablosunun birincil anahtarı olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="fcbb7-114">The **Element1_Id** column will be set as the primary key of the **Element1** table.</span></span>  
  
 <span data-ttu-id="fcbb7-115">**ChildElement1** tablosunda üç sütun olacak: **attr1**, **attr2** ve **Element1_Id**.</span><span class="sxs-lookup"><span data-stu-id="fcbb7-115">The **ChildElement1** table will have three columns: **attr1**, **attr2** and **Element1_Id**.</span></span> <span data-ttu-id="fcbb7-116">**Attr1** ve **attr2** sütunlarının **ColumnMapping** özelliği **MappingType. Attribute**olarak ayarlanacak.</span><span class="sxs-lookup"><span data-stu-id="fcbb7-116">The **ColumnMapping** property for the **attr1** and **attr2** columns will be set to **MappingType.Attribute**.</span></span> <span data-ttu-id="fcbb7-117">**Element1_Id** sütununun **ColumnMapping** özelliği **MappingType. Hidden**olarak ayarlanacak.</span><span class="sxs-lookup"><span data-stu-id="fcbb7-117">The **ColumnMapping** property of the **Element1_Id** column will be set to **MappingType.Hidden**.</span></span>  
  
 <span data-ttu-id="fcbb7-118">Bir **DataRelation** ve **ForeignKeyConstraint** , her iki tablodan **Element1_Id** sütunları kullanılarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="fcbb7-118">A **DataRelation** and **ForeignKeyConstraint** will be created using the **Element1_Id** columns from both tables.</span></span>  
  
 <span data-ttu-id="fcbb7-119">**Veri kümesi:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="fcbb7-119">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="fcbb7-120">**Tablo:** Element1</span><span class="sxs-lookup"><span data-stu-id="fcbb7-120">**Table:** Element1</span></span>  
  
|<span data-ttu-id="fcbb7-121">Element1_Id</span><span class="sxs-lookup"><span data-stu-id="fcbb7-121">Element1_Id</span></span>|<span data-ttu-id="fcbb7-122">ChildElement2</span><span class="sxs-lookup"><span data-stu-id="fcbb7-122">ChildElement2</span></span>|  
|------------------|-------------------|  
|<span data-ttu-id="fcbb7-123">0</span><span class="sxs-lookup"><span data-stu-id="fcbb7-123">0</span></span>|<span data-ttu-id="fcbb7-124">Metin2</span><span class="sxs-lookup"><span data-stu-id="fcbb7-124">Text2</span></span>|  
  
 <span data-ttu-id="fcbb7-125">**Tablo:** ChildElement1</span><span class="sxs-lookup"><span data-stu-id="fcbb7-125">**Table:** ChildElement1</span></span>  
  
|<span data-ttu-id="fcbb7-126">attr1</span><span class="sxs-lookup"><span data-stu-id="fcbb7-126">attr1</span></span>|<span data-ttu-id="fcbb7-127">attr2</span><span class="sxs-lookup"><span data-stu-id="fcbb7-127">attr2</span></span>|<span data-ttu-id="fcbb7-128">Element1_Id</span><span class="sxs-lookup"><span data-stu-id="fcbb7-128">Element1_Id</span></span>|  
|-----------|-----------|------------------|  
|<span data-ttu-id="fcbb7-129">value1</span><span class="sxs-lookup"><span data-stu-id="fcbb7-129">value1</span></span>|<span data-ttu-id="fcbb7-130">value2</span><span class="sxs-lookup"><span data-stu-id="fcbb7-130">value2</span></span>|<span data-ttu-id="fcbb7-131">0</span><span class="sxs-lookup"><span data-stu-id="fcbb7-131">0</span></span>|  
  
 <span data-ttu-id="fcbb7-132">**DataRelation:** Element1_ChildElement1</span><span class="sxs-lookup"><span data-stu-id="fcbb7-132">**DataRelation:** Element1_ChildElement1</span></span>  
  
 <span data-ttu-id="fcbb7-133">**ParentTable:** Element1</span><span class="sxs-lookup"><span data-stu-id="fcbb7-133">**ParentTable:** Element1</span></span>  
  
 <span data-ttu-id="fcbb7-134">**ParentColumn:** Element1_Id</span><span class="sxs-lookup"><span data-stu-id="fcbb7-134">**ParentColumn:** Element1_Id</span></span>  
  
 <span data-ttu-id="fcbb7-135">**ChildTable:** ChildElement1</span><span class="sxs-lookup"><span data-stu-id="fcbb7-135">**ChildTable:** ChildElement1</span></span>  
  
 <span data-ttu-id="fcbb7-136">**ChildColumn:** Element1_Id</span><span class="sxs-lookup"><span data-stu-id="fcbb7-136">**ChildColumn:** Element1_Id</span></span>  
  
 <span data-ttu-id="fcbb7-137">**Iç içe:** Değeri</span><span class="sxs-lookup"><span data-stu-id="fcbb7-137">**Nested:** True</span></span>  
  
 <span data-ttu-id="fcbb7-138">**ForeignKeyConstraint:** Element1_ChildElement1</span><span class="sxs-lookup"><span data-stu-id="fcbb7-138">**ForeignKeyConstraint:** Element1_ChildElement1</span></span>  
  
 <span data-ttu-id="fcbb7-139">**Sütun:** Element1_Id</span><span class="sxs-lookup"><span data-stu-id="fcbb7-139">**Column:** Element1_Id</span></span>  
  
 <span data-ttu-id="fcbb7-140">**ParentTable:** Element1</span><span class="sxs-lookup"><span data-stu-id="fcbb7-140">**ParentTable:** Element1</span></span>  
  
 <span data-ttu-id="fcbb7-141">**ChildTable:** ChildElement1</span><span class="sxs-lookup"><span data-stu-id="fcbb7-141">**ChildTable:** ChildElement1</span></span>  
  
 <span data-ttu-id="fcbb7-142">**DeleteRule:** Seçilemez</span><span class="sxs-lookup"><span data-stu-id="fcbb7-142">**DeleteRule:** Cascade</span></span>  
  
 <span data-ttu-id="fcbb7-143">**AcceptRejectRule:** Seçim</span><span class="sxs-lookup"><span data-stu-id="fcbb7-143">**AcceptRejectRule:** None</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcbb7-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fcbb7-144">See also</span></span>

- [<span data-ttu-id="fcbb7-145">XML’den DataSet İlişkisel Yapısını Çıkarma</span><span class="sxs-lookup"><span data-stu-id="fcbb7-145">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="fcbb7-146">XML’den DataSet Yükleme</span><span class="sxs-lookup"><span data-stu-id="fcbb7-146">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="fcbb7-147">XML’den DataSet Schema Bilgilerini Yükleme</span><span class="sxs-lookup"><span data-stu-id="fcbb7-147">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="fcbb7-148">DataRelations’ı İç İçe Yerleştirme</span><span class="sxs-lookup"><span data-stu-id="fcbb7-148">Nesting DataRelations</span></span>](nesting-datarelations.md)
- [<span data-ttu-id="fcbb7-149">DataSet içinde XML kullanma</span><span class="sxs-lookup"><span data-stu-id="fcbb7-149">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="fcbb7-150">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="fcbb7-150">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="fcbb7-151">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="fcbb7-151">ADO.NET Overview</span></span>](../ado-net-overview.md)
