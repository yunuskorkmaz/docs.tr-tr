---
title: XML Verileri Olarak DataSet İçeriği Yazma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fd15f8a5-3b4c-46d0-a561-4559ab2a4705
ms.openlocfilehash: b8a8656bb68832a09490e656903fd68788bdeb1d
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203103"
---
# <a name="writing-dataset-contents-as-xml-data"></a><span data-ttu-id="fedcc-102">XML Verileri Olarak DataSet İçeriği Yazma</span><span class="sxs-lookup"><span data-stu-id="fedcc-102">Writing DataSet Contents as XML Data</span></span>
<span data-ttu-id="fedcc-103">ADO.NET içinde, şemasına sahip veya olmadan bir <xref:System.Data.DataSet>XML temsili yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fedcc-103">In ADO.NET you can write an XML representation of a <xref:System.Data.DataSet>, with or without its schema.</span></span> <span data-ttu-id="fedcc-104">Şema bilgileri XML ile satır içi içeriyorsa, XML şeması tanım dili (XSD) kullanılarak yazılır.</span><span class="sxs-lookup"><span data-stu-id="fedcc-104">If schema information is included inline with the XML, it is written using the XML Schema definition language (XSD).</span></span> <span data-ttu-id="fedcc-105">Şema, ilişki ve kısıtlama tanımlarının tablo tanımlarını <xref:System.Data.DataSet> içerir.</span><span class="sxs-lookup"><span data-stu-id="fedcc-105">The schema contains the table definitions of the <xref:System.Data.DataSet> as well as the relation and constraint definitions.</span></span>  
  
 <span data-ttu-id="fedcc-106">Bir <xref:System.Data.DataSet> , XML verileri olarak yazıldığında, <xref:System.Data.DataSet> içindeki satırlar geçerli sürümlerinde yazılır.</span><span class="sxs-lookup"><span data-stu-id="fedcc-106">When a <xref:System.Data.DataSet> is written as XML data, the rows in the <xref:System.Data.DataSet> are written in their current versions.</span></span> <span data-ttu-id="fedcc-107">Ancak, hem <xref:System.Data.DataSet> geçerli hem de satırların orijinal değerlerinin dahil edilmesini sağlamak için de bir DiffGram olarak yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="fedcc-107">However, the <xref:System.Data.DataSet> can also be written as a DiffGram so that both the current and the original values of the rows will be included.</span></span>  
  
 <span data-ttu-id="fedcc-108">Öğesinin <xref:System.Data.DataSet> XML temsili bir dosyaya, akışa, bir **XmlWriter**'a veya bir dizeye yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="fedcc-108">The XML representation of the <xref:System.Data.DataSet> can be written to a file, a stream, an **XmlWriter**, or a string.</span></span> <span data-ttu-id="fedcc-109">Bu seçimler, <xref:System.Data.DataSet>öğesinin XML gösterimini taşımanın harika bir esnekliğini sağlar.</span><span class="sxs-lookup"><span data-stu-id="fedcc-109">These choices provide great flexibility for how you transport the XML representation of the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="fedcc-110">Öğesinin <xref:System.Data.DataSet> XML temsilini bir dize olarak almak için aşağıdaki örnekte gösterildiği gibi **GetXml** metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="fedcc-110">To obtain the XML representation of the <xref:System.Data.DataSet> as a string, use the **GetXml** method as shown in the following example.</span></span>  
  
```vb  
Dim xmlDS As String = custDS.GetXml()  
```  
  
```csharp  
string xmlDS = custDS.GetXml();  
```  
  
 <span data-ttu-id="fedcc-111">**GetXml** şema bilgilerinin <xref:System.Data.DataSet> olmayan XML gösterimini döndürür.</span><span class="sxs-lookup"><span data-stu-id="fedcc-111">**GetXml** returns the XML representation of the <xref:System.Data.DataSet> without schema information.</span></span> <span data-ttu-id="fedcc-112">Şema bilgilerini <xref:System.Data.DataSet> (XML şeması olarak) bir dizeye yazmak için **GetXmlSchema**kullanın.</span><span class="sxs-lookup"><span data-stu-id="fedcc-112">To write the schema information from the <xref:System.Data.DataSet> (as XML Schema) to a string, use **GetXmlSchema**.</span></span>  
  
 <span data-ttu-id="fedcc-113">Bir <xref:System.Data.DataSet> dosyaya, akışa veya **XmlWriter**'a yazmak için **WriteXml** yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="fedcc-113">To write a <xref:System.Data.DataSet> to a file, stream, or **XmlWriter**, use the **WriteXml** method.</span></span> <span data-ttu-id="fedcc-114">**WriteXml** öğesine geçirdiğiniz ilk parametre, XML çıkışının hedefdir.</span><span class="sxs-lookup"><span data-stu-id="fedcc-114">The first parameter you pass to **WriteXml** is the destination of the XML output.</span></span> <span data-ttu-id="fedcc-115">Örneğin, bir dosya adı, bir **System. IO. TextWriter** nesnesi vb. içeren bir dize geçirin.</span><span class="sxs-lookup"><span data-stu-id="fedcc-115">For example, pass a string containing a file name, a **System.IO.TextWriter** object, and so on.</span></span> <span data-ttu-id="fedcc-116">XML çıkışının nasıl yazılacağını belirtmek için bir **XmlWriteMode** isteğe bağlı ikinci parametresini geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fedcc-116">You can pass an optional second parameter of an **XmlWriteMode** to specify how the XML output is to be written.</span></span>  
  
 <span data-ttu-id="fedcc-117">Aşağıdaki tabloda **XmlWriteMode**seçenekleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="fedcc-117">The following table shows the options for **XmlWriteMode**.</span></span>  
  
|<span data-ttu-id="fedcc-118">XmlWriteMode option</span><span class="sxs-lookup"><span data-stu-id="fedcc-118">XmlWriteMode option</span></span>|<span data-ttu-id="fedcc-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fedcc-119">Description</span></span>|  
|-------------------------|-----------------|  
|<span data-ttu-id="fedcc-120">**IgnoreSchema**</span><span class="sxs-lookup"><span data-stu-id="fedcc-120">**IgnoreSchema**</span></span>|<span data-ttu-id="fedcc-121">XML şeması olmadan, XML verilerinin <xref:System.Data.DataSet> geçerli içeriğini yazar.</span><span class="sxs-lookup"><span data-stu-id="fedcc-121">Writes the current contents of the <xref:System.Data.DataSet> as XML data, without an XML Schema.</span></span> <span data-ttu-id="fedcc-122">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="fedcc-122">This is the default.</span></span>|  
|<span data-ttu-id="fedcc-123">**WriteSchema seçeneğine ayarlayın**</span><span class="sxs-lookup"><span data-stu-id="fedcc-123">**WriteSchema**</span></span>|<span data-ttu-id="fedcc-124">XML verilerinin güncel içeriğini <xref:System.Data.DataSet> ilişkisel yapıda satır içi xml şeması olarak yazar.</span><span class="sxs-lookup"><span data-stu-id="fedcc-124">Writes the current contents of the <xref:System.Data.DataSet> as XML data with the relational structure as inline XML Schema.</span></span>|  
|<span data-ttu-id="fedcc-125">**Içeriyor**</span><span class="sxs-lookup"><span data-stu-id="fedcc-125">**DiffGram**</span></span>|<span data-ttu-id="fedcc-126">Özgün ve geçerli <xref:System.Data.DataSet> değerler dahil olmak üzere bir DiffGram olarak tümünü yazar.</span><span class="sxs-lookup"><span data-stu-id="fedcc-126">Writes the entire <xref:System.Data.DataSet> as a DiffGram, including original and current values.</span></span> <span data-ttu-id="fedcc-127">Daha fazla bilgi için bkz. [DiffGram](diffgrams.md).</span><span class="sxs-lookup"><span data-stu-id="fedcc-127">For more information, see [DiffGrams](diffgrams.md).</span></span>|  
  
 <span data-ttu-id="fedcc-128"><xref:System.Data.DataSet> **DataRelation** nesneleri içeren bir XML temsili yazarken, sonuçta elde edilen XML 'nin ilgili üst öğeleri içinde iç içe geçmiş her ilişkinin alt satırlarına sahip olmasını istersiniz.</span><span class="sxs-lookup"><span data-stu-id="fedcc-128">When writing an XML representation of a <xref:System.Data.DataSet> that contains **DataRelation** objects, you will most likely want the resulting XML to have the child rows of each relation nested within their related parent elements.</span></span> <span data-ttu-id="fedcc-129">Bunu gerçekleştirmek için, **DataRelation** 'ı öğesine <xref:System.Data.DataSet>eklediğinizde **DataRelation** 'ın **Nested** özelliğini **true** olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="fedcc-129">To accomplish this, set the **Nested** property of the **DataRelation** to **true** when you add the **DataRelation** to the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="fedcc-130">Daha fazla bilgi için bkz. [DataRelation Ile Iç Içe geçme](nesting-datarelations.md).</span><span class="sxs-lookup"><span data-stu-id="fedcc-130">For more information, see [Nesting DataRelations](nesting-datarelations.md).</span></span>  
  
 <span data-ttu-id="fedcc-131">Aşağıda bir dosyasına bir <xref:System.Data.DataSet> dosyasının XML gösteriminin nasıl yazılacağı hakkında iki örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="fedcc-131">Following are two examples of how to write the XML representation of a <xref:System.Data.DataSet> to a file.</span></span> <span data-ttu-id="fedcc-132">İlk örnek, sonuçta elde edilen XML için dosya adını **WriteXml**öğesine bir dize olarak geçirir.</span><span class="sxs-lookup"><span data-stu-id="fedcc-132">The first example passes the file name for the resulting XML as a string to **WriteXml**.</span></span> <span data-ttu-id="fedcc-133">İkinci örnek, bir **System. IO. StreamWriter** nesnesi geçirir.</span><span class="sxs-lookup"><span data-stu-id="fedcc-133">The second example passes a **System.IO.StreamWriter** object.</span></span>  
  
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
  
## <a name="mapping-columns-to-xml-elements-attributes-and-text"></a><span data-ttu-id="fedcc-134">Sütunları XML öğeleri, öznitelikleri ve metin ile eşleme</span><span class="sxs-lookup"><span data-stu-id="fedcc-134">Mapping Columns to XML Elements, Attributes, and Text</span></span>  
 <span data-ttu-id="fedcc-135">**DataColumn** nesnesinin **ColumnMapping** özelliğini kullanarak bir tablo sütununun XML olarak nasıl temsil edileceğini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fedcc-135">You can specify how a column of a table is represented in XML using the **ColumnMapping** property of the **DataColumn** object.</span></span> <span data-ttu-id="fedcc-136">Aşağıdaki tablo, bir tablo sütununun **ColumnMapping** özelliği ve elde edilen XML Için farklı **MappingType** değerlerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="fedcc-136">The following table shows the different **MappingType** values for the **ColumnMapping** property of a table column, and the resulting XML.</span></span>  
  
|<span data-ttu-id="fedcc-137">MappingType değeri</span><span class="sxs-lookup"><span data-stu-id="fedcc-137">MappingType value</span></span>|<span data-ttu-id="fedcc-138">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fedcc-138">Description</span></span>|  
|-----------------------|-----------------|  
|<span data-ttu-id="fedcc-139">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="fedcc-139">**Element**</span></span>|<span data-ttu-id="fedcc-140">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="fedcc-140">This is the default.</span></span> <span data-ttu-id="fedcc-141">Sütun, ColumnName 'un öğenin adı olduğu ve sütunun içeriği öğenin metni olarak yazıldığı bir XML öğesi olarak yazılır.</span><span class="sxs-lookup"><span data-stu-id="fedcc-141">The column is written as an XML element where the ColumnName is the name of the element and the contents of the column are written as the text of the element.</span></span> <span data-ttu-id="fedcc-142">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="fedcc-142">For example:</span></span><br /><br /> `<ColumnName>Column Contents</ColumnName>`|  
|<span data-ttu-id="fedcc-143">**Öznitelik**</span><span class="sxs-lookup"><span data-stu-id="fedcc-143">**Attribute**</span></span>|<span data-ttu-id="fedcc-144">Sütun, ColumnName 'un özniteliğin adı olduğu ve sütunun içeriğinin öznitelik değeri olarak yazıldığı geçerli satır için XML öğesinin XML özniteliği olarak yazılır.</span><span class="sxs-lookup"><span data-stu-id="fedcc-144">The column is written as an XML attribute of the XML element for the current row where the ColumnName is the name of the attribute and the contents of the column are written as the value of the attribute.</span></span> <span data-ttu-id="fedcc-145">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="fedcc-145">For example:</span></span><br /><br /> `<RowElement ColumnName="Column Contents" />`|  
|<span data-ttu-id="fedcc-146">**'Dir**</span><span class="sxs-lookup"><span data-stu-id="fedcc-146">**SimpleContent**</span></span>|<span data-ttu-id="fedcc-147">Sütunun içeriği, geçerli satırın XML öğesinde metin olarak yazılır.</span><span class="sxs-lookup"><span data-stu-id="fedcc-147">The contents of the column are written as text in the XML element for the current row.</span></span> <span data-ttu-id="fedcc-148">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="fedcc-148">For example:</span></span><br /><br /> `<RowElement>Column Contents</RowElement>`<br /><br /> <span data-ttu-id="fedcc-149">**Öğe** sütunları veya iç içe ilişkiler içeren bir tablonun sütunu için **simpleContent** ayarlanamaz.</span><span class="sxs-lookup"><span data-stu-id="fedcc-149">Note that **SimpleContent** cannot be set for a column of a table that has **Element** columns or nested relations.</span></span>|  
|<span data-ttu-id="fedcc-150">**Lene**</span><span class="sxs-lookup"><span data-stu-id="fedcc-150">**Hidden**</span></span>|<span data-ttu-id="fedcc-151">Sütun XML çıktısında yazılmadı.</span><span class="sxs-lookup"><span data-stu-id="fedcc-151">The column is not written in the XML output.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fedcc-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fedcc-152">See also</span></span>

- [<span data-ttu-id="fedcc-153">DataSet içinde XML kullanma</span><span class="sxs-lookup"><span data-stu-id="fedcc-153">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="fedcc-154">DiffGrams</span><span class="sxs-lookup"><span data-stu-id="fedcc-154">DiffGrams</span></span>](diffgrams.md)
- [<span data-ttu-id="fedcc-155">DataRelations’ı İç İçe Yerleştirme</span><span class="sxs-lookup"><span data-stu-id="fedcc-155">Nesting DataRelations</span></span>](nesting-datarelations.md)
- [<span data-ttu-id="fedcc-156">XSD Olarak DataSet Schema Bilgilerini Yazma</span><span class="sxs-lookup"><span data-stu-id="fedcc-156">Writing DataSet Schema Information as XSD</span></span>](writing-dataset-schema-information-as-xsd.md)
- [<span data-ttu-id="fedcc-157">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="fedcc-157">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="fedcc-158">ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="fedcc-158">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
