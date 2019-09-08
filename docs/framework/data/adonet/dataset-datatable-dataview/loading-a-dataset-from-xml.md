---
title: XML’den DataSet Yükleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49c083b7-a5ed-41cf-aabc-5aaba96f00e6
ms.openlocfilehash: 4c8b26651a1f4050145b6d43e03f9d4cc3d68202
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785286"
---
# <a name="loading-a-dataset-from-xml"></a><span data-ttu-id="757be-102">XML’den DataSet Yükleme</span><span class="sxs-lookup"><span data-stu-id="757be-102">Loading a DataSet from XML</span></span>
<span data-ttu-id="757be-103">Bir ADO.net <xref:System.Data.DataSet> içeriği bir XML akışından veya belgesinden oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="757be-103">The contents of an ADO.NET <xref:System.Data.DataSet> can be created from an XML stream or document.</span></span> <span data-ttu-id="757be-104">Ayrıca .NET Framework, XML 'den hangi bilgilerin yüklendiği ve şema ya da ilişkisel yapısının nasıl oluşturulduğuna ilişkin büyük bir <xref:System.Data.DataSet> esnekliğe sahip olursunuz.</span><span class="sxs-lookup"><span data-stu-id="757be-104">In addition, with the .NET Framework you have great flexibility over what information is loaded from XML, and how the schema or relational structure of the <xref:System.Data.DataSet> is created.</span></span>  
  
 <span data-ttu-id="757be-105">XML 'deki verileri <xref:System.Data.DataSet> bir ile doldurmanız için <xref:System.Data.DataSet> nesnenin **ReadXml** yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="757be-105">To fill a <xref:System.Data.DataSet> with data from XML, use the **ReadXml** method of the <xref:System.Data.DataSet> object.</span></span> <span data-ttu-id="757be-106">**ReadXml** yöntemi bir dosyadan, akıştan veya bir **XmlReader**'dan yararlanır ve XML kaynağı Ile Isteğe bağlı bir **XmlReadMode** bağımsız değişkeni olarak bağımsız değişken alır.</span><span class="sxs-lookup"><span data-stu-id="757be-106">The **ReadXml** method reads from a file, a stream, or an **XmlReader**, and takes as arguments the source of the XML plus an optional **XmlReadMode** argument.</span></span> <span data-ttu-id="757be-107">**XmlReader**hakkında daha fazla bilgi için bkz. [XML verilerini XmlTextReader ile okuma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/tfz3cz6w(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="757be-107">For more information about the **XmlReader**, see [Reading XML Data with XmlTextReader](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/tfz3cz6w(v=vs.100)).</span></span> <span data-ttu-id="757be-108">**ReadXml** yöntemi, XML akışı veya belgesinin içeriğini okur ve <xref:System.Data.DataSet> ile verileri yükler.</span><span class="sxs-lookup"><span data-stu-id="757be-108">The **ReadXml** method reads the contents of the XML stream or document and loads the <xref:System.Data.DataSet> with data.</span></span> <span data-ttu-id="757be-109">Ayrıca, <xref:System.Data.DataSet> belirtilen **XmlReadMode** öğesine ve ilişkisel bir şemanın zaten mevcut olup olmadığına bağlı olarak ilişkisel şeması da oluşturur.</span><span class="sxs-lookup"><span data-stu-id="757be-109">It will also create the relational schema of the <xref:System.Data.DataSet> depending on the **XmlReadMode** specified and whether or not a relational schema already exists.</span></span>  
  
 <span data-ttu-id="757be-110">Aşağıdaki tabloda **XmlReadMode** bağımsız değişkeninin seçenekleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="757be-110">The following table describes the options for the **XmlReadMode** argument.</span></span>  
  
|<span data-ttu-id="757be-111">Seçenek</span><span class="sxs-lookup"><span data-stu-id="757be-111">Option</span></span>|<span data-ttu-id="757be-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="757be-112">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="757be-113">**Auto**</span><span class="sxs-lookup"><span data-stu-id="757be-113">**Auto**</span></span>|<span data-ttu-id="757be-114">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="757be-114">This is the default.</span></span> <span data-ttu-id="757be-115">XML 'i inceler ve aşağıdaki sırada en uygun seçeneği seçer:</span><span class="sxs-lookup"><span data-stu-id="757be-115">Examines the XML and chooses the most appropriate option in the following order:</span></span><br /><br /> <span data-ttu-id="757be-116">-XML bir DiffGram ise, **DiffGram** kullanılır.</span><span class="sxs-lookup"><span data-stu-id="757be-116">-   If the XML is a DiffGram, **DiffGram** is used.</span></span><br /><span data-ttu-id="757be-117">-Bir şema içeriyorsaveyaXMLbirsatıriçişemaiçeriyorsaReadSchema<xref:System.Data.DataSet> kullanılır.</span><span class="sxs-lookup"><span data-stu-id="757be-117">-   If the <xref:System.Data.DataSet> contains a schema or the XML contains an inline schema, **ReadSchema** is used.</span></span><br /><span data-ttu-id="757be-118">-Bir şema içermiyorsa ve XML bir satır içi şema içermiyorsa, **ınseschema kullanılır.** <xref:System.Data.DataSet></span><span class="sxs-lookup"><span data-stu-id="757be-118">-   If the <xref:System.Data.DataSet> does not contain a schema and the XML does not contain an inline schema, **InferSchema** is used.</span></span><br /><br /> <span data-ttu-id="757be-119">Okunan XML 'nin biçimini biliyorsanız, en iyi performans için **Otomatik** varsayılanı kabul etmek yerine açık bir **XmlReadMode**ayarlamanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="757be-119">If you know the format of the XML being read, for best performance it is recommended that you set an explicit **XmlReadMode**, rather than accept the **Auto** default.</span></span>|  
|<span data-ttu-id="757be-120">**ReadSchema**</span><span class="sxs-lookup"><span data-stu-id="757be-120">**ReadSchema**</span></span>|<span data-ttu-id="757be-121">Herhangi bir satır içi şemayı okur ve verileri ve şemayı yükler.</span><span class="sxs-lookup"><span data-stu-id="757be-121">Reads any inline schema and loads the data and schema.</span></span><br /><br /> <span data-ttu-id="757be-122">Zaten bir şema içeriyorsa, yeni tablolar satır içi şemadan <xref:System.Data.DataSet>içindeki mevcut şemaya eklenir. <xref:System.Data.DataSet></span><span class="sxs-lookup"><span data-stu-id="757be-122">If the <xref:System.Data.DataSet> already contains a schema, new tables are added from the inline schema to the existing schema in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="757be-123">Satır içi şemadaki herhangi bir tablo ' de <xref:System.Data.DataSet>zaten mevcutsa, bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="757be-123">If any tables in the inline schema already exist in the <xref:System.Data.DataSet>, an exception is thrown.</span></span> <span data-ttu-id="757be-124">**XmlReadMode. ReadSchema**kullanarak var olan bir tablonun şemasını değiştiremeyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="757be-124">You will not be able to modify the schema of an existing table using **XmlReadMode.ReadSchema**.</span></span><br /><br /> <span data-ttu-id="757be-125"><xref:System.Data.DataSet> Bir şema içermiyorsa ve satır içi şema yoksa, hiçbir veri okunamaz.</span><span class="sxs-lookup"><span data-stu-id="757be-125">If the <xref:System.Data.DataSet> does not contain a schema, and there is no inline schema, no data is read.</span></span><br /><br /> <span data-ttu-id="757be-126">Satır içi şema, XML şeması tanım dili (XSD) şeması kullanılarak tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="757be-126">Inline schema can be defined using XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="757be-127">Satır içi şemayı XML şeması olarak yazma hakkında daha fazla bilgi için bkz. [xml şemasından (xsd) DataSet Ilişkisel yapısını türetme](deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span><span class="sxs-lookup"><span data-stu-id="757be-127">For details about writing inline schema as XML Schema, see [Deriving DataSet Relational Structure from XML Schema (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span></span>|  
|<span data-ttu-id="757be-128">**IgnoreSchema**</span><span class="sxs-lookup"><span data-stu-id="757be-128">**IgnoreSchema**</span></span>|<span data-ttu-id="757be-129">Herhangi bir satır içi şemayı yoksayar ve verileri var olan <xref:System.Data.DataSet> şemaya yükler.</span><span class="sxs-lookup"><span data-stu-id="757be-129">Ignores any inline schema and loads the data into the existing <xref:System.Data.DataSet> schema.</span></span> <span data-ttu-id="757be-130">Varolan şemayla eşleşmeyen tüm veriler atılır.</span><span class="sxs-lookup"><span data-stu-id="757be-130">Any data that does not match the existing schema is discarded.</span></span> <span data-ttu-id="757be-131">İçinde hiçbir şema yoksa <xref:System.Data.DataSet>, hiçbir veri yüklenmez.</span><span class="sxs-lookup"><span data-stu-id="757be-131">If no schema exists in the <xref:System.Data.DataSet>, no data is loaded.</span></span><br /><br /> <span data-ttu-id="757be-132">Veriler bir DiffGram ise, **ıgnoreschema** **DiffGram** ile aynı işlevselliğe sahiptir *.*</span><span class="sxs-lookup"><span data-stu-id="757be-132">If the data is a DiffGram, **IgnoreSchema** has the same functionality as **DiffGram** *.*</span></span>|  
|<span data-ttu-id="757be-133">**Inseschema**</span><span class="sxs-lookup"><span data-stu-id="757be-133">**InferSchema**</span></span>|<span data-ttu-id="757be-134">Satır içi şemayı yoksayar ve XML verilerinin yapısına göre şemayı algılar, ardından verileri yükler.</span><span class="sxs-lookup"><span data-stu-id="757be-134">Ignores any inline schema and infers the schema per the structure of the XML data, then loads the data.</span></span><br /><br /> <span data-ttu-id="757be-135"><xref:System.Data.DataSet> Zaten bir şema içeriyorsa, geçerli şema varolan tablolara sütun eklenerek genişletilir.</span><span class="sxs-lookup"><span data-stu-id="757be-135">If the <xref:System.Data.DataSet> already contains a schema, the current schema is extended by adding columns to existing tables.</span></span> <span data-ttu-id="757be-136">Mevcut tablolar yoksa ek tablolar eklenmez.</span><span class="sxs-lookup"><span data-stu-id="757be-136">Extra tables will not be added if there are not existing tables.</span></span> <span data-ttu-id="757be-137">Başka bir ad alanı olan çıkartılan bir tablo zaten varsa veya herhangi bir çıkarılan sütun varolan sütunlarla çakışıyorsa, bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="757be-137">An exception is thrown if an inferred table already exists with a different namespace, or if any inferred columns conflict with existing columns.</span></span><br /><br /> <span data-ttu-id="757be-138">**ReadXmlSchema** 'ın bir XML belgesinden bir şemayı nasıl kullandığını öğrenmek için bkz. [XML 'Den veri kümesi ilişkisel yapısını](inferring-dataset-relational-structure-from-xml.md)anlamak.</span><span class="sxs-lookup"><span data-stu-id="757be-138">For details about how **ReadXmlSchema** infers a schema from an XML document, see [Inferring DataSet Relational Structure from XML](inferring-dataset-relational-structure-from-xml.md).</span></span>|  
|<span data-ttu-id="757be-139">**Içeriyor**</span><span class="sxs-lookup"><span data-stu-id="757be-139">**DiffGram**</span></span>|<span data-ttu-id="757be-140">Bir DiffGram okur ve verileri geçerli şemaya ekler.</span><span class="sxs-lookup"><span data-stu-id="757be-140">Reads a DiffGram and adds the data to the current schema.</span></span> <span data-ttu-id="757be-141">**DiffGram** , benzersiz tanımlayıcı değerlerinin eşleştiği varolan satırlarla yeni satırları birleştirir.</span><span class="sxs-lookup"><span data-stu-id="757be-141">**DiffGram** merges new rows with existing rows where the unique identifier values match.</span></span> <span data-ttu-id="757be-142">Bu konunun sonundaki "XML 'den veri birleştirme" konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="757be-142">See "Merging Data from XML" at the end of this topic.</span></span> <span data-ttu-id="757be-143">DiffGram hakkında daha fazla bilgi için bkz. [DiffGram](diffgrams.md).</span><span class="sxs-lookup"><span data-stu-id="757be-143">For more information about DiffGrams, see [DiffGrams](diffgrams.md).</span></span>|  
|<span data-ttu-id="757be-144">**Parçada**</span><span class="sxs-lookup"><span data-stu-id="757be-144">**Fragment**</span></span>|<span data-ttu-id="757be-145">Akışın sonuna ulaşılana kadar birden çok XML parçasının okunmasına devam eder.</span><span class="sxs-lookup"><span data-stu-id="757be-145">Continues reading multiple XML fragments until the end of the stream is reached.</span></span> <span data-ttu-id="757be-146"><xref:System.Data.DataSet> Şemayla eşleşen parçalar ilgili tablolara eklenir.</span><span class="sxs-lookup"><span data-stu-id="757be-146">Fragments that match the <xref:System.Data.DataSet> schema are appended to the appropriate tables.</span></span> <span data-ttu-id="757be-147"><xref:System.Data.DataSet> Şemayla eşleşmeyen parçalar atılır.</span><span class="sxs-lookup"><span data-stu-id="757be-147">Fragments that do not match the <xref:System.Data.DataSet> schema are discarded.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="757be-148">Bir XML belgesine yolunun bir parçası **olarak konumlandırılmış** bir XmlReader öğesine bir **XmlReader** geçirirseniz, **ReadXml** sonraki öğe düğümüne okur ve bunu yalnızca öğe düğümünün sonuna kadar okuyan kök öğe olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="757be-148">If you pass an **XmlReader** to **ReadXml** that is positioned part of the way into an XML document, **ReadXml** will read to the next element node and will treat that as the root element, reading until the end of the element node only.</span></span> <span data-ttu-id="757be-149">**XmlReadMode. Fragment**belirtirseniz bu uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="757be-149">This does not apply if you specify **XmlReadMode.Fragment**.</span></span>  
  
## <a name="dtd-entities"></a><span data-ttu-id="757be-150">DTD varlıkları</span><span class="sxs-lookup"><span data-stu-id="757be-150">DTD Entities</span></span>  
 <span data-ttu-id="757be-151">XML 'niz bir belge türü tanımı (DTD) şemasında tanımlanan varlıklar içeriyorsa, bir dosya adı, akış veya doğrulama olmayan **XmlReader** öğesini **ReadXml**öğesine geçirerek <xref:System.Data.DataSet> yüklemeyi denerseniz bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="757be-151">If your XML contains entities defined in a document type definition (DTD) schema, an exception will be thrown if you attempt to load a <xref:System.Data.DataSet> by passing a file name, stream, or non-validating **XmlReader** to **ReadXml**.</span></span> <span data-ttu-id="757be-152">Bunun yerine, **EntityHandling** 'U **EntityHandling. ExpandEntities**olarak ayarlayıp bir **XmlValidatingReader**oluşturmanız ve **XmlValidatingReader** 'ı **ReadXml**'e geçirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="757be-152">Instead, you must create an **XmlValidatingReader**, with **EntityHandling** set to **EntityHandling.ExpandEntities**, and pass your **XmlValidatingReader** to **ReadXml**.</span></span> <span data-ttu-id="757be-153">**XmlValidatingReader** , tarafından <xref:System.Data.DataSet>okunmadan önce varlıkları genişletir.</span><span class="sxs-lookup"><span data-stu-id="757be-153">The **XmlValidatingReader** will expand the entities prior to being read by the <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="757be-154">Aşağıdaki kod örnekleri, bir <xref:System.Data.DataSet> XML akışından nasıl yükleneceğini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="757be-154">The following code examples show how to load a <xref:System.Data.DataSet> from an XML stream.</span></span> <span data-ttu-id="757be-155">İlk örnekte, **ReadXml** yöntemine geçirilmiş bir dosya adı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="757be-155">The first example shows a file name being passed to the **ReadXml** method.</span></span> <span data-ttu-id="757be-156">İkinci örnek, kullanılarak <xref:System.IO.StringReader>yüklenen XML içeren bir dize gösterir.</span><span class="sxs-lookup"><span data-stu-id="757be-156">The second example shows a string that contains XML being loaded using a <xref:System.IO.StringReader>.</span></span>  
  
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
> <span data-ttu-id="757be-157">Çok büyük bir dosyayı yüklemek için **ReadXml** çağrısı yaparsanız, yavaş performansla karşılaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="757be-157">If you call **ReadXml** to load a very large file, you may encounter slow performance.</span></span> <span data-ttu-id="757be-158">**ReadXml**için en iyi performansı sağlamak üzere, büyük bir dosyada, içindeki <xref:System.Data.DataTable.BeginLoadData%2A> <xref:System.Data.DataSet>her tablo için yöntemini çağırın ve ardından **ReadXml**öğesini çağırın.</span><span class="sxs-lookup"><span data-stu-id="757be-158">To ensure best performance for **ReadXml**, on a large file, call the <xref:System.Data.DataTable.BeginLoadData%2A> method for each table in the <xref:System.Data.DataSet>, and then call **ReadXml**.</span></span> <span data-ttu-id="757be-159">Son olarak, <xref:System.Data.DataTable.EndLoadData%2A> aşağıdaki örnekte gösterildiği gibi, <xref:System.Data.DataSet>içindeki her tablo için öğesini çağırın.</span><span class="sxs-lookup"><span data-stu-id="757be-159">Finally, call <xref:System.Data.DataTable.EndLoadData%2A> for each table in the <xref:System.Data.DataSet>, as shown in the following example.</span></span>  
  
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
> <span data-ttu-id="757be-160">İçin <xref:System.Data.DataSet> xsd şeması bir **targetNamespace**içeriyorsa, veriler okunmayabilir ve uygun bir ad alanı olmayan öğeleri içeren XML <xref:System.Data.DataSet> ile yüklemek için **ReadXml** çağrılırken özel durumlarla karşılaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="757be-160">If the XSD schema for your <xref:System.Data.DataSet> includes a **targetNamespace**, data may not be read, and you may encounter exceptions, when calling **ReadXml** to load the <xref:System.Data.DataSet> with XML that contains elements with no qualifying namespace.</span></span> <span data-ttu-id="757be-161">Bu durumda nitelenmemiş öğeleri okumak için, XSD şemanızda **elementFormDefault** eşittir "Qualified" olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="757be-161">To read unqualified elements in this case, set **elementFormDefault** equal to "qualified" in your XSD schema.</span></span> <span data-ttu-id="757be-162">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="757be-162">For example:</span></span>  
  
```xml  
<xsd:schema id="customDataSet"   
  elementFormDefault="qualified"  
  targetNamespace="http://www.tempuri.org/customDataSet.xsd"   
  xmlns="http://www.tempuri.org/customDataSet.xsd"   
  xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
  xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
</xsd:schema>  
```  
  
## <a name="merging-data-from-xml"></a><span data-ttu-id="757be-163">XML 'den veri birleştirme</span><span class="sxs-lookup"><span data-stu-id="757be-163">Merging Data from XML</span></span>  
 <span data-ttu-id="757be-164">Zaten veri içeriyorsa, XML 'deki yeni veriler, <xref:System.Data.DataSet>içinde zaten mevcut olan verilere eklenir. <xref:System.Data.DataSet></span><span class="sxs-lookup"><span data-stu-id="757be-164">If the <xref:System.Data.DataSet> already contains data, the new data from the XML is added to the data already present in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="757be-165">**ReadXml** , XML <xref:System.Data.DataSet> 'den eşleşen birincil anahtarlarla satır bilgileriyle birleştirme yapmaz.</span><span class="sxs-lookup"><span data-stu-id="757be-165">**ReadXml** does not merge from the XML into the <xref:System.Data.DataSet> any row information with matching primary keys.</span></span> <span data-ttu-id="757be-166">XML 'deki yeni bilgilerle mevcut satır bilgilerinin üzerine yazmak için, **ReadXml** kullanarak yeni <xref:System.Data.DataSet>bir <xref:System.Data.DataSet> ve <xref:System.Data.DataSet.Merge%2A> <xref:System.Data.DataSet>yeni bir oluşturma yapın.</span><span class="sxs-lookup"><span data-stu-id="757be-166">To overwrite existing row information with new information from XML, use **ReadXml** to create a new <xref:System.Data.DataSet>, and then <xref:System.Data.DataSet.Merge%2A> the new <xref:System.Data.DataSet> into the existing <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="757be-167">**DiffGram bir** **XmlReadMode** Ile **ReadXml** kullanarak bir DiffGram yüklemenin aynı benzersiz tanımlayıcıya sahip satırları birleştirdiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="757be-167">Note that loading a DiffGram using **ReadXML** with an **XmlReadMode** of **DiffGram** will merge rows that have the same unique identifier.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="757be-168">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="757be-168">See also</span></span>

- <xref:System.Data.DataSet.Merge%2A?displayProperty=nameWithType>
- [<span data-ttu-id="757be-169">DataSet içinde XML kullanma</span><span class="sxs-lookup"><span data-stu-id="757be-169">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="757be-170">DiffGrams</span><span class="sxs-lookup"><span data-stu-id="757be-170">DiffGrams</span></span>](diffgrams.md)
- [<span data-ttu-id="757be-171">XML Şemasından (XSD) DataSet İlişkisel Yapısını Türetme</span><span class="sxs-lookup"><span data-stu-id="757be-171">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [<span data-ttu-id="757be-172">XML’den DataSet İlişkisel Yapısını Çıkarma</span><span class="sxs-lookup"><span data-stu-id="757be-172">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="757be-173">XML’den DataSet Schema Bilgilerini Yükleme</span><span class="sxs-lookup"><span data-stu-id="757be-173">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="757be-174">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="757be-174">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="757be-175">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="757be-175">ADO.NET Overview</span></span>](../ado-net-overview.md)
