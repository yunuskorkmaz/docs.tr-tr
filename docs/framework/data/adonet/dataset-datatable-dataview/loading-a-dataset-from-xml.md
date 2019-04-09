---
title: XML’den DataSet Yükleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49c083b7-a5ed-41cf-aabc-5aaba96f00e6
ms.openlocfilehash: 0c53e3a15bcbe61db7da1edb31ecd3fd562603f5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59099904"
---
# <a name="loading-a-dataset-from-xml"></a><span data-ttu-id="99666-102">XML’den DataSet Yükleme</span><span class="sxs-lookup"><span data-stu-id="99666-102">Loading a DataSet from XML</span></span>
<span data-ttu-id="99666-103">Bir ADO.NET içeriğini <xref:System.Data.DataSet> bir XML akışı veya bir belgeden oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="99666-103">The contents of an ADO.NET <xref:System.Data.DataSet> can be created from an XML stream or document.</span></span> <span data-ttu-id="99666-104">Ayrıca, .NET Framework ile büyük esneklik hangi bilgilerin, XML'den yüklenen sahip olduğunuz ve nasıl önceden şema veya ilişkisel yapısını <xref:System.Data.DataSet> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="99666-104">In addition, with the .NET Framework you have great flexibility over what information is loaded from XML, and how the schema or relational structure of the <xref:System.Data.DataSet> is created.</span></span>  
  
 <span data-ttu-id="99666-105">Doldurmak için bir <xref:System.Data.DataSet> XML verileri ile kullanma **ReadXml** yöntemi <xref:System.Data.DataSet> nesne.</span><span class="sxs-lookup"><span data-stu-id="99666-105">To fill a <xref:System.Data.DataSet> with data from XML, use the **ReadXml** method of the <xref:System.Data.DataSet> object.</span></span> <span data-ttu-id="99666-106">**ReadXml** yöntemi bir akışa bir dosyadan okur ya da bir **XmlReader**ve kaynak XML ek olarak isteğe bağlı bağımsız değişkenleri alan **XmlReadMode** bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="99666-106">The **ReadXml** method reads from a file, a stream, or an **XmlReader**, and takes as arguments the source of the XML plus an optional **XmlReadMode** argument.</span></span> <span data-ttu-id="99666-107">Hakkında daha fazla bilgi için **XmlReader**, bkz: [XmlTextReader ile XML verileri okuma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/tfz3cz6w(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="99666-107">For more information about the **XmlReader**, see [Reading XML Data with XmlTextReader](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/tfz3cz6w(v=vs.100)).</span></span> <span data-ttu-id="99666-108">**ReadXml** yöntemi XML akışı veya belge ve yükleri içeriğini okur <xref:System.Data.DataSet> verilerle.</span><span class="sxs-lookup"><span data-stu-id="99666-108">The **ReadXml** method reads the contents of the XML stream or document and loads the <xref:System.Data.DataSet> with data.</span></span> <span data-ttu-id="99666-109">İlişkisel şemasını oluşturacak <xref:System.Data.DataSet> bağlı olarak **XmlReadMode** belirtilen ve olup olmadığı bir ilişkisel şema zaten mevcut.</span><span class="sxs-lookup"><span data-stu-id="99666-109">It will also create the relational schema of the <xref:System.Data.DataSet> depending on the **XmlReadMode** specified and whether or not a relational schema already exists.</span></span>  
  
 <span data-ttu-id="99666-110">Aşağıdaki tablo için seçenekleri açıklar **XmlReadMode** bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="99666-110">The following table describes the options for the **XmlReadMode** argument.</span></span>  
  
|<span data-ttu-id="99666-111">Seçenek</span><span class="sxs-lookup"><span data-stu-id="99666-111">Option</span></span>|<span data-ttu-id="99666-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="99666-112">Description</span></span>|  
|------------|-----------------|  
|**<span data-ttu-id="99666-113">Otomatik</span><span class="sxs-lookup"><span data-stu-id="99666-113">Auto</span></span>**|<span data-ttu-id="99666-114">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="99666-114">This is the default.</span></span> <span data-ttu-id="99666-115">XML inceler ve en uygun seçeneği şu sırayla seçer:</span><span class="sxs-lookup"><span data-stu-id="99666-115">Examines the XML and chooses the most appropriate option in the following order:</span></span><br /><br /> <span data-ttu-id="99666-116">-Bir DiffGram XML olup olmadığını **DiffGram** kullanılır.</span><span class="sxs-lookup"><span data-stu-id="99666-116">-   If the XML is a DiffGram, **DiffGram** is used.</span></span><br /><span data-ttu-id="99666-117">-Eğer <xref:System.Data.DataSet> bir şema içeriyor veya bir satır içi şema XML içeriyor **ReadSchema** kullanılır.</span><span class="sxs-lookup"><span data-stu-id="99666-117">-   If the <xref:System.Data.DataSet> contains a schema or the XML contains an inline schema, **ReadSchema** is used.</span></span><br /><span data-ttu-id="99666-118">-Eğer <xref:System.Data.DataSet> bir şema içermiyor ve bir satır içi şema XML içermiyor **InferSchema** kullanılır.</span><span class="sxs-lookup"><span data-stu-id="99666-118">-   If the <xref:System.Data.DataSet> does not contain a schema and the XML does not contain an inline schema, **InferSchema** is used.</span></span><br /><br /> <span data-ttu-id="99666-119">Okunan XML biçimini biliyorsanız, en iyi performans için açık bir ayarladığınız önerilir **XmlReadMode**yerine kabul daha **otomatik** varsayılan.</span><span class="sxs-lookup"><span data-stu-id="99666-119">If you know the format of the XML being read, for best performance it is recommended that you set an explicit **XmlReadMode**, rather than accept the **Auto** default.</span></span>|  
|**<span data-ttu-id="99666-120">ReadSchema</span><span class="sxs-lookup"><span data-stu-id="99666-120">ReadSchema</span></span>**|<span data-ttu-id="99666-121">Herhangi bir satır içi şema okur ve verileri hem de şemayı yükler.</span><span class="sxs-lookup"><span data-stu-id="99666-121">Reads any inline schema and loads the data and schema.</span></span><br /><br /> <span data-ttu-id="99666-122">Varsa <xref:System.Data.DataSet> zaten bir şema mevcut şemayla eklenen yeni tablolar satır içi şema içeriyor. <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="99666-122">If the <xref:System.Data.DataSet> already contains a schema, new tables are added from the inline schema to the existing schema in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="99666-123">Herhangi bir tablo satır içi şema zaten mevcut değilse <xref:System.Data.DataSet>, bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="99666-123">If any tables in the inline schema already exist in the <xref:System.Data.DataSet>, an exception is thrown.</span></span> <span data-ttu-id="99666-124">Mevcut bir tabloyu kullanarak şemayı değiştirmek mümkün olmayacaktır **gt;XmlReadMode.ReadSchema**.</span><span class="sxs-lookup"><span data-stu-id="99666-124">You will not be able to modify the schema of an existing table using **XmlReadMode.ReadSchema**.</span></span><br /><br /> <span data-ttu-id="99666-125">Varsa <xref:System.Data.DataSet> bir şema içermiyor ve satır içi şema yok, hiçbir veri okuyun.</span><span class="sxs-lookup"><span data-stu-id="99666-125">If the <xref:System.Data.DataSet> does not contain a schema, and there is no inline schema, no data is read.</span></span><br /><br /> <span data-ttu-id="99666-126">Satır içi şema XML Şeması Tanım Dili (XSD) şemaya kullanılarak tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="99666-126">Inline schema can be defined using XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="99666-127">Satır içi şema XML şema olarak yazma hakkında daha fazla ayrıntı için bkz. [türetme DataSet ilişkisel yapısını XML Şeması (XSD) öğesinden](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span><span class="sxs-lookup"><span data-stu-id="99666-127">For details about writing inline schema as XML Schema, see [Deriving DataSet Relational Structure from XML Schema (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span></span>|  
|**<span data-ttu-id="99666-128">IgnoreSchema</span><span class="sxs-lookup"><span data-stu-id="99666-128">IgnoreSchema</span></span>**|<span data-ttu-id="99666-129">Herhangi bir satır içi şema yoksayar ve mevcut verileri yükler <xref:System.Data.DataSet> şema.</span><span class="sxs-lookup"><span data-stu-id="99666-129">Ignores any inline schema and loads the data into the existing <xref:System.Data.DataSet> schema.</span></span> <span data-ttu-id="99666-130">Varolan şema eşleşmeyen herhangi bir veri göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="99666-130">Any data that does not match the existing schema is discarded.</span></span> <span data-ttu-id="99666-131">Şema varsa <xref:System.Data.DataSet>, hiç veri yüklenmedi.</span><span class="sxs-lookup"><span data-stu-id="99666-131">If no schema exists in the <xref:System.Data.DataSet>, no data is loaded.</span></span><br /><br /> <span data-ttu-id="99666-132">Veriler bir DiffGram ise **IgnoreSchema** ile aynı işlevlere sahip **DiffGram** *.*</span><span class="sxs-lookup"><span data-stu-id="99666-132">If the data is a DiffGram, **IgnoreSchema** has the same functionality as **DiffGram** *.*</span></span>|  
|**<span data-ttu-id="99666-133">InferSchema</span><span class="sxs-lookup"><span data-stu-id="99666-133">InferSchema</span></span>**|<span data-ttu-id="99666-134">Herhangi bir satır içi şema yoksayar ve XML veri yapısını başına şemayı algılar ve ardından verileri yükler.</span><span class="sxs-lookup"><span data-stu-id="99666-134">Ignores any inline schema and infers the schema per the structure of the XML data, then loads the data.</span></span><br /><br /> <span data-ttu-id="99666-135">Varsa <xref:System.Data.DataSet> zaten bir şema içeriyor. Geçerli şema varolan tablolarda sütunlar ekleyerek genişletilir.</span><span class="sxs-lookup"><span data-stu-id="99666-135">If the <xref:System.Data.DataSet> already contains a schema, the current schema is extended by adding columns to existing tables.</span></span> <span data-ttu-id="99666-136">Ek tablolar değil varsa tablolar eklenmeden bırakılır.</span><span class="sxs-lookup"><span data-stu-id="99666-136">Extra tables will not be added if there are not existing tables.</span></span> <span data-ttu-id="99666-137">Farklı bir ad alanı ile gösterilen bir tablo zaten varsa veya çıkarsanan sütun mevcut sütunları arasında çakışma varsa, bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="99666-137">An exception is thrown if an inferred table already exists with a different namespace, or if any inferred columns conflict with existing columns.</span></span><br /><br /> <span data-ttu-id="99666-138">Hakkında ayrıntılar için **ReadXmlSchema** bir şema çıkarsar bir XML belgesinden bkz [DataSet ilişkisel yapısını çıkarma XML'den](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md).</span><span class="sxs-lookup"><span data-stu-id="99666-138">For details about how **ReadXmlSchema** infers a schema from an XML document, see [Inferring DataSet Relational Structure from XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md).</span></span>|  
|**<span data-ttu-id="99666-139">DiffGram</span><span class="sxs-lookup"><span data-stu-id="99666-139">DiffGram</span></span>**|<span data-ttu-id="99666-140">Bir DiffGram okur ve verileri geçerli şemaya ekler.</span><span class="sxs-lookup"><span data-stu-id="99666-140">Reads a DiffGram and adds the data to the current schema.</span></span> <span data-ttu-id="99666-141">**DiffGram** yeni varolan satırları benzersiz tanımlayıcı değerlerinin eşleştiği satırları birleştirir.</span><span class="sxs-lookup"><span data-stu-id="99666-141">**DiffGram** merges new rows with existing rows where the unique identifier values match.</span></span> <span data-ttu-id="99666-142">"Birleştirme veri gelen XML" Bu konu sonuna bakın.</span><span class="sxs-lookup"><span data-stu-id="99666-142">See "Merging Data from XML" at the end of this topic.</span></span> <span data-ttu-id="99666-143">DiffGrams hakkında daha fazla bilgi için bkz: [DiffGrams](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md).</span><span class="sxs-lookup"><span data-stu-id="99666-143">For more information about DiffGrams, see [DiffGrams](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md).</span></span>|  
|**<span data-ttu-id="99666-144">Parça</span><span class="sxs-lookup"><span data-stu-id="99666-144">Fragment</span></span>**|<span data-ttu-id="99666-145">Birden çok XML parçası okuma, akışın sonuna ulaşılana kadar devam eder.</span><span class="sxs-lookup"><span data-stu-id="99666-145">Continues reading multiple XML fragments until the end of the stream is reached.</span></span> <span data-ttu-id="99666-146">Parçacık eşleşen <xref:System.Data.DataSet> şema uygun tablolarına eklenir.</span><span class="sxs-lookup"><span data-stu-id="99666-146">Fragments that match the <xref:System.Data.DataSet> schema are appended to the appropriate tables.</span></span> <span data-ttu-id="99666-147">Eşleşmeyen parçaları <xref:System.Data.DataSet> şema atılır.</span><span class="sxs-lookup"><span data-stu-id="99666-147">Fragments that do not match the <xref:System.Data.DataSet> schema are discarded.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="99666-148">Geçirirseniz bir **XmlReader** için **ReadXml** konumlandırılmış parçası olan bir XML belgesine biçimini **ReadXml** sonraki öğe düğümü için okur ve, temeli olarak değerlendirilecektir. öğe, öğe düğümü yalnızca sonuna kadar okumak.</span><span class="sxs-lookup"><span data-stu-id="99666-148">If you pass an **XmlReader** to **ReadXml** that is positioned part of the way into an XML document, **ReadXml** will read to the next element node and will treat that as the root element, reading until the end of the element node only.</span></span> <span data-ttu-id="99666-149">Belirtirseniz bu uygulanmaz **XmlReadMode.Fragment**.</span><span class="sxs-lookup"><span data-stu-id="99666-149">This does not apply if you specify **XmlReadMode.Fragment**.</span></span>  
  
## <a name="dtd-entities"></a><span data-ttu-id="99666-150">DTD'nin varlıkları</span><span class="sxs-lookup"><span data-stu-id="99666-150">DTD Entities</span></span>  
 <span data-ttu-id="99666-151">Yüklemeye çalışırsanız, XML belge türü tanımı (DTD'nin) şemasında tanımlanan varlıklarını içeriyorsa, bir özel durum oluşturulur bir <xref:System.Data.DataSet> bir dosyaya geçirerek adı, akış veya yapmayan **XmlReader** için  **ReadXml**.</span><span class="sxs-lookup"><span data-stu-id="99666-151">If your XML contains entities defined in a document type definition (DTD) schema, an exception will be thrown if you attempt to load a <xref:System.Data.DataSet> by passing a file name, stream, or non-validating **XmlReader** to **ReadXml**.</span></span> <span data-ttu-id="99666-152">Bunun yerine, oluşturmalısınız bir **XmlValidatingReader**, ile **EntityHandling** kümesine **EntityHandling.ExpandEntities**, geçirin,  **XmlValidatingReader** için **ReadXml**.</span><span class="sxs-lookup"><span data-stu-id="99666-152">Instead, you must create an **XmlValidatingReader**, with **EntityHandling** set to **EntityHandling.ExpandEntities**, and pass your **XmlValidatingReader** to **ReadXml**.</span></span> <span data-ttu-id="99666-153">**XmlValidatingReader** varlıklar tarafından okunan önce genişletilir <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="99666-153">The **XmlValidatingReader** will expand the entities prior to being read by the <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="99666-154">Aşağıdaki kod örneğinde nasıl yükleneceğini gösterir. bir <xref:System.Data.DataSet> bir XML Akışı'ndan.</span><span class="sxs-lookup"><span data-stu-id="99666-154">The following code examples show how to load a <xref:System.Data.DataSet> from an XML stream.</span></span> <span data-ttu-id="99666-155">İlk örnek, gönderilmiş bir dosya adı gösterir **ReadXml** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="99666-155">The first example shows a file name being passed to the **ReadXml** method.</span></span> <span data-ttu-id="99666-156">İkinci örnek XML durdurulmasını kullanarak yüklenen içeren bir dize gösterir bir <xref:System.IO.StringReader>.</span><span class="sxs-lookup"><span data-stu-id="99666-156">The second example shows a string that contains XML being loaded using a <xref:System.IO.StringReader>.</span></span>  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.ReadXml("input.xml", XmlReadMode.ReadSchema)  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.ReadXml("input.xml", XmlReadMode.ReadSchema);  
```  
  
```vb  
Dim dataSet As DataSet = New DataSet  
Dim dataTable As DataTable = New DataTable("table1")  
dataTable.Columns.Add("col1", Type.GetType("System.String"))  
dataSet.Tables.Add(dataTable)  
  
Dim xmlData As String = "<XmlDS><table1><col1>Value1</col1></table1><table1><col1>Value2</col1></table1></XmlDS>"  
  
Dim xmlSR As System.IO.StringReader = New System.IO.StringReader(xmlData)  
  
dataSet.ReadXml(xmlSR, XmlReadMode.IgnoreSchema)  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
DataTable dataTable = new DataTable("table1");  
dataTable.Columns.Add("col1", typeof(string));  
dataSet.Tables.Add(dataTable);  
  
string xmlData = "<XmlDS><table1><col1>Value1</col1></table1><table1><col1>Value2</col1></table1></XmlDS>";  
  
System.IO.StringReader xmlSR = new System.IO.StringReader(xmlData);  
  
dataSet.ReadXml(xmlSR, XmlReadMode.IgnoreSchema);  
```  
  
> [!NOTE]
>  <span data-ttu-id="99666-157">Eğer **ReadXml** çok büyük bir dosya yüklemek için yavaş performansla karşılaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="99666-157">If you call **ReadXml** to load a very large file, you may encounter slow performance.</span></span> <span data-ttu-id="99666-158">İçin en iyi performansı elde etmek için **ReadXml**, büyük bir dosya arama <xref:System.Data.DataTable.BeginLoadData%2A> yöntemi her tablo için <xref:System.Data.DataSet>ve sonra çağrı **ReadXml**.</span><span class="sxs-lookup"><span data-stu-id="99666-158">To ensure best performance for **ReadXml**, on a large file, call the <xref:System.Data.DataTable.BeginLoadData%2A> method for each table in the <xref:System.Data.DataSet>, and then call **ReadXml**.</span></span> <span data-ttu-id="99666-159">Son olarak, çağrı <xref:System.Data.DataTable.EndLoadData%2A> her tablo için <xref:System.Data.DataSet>, aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="99666-159">Finally, call <xref:System.Data.DataTable.EndLoadData%2A> for each table in the <xref:System.Data.DataSet>, as shown in the following example.</span></span>  
  
```vb  
Dim dataTable As DataTable  
  
For Each dataTable In dataSet.Tables  
   dataTable.BeginLoadData()  
Next  
  
dataSet.ReadXml("file.xml")  
  
For Each dataTable in dataSet.Tables  
   dataTable.EndLoadData()  
Next  
```  
  
```csharp  
foreach (DataTable dataTable in dataSet.Tables)  
   dataTable.BeginLoadData();  
  
dataSet.ReadXml("file.xml");   
  
foreach (DataTable dataTable in dataSet.Tables)  
   dataTable.EndLoadData();  
```  
  
> [!NOTE]
>  <span data-ttu-id="99666-160">XSD şeması, <xref:System.Data.DataSet> içeren bir **targetNamespace**veri olmayan okunabilir ve çağrılırken özel durum, karşılaşabileceğiniz **ReadXml** yüklemek için <xref:System.Data.DataSet> barındıran XML ile ad alanı içermeyen öğeler.</span><span class="sxs-lookup"><span data-stu-id="99666-160">If the XSD schema for your <xref:System.Data.DataSet> includes a **targetNamespace**, data may not be read, and you may encounter exceptions, when calling **ReadXml** to load the <xref:System.Data.DataSet> with XML that contains elements with no qualifying namespace.</span></span> <span data-ttu-id="99666-161">Bu durumda, nitelenmemiş öğeleri okumak için ayarlanmış **elementFormDefault** , XSD şema "nitelenmiş" değerine eşit.</span><span class="sxs-lookup"><span data-stu-id="99666-161">To read unqualified elements in this case, set **elementFormDefault** equal to "qualified" in your XSD schema.</span></span> <span data-ttu-id="99666-162">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="99666-162">For example:</span></span>  
  
```xml  
<xsd:schema id="customDataSet"   
  elementFormDefault="qualified"  
  targetNamespace="http://www.tempuri.org/customDataSet.xsd"   
  xmlns="http://www.tempuri.org/customDataSet.xsd"   
  xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
  xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
</xsd:schema>  
```  
  
## <a name="merging-data-from-xml"></a><span data-ttu-id="99666-163">XML verilerini birleştirme</span><span class="sxs-lookup"><span data-stu-id="99666-163">Merging Data from XML</span></span>  
 <span data-ttu-id="99666-164">Varsa <xref:System.Data.DataSet> zaten veri içeriyor. XML yeni verileri zaten mevcut verilere eklenir <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="99666-164">If the <xref:System.Data.DataSet> already contains data, the new data from the XML is added to the data already present in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="99666-165">**ReadXml** XML'den birleştirmez <xref:System.Data.DataSet> herhangi bir satır birincil anahtarları eşleşen bilgileri.</span><span class="sxs-lookup"><span data-stu-id="99666-165">**ReadXml** does not merge from the XML into the <xref:System.Data.DataSet> any row information with matching primary keys.</span></span> <span data-ttu-id="99666-166">Var olan satır bilgileri XML alınan yeni bilgilerle üzerine yazmak için kullanmak **ReadXml** yeni bir <xref:System.Data.DataSet>, ardından <xref:System.Data.DataSet.Merge%2A> yeni <xref:System.Data.DataSet> varolan içine <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="99666-166">To overwrite existing row information with new information from XML, use **ReadXml** to create a new <xref:System.Data.DataSet>, and then <xref:System.Data.DataSet.Merge%2A> the new <xref:System.Data.DataSet> into the existing <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="99666-167">Bu kullanarak DiffGram yüklenirken Not **ReadXML** ile bir **XmlReadMode** , **DiffGram** aynı benzersiz tanımlayıcıya sahip satırları birleştirir.</span><span class="sxs-lookup"><span data-stu-id="99666-167">Note that loading a DiffGram using **ReadXML** with an **XmlReadMode** of **DiffGram** will merge rows that have the same unique identifier.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99666-168">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="99666-168">See also</span></span>

- <xref:System.Data.DataSet.Merge%2A?displayProperty=nameWithType>
- [<span data-ttu-id="99666-169">DataSet içinde XML kullanma</span><span class="sxs-lookup"><span data-stu-id="99666-169">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
- [<span data-ttu-id="99666-170">DiffGrams</span><span class="sxs-lookup"><span data-stu-id="99666-170">DiffGrams</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md)
- [<span data-ttu-id="99666-171">XML Şemasından (XSD) DataSet İlişkisel Yapısını Türetme</span><span class="sxs-lookup"><span data-stu-id="99666-171">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [<span data-ttu-id="99666-172">XML’den DataSet İlişkisel Yapısını Çıkarma</span><span class="sxs-lookup"><span data-stu-id="99666-172">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="99666-173">XML’den DataSet Schema Bilgilerini Yükleme</span><span class="sxs-lookup"><span data-stu-id="99666-173">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="99666-174">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="99666-174">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [<span data-ttu-id="99666-175">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="99666-175">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
