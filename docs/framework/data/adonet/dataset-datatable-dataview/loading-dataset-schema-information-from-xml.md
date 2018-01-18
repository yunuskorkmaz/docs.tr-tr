---
title: "XML'den veri kümesi şema bilgileri yükleniyor"
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
ms.assetid: 43dfb23b-5cef-46f2-8d87-78f0fba1eb8c
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 8b814715782710994f18163ccfcd3db342199145
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="loading-dataset-schema-information-from-xml"></a><span data-ttu-id="a3e55-102">XML'den veri kümesi şema bilgileri yükleniyor</span><span class="sxs-lookup"><span data-stu-id="a3e55-102">Loading DataSet Schema Information from XML</span></span>
<span data-ttu-id="a3e55-103">Şeması bir <xref:System.Data.DataSet> (kendi tablolar, sütunlar, ilişkileri ve kısıtlamalar) programlı olarak tarafından oluşturulan tanımlanabilir **doldurun** veya **FillSchema** yöntemlerinin bir <xref:System.Data.Common.DataAdapter>, veya gelen yüklenen bir XML belgesi.</span><span class="sxs-lookup"><span data-stu-id="a3e55-103">The schema of a <xref:System.Data.DataSet> (its tables, columns, relations, and constraints) can be defined programmatically, created by the **Fill** or **FillSchema** methods of a <xref:System.Data.Common.DataAdapter>, or loaded from an XML document.</span></span> <span data-ttu-id="a3e55-104">Yüklemek için **DataSet** şema bilgileri bir XML belgesinden kullanabilirsiniz **ReadXmlSchema** veya **InferXmlSchema** yöntemi **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="a3e55-104">To load **DataSet** schema information from an XML document, you can use either the **ReadXmlSchema** or the **InferXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="a3e55-105">**ReadXmlSchema** yüklemek veya Infer sağlayan **DataSet** XML Şeması Tanım Dili (XSD) şeması veya satır içi XML Şeması XML belgesiyle içeren belgedeki şema bilgileri.</span><span class="sxs-lookup"><span data-stu-id="a3e55-105">**ReadXmlSchema** allows you to load or infer **DataSet** schema information from the document containing XML Schema definition language (XSD) schema, or an XML document with inline XML Schema.</span></span> <span data-ttu-id="a3e55-106">**InferXmlSchema** belirttiğiniz belirli XML ad alanları yoksayılıyor sırasında şemasını XML belgesinden olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="a3e55-106">**InferXmlSchema** allows you to infer the schema from the XML document while ignoring certain XML namespaces that you specify.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a3e55-107">Tablo içinde sıralama bir **DataSet** aktarmak için Web Hizmetleri veya XML serileştirme kullandığınızda korunmayabilir bir **DataSet** XSD yapıları (örneğin, iç içe geçmiş ilişkileri) kullanarak bellek içi oluşturulmuş.</span><span class="sxs-lookup"><span data-stu-id="a3e55-107">Table ordering in a **DataSet** might not be preserved when you use Web services or XML serialization to transfer a **DataSet** that was created in-memory by using XSD constructs (such as nested relations).</span></span> <span data-ttu-id="a3e55-108">Bu nedenle, alıcısı **DataSet** tablo bu durumda sırasını bağlı olmaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a3e55-108">Therefore, the recipient of the **DataSet** should not depend on table ordering in this case.</span></span> <span data-ttu-id="a3e55-109">Ancak, tablo sıralama her zaman korunur ve şema **DataSet** aktarılan bellek içi oluşturulan yerine XSD dosyalarından okundu.</span><span class="sxs-lookup"><span data-stu-id="a3e55-109">However, table ordering is always preserved if the schema of the **DataSet** being transferred was read from XSD files, instead of being created in-memory.</span></span>  
  
## <a name="readxmlschema"></a><span data-ttu-id="a3e55-110">ReadXmlSchema</span><span class="sxs-lookup"><span data-stu-id="a3e55-110">ReadXmlSchema</span></span>  
 <span data-ttu-id="a3e55-111">Şeması yüklemek için bir **DataSet** herhangi bir veri yükleme olmadan bir XML belgesinden, kullandığınız **ReadXmlSchema** yöntemi **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="a3e55-111">To load the schema of a **DataSet** from an XML document without loading any data, you can use the **ReadXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="a3e55-112">**ReadXmlSchema** oluşturur **DataSet** XML Şeması Tanım Dili (XSD) şeması kullanılarak tanımlanan şema.</span><span class="sxs-lookup"><span data-stu-id="a3e55-112">**ReadXmlSchema** creates **DataSet** schema defined using XML Schema definition language (XSD) schema.</span></span>  
  
 <span data-ttu-id="a3e55-113">**ReadXmlSchema** yöntemi alır, bir akış bir dosya adı, tek bir bağımsız değişken veya bir **XmlReader** yüklenecek XML belgesi içeren.</span><span class="sxs-lookup"><span data-stu-id="a3e55-113">The **ReadXmlSchema** method takes a single argument of a file name, a stream, or an **XmlReader** containing the XML document to be loaded.</span></span> <span data-ttu-id="a3e55-114">XML belgesi yalnızca şema içerebilir veya şema satır içi ile verileri içeren XML öğeleri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="a3e55-114">The XML document can contain only schema, or can contain schema inline with XML elements containing data.</span></span> <span data-ttu-id="a3e55-115">Satır içi şeması XML şeması olarak yazma hakkında daha fazla bilgi için bkz [türetme DataSet ilişkisel yapısı XML Şeması'ndan (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span><span class="sxs-lookup"><span data-stu-id="a3e55-115">For details about writing inline schema as XML Schema, see [Deriving DataSet Relational Structure from XML Schema (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span></span>  
  
 <span data-ttu-id="a3e55-116">XML belgesi için aktarılırsa **ReadXmlSchema** hiçbir satır içi şema bilgileri içeriyor **ReadXmlSchema** XML belgedeki öğelerden şemasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a3e55-116">If the XML document passed to **ReadXmlSchema** contains no inline schema information, **ReadXmlSchema** will infer the schema from the elements in the XML document.</span></span> <span data-ttu-id="a3e55-117">Varsa **DataSet** zaten bir şema içeriyor geçerli şema zaten mevcut değilse yeni tablolar ekleyerek uzatılır.</span><span class="sxs-lookup"><span data-stu-id="a3e55-117">If the **DataSet** already contains a schema, the current schema will be extended by adding new tables if they do not already exist.</span></span> <span data-ttu-id="a3e55-118">Yeni sütunlar için var olan tablolara eklenen eklenmez.</span><span class="sxs-lookup"><span data-stu-id="a3e55-118">New columns will not be added to added to existing tables.</span></span> <span data-ttu-id="a3e55-119">Eklenmekte olan bir sütun varsa **DataSet** ancak sütun türü uyumsuz buldu XML'de, bir özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="a3e55-119">If a column being added already exists in the **DataSet** but has an incompatible type with the column found in the XML, an exception is thrown.</span></span> <span data-ttu-id="a3e55-120">Hakkında ayrıntılar için **ReadXmlSchema** bir şema oluşturur bir XML belgesinden bkz [çıkarımını yapma DataSet ilişkisel yapısından XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md).</span><span class="sxs-lookup"><span data-stu-id="a3e55-120">For details about how **ReadXmlSchema** infers a schema from an XML document, see [Inferring DataSet Relational Structure from XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md).</span></span>  
  
 <span data-ttu-id="a3e55-121">Ancak **ReadXmlSchema** yükler veya yalnızca şeması oluşturur bir **DataSet**, **ReadXml** yöntemi **DataSet** yükler veya her ikisini de oluşturur Şema ve XML belgesinde bulunan verileri.</span><span class="sxs-lookup"><span data-stu-id="a3e55-121">Although **ReadXmlSchema** loads or infers only the schema of a **DataSet**, the **ReadXml** method of the **DataSet** loads or infers both the schema and the data contained in the XML document.</span></span> <span data-ttu-id="a3e55-122">Daha fazla bilgi için bkz: [bir veri kümesini XML dosyası şuradan yükleniyor](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md).</span><span class="sxs-lookup"><span data-stu-id="a3e55-122">For more information, see [Loading a DataSet from XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md).</span></span>  
  
 <span data-ttu-id="a3e55-123">Aşağıdaki kodu nasıl yükleneceğini örnekler bir **DataSet** bir XML belgesi veya akış şeması.</span><span class="sxs-lookup"><span data-stu-id="a3e55-123">The following code examples show how to load a **DataSet** schema from an XML document or stream.</span></span> <span data-ttu-id="a3e55-124">İlk örnek için geçirilen bir XML Şeması dosya adı gösterir **ReadXmlSchema** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a3e55-124">The first example shows an XML Schema file name being passed to the **ReadXmlSchema** method.</span></span> <span data-ttu-id="a3e55-125">İkinci örnekteki bir **System.IO.StreamReader**.</span><span class="sxs-lookup"><span data-stu-id="a3e55-125">The second example shows a **System.IO.StreamReader**.</span></span>  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.ReadXmlSchema("schema.xsd")  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.ReadXmlSchema("schema.xsd");  
```  
  
```vb  
Dim xmlStream As System.IO.StreamReader = New System.IO.StreamReader ("schema.xsd");  
Dim dataSet As DataSet = New DataSet  
dataSet.ReadXmlSchema(xmlStream)  
xmlStream.Close()  
```  
  
```csharp  
System.IO.StreamReader xmlStream = new System.IO.StreamReader("schema.xsd");  
DataSet dataSet = new DataSet();  
dataSet.ReadXmlSchema(xmlStream);  
xmlStream.Close();  
```  
  
## <a name="inferxmlschema"></a><span data-ttu-id="a3e55-126">InferXmlSchema</span><span class="sxs-lookup"><span data-stu-id="a3e55-126">InferXmlSchema</span></span>  
 <span data-ttu-id="a3e55-127">Ayrıca söyleyebilirsiniz **DataSet** bir XML belgesi kullanarak şemasına gerçekleştirip **InferXmlSchema** yöntemi **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="a3e55-127">You can also instruct the **DataSet** to infer its schema from an XML document using the **InferXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="a3e55-128">**InferXmlSchema** gibi her ikisi de aynı işlevleri **ReadXml** ile bir **XmlReadMode** , **InferSchema** (verileri yükler yanı sıra şema oluşturur) ve  **ReadXmlSchema** okunan belge hiçbir satır içi şema içeriyorsa.</span><span class="sxs-lookup"><span data-stu-id="a3e55-128">**InferXmlSchema** functions the same as do both **ReadXml** with an **XmlReadMode** of **InferSchema** (loads data as well as infers schema), and **ReadXmlSchema** if the document being read contains no inline schema.</span></span> <span data-ttu-id="a3e55-129">Ancak, **InferXmlSchema** şema çıkarıldığında yok sayılacak belirli XML ad alanları belirtmek için sağlayarak ek özelliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="a3e55-129">However, **InferXmlSchema** provides the additional capability of allowing you to specify particular XML namespaces to be ignored when the schema is inferred.</span></span> <span data-ttu-id="a3e55-130">**InferXmlSchema** iki gerekli bağımsız değişkeni alır: bir akış bir dosya adıyla belirtilen XML belgesinin konumu veya bir **XmlReader**; ve işlem tarafından yoksayılacak XML ad alanları bir dize dizisi.</span><span class="sxs-lookup"><span data-stu-id="a3e55-130">**InferXmlSchema** takes two required arguments: the location of the XML document, specified by a file name, a stream, or an **XmlReader**; and a string array of XML namespaces to be ignored by the operation.</span></span>  
  
 <span data-ttu-id="a3e55-131">Örneğin, aşağıdaki XML göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="a3e55-131">For example, consider the following XML:</span></span>  
  
```xml  
<NewDataSet xmlns:od="urn:schemas-microsoft-com:officedata">  
<Categories>  
  <CategoryID od:adotype="3">1</CategoryID>   
  <CategoryName od:maxLength="15" od:adotype="130">Beverages</CategoryName>   
  <Description od:adotype="203">Soft drinks and teas</Description>   
</Categories>  
<Products>  
  <ProductID od:adotype="20">1</ProductID>   
  <ReorderLevel od:adotype="3">10</ReorderLevel>   
  <Discontinued od:adotype="11">0</Discontinued>   
</Products>  
</NewDataSet>  
```  
  
 <span data-ttu-id="a3e55-132">Önceki XML belgesindeki öğeleri için belirtilen öznitelikler nedeniyle hem **ReadXmlSchema** yöntemi ve **ReadXml** yöntemi ile bir **XmlReadMode** , **InferSchema** her öğe için tabloları belgede oluşturursunuz: **kategorileri**, **adlı kullanıcı, Categoryıd'si**, **CategoryName**, **Açıklama**, **ürünleri**, **ProductID**, **türünde**, ve **dönüştürülmesine**.</span><span class="sxs-lookup"><span data-stu-id="a3e55-132">Because of the attributes specified for the elements in the preceding XML document, both the **ReadXmlSchema** method and the **ReadXml** method with an **XmlReadMode** of **InferSchema** would create tables for every element in the document: **Categories**, **CategoryID**, **CategoryName**, **Description**, **Products**, **ProductID**, **ReorderLevel**, and **Discontinued**.</span></span> <span data-ttu-id="a3e55-133">(Daha fazla bilgi için bkz: [çıkarımını yapma DataSet ilişkisel yapısından XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md).) Ancak, yalnızca oluşturmak için daha uygun bir yapı olacaktır **kategorileri** ve **ürünleri** tabloları, ardından oluşturmak için **adlı kullanıcı, Categoryıd'si**, **CategoryName** , ve **açıklama** sütunlarında **kategorileri** tablo ve **ProductID**, **türünde**, ve **Üretimi Durdurulmuş** sütunlarında **ürünleri** tablo.</span><span class="sxs-lookup"><span data-stu-id="a3e55-133">(For more information, see [Inferring DataSet Relational Structure from XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md).) However, a more appropriate structure would be to create only the **Categories** and **Products** tables, and then to create **CategoryID**, **CategoryName**, and **Description** columns in the **Categories** table, and **ProductID**, **ReorderLevel**, and **Discontinued** columns in the **Products** table.</span></span> <span data-ttu-id="a3e55-134">Çıkarsanan şemanın XML öğeleri belirtilen öznitelikler yoksaymasını sağlamak için kullanmak **InferXmlSchema** yöntemi için XML ad alanı belirtin **officedata** gösterildiği gibi yoksayılacak Aşağıdaki örnek.</span><span class="sxs-lookup"><span data-stu-id="a3e55-134">To ensure that the inferred schema ignores the attributes specified in the XML elements, use the **InferXmlSchema** method and specify the XML namespace for **officedata** to be ignored, as shown in the following example.</span></span>  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.InferXmlSchema("input_od.xml", New String() {"urn:schemas-microsoft-com:officedata"})  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.InferXmlSchema("input_od.xml", new string[] "urn:schemas-microsoft-com:officedata");  
```  
  
## <a name="see-also"></a><span data-ttu-id="a3e55-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a3e55-135">See Also</span></span>  
 [<span data-ttu-id="a3e55-136">DataSet içinde XML kullanma</span><span class="sxs-lookup"><span data-stu-id="a3e55-136">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [<span data-ttu-id="a3e55-137">XML Şemasından (XSD) DataSet İlişkisel Yapısını Türetme</span><span class="sxs-lookup"><span data-stu-id="a3e55-137">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 [<span data-ttu-id="a3e55-138">XML’den DataSet İlişkisel Yapısını Çıkarma</span><span class="sxs-lookup"><span data-stu-id="a3e55-138">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [<span data-ttu-id="a3e55-139">XML’den DataSet Yükleme</span><span class="sxs-lookup"><span data-stu-id="a3e55-139">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [<span data-ttu-id="a3e55-140">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="a3e55-140">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="a3e55-141">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="a3e55-141">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
