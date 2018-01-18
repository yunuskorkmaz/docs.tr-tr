---
title: "XML verileri olarak DataSet içeriğini yazma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: fd15f8a5-3b4c-46d0-a561-4559ab2a4705
caps.latest.revision: "5"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 9b1250d616ad5835fccd1a3acbf0b8a759c34181
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="writing-dataset-contents-as-xml-data"></a><span data-ttu-id="b33cf-102">XML verileri olarak DataSet içeriğini yazma</span><span class="sxs-lookup"><span data-stu-id="b33cf-102">Writing DataSet Contents as XML Data</span></span>
<span data-ttu-id="b33cf-103">ADO.NET bir XML temsili yazabilen bir <xref:System.Data.DataSet>, ile veya olmadan şemasına.</span><span class="sxs-lookup"><span data-stu-id="b33cf-103">In ADO.NET you can write an XML representation of a <xref:System.Data.DataSet>, with or without its schema.</span></span> <span data-ttu-id="b33cf-104">Şema bilgileri XML ile birlikte satır içi ise XML Şeması Tanım Dili (XSD) kullanılarak yazılır.</span><span class="sxs-lookup"><span data-stu-id="b33cf-104">If schema information is included inline with the XML, it is written using the XML Schema definition language (XSD).</span></span> <span data-ttu-id="b33cf-105">Tablo tanımları bir şema içeriyor <xref:System.Data.DataSet> ilişki ve kısıtlama tanımları yanı sıra.</span><span class="sxs-lookup"><span data-stu-id="b33cf-105">The schema contains the table definitions of the <xref:System.Data.DataSet> as well as the relation and constraint definitions.</span></span>  
  
 <span data-ttu-id="b33cf-106">Zaman bir <xref:System.Data.DataSet> XML verileri, satırları olarak yazılmış <xref:System.Data.DataSet> geçerli sürümlerine yazılır.</span><span class="sxs-lookup"><span data-stu-id="b33cf-106">When a <xref:System.Data.DataSet> is written as XML data, the rows in the <xref:System.Data.DataSet> are written in their current versions.</span></span> <span data-ttu-id="b33cf-107">Ancak, <xref:System.Data.DataSet> böylece geçerli ve özgün değerleri satır eklenecek DiffGram da yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="b33cf-107">However, the <xref:System.Data.DataSet> can also be written as a DiffGram so that both the current and the original values of the rows will be included.</span></span>  
  
 <span data-ttu-id="b33cf-108">XML gösterimini <xref:System.Data.DataSet> bir dosyaya, bir akış yazılabilir bir **XmlWriter**, veya bir dize.</span><span class="sxs-lookup"><span data-stu-id="b33cf-108">The XML representation of the <xref:System.Data.DataSet> can be written to a file, a stream, an **XmlWriter**, or a string.</span></span> <span data-ttu-id="b33cf-109">Bu seçenekler XML gösterimini nasıl taşıma için büyük esneklik sağlar <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="b33cf-109">These choices provide great flexibility for how you transport the XML representation of the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="b33cf-110">XML gösterimini almak için <xref:System.Data.DataSet> bir dize kullanmak **GetXml** aşağıdaki örnekte gösterildiği gibi yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b33cf-110">To obtain the XML representation of the <xref:System.Data.DataSet> as a string, use the **GetXml** method as shown in the following example.</span></span>  
  
```vb  
Dim xmlDS As String = custDS.GetXml()  
```  
  
```csharp  
string xmlDS = custDS.GetXml();  
```  
  
 <span data-ttu-id="b33cf-111">**GetXml** XML gösterimini döndürür <xref:System.Data.DataSet> şema bilgileri olmadan.</span><span class="sxs-lookup"><span data-stu-id="b33cf-111">**GetXml** returns the XML representation of the <xref:System.Data.DataSet> without schema information.</span></span> <span data-ttu-id="b33cf-112">Şema bilgileri yazmak için <xref:System.Data.DataSet> (olarak XML Şeması) bir dizeye kullanmak **GetXmlSchema**.</span><span class="sxs-lookup"><span data-stu-id="b33cf-112">To write the schema information from the <xref:System.Data.DataSet> (as XML Schema) to a string, use **GetXmlSchema**.</span></span>  
  
 <span data-ttu-id="b33cf-113">Yazmak için bir <xref:System.Data.DataSet> bir dosyaya akışı veya **XmlWriter**, kullanın **WriteXml** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b33cf-113">To write a <xref:System.Data.DataSet> to a file, stream, or **XmlWriter**, use the **WriteXml** method.</span></span> <span data-ttu-id="b33cf-114">Geçirdiğiniz için ilk parametre **WriteXml** XML çıktı hedefi.</span><span class="sxs-lookup"><span data-stu-id="b33cf-114">The first parameter you pass to **WriteXml** is the destination of the XML output.</span></span> <span data-ttu-id="b33cf-115">Örneğin, bir dosya adı içeren bir dizeyi geçirmek bir **System.IO.TextWriter** nesne ve benzeri.</span><span class="sxs-lookup"><span data-stu-id="b33cf-115">For example, pass a string containing a file name, a **System.IO.TextWriter** object, and so on.</span></span> <span data-ttu-id="b33cf-116">Bir isteğe bağlı ikinci parametresi, geçirdiğiniz bir **XmlWriteMode** nasıl yazılacak XML çıktısı olduğunu belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="b33cf-116">You can pass an optional second parameter of an **XmlWriteMode** to specify how the XML output is to be written.</span></span>  
  
 <span data-ttu-id="b33cf-117">Aşağıdaki tabloda seçeneklerini gösterir **XmlWriteMode**.</span><span class="sxs-lookup"><span data-stu-id="b33cf-117">The following table shows the options for **XmlWriteMode**.</span></span>  
  
|<span data-ttu-id="b33cf-118">XmlWriteMode option</span><span class="sxs-lookup"><span data-stu-id="b33cf-118">XmlWriteMode option</span></span>|<span data-ttu-id="b33cf-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b33cf-119">Description</span></span>|  
|-------------------------|-----------------|  
|<span data-ttu-id="b33cf-120">**IgnoreSchema**</span><span class="sxs-lookup"><span data-stu-id="b33cf-120">**IgnoreSchema**</span></span>|<span data-ttu-id="b33cf-121">Geçerli içeriğini Yazar <xref:System.Data.DataSet> bir XML Şeması olmadan XML verileri olarak.</span><span class="sxs-lookup"><span data-stu-id="b33cf-121">Writes the current contents of the <xref:System.Data.DataSet> as XML data, without an XML Schema.</span></span> <span data-ttu-id="b33cf-122">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="b33cf-122">This is the default.</span></span>|  
|<span data-ttu-id="b33cf-123">**WriteSchema**</span><span class="sxs-lookup"><span data-stu-id="b33cf-123">**WriteSchema**</span></span>|<span data-ttu-id="b33cf-124">Geçerli içeriğini Yazar <xref:System.Data.DataSet> XML Şeması satır içi olarak ilişkisel yapısı ile XML verileri olarak.</span><span class="sxs-lookup"><span data-stu-id="b33cf-124">Writes the current contents of the <xref:System.Data.DataSet> as XML data with the relational structure as inline XML Schema.</span></span>|  
|<span data-ttu-id="b33cf-125">**DiffGram**</span><span class="sxs-lookup"><span data-stu-id="b33cf-125">**DiffGram**</span></span>|<span data-ttu-id="b33cf-126">Tüm Yazar <xref:System.Data.DataSet> bir DiffGram özgün geçerli değerler dahil olmak üzere.</span><span class="sxs-lookup"><span data-stu-id="b33cf-126">Writes the entire <xref:System.Data.DataSet> as a DiffGram, including original and current values.</span></span> <span data-ttu-id="b33cf-127">Daha fazla bilgi için bkz: [DiffGrams](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md).</span><span class="sxs-lookup"><span data-stu-id="b33cf-127">For more information, see [DiffGrams](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md).</span></span>|  
  
 <span data-ttu-id="b33cf-128">Bir XML temsili yazılırken bir <xref:System.Data.DataSet> içeren **DataRelation** nesneleri büyük olasılıkla istediğiniz kendi ilgili üst öğeler içinde iç içe geçmiş her ilişkinin alt satır olması için sonuç XML.</span><span class="sxs-lookup"><span data-stu-id="b33cf-128">When writing an XML representation of a <xref:System.Data.DataSet> that contains **DataRelation** objects, you will most likely want the resulting XML to have the child rows of each relation nested within their related parent elements.</span></span> <span data-ttu-id="b33cf-129">Bunu gerçekleştirmek için ayarlanmış **iç içe** özelliği **DataRelation** için **true** eklediğinizde **DataRelation** için<xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="b33cf-129">To accomplish this, set the **Nested** property of the **DataRelation** to **true** when you add the **DataRelation** to the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="b33cf-130">Daha fazla bilgi için bkz: [iç içe geçme DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md).</span><span class="sxs-lookup"><span data-stu-id="b33cf-130">For more information, see [Nesting DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md).</span></span>  
  
 <span data-ttu-id="b33cf-131">XML gösterimini yazmak iki örnekleri verilmiştir bir <xref:System.Data.DataSet> bir dosyaya.</span><span class="sxs-lookup"><span data-stu-id="b33cf-131">Following are two examples of how to write the XML representation of a <xref:System.Data.DataSet> to a file.</span></span> <span data-ttu-id="b33cf-132">İlk örnek için sonuç XML dosya adı bir dize olarak geçirir. **WriteXml**.</span><span class="sxs-lookup"><span data-stu-id="b33cf-132">The first example passes the file name for the resulting XML as a string to **WriteXml**.</span></span> <span data-ttu-id="b33cf-133">İkinci örnek geçirmeden bir **System.IO.StreamWriter** nesnesi.</span><span class="sxs-lookup"><span data-stu-id="b33cf-133">The second example passes a **System.IO.StreamWriter** object.</span></span>  
  
```vb  
custDS.WriteXml("Customers.xml", XmlWriteMode.WriteSchema)  
```  
  
```csharp  
custDS.WriteXml("Customers.xml", XmlWriteMode.WriteSchema);  
```  
  
```vb  
Dim xmlSW As System.IO.StreamWriter = New System.IO.StreamWriter("Customers.xml")  
custDS.WriteXml(xmlSW, XmlWriteMode.WriteSchema)  
xmlSW.Close()  
```  
  
```csharp  
System.IO.StreamWriter xmlSW = new System.IO.StreamWriter("Customers.xml");  
custDS.WriteXml(xmlSW, XmlWriteMode.WriteSchema);  
xmlSW.Close();  
```  
  
## <a name="mapping-columns-to-xml-elements-attributes-and-text"></a><span data-ttu-id="b33cf-134">XML öğeleri, öznitelikleri ve metin sütunları eşleme</span><span class="sxs-lookup"><span data-stu-id="b33cf-134">Mapping Columns to XML Elements, Attributes, and Text</span></span>  
 <span data-ttu-id="b33cf-135">Bir tablo sütunu XML'de nasıl temsil belirtebilirsiniz kullanarak **ColumnMapping** özelliği **DataColumn** nesnesi.</span><span class="sxs-lookup"><span data-stu-id="b33cf-135">You can specify how a column of a table is represented in XML using the **ColumnMapping** property of the **DataColumn** object.</span></span> <span data-ttu-id="b33cf-136">Aşağıdaki tabloda farklı gösterilmektedir **MappingType** değerleri **ColumnMapping** bir tablo sütunu ve sonuçta elde edilen XML özelliği.</span><span class="sxs-lookup"><span data-stu-id="b33cf-136">The following table shows the different **MappingType** values for the **ColumnMapping** property of a table column, and the resulting XML.</span></span>  
  
|<span data-ttu-id="b33cf-137">MappingType değeri</span><span class="sxs-lookup"><span data-stu-id="b33cf-137">MappingType value</span></span>|<span data-ttu-id="b33cf-138">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b33cf-138">Description</span></span>|  
|-----------------------|-----------------|  
|<span data-ttu-id="b33cf-139">**Öğesi**</span><span class="sxs-lookup"><span data-stu-id="b33cf-139">**Element**</span></span>|<span data-ttu-id="b33cf-140">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="b33cf-140">This is the default.</span></span> <span data-ttu-id="b33cf-141">Sütun, burada ColumnName öğenin adını ve sütun içeriğini öğesinin metin olarak yazılan bir XML öğesi olarak yazılır.</span><span class="sxs-lookup"><span data-stu-id="b33cf-141">The column is written as an XML element where the ColumnName is the name of the element and the contents of the column are written as the text of the element.</span></span> <span data-ttu-id="b33cf-142">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="b33cf-142">For example:</span></span><br /><br /> `<ColumnName>Column Contents</ColumnName>`|  
|<span data-ttu-id="b33cf-143">**Özniteliği**</span><span class="sxs-lookup"><span data-stu-id="b33cf-143">**Attribute**</span></span>|<span data-ttu-id="b33cf-144">Sütun XML öğesi burada ColumnName özniteliğin adını ve sütun içeriğini öznitelik değeri olarak yazılan geçerli satır için XML özniteliği olarak yazılır.</span><span class="sxs-lookup"><span data-stu-id="b33cf-144">The column is written as an XML attribute of the XML element for the current row where the ColumnName is the name of the attribute and the contents of the column are written as the value of the attribute.</span></span> <span data-ttu-id="b33cf-145">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="b33cf-145">For example:</span></span><br /><br /> `<RowElement ColumnName="Column Contents" />`|  
|<span data-ttu-id="b33cf-146">**SimpleContent**</span><span class="sxs-lookup"><span data-stu-id="b33cf-146">**SimpleContent**</span></span>|<span data-ttu-id="b33cf-147">Sütunun içeriğine metin XML öğesi geçerli satır için olarak yazılır.</span><span class="sxs-lookup"><span data-stu-id="b33cf-147">The contents of the column are written as text in the XML element for the current row.</span></span> <span data-ttu-id="b33cf-148">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="b33cf-148">For example:</span></span><br /><br /> `<RowElement>Column Contents</RowElement>`<br /><br /> <span data-ttu-id="b33cf-149">Unutmayın **SimpleContent** sahip bir tablo için bir sütun ayarlanamaz **öğesi** sütunları veya iç içe ilişkiler.</span><span class="sxs-lookup"><span data-stu-id="b33cf-149">Note that **SimpleContent** cannot be set for a column of a table that has **Element** columns or nested relations.</span></span>|  
|<span data-ttu-id="b33cf-150">**Hidden**</span><span class="sxs-lookup"><span data-stu-id="b33cf-150">**Hidden**</span></span>|<span data-ttu-id="b33cf-151">Sütun XML çıktısında yazılmaz.</span><span class="sxs-lookup"><span data-stu-id="b33cf-151">The column is not written in the XML output.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b33cf-152">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b33cf-152">See Also</span></span>  
 [<span data-ttu-id="b33cf-153">DataSet içinde XML kullanma</span><span class="sxs-lookup"><span data-stu-id="b33cf-153">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [<span data-ttu-id="b33cf-154">DiffGrams</span><span class="sxs-lookup"><span data-stu-id="b33cf-154">DiffGrams</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md)  
 [<span data-ttu-id="b33cf-155">DataRelations’ı İç İçe Yerleştirme</span><span class="sxs-lookup"><span data-stu-id="b33cf-155">Nesting DataRelations</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)  
 [<span data-ttu-id="b33cf-156">XSD Olarak DataSet Schema Bilgilerini Yazma</span><span class="sxs-lookup"><span data-stu-id="b33cf-156">Writing DataSet Schema Information as XSD</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-schema-information-as-xsd.md)  
 [<span data-ttu-id="b33cf-157">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="b33cf-157">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="b33cf-158">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="b33cf-158">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
