---
description: 'Hakkında daha fazla bilgi edinin: veri kümesi Içeriğini XML verileri olarak yazma'
title: XML Verileri Olarak DataSet İçeriği Yazma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fd15f8a5-3b4c-46d0-a561-4559ab2a4705
ms.openlocfilehash: 0ad232f744f69f822d09c0af6c4374b6e5f0147d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99651372"
---
# <a name="writing-dataset-contents-as-xml-data"></a><span data-ttu-id="1580d-103">XML Verileri Olarak DataSet İçeriği Yazma</span><span class="sxs-lookup"><span data-stu-id="1580d-103">Writing DataSet Contents as XML Data</span></span>

<span data-ttu-id="1580d-104">ADO.NET içinde <xref:System.Data.DataSet> , şemasına sahip veya olmadan BIR XML temsili yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1580d-104">In ADO.NET you can write an XML representation of a <xref:System.Data.DataSet>, with or without its schema.</span></span> <span data-ttu-id="1580d-105">Şema bilgileri XML ile satır içi içeriyorsa, XML şeması tanım dili (XSD) kullanılarak yazılır.</span><span class="sxs-lookup"><span data-stu-id="1580d-105">If schema information is included inline with the XML, it is written using the XML Schema definition language (XSD).</span></span> <span data-ttu-id="1580d-106">Şema, <xref:System.Data.DataSet> ilişki ve kısıtlama tanımlarının tablo tanımlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="1580d-106">The schema contains the table definitions of the <xref:System.Data.DataSet> as well as the relation and constraint definitions.</span></span>  
  
 <span data-ttu-id="1580d-107">Bir, <xref:System.Data.DataSet> XML verileri olarak yazıldığında, içindeki satırlar <xref:System.Data.DataSet> geçerli sürümlerinde yazılır.</span><span class="sxs-lookup"><span data-stu-id="1580d-107">When a <xref:System.Data.DataSet> is written as XML data, the rows in the <xref:System.Data.DataSet> are written in their current versions.</span></span> <span data-ttu-id="1580d-108">Ancak, <xref:System.Data.DataSet> hem geçerli hem de satırların orijinal değerlerinin dahil edilmesini sağlamak için de bir DiffGram olarak yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="1580d-108">However, the <xref:System.Data.DataSet> can also be written as a DiffGram so that both the current and the original values of the rows will be included.</span></span>  
  
 <span data-ttu-id="1580d-109">Öğesinin XML temsili <xref:System.Data.DataSet> bir dosyaya, akışa, bir **XmlWriter**'a veya bir dizeye yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="1580d-109">The XML representation of the <xref:System.Data.DataSet> can be written to a file, a stream, an **XmlWriter**, or a string.</span></span> <span data-ttu-id="1580d-110">Bu seçimler, öğesinin XML gösterimini taşımanın harika bir esnekliğini sağlar <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="1580d-110">These choices provide great flexibility for how you transport the XML representation of the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="1580d-111">Öğesinin XML temsilini <xref:System.Data.DataSet> bir dize olarak almak için aşağıdaki örnekte gösterildiği gibi **GetXml** metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="1580d-111">To obtain the XML representation of the <xref:System.Data.DataSet> as a string, use the **GetXml** method as shown in the following example.</span></span>  
  
```vb  
Dim xmlDS As String = custDS.GetXml()  
```  
  
```csharp  
string xmlDS = custDS.GetXml();  
```  
  
 <span data-ttu-id="1580d-112">**GetXml** şema BILGILERININ olmayan XML gösterimini döndürür <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="1580d-112">**GetXml** returns the XML representation of the <xref:System.Data.DataSet> without schema information.</span></span> <span data-ttu-id="1580d-113">Şema bilgilerini <xref:System.Data.DataSet> (XML şeması olarak) bir dizeye yazmak Için **GetXmlSchema** kullanın.</span><span class="sxs-lookup"><span data-stu-id="1580d-113">To write the schema information from the <xref:System.Data.DataSet> (as XML Schema) to a string, use **GetXmlSchema**.</span></span>  
  
 <span data-ttu-id="1580d-114">Bir <xref:System.Data.DataSet> dosyaya, akışa veya **XmlWriter**'A yazmak için **WriteXml** yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="1580d-114">To write a <xref:System.Data.DataSet> to a file, stream, or **XmlWriter**, use the **WriteXml** method.</span></span> <span data-ttu-id="1580d-115">**WriteXml** öğesine geçirdiğiniz ilk parametre, XML çıkışının hedefdir.</span><span class="sxs-lookup"><span data-stu-id="1580d-115">The first parameter you pass to **WriteXml** is the destination of the XML output.</span></span> <span data-ttu-id="1580d-116">Örneğin, bir dosya adı, bir **System. IO. TextWriter** nesnesi vb. içeren bir dize geçirin.</span><span class="sxs-lookup"><span data-stu-id="1580d-116">For example, pass a string containing a file name, a **System.IO.TextWriter** object, and so on.</span></span> <span data-ttu-id="1580d-117">XML çıkışının nasıl yazılacağını belirtmek için bir **XmlWriteMode** isteğe bağlı ikinci parametresini geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1580d-117">You can pass an optional second parameter of an **XmlWriteMode** to specify how the XML output is to be written.</span></span>  
  
 <span data-ttu-id="1580d-118">Aşağıdaki tabloda **XmlWriteMode** seçenekleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1580d-118">The following table shows the options for **XmlWriteMode**.</span></span>  
  
|<span data-ttu-id="1580d-119">XmlWriteMode seçeneği</span><span class="sxs-lookup"><span data-stu-id="1580d-119">XmlWriteMode option</span></span>|<span data-ttu-id="1580d-120">Description</span><span class="sxs-lookup"><span data-stu-id="1580d-120">Description</span></span>|  
|-------------------------|-----------------|  
|<span data-ttu-id="1580d-121">**IgnoreSchema**</span><span class="sxs-lookup"><span data-stu-id="1580d-121">**IgnoreSchema**</span></span>|<span data-ttu-id="1580d-122">XML <xref:System.Data.DataSet> şeması olmadan, XML verilerinin geçerli içeriğini yazar.</span><span class="sxs-lookup"><span data-stu-id="1580d-122">Writes the current contents of the <xref:System.Data.DataSet> as XML data, without an XML Schema.</span></span> <span data-ttu-id="1580d-123">Bu varsayılan seçenektir.</span><span class="sxs-lookup"><span data-stu-id="1580d-123">This is the default.</span></span>|  
|<span data-ttu-id="1580d-124">**WriteSchema seçeneğine ayarlayın**</span><span class="sxs-lookup"><span data-stu-id="1580d-124">**WriteSchema**</span></span>|<span data-ttu-id="1580d-125"><xref:System.Data.DataSet>XML verilerinin güncel içeriğini ilişkisel yapıda satır ıçı XML şeması olarak yazar.</span><span class="sxs-lookup"><span data-stu-id="1580d-125">Writes the current contents of the <xref:System.Data.DataSet> as XML data with the relational structure as inline XML Schema.</span></span>|  
|<span data-ttu-id="1580d-126">**Içeriyor**</span><span class="sxs-lookup"><span data-stu-id="1580d-126">**DiffGram**</span></span>|<span data-ttu-id="1580d-127"><xref:System.Data.DataSet>Özgün ve geçerli değerler dahil olmak üzere bir DiffGram olarak tümünü yazar.</span><span class="sxs-lookup"><span data-stu-id="1580d-127">Writes the entire <xref:System.Data.DataSet> as a DiffGram, including original and current values.</span></span> <span data-ttu-id="1580d-128">Daha fazla bilgi için bkz. [DiffGram](diffgrams.md).</span><span class="sxs-lookup"><span data-stu-id="1580d-128">For more information, see [DiffGrams](diffgrams.md).</span></span>|  
  
 <span data-ttu-id="1580d-129">DataRelation nesneleri içeren bir XML temsili yazarken <xref:System.Data.DataSet> , sonuçta  elde edilen XML 'nin ilgili üst öğeleri içinde iç içe geçmiş her ilişkinin alt satırlarına sahip olmasını istersiniz.</span><span class="sxs-lookup"><span data-stu-id="1580d-129">When writing an XML representation of a <xref:System.Data.DataSet> that contains **DataRelation** objects, you will most likely want the resulting XML to have the child rows of each relation nested within their related parent elements.</span></span> <span data-ttu-id="1580d-130">Bunu gerçekleştirmek için, **DataRelation** 'ı öğesine eklediğinizde **DataRelation** 'ın **Nested** özelliğini **true** olarak ayarlayın <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="1580d-130">To accomplish this, set the **Nested** property of the **DataRelation** to **true** when you add the **DataRelation** to the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="1580d-131">Daha fazla bilgi için bkz. [DataRelation Ile Iç Içe geçme](nesting-datarelations.md).</span><span class="sxs-lookup"><span data-stu-id="1580d-131">For more information, see [Nesting DataRelations](nesting-datarelations.md).</span></span>  
  
 <span data-ttu-id="1580d-132">Aşağıda bir dosyasına bir dosyasının XML gösteriminin nasıl yazılacağı hakkında iki örnek verilmiştir <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="1580d-132">The following are two examples of how to write the XML representation of a <xref:System.Data.DataSet> to a file.</span></span> <span data-ttu-id="1580d-133">İlk örnek, sonuçta elde edilen XML için dosya adını **WriteXml** öğesine bir dize olarak geçirir.</span><span class="sxs-lookup"><span data-stu-id="1580d-133">The first example passes the file name for the resulting XML as a string to **WriteXml**.</span></span> <span data-ttu-id="1580d-134">İkinci örnek, bir **System. IO. StreamWriter** nesnesi geçirir.</span><span class="sxs-lookup"><span data-stu-id="1580d-134">The second example passes a **System.IO.StreamWriter** object.</span></span>
  
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
  
## <a name="mapping-columns-to-xml-elements-attributes-and-text"></a><span data-ttu-id="1580d-135">Sütunları XML öğeleri, öznitelikleri ve metin ile eşleme</span><span class="sxs-lookup"><span data-stu-id="1580d-135">Mapping Columns to XML Elements, Attributes, and Text</span></span>  

 <span data-ttu-id="1580d-136">**DataColumn** nesnesinin **ColumnMapping** özelliğini kullanarak bir tablo sütununun XML olarak nasıl temsil edileceğini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1580d-136">You can specify how a column of a table is represented in XML using the **ColumnMapping** property of the **DataColumn** object.</span></span> <span data-ttu-id="1580d-137">Aşağıdaki tablo, bir tablo sütununun **ColumnMapping** özelliği ve elde edilen XML Için farklı **MappingType** değerlerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="1580d-137">The following table shows the different **MappingType** values for the **ColumnMapping** property of a table column, and the resulting XML.</span></span>  
  
|<span data-ttu-id="1580d-138">MappingType değeri</span><span class="sxs-lookup"><span data-stu-id="1580d-138">MappingType value</span></span>|<span data-ttu-id="1580d-139">Description</span><span class="sxs-lookup"><span data-stu-id="1580d-139">Description</span></span>|  
|-----------------------|-----------------|  
|<span data-ttu-id="1580d-140">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="1580d-140">**Element**</span></span>|<span data-ttu-id="1580d-141">Bu varsayılan seçenektir.</span><span class="sxs-lookup"><span data-stu-id="1580d-141">This is the default.</span></span> <span data-ttu-id="1580d-142">Sütun, ColumnName 'un öğenin adı olduğu ve sütunun içeriği öğenin metni olarak yazıldığı bir XML öğesi olarak yazılır.</span><span class="sxs-lookup"><span data-stu-id="1580d-142">The column is written as an XML element where the ColumnName is the name of the element and the contents of the column are written as the text of the element.</span></span> <span data-ttu-id="1580d-143">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="1580d-143">For example:</span></span><br /><br /> `<ColumnName>Column Contents</ColumnName>`|  
|<span data-ttu-id="1580d-144">**Öznitelik**</span><span class="sxs-lookup"><span data-stu-id="1580d-144">**Attribute**</span></span>|<span data-ttu-id="1580d-145">Sütun, ColumnName 'un özniteliğin adı olduğu ve sütunun içeriğinin öznitelik değeri olarak yazıldığı geçerli satır için XML öğesinin XML özniteliği olarak yazılır.</span><span class="sxs-lookup"><span data-stu-id="1580d-145">The column is written as an XML attribute of the XML element for the current row where the ColumnName is the name of the attribute and the contents of the column are written as the value of the attribute.</span></span> <span data-ttu-id="1580d-146">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="1580d-146">For example:</span></span><br /><br /> `<RowElement ColumnName="Column Contents" />`|  
|<span data-ttu-id="1580d-147">**'Dir**</span><span class="sxs-lookup"><span data-stu-id="1580d-147">**SimpleContent**</span></span>|<span data-ttu-id="1580d-148">Sütunun içeriği, geçerli satırın XML öğesinde metin olarak yazılır.</span><span class="sxs-lookup"><span data-stu-id="1580d-148">The contents of the column are written as text in the XML element for the current row.</span></span> <span data-ttu-id="1580d-149">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="1580d-149">For example:</span></span><br /><br /> `<RowElement>Column Contents</RowElement>`<br /><br /> <span data-ttu-id="1580d-150">**Öğe** sütunları veya iç içe ilişkiler içeren bir tablonun sütunu için **simpleContent** ayarlanamaz.</span><span class="sxs-lookup"><span data-stu-id="1580d-150">Note that **SimpleContent** cannot be set for a column of a table that has **Element** columns or nested relations.</span></span>|  
|<span data-ttu-id="1580d-151">**Gizli**</span><span class="sxs-lookup"><span data-stu-id="1580d-151">**Hidden**</span></span>|<span data-ttu-id="1580d-152">Sütun XML çıktısında yazılmadı.</span><span class="sxs-lookup"><span data-stu-id="1580d-152">The column is not written in the XML output.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1580d-153">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1580d-153">See also</span></span>

- [<span data-ttu-id="1580d-154">DataSet içinde XML kullanma</span><span class="sxs-lookup"><span data-stu-id="1580d-154">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="1580d-155">DiffGrams</span><span class="sxs-lookup"><span data-stu-id="1580d-155">DiffGrams</span></span>](diffgrams.md)
- [<span data-ttu-id="1580d-156">DataRelations’ı İç İçe Yerleştirme</span><span class="sxs-lookup"><span data-stu-id="1580d-156">Nesting DataRelations</span></span>](nesting-datarelations.md)
- [<span data-ttu-id="1580d-157">XSD Olarak DataSet Schema Bilgilerini Yazma</span><span class="sxs-lookup"><span data-stu-id="1580d-157">Writing DataSet Schema Information as XSD</span></span>](writing-dataset-schema-information-as-xsd.md)
- [<span data-ttu-id="1580d-158">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="1580d-158">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="1580d-159">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="1580d-159">ADO.NET Overview</span></span>](../ado-net-overview.md)
