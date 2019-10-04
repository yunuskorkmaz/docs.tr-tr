---
title: Veri kümesi Içeriğini XML verileri olarak yazma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fd15f8a5-3b4c-46d0-a561-4559ab2a4705
ms.openlocfilehash: 9a63e79b2fce137ba9d21db861850a471cb42b9f
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833964"
---
# <a name="writing-dataset-contents-as-xml-data"></a><span data-ttu-id="1570f-102">Veri kümesi Içeriğini XML verileri olarak yazma</span><span class="sxs-lookup"><span data-stu-id="1570f-102">Writing DataSet Contents as XML Data</span></span>
<span data-ttu-id="1570f-103">ADO.NET ' de, şemasına sahip veya olmayan <xref:System.Data.DataSet> ' ın bir XML gösterimini yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1570f-103">In ADO.NET you can write an XML representation of a <xref:System.Data.DataSet>, with or without its schema.</span></span> <span data-ttu-id="1570f-104">Şema bilgileri XML ile satır içi içeriyorsa, XML şeması tanım dili (XSD) kullanılarak yazılır.</span><span class="sxs-lookup"><span data-stu-id="1570f-104">If schema information is included inline with the XML, it is written using the XML Schema definition language (XSD).</span></span> <span data-ttu-id="1570f-105">Şema <xref:System.Data.DataSet> ' ın tablo tanımlarını ve ilişki ve kısıtlama tanımlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="1570f-105">The schema contains the table definitions of the <xref:System.Data.DataSet> as well as the relation and constraint definitions.</span></span>  
  
 <span data-ttu-id="1570f-106">Bir <xref:System.Data.DataSet>, XML verisi olarak yazıldığında, <xref:System.Data.DataSet> ' deki satırlar geçerli sürümlerinde yazılır.</span><span class="sxs-lookup"><span data-stu-id="1570f-106">When a <xref:System.Data.DataSet> is written as XML data, the rows in the <xref:System.Data.DataSet> are written in their current versions.</span></span> <span data-ttu-id="1570f-107">Ancak, <xref:System.Data.DataSet> ' ın hem geçerli hem de orijinal değerlerinin dahil edilmesini sağlamak için bir DiffGram olarak yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="1570f-107">However, the <xref:System.Data.DataSet> can also be written as a DiffGram so that both the current and the original values of the rows will be included.</span></span>  
  
 <span data-ttu-id="1570f-108">@No__t-0 ' ın XML temsili bir dosyaya, akışa, bir **XmlWriter**'a veya dizeye yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="1570f-108">The XML representation of the <xref:System.Data.DataSet> can be written to a file, a stream, an **XmlWriter**, or a string.</span></span> <span data-ttu-id="1570f-109">Bu seçimler <xref:System.Data.DataSet> ' ın XML gösterimini taşımanın harika bir esnekliğini sağlar.</span><span class="sxs-lookup"><span data-stu-id="1570f-109">These choices provide great flexibility for how you transport the XML representation of the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="1570f-110">@No__t-0 ' ın XML gösterimini bir dize olarak almak için, aşağıdaki örnekte gösterildiği gibi **GetXml** metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="1570f-110">To obtain the XML representation of the <xref:System.Data.DataSet> as a string, use the **GetXml** method as shown in the following example.</span></span>  
  
```vb  
Dim xmlDS As String = custDS.GetXml()  
```  
  
```csharp  
string xmlDS = custDS.GetXml();  
```  
  
 <span data-ttu-id="1570f-111">**GetXml** şema bilgisi olmadan <xref:System.Data.DataSet> ' in XML gösterimini döndürür.</span><span class="sxs-lookup"><span data-stu-id="1570f-111">**GetXml** returns the XML representation of the <xref:System.Data.DataSet> without schema information.</span></span> <span data-ttu-id="1570f-112">@No__t-0 ' dan (XML şeması olarak) şema bilgilerini bir dizeye yazmak için **GetXmlSchema**kullanın.</span><span class="sxs-lookup"><span data-stu-id="1570f-112">To write the schema information from the <xref:System.Data.DataSet> (as XML Schema) to a string, use **GetXmlSchema**.</span></span>  
  
 <span data-ttu-id="1570f-113">Bir dosyaya, akışa veya **XmlWriter**'a bir @no__t yazmak için **WriteXml** yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="1570f-113">To write a <xref:System.Data.DataSet> to a file, stream, or **XmlWriter**, use the **WriteXml** method.</span></span> <span data-ttu-id="1570f-114">**WriteXml** öğesine geçirdiğiniz ilk parametre, XML çıkışının hedefdir.</span><span class="sxs-lookup"><span data-stu-id="1570f-114">The first parameter you pass to **WriteXml** is the destination of the XML output.</span></span> <span data-ttu-id="1570f-115">Örneğin, bir dosya adı, bir **System. IO. TextWriter** nesnesi vb. içeren bir dize geçirin.</span><span class="sxs-lookup"><span data-stu-id="1570f-115">For example, pass a string containing a file name, a **System.IO.TextWriter** object, and so on.</span></span> <span data-ttu-id="1570f-116">XML çıkışının nasıl yazılacağını belirtmek için bir **XmlWriteMode** isteğe bağlı ikinci parametresini geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1570f-116">You can pass an optional second parameter of an **XmlWriteMode** to specify how the XML output is to be written.</span></span>  
  
 <span data-ttu-id="1570f-117">Aşağıdaki tabloda **XmlWriteMode**seçenekleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1570f-117">The following table shows the options for **XmlWriteMode**.</span></span>  
  
|<span data-ttu-id="1570f-118">XmlWriteMode seçeneği</span><span class="sxs-lookup"><span data-stu-id="1570f-118">XmlWriteMode option</span></span>|<span data-ttu-id="1570f-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1570f-119">Description</span></span>|  
|-------------------------|-----------------|  
|<span data-ttu-id="1570f-120">**IgnoreSchema**</span><span class="sxs-lookup"><span data-stu-id="1570f-120">**IgnoreSchema**</span></span>|<span data-ttu-id="1570f-121">@No__t-0 ' ın geçerli içeriğini xml şeması olmadan XML verisi olarak yazar.</span><span class="sxs-lookup"><span data-stu-id="1570f-121">Writes the current contents of the <xref:System.Data.DataSet> as XML data, without an XML Schema.</span></span> <span data-ttu-id="1570f-122">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="1570f-122">This is the default.</span></span>|  
|<span data-ttu-id="1570f-123">**WriteSchema seçeneğine ayarlayın**</span><span class="sxs-lookup"><span data-stu-id="1570f-123">**WriteSchema**</span></span>|<span data-ttu-id="1570f-124">@No__t-0 ' ın geçerli içeriğini, ilişkisel yapıda satır içi XML şeması olarak XML verisi olarak yazar.</span><span class="sxs-lookup"><span data-stu-id="1570f-124">Writes the current contents of the <xref:System.Data.DataSet> as XML data with the relational structure as inline XML Schema.</span></span>|  
|<span data-ttu-id="1570f-125">**Içeriyor**</span><span class="sxs-lookup"><span data-stu-id="1570f-125">**DiffGram**</span></span>|<span data-ttu-id="1570f-126">Özgün ve geçerli değerler dahil olmak üzere tüm <xref:System.Data.DataSet> ' ı bir DiffGram olarak yazar.</span><span class="sxs-lookup"><span data-stu-id="1570f-126">Writes the entire <xref:System.Data.DataSet> as a DiffGram, including original and current values.</span></span> <span data-ttu-id="1570f-127">Daha fazla bilgi için bkz. [DiffGram](diffgrams.md).</span><span class="sxs-lookup"><span data-stu-id="1570f-127">For more information, see [DiffGrams](diffgrams.md).</span></span>|  
  
 <span data-ttu-id="1570f-128">**DataRelation** nesneleri içeren <xref:System.Data.DataSet> ' ın bir XML temsilini yazarken, sonuçta elde edilen XML 'nin ilgili üst öğelerinde iç içe geçmiş her ilişkinin alt satırlarına sahip olmasını istersiniz.</span><span class="sxs-lookup"><span data-stu-id="1570f-128">When writing an XML representation of a <xref:System.Data.DataSet> that contains **DataRelation** objects, you will most likely want the resulting XML to have the child rows of each relation nested within their related parent elements.</span></span> <span data-ttu-id="1570f-129">Bunu gerçekleştirmek için, **DataRelation** 'ı <xref:System.Data.DataSet> ' e eklediğinizde **DataRelation** 'ın **Nested** özelliğini **true** olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="1570f-129">To accomplish this, set the **Nested** property of the **DataRelation** to **true** when you add the **DataRelation** to the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="1570f-130">Daha fazla bilgi için bkz. [DataRelation Ile Iç Içe geçme](nesting-datarelations.md).</span><span class="sxs-lookup"><span data-stu-id="1570f-130">For more information, see [Nesting DataRelations](nesting-datarelations.md).</span></span>  
  
 <span data-ttu-id="1570f-131">Aşağıda bir <xref:System.Data.DataSet> ' ın XML gösteriminin bir dosyaya nasıl yazılacağı hakkında iki örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="1570f-131">The following are two examples of how to write the XML representation of a <xref:System.Data.DataSet> to a file.</span></span> <span data-ttu-id="1570f-132">İlk örnek, sonuçta elde edilen XML için dosya adını **WriteXml**öğesine bir dize olarak geçirir.</span><span class="sxs-lookup"><span data-stu-id="1570f-132">The first example passes the file name for the resulting XML as a string to **WriteXml**.</span></span> <span data-ttu-id="1570f-133">İkinci örnek, bir **System. IO. StreamWriter** nesnesi geçirir.</span><span class="sxs-lookup"><span data-stu-id="1570f-133">The second example passes a **System.IO.StreamWriter** object.</span></span>
  
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
  
## <a name="mapping-columns-to-xml-elements-attributes-and-text"></a><span data-ttu-id="1570f-134">Sütunları XML öğeleri, öznitelikleri ve metin ile eşleme</span><span class="sxs-lookup"><span data-stu-id="1570f-134">Mapping Columns to XML Elements, Attributes, and Text</span></span>  
 <span data-ttu-id="1570f-135">**DataColumn** nesnesinin **ColumnMapping** özelliğini kullanarak bir tablo sütununun XML olarak nasıl temsil edileceğini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1570f-135">You can specify how a column of a table is represented in XML using the **ColumnMapping** property of the **DataColumn** object.</span></span> <span data-ttu-id="1570f-136">Aşağıdaki tablo, bir tablo sütununun **ColumnMapping** özelliği ve elde edilen XML Için farklı **MappingType** değerlerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="1570f-136">The following table shows the different **MappingType** values for the **ColumnMapping** property of a table column, and the resulting XML.</span></span>  
  
|<span data-ttu-id="1570f-137">MappingType değeri</span><span class="sxs-lookup"><span data-stu-id="1570f-137">MappingType value</span></span>|<span data-ttu-id="1570f-138">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1570f-138">Description</span></span>|  
|-----------------------|-----------------|  
|<span data-ttu-id="1570f-139">**Dosyalarında**</span><span class="sxs-lookup"><span data-stu-id="1570f-139">**Element**</span></span>|<span data-ttu-id="1570f-140">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="1570f-140">This is the default.</span></span> <span data-ttu-id="1570f-141">Sütun, ColumnName 'un öğenin adı olduğu ve sütunun içeriği öğenin metni olarak yazıldığı bir XML öğesi olarak yazılır.</span><span class="sxs-lookup"><span data-stu-id="1570f-141">The column is written as an XML element where the ColumnName is the name of the element and the contents of the column are written as the text of the element.</span></span> <span data-ttu-id="1570f-142">Örnek:</span><span class="sxs-lookup"><span data-stu-id="1570f-142">For example:</span></span><br /><br /> `<ColumnName>Column Contents</ColumnName>`|  
|<span data-ttu-id="1570f-143">**Özniteliğe**</span><span class="sxs-lookup"><span data-stu-id="1570f-143">**Attribute**</span></span>|<span data-ttu-id="1570f-144">Sütun, ColumnName 'un özniteliğin adı olduğu ve sütunun içeriğinin öznitelik değeri olarak yazıldığı geçerli satır için XML öğesinin XML özniteliği olarak yazılır.</span><span class="sxs-lookup"><span data-stu-id="1570f-144">The column is written as an XML attribute of the XML element for the current row where the ColumnName is the name of the attribute and the contents of the column are written as the value of the attribute.</span></span> <span data-ttu-id="1570f-145">Örnek:</span><span class="sxs-lookup"><span data-stu-id="1570f-145">For example:</span></span><br /><br /> `<RowElement ColumnName="Column Contents" />`|  
|<span data-ttu-id="1570f-146">**'Dir**</span><span class="sxs-lookup"><span data-stu-id="1570f-146">**SimpleContent**</span></span>|<span data-ttu-id="1570f-147">Sütunun içeriği, geçerli satırın XML öğesinde metin olarak yazılır.</span><span class="sxs-lookup"><span data-stu-id="1570f-147">The contents of the column are written as text in the XML element for the current row.</span></span> <span data-ttu-id="1570f-148">Örnek:</span><span class="sxs-lookup"><span data-stu-id="1570f-148">For example:</span></span><br /><br /> `<RowElement>Column Contents</RowElement>`<br /><br /> <span data-ttu-id="1570f-149">**Öğe** sütunları veya iç içe ilişkiler içeren bir tablonun sütunu için **simpleContent** ayarlanamaz.</span><span class="sxs-lookup"><span data-stu-id="1570f-149">Note that **SimpleContent** cannot be set for a column of a table that has **Element** columns or nested relations.</span></span>|  
|<span data-ttu-id="1570f-150">**Lene**</span><span class="sxs-lookup"><span data-stu-id="1570f-150">**Hidden**</span></span>|<span data-ttu-id="1570f-151">Sütun XML çıktısında yazılmadı.</span><span class="sxs-lookup"><span data-stu-id="1570f-151">The column is not written in the XML output.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1570f-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1570f-152">See also</span></span>

- [<span data-ttu-id="1570f-153">Bir veri kümesinde XML kullanma</span><span class="sxs-lookup"><span data-stu-id="1570f-153">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="1570f-154">DiffGram</span><span class="sxs-lookup"><span data-stu-id="1570f-154">DiffGrams</span></span>](diffgrams.md)
- [<span data-ttu-id="1570f-155">DataRelation 'ı iç içe geçirme</span><span class="sxs-lookup"><span data-stu-id="1570f-155">Nesting DataRelations</span></span>](nesting-datarelations.md)
- [<span data-ttu-id="1570f-156">Veri kümesi şema bilgilerini XSD olarak yazma</span><span class="sxs-lookup"><span data-stu-id="1570f-156">Writing DataSet Schema Information as XSD</span></span>](writing-dataset-schema-information-as-xsd.md)
- [<span data-ttu-id="1570f-157">Veri kümeleri, DataTable ve DataView</span><span class="sxs-lookup"><span data-stu-id="1570f-157">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="1570f-158">ADO.NET genel bakış</span><span class="sxs-lookup"><span data-stu-id="1570f-158">ADO.NET Overview</span></span>](../ado-net-overview.md)
