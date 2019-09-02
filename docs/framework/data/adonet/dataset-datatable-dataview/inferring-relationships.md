---
title: İlişkilerin Çıkarımını Yapma
ms.date: 03/30/2017
ms.assetid: 8fa86a9d-6545-4a9d-b1f5-58d9742179c7
ms.openlocfilehash: 92a4953dc7f5119ffbf171ff2a7bf5b58e896638
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204764"
---
# <a name="inferring-relationships"></a><span data-ttu-id="2ad7b-102">İlişkilerin Çıkarımını Yapma</span><span class="sxs-lookup"><span data-stu-id="2ad7b-102">Inferring Relationships</span></span>
<span data-ttu-id="2ad7b-103">Tablo olarak gösterilen bir öğe, tablo olarak da gösterilen bir alt öğe içeriyorsa, iki tablo arasında bir <xref:System.Data.DataRelation> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="2ad7b-103">If an element that is inferred as a table has a child element that is also inferred as a table, a <xref:System.Data.DataRelation> will be created between the two tables.</span></span> <span data-ttu-id="2ad7b-104">Üst öğe için oluşturulan tabloya ve alt öğe için oluşturulan tabloya **ParentTableName_Id** adlı yeni bir sütun eklenir.</span><span class="sxs-lookup"><span data-stu-id="2ad7b-104">A new column with a name of **ParentTableName_Id** will be added to both the table created for the parent element, and the table created for the child element.</span></span> <span data-ttu-id="2ad7b-105">Bu kimlik sütununun **ColumnMapping** özelliği **MappingType. Hidden**olarak ayarlanacak.</span><span class="sxs-lookup"><span data-stu-id="2ad7b-105">The **ColumnMapping** property of this identity column will be set to **MappingType.Hidden**.</span></span> <span data-ttu-id="2ad7b-106">Sütun üst tablo için otomatik olarak artan birincil anahtar olur ve iki tablo arasında **DataRelation** için kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="2ad7b-106">The column will be an auto-incrementing primary key for the parent table, and will be used for the **DataRelation** between the two tables.</span></span> <span data-ttu-id="2ad7b-107">Eklenen kimlik sütununun veri türü, System. **String**olan diğer tüm çıkartılan sütunların veri türünden farklı olarak **System. Int32**olacaktır.</span><span class="sxs-lookup"><span data-stu-id="2ad7b-107">The data type of the added identity column will be **System.Int32**, unlike the data type of all other inferred columns, which is **System.String**.</span></span> <span data-ttu-id="2ad7b-108">Hem üst hem de alt tablolardaki yeni sütun kullanılarak **DeleteRule** = **Cascade** ilebirlikteoluşturulur.<xref:System.Data.ForeignKeyConstraint></span><span class="sxs-lookup"><span data-stu-id="2ad7b-108">A <xref:System.Data.ForeignKeyConstraint> with **DeleteRule** = **Cascade** will also be created using the new column in both the parent and child tables.</span></span>  
  
 <span data-ttu-id="2ad7b-109">Örneğin, aşağıdaki XML 'i göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="2ad7b-109">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1 attr1="value1" attr2="value2"/>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="2ad7b-110">Çıkarım işlemi iki tablo oluşturacak: **Element1** ve **ChildElement1**.</span><span class="sxs-lookup"><span data-stu-id="2ad7b-110">The inference process will produce two tables: **Element1** and **ChildElement1**.</span></span>  
  
 <span data-ttu-id="2ad7b-111">**Element1** tablosunun iki sütunu olacaktır: **Element1_Id** ve **ChildElement2**.</span><span class="sxs-lookup"><span data-stu-id="2ad7b-111">The **Element1** table will have two columns: **Element1_Id** and **ChildElement2**.</span></span> <span data-ttu-id="2ad7b-112">**Element1_Id** sütununun **ColumnMapping** özelliği **MappingType. Hidden**olarak ayarlanacak.</span><span class="sxs-lookup"><span data-stu-id="2ad7b-112">The **ColumnMapping** property of the **Element1_Id** column will be set to **MappingType.Hidden**.</span></span> <span data-ttu-id="2ad7b-113">**ChildElement2** sütununun **ColumnMapping** özelliği **MappingType. element**olarak ayarlanacak.</span><span class="sxs-lookup"><span data-stu-id="2ad7b-113">The **ColumnMapping** property of the **ChildElement2** column will be set to **MappingType.Element**.</span></span> <span data-ttu-id="2ad7b-114">**Element1_Id** sütunu, **Element1** tablosunun birincil anahtarı olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="2ad7b-114">The **Element1_Id** column will be set as the primary key of the **Element1** table.</span></span>  
  
 <span data-ttu-id="2ad7b-115">**ChildElement1** tablosunda üç sütun olacak: **attr1**, **attr2** ve **Element1_Id**.</span><span class="sxs-lookup"><span data-stu-id="2ad7b-115">The **ChildElement1** table will have three columns: **attr1**, **attr2** and **Element1_Id**.</span></span> <span data-ttu-id="2ad7b-116">**Attr1** ve **attr2** sütunlarının **ColumnMapping** özelliği **MappingType. Attribute**olarak ayarlanacak.</span><span class="sxs-lookup"><span data-stu-id="2ad7b-116">The **ColumnMapping** property for the **attr1** and **attr2** columns will be set to **MappingType.Attribute**.</span></span> <span data-ttu-id="2ad7b-117">**Element1_Id** sütununun **ColumnMapping** özelliği **MappingType. Hidden**olarak ayarlanacak.</span><span class="sxs-lookup"><span data-stu-id="2ad7b-117">The **ColumnMapping** property of the **Element1_Id** column will be set to **MappingType.Hidden**.</span></span>  
  
 <span data-ttu-id="2ad7b-118">Bir **DataRelation** ve **ForeignKeyConstraint** , her iki tablodan **Element1_Id** sütunları kullanılarak oluşturulacaktır.</span><span class="sxs-lookup"><span data-stu-id="2ad7b-118">A **DataRelation** and **ForeignKeyConstraint** will be created using the **Element1_Id** columns from both tables.</span></span>  
  
 <span data-ttu-id="2ad7b-119">**Veri kümesi** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="2ad7b-119">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="2ad7b-120">**Tablosundan** Element1</span><span class="sxs-lookup"><span data-stu-id="2ad7b-120">**Table:** Element1</span></span>  
  
|<span data-ttu-id="2ad7b-121">Element1_Id</span><span class="sxs-lookup"><span data-stu-id="2ad7b-121">Element1_Id</span></span>|<span data-ttu-id="2ad7b-122">ChildElement2</span><span class="sxs-lookup"><span data-stu-id="2ad7b-122">ChildElement2</span></span>|  
|------------------|-------------------|  
|<span data-ttu-id="2ad7b-123">0</span><span class="sxs-lookup"><span data-stu-id="2ad7b-123">0</span></span>|<span data-ttu-id="2ad7b-124">Metin2</span><span class="sxs-lookup"><span data-stu-id="2ad7b-124">Text2</span></span>|  
  
 <span data-ttu-id="2ad7b-125">**Tablosundan** ChildElement1</span><span class="sxs-lookup"><span data-stu-id="2ad7b-125">**Table:** ChildElement1</span></span>  
  
|<span data-ttu-id="2ad7b-126">attr1</span><span class="sxs-lookup"><span data-stu-id="2ad7b-126">attr1</span></span>|<span data-ttu-id="2ad7b-127">attr2</span><span class="sxs-lookup"><span data-stu-id="2ad7b-127">attr2</span></span>|<span data-ttu-id="2ad7b-128">Element1_Id</span><span class="sxs-lookup"><span data-stu-id="2ad7b-128">Element1_Id</span></span>|  
|-----------|-----------|------------------|  
|<span data-ttu-id="2ad7b-129">value1</span><span class="sxs-lookup"><span data-stu-id="2ad7b-129">value1</span></span>|<span data-ttu-id="2ad7b-130">value2</span><span class="sxs-lookup"><span data-stu-id="2ad7b-130">value2</span></span>|<span data-ttu-id="2ad7b-131">0</span><span class="sxs-lookup"><span data-stu-id="2ad7b-131">0</span></span>|  
  
 <span data-ttu-id="2ad7b-132">**Nesnesinin** Element1_ChildElement1</span><span class="sxs-lookup"><span data-stu-id="2ad7b-132">**DataRelation:** Element1_ChildElement1</span></span>  
  
 <span data-ttu-id="2ad7b-133">**ParentTable:** Element1</span><span class="sxs-lookup"><span data-stu-id="2ad7b-133">**ParentTable:** Element1</span></span>  
  
 <span data-ttu-id="2ad7b-134">**ParentColumn:** Element1_Id</span><span class="sxs-lookup"><span data-stu-id="2ad7b-134">**ParentColumn:** Element1_Id</span></span>  
  
 <span data-ttu-id="2ad7b-135">**Childschema** ChildElement1</span><span class="sxs-lookup"><span data-stu-id="2ad7b-135">**ChildTable:** ChildElement1</span></span>  
  
 <span data-ttu-id="2ad7b-136">**ChildColumn:** Element1_Id</span><span class="sxs-lookup"><span data-stu-id="2ad7b-136">**ChildColumn:** Element1_Id</span></span>  
  
 <span data-ttu-id="2ad7b-137">**Ble** Doğru</span><span class="sxs-lookup"><span data-stu-id="2ad7b-137">**Nested:** True</span></span>  
  
 <span data-ttu-id="2ad7b-138">**ForeignKeyConstraint** Element1_ChildElement1</span><span class="sxs-lookup"><span data-stu-id="2ad7b-138">**ForeignKeyConstraint:** Element1_ChildElement1</span></span>  
  
 <span data-ttu-id="2ad7b-139">**Sütunuyla** Element1_Id</span><span class="sxs-lookup"><span data-stu-id="2ad7b-139">**Column:** Element1_Id</span></span>  
  
 <span data-ttu-id="2ad7b-140">**ParentTable:** Element1</span><span class="sxs-lookup"><span data-stu-id="2ad7b-140">**ParentTable:** Element1</span></span>  
  
 <span data-ttu-id="2ad7b-141">**Childschema** ChildElement1</span><span class="sxs-lookup"><span data-stu-id="2ad7b-141">**ChildTable:** ChildElement1</span></span>  
  
 <span data-ttu-id="2ad7b-142">**DeleteRule:** Seçilemez</span><span class="sxs-lookup"><span data-stu-id="2ad7b-142">**DeleteRule:** Cascade</span></span>  
  
 <span data-ttu-id="2ad7b-143">**AcceptRejectRule:** Yok.</span><span class="sxs-lookup"><span data-stu-id="2ad7b-143">**AcceptRejectRule:** None</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ad7b-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2ad7b-144">See also</span></span>

- [<span data-ttu-id="2ad7b-145">XML’den DataSet İlişkisel Yapısını Çıkarma</span><span class="sxs-lookup"><span data-stu-id="2ad7b-145">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="2ad7b-146">XML’den DataSet Yükleme</span><span class="sxs-lookup"><span data-stu-id="2ad7b-146">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="2ad7b-147">XML’den DataSet Schema Bilgilerini Yükleme</span><span class="sxs-lookup"><span data-stu-id="2ad7b-147">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="2ad7b-148">DataRelations’ı İç İçe Yerleştirme</span><span class="sxs-lookup"><span data-stu-id="2ad7b-148">Nesting DataRelations</span></span>](nesting-datarelations.md)
- [<span data-ttu-id="2ad7b-149">DataSet içinde XML kullanma</span><span class="sxs-lookup"><span data-stu-id="2ad7b-149">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="2ad7b-150">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="2ad7b-150">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="2ad7b-151">ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="2ad7b-151">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
