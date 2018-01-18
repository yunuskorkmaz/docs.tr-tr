---
title: "Bir veri kümesini XML dosyası şuradan yükleniyor"
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
ms.assetid: 49c083b7-a5ed-41cf-aabc-5aaba96f00e6
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 1d0c98224b8b508fec5fe584388872757a9dfdf3
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="loading-a-dataset-from-xml"></a><span data-ttu-id="c362a-102">Bir veri kümesini XML dosyası şuradan yükleniyor</span><span class="sxs-lookup"><span data-stu-id="c362a-102">Loading a DataSet from XML</span></span>
<span data-ttu-id="c362a-103">Bir ADO.NET içeriğini <xref:System.Data.DataSet> bir XML akışı veya belge oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="c362a-103">The contents of an ADO.NET <xref:System.Data.DataSet> can be created from an XML stream or document.</span></span> <span data-ttu-id="c362a-104">Ayrıca, .NET Framework ile büyük esneklik hangi bilgilerin, XML'den yüklenen elinizde ve nasıl şema veya ilişkisel yapısını <xref:System.Data.DataSet> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c362a-104">In addition, with the .NET Framework you have great flexibility over what information is loaded from XML, and how the schema or relational structure of the <xref:System.Data.DataSet> is created.</span></span>  
  
 <span data-ttu-id="c362a-105">Doldurmak için bir <xref:System.Data.DataSet> ile verileri XML kullanarak **ReadXml** yöntemi <xref:System.Data.DataSet> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="c362a-105">To fill a <xref:System.Data.DataSet> with data from XML, use the **ReadXml** method of the <xref:System.Data.DataSet> object.</span></span> <span data-ttu-id="c362a-106">**ReadXml** yöntemi bir dosyadan bir akış okur veya bir **XmlReader**ve kaynak XML ve isteğe bağlı bir bağımsız değişken olarak alan **XmlReadMode** bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="c362a-106">The **ReadXml** method reads from a file, a stream, or an **XmlReader**, and takes as arguments the source of the XML plus an optional **XmlReadMode** argument.</span></span> <span data-ttu-id="c362a-107">(Hakkında daha fazla bilgi için **XmlReader**, bkz: [NIB: Okuma XML XmlTextReader verileriyle](http://msdn.microsoft.com/en-us/762c069b-b50c-41b8-936e-39eacfb0d540).) **ReadXml** yöntemi XML akışı veya belge ve yükleri içeriğini okur <xref:System.Data.DataSet> verilerle.</span><span class="sxs-lookup"><span data-stu-id="c362a-107">(For more information about the **XmlReader**, see [NIB: Reading XML Data with XmlTextReader](http://msdn.microsoft.com/en-us/762c069b-b50c-41b8-936e-39eacfb0d540).) The **ReadXml** method reads the contents of the XML stream or document and loads the <xref:System.Data.DataSet> with data.</span></span> <span data-ttu-id="c362a-108">İlişkisel şeması oluşturacak <xref:System.Data.DataSet> bağlı olarak **XmlReadMode** belirtilen ve desteklemediğini ilişkisel şema zaten mevcut.</span><span class="sxs-lookup"><span data-stu-id="c362a-108">It will also create the relational schema of the <xref:System.Data.DataSet> depending on the **XmlReadMode** specified and whether or not a relational schema already exists.</span></span>  
  
 <span data-ttu-id="c362a-109">Aşağıdaki tabloda ilgili seçenekleri açıklar **XmlReadMode** bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="c362a-109">The following table describes the options for the **XmlReadMode** argument.</span></span>  
  
|<span data-ttu-id="c362a-110">Seçenek</span><span class="sxs-lookup"><span data-stu-id="c362a-110">Option</span></span>|<span data-ttu-id="c362a-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c362a-111">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="c362a-112">**Auto**</span><span class="sxs-lookup"><span data-stu-id="c362a-112">**Auto**</span></span>|<span data-ttu-id="c362a-113">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="c362a-113">This is the default.</span></span> <span data-ttu-id="c362a-114">XML inceler ve aşağıdaki sırayla en uygun seçeneği seçer:</span><span class="sxs-lookup"><span data-stu-id="c362a-114">Examines the XML and chooses the most appropriate option in the following order:</span></span><br /><br /> <span data-ttu-id="c362a-115">-Bir DiffGram XML olup olmadığını **DiffGram** kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c362a-115">-   If the XML is a DiffGram, **DiffGram** is used.</span></span><br /><span data-ttu-id="c362a-116">-İf <xref:System.Data.DataSet> bir şema içeriyor veya bir satır içi şema XML içeriyor **ReadSchema** kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c362a-116">-   If the <xref:System.Data.DataSet> contains a schema or the XML contains an inline schema, **ReadSchema** is used.</span></span><br /><span data-ttu-id="c362a-117">-İf <xref:System.Data.DataSet> bir şema içermiyor ve XML bir satır içi şema içermediğinden **InferSchema** kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c362a-117">-   If the <xref:System.Data.DataSet> does not contain a schema and the XML does not contain an inline schema, **InferSchema** is used.</span></span><br /><br /> <span data-ttu-id="c362a-118">Okunan XML biçimi biliyorsanız, en iyi performans için açık bir ayarlamanız önerilir **XmlReadMode**, bunun yerine kabul daha **otomatik** varsayılan.</span><span class="sxs-lookup"><span data-stu-id="c362a-118">If you know the format of the XML being read, for best performance it is recommended that you set an explicit **XmlReadMode**, rather than accept the **Auto** default.</span></span>|  
|<span data-ttu-id="c362a-119">**ReadSchema**</span><span class="sxs-lookup"><span data-stu-id="c362a-119">**ReadSchema**</span></span>|<span data-ttu-id="c362a-120">Herhangi bir satır içi şema okur ve veri ve şema yükler.</span><span class="sxs-lookup"><span data-stu-id="c362a-120">Reads any inline schema and loads the data and schema.</span></span><br /><br /> <span data-ttu-id="c362a-121">Varsa <xref:System.Data.DataSet> zaten varolan şemayla eklenen yeni tablolar satır içi şema bir şema içeriyor <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="c362a-121">If the <xref:System.Data.DataSet> already contains a schema, new tables are added from the inline schema to the existing schema in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="c362a-122">Satır içi şema herhangi bir tablo zaten içinde olup olmadığını <xref:System.Data.DataSet>, bir özel durum.</span><span class="sxs-lookup"><span data-stu-id="c362a-122">If any tables in the inline schema already exist in the <xref:System.Data.DataSet>, an exception is thrown.</span></span> <span data-ttu-id="c362a-123">Kullanarak varolan bir tablo için şemayı mümkün olmaz **XmlReadMode.ReadSchema**.</span><span class="sxs-lookup"><span data-stu-id="c362a-123">You will not be able to modify the schema of an existing table using **XmlReadMode.ReadSchema**.</span></span><br /><br /> <span data-ttu-id="c362a-124">Varsa <xref:System.Data.DataSet> bir şema içermiyor ve satır içi şema yok, hiçbir veri okuma.</span><span class="sxs-lookup"><span data-stu-id="c362a-124">If the <xref:System.Data.DataSet> does not contain a schema, and there is no inline schema, no data is read.</span></span><br /><br /> <span data-ttu-id="c362a-125">Satır içi şema XML Şeması Tanım Dili (XSD) şeması kullanılarak tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="c362a-125">Inline schema can be defined using XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="c362a-126">Satır içi şeması XML şeması olarak yazma hakkında daha fazla bilgi için bkz [türetme DataSet ilişkisel yapısı XML Şeması'ndan (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span><span class="sxs-lookup"><span data-stu-id="c362a-126">For details about writing inline schema as XML Schema, see [Deriving DataSet Relational Structure from XML Schema (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span></span>|  
|<span data-ttu-id="c362a-127">**IgnoreSchema**</span><span class="sxs-lookup"><span data-stu-id="c362a-127">**IgnoreSchema**</span></span>|<span data-ttu-id="c362a-128">Herhangi bir satır içi şema yoksayar ve mevcut verileri yükler <xref:System.Data.DataSet> şema.</span><span class="sxs-lookup"><span data-stu-id="c362a-128">Ignores any inline schema and loads the data into the existing <xref:System.Data.DataSet> schema.</span></span> <span data-ttu-id="c362a-129">Varolan şema eşleşmiyor herhangi bir veri göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="c362a-129">Any data that does not match the existing schema is discarded.</span></span> <span data-ttu-id="c362a-130">Hiçbir şema varsa <xref:System.Data.DataSet>, hiçbir veri yüklendi.</span><span class="sxs-lookup"><span data-stu-id="c362a-130">If no schema exists in the <xref:System.Data.DataSet>, no data is loaded.</span></span><br /><br /> <span data-ttu-id="c362a-131">Verileri bir DiffGram ise **IgnoreSchema** aynı işlevselliğe sahip **DiffGram** *.*</span><span class="sxs-lookup"><span data-stu-id="c362a-131">If the data is a DiffGram, **IgnoreSchema** has the same functionality as **DiffGram** *.*</span></span>|  
|<span data-ttu-id="c362a-132">**InferSchema**</span><span class="sxs-lookup"><span data-stu-id="c362a-132">**InferSchema**</span></span>|<span data-ttu-id="c362a-133">Herhangi bir satır içi şema yoksayar, şemanın XML veri yapısı başına oluşturur ve sonra verileri yükler.</span><span class="sxs-lookup"><span data-stu-id="c362a-133">Ignores any inline schema and infers the schema per the structure of the XML data, then loads the data.</span></span><br /><br /> <span data-ttu-id="c362a-134">Varsa <xref:System.Data.DataSet> zaten bir şema içeriyor geçerli şema var olan tablolara sütunlar ekleyerek genişletilir.</span><span class="sxs-lookup"><span data-stu-id="c362a-134">If the <xref:System.Data.DataSet> already contains a schema, the current schema is extended by adding columns to existing tables.</span></span> <span data-ttu-id="c362a-135">Değil varsa tabloları ek tablolar eklenmez.</span><span class="sxs-lookup"><span data-stu-id="c362a-135">Extra tables will not be added if there are not existing tables.</span></span> <span data-ttu-id="c362a-136">Farklı bir ad alanı ile oluşturulursa bir tablo zaten varsa veya çıkarsanan sütun varolan sütunlarla çakışırsa özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="c362a-136">An exception is thrown if an inferred table already exists with a different namespace, or if any inferred columns conflict with existing columns.</span></span><br /><br /> <span data-ttu-id="c362a-137">Hakkında ayrıntılar için **ReadXmlSchema** bir şema oluşturur bir XML belgesinden bkz [çıkarımını yapma DataSet ilişkisel yapısından XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md).</span><span class="sxs-lookup"><span data-stu-id="c362a-137">For details about how **ReadXmlSchema** infers a schema from an XML document, see [Inferring DataSet Relational Structure from XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md).</span></span>|  
|<span data-ttu-id="c362a-138">**DiffGram**</span><span class="sxs-lookup"><span data-stu-id="c362a-138">**DiffGram**</span></span>|<span data-ttu-id="c362a-139">Bir DiffGram okur ve verileri geçerli şemaya ekler.</span><span class="sxs-lookup"><span data-stu-id="c362a-139">Reads a DiffGram and adds the data to the current schema.</span></span> <span data-ttu-id="c362a-140">**DiffGram** yeni satırların benzersiz tanımlayıcı değerlerini eşleştiği varolan satırları ile birleştirir.</span><span class="sxs-lookup"><span data-stu-id="c362a-140">**DiffGram** merges new rows with existing rows where the unique identifier values match.</span></span> <span data-ttu-id="c362a-141">"Birleştirme veri gelen XML" Bu konunun sonundaki bakın.</span><span class="sxs-lookup"><span data-stu-id="c362a-141">See "Merging Data from XML" at the end of this topic.</span></span> <span data-ttu-id="c362a-142">DiffGrams hakkında daha fazla bilgi için bkz: [DiffGrams](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md).</span><span class="sxs-lookup"><span data-stu-id="c362a-142">For more information about DiffGrams, see [DiffGrams](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md).</span></span>|  
|<span data-ttu-id="c362a-143">**Parça**</span><span class="sxs-lookup"><span data-stu-id="c362a-143">**Fragment**</span></span>|<span data-ttu-id="c362a-144">Akışın sonuna ulaşılana kadar birden çok XML parçaları okuma devam eder.</span><span class="sxs-lookup"><span data-stu-id="c362a-144">Continues reading multiple XML fragments until the end of the stream is reached.</span></span> <span data-ttu-id="c362a-145">Parça eşleşen <xref:System.Data.DataSet> şema uygun tablolara eklenir.</span><span class="sxs-lookup"><span data-stu-id="c362a-145">Fragments that match the <xref:System.Data.DataSet> schema are appended to the appropriate tables.</span></span> <span data-ttu-id="c362a-146">Eşleşmeyen parçaları <xref:System.Data.DataSet> şema atılır.</span><span class="sxs-lookup"><span data-stu-id="c362a-146">Fragments that do not match the <xref:System.Data.DataSet> schema are discarded.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="c362a-147">Geçirirseniz bir **XmlReader** için **ReadXml** konumlandırılmış parçası olan bir XML belgesi içine yolu **ReadXml** sonraki öğe düğüme okuma yapacak ve kök olarak kabul eder öğesi, yalnızca öğe düğümü sonuna kadar okumak.</span><span class="sxs-lookup"><span data-stu-id="c362a-147">If you pass an **XmlReader** to **ReadXml** that is positioned part of the way into an XML document, **ReadXml** will read to the next element node and will treat that as the root element, reading until the end of the element node only.</span></span> <span data-ttu-id="c362a-148">Belirtirseniz bu uygulanmaz **XmlReadMode.Fragment**.</span><span class="sxs-lookup"><span data-stu-id="c362a-148">This does not apply if you specify **XmlReadMode.Fragment**.</span></span>  
  
## <a name="dtd-entities"></a><span data-ttu-id="c362a-149">DTD varlıklar</span><span class="sxs-lookup"><span data-stu-id="c362a-149">DTD Entities</span></span>  
 <span data-ttu-id="c362a-150">Yüklemeye çalışırsanız, XML belge türü tanımı (DTD) şemada tanımlanan varlıklar içeriyorsa, bir özel durum oluşturulur bir <xref:System.Data.DataSet> geçirerek bir dosya adı, akış veya yapmayan **XmlReader** için  **ReadXml**.</span><span class="sxs-lookup"><span data-stu-id="c362a-150">If your XML contains entities defined in a document type definition (DTD) schema, an exception will be thrown if you attempt to load a <xref:System.Data.DataSet> by passing a file name, stream, or non-validating **XmlReader** to **ReadXml**.</span></span> <span data-ttu-id="c362a-151">Bunun yerine, oluşturmalısınız bir **XmlValidatingReader**, ile **EntityHandling** kümesine **EntityHandling.ExpandEntities**ve geçirmek,  **XmlValidatingReader** için **ReadXml**.</span><span class="sxs-lookup"><span data-stu-id="c362a-151">Instead, you must create an **XmlValidatingReader**, with **EntityHandling** set to **EntityHandling.ExpandEntities**, and pass your **XmlValidatingReader** to **ReadXml**.</span></span> <span data-ttu-id="c362a-152">**XmlValidatingReader** tarafından okunan önce varlıkları genişletecek <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="c362a-152">The **XmlValidatingReader** will expand the entities prior to being read by the <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="c362a-153">Aşağıdaki kodu nasıl yükleneceğini örnekler bir <xref:System.Data.DataSet> bir XML akışından.</span><span class="sxs-lookup"><span data-stu-id="c362a-153">The following code examples show how to load a <xref:System.Data.DataSet> from an XML stream.</span></span> <span data-ttu-id="c362a-154">İlk örnek için geçirilen bir dosya adı gösterir **ReadXml** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c362a-154">The first example shows a file name being passed to the **ReadXml** method.</span></span> <span data-ttu-id="c362a-155">İkinci örnek XML olma kullanarak yüklenen içeren bir dize gösterir bir <xref:System.IO.StringReader>.</span><span class="sxs-lookup"><span data-stu-id="c362a-155">The second example shows a string that contains XML being loaded using a <xref:System.IO.StringReader>.</span></span>  
  
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
>  <span data-ttu-id="c362a-156">Çağırırsanız **ReadXml** çok büyük bir dosya yüklemek için yavaş performans karşılaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c362a-156">If you call **ReadXml** to load a very large file, you may encounter slow performance.</span></span> <span data-ttu-id="c362a-157">İçin en iyi performansı elde etmek için **ReadXml**, büyük boyutlu bir dosyayı çağrısı <xref:System.Data.DataTable.BeginLoadData%2A> yöntemi her tablo için <xref:System.Data.DataSet>ve ardından arama **ReadXml**.</span><span class="sxs-lookup"><span data-stu-id="c362a-157">To ensure best performance for **ReadXml**, on a large file, call the <xref:System.Data.DataTable.BeginLoadData%2A> method for each table in the <xref:System.Data.DataSet>, and then call **ReadXml**.</span></span> <span data-ttu-id="c362a-158">Son olarak, arama <xref:System.Data.DataTable.EndLoadData%2A> her tablo için <xref:System.Data.DataSet>, aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="c362a-158">Finally, call <xref:System.Data.DataTable.EndLoadData%2A> for each table in the <xref:System.Data.DataSet>, as shown in the following example.</span></span>  
  
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
>  <span data-ttu-id="c362a-159">Varsa XSD şeması, <xref:System.Data.DataSet> içeren bir **targetNamespace**veri okunamadığı ve çağrılırken özel durumlar, karşılaşabileceğiniz **ReadXml** yüklemek için <xref:System.Data.DataSet> içeren XML ile öğeleri ile belirleme ad alanı yok.</span><span class="sxs-lookup"><span data-stu-id="c362a-159">If the XSD schema for your <xref:System.Data.DataSet> includes a **targetNamespace**, data may not be read, and you may encounter exceptions, when calling **ReadXml** to load the <xref:System.Data.DataSet> with XML that contains elements with no qualifying namespace.</span></span> <span data-ttu-id="c362a-160">Bu durumda nitelenmemiş öğelerini okumak için **elementFormDefault** eşit "tam" XSD şemasında.</span><span class="sxs-lookup"><span data-stu-id="c362a-160">To read unqualified elements in this case, set **elementFormDefault** equal to "qualified" in your XSD schema.</span></span> <span data-ttu-id="c362a-161">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="c362a-161">For example:</span></span>  
  
```xml  
<xsd:schema id="customDataSet"   
  elementFormDefault="qualified"  
  targetNamespace="http://www.tempuri.org/customDataSet.xsd"   
  xmlns="http://www.tempuri.org/customDataSet.xsd"   
  xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
  xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
</xsd:schema>  
```  
  
## <a name="merging-data-from-xml"></a><span data-ttu-id="c362a-162">XML verileri birleştirme</span><span class="sxs-lookup"><span data-stu-id="c362a-162">Merging Data from XML</span></span>  
 <span data-ttu-id="c362a-163">Varsa <xref:System.Data.DataSet> zaten verilerini içeren XML yeni verileri zaten mevcut verilere eklenir <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="c362a-163">If the <xref:System.Data.DataSet> already contains data, the new data from the XML is added to the data already present in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="c362a-164">**ReadXml** XML'den birleştirmez <xref:System.Data.DataSet> herhangi bir satır eşleşen birincil anahtarlarla bilgi.</span><span class="sxs-lookup"><span data-stu-id="c362a-164">**ReadXml** does not merge from the XML into the <xref:System.Data.DataSet> any row information with matching primary keys.</span></span> <span data-ttu-id="c362a-165">Var olan satır bilgilerini XML yeni bilgilerle üzerine yazmak için kullanın **ReadXml** yeni <xref:System.Data.DataSet>ve ardından <xref:System.Data.DataSet.Merge%2A> yeni <xref:System.Data.DataSet> varolan içine <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="c362a-165">To overwrite existing row information with new information from XML, use **ReadXml** to create a new <xref:System.Data.DataSet>, and then <xref:System.Data.DataSet.Merge%2A> the new <xref:System.Data.DataSet> into the existing <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="c362a-166">Bu DiffGram kullanarak yükleme Not **ReadXML** ile bir **XmlReadMode** , **DiffGram** aynı benzersiz tanımlayıcısına sahip satırları birleştirir.</span><span class="sxs-lookup"><span data-stu-id="c362a-166">Note that loading a DiffGram using **ReadXML** with an **XmlReadMode** of **DiffGram** will merge rows that have the same unique identifier.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c362a-167">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c362a-167">See Also</span></span>  
 <xref:System.Data.DataSet.Merge%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="c362a-168">DataSet içinde XML kullanma</span><span class="sxs-lookup"><span data-stu-id="c362a-168">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [<span data-ttu-id="c362a-169">DiffGrams</span><span class="sxs-lookup"><span data-stu-id="c362a-169">DiffGrams</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md)  
 [<span data-ttu-id="c362a-170">XML Şemasından (XSD) DataSet İlişkisel Yapısını Türetme</span><span class="sxs-lookup"><span data-stu-id="c362a-170">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 [<span data-ttu-id="c362a-171">XML’den DataSet İlişkisel Yapısını Çıkarma</span><span class="sxs-lookup"><span data-stu-id="c362a-171">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [<span data-ttu-id="c362a-172">XML’den DataSet Schema Bilgilerini Yükleme</span><span class="sxs-lookup"><span data-stu-id="c362a-172">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [<span data-ttu-id="c362a-173">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="c362a-173">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="c362a-174">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="c362a-174">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
