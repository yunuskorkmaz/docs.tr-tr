---
description: 'Daha fazla bilgi edinin: sütunları erteleme'
title: Sütunların Çıkarımını Yapma
ms.date: 03/30/2017
ms.assetid: 0e022699-c922-454c-93e2-957dd7e7247a
ms.openlocfilehash: 528d4ea20260b5f1fbf30536eafcaec8c5f9215a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652256"
---
# <a name="inferring-columns"></a><span data-ttu-id="e9a76-103">Sütunların Çıkarımını Yapma</span><span class="sxs-lookup"><span data-stu-id="e9a76-103">Inferring Columns</span></span>

<span data-ttu-id="e9a76-104">ADO.NET, bir XML belgesinden bir için tablo olarak hangi öğelerin çıkarması gerektiğini belirledikten sonra <xref:System.Data.DataSet> , bu tablolar için sütunları algılar.</span><span class="sxs-lookup"><span data-stu-id="e9a76-104">After ADO.NET has determined from an XML document which elements to infer as tables for a <xref:System.Data.DataSet>, it then infers the columns for those tables.</span></span> <span data-ttu-id="e9a76-105">ADO.NET 2,0, her **simpleType** öğe için kesin olarak belirlenmiş bir veri türünü gösteren yeni bir şema çıkarımı altyapısı sunmuştur.</span><span class="sxs-lookup"><span data-stu-id="e9a76-105">ADO.NET 2.0 introduced a new schema inference engine that infers a strongly typed data type for each **simpleType** element.</span></span> <span data-ttu-id="e9a76-106">Önceki sürümlerde, gösterilen bir **simpleType** öğenin veri türü her zaman **xsd: String** idi.</span><span class="sxs-lookup"><span data-stu-id="e9a76-106">In previous versions, the data type of an inferred **simpleType** element was always **xsd:string**.</span></span>  
  
## <a name="migration-and-backward-compatibility"></a><span data-ttu-id="e9a76-107">Geçiş ve geri uyumluluk</span><span class="sxs-lookup"><span data-stu-id="e9a76-107">Migration and Backward Compatibility</span></span>  

 <span data-ttu-id="e9a76-108">**ReadXml** yöntemi **ınsetype** türünde bir bağımsız değişken alır.</span><span class="sxs-lookup"><span data-stu-id="e9a76-108">The **ReadXml** method takes an argument of type **InferSchema**.</span></span> <span data-ttu-id="e9a76-109">Bu bağımsız değişken, önceki sürümlerle uyumlu çıkarım davranışı belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="e9a76-109">This argument allows you to specify inference behavior compatible with previous versions.</span></span> <span data-ttu-id="e9a76-110">**Inseschema** numaralandırması için kullanılabilir değerler aşağıdaki tabloda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e9a76-110">The available values for the **InferSchema** enumeration are shown in the following table.</span></span>  
  
 <xref:System.Data.XmlReadMode.InferSchema>  
 <span data-ttu-id="e9a76-111">, Bir basit türü her zaman olarak değiştirerek geriye dönük uyumluluk sağlar <xref:System.String> .</span><span class="sxs-lookup"><span data-stu-id="e9a76-111">Provides backward compatibility by always inferring a simple type as <xref:System.String>.</span></span>  
  
 <xref:System.Data.XmlReadMode.InferTypedSchema>  
 <span data-ttu-id="e9a76-112">Kesin tür belirtilmiş bir veri türünü haller.</span><span class="sxs-lookup"><span data-stu-id="e9a76-112">Infers a strongly typed data type.</span></span> <span data-ttu-id="e9a76-113">İle kullanılırsa bir özel durum oluşturur <xref:System.Data.DataTable> .</span><span class="sxs-lookup"><span data-stu-id="e9a76-113">Throws an exception if used with a <xref:System.Data.DataTable>.</span></span>  
  
 <xref:System.Data.XmlReadMode.IgnoreSchema>  
 <span data-ttu-id="e9a76-114">Herhangi bir satır içi şemayı yoksayar ve verileri var olan <xref:System.Data.DataSet> şemaya okur.</span><span class="sxs-lookup"><span data-stu-id="e9a76-114">Ignores any inline schema and reads data into the existing <xref:System.Data.DataSet> schema.</span></span>  
  
## <a name="attributes"></a><span data-ttu-id="e9a76-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e9a76-115">Attributes</span></span>  

 <span data-ttu-id="e9a76-116">[Tablolarda](inferring-tables.md)tanımlandığı gibi, öznitelikleri olan bir öğesi tablo olarak çıkarsolur.</span><span class="sxs-lookup"><span data-stu-id="e9a76-116">As defined in [Inferring Tables](inferring-tables.md), an element with attributes will be inferred as a table.</span></span> <span data-ttu-id="e9a76-117">Daha sonra bu öğenin öznitelikleri tablo için sütun olarak algılanır.</span><span class="sxs-lookup"><span data-stu-id="e9a76-117">The attributes of that element will then be inferred as columns for the table.</span></span> <span data-ttu-id="e9a76-118">Şema XML 'e geri yazılmışsa sütun adlarının öznitelik olarak yazılmasını sağlamak için sütunların **ColumnMapping** özelliği **MappingType. Attribute** olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="e9a76-118">The **ColumnMapping** property of the columns will be set to **MappingType.Attribute**, to ensure that the column names will be written as attributes if the schema is written back to XML.</span></span> <span data-ttu-id="e9a76-119">Özniteliklerin değerleri tablodaki bir satırda depolanır.</span><span class="sxs-lookup"><span data-stu-id="e9a76-119">The values of the attributes are stored in a row in the table.</span></span> <span data-ttu-id="e9a76-120">Örneğin, aşağıdaki XML 'i göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="e9a76-120">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 <span data-ttu-id="e9a76-121">Çıkarım işlemi, **Element1** adında, **attr1** ve **attr2** olmak üzere iki sütunlu bir tablo oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e9a76-121">The inference process will produce a table named **Element1** with two columns, **attr1** and **attr2**.</span></span> <span data-ttu-id="e9a76-122">Her iki sütunun **ColumnMapping** özelliği **MappingType. Attribute** olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="e9a76-122">The **ColumnMapping** property of both columns will be set to **MappingType.Attribute**.</span></span>  
  
 <span data-ttu-id="e9a76-123">**Veri kümesi:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="e9a76-123">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="e9a76-124">**Tablo:** Element1</span><span class="sxs-lookup"><span data-stu-id="e9a76-124">**Table:** Element1</span></span>  
  
|<span data-ttu-id="e9a76-125">attr1</span><span class="sxs-lookup"><span data-stu-id="e9a76-125">attr1</span></span>|<span data-ttu-id="e9a76-126">attr2</span><span class="sxs-lookup"><span data-stu-id="e9a76-126">attr2</span></span>|  
|-----------|-----------|  
|<span data-ttu-id="e9a76-127">value1</span><span class="sxs-lookup"><span data-stu-id="e9a76-127">value1</span></span>|<span data-ttu-id="e9a76-128">value2</span><span class="sxs-lookup"><span data-stu-id="e9a76-128">value2</span></span>|  
  
## <a name="elements-without-attributes-or-child-elements"></a><span data-ttu-id="e9a76-129">Öznitelikleri veya alt öğeleri olmayan öğeler</span><span class="sxs-lookup"><span data-stu-id="e9a76-129">Elements Without Attributes or Child Elements</span></span>  

 <span data-ttu-id="e9a76-130">Bir öğenin alt öğesi veya özniteliği yoksa, sütun olarak algılanır.</span><span class="sxs-lookup"><span data-stu-id="e9a76-130">If an element has no child elements or attributes, it will be inferred as a column.</span></span> <span data-ttu-id="e9a76-131">Sütunun **ColumnMapping** özelliği **MappingType. element** olarak ayarlanacak.</span><span class="sxs-lookup"><span data-stu-id="e9a76-131">The **ColumnMapping** property of the column will be set to **MappingType.Element**.</span></span> <span data-ttu-id="e9a76-132">Alt öğeler için metin, tablodaki bir satırda saklanır.</span><span class="sxs-lookup"><span data-stu-id="e9a76-132">The text for child elements is stored in a row in the table.</span></span> <span data-ttu-id="e9a76-133">Örneğin, aşağıdaki XML 'i göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="e9a76-133">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="e9a76-134">Çıkarım işlemi, **Element1** adında, **ChildElement1** ve **ChildElement2** olmak üzere iki sütunlu bir tablo oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e9a76-134">The inference process will produce a table named **Element1** with two columns, **ChildElement1** and **ChildElement2**.</span></span> <span data-ttu-id="e9a76-135">Her iki sütunun **ColumnMapping** özelliği **MappingType. element** olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="e9a76-135">The **ColumnMapping** property of both columns will be set to **MappingType.Element**.</span></span>  
  
 <span data-ttu-id="e9a76-136">**Veri kümesi:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="e9a76-136">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="e9a76-137">**Tablo:** Element1</span><span class="sxs-lookup"><span data-stu-id="e9a76-137">**Table:** Element1</span></span>  
  
|<span data-ttu-id="e9a76-138">ChildElement1</span><span class="sxs-lookup"><span data-stu-id="e9a76-138">ChildElement1</span></span>|<span data-ttu-id="e9a76-139">ChildElement2</span><span class="sxs-lookup"><span data-stu-id="e9a76-139">ChildElement2</span></span>|  
|-------------------|-------------------|  
|<span data-ttu-id="e9a76-140">Text1</span><span class="sxs-lookup"><span data-stu-id="e9a76-140">Text1</span></span>|<span data-ttu-id="e9a76-141">Metin2</span><span class="sxs-lookup"><span data-stu-id="e9a76-141">Text2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e9a76-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e9a76-142">See also</span></span>

- [<span data-ttu-id="e9a76-143">XML’den DataSet İlişkisel Yapısını Çıkarma</span><span class="sxs-lookup"><span data-stu-id="e9a76-143">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="e9a76-144">XML’den DataSet Yükleme</span><span class="sxs-lookup"><span data-stu-id="e9a76-144">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="e9a76-145">XML’den DataSet Schema Bilgilerini Yükleme</span><span class="sxs-lookup"><span data-stu-id="e9a76-145">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="e9a76-146">DataSet içinde XML kullanma</span><span class="sxs-lookup"><span data-stu-id="e9a76-146">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="e9a76-147">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="e9a76-147">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="e9a76-148">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e9a76-148">ADO.NET Overview</span></span>](../ado-net-overview.md)
