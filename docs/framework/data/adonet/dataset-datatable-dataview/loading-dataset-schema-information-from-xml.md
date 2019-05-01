---
title: XML’den DataSet Schema Bilgilerini Yükleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 43dfb23b-5cef-46f2-8d87-78f0fba1eb8c
ms.openlocfilehash: 06dcbbedf8c1533b3da52b447c121746ce705083
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61785456"
---
# <a name="loading-dataset-schema-information-from-xml"></a><span data-ttu-id="7222e-102">XML’den DataSet Schema Bilgilerini Yükleme</span><span class="sxs-lookup"><span data-stu-id="7222e-102">Loading DataSet Schema Information from XML</span></span>
<span data-ttu-id="7222e-103">Şemasını bir <xref:System.Data.DataSet> (kendi tablolar, sütunlar, ilişkiler ve kısıtlamalar) programlı olarak tarafından oluşturulan tanımlanabilir **dolgu** veya **FillSchema** yöntemlerinin bir <xref:System.Data.Common.DataAdapter>, veya gelen yüklenen bir XML belgesi.</span><span class="sxs-lookup"><span data-stu-id="7222e-103">The schema of a <xref:System.Data.DataSet> (its tables, columns, relations, and constraints) can be defined programmatically, created by the **Fill** or **FillSchema** methods of a <xref:System.Data.Common.DataAdapter>, or loaded from an XML document.</span></span> <span data-ttu-id="7222e-104">Yüklenecek **veri kümesi** şema bilgileri bir XML belgesinden ya da kullanabilirsiniz **ReadXmlSchema** veya **InferXmlSchema** yöntemi **verikümesi**.</span><span class="sxs-lookup"><span data-stu-id="7222e-104">To load **DataSet** schema information from an XML document, you can use either the **ReadXmlSchema** or the **InferXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="7222e-105">**ReadXmlSchema** yüklemek veya tanım Çıkarsama sağlar **veri kümesi** belgesinden XML Şeması Tanım Dili (XSD) şemaya veya satır içi XML şeması bir XML belgesi içeren şema bilgileri.</span><span class="sxs-lookup"><span data-stu-id="7222e-105">**ReadXmlSchema** allows you to load or infer **DataSet** schema information from the document containing XML Schema definition language (XSD) schema, or an XML document with inline XML Schema.</span></span> <span data-ttu-id="7222e-106">**InferXmlSchema** belirttiğiniz belirli XML ad alanları yoksayılıyor çalışırken XML belgesi şemanın çıkarsandığı olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="7222e-106">**InferXmlSchema** allows you to infer the schema from the XML document while ignoring certain XML namespaces that you specify.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7222e-107">Tablo, sıralama bir **veri kümesi** aktarmak için Web Hizmetleri veya XML serileştirme kullandığınızda korunmayabilir bir **veri kümesi** XSD yapıları (örneğin, iç içe geçmiş ilişkileri) kullanarak bellek içi oluşturulmuş.</span><span class="sxs-lookup"><span data-stu-id="7222e-107">Table ordering in a **DataSet** might not be preserved when you use Web services or XML serialization to transfer a **DataSet** that was created in-memory by using XSD constructs (such as nested relations).</span></span> <span data-ttu-id="7222e-108">Bu nedenle, alıcısı **veri kümesi** tablo bu durumda sıralamaya bağlı olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="7222e-108">Therefore, the recipient of the **DataSet** should not depend on table ordering in this case.</span></span> <span data-ttu-id="7222e-109">Ancak, tablo sıralama her zaman korunur şemasını **veri kümesi** aktarılan XSD dosyalarından, bellek içi oluşturulan yerine okundu.</span><span class="sxs-lookup"><span data-stu-id="7222e-109">However, table ordering is always preserved if the schema of the **DataSet** being transferred was read from XSD files, instead of being created in-memory.</span></span>  
  
## <a name="readxmlschema"></a><span data-ttu-id="7222e-110">ReadXmlSchema</span><span class="sxs-lookup"><span data-stu-id="7222e-110">ReadXmlSchema</span></span>  
 <span data-ttu-id="7222e-111">Şeması'nı yüklemek için bir **veri kümesi** herhangi bir veri yükleme olmadan bir XML belgesinden, kullandığınız **ReadXmlSchema** yöntemi **veri kümesi**.</span><span class="sxs-lookup"><span data-stu-id="7222e-111">To load the schema of a **DataSet** from an XML document without loading any data, you can use the **ReadXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="7222e-112">**ReadXmlSchema** oluşturur **veri kümesi** şeması XML Şeması Tanım Dili (XSD) şemaya tanımlanmadı.</span><span class="sxs-lookup"><span data-stu-id="7222e-112">**ReadXmlSchema** creates **DataSet** schema defined using XML Schema definition language (XSD) schema.</span></span>  
  
 <span data-ttu-id="7222e-113">**ReadXmlSchema** yöntemi, bir dosyanın adında bir akış tek bir bağımsız değişken alır veya bir **XmlReader** yüklenecek XML belgesi içeren.</span><span class="sxs-lookup"><span data-stu-id="7222e-113">The **ReadXmlSchema** method takes a single argument of a file name, a stream, or an **XmlReader** containing the XML document to be loaded.</span></span> <span data-ttu-id="7222e-114">XML belgesi, yalnızca şema içerebilir veya şema satır içi verilerini içeren XML öğeleri ile içerebilir.</span><span class="sxs-lookup"><span data-stu-id="7222e-114">The XML document can contain only schema, or can contain schema inline with XML elements containing data.</span></span> <span data-ttu-id="7222e-115">Satır içi şema XML şema olarak yazma hakkında daha fazla ayrıntı için bkz. [türetme DataSet ilişkisel yapısını XML Şeması (XSD) öğesinden](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span><span class="sxs-lookup"><span data-stu-id="7222e-115">For details about writing inline schema as XML Schema, see [Deriving DataSet Relational Structure from XML Schema (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span></span>  
  
 <span data-ttu-id="7222e-116">XML belgesi geçirilmiş **ReadXmlSchema** hiçbir satır içi şema bilgileri içeriyor **ReadXmlSchema** XML belgesi içindeki öğeleri şemanın çıkarsandığı.</span><span class="sxs-lookup"><span data-stu-id="7222e-116">If the XML document passed to **ReadXmlSchema** contains no inline schema information, **ReadXmlSchema** will infer the schema from the elements in the XML document.</span></span> <span data-ttu-id="7222e-117">Varsa **veri kümesi** zaten bir şema içeriyor. Geçerli şema zaten mevcut değilse yeni tablolar ekleyerek genişletilir.</span><span class="sxs-lookup"><span data-stu-id="7222e-117">If the **DataSet** already contains a schema, the current schema will be extended by adding new tables if they do not already exist.</span></span> <span data-ttu-id="7222e-118">Yeni sütunlar için var olan tablolara eklenen eklenmeyecek.</span><span class="sxs-lookup"><span data-stu-id="7222e-118">New columns will not be added to added to existing tables.</span></span> <span data-ttu-id="7222e-119">Zaten eklenmiş bir sütun varsa **veri kümesi** ancak sütunu türü uyumsuz buldu XML'de özel durum harekete geçirilir.</span><span class="sxs-lookup"><span data-stu-id="7222e-119">If a column being added already exists in the **DataSet** but has an incompatible type with the column found in the XML, an exception is thrown.</span></span> <span data-ttu-id="7222e-120">Hakkında ayrıntılar için **ReadXmlSchema** bir şema çıkarsar bir XML belgesinden bkz [DataSet ilişkisel yapısını çıkarma XML'den](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md).</span><span class="sxs-lookup"><span data-stu-id="7222e-120">For details about how **ReadXmlSchema** infers a schema from an XML document, see [Inferring DataSet Relational Structure from XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md).</span></span>  
  
 <span data-ttu-id="7222e-121">Ancak **ReadXmlSchema** yükler veya yalnızca şeması çıkarır bir **veri kümesi**, **ReadXml** yöntemi **veri kümesi** yükler veya her ikisi de algılar Şema ve XML belgesinde bulunan veriler.</span><span class="sxs-lookup"><span data-stu-id="7222e-121">Although **ReadXmlSchema** loads or infers only the schema of a **DataSet**, the **ReadXml** method of the **DataSet** loads or infers both the schema and the data contained in the XML document.</span></span> <span data-ttu-id="7222e-122">Daha fazla bilgi için [XML'den DataSet yükleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md).</span><span class="sxs-lookup"><span data-stu-id="7222e-122">For more information, see [Loading a DataSet from XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md).</span></span>  
  
 <span data-ttu-id="7222e-123">Aşağıdaki kod örneğinde nasıl yükleneceğini gösterir. bir **veri kümesi** şeması bir XML belgesi ya da akış.</span><span class="sxs-lookup"><span data-stu-id="7222e-123">The following code examples show how to load a **DataSet** schema from an XML document or stream.</span></span> <span data-ttu-id="7222e-124">Gönderilmiş bir XML şema dosyası adı ilk örnekte gösterilmektedir **ReadXmlSchema** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7222e-124">The first example shows an XML Schema file name being passed to the **ReadXmlSchema** method.</span></span> <span data-ttu-id="7222e-125">İkinci örnekte gösterildiği bir **System.IO.StreamReader**.</span><span class="sxs-lookup"><span data-stu-id="7222e-125">The second example shows a **System.IO.StreamReader**.</span></span>  
  
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
  
## <a name="inferxmlschema"></a><span data-ttu-id="7222e-126">InferXmlSchema</span><span class="sxs-lookup"><span data-stu-id="7222e-126">InferXmlSchema</span></span>  
 <span data-ttu-id="7222e-127">Ayrıca bildirebilirsiniz **veri kümesi** kullanarak bir XML belgesi, şema çıkarsanacak **InferXmlSchema** yöntemi **veri kümesi**.</span><span class="sxs-lookup"><span data-stu-id="7222e-127">You can also instruct the **DataSet** to infer its schema from an XML document using the **InferXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="7222e-128">**InferXmlSchema** gibi her ikisi de aynı işlevleri **ReadXml** ile bir **XmlReadMode** , **InferSchema** (verileri yükler hem de şemayı algılar) ve **ReadXmlSchema** belgenin okunan satır içi şema içeriyorsa.</span><span class="sxs-lookup"><span data-stu-id="7222e-128">**InferXmlSchema** functions the same as do both **ReadXml** with an **XmlReadMode** of **InferSchema** (loads data as well as infers schema), and **ReadXmlSchema** if the document being read contains no inline schema.</span></span> <span data-ttu-id="7222e-129">Ancak, **InferXmlSchema** şema çıkarıldığında yok sayılacak belirli XML ad alanları belirtmek için izin verme ek yeteneği sağlar.</span><span class="sxs-lookup"><span data-stu-id="7222e-129">However, **InferXmlSchema** provides the additional capability of allowing you to specify particular XML namespaces to be ignored when the schema is inferred.</span></span> <span data-ttu-id="7222e-130">**InferXmlSchema** iki gerekli bağımsız değişkeni alır: bir akışa bir dosya adıyla belirtilen XML belgesinin konumunu veya **XmlReader**; ve bir dize dizisi XML ad alanları, işlem tarafından yok sayılacak.</span><span class="sxs-lookup"><span data-stu-id="7222e-130">**InferXmlSchema** takes two required arguments: the location of the XML document, specified by a file name, a stream, or an **XmlReader**; and a string array of XML namespaces to be ignored by the operation.</span></span>  
  
 <span data-ttu-id="7222e-131">Örneğin, aşağıdaki XML göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="7222e-131">For example, consider the following XML:</span></span>  
  
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
  
 <span data-ttu-id="7222e-132">Önceki XML belgesindeki öğeler için belirtilen öznitelikleri nedeniyle hem **ReadXmlSchema** yöntemi ve **ReadXml** yöntemi ile bir **XmlReadMode** , **InferSchema** belgede her öğe için tablolar oluşturur: **Kategorileri**, **CategoryID**, **CategoryName**, **açıklama**, **ürünleri**, **ProductID**, **Türünde**, ve **kullanımdan**.</span><span class="sxs-lookup"><span data-stu-id="7222e-132">Because of the attributes specified for the elements in the preceding XML document, both the **ReadXmlSchema** method and the **ReadXml** method with an **XmlReadMode** of **InferSchema** would create tables for every element in the document: **Categories**, **CategoryID**, **CategoryName**, **Description**, **Products**, **ProductID**, **ReorderLevel**, and **Discontinued**.</span></span> <span data-ttu-id="7222e-133">(Daha fazla bilgi için [DataSet ilişkisel yapısını çıkarma XML'den](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md).) Ancak, yalnızca oluşturmak için daha uygun bir yapı olacaktır **kategorileri** ve **ürünleri** tablolar oluşturmak için sonra da **CategoryID**, **CategoryName** , ve **açıklama** sütunlarında **kategorileri** tablosunu ve **ProductID**, **türünde**, ve **Artık Üretilmiyor** sütunlarında **ürünleri** tablo.</span><span class="sxs-lookup"><span data-stu-id="7222e-133">(For more information, see [Inferring DataSet Relational Structure from XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md).) However, a more appropriate structure would be to create only the **Categories** and **Products** tables, and then to create **CategoryID**, **CategoryName**, and **Description** columns in the **Categories** table, and **ProductID**, **ReorderLevel**, and **Discontinued** columns in the **Products** table.</span></span> <span data-ttu-id="7222e-134">Çıkarsanan şema XML öğeleri belirtilen öznitelikleri yoksayılmasını sağlamak için kullanın **InferXmlSchema** yöntemi ve XML ad alanı belirtin **officedata** gösterildiği yoksayılacak Aşağıdaki örnek.</span><span class="sxs-lookup"><span data-stu-id="7222e-134">To ensure that the inferred schema ignores the attributes specified in the XML elements, use the **InferXmlSchema** method and specify the XML namespace for **officedata** to be ignored, as shown in the following example.</span></span>  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.InferXmlSchema("input_od.xml", New String() {"urn:schemas-microsoft-com:officedata"})  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.InferXmlSchema("input_od.xml", new string[] "urn:schemas-microsoft-com:officedata");  
```  
  
## <a name="see-also"></a><span data-ttu-id="7222e-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7222e-135">See also</span></span>

- [<span data-ttu-id="7222e-136">DataSet içinde XML kullanma</span><span class="sxs-lookup"><span data-stu-id="7222e-136">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
- [<span data-ttu-id="7222e-137">XML Şemasından (XSD) DataSet İlişkisel Yapısını Türetme</span><span class="sxs-lookup"><span data-stu-id="7222e-137">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [<span data-ttu-id="7222e-138">XML’den DataSet İlişkisel Yapısını Çıkarma</span><span class="sxs-lookup"><span data-stu-id="7222e-138">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="7222e-139">XML’den DataSet Yükleme</span><span class="sxs-lookup"><span data-stu-id="7222e-139">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)
- [<span data-ttu-id="7222e-140">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="7222e-140">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [<span data-ttu-id="7222e-141">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="7222e-141">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
