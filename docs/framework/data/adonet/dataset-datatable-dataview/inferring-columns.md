---
title: Sütunların çıkarımını yapma
ms.date: 03/30/2017
ms.assetid: 0e022699-c922-454c-93e2-957dd7e7247a
ms.openlocfilehash: 56de4b4d6cf704473ec46957625ad1c376f595c2
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43891359"
---
# <a name="inferring-columns"></a><span data-ttu-id="f4df9-102">Sütunların çıkarımını yapma</span><span class="sxs-lookup"><span data-stu-id="f4df9-102">Inferring Columns</span></span>
<span data-ttu-id="f4df9-103">ADO.NET için tabloları olarak çıkarsamak için hangi öğelerin bir XML belgesinden belirledi sonra bir <xref:System.Data.DataSet>, ardından bu tablonun sütunlarını algılar.</span><span class="sxs-lookup"><span data-stu-id="f4df9-103">After ADO.NET has determined from an XML document which elements to infer as tables for a <xref:System.Data.DataSet>, it then infers the columns for those tables.</span></span> <span data-ttu-id="f4df9-104">ADO.NET 2.0 sunulan her biri için kesin türü belirtilmiş veri türünü çıkarsar yeni bir şema çıkarımı altyapısının **simpleType** öğesi.</span><span class="sxs-lookup"><span data-stu-id="f4df9-104">ADO.NET 2.0 introduced a new schema inference engine that infers a strongly typed data type for each **simpleType** element.</span></span> <span data-ttu-id="f4df9-105">Önceki sürümlerde, veri türü bir çıkarsanan **simpleType** öğe bulunamadı her zaman **xsd: String'e**.</span><span class="sxs-lookup"><span data-stu-id="f4df9-105">In previous versions, the data type of an inferred **simpleType** element was always **xsd:string**.</span></span>  
  
## <a name="migration-and-backward-compatibility"></a><span data-ttu-id="f4df9-106">Geçiş ve geriye dönük uyumluluk</span><span class="sxs-lookup"><span data-stu-id="f4df9-106">Migration and Backward Compatibility</span></span>  
 <span data-ttu-id="f4df9-107">**ReadXml** yöntemi türünde bir bağımsız değişken alır **InferSchema**.</span><span class="sxs-lookup"><span data-stu-id="f4df9-107">The **ReadXml** method takes an argument of type **InferSchema**.</span></span> <span data-ttu-id="f4df9-108">Bu bağımsız değişken kesmesi davranışını önceki sürümleriyle uyumlu belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="f4df9-108">This argument allows you to specify inference behavior compatible with previous versions.</span></span> <span data-ttu-id="f4df9-109">Kullanılabilir değerler için **InferSchema** numaralandırma aşağıdaki tabloda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f4df9-109">The available values for the **InferSchema** enumeration are shown in the following table.</span></span>  
  
 <xref:System.Data.XmlReadMode.InferSchema>  
 <span data-ttu-id="f4df9-110">Her zaman olarak basit bir tür çıkarımını yapma geriye dönük uyumluluk sağlar <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="f4df9-110">Provides backward compatibility by always inferring a simple type as <xref:System.String>.</span></span>  
  
 <xref:System.Data.XmlReadMode.InferTypedSchema>  
 <span data-ttu-id="f4df9-111">Kesin türü belirtilmiş veri türü çıkarır.</span><span class="sxs-lookup"><span data-stu-id="f4df9-111">Infers a strongly typed data type.</span></span> <span data-ttu-id="f4df9-112">Birlikte kullanılırsa bir özel durum oluşturur. bir <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="f4df9-112">Throws an exception if used with a <xref:System.Data.DataTable>.</span></span>  
  
 <xref:System.Data.XmlReadMode.IgnoreSchema>  
 <span data-ttu-id="f4df9-113">Herhangi bir satır içi şema yoksayar ve mevcut verileri okuyan <xref:System.Data.DataSet> şema.</span><span class="sxs-lookup"><span data-stu-id="f4df9-113">Ignores any inline schema and reads data into the existing <xref:System.Data.DataSet> schema.</span></span>  
  
## <a name="attributes"></a><span data-ttu-id="f4df9-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f4df9-114">Attributes</span></span>  
 <span data-ttu-id="f4df9-115">Sınıfında tanımlandığı gibi [tabloların çıkarımını yapma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-tables.md), özniteliklere sahip bir öğe bir tablo çıkarılan.</span><span class="sxs-lookup"><span data-stu-id="f4df9-115">As defined in [Inferring Tables](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-tables.md), an element with attributes will be inferred as a table.</span></span> <span data-ttu-id="f4df9-116">Bu öğenin öznitelikleri olarak tablonun sütunlarını ardından çıkarılan.</span><span class="sxs-lookup"><span data-stu-id="f4df9-116">The attributes of that element will then be inferred as columns for the table.</span></span> <span data-ttu-id="f4df9-117">**Columnmapping'in** sütunların özellik ayarlanacak **MappingType.Attribute**, XML şema geri yazılmışsa sütun adları öznitelik olarak yazılır emin olmak için.</span><span class="sxs-lookup"><span data-stu-id="f4df9-117">The **ColumnMapping** property of the columns will be set to **MappingType.Attribute**, to ensure that the column names will be written as attributes if the schema is written back to XML.</span></span> <span data-ttu-id="f4df9-118">Öznitelik değerleri, tabloda bir satır depolanır.</span><span class="sxs-lookup"><span data-stu-id="f4df9-118">The values of the attributes are stored in a row in the table.</span></span> <span data-ttu-id="f4df9-119">Örneğin, aşağıdaki XML göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="f4df9-119">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 <span data-ttu-id="f4df9-120">Çıkarma işlemi adlı bir tablo oluşturur **Element1** iki sütunlu **attr1** ve **attr2**.</span><span class="sxs-lookup"><span data-stu-id="f4df9-120">The inference process will produce a table named **Element1** with two columns, **attr1** and **attr2**.</span></span> <span data-ttu-id="f4df9-121">**Columnmapping'in** hem sütunların özellik ayarlanacak **MappingType.Attribute**.</span><span class="sxs-lookup"><span data-stu-id="f4df9-121">The **ColumnMapping** property of both columns will be set to **MappingType.Attribute**.</span></span>  
  
 <span data-ttu-id="f4df9-122">**Veri kümesi:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="f4df9-122">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="f4df9-123">**Tablo:** Element1</span><span class="sxs-lookup"><span data-stu-id="f4df9-123">**Table:** Element1</span></span>  
  
|<span data-ttu-id="f4df9-124">attr1</span><span class="sxs-lookup"><span data-stu-id="f4df9-124">attr1</span></span>|<span data-ttu-id="f4df9-125">attr2</span><span class="sxs-lookup"><span data-stu-id="f4df9-125">attr2</span></span>|  
|-----------|-----------|  
|<span data-ttu-id="f4df9-126">Değer1</span><span class="sxs-lookup"><span data-stu-id="f4df9-126">value1</span></span>|<span data-ttu-id="f4df9-127">Value2</span><span class="sxs-lookup"><span data-stu-id="f4df9-127">value2</span></span>|  
  
## <a name="elements-without-attributes-or-child-elements"></a><span data-ttu-id="f4df9-128">Öğeler olmadan öznitelikleri veya alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="f4df9-128">Elements Without Attributes or Child Elements</span></span>  
 <span data-ttu-id="f4df9-129">Hiçbir alt öğeler veya öznitelikleri bir öğe varsa, bir sütun olarak çıkarılan.</span><span class="sxs-lookup"><span data-stu-id="f4df9-129">If an element has no child elements or attributes, it will be inferred as a column.</span></span> <span data-ttu-id="f4df9-130">**Columnmapping'in** sütununun özellik ayarlanacak **MappingType.Element**.</span><span class="sxs-lookup"><span data-stu-id="f4df9-130">The **ColumnMapping** property of the column will be set to **MappingType.Element**.</span></span> <span data-ttu-id="f4df9-131">Alt öğelere metin tablosunda bir satıra depolanır.</span><span class="sxs-lookup"><span data-stu-id="f4df9-131">The text for child elements is stored in a row in the table.</span></span> <span data-ttu-id="f4df9-132">Örneğin, aşağıdaki XML göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="f4df9-132">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="f4df9-133">Çıkarma işlemi adlı bir tablo oluşturur **Element1** iki sütunlu **ChildElement1** ve **ChildElement2**.</span><span class="sxs-lookup"><span data-stu-id="f4df9-133">The inference process will produce a table named **Element1** with two columns, **ChildElement1** and **ChildElement2**.</span></span> <span data-ttu-id="f4df9-134">**Columnmapping'in** hem sütunların özellik ayarlanacak **MappingType.Element**.</span><span class="sxs-lookup"><span data-stu-id="f4df9-134">The **ColumnMapping** property of both columns will be set to **MappingType.Element**.</span></span>  
  
 <span data-ttu-id="f4df9-135">**Veri kümesi:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="f4df9-135">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="f4df9-136">**Tablo:** Element1</span><span class="sxs-lookup"><span data-stu-id="f4df9-136">**Table:** Element1</span></span>  
  
|<span data-ttu-id="f4df9-137">ChildElement1</span><span class="sxs-lookup"><span data-stu-id="f4df9-137">ChildElement1</span></span>|<span data-ttu-id="f4df9-138">ChildElement2</span><span class="sxs-lookup"><span data-stu-id="f4df9-138">ChildElement2</span></span>|  
|-------------------|-------------------|  
|<span data-ttu-id="f4df9-139">text1</span><span class="sxs-lookup"><span data-stu-id="f4df9-139">Text1</span></span>|<span data-ttu-id="f4df9-140">Text2</span><span class="sxs-lookup"><span data-stu-id="f4df9-140">Text2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f4df9-141">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f4df9-141">See Also</span></span>  
 [<span data-ttu-id="f4df9-142">XML’den DataSet İlişkisel Yapısını Çıkarma</span><span class="sxs-lookup"><span data-stu-id="f4df9-142">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [<span data-ttu-id="f4df9-143">XML’den DataSet Yükleme</span><span class="sxs-lookup"><span data-stu-id="f4df9-143">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [<span data-ttu-id="f4df9-144">XML’den DataSet Schema Bilgilerini Yükleme</span><span class="sxs-lookup"><span data-stu-id="f4df9-144">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [<span data-ttu-id="f4df9-145">DataSet içinde XML kullanma</span><span class="sxs-lookup"><span data-stu-id="f4df9-145">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [<span data-ttu-id="f4df9-146">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="f4df9-146">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="f4df9-147">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="f4df9-147">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
