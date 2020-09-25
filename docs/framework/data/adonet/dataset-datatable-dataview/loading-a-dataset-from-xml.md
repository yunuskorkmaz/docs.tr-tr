---
title: XML’den DataSet Yükleme
description: XML 'den bir ADO.NET veri kümesine içerik eklemeyi öğrenin. .NET Framework, yükleme ve veri kümesinin yapısına yönelik esneklik sunar.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49c083b7-a5ed-41cf-aabc-5aaba96f00e6
ms.openlocfilehash: 0920acac2c82677cfce37703b7027dedce91a535
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166813"
---
# <a name="loading-a-dataset-from-xml"></a><span data-ttu-id="7d7f6-104">XML’den DataSet Yükleme</span><span class="sxs-lookup"><span data-stu-id="7d7f6-104">Loading a DataSet from XML</span></span>

<span data-ttu-id="7d7f6-105">Bir ADO.NET içeriği <xref:System.Data.DataSet> BIR XML akışından veya belgesinden oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="7d7f6-105">The contents of an ADO.NET <xref:System.Data.DataSet> can be created from an XML stream or document.</span></span> <span data-ttu-id="7d7f6-106">Ayrıca .NET Framework, XML 'den hangi bilgilerin yüklendiği ve şema ya da ilişkisel yapısının nasıl oluşturulduğuna ilişkin büyük bir esnekliğe sahip olursunuz <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="7d7f6-106">In addition, with the .NET Framework you have great flexibility over what information is loaded from XML, and how the schema or relational structure of the <xref:System.Data.DataSet> is created.</span></span>  
  
 <span data-ttu-id="7d7f6-107"><xref:System.Data.DataSet>XML 'deki verileri bir ile doldurmanız için nesnenin **ReadXml** yöntemini kullanın <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="7d7f6-107">To fill a <xref:System.Data.DataSet> with data from XML, use the **ReadXml** method of the <xref:System.Data.DataSet> object.</span></span> <span data-ttu-id="7d7f6-108">**ReadXml** yöntemi bir dosyadan, akıştan veya bir **XmlReader**'dan yararlanır ve XML kaynağı Ile Isteğe bağlı bir **XmlReadMode** bağımsız değişkeni olarak bağımsız değişken alır.</span><span class="sxs-lookup"><span data-stu-id="7d7f6-108">The **ReadXml** method reads from a file, a stream, or an **XmlReader**, and takes as arguments the source of the XML plus an optional **XmlReadMode** argument.</span></span> <span data-ttu-id="7d7f6-109">**XmlReader**hakkında daha fazla bilgi için bkz. [XML verilerini XmlTextReader ile okuma](/previous-versions/dotnet/netframework-4.0/tfz3cz6w(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="7d7f6-109">For more information about the **XmlReader**, see [Reading XML Data with XmlTextReader](/previous-versions/dotnet/netframework-4.0/tfz3cz6w(v=vs.100)).</span></span> <span data-ttu-id="7d7f6-110">**ReadXml** YÖNTEMI, XML akışı veya belgesinin içeriğini okur ve <xref:System.Data.DataSet> ile verileri yükler.</span><span class="sxs-lookup"><span data-stu-id="7d7f6-110">The **ReadXml** method reads the contents of the XML stream or document and loads the <xref:System.Data.DataSet> with data.</span></span> <span data-ttu-id="7d7f6-111">Ayrıca, <xref:System.Data.DataSet> belirtilen **XmlReadMode** öğesine ve ilişkisel bir şemanın zaten mevcut olup olmadığına bağlı olarak ilişkisel şeması da oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7d7f6-111">It will also create the relational schema of the <xref:System.Data.DataSet> depending on the **XmlReadMode** specified and whether or not a relational schema already exists.</span></span>  
  
 <span data-ttu-id="7d7f6-112">Aşağıdaki tabloda **XmlReadMode** bağımsız değişkeninin seçenekleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7d7f6-112">The following table describes the options for the **XmlReadMode** argument.</span></span>  
  
|<span data-ttu-id="7d7f6-113">Seçenek</span><span class="sxs-lookup"><span data-stu-id="7d7f6-113">Option</span></span>|<span data-ttu-id="7d7f6-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7d7f6-114">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="7d7f6-115">**Otomatik**</span><span class="sxs-lookup"><span data-stu-id="7d7f6-115">**Auto**</span></span>|<span data-ttu-id="7d7f6-116">Bu varsayılan seçenektir.</span><span class="sxs-lookup"><span data-stu-id="7d7f6-116">This is the default.</span></span> <span data-ttu-id="7d7f6-117">XML 'i inceler ve aşağıdaki sırada en uygun seçeneği seçer:</span><span class="sxs-lookup"><span data-stu-id="7d7f6-117">Examines the XML and chooses the most appropriate option in the following order:</span></span><br /><br /> <span data-ttu-id="7d7f6-118">-XML bir DiffGram ise, **DiffGram** kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7d7f6-118">-   If the XML is a DiffGram, **DiffGram** is used.</span></span><br /><span data-ttu-id="7d7f6-119">- <xref:System.Data.DataSet> Bir şema içeriyorsa veya XML bir satır içi şema Içeriyorsa **ReadSchema** kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7d7f6-119">-   If the <xref:System.Data.DataSet> contains a schema or the XML contains an inline schema, **ReadSchema** is used.</span></span><br /><span data-ttu-id="7d7f6-120">- <xref:System.Data.DataSet> Bir şema içermiyorsa ve XML bir satır içi şema içermiyorsa, **ınseschema** kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7d7f6-120">-   If the <xref:System.Data.DataSet> does not contain a schema and the XML does not contain an inline schema, **InferSchema** is used.</span></span><br /><br /> <span data-ttu-id="7d7f6-121">Okunan XML 'nin biçimini biliyorsanız, en iyi performans için **Otomatik** varsayılanı kabul etmek yerine açık bir **XmlReadMode**ayarlamanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="7d7f6-121">If you know the format of the XML being read, for best performance it is recommended that you set an explicit **XmlReadMode**, rather than accept the **Auto** default.</span></span>|  
|<span data-ttu-id="7d7f6-122">**ReadSchema**</span><span class="sxs-lookup"><span data-stu-id="7d7f6-122">**ReadSchema**</span></span>|<span data-ttu-id="7d7f6-123">Herhangi bir satır içi şemayı okur ve verileri ve şemayı yükler.</span><span class="sxs-lookup"><span data-stu-id="7d7f6-123">Reads any inline schema and loads the data and schema.</span></span><br /><br /> <span data-ttu-id="7d7f6-124"><xref:System.Data.DataSet>Zaten bir şema içeriyorsa, yeni tablolar satır içi şemadan içindeki mevcut şemaya eklenir <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="7d7f6-124">If the <xref:System.Data.DataSet> already contains a schema, new tables are added from the inline schema to the existing schema in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="7d7f6-125">Satır içi şemadaki herhangi bir tablo ' de zaten mevcutsa <xref:System.Data.DataSet> , bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="7d7f6-125">If any tables in the inline schema already exist in the <xref:System.Data.DataSet>, an exception is thrown.</span></span> <span data-ttu-id="7d7f6-126">**XmlReadMode. ReadSchema**kullanarak var olan bir tablonun şemasını değiştiremeyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="7d7f6-126">You will not be able to modify the schema of an existing table using **XmlReadMode.ReadSchema**.</span></span><br /><br /> <span data-ttu-id="7d7f6-127"><xref:System.Data.DataSet>Bir şema içermiyorsa ve satır içi şema yoksa, hiçbir veri okunamaz.</span><span class="sxs-lookup"><span data-stu-id="7d7f6-127">If the <xref:System.Data.DataSet> does not contain a schema, and there is no inline schema, no data is read.</span></span><br /><br /> <span data-ttu-id="7d7f6-128">Satır içi şema, XML şeması tanım dili (XSD) şeması kullanılarak tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="7d7f6-128">Inline schema can be defined using XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="7d7f6-129">Satır içi şemayı XML şeması olarak yazma hakkında daha fazla bilgi için bkz. [xml şemasından (xsd) DataSet Ilişkisel yapısını türetme](deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span><span class="sxs-lookup"><span data-stu-id="7d7f6-129">For details about writing inline schema as XML Schema, see [Deriving DataSet Relational Structure from XML Schema (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span></span>|  
|<span data-ttu-id="7d7f6-130">**IgnoreSchema**</span><span class="sxs-lookup"><span data-stu-id="7d7f6-130">**IgnoreSchema**</span></span>|<span data-ttu-id="7d7f6-131">Herhangi bir satır içi şemayı yoksayar ve verileri var olan <xref:System.Data.DataSet> şemaya yükler.</span><span class="sxs-lookup"><span data-stu-id="7d7f6-131">Ignores any inline schema and loads the data into the existing <xref:System.Data.DataSet> schema.</span></span> <span data-ttu-id="7d7f6-132">Varolan şemayla eşleşmeyen tüm veriler atılır.</span><span class="sxs-lookup"><span data-stu-id="7d7f6-132">Any data that does not match the existing schema is discarded.</span></span> <span data-ttu-id="7d7f6-133">İçinde hiçbir şema yoksa <xref:System.Data.DataSet> , hiçbir veri yüklenmez.</span><span class="sxs-lookup"><span data-stu-id="7d7f6-133">If no schema exists in the <xref:System.Data.DataSet>, no data is loaded.</span></span><br /><br /> <span data-ttu-id="7d7f6-134">Veriler bir DiffGram ise, **ıgnoreschema** **DiffGram** ile aynı işlevselliğe sahiptir *.*</span><span class="sxs-lookup"><span data-stu-id="7d7f6-134">If the data is a DiffGram, **IgnoreSchema** has the same functionality as **DiffGram** *.*</span></span>|  
|<span data-ttu-id="7d7f6-135">**Inseschema**</span><span class="sxs-lookup"><span data-stu-id="7d7f6-135">**InferSchema**</span></span>|<span data-ttu-id="7d7f6-136">Satır içi şemayı yoksayar ve XML verilerinin yapısına göre şemayı algılar, ardından verileri yükler.</span><span class="sxs-lookup"><span data-stu-id="7d7f6-136">Ignores any inline schema and infers the schema per the structure of the XML data, then loads the data.</span></span><br /><br /> <span data-ttu-id="7d7f6-137"><xref:System.Data.DataSet>Zaten bir şema içeriyorsa, geçerli şema varolan tablolara sütun eklenerek genişletilir.</span><span class="sxs-lookup"><span data-stu-id="7d7f6-137">If the <xref:System.Data.DataSet> already contains a schema, the current schema is extended by adding columns to existing tables.</span></span> <span data-ttu-id="7d7f6-138">Mevcut tablolar yoksa ek tablolar eklenmez.</span><span class="sxs-lookup"><span data-stu-id="7d7f6-138">Extra tables will not be added if there are not existing tables.</span></span> <span data-ttu-id="7d7f6-139">Başka bir ad alanı olan çıkartılan bir tablo zaten varsa veya herhangi bir çıkarılan sütun varolan sütunlarla çakışıyorsa, bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="7d7f6-139">An exception is thrown if an inferred table already exists with a different namespace, or if any inferred columns conflict with existing columns.</span></span><br /><br /> <span data-ttu-id="7d7f6-140">**ReadXmlSchema** 'ın bir XML belgesinden bir şemayı nasıl kullandığını öğrenmek için bkz. [XML 'Den veri kümesi ilişkisel yapısını](inferring-dataset-relational-structure-from-xml.md)anlamak.</span><span class="sxs-lookup"><span data-stu-id="7d7f6-140">For details about how **ReadXmlSchema** infers a schema from an XML document, see [Inferring DataSet Relational Structure from XML](inferring-dataset-relational-structure-from-xml.md).</span></span>|  
|<span data-ttu-id="7d7f6-141">**Içeriyor**</span><span class="sxs-lookup"><span data-stu-id="7d7f6-141">**DiffGram**</span></span>|<span data-ttu-id="7d7f6-142">Bir DiffGram okur ve verileri geçerli şemaya ekler.</span><span class="sxs-lookup"><span data-stu-id="7d7f6-142">Reads a DiffGram and adds the data to the current schema.</span></span> <span data-ttu-id="7d7f6-143">**DiffGram** , benzersiz tanımlayıcı değerlerinin eşleştiği varolan satırlarla yeni satırları birleştirir.</span><span class="sxs-lookup"><span data-stu-id="7d7f6-143">**DiffGram** merges new rows with existing rows where the unique identifier values match.</span></span> <span data-ttu-id="7d7f6-144">Bu konunun sonundaki "XML 'den veri birleştirme" konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="7d7f6-144">See "Merging Data from XML" at the end of this topic.</span></span> <span data-ttu-id="7d7f6-145">DiffGram hakkında daha fazla bilgi için bkz. [DiffGram](diffgrams.md).</span><span class="sxs-lookup"><span data-stu-id="7d7f6-145">For more information about DiffGrams, see [DiffGrams](diffgrams.md).</span></span>|  
|<span data-ttu-id="7d7f6-146">**Parça**</span><span class="sxs-lookup"><span data-stu-id="7d7f6-146">**Fragment**</span></span>|<span data-ttu-id="7d7f6-147">Akışın sonuna ulaşılana kadar birden çok XML parçasının okunmasına devam eder.</span><span class="sxs-lookup"><span data-stu-id="7d7f6-147">Continues reading multiple XML fragments until the end of the stream is reached.</span></span> <span data-ttu-id="7d7f6-148">Şemayla eşleşen parçalar <xref:System.Data.DataSet> ilgili tablolara eklenir.</span><span class="sxs-lookup"><span data-stu-id="7d7f6-148">Fragments that match the <xref:System.Data.DataSet> schema are appended to the appropriate tables.</span></span> <span data-ttu-id="7d7f6-149">Şemayla eşleşmeyen parçalar <xref:System.Data.DataSet> atılır.</span><span class="sxs-lookup"><span data-stu-id="7d7f6-149">Fragments that do not match the <xref:System.Data.DataSet> schema are discarded.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="7d7f6-150">Bir XML belgesine yolunun bir parçası **olarak konumlandırılmış** bir XmlReader öğesine bir **XmlReader** geçirirseniz, **ReadXml** sonraki öğe düğümüne okur ve bunu yalnızca öğe düğümünün sonuna kadar okuyan kök öğe olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="7d7f6-150">If you pass an **XmlReader** to **ReadXml** that is positioned part of the way into an XML document, **ReadXml** will read to the next element node and will treat that as the root element, reading until the end of the element node only.</span></span> <span data-ttu-id="7d7f6-151">**XmlReadMode. Fragment**belirtirseniz bu uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="7d7f6-151">This does not apply if you specify **XmlReadMode.Fragment**.</span></span>  
  
## <a name="dtd-entities"></a><span data-ttu-id="7d7f6-152">DTD varlıkları</span><span class="sxs-lookup"><span data-stu-id="7d7f6-152">DTD Entities</span></span>  

 <span data-ttu-id="7d7f6-153">XML 'niz bir belge türü tanımı (DTD) şemasında tanımlanan varlıklar içeriyorsa, bir <xref:System.Data.DataSet> dosya adı, akış veya doğrulama olmayan **XmlReader** öğesini **ReadXml**öğesine geçirerek yüklemeyi denerseniz bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="7d7f6-153">If your XML contains entities defined in a document type definition (DTD) schema, an exception will be thrown if you attempt to load a <xref:System.Data.DataSet> by passing a file name, stream, or non-validating **XmlReader** to **ReadXml**.</span></span> <span data-ttu-id="7d7f6-154">Bunun yerine, **EntityHandling** 'U **EntityHandling. ExpandEntities**olarak ayarlayıp bir **XmlValidatingReader**oluşturmanız ve **XmlValidatingReader** 'ı **ReadXml**'e geçirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="7d7f6-154">Instead, you must create an **XmlValidatingReader**, with **EntityHandling** set to **EntityHandling.ExpandEntities**, and pass your **XmlValidatingReader** to **ReadXml**.</span></span> <span data-ttu-id="7d7f6-155">**XmlValidatingReader** , tarafından okunmadan önce varlıkları genişletir <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="7d7f6-155">The **XmlValidatingReader** will expand the entities prior to being read by the <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="7d7f6-156">Aşağıdaki kod örnekleri, bir XML akışından nasıl yükleneceğini göstermektedir <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="7d7f6-156">The following code examples show how to load a <xref:System.Data.DataSet> from an XML stream.</span></span> <span data-ttu-id="7d7f6-157">İlk örnekte, **ReadXml** yöntemine geçirilmiş bir dosya adı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7d7f6-157">The first example shows a file name being passed to the **ReadXml** method.</span></span> <span data-ttu-id="7d7f6-158">İkinci örnek, kullanılarak yüklenen XML içeren bir dize gösterir <xref:System.IO.StringReader> .</span><span class="sxs-lookup"><span data-stu-id="7d7f6-158">The second example shows a string that contains XML being loaded using a <xref:System.IO.StringReader>.</span></span>  
  
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
> <span data-ttu-id="7d7f6-159">Çok büyük bir dosyayı yüklemek için **ReadXml** çağrısı yaparsanız, yavaş performansla karşılaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7d7f6-159">If you call **ReadXml** to load a very large file, you may encounter slow performance.</span></span> <span data-ttu-id="7d7f6-160">**ReadXml**için en iyi performansı sağlamak üzere, büyük bir dosyada, <xref:System.Data.DataTable.BeginLoadData%2A> içindeki her tablo için yöntemini çağırın <xref:System.Data.DataSet> ve ardından **ReadXml**öğesini çağırın.</span><span class="sxs-lookup"><span data-stu-id="7d7f6-160">To ensure best performance for **ReadXml**, on a large file, call the <xref:System.Data.DataTable.BeginLoadData%2A> method for each table in the <xref:System.Data.DataSet>, and then call **ReadXml**.</span></span> <span data-ttu-id="7d7f6-161">Son olarak, <xref:System.Data.DataTable.EndLoadData%2A> Aşağıdaki örnekte gösterildiği gibi, içindeki her tablo için öğesini çağırın <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="7d7f6-161">Finally, call <xref:System.Data.DataTable.EndLoadData%2A> for each table in the <xref:System.Data.DataSet>, as shown in the following example.</span></span>  
  
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
> <span data-ttu-id="7d7f6-162">İçin XSD şeması <xref:System.Data.DataSet> bir **targetNamespace**içeriyorsa, veriler okunmayabilir ve uygun bir **ReadXml** <xref:System.Data.DataSet> ad alanı olmayan öğeleri içeren XML ile yüklemek için ReadXml çağrılırken özel durumlarla karşılaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7d7f6-162">If the XSD schema for your <xref:System.Data.DataSet> includes a **targetNamespace**, data may not be read, and you may encounter exceptions, when calling **ReadXml** to load the <xref:System.Data.DataSet> with XML that contains elements with no qualifying namespace.</span></span> <span data-ttu-id="7d7f6-163">Bu durumda nitelenmemiş öğeleri okumak için, XSD şemanızda **elementFormDefault** eşittir "Qualified" olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="7d7f6-163">To read unqualified elements in this case, set **elementFormDefault** equal to "qualified" in your XSD schema.</span></span> <span data-ttu-id="7d7f6-164">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="7d7f6-164">For example:</span></span>  
  
```xml  
<xsd:schema id="customDataSet"
  elementFormDefault="qualified"  
  targetNamespace="http://www.tempuri.org/customDataSet.xsd"
  xmlns="http://www.tempuri.org/customDataSet.xsd"
  xmlns:xsd="http://www.w3.org/2001/XMLSchema"
  xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
</xsd:schema>  
```  
  
## <a name="merging-data-from-xml"></a><span data-ttu-id="7d7f6-165">XML 'den veri birleştirme</span><span class="sxs-lookup"><span data-stu-id="7d7f6-165">Merging Data from XML</span></span>  

 <span data-ttu-id="7d7f6-166"><xref:System.Data.DataSet>Zaten veri içeriyorsa, XML 'deki yeni veriler, içinde zaten mevcut olan verilere eklenir <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="7d7f6-166">If the <xref:System.Data.DataSet> already contains data, the new data from the XML is added to the data already present in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="7d7f6-167">**ReadXml** , XML 'den <xref:System.Data.DataSet> eşleşen birincil anahtarlarla satır bilgileriyle birleştirme yapmaz.</span><span class="sxs-lookup"><span data-stu-id="7d7f6-167">**ReadXml** does not merge from the XML into the <xref:System.Data.DataSet> any row information with matching primary keys.</span></span> <span data-ttu-id="7d7f6-168">XML 'deki yeni bilgilerle mevcut satır bilgilerinin üzerine yazmak için, **ReadXml** kullanarak yeni bir ve yeni bir oluşturma <xref:System.Data.DataSet> yapın <xref:System.Data.DataSet.Merge%2A> <xref:System.Data.DataSet> <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="7d7f6-168">To overwrite existing row information with new information from XML, use **ReadXml** to create a new <xref:System.Data.DataSet>, and then <xref:System.Data.DataSet.Merge%2A> the new <xref:System.Data.DataSet> into the existing <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="7d7f6-169">**DiffGram bir** **XmlReadMode** Ile **ReadXml** kullanarak bir DiffGram yüklemenin aynı benzersiz tanımlayıcıya sahip satırları birleştirdiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="7d7f6-169">Note that loading a DiffGram using **ReadXML** with an **XmlReadMode** of **DiffGram** will merge rows that have the same unique identifier.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d7f6-170">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7d7f6-170">See also</span></span>

- <xref:System.Data.DataSet.Merge%2A?displayProperty=nameWithType>
- [<span data-ttu-id="7d7f6-171">DataSet içinde XML kullanma</span><span class="sxs-lookup"><span data-stu-id="7d7f6-171">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="7d7f6-172">DiffGrams</span><span class="sxs-lookup"><span data-stu-id="7d7f6-172">DiffGrams</span></span>](diffgrams.md)
- [<span data-ttu-id="7d7f6-173">XML Şemasından (XSD) DataSet İlişkisel Yapısını Türetme</span><span class="sxs-lookup"><span data-stu-id="7d7f6-173">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [<span data-ttu-id="7d7f6-174">XML’den DataSet İlişkisel Yapısını Çıkarma</span><span class="sxs-lookup"><span data-stu-id="7d7f6-174">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="7d7f6-175">XML’den DataSet Schema Bilgilerini Yükleme</span><span class="sxs-lookup"><span data-stu-id="7d7f6-175">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="7d7f6-176">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="7d7f6-176">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="7d7f6-177">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="7d7f6-177">ADO.NET Overview</span></span>](../ado-net-overview.md)
