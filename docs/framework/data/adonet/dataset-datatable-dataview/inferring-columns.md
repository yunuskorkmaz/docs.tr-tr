---
title: Sütunların Çıkarımını Yapma
ms.date: 03/30/2017
ms.assetid: 0e022699-c922-454c-93e2-957dd7e7247a
ms.openlocfilehash: 2718cbcf29799f99c8648b129fdb6079a6f6d344
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786180"
---
# <a name="inferring-columns"></a><span data-ttu-id="3d1f8-102">Sütunların Çıkarımını Yapma</span><span class="sxs-lookup"><span data-stu-id="3d1f8-102">Inferring Columns</span></span>
<span data-ttu-id="3d1f8-103">ADO.net, bir XML belgesinden bir <xref:System.Data.DataSet>için tablo olarak hangi öğelerin çıkarması gerektiğini belirledikten sonra, bu tablolar için sütunları algılar.</span><span class="sxs-lookup"><span data-stu-id="3d1f8-103">After ADO.NET has determined from an XML document which elements to infer as tables for a <xref:System.Data.DataSet>, it then infers the columns for those tables.</span></span> <span data-ttu-id="3d1f8-104">ADO.NET 2,0, her **simpleType** öğe için kesin olarak belirlenmiş bir veri türünü gösteren yeni bir şema çıkarımı altyapısı sunmuştur.</span><span class="sxs-lookup"><span data-stu-id="3d1f8-104">ADO.NET 2.0 introduced a new schema inference engine that infers a strongly typed data type for each **simpleType** element.</span></span> <span data-ttu-id="3d1f8-105">Önceki sürümlerde, gösterilen bir **simpleType** öğenin veri türü her zaman **xsd: String**idi.</span><span class="sxs-lookup"><span data-stu-id="3d1f8-105">In previous versions, the data type of an inferred **simpleType** element was always **xsd:string**.</span></span>  
  
## <a name="migration-and-backward-compatibility"></a><span data-ttu-id="3d1f8-106">Geçiş ve geri uyumluluk</span><span class="sxs-lookup"><span data-stu-id="3d1f8-106">Migration and Backward Compatibility</span></span>  
 <span data-ttu-id="3d1f8-107">**ReadXml** yöntemi **ınsetype**türünde bir bağımsız değişken alır.</span><span class="sxs-lookup"><span data-stu-id="3d1f8-107">The **ReadXml** method takes an argument of type **InferSchema**.</span></span> <span data-ttu-id="3d1f8-108">Bu bağımsız değişken, önceki sürümlerle uyumlu çıkarım davranışı belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="3d1f8-108">This argument allows you to specify inference behavior compatible with previous versions.</span></span> <span data-ttu-id="3d1f8-109">**Inseschema** numaralandırması için kullanılabilir değerler aşağıdaki tabloda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="3d1f8-109">The available values for the **InferSchema** enumeration are shown in the following table.</span></span>  
  
 <xref:System.Data.XmlReadMode.InferSchema>  
 <span data-ttu-id="3d1f8-110">, Bir basit türü her zaman olarak <xref:System.String>değiştirerek geriye dönük uyumluluk sağlar.</span><span class="sxs-lookup"><span data-stu-id="3d1f8-110">Provides backward compatibility by always inferring a simple type as <xref:System.String>.</span></span>  
  
 <xref:System.Data.XmlReadMode.InferTypedSchema>  
 <span data-ttu-id="3d1f8-111">Kesin tür belirtilmiş bir veri türünü haller.</span><span class="sxs-lookup"><span data-stu-id="3d1f8-111">Infers a strongly typed data type.</span></span> <span data-ttu-id="3d1f8-112">İle kullanılırsa bir <xref:System.Data.DataTable>özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3d1f8-112">Throws an exception if used with a <xref:System.Data.DataTable>.</span></span>  
  
 <xref:System.Data.XmlReadMode.IgnoreSchema>  
 <span data-ttu-id="3d1f8-113">Herhangi bir satır içi şemayı yoksayar ve verileri var olan <xref:System.Data.DataSet> şemaya okur.</span><span class="sxs-lookup"><span data-stu-id="3d1f8-113">Ignores any inline schema and reads data into the existing <xref:System.Data.DataSet> schema.</span></span>  
  
## <a name="attributes"></a><span data-ttu-id="3d1f8-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3d1f8-114">Attributes</span></span>  
 <span data-ttu-id="3d1f8-115">[Tablolarda](inferring-tables.md)tanımlandığı gibi, öznitelikleri olan bir öğesi tablo olarak çıkarsolur.</span><span class="sxs-lookup"><span data-stu-id="3d1f8-115">As defined in [Inferring Tables](inferring-tables.md), an element with attributes will be inferred as a table.</span></span> <span data-ttu-id="3d1f8-116">Daha sonra bu öğenin öznitelikleri tablo için sütun olarak algılanır.</span><span class="sxs-lookup"><span data-stu-id="3d1f8-116">The attributes of that element will then be inferred as columns for the table.</span></span> <span data-ttu-id="3d1f8-117">Şema XML 'e geri yazılmışsa sütun adlarının öznitelik olarak yazılmasını sağlamak için sütunların **ColumnMapping** özelliği **MappingType. Attribute**olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="3d1f8-117">The **ColumnMapping** property of the columns will be set to **MappingType.Attribute**, to ensure that the column names will be written as attributes if the schema is written back to XML.</span></span> <span data-ttu-id="3d1f8-118">Özniteliklerin değerleri tablodaki bir satırda depolanır.</span><span class="sxs-lookup"><span data-stu-id="3d1f8-118">The values of the attributes are stored in a row in the table.</span></span> <span data-ttu-id="3d1f8-119">Örneğin, aşağıdaki XML 'i göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="3d1f8-119">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 <span data-ttu-id="3d1f8-120">Çıkarım işlemi, **Element1** adında, **attr1** ve **attr2**olmak üzere iki sütunlu bir tablo oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3d1f8-120">The inference process will produce a table named **Element1** with two columns, **attr1** and **attr2**.</span></span> <span data-ttu-id="3d1f8-121">Her iki sütunun **ColumnMapping** özelliği **MappingType. Attribute**olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="3d1f8-121">The **ColumnMapping** property of both columns will be set to **MappingType.Attribute**.</span></span>  
  
 <span data-ttu-id="3d1f8-122">**Veri kümesi** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="3d1f8-122">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="3d1f8-123">**Tablosundan** Element1</span><span class="sxs-lookup"><span data-stu-id="3d1f8-123">**Table:** Element1</span></span>  
  
|<span data-ttu-id="3d1f8-124">attr1</span><span class="sxs-lookup"><span data-stu-id="3d1f8-124">attr1</span></span>|<span data-ttu-id="3d1f8-125">attr2</span><span class="sxs-lookup"><span data-stu-id="3d1f8-125">attr2</span></span>|  
|-----------|-----------|  
|<span data-ttu-id="3d1f8-126">value1</span><span class="sxs-lookup"><span data-stu-id="3d1f8-126">value1</span></span>|<span data-ttu-id="3d1f8-127">value2</span><span class="sxs-lookup"><span data-stu-id="3d1f8-127">value2</span></span>|  
  
## <a name="elements-without-attributes-or-child-elements"></a><span data-ttu-id="3d1f8-128">Öznitelikleri veya alt öğeleri olmayan öğeler</span><span class="sxs-lookup"><span data-stu-id="3d1f8-128">Elements Without Attributes or Child Elements</span></span>  
 <span data-ttu-id="3d1f8-129">Bir öğenin alt öğesi veya özniteliği yoksa, sütun olarak algılanır.</span><span class="sxs-lookup"><span data-stu-id="3d1f8-129">If an element has no child elements or attributes, it will be inferred as a column.</span></span> <span data-ttu-id="3d1f8-130">Sütunun **ColumnMapping** özelliği **MappingType. element**olarak ayarlanacak.</span><span class="sxs-lookup"><span data-stu-id="3d1f8-130">The **ColumnMapping** property of the column will be set to **MappingType.Element**.</span></span> <span data-ttu-id="3d1f8-131">Alt öğeler için metin, tablodaki bir satırda saklanır.</span><span class="sxs-lookup"><span data-stu-id="3d1f8-131">The text for child elements is stored in a row in the table.</span></span> <span data-ttu-id="3d1f8-132">Örneğin, aşağıdaki XML 'i göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="3d1f8-132">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="3d1f8-133">Çıkarım işlemi, **Element1** adında, **ChildElement1** ve **ChildElement2**olmak üzere iki sütunlu bir tablo oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3d1f8-133">The inference process will produce a table named **Element1** with two columns, **ChildElement1** and **ChildElement2**.</span></span> <span data-ttu-id="3d1f8-134">Her iki sütunun **ColumnMapping** özelliği **MappingType. element**olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="3d1f8-134">The **ColumnMapping** property of both columns will be set to **MappingType.Element**.</span></span>  
  
 <span data-ttu-id="3d1f8-135">**Veri kümesi** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="3d1f8-135">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="3d1f8-136">**Tablosundan** Element1</span><span class="sxs-lookup"><span data-stu-id="3d1f8-136">**Table:** Element1</span></span>  
  
|<span data-ttu-id="3d1f8-137">ChildElement1</span><span class="sxs-lookup"><span data-stu-id="3d1f8-137">ChildElement1</span></span>|<span data-ttu-id="3d1f8-138">ChildElement2</span><span class="sxs-lookup"><span data-stu-id="3d1f8-138">ChildElement2</span></span>|  
|-------------------|-------------------|  
|<span data-ttu-id="3d1f8-139">Text1</span><span class="sxs-lookup"><span data-stu-id="3d1f8-139">Text1</span></span>|<span data-ttu-id="3d1f8-140">Metin2</span><span class="sxs-lookup"><span data-stu-id="3d1f8-140">Text2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3d1f8-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3d1f8-141">See also</span></span>

- [<span data-ttu-id="3d1f8-142">XML’den DataSet İlişkisel Yapısını Çıkarma</span><span class="sxs-lookup"><span data-stu-id="3d1f8-142">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="3d1f8-143">XML’den DataSet Yükleme</span><span class="sxs-lookup"><span data-stu-id="3d1f8-143">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="3d1f8-144">XML’den DataSet Schema Bilgilerini Yükleme</span><span class="sxs-lookup"><span data-stu-id="3d1f8-144">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="3d1f8-145">DataSet içinde XML kullanma</span><span class="sxs-lookup"><span data-stu-id="3d1f8-145">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="3d1f8-146">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="3d1f8-146">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="3d1f8-147">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="3d1f8-147">ADO.NET Overview</span></span>](../ado-net-overview.md)
