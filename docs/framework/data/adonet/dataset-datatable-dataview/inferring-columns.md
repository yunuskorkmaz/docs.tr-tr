---
title: "Sütunları çıkarımını yapma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e022699-c922-454c-93e2-957dd7e7247a
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 858a23fb8fec7b7f2eee95a1365d16e846beb548
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="inferring-columns"></a><span data-ttu-id="3f58e-102">Sütunları çıkarımını yapma</span><span class="sxs-lookup"><span data-stu-id="3f58e-102">Inferring Columns</span></span>
<span data-ttu-id="3f58e-103">ADO.NET için tabloları olarak Infer hangi öğelerin bir XML belgesinden belirledi sonra bir <xref:System.Data.DataSet>, ardından bu tablo sütunlarını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3f58e-103">After ADO.NET has determined from an XML document which elements to infer as tables for a <xref:System.Data.DataSet>, it then infers the columns for those tables.</span></span> <span data-ttu-id="3f58e-104">ADO.NET 2.0 sunulan her biri için kesin türü belirtilmiş veri türü oluşturur Yeni bir şema çıkarımı altyapısının **simpleType** öğesi.</span><span class="sxs-lookup"><span data-stu-id="3f58e-104">ADO.NET 2.0 introduced a new schema inference engine that infers a strongly typed data type for each **simpleType** element.</span></span> <span data-ttu-id="3f58e-105">Önceki sürümlerde, veri türü bir oluşturulursa **simpleType** öğesi olan her zaman **xsd:string**.</span><span class="sxs-lookup"><span data-stu-id="3f58e-105">In previous versions, the data type of an inferred **simpleType** element was always **xsd:string**.</span></span>  
  
## <a name="migration-and-backward-compatibility"></a><span data-ttu-id="3f58e-106">Geçiş ve geriye dönük uyumluluk</span><span class="sxs-lookup"><span data-stu-id="3f58e-106">Migration and Backward Compatibility</span></span>  
 <span data-ttu-id="3f58e-107">**ReadXml** yöntemi alır türünde bir bağımsız değişken **InferSchema**.</span><span class="sxs-lookup"><span data-stu-id="3f58e-107">The **ReadXml** method takes an argument of type **InferSchema**.</span></span> <span data-ttu-id="3f58e-108">Bu bağımsız değişken çıkarım davranış önceki sürümleriyle uyumlu belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="3f58e-108">This argument allows you to specify inference behavior compatible with previous versions.</span></span> <span data-ttu-id="3f58e-109">Kullanılabilir değerler için **InferSchema** numaralandırma aşağıdaki tabloda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="3f58e-109">The available values for the **InferSchema** enumeration are shown in the following table.</span></span>  
  
 <xref:System.Data.XmlReadMode.InferSchema>  
 <span data-ttu-id="3f58e-110">Her zaman bir basit tür olarak çıkarımını yapma geriye dönük uyumluluk sağlar <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="3f58e-110">Provides backward compatibility by always inferring a simple type as <xref:System.String>.</span></span>  
  
 <xref:System.Data.XmlReadMode.InferTypedSchema>  
 <span data-ttu-id="3f58e-111">Kesin türü belirtilmiş veri türü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3f58e-111">Infers a strongly typed data type.</span></span> <span data-ttu-id="3f58e-112">Bir özel durum ile kullanılan döndürürse bir <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="3f58e-112">Throws an exception if used with a <xref:System.Data.DataTable>.</span></span>  
  
 <xref:System.Data.XmlReadMode.IgnoreSchema>  
 <span data-ttu-id="3f58e-113">Herhangi bir satır içi şema yoksayar ve mevcut verileri okur <xref:System.Data.DataSet> şema.</span><span class="sxs-lookup"><span data-stu-id="3f58e-113">Ignores any inline schema and reads data into the existing <xref:System.Data.DataSet> schema.</span></span>  
  
## <a name="attributes"></a><span data-ttu-id="3f58e-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3f58e-114">Attributes</span></span>  
 <span data-ttu-id="3f58e-115">' Da tanımlandığı gibi [çıkarımını yapma tabloları](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-tables.md), öğenin özniteliklere sahip bir tablo olarak çıkarımı yapılan.</span><span class="sxs-lookup"><span data-stu-id="3f58e-115">As defined in [Inferring Tables](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-tables.md), an element with attributes will be inferred as a table.</span></span> <span data-ttu-id="3f58e-116">Bu öğenin öznitelikleri tablosu için sütun olarak sonra olayla.</span><span class="sxs-lookup"><span data-stu-id="3f58e-116">The attributes of that element will then be inferred as columns for the table.</span></span> <span data-ttu-id="3f58e-117">**ColumnMapping** sütunların özellik ayarlanacak **MappingType.Attribute**, şemanın XML geri yazılmışsa sütun adları olarak öznitelikleri yazılmış emin olun.</span><span class="sxs-lookup"><span data-stu-id="3f58e-117">The **ColumnMapping** property of the columns will be set to **MappingType.Attribute**, to ensure that the column names will be written as attributes if the schema is written back to XML.</span></span> <span data-ttu-id="3f58e-118">Özniteliklerin değerleri tablosunda bir satırı depolanır.</span><span class="sxs-lookup"><span data-stu-id="3f58e-118">The values of the attributes are stored in a row in the table.</span></span> <span data-ttu-id="3f58e-119">Örneğin, aşağıdaki XML göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="3f58e-119">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 <span data-ttu-id="3f58e-120">Çıkarma işlemi adlı bir tablo oluşturur **Element1** iki sütunlarla **attr1** ve **attr2**.</span><span class="sxs-lookup"><span data-stu-id="3f58e-120">The inference process will produce a table named **Element1** with two columns, **attr1** and **attr2**.</span></span> <span data-ttu-id="3f58e-121">**ColumnMapping** hem sütunların özellik ayarlanacak **MappingType.Attribute**.</span><span class="sxs-lookup"><span data-stu-id="3f58e-121">The **ColumnMapping** property of both columns will be set to **MappingType.Attribute**.</span></span>  
  
 <span data-ttu-id="3f58e-122">**Veri kümesi:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="3f58e-122">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="3f58e-123">**Tablo:** Element1</span><span class="sxs-lookup"><span data-stu-id="3f58e-123">**Table:** Element1</span></span>  
  
|<span data-ttu-id="3f58e-124">attr1</span><span class="sxs-lookup"><span data-stu-id="3f58e-124">attr1</span></span>|<span data-ttu-id="3f58e-125">attr2</span><span class="sxs-lookup"><span data-stu-id="3f58e-125">attr2</span></span>|  
|-----------|-----------|  
|<span data-ttu-id="3f58e-126">Değer1</span><span class="sxs-lookup"><span data-stu-id="3f58e-126">value1</span></span>|<span data-ttu-id="3f58e-127">Value2</span><span class="sxs-lookup"><span data-stu-id="3f58e-127">value2</span></span>|  
  
## <a name="elements-without-attributes-or-child-elements"></a><span data-ttu-id="3f58e-128">Öznitelik veya alt öğe olmadan öğeleri</span><span class="sxs-lookup"><span data-stu-id="3f58e-128">Elements Without Attributes or Child Elements</span></span>  
 <span data-ttu-id="3f58e-129">Bir öğenin hiçbir alt öğe veya öznitelik varsa, bir sütun olarak olayla.</span><span class="sxs-lookup"><span data-stu-id="3f58e-129">If an element has no child elements or attributes, it will be inferred as a column.</span></span> <span data-ttu-id="3f58e-130">**ColumnMapping** sütunun özelliği ayarlanacak **MappingType.Element**.</span><span class="sxs-lookup"><span data-stu-id="3f58e-130">The **ColumnMapping** property of the column will be set to **MappingType.Element**.</span></span> <span data-ttu-id="3f58e-131">Alt öğeler için metin tablosunda bir satırı depolanır.</span><span class="sxs-lookup"><span data-stu-id="3f58e-131">The text for child elements is stored in a row in the table.</span></span> <span data-ttu-id="3f58e-132">Örneğin, aşağıdaki XML göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="3f58e-132">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="3f58e-133">Çıkarma işlemi adlı bir tablo oluşturur **Element1** iki sütunlarla **ChildElement1** ve **ChildElement2**.</span><span class="sxs-lookup"><span data-stu-id="3f58e-133">The inference process will produce a table named **Element1** with two columns, **ChildElement1** and **ChildElement2**.</span></span> <span data-ttu-id="3f58e-134">**ColumnMapping** hem sütunların özellik ayarlanacak **MappingType.Element**.</span><span class="sxs-lookup"><span data-stu-id="3f58e-134">The **ColumnMapping** property of both columns will be set to **MappingType.Element**.</span></span>  
  
 <span data-ttu-id="3f58e-135">**Veri kümesi:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="3f58e-135">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="3f58e-136">**Tablo:** Element1</span><span class="sxs-lookup"><span data-stu-id="3f58e-136">**Table:** Element1</span></span>  
  
|<span data-ttu-id="3f58e-137">ChildElement1</span><span class="sxs-lookup"><span data-stu-id="3f58e-137">ChildElement1</span></span>|<span data-ttu-id="3f58e-138">ChildElement2</span><span class="sxs-lookup"><span data-stu-id="3f58e-138">ChildElement2</span></span>|  
|-------------------|-------------------|  
|<span data-ttu-id="3f58e-139">Text1</span><span class="sxs-lookup"><span data-stu-id="3f58e-139">Text1</span></span>|<span data-ttu-id="3f58e-140">Metin2</span><span class="sxs-lookup"><span data-stu-id="3f58e-140">Text2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3f58e-141">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3f58e-141">See Also</span></span>  
 [<span data-ttu-id="3f58e-142">XML’den DataSet İlişkisel Yapısını Çıkarma</span><span class="sxs-lookup"><span data-stu-id="3f58e-142">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [<span data-ttu-id="3f58e-143">XML’den DataSet Yükleme</span><span class="sxs-lookup"><span data-stu-id="3f58e-143">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [<span data-ttu-id="3f58e-144">XML’den DataSet Schema Bilgilerini Yükleme</span><span class="sxs-lookup"><span data-stu-id="3f58e-144">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [<span data-ttu-id="3f58e-145">DataSet içinde XML kullanma</span><span class="sxs-lookup"><span data-stu-id="3f58e-145">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [<span data-ttu-id="3f58e-146">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="3f58e-146">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="3f58e-147">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="3f58e-147">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
