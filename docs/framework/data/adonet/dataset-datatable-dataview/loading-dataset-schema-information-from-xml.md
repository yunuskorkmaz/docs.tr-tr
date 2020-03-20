---
title: XML’den DataSet Schema Bilgilerini Yükleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 43dfb23b-5cef-46f2-8d87-78f0fba1eb8c
ms.openlocfilehash: 69994c546fea842ffef1c8c43d6d6f5bc35e0629
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151058"
---
# <a name="loading-dataset-schema-information-from-xml"></a><span data-ttu-id="15347-102">XML’den DataSet Schema Bilgilerini Yükleme</span><span class="sxs-lookup"><span data-stu-id="15347-102">Loading DataSet Schema Information from XML</span></span>
<span data-ttu-id="15347-103">Bir <xref:System.Data.DataSet> şema (tabloları, sütunları, ilişkileri ve kısıtlamaları) programlı olarak tanımlanabilir, bir <xref:System.Data.Common.DataAdapter>'nin **Dolgu** veya **FillSchema** yöntemleri tarafından oluşturulabilir veya bir XML belgesinden yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="15347-103">The schema of a <xref:System.Data.DataSet> (its tables, columns, relations, and constraints) can be defined programmatically, created by the **Fill** or **FillSchema** methods of a <xref:System.Data.Common.DataAdapter>, or loaded from an XML document.</span></span> <span data-ttu-id="15347-104">Bir XML belgesinden **DataSet** şema bilgilerini yüklemek için, **DataSet'in** **ReadXmlSchema** veya **InferXmlSchema** yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="15347-104">To load **DataSet** schema information from an XML document, you can use either the **ReadXmlSchema** or the **InferXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="15347-105">**ReadXmlSchema,** XML Şema tanım dili (XSD) şeması veya satır satır lı XML şeması içeren belgeden **DataSet** şema bilgilerini yüklemenize veya çıkaramanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="15347-105">**ReadXmlSchema** allows you to load or infer **DataSet** schema information from the document containing XML Schema definition language (XSD) schema, or an XML document with inline XML Schema.</span></span> <span data-ttu-id="15347-106">**InferXmlSchema,** belirttiğiniz belirli XML ad alanlarını yoksayarak XML belgesinden şemayı çıkartmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="15347-106">**InferXmlSchema** allows you to infer the schema from the XML document while ignoring certain XML namespaces that you specify.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="15347-107">**DataSet'teki** tablo sıralama, XSD yapıları (iç içe ilişkiler gibi) kullanılarak bellekte oluşturulan bir **DataSet'i** aktarmak için Web hizmetlerini veya XML serileştirmeyi kullandığınızda korunmayabilir.</span><span class="sxs-lookup"><span data-stu-id="15347-107">Table ordering in a **DataSet** might not be preserved when you use Web services or XML serialization to transfer a **DataSet** that was created in-memory by using XSD constructs (such as nested relations).</span></span> <span data-ttu-id="15347-108">Bu nedenle, **DataSet'in** alıcısı bu durumda tablo sıralamasına bağlı olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="15347-108">Therefore, the recipient of the **DataSet** should not depend on table ordering in this case.</span></span> <span data-ttu-id="15347-109">Ancak, aktarılan **DataSet** şeası bellekte oluşturulmak yerine XSD dosyalarından okunduysa, tablo sıralama her zaman korunur.</span><span class="sxs-lookup"><span data-stu-id="15347-109">However, table ordering is always preserved if the schema of the **DataSet** being transferred was read from XSD files, instead of being created in-memory.</span></span>  
  
## <a name="readxmlschema"></a><span data-ttu-id="15347-110">Readxmlschema</span><span class="sxs-lookup"><span data-stu-id="15347-110">ReadXmlSchema</span></span>  
 <span data-ttu-id="15347-111">Herhangi bir veri yüklemeden bir XML belgesinden Bir **DataSet** şemasını yüklemek için, **DataSet'in** **ReadXmlSchema** yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="15347-111">To load the schema of a **DataSet** from an XML document without loading any data, you can use the **ReadXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="15347-112">**ReadXmlSchema,** XML Şema tanım dili (XSD) şeması kullanılarak tanımlanan **DataSet** şemasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="15347-112">**ReadXmlSchema** creates **DataSet** schema defined using XML Schema definition language (XSD) schema.</span></span>  
  
 <span data-ttu-id="15347-113">**ReadXmlSchema** yöntemi, yüklenecek XML belgesini içeren bir dosya adı, akış veya **XmlReader** tek bir bağımsız değişken alır.</span><span class="sxs-lookup"><span data-stu-id="15347-113">The **ReadXmlSchema** method takes a single argument of a file name, a stream, or an **XmlReader** containing the XML document to be loaded.</span></span> <span data-ttu-id="15347-114">XML belgesi yalnızca şema içerebilir veya veri içeren XML öğeleriyle satır satır şema içerebilir.</span><span class="sxs-lookup"><span data-stu-id="15347-114">The XML document can contain only schema, or can contain schema inline with XML elements containing data.</span></span> <span data-ttu-id="15347-115">XML Şema olarak satır içinde şema yazma hakkında ayrıntılı bilgi için, [XML Schema (XSD) gelen Veri Seti İlişkisel Yapısı Türetilmesi](deriving-dataset-relational-structure-from-xml-schema-xsd.md)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="15347-115">For details about writing inline schema as XML Schema, see [Deriving DataSet Relational Structure from XML Schema (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span></span>  
  
 <span data-ttu-id="15347-116">**ReadXmlSchema'ya** geçirilen XML belgesi satır içinde şema bilgisi içermezse, **ReadXmlSchema** şemayı XML belgesindeki öğelerden çıkaracaktır.</span><span class="sxs-lookup"><span data-stu-id="15347-116">If the XML document passed to **ReadXmlSchema** contains no inline schema information, **ReadXmlSchema** will infer the schema from the elements in the XML document.</span></span> <span data-ttu-id="15347-117">**DataSet** zaten bir şema içeriyorsa, geçerli şema zaten yoksa yeni tablolar ekleyerek genişletilir.</span><span class="sxs-lookup"><span data-stu-id="15347-117">If the **DataSet** already contains a schema, the current schema will be extended by adding new tables if they do not already exist.</span></span> <span data-ttu-id="15347-118">Varolan tablolara yeni sütunlar eklenmez.</span><span class="sxs-lookup"><span data-stu-id="15347-118">New columns will not be added to added to existing tables.</span></span> <span data-ttu-id="15347-119">Eklenen bir sütun **DataSet'te** zaten varsa ancak XML'de bulunan sütunla uyumsuz bir türü varsa, bir özel durum atılır.</span><span class="sxs-lookup"><span data-stu-id="15347-119">If a column being added already exists in the **DataSet** but has an incompatible type with the column found in the XML, an exception is thrown.</span></span> <span data-ttu-id="15347-120">**ReadXmlSchema'nın** bir XML belgesinden bir şema çıkartması hakkında ayrıntılı bilgi [için](inferring-dataset-relational-structure-from-xml.md)bkz.</span><span class="sxs-lookup"><span data-stu-id="15347-120">For details about how **ReadXmlSchema** infers a schema from an XML document, see [Inferring DataSet Relational Structure from XML](inferring-dataset-relational-structure-from-xml.md).</span></span>  
  
 <span data-ttu-id="15347-121">**ReadXmlSchema** yalnızca bir **DataSet**şeasını yükler veya çıkarsa da, **DataSet'in** **ReadXml** yöntemi Hem şeayı hem de XML belgesinde yer alan verileri yükler veya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="15347-121">Although **ReadXmlSchema** loads or infers only the schema of a **DataSet**, the **ReadXml** method of the **DataSet** loads or infers both the schema and the data contained in the XML document.</span></span> <span data-ttu-id="15347-122">Daha fazla bilgi için Bkz. [XML'den Veri Seti Yükleme.](loading-a-dataset-from-xml.md)</span><span class="sxs-lookup"><span data-stu-id="15347-122">For more information, see [Loading a DataSet from XML](loading-a-dataset-from-xml.md).</span></span>  
  
 <span data-ttu-id="15347-123">Aşağıdaki kod örnekleri, Bir **XML** belgesinden veya akışından bir DataSet şemasını nasıl yükleyeceğimi gösterir.</span><span class="sxs-lookup"><span data-stu-id="15347-123">The following code examples show how to load a **DataSet** schema from an XML document or stream.</span></span> <span data-ttu-id="15347-124">İlk örnek, **ReadXmlSchema** yöntemine geçirilen bir XML Şema dosya adının olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="15347-124">The first example shows an XML Schema file name being passed to the **ReadXmlSchema** method.</span></span> <span data-ttu-id="15347-125">İkinci örnek bir **System.IO.StreamReader**gösterir.</span><span class="sxs-lookup"><span data-stu-id="15347-125">The second example shows a **System.IO.StreamReader**.</span></span>  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.ReadXmlSchema("schema.xsd")  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.ReadXmlSchema("schema.xsd");  
```  
  
```vb  
Dim xmlStream As New System.IO.StreamReader("schema.xsd")
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
  
## <a name="inferxmlschema"></a><span data-ttu-id="15347-126">InferXmlSchema</span><span class="sxs-lookup"><span data-stu-id="15347-126">InferXmlSchema</span></span>  
 <span data-ttu-id="15347-127">DataSet'in **InferXmlSchema** yöntemini kullanarak **DataSet'e** şemasını bir XML **DataSet**belgesinden çıkarmasını da öğretebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="15347-127">You can also instruct the **DataSet** to infer its schema from an XML document using the **InferXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="15347-128">**InferXmlSchema,** **XmlReadMode** of **InferSchema** (verileri yükler ve şema yükler) ile **ReadXmlml'in** her ikisiyle aynı işlevi görür (veriler yükler ve okunan belge satır içinde şema içermese **ReadXmlSchema.**</span><span class="sxs-lookup"><span data-stu-id="15347-128">**InferXmlSchema** functions the same as do both **ReadXml** with an **XmlReadMode** of **InferSchema** (loads data as well as infers schema), and **ReadXmlSchema** if the document being read contains no inline schema.</span></span> <span data-ttu-id="15347-129">Ancak, **InferXmlSchema** şema çıkarıldığında göz ardı edilecek belirli XML ad boşluklarını belirtmenize izin veren ek bir yetenek sağlar.</span><span class="sxs-lookup"><span data-stu-id="15347-129">However, **InferXmlSchema** provides the additional capability of allowing you to specify particular XML namespaces to be ignored when the schema is inferred.</span></span> <span data-ttu-id="15347-130">**InferXmlSchema** iki gerekli bağımsız değişkenalır: XML belgenin konumu, bir dosya adı, bir akış veya **XmlReader**tarafından belirtilen; ve işlem tarafından yoksayılacak bir dizi XML ad alanı.</span><span class="sxs-lookup"><span data-stu-id="15347-130">**InferXmlSchema** takes two required arguments: the location of the XML document, specified by a file name, a stream, or an **XmlReader**; and a string array of XML namespaces to be ignored by the operation.</span></span>  
  
 <span data-ttu-id="15347-131">Örneğin, aşağıdaki XML'yi göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="15347-131">For example, consider the following XML:</span></span>  
  
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
  
 <span data-ttu-id="15347-132">Önceki XML belgesindeki öğeler için belirtilen öznitelikler nedeniyle, hem **ReadXmlSchema** yöntemi hem de **InferSchema** **xmlReadMode** ile **ReadXml** yöntemi belgede her öğe için tablolar oluşturacak: **Kategoriler**, **CategoryID**, **CategoryName**, **Açıklama**, **Ürünler**, **ProductID**, **ReorderLevel**, ve **Durdurulan**.</span><span class="sxs-lookup"><span data-stu-id="15347-132">Because of the attributes specified for the elements in the preceding XML document, both the **ReadXmlSchema** method and the **ReadXml** method with an **XmlReadMode** of **InferSchema** would create tables for every element in the document: **Categories**, **CategoryID**, **CategoryName**, **Description**, **Products**, **ProductID**, **ReorderLevel**, and **Discontinued**.</span></span> <span data-ttu-id="15347-133">(Daha fazla bilgi için [bkz.](inferring-dataset-relational-structure-from-xml.md) Ancak, daha uygun bir yapı yalnızca **Kategoriler** ve **Ürünler** tabloları oluşturmak ve daha sonra **Kategoriler** tablosunda **CategoryID**, **CategoryName**ve **Açıklama** sütunları oluşturmak ve **Ürünler** tablosunda **ProductID**, **ReorderLevel**ve **Durdurulan** sütunlar olacaktır.</span><span class="sxs-lookup"><span data-stu-id="15347-133">(For more information, see [Inferring DataSet Relational Structure from XML](inferring-dataset-relational-structure-from-xml.md).) However, a more appropriate structure would be to create only the **Categories** and **Products** tables, and then to create **CategoryID**, **CategoryName**, and **Description** columns in the **Categories** table, and **ProductID**, **ReorderLevel**, and **Discontinued** columns in the **Products** table.</span></span> <span data-ttu-id="15347-134">Çıkarılan şemaXML öğeleri belirtilen öznitelikleri yoksayılsa emin olmak için, **InferXmlSchema** yöntemini kullanın ve aşağıdaki örnekte gösterildiği **gibi, ofis verileri** için göz ardı edilecek XML ad alanını belirtin.</span><span class="sxs-lookup"><span data-stu-id="15347-134">To ensure that the inferred schema ignores the attributes specified in the XML elements, use the **InferXmlSchema** method and specify the XML namespace for **officedata** to be ignored, as shown in the following example.</span></span>  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.InferXmlSchema("input_od.xml", New String() {"urn:schemas-microsoft-com:officedata"})  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.InferXmlSchema("input_od.xml", new string[] "urn:schemas-microsoft-com:officedata");  
```  
  
## <a name="see-also"></a><span data-ttu-id="15347-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="15347-135">See also</span></span>

- [<span data-ttu-id="15347-136">DataSet içinde XML kullanma</span><span class="sxs-lookup"><span data-stu-id="15347-136">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="15347-137">XML Şemasından (XSD) DataSet İlişkisel Yapısını Türetme</span><span class="sxs-lookup"><span data-stu-id="15347-137">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [<span data-ttu-id="15347-138">XML’den DataSet İlişkisel Yapısını Çıkarma</span><span class="sxs-lookup"><span data-stu-id="15347-138">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="15347-139">XML’den DataSet Yükleme</span><span class="sxs-lookup"><span data-stu-id="15347-139">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="15347-140">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="15347-140">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="15347-141">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="15347-141">ADO.NET Overview</span></span>](../ado-net-overview.md)
