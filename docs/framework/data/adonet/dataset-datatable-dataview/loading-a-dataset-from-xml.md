---
title: XML’den DataSet Yükleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49c083b7-a5ed-41cf-aabc-5aaba96f00e6
ms.openlocfilehash: c21ed3bb31add285d64272040680433fff4e16fd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151071"
---
# <a name="loading-a-dataset-from-xml"></a><span data-ttu-id="8b5af-102">XML’den DataSet Yükleme</span><span class="sxs-lookup"><span data-stu-id="8b5af-102">Loading a DataSet from XML</span></span>
<span data-ttu-id="8b5af-103">Bir ADO.NET <xref:System.Data.DataSet> içeriği bir XML akışından veya belgeden oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="8b5af-103">The contents of an ADO.NET <xref:System.Data.DataSet> can be created from an XML stream or document.</span></span> <span data-ttu-id="8b5af-104">Buna ek olarak, .NET Framework ile XML'den hangi bilgilerin yüklendiği ve şema veya ilişkisel yapının <xref:System.Data.DataSet> nasıl oluşturulduğu konusunda büyük bir esnekliğe sahipsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b5af-104">In addition, with the .NET Framework you have great flexibility over what information is loaded from XML, and how the schema or relational structure of the <xref:System.Data.DataSet> is created.</span></span>  
  
 <span data-ttu-id="8b5af-105">XML'den gelen <xref:System.Data.DataSet> verilerle doldurmak için nesnenin <xref:System.Data.DataSet> **ReadXml** yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="8b5af-105">To fill a <xref:System.Data.DataSet> with data from XML, use the **ReadXml** method of the <xref:System.Data.DataSet> object.</span></span> <span data-ttu-id="8b5af-106">**ReadXml** yöntemi bir dosya, bir akış veya **XmlReader**okur ve bağımsız değişkenler XML artı isteğe bağlı **XmlReadMode** bağımsız değişken kaynağı olarak alır.</span><span class="sxs-lookup"><span data-stu-id="8b5af-106">The **ReadXml** method reads from a file, a stream, or an **XmlReader**, and takes as arguments the source of the XML plus an optional **XmlReadMode** argument.</span></span> <span data-ttu-id="8b5af-107">**XmlReader**hakkında daha fazla bilgi için, [XmlTextReader ile XML Veri Okuma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/tfz3cz6w(v=vs.100))bakın.</span><span class="sxs-lookup"><span data-stu-id="8b5af-107">For more information about the **XmlReader**, see [Reading XML Data with XmlTextReader](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/tfz3cz6w(v=vs.100)).</span></span> <span data-ttu-id="8b5af-108">**ReadXml** yöntemi XML akışının veya belgenin içeriğini <xref:System.Data.DataSet> okur ve verileri yükler.</span><span class="sxs-lookup"><span data-stu-id="8b5af-108">The **ReadXml** method reads the contents of the XML stream or document and loads the <xref:System.Data.DataSet> with data.</span></span> <span data-ttu-id="8b5af-109">Ayrıca <xref:System.Data.DataSet> **xmlReadMode** belirtilen bağlı olarak ilişkisel şema yaratacak ve bir ilişkisel şema zaten var olup olmadığını.</span><span class="sxs-lookup"><span data-stu-id="8b5af-109">It will also create the relational schema of the <xref:System.Data.DataSet> depending on the **XmlReadMode** specified and whether or not a relational schema already exists.</span></span>  
  
 <span data-ttu-id="8b5af-110">Aşağıdaki tabloda **XmlReadMode** bağımsız değişkeni için seçenekler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8b5af-110">The following table describes the options for the **XmlReadMode** argument.</span></span>  
  
|<span data-ttu-id="8b5af-111">Seçenek</span><span class="sxs-lookup"><span data-stu-id="8b5af-111">Option</span></span>|<span data-ttu-id="8b5af-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8b5af-112">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="8b5af-113">**Otomatik**</span><span class="sxs-lookup"><span data-stu-id="8b5af-113">**Auto**</span></span>|<span data-ttu-id="8b5af-114">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="8b5af-114">This is the default.</span></span> <span data-ttu-id="8b5af-115">XML'i inceler ve aşağıdaki sırada en uygun seçeneği seçer:</span><span class="sxs-lookup"><span data-stu-id="8b5af-115">Examines the XML and chooses the most appropriate option in the following order:</span></span><br /><br /> <span data-ttu-id="8b5af-116">- XML diffgram ise **DiffGram** kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8b5af-116">-   If the XML is a DiffGram, **DiffGram** is used.</span></span><br /><span data-ttu-id="8b5af-117">- Bir <xref:System.Data.DataSet> şema içeriyorsa veya XML satır içi şema içeriyorsa, **ReadSchema** kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8b5af-117">-   If the <xref:System.Data.DataSet> contains a schema or the XML contains an inline schema, **ReadSchema** is used.</span></span><br /><span data-ttu-id="8b5af-118">- Şema <xref:System.Data.DataSet> içermiyorsa ve XML satır içi şema içermiyorsa, **InferSchema** kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8b5af-118">-   If the <xref:System.Data.DataSet> does not contain a schema and the XML does not contain an inline schema, **InferSchema** is used.</span></span><br /><br /> <span data-ttu-id="8b5af-119">XML'in okunan biçimini biliyorsanız, en iyi performans için **Otomatik** varsayılanı kabul etmek yerine açık bir **XmlReadMode**ayarlamanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="8b5af-119">If you know the format of the XML being read, for best performance it is recommended that you set an explicit **XmlReadMode**, rather than accept the **Auto** default.</span></span>|  
|<span data-ttu-id="8b5af-120">**Okuma Skeci**</span><span class="sxs-lookup"><span data-stu-id="8b5af-120">**ReadSchema**</span></span>|<span data-ttu-id="8b5af-121">Herhangi bir satır lı şema okur ve veri ve şema yükler.</span><span class="sxs-lookup"><span data-stu-id="8b5af-121">Reads any inline schema and loads the data and schema.</span></span><br /><br /> <span data-ttu-id="8b5af-122"><xref:System.Data.DataSet> Zaten bir şema içeriyorsa, satır satır şemasından varolan şemaya yeni <xref:System.Data.DataSet>tablolar eklenir.</span><span class="sxs-lookup"><span data-stu-id="8b5af-122">If the <xref:System.Data.DataSet> already contains a schema, new tables are added from the inline schema to the existing schema in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="8b5af-123">Satır satırşeşemasında herhangi bir tablo zaten <xref:System.Data.DataSet>varsa, bir özel durum atılır.</span><span class="sxs-lookup"><span data-stu-id="8b5af-123">If any tables in the inline schema already exist in the <xref:System.Data.DataSet>, an exception is thrown.</span></span> <span data-ttu-id="8b5af-124">**XmlReadMode.ReadSchema**kullanarak varolan bir tablonun şemasını değiştiremeyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="8b5af-124">You will not be able to modify the schema of an existing table using **XmlReadMode.ReadSchema**.</span></span><br /><br /> <span data-ttu-id="8b5af-125">Şema <xref:System.Data.DataSet> içermiyorsa ve satır satır şeması yoksa, veri okunmaz.</span><span class="sxs-lookup"><span data-stu-id="8b5af-125">If the <xref:System.Data.DataSet> does not contain a schema, and there is no inline schema, no data is read.</span></span><br /><br /> <span data-ttu-id="8b5af-126">Satır çizgisi şema XML Şema tanım dili (XSD) şeması kullanılarak tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="8b5af-126">Inline schema can be defined using XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="8b5af-127">XML Şema olarak satır içinde şema yazma hakkında ayrıntılı bilgi için, [XML Schema (XSD) gelen Veri Seti İlişkisel Yapısı Türetilmesi](deriving-dataset-relational-structure-from-xml-schema-xsd.md)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="8b5af-127">For details about writing inline schema as XML Schema, see [Deriving DataSet Relational Structure from XML Schema (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span></span>|  
|<span data-ttu-id="8b5af-128">**Schema'yı Yok Sayma**</span><span class="sxs-lookup"><span data-stu-id="8b5af-128">**IgnoreSchema**</span></span>|<span data-ttu-id="8b5af-129">Herhangi bir satır dışı şema yoksa <xref:System.Data.DataSet> ve verileri varolan şema içine yükler.</span><span class="sxs-lookup"><span data-stu-id="8b5af-129">Ignores any inline schema and loads the data into the existing <xref:System.Data.DataSet> schema.</span></span> <span data-ttu-id="8b5af-130">Varolan şemaya uymayan tüm veriler atılır.</span><span class="sxs-lookup"><span data-stu-id="8b5af-130">Any data that does not match the existing schema is discarded.</span></span> <span data-ttu-id="8b5af-131">Hiçbir şema <xref:System.Data.DataSet>varsa, hiçbir veri yüklenir.</span><span class="sxs-lookup"><span data-stu-id="8b5af-131">If no schema exists in the <xref:System.Data.DataSet>, no data is loaded.</span></span><br /><br /> <span data-ttu-id="8b5af-132">Veriler Bir DiffGram ise, **YokSaysşek** **DiffGram** ile aynı işlevsellik *vardır.*</span><span class="sxs-lookup"><span data-stu-id="8b5af-132">If the data is a DiffGram, **IgnoreSchema** has the same functionality as **DiffGram** *.*</span></span>|  
|<span data-ttu-id="8b5af-133">**ınferschema**</span><span class="sxs-lookup"><span data-stu-id="8b5af-133">**InferSchema**</span></span>|<span data-ttu-id="8b5af-134">Herhangi bir satır dışı şema yoksave XML verilerinin yapısına göre şema çıkar, sonra verileri yükler.</span><span class="sxs-lookup"><span data-stu-id="8b5af-134">Ignores any inline schema and infers the schema per the structure of the XML data, then loads the data.</span></span><br /><br /> <span data-ttu-id="8b5af-135"><xref:System.Data.DataSet> Zaten bir şema içeriyorsa, geçerli şema varolan tablolara sütunlar eklenerek genişletilir.</span><span class="sxs-lookup"><span data-stu-id="8b5af-135">If the <xref:System.Data.DataSet> already contains a schema, the current schema is extended by adding columns to existing tables.</span></span> <span data-ttu-id="8b5af-136">Varolan tablolar yoksa ek tablolar eklenmez.</span><span class="sxs-lookup"><span data-stu-id="8b5af-136">Extra tables will not be added if there are not existing tables.</span></span> <span data-ttu-id="8b5af-137">Çıkarılan bir tablo zaten farklı bir ad alanıyla varsa veya çıkarılan sütunlar varolan sütunlarla çakışmışsa bir özel durum atılır.</span><span class="sxs-lookup"><span data-stu-id="8b5af-137">An exception is thrown if an inferred table already exists with a different namespace, or if any inferred columns conflict with existing columns.</span></span><br /><br /> <span data-ttu-id="8b5af-138">**ReadXmlSchema'nın** bir XML belgesinden bir şema çıkartması hakkında ayrıntılı bilgi [için](inferring-dataset-relational-structure-from-xml.md)bkz.</span><span class="sxs-lookup"><span data-stu-id="8b5af-138">For details about how **ReadXmlSchema** infers a schema from an XML document, see [Inferring DataSet Relational Structure from XML](inferring-dataset-relational-structure-from-xml.md).</span></span>|  
|<span data-ttu-id="8b5af-139">**Diffgram**</span><span class="sxs-lookup"><span data-stu-id="8b5af-139">**DiffGram**</span></span>|<span data-ttu-id="8b5af-140">DiffGram okur ve verileri geçerli şemaya ekler.</span><span class="sxs-lookup"><span data-stu-id="8b5af-140">Reads a DiffGram and adds the data to the current schema.</span></span> <span data-ttu-id="8b5af-141">**DiffGram,** benzersiz tanımlayıcı değerlerinin eşleştiği varolan satırlarla yeni satırları birleştirir.</span><span class="sxs-lookup"><span data-stu-id="8b5af-141">**DiffGram** merges new rows with existing rows where the unique identifier values match.</span></span> <span data-ttu-id="8b5af-142">Bu konunun sonundaki "XML'den Verileri Birleştirme" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="8b5af-142">See "Merging Data from XML" at the end of this topic.</span></span> <span data-ttu-id="8b5af-143">DiffGrams hakkında daha fazla bilgi için [Bkz.](diffgrams.md)</span><span class="sxs-lookup"><span data-stu-id="8b5af-143">For more information about DiffGrams, see [DiffGrams](diffgrams.md).</span></span>|  
|<span data-ttu-id="8b5af-144">**Parça**</span><span class="sxs-lookup"><span data-stu-id="8b5af-144">**Fragment**</span></span>|<span data-ttu-id="8b5af-145">Akışın sonuna ulaşana kadar birden çok XML parçasını okumaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="8b5af-145">Continues reading multiple XML fragments until the end of the stream is reached.</span></span> <span data-ttu-id="8b5af-146"><xref:System.Data.DataSet> Şemaya uyan parçalar uygun tablolara eklenir.</span><span class="sxs-lookup"><span data-stu-id="8b5af-146">Fragments that match the <xref:System.Data.DataSet> schema are appended to the appropriate tables.</span></span> <span data-ttu-id="8b5af-147"><xref:System.Data.DataSet> Şemaya uymayan parçalar atılır.</span><span class="sxs-lookup"><span data-stu-id="8b5af-147">Fragments that do not match the <xref:System.Data.DataSet> schema are discarded.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="8b5af-148">Bir XML belgesine yolun bir parçası konumlandırılmış **ReadXml** bir Xml için bir **XmlReader** geçerseniz, **ReadXml** sonraki öğe düğümü ne okuyacak ve kök öğesi olarak, yalnızca öğe düğümü sonuna kadar okuma olarak ele alacaktır.</span><span class="sxs-lookup"><span data-stu-id="8b5af-148">If you pass an **XmlReader** to **ReadXml** that is positioned part of the way into an XML document, **ReadXml** will read to the next element node and will treat that as the root element, reading until the end of the element node only.</span></span> <span data-ttu-id="8b5af-149">**XmlReadMode.Fragment**belirtirseniz bu geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="8b5af-149">This does not apply if you specify **XmlReadMode.Fragment**.</span></span>  
  
## <a name="dtd-entities"></a><span data-ttu-id="8b5af-150">DTD Varlıklar</span><span class="sxs-lookup"><span data-stu-id="8b5af-150">DTD Entities</span></span>  
 <span data-ttu-id="8b5af-151">XML'iniz belge türü tanımında (DTD) şemada tanımlanan varlıklar içeriyorsa, bir <xref:System.Data.DataSet> dosya adını, akışı veya **XmlReader'ı** **ReadXml'e**doğrulamayarak yüklemeyi denerseniz bir özel durum atılır.</span><span class="sxs-lookup"><span data-stu-id="8b5af-151">If your XML contains entities defined in a document type definition (DTD) schema, an exception will be thrown if you attempt to load a <xref:System.Data.DataSet> by passing a file name, stream, or non-validating **XmlReader** to **ReadXml**.</span></span> <span data-ttu-id="8b5af-152">Bunun yerine, **EntityHandling.ExpandEntities**için **EntityHandling** ayarlanmış bir **XmlValidatingReader**oluşturmanız ve **ReadXml**için **XmlValidatingReader** geçmek gerekir.</span><span class="sxs-lookup"><span data-stu-id="8b5af-152">Instead, you must create an **XmlValidatingReader**, with **EntityHandling** set to **EntityHandling.ExpandEntities**, and pass your **XmlValidatingReader** to **ReadXml**.</span></span> <span data-ttu-id="8b5af-153">**XmlValidatingReader** tarafından okunmadan önce varlıkları <xref:System.Data.DataSet>genişletecektir.</span><span class="sxs-lookup"><span data-stu-id="8b5af-153">The **XmlValidatingReader** will expand the entities prior to being read by the <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="8b5af-154">Aşağıdaki kod örnekleri, XML <xref:System.Data.DataSet> akışından nasıl yüklenirgösteriz.</span><span class="sxs-lookup"><span data-stu-id="8b5af-154">The following code examples show how to load a <xref:System.Data.DataSet> from an XML stream.</span></span> <span data-ttu-id="8b5af-155">İlk örnek, **ReadXml** yöntemine geçirilen bir dosya adını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8b5af-155">The first example shows a file name being passed to the **ReadXml** method.</span></span> <span data-ttu-id="8b5af-156">İkinci örnek, XML'nin bir <xref:System.IO.StringReader>.</span><span class="sxs-lookup"><span data-stu-id="8b5af-156">The second example shows a string that contains XML being loaded using a <xref:System.IO.StringReader>.</span></span>  
  
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
> <span data-ttu-id="8b5af-157">**ReadXml'i** çok büyük bir dosyayüklemek için ararsanız, yavaş performansla karşılaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b5af-157">If you call **ReadXml** to load a very large file, you may encounter slow performance.</span></span> <span data-ttu-id="8b5af-158">**ReadXml**için en iyi performansı sağlamak için, <xref:System.Data.DataTable.BeginLoadData%2A> büyük bir dosyada, her tablo için yöntemi arayın <xref:System.Data.DataSet>, ve sonra **ReadXml**arayın.</span><span class="sxs-lookup"><span data-stu-id="8b5af-158">To ensure best performance for **ReadXml**, on a large file, call the <xref:System.Data.DataTable.BeginLoadData%2A> method for each table in the <xref:System.Data.DataSet>, and then call **ReadXml**.</span></span> <span data-ttu-id="8b5af-159">Son olarak, aşağıdaki örnekte gösterildiği <xref:System.Data.DataTable.EndLoadData%2A> <xref:System.Data.DataSet>gibi, her tablo için çağrı.</span><span class="sxs-lookup"><span data-stu-id="8b5af-159">Finally, call <xref:System.Data.DataTable.EndLoadData%2A> for each table in the <xref:System.Data.DataSet>, as shown in the following example.</span></span>  
  
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
> <span data-ttu-id="8b5af-160">Sizin <xref:System.Data.DataSet> için XSD şema bir **targetNamespace**içeriyorsa, veri okunmayabilir ve özel durumlar karşılaşabilirsiniz, <xref:System.Data.DataSet> **ReadXml'i** arayarak uygun ad alanı olmayan öğeler içeren XML'yi yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b5af-160">If the XSD schema for your <xref:System.Data.DataSet> includes a **targetNamespace**, data may not be read, and you may encounter exceptions, when calling **ReadXml** to load the <xref:System.Data.DataSet> with XML that contains elements with no qualifying namespace.</span></span> <span data-ttu-id="8b5af-161">Bu durumda niteliksiz öğeleri okumak için, XSD şemanızda "nitelikli" **öğesiFormDefault'ı** eşit olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="8b5af-161">To read unqualified elements in this case, set **elementFormDefault** equal to "qualified" in your XSD schema.</span></span> <span data-ttu-id="8b5af-162">Örnek:</span><span class="sxs-lookup"><span data-stu-id="8b5af-162">For example:</span></span>  
  
```xml  
<xsd:schema id="customDataSet"
  elementFormDefault="qualified"  
  targetNamespace="http://www.tempuri.org/customDataSet.xsd"
  xmlns="http://www.tempuri.org/customDataSet.xsd"
  xmlns:xsd="http://www.w3.org/2001/XMLSchema"
  xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
</xsd:schema>  
```  
  
## <a name="merging-data-from-xml"></a><span data-ttu-id="8b5af-163">XML'den Veri Birleştirme</span><span class="sxs-lookup"><span data-stu-id="8b5af-163">Merging Data from XML</span></span>  
 <span data-ttu-id="8b5af-164"><xref:System.Data.DataSet> Zaten veri içeriyorsa, XML'den gelen yeni veriler, 'de mevcut olan verilere <xref:System.Data.DataSet>eklenir.</span><span class="sxs-lookup"><span data-stu-id="8b5af-164">If the <xref:System.Data.DataSet> already contains data, the new data from the XML is added to the data already present in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="8b5af-165">**ReadXml,** XML'den eşleşen <xref:System.Data.DataSet> birincil anahtarlarla herhangi bir satır bilgisine birleşmez.</span><span class="sxs-lookup"><span data-stu-id="8b5af-165">**ReadXml** does not merge from the XML into the <xref:System.Data.DataSet> any row information with matching primary keys.</span></span> <span data-ttu-id="8b5af-166">XML'den gelen yeni bilgilerle varolan satır bilgilerinin üzerine <xref:System.Data.DataSet>yazmak <xref:System.Data.DataSet.Merge%2A> için <xref:System.Data.DataSet> <xref:System.Data.DataSet> **ReadXml'i** kullanarak yeni bir ve sonra varolana yeni bir tane oluşturun.</span><span class="sxs-lookup"><span data-stu-id="8b5af-166">To overwrite existing row information with new information from XML, use **ReadXml** to create a new <xref:System.Data.DataSet>, and then <xref:System.Data.DataSet.Merge%2A> the new <xref:System.Data.DataSet> into the existing <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="8b5af-167">**ReadXML** kullanarak **DiffGram'ı** **XmlReadMode** of DiffGram ile yüklemenin, aynı benzersiz tanımlayıcıya sahip satırları birleştireceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="8b5af-167">Note that loading a DiffGram using **ReadXML** with an **XmlReadMode** of **DiffGram** will merge rows that have the same unique identifier.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b5af-168">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8b5af-168">See also</span></span>

- <xref:System.Data.DataSet.Merge%2A?displayProperty=nameWithType>
- [<span data-ttu-id="8b5af-169">DataSet içinde XML kullanma</span><span class="sxs-lookup"><span data-stu-id="8b5af-169">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="8b5af-170">DiffGrams</span><span class="sxs-lookup"><span data-stu-id="8b5af-170">DiffGrams</span></span>](diffgrams.md)
- [<span data-ttu-id="8b5af-171">XML Şemasından (XSD) DataSet İlişkisel Yapısını Türetme</span><span class="sxs-lookup"><span data-stu-id="8b5af-171">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [<span data-ttu-id="8b5af-172">XML’den DataSet İlişkisel Yapısını Çıkarma</span><span class="sxs-lookup"><span data-stu-id="8b5af-172">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="8b5af-173">XML’den DataSet Schema Bilgilerini Yükleme</span><span class="sxs-lookup"><span data-stu-id="8b5af-173">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="8b5af-174">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="8b5af-174">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="8b5af-175">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="8b5af-175">ADO.NET Overview</span></span>](../ado-net-overview.md)
