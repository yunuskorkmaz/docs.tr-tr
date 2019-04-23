---
title: XML Verileri Olarak DataSet İçeriği Yazma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fd15f8a5-3b4c-46d0-a561-4559ab2a4705
ms.openlocfilehash: dae044a9d7802e858f1f24dd4aa0f1de8f6cba7a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59158958"
---
# <a name="writing-dataset-contents-as-xml-data"></a><span data-ttu-id="04b35-102">XML Verileri Olarak DataSet İçeriği Yazma</span><span class="sxs-lookup"><span data-stu-id="04b35-102">Writing DataSet Contents as XML Data</span></span>
<span data-ttu-id="04b35-103">ADO.NET içinde bir XML temsilini yazabileceğiniz bir <xref:System.Data.DataSet>, ile veya olmadan şeması.</span><span class="sxs-lookup"><span data-stu-id="04b35-103">In ADO.NET you can write an XML representation of a <xref:System.Data.DataSet>, with or without its schema.</span></span> <span data-ttu-id="04b35-104">XML ile satır içi şema bilgileri ise XML Şeması Tanım Dili (XSD) kullanarak yazılır.</span><span class="sxs-lookup"><span data-stu-id="04b35-104">If schema information is included inline with the XML, it is written using the XML Schema definition language (XSD).</span></span> <span data-ttu-id="04b35-105">Tablo tanımları şema içeriyor <xref:System.Data.DataSet> ilişki ve kısıtlama tanımları yanı sıra.</span><span class="sxs-lookup"><span data-stu-id="04b35-105">The schema contains the table definitions of the <xref:System.Data.DataSet> as well as the relation and constraint definitions.</span></span>  
  
 <span data-ttu-id="04b35-106">Olduğunda bir <xref:System.Data.DataSet> XML verileri, satır olarak yazılır <xref:System.Data.DataSet> geçerli sürümlerine yazılır.</span><span class="sxs-lookup"><span data-stu-id="04b35-106">When a <xref:System.Data.DataSet> is written as XML data, the rows in the <xref:System.Data.DataSet> are written in their current versions.</span></span> <span data-ttu-id="04b35-107">Ancak, <xref:System.Data.DataSet> böylece hem geçerli hem de satır özgün değerlerine dahil edilecek bir DiffGram da yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="04b35-107">However, the <xref:System.Data.DataSet> can also be written as a DiffGram so that both the current and the original values of the rows will be included.</span></span>  
  
 <span data-ttu-id="04b35-108">XML gösterimini <xref:System.Data.DataSet> bir dosyaya, bir akışa yazılabilir bir **XmlWriter**, veya bir dize.</span><span class="sxs-lookup"><span data-stu-id="04b35-108">The XML representation of the <xref:System.Data.DataSet> can be written to a file, a stream, an **XmlWriter**, or a string.</span></span> <span data-ttu-id="04b35-109">Bu seçenek, XML gösterimini nasıl aktarım için büyük esneklik sağlar <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="04b35-109">These choices provide great flexibility for how you transport the XML representation of the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="04b35-110">XML gösterimini elde etmek için <xref:System.Data.DataSet> bir dize kullanmak **GetXml** aşağıdaki örnekte gösterildiği gibi yöntemi.</span><span class="sxs-lookup"><span data-stu-id="04b35-110">To obtain the XML representation of the <xref:System.Data.DataSet> as a string, use the **GetXml** method as shown in the following example.</span></span>  
  
```vb  
Dim xmlDS As String = custDS.GetXml()  
```  
  
```csharp  
string xmlDS = custDS.GetXml();  
```  
  
 <span data-ttu-id="04b35-111">**GetXml** XML gösterimini döndürür <xref:System.Data.DataSet> şema bilgileri olmadan.</span><span class="sxs-lookup"><span data-stu-id="04b35-111">**GetXml** returns the XML representation of the <xref:System.Data.DataSet> without schema information.</span></span> <span data-ttu-id="04b35-112">Şema bilgileri yazılacak <xref:System.Data.DataSet> (olarak XML şema) kullanan bir dizeye **GetXmlSchema**.</span><span class="sxs-lookup"><span data-stu-id="04b35-112">To write the schema information from the <xref:System.Data.DataSet> (as XML Schema) to a string, use **GetXmlSchema**.</span></span>  
  
 <span data-ttu-id="04b35-113">Yazılacak bir <xref:System.Data.DataSet> bir dosya için akışı veya **XmlWriter**, kullanın **WriteXml** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="04b35-113">To write a <xref:System.Data.DataSet> to a file, stream, or **XmlWriter**, use the **WriteXml** method.</span></span> <span data-ttu-id="04b35-114">Geçirmek için ilk parametre **WriteXml** hedefi olan XML çıktısı.</span><span class="sxs-lookup"><span data-stu-id="04b35-114">The first parameter you pass to **WriteXml** is the destination of the XML output.</span></span> <span data-ttu-id="04b35-115">Örneğin, bir dosya adı içeren bir dizeyi geçirmek bir **System.IO.TextWriter** nesne ve benzeri.</span><span class="sxs-lookup"><span data-stu-id="04b35-115">For example, pass a string containing a file name, a **System.IO.TextWriter** object, and so on.</span></span> <span data-ttu-id="04b35-116">İsteğe bağlı ikinci parametresi, geçirdiğiniz bir **XmlWriteMode** nasıl yazılacak XML çıktısı olduğunu belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="04b35-116">You can pass an optional second parameter of an **XmlWriteMode** to specify how the XML output is to be written.</span></span>  
  
 <span data-ttu-id="04b35-117">Aşağıdaki tabloda ilişkin seçenekler gösterilir **XmlWriteMode**.</span><span class="sxs-lookup"><span data-stu-id="04b35-117">The following table shows the options for **XmlWriteMode**.</span></span>  
  
|<span data-ttu-id="04b35-118">XmlWriteMode option</span><span class="sxs-lookup"><span data-stu-id="04b35-118">XmlWriteMode option</span></span>|<span data-ttu-id="04b35-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="04b35-119">Description</span></span>|  
|-------------------------|-----------------|  
|<span data-ttu-id="04b35-120">**IgnoreSchema**</span><span class="sxs-lookup"><span data-stu-id="04b35-120">**IgnoreSchema**</span></span>|<span data-ttu-id="04b35-121">Geçerli içeriği Yazar <xref:System.Data.DataSet> olmadan bir XML Şeması XML verileri olarak.</span><span class="sxs-lookup"><span data-stu-id="04b35-121">Writes the current contents of the <xref:System.Data.DataSet> as XML data, without an XML Schema.</span></span> <span data-ttu-id="04b35-122">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="04b35-122">This is the default.</span></span>|  
|<span data-ttu-id="04b35-123">**WriteSchema**</span><span class="sxs-lookup"><span data-stu-id="04b35-123">**WriteSchema**</span></span>|<span data-ttu-id="04b35-124">Geçerli içeriği Yazar <xref:System.Data.DataSet> XML Şeması satır içi olarak ilişkisel yapı ile XML verileri olarak.</span><span class="sxs-lookup"><span data-stu-id="04b35-124">Writes the current contents of the <xref:System.Data.DataSet> as XML data with the relational structure as inline XML Schema.</span></span>|  
|<span data-ttu-id="04b35-125">**DiffGram**</span><span class="sxs-lookup"><span data-stu-id="04b35-125">**DiffGram**</span></span>|<span data-ttu-id="04b35-126">Tüm Yazar <xref:System.Data.DataSet> bir DiffGram özgün ve geçerli değerleri dahil.</span><span class="sxs-lookup"><span data-stu-id="04b35-126">Writes the entire <xref:System.Data.DataSet> as a DiffGram, including original and current values.</span></span> <span data-ttu-id="04b35-127">Daha fazla bilgi için [DiffGrams](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md).</span><span class="sxs-lookup"><span data-stu-id="04b35-127">For more information, see [DiffGrams](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md).</span></span>|  
  
 <span data-ttu-id="04b35-128">Bir XML temsilini yazılırken bir <xref:System.Data.DataSet> içeren **DataRelation** nesneler, büyük olasılıkla her ilişkinin ilgili üst öğeleri içinde iç içe geçmiş alt öğe satırları için elde edilen XML Environment.</span><span class="sxs-lookup"><span data-stu-id="04b35-128">When writing an XML representation of a <xref:System.Data.DataSet> that contains **DataRelation** objects, you will most likely want the resulting XML to have the child rows of each relation nested within their related parent elements.</span></span> <span data-ttu-id="04b35-129">Bunu gerçekleştirmek için ayarlanmış **iç içe** özelliği **DataRelation** için **true** eklediğinizde **DataRelation** için<xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="04b35-129">To accomplish this, set the **Nested** property of the **DataRelation** to **true** when you add the **DataRelation** to the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="04b35-130">Daha fazla bilgi için [iç içe DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md).</span><span class="sxs-lookup"><span data-stu-id="04b35-130">For more information, see [Nesting DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md).</span></span>  
  
 <span data-ttu-id="04b35-131">XML gösterimini yazma konusunda iki örnek aşağıda verilmiştir bir <xref:System.Data.DataSet> dosyaya.</span><span class="sxs-lookup"><span data-stu-id="04b35-131">Following are two examples of how to write the XML representation of a <xref:System.Data.DataSet> to a file.</span></span> <span data-ttu-id="04b35-132">İlk örnek, bir dize olarak elde edilen XML dosyası adını geçirir. **WriteXml**.</span><span class="sxs-lookup"><span data-stu-id="04b35-132">The first example passes the file name for the resulting XML as a string to **WriteXml**.</span></span> <span data-ttu-id="04b35-133">İkinci örnek geçen bir **System.IO.StreamWriter** nesne.</span><span class="sxs-lookup"><span data-stu-id="04b35-133">The second example passes a **System.IO.StreamWriter** object.</span></span>  
  
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
  
## <a name="mapping-columns-to-xml-elements-attributes-and-text"></a><span data-ttu-id="04b35-134">XML öğeleri, öznitelikleri ve metin sütunları eşleme</span><span class="sxs-lookup"><span data-stu-id="04b35-134">Mapping Columns to XML Elements, Attributes, and Text</span></span>  
 <span data-ttu-id="04b35-135">Bir tablo sütunu XML nasıl temsil edildiğini belirtebilirsiniz kullanarak **Columnmapping'in** özelliği **DataColumn** nesne.</span><span class="sxs-lookup"><span data-stu-id="04b35-135">You can specify how a column of a table is represented in XML using the **ColumnMapping** property of the **DataColumn** object.</span></span> <span data-ttu-id="04b35-136">Aşağıdaki tabloda farklı gösterilmektedir **MappingType** değerleri **Columnmapping'in** bir tablo sütunu ve elde edilen XML özelliği.</span><span class="sxs-lookup"><span data-stu-id="04b35-136">The following table shows the different **MappingType** values for the **ColumnMapping** property of a table column, and the resulting XML.</span></span>  
  
|<span data-ttu-id="04b35-137">MappingType değeri</span><span class="sxs-lookup"><span data-stu-id="04b35-137">MappingType value</span></span>|<span data-ttu-id="04b35-138">Açıklama</span><span class="sxs-lookup"><span data-stu-id="04b35-138">Description</span></span>|  
|-----------------------|-----------------|  
|<span data-ttu-id="04b35-139">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="04b35-139">**Element**</span></span>|<span data-ttu-id="04b35-140">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="04b35-140">This is the default.</span></span> <span data-ttu-id="04b35-141">Sütun, burada ColumnName öğe adı, sütunun içeriğine öğenin metin olarak yazılmış bir XML öğesi olarak yazılır.</span><span class="sxs-lookup"><span data-stu-id="04b35-141">The column is written as an XML element where the ColumnName is the name of the element and the contents of the column are written as the text of the element.</span></span> <span data-ttu-id="04b35-142">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="04b35-142">For example:</span></span><br /><br /> `<ColumnName>Column Contents</ColumnName>`|  
|<span data-ttu-id="04b35-143">**Öznitelik**</span><span class="sxs-lookup"><span data-stu-id="04b35-143">**Attribute**</span></span>|<span data-ttu-id="04b35-144">Sütun XML öğesi geçerli satıra burada ColumnName özniteliğin adını ve sütun içeriğini öznitelik değeri olarak yazılmış bir XML özniteliği olarak yazılır.</span><span class="sxs-lookup"><span data-stu-id="04b35-144">The column is written as an XML attribute of the XML element for the current row where the ColumnName is the name of the attribute and the contents of the column are written as the value of the attribute.</span></span> <span data-ttu-id="04b35-145">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="04b35-145">For example:</span></span><br /><br /> `<RowElement ColumnName="Column Contents" />`|  
|<span data-ttu-id="04b35-146">**SimpleContent**</span><span class="sxs-lookup"><span data-stu-id="04b35-146">**SimpleContent**</span></span>|<span data-ttu-id="04b35-147">Bir sütunun içeriğine metin XML öğesi geçerli satır olarak yazılır.</span><span class="sxs-lookup"><span data-stu-id="04b35-147">The contents of the column are written as text in the XML element for the current row.</span></span> <span data-ttu-id="04b35-148">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="04b35-148">For example:</span></span><br /><br /> `<RowElement>Column Contents</RowElement>`<br /><br /> <span data-ttu-id="04b35-149">Unutmayın **SimpleContent** sahip bir tablo için bir sütun ayarlanamaz **öğesi** sütunları veya iç içe geçmiş ilişkileri.</span><span class="sxs-lookup"><span data-stu-id="04b35-149">Note that **SimpleContent** cannot be set for a column of a table that has **Element** columns or nested relations.</span></span>|  
|<span data-ttu-id="04b35-150">**Gizli**</span><span class="sxs-lookup"><span data-stu-id="04b35-150">**Hidden**</span></span>|<span data-ttu-id="04b35-151">Sütun XML çıktısında yazılmaz.</span><span class="sxs-lookup"><span data-stu-id="04b35-151">The column is not written in the XML output.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="04b35-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="04b35-152">See also</span></span>

- [<span data-ttu-id="04b35-153">DataSet içinde XML kullanma</span><span class="sxs-lookup"><span data-stu-id="04b35-153">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
- [<span data-ttu-id="04b35-154">DiffGrams</span><span class="sxs-lookup"><span data-stu-id="04b35-154">DiffGrams</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md)
- [<span data-ttu-id="04b35-155">DataRelations’ı İç İçe Yerleştirme</span><span class="sxs-lookup"><span data-stu-id="04b35-155">Nesting DataRelations</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)
- [<span data-ttu-id="04b35-156">XSD Olarak DataSet Schema Bilgilerini Yazma</span><span class="sxs-lookup"><span data-stu-id="04b35-156">Writing DataSet Schema Information as XSD</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-schema-information-as-xsd.md)
- [<span data-ttu-id="04b35-157">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="04b35-157">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [<span data-ttu-id="04b35-158">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="04b35-158">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
