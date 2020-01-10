---
title: Şema Derleme için XmlSchemaSet
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 55c4b175-3170-4071-9d60-dd5a42f79b54
ms.openlocfilehash: 55347de81c65b7390584415dd29044f4ca4ba02a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709822"
---
# <a name="xmlschemaset-for-schema-compilation"></a><span data-ttu-id="78363-102">Şema Derleme için XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="78363-102">XmlSchemaSet for Schema Compilation</span></span>
<span data-ttu-id="78363-103">XML şeması tanım dili (XSD) şemaları depolanabilecek ve doğrulanabilen bir önbellek <xref:System.Xml.Schema.XmlSchemaSet>açıklar.</span><span class="sxs-lookup"><span data-stu-id="78363-103">Describes the <xref:System.Xml.Schema.XmlSchemaSet>, a cache where XML Schema definition language (XSD) schemas can be stored and validated.</span></span>  
  
## <a name="the-xmlschemaset-class"></a><span data-ttu-id="78363-104">XmlSchemaSet sınıfı</span><span class="sxs-lookup"><span data-stu-id="78363-104">The XmlSchemaSet Class</span></span>  
 <span data-ttu-id="78363-105"><xref:System.Xml.Schema.XmlSchemaSet>, XML şeması tanım dili (XSD) şemaları depolanabilecek ve doğrulanabilen bir önbelleğidir.</span><span class="sxs-lookup"><span data-stu-id="78363-105">The <xref:System.Xml.Schema.XmlSchemaSet> is a cache where XML Schema definition language (XSD) schemas can be stored and validated.</span></span>  
  
 <span data-ttu-id="78363-106"><xref:System.Xml?displayProperty=nameWithType> sürüm 1,0 ' de, XML şemaları bir şema kitaplığı olarak bir <xref:System.Xml.Schema.XmlSchemaCollection> sınıfına yüklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="78363-106">In <xref:System.Xml?displayProperty=nameWithType> version 1.0, XML schemas were loaded into an <xref:System.Xml.Schema.XmlSchemaCollection> class as a library of schemas.</span></span> <span data-ttu-id="78363-107"><xref:System.Xml?displayProperty=nameWithType> sürüm 2,0 ' de, <xref:System.Xml.XmlValidatingReader> ve <xref:System.Xml.Schema.XmlSchemaCollection> sınıfları kullanımdan kaldırılmıştır ve sırasıyla <xref:System.Xml.XmlReader.Create%2A> yöntemlerle ve <xref:System.Xml.Schema.XmlSchemaSet> sınıfıyla değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="78363-107">In <xref:System.Xml?displayProperty=nameWithType> version 2.0, the <xref:System.Xml.XmlValidatingReader> and the <xref:System.Xml.Schema.XmlSchemaCollection> classes are obsolete, and have been replaced by the <xref:System.Xml.XmlReader.Create%2A> methods, and the <xref:System.Xml.Schema.XmlSchemaSet> class respectively.</span></span>  
  
 <span data-ttu-id="78363-108"><xref:System.Xml.Schema.XmlSchemaSet>, standart uyumluluk, performans ve kullanılmayan Microsoft XML-verileri azaltılmış (XDR) şema biçimi gibi birçok sorunu gidermeye yönelik olarak sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="78363-108">The <xref:System.Xml.Schema.XmlSchemaSet> has been introduced to fix a number of issues including standards compatibility, performance, and the obsolete Microsoft XML-Data Reduced (XDR) schema format.</span></span>  
  
 <span data-ttu-id="78363-109"><xref:System.Xml.Schema.XmlSchemaCollection> sınıfı ve <xref:System.Xml.Schema.XmlSchemaSet> sınıfı arasında bir karşılaştırma aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="78363-109">The following is a comparison between the <xref:System.Xml.Schema.XmlSchemaCollection> class and the <xref:System.Xml.Schema.XmlSchemaSet> class.</span></span>  
  
|<span data-ttu-id="78363-110">XmlSchemaCollection</span><span class="sxs-lookup"><span data-stu-id="78363-110">XmlSchemaCollection</span></span>|<span data-ttu-id="78363-111">XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="78363-111">XmlSchemaSet</span></span>|  
|-------------------------|------------------|  
|<span data-ttu-id="78363-112">Microsoft XDR ve W3C XML şemalarını destekler.</span><span class="sxs-lookup"><span data-stu-id="78363-112">Supports Microsoft XDR and W3C XML schemas.</span></span>|<span data-ttu-id="78363-113">Yalnızca W3C XML şemalarını destekler.</span><span class="sxs-lookup"><span data-stu-id="78363-113">Only supports W3C XML schemas.</span></span>|  
|<span data-ttu-id="78363-114"><xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> yöntemi çağrıldığında şemalar derlenir.</span><span class="sxs-lookup"><span data-stu-id="78363-114">Schemas are compiled when the <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> method is called.</span></span>|<span data-ttu-id="78363-115"><xref:System.Xml.Schema.XmlSchemaSet.Add%2A> yöntemi çağrıldığında şemalar derlenmez.</span><span class="sxs-lookup"><span data-stu-id="78363-115">Schemas are not compiled when the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method is called.</span></span> <span data-ttu-id="78363-116">Bu, şema kitaplığının oluşturulması sırasında bir performans geliştirmesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="78363-116">This provides a performance improvement during creation of the schema library.</span></span>|  
|<span data-ttu-id="78363-117">Her şema, "Schema Adaları" ile sonuçlanabileceğinden bağımsız bir derlenmiş sürüm oluşturur.</span><span class="sxs-lookup"><span data-stu-id="78363-117">Each schema generates an individual compiled version that can result in "schema islands."</span></span> <span data-ttu-id="78363-118">Sonuç olarak, tüm dahil ve içeri aktarmalar yalnızca o şemanın içinde kapsamlandırılır.</span><span class="sxs-lookup"><span data-stu-id="78363-118">As a result, all includes and imports are scoped only within that schema.</span></span>|<span data-ttu-id="78363-119">Derlenmiş şemalar, şemaların "kümesi" olan tek bir mantıksal şema oluşturur.</span><span class="sxs-lookup"><span data-stu-id="78363-119">Compiled schemas generate a single logical schema, a "set" of schemas.</span></span> <span data-ttu-id="78363-120">Kümesine eklenen bir şema içindeki tüm içeri aktarılan şemalar doğrudan kümesine eklenir.</span><span class="sxs-lookup"><span data-stu-id="78363-120">Any imported schemas within a schema that are added to the set are directly added to the set themselves.</span></span> <span data-ttu-id="78363-121">Bu, tüm türlerin tüm şemalarda kullanılabildiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="78363-121">This means that all types are available to all schemas.</span></span>|  
|<span data-ttu-id="78363-122">Koleksiyonda belirli bir hedef ad alanı için yalnızca bir şema bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="78363-122">Only one schema for a particular target namespace can exist in the collection.</span></span>|<span data-ttu-id="78363-123">Aynı hedef ad alanı için birden çok şema, tür çakışması olmadığı sürece eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="78363-123">Multiple schemas for the same target namespace can be added as long as there are no type conflicts.</span></span>|  
  
## <a name="migrating-to-the-xmlschemaset"></a><span data-ttu-id="78363-124">XmlSchemaSet 'e geçiş</span><span class="sxs-lookup"><span data-stu-id="78363-124">Migrating to the XmlSchemaSet</span></span>  
 <span data-ttu-id="78363-125">Aşağıdaki kod örneği, eski <xref:System.Xml.Schema.XmlSchemaCollection> sınıfından yeni <xref:System.Xml.Schema.XmlSchemaSet> sınıfına geçiş yapmak için bir kılavuz sağlar.</span><span class="sxs-lookup"><span data-stu-id="78363-125">The following code example provides a guide to migrating to the new <xref:System.Xml.Schema.XmlSchemaSet> class from the obsolete <xref:System.Xml.Schema.XmlSchemaCollection> class.</span></span> <span data-ttu-id="78363-126">Kod örneği, iki sınıf arasındaki aşağıdaki önemli farklılıkları gösterir.</span><span class="sxs-lookup"><span data-stu-id="78363-126">The code example illustrates the following major differences between the two classes.</span></span>  
  
- <span data-ttu-id="78363-127"><xref:System.Xml.Schema.XmlSchemaCollection> sınıfının <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> yönteminin aksine, şemalar <xref:System.Xml.Schema.XmlSchemaSet><xref:System.Xml.Schema.XmlSchemaSet.Add%2A> yöntemi çağrılırken derlenmez.</span><span class="sxs-lookup"><span data-stu-id="78363-127">Unlike the <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> method of the <xref:System.Xml.Schema.XmlSchemaCollection> class, schemas are not compiled when calling the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="78363-128"><xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> yöntemi, örnek kodda açıkça çağırılır.</span><span class="sxs-lookup"><span data-stu-id="78363-128">The <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet> is explicitly called in the example code.</span></span>  
  
- <span data-ttu-id="78363-129">Bir <xref:System.Xml.Schema.XmlSchemaSet>üzerinden yinelemek için <xref:System.Xml.Schema.XmlSchemaSet><xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> özelliğini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="78363-129">To iterate over an <xref:System.Xml.Schema.XmlSchemaSet>, you must use the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
 <span data-ttu-id="78363-130">Eski <xref:System.Xml.Schema.XmlSchemaCollection> kod örneği aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="78363-130">The following is the obsolete <xref:System.Xml.Schema.XmlSchemaCollection> code example.</span></span>  
  
```vb  
Dim schemaCollection As XmlSchemaCollection = New XmlSchemaCollection()  
schemaCollection.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd")  
schemaCollection.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd")  
  
Dim schema As XmlSchema  
  
For Each schema in schemaCollection  
  
   Console.WriteLine(schema.TargetNamespace)  
  
Next  
```  
  
```csharp  
XmlSchemaCollection schemaCollection = new XmlSchemaCollection();  
schemaCollection.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd");  
schemaCollection.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd");  
  
foreach(XmlSchema schema in schemaCollection)  
{  
   Console.WriteLine(schema.TargetNamespace);  
}  
```  
  
 <span data-ttu-id="78363-131">Aşağıda eşdeğer <xref:System.Xml.Schema.XmlSchemaSet> kod örneği verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="78363-131">The following is the equivalent <xref:System.Xml.Schema.XmlSchemaSet> code example.</span></span>  
  
```vb  
Dim schemaSet As XmlSchemaSet = New XmlSchemaSet()  
schemaSet.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd")  
schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd")  
schemaSet.Compile()  
  
Dim schema As XmlSchema  
  
For Each schema in schemaSet.Schemas()  
  
   Console.WriteLine(schema.TargetNamespace)  
  
Next  
```  
  
```csharp  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
schemaSet.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd");  
schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd");  
schemaSet.Compile();  
  
foreach(XmlSchema schema in schemaSet.Schemas())  
{  
   Console.WriteLine(schema.TargetNamespace);  
}  
```  
  
## <a name="adding-and-retrieving-schemas"></a><span data-ttu-id="78363-132">Şemaları ekleme ve alma</span><span class="sxs-lookup"><span data-stu-id="78363-132">Adding and Retrieving Schemas</span></span>  
 <span data-ttu-id="78363-133">Şemalar, <xref:System.Xml.Schema.XmlSchemaSet><xref:System.Xml.Schema.XmlSchemaSet.Add%2A> yöntemi kullanılarak bir <xref:System.Xml.Schema.XmlSchemaSet> eklenir.</span><span class="sxs-lookup"><span data-stu-id="78363-133">Schemas are added to an <xref:System.Xml.Schema.XmlSchemaSet> using the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="78363-134">Bir şema bir <xref:System.Xml.Schema.XmlSchemaSet>eklendiğinde, hedef ad alanı URI 'SI ile ilişkilendirilir.</span><span class="sxs-lookup"><span data-stu-id="78363-134">When a schema is added to an <xref:System.Xml.Schema.XmlSchemaSet>, it is associated with a target namespace URI.</span></span> <span data-ttu-id="78363-135">Hedef ad alanı URI 'SI <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> yöntemi için bir parametre olarak belirtilebilir veya hiçbir hedef ad alanı belirtilmemişse, <xref:System.Xml.Schema.XmlSchemaSet> şemada tanımlanan hedef ad alanını kullanır.</span><span class="sxs-lookup"><span data-stu-id="78363-135">The target namespace URI can either be specified as a parameter to the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method or if no target namespace is specified, the <xref:System.Xml.Schema.XmlSchemaSet> uses the target namespace defined in the schema.</span></span>  
  
 <span data-ttu-id="78363-136">Şemalar, <xref:System.Xml.Schema.XmlSchemaSet><xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> özelliğini kullanarak bir <xref:System.Xml.Schema.XmlSchemaSet> alınır.</span><span class="sxs-lookup"><span data-stu-id="78363-136">Schemas are retrieved from an <xref:System.Xml.Schema.XmlSchemaSet> using the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="78363-137"><xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> özelliği, <xref:System.Xml.Schema.XmlSchemaSet>bulunan <xref:System.Xml.Schema.XmlSchema> nesneleri üzerinde yineleme yapmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="78363-137">The <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet> allows you to iterate over the <xref:System.Xml.Schema.XmlSchema> objects contained in the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="78363-138"><xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> özelliği, <xref:System.Xml.Schema.XmlSchemaSet>içerilen tüm <xref:System.Xml.Schema.XmlSchema> nesneleri döndürür veya hedef ad alanı parametresi verildiğinde, hedef ad alanına ait tüm <xref:System.Xml.Schema.XmlSchema> nesnelerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="78363-138">The <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property either returns all the <xref:System.Xml.Schema.XmlSchema> objects contained in the <xref:System.Xml.Schema.XmlSchemaSet>, or, given a target namespace parameter, returns all the <xref:System.Xml.Schema.XmlSchema> objects that belong to the target namespace.</span></span> <span data-ttu-id="78363-139">`null` hedef ad alanı parametresi olarak belirtilmişse, <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> özelliği ad alanı olmayan tüm şemaları döndürür.</span><span class="sxs-lookup"><span data-stu-id="78363-139">If `null` is specified as the target namespace parameter, the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property returns all schemas without a namespace.</span></span>  
  
 <span data-ttu-id="78363-140">Aşağıdaki örnek, `http://www.contoso.com/books` ad alanındaki `books.xsd` şemasını bir <xref:System.Xml.Schema.XmlSchemaSet>ekler, <xref:System.Xml.Schema.XmlSchemaSet>`http://www.contoso.com/books` ad alanına ait olan tüm şemaları alır ve ardından bu şemaları <xref:System.Console>yazar.</span><span class="sxs-lookup"><span data-stu-id="78363-140">The following example adds the `books.xsd` schema in the `http://www.contoso.com/books` namespace to an <xref:System.Xml.Schema.XmlSchemaSet>, retrieves all schemas that belong to the `http://www.contoso.com/books` namespace from the <xref:System.Xml.Schema.XmlSchemaSet>, and then writes those schemas to the <xref:System.Console>.</span></span>  
  
```vb  
Dim schemaSet As XmlSchemaSet = New XmlSchemaSet  
schemaSet.Add("http://www.contoso.com/books", "books.xsd")  
  
Dim schema As XmlSchema  
  
For Each schema In schemaSet.Schemas("http://www.contoso.com/books")  
  
   schema.Write(Console.Out)  
  
Next  
```  
  
```csharp  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
schemaSet.Add("http://www.contoso.com/books", "books.xsd");  
  
foreach (XmlSchema schema in schemaSet.Schemas("http://www.contoso.com/books"))  
{  
   schema.Write(Console.Out);  
}  
```  
  
 <span data-ttu-id="78363-141"><xref:System.Xml.Schema.XmlSchemaSet> nesnesinden şemaları ekleme ve alma hakkında daha fazla bilgi için <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> yöntemine ve <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> özellik başvurusu belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="78363-141">For more information about adding and retrieving schemas from an <xref:System.Xml.Schema.XmlSchemaSet> object, see the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method and the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property reference documentation.</span></span>  
  
## <a name="compiling-schemas"></a><span data-ttu-id="78363-142">Şemaları derleme</span><span class="sxs-lookup"><span data-stu-id="78363-142">Compiling Schemas</span></span>  
 <span data-ttu-id="78363-143">Bir <xref:System.Xml.Schema.XmlSchemaSet> şemaları, <xref:System.Xml.Schema.XmlSchemaSet><xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> yöntemi tarafından bir mantıksal şemaya derlenir.</span><span class="sxs-lookup"><span data-stu-id="78363-143">Schemas in an <xref:System.Xml.Schema.XmlSchemaSet> are compiled into one logical schema by the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="78363-144">Eski <xref:System.Xml.Schema.XmlSchemaCollection> sınıfından farklı olarak, <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> yöntemi çağrıldığında şemalar derlenmez.</span><span class="sxs-lookup"><span data-stu-id="78363-144">Unlike the obsolete <xref:System.Xml.Schema.XmlSchemaCollection> class, schemas are not compiled when the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method is called.</span></span>  
  
 <span data-ttu-id="78363-145"><xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> yöntemi başarıyla yürütülüyorsa, <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> özelliği `true`olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="78363-145">If the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method executes successfully, the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet> is set to `true`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="78363-146"><xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> özelliği, şemalar <xref:System.Xml.Schema.XmlSchemaSet>sırada düzenleniyorsa etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="78363-146">The <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property is not affected if schemas are edited while in the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="78363-147"><xref:System.Xml.Schema.XmlSchemaSet> tek tek şemaların güncelleştirmeleri izlenmez.</span><span class="sxs-lookup"><span data-stu-id="78363-147">Updates of the individual schemas in the <xref:System.Xml.Schema.XmlSchemaSet> are not tracked.</span></span> <span data-ttu-id="78363-148">Sonuç olarak, <xref:System.Xml.Schema.XmlSchemaSet>hiçbir şema eklenmemiş veya kaldırılmadığı sürece, <xref:System.Xml.Schema.XmlSchemaSet> bulunan şemalardan biri değiştirilmiş olsa bile <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> özelliği `true` olabilir.</span><span class="sxs-lookup"><span data-stu-id="78363-148">As a result, the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property can be `true` even though one of the schemas contained in the <xref:System.Xml.Schema.XmlSchemaSet> has been altered, as long as no schemas were added or removed from the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
 <span data-ttu-id="78363-149">Aşağıdaki örnek `books.xsd` dosyasını <xref:System.Xml.Schema.XmlSchemaSet> ekler ve sonra <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="78363-149">The following example adds the `books.xsd` file to the <xref:System.Xml.Schema.XmlSchemaSet> and then calls the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method.</span></span>  
  
```vb  
Dim schemaSet As XmlSchemaSet = New XmlSchemaSet()  
schemaSet.Add("http://www.contoso.com/books", "books.xsd")  
schemaSet.Compile()  
```  
  
```csharp  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
schemaSet.Add("http://www.contoso.com/books", "books.xsd");  
schemaSet.Compile();  
```  
  
 <span data-ttu-id="78363-150"><xref:System.Xml.Schema.XmlSchemaSet>şemaları derleme hakkında daha fazla bilgi için <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> yöntemi başvuru belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="78363-150">For more information about compiling schemas in an <xref:System.Xml.Schema.XmlSchemaSet>, see the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method reference documentation.</span></span>  
  
## <a name="reprocessing-schemas"></a><span data-ttu-id="78363-151">Şemaları yeniden işleme</span><span class="sxs-lookup"><span data-stu-id="78363-151">Reprocessing Schemas</span></span>  
 <span data-ttu-id="78363-152">Bir <xref:System.Xml.Schema.XmlSchemaSet> şemayı yeniden işlemek, <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> yöntemi çağrıldığında bir şemada gerçekleştirilen tüm ön işleme adımlarını gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="78363-152">Reprocessing a schema in an <xref:System.Xml.Schema.XmlSchemaSet> performs all the preprocessing steps performed on a schema when the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet> is called.</span></span> <span data-ttu-id="78363-153"><xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> yöntemine yapılan çağrı başarılı olursa <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> özelliği `false`olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="78363-153">If the call to the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method is successful, the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet> is set to `false`.</span></span>  
  
 <span data-ttu-id="78363-154"><xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> yöntemi, <xref:System.Xml.Schema.XmlSchemaSet> derlemeyi gerçekleştirdikten sonra <xref:System.Xml.Schema.XmlSchemaSet> bir şema değiştirildiğinde kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="78363-154">The <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method should be used when a schema in the <xref:System.Xml.Schema.XmlSchemaSet> has been modified after the <xref:System.Xml.Schema.XmlSchemaSet> has performed compilation.</span></span>  
  
 <span data-ttu-id="78363-155">Aşağıdaki örnek, <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> yöntemi kullanılarak <xref:System.Xml.Schema.XmlSchemaSet> eklenen bir şemanın yeniden işlenmesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="78363-155">The following example illustrates reprocessing a schema added to the <xref:System.Xml.Schema.XmlSchemaSet> using the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method.</span></span> <span data-ttu-id="78363-156"><xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> yöntemi kullanılarak derlendikten ve <xref:System.Xml.Schema.XmlSchemaSet> eklenen şema değiştirilirse, `true` bir şema değiştirilse bile <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> özelliği <xref:System.Xml.Schema.XmlSchemaSet> olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="78363-156">After the <xref:System.Xml.Schema.XmlSchemaSet> is compiled using the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method, and the schema added to the <xref:System.Xml.Schema.XmlSchemaSet> is modified, the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property is set to `true` even though a schema in the <xref:System.Xml.Schema.XmlSchemaSet> has been modified.</span></span> <span data-ttu-id="78363-157"><xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> yöntemini çağırmak, <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> yöntemi tarafından gerçekleştirilen tüm ön işleme gerçekleştirir ve <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> özelliğini `false`olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="78363-157">Calling the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method performs all the preprocessing performed by the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method, and sets the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property to `false`.</span></span>  
  
```vb  
Dim schemaSet As XmlSchemaSet = New XmlSchemaSet()  
Dim schema As XmlSchema = schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd")  
schemaSet.Compile()  
  
Dim element As XmlSchemaElement = New XmlSchemaElement()  
schema.Items.Add(element)  
element.Name = "book"  
element.SchemaTypeName = New XmlQualifiedName("string", "http://www.w3.org/2001/XMLSchema")  
  
schemaSet.Reprocess(schema)  
```  
  
```csharp  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
XmlSchema schema = schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd");  
schemaSet.Compile();  
  
XmlSchemaElement element = new XmlSchemaElement();  
schema.Items.Add(element);  
element.Name = "book";  
element.SchemaTypeName = new XmlQualifiedName("string", "http://www.w3.org/2001/XMLSchema");  
  
schemaSet.Reprocess(schema);  
```  
  
 <span data-ttu-id="78363-158">Bir <xref:System.Xml.Schema.XmlSchemaSet>şemayı yeniden işleme hakkında daha fazla bilgi için <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> yöntemi başvuru belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="78363-158">For more information about reprocessing a schema in an <xref:System.Xml.Schema.XmlSchemaSet>, see the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method reference documentation.</span></span>  
  
## <a name="checking-for-a-schema"></a><span data-ttu-id="78363-159">Şema denetleniyor</span><span class="sxs-lookup"><span data-stu-id="78363-159">Checking for a Schema</span></span>  
 <span data-ttu-id="78363-160">Bir şemanın bir <xref:System.Xml.Schema.XmlSchemaSet>dahil olup olmadığını denetlemek için <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="78363-160">You can use the <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet> to check if a schema is contained within an <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="78363-161"><xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> yöntemi, denetlenecek bir hedef ad alanı ya da bir <xref:System.Xml.Schema.XmlSchema> nesnesi alır.</span><span class="sxs-lookup"><span data-stu-id="78363-161">The <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> method takes either a target namespace or an <xref:System.Xml.Schema.XmlSchema> object to check for.</span></span> <span data-ttu-id="78363-162">Her iki durumda da, şema <xref:System.Xml.Schema.XmlSchemaSet>içindeyse <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> yöntemi `true` döndürür; Aksi takdirde, `false`döndürür.</span><span class="sxs-lookup"><span data-stu-id="78363-162">In either case, the <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> method returns `true` if the schema is contained within the <xref:System.Xml.Schema.XmlSchemaSet>; otherwise, it returns `false`.</span></span>  
  
 <span data-ttu-id="78363-163">Bir şemayı denetleme hakkında daha fazla bilgi için <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> yöntemi başvuru belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="78363-163">For more information about checking for a schema, see the <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> method reference documentation.</span></span>  
  
## <a name="removing-schemas"></a><span data-ttu-id="78363-164">Şemaları kaldırma</span><span class="sxs-lookup"><span data-stu-id="78363-164">Removing Schemas</span></span>  
 <span data-ttu-id="78363-165">Şemalar, <xref:System.Xml.Schema.XmlSchemaSet><xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> ve <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> yöntemleri kullanılarak bir <xref:System.Xml.Schema.XmlSchemaSet> kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="78363-165">Schemas are removed from an <xref:System.Xml.Schema.XmlSchemaSet> using the <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> and <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> methods of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="78363-166"><xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> yöntemi, belirtilen şemayı <xref:System.Xml.Schema.XmlSchemaSet>kaldırır, ancak <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> yöntemi belirtilen şemayı ve <xref:System.Xml.Schema.XmlSchemaSet>içeri aktardığı tüm şemaları kaldırır.</span><span class="sxs-lookup"><span data-stu-id="78363-166">The <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> method removes the specified schema from the <xref:System.Xml.Schema.XmlSchemaSet>, while the <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> method removes the specified schema and all the schemas it imports from the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
 <span data-ttu-id="78363-167">Aşağıdaki örnek, bir <xref:System.Xml.Schema.XmlSchemaSet>birden çok şema eklemeyi, sonra şemalardan birini ve içeri aktardığı tüm şemaları kaldırmak için <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> yöntemini kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="78363-167">The following example illustrates adding multiple schemas to an <xref:System.Xml.Schema.XmlSchemaSet>, then using the <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> method to remove one of the schemas and all the schemas it imports.</span></span>  
  
```vb  
Dim schemaSet As XmlSchemaSet = New XmlSchemaSet()  
schemaSet.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd")  
schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd")  
schemaSet.Add("http://www.contoso.com/music", "http://www.contoso.com/music.xsd")  
  
Dim schema As XmlSchema  
  
For Each schema In schemaSet.Schemas()  
  
   If schema.TargetNamespace = "http://www.contoso.com/music" Then  
      schemaSet.RemoveRecursive(schema)  
   End If  
  
Next  
```  
  
```csharp  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
schemaSet.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd");  
schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd");  
schemaSet.Add("http://www.contoso.com/music", "http://www.contoso.com/music.xsd");  
  
foreach (XmlSchema schema in schemaSet.Schemas())  
{  
   if (schema.TargetNamespace == "http://www.contoso.com/music")  
   {  
      schemaSet.RemoveRecursive(schema);  
   }  
}  
```  
  
 <span data-ttu-id="78363-168"><xref:System.Xml.Schema.XmlSchemaSet>şemaları kaldırma hakkında daha fazla bilgi için <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> ve <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> yöntemleri başvuru belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="78363-168">For more information about removing schemas from an <xref:System.Xml.Schema.XmlSchemaSet>, see the <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> and <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> methods reference documentation.</span></span>  
  
## <a name="schema-resolution-and-xsimport"></a><span data-ttu-id="78363-169">Şema çözünürlüğü ve xs: import</span><span class="sxs-lookup"><span data-stu-id="78363-169">Schema Resolution and xs:import</span></span>  
 <span data-ttu-id="78363-170">Aşağıdaki örneklerde, bir <xref:System.Xml.Schema.XmlSchemaSet>verilen bir ad alanı için birden çok şema varsa şemaları içeri aktarmaya yönelik <xref:System.Xml.Schema.XmlSchemaSet> davranışı açıklanır.</span><span class="sxs-lookup"><span data-stu-id="78363-170">The following examples describe the <xref:System.Xml.Schema.XmlSchemaSet> behavior for importing schemas when multiple schemas for a given namespace exist in an <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
 <span data-ttu-id="78363-171">Örneğin, `http://www.contoso.com` ad alanı için birden çok şema içeren bir <xref:System.Xml.Schema.XmlSchemaSet> düşünün.</span><span class="sxs-lookup"><span data-stu-id="78363-171">For example, consider an <xref:System.Xml.Schema.XmlSchemaSet> that contains multiple schemas for the `http://www.contoso.com` namespace.</span></span> <span data-ttu-id="78363-172">Aşağıdaki `xs:import` yönergesine sahip bir şema <xref:System.Xml.Schema.XmlSchemaSet>eklenmiş.</span><span class="sxs-lookup"><span data-stu-id="78363-172">A schema with the following `xs:import` directive is added to the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
```xml  
<xs:import namespace="http://www.contoso.com" schemaLocation="http://www.contoso.com/schema.xsd" />  
```  
  
 <span data-ttu-id="78363-173"><xref:System.Xml.Schema.XmlSchemaSet>, `http://www.contoso.com/schema.xsd` URL 'sinden yükleyerek `http://www.contoso.com` ad alanı için bir şemayı içeri aktarmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="78363-173">The <xref:System.Xml.Schema.XmlSchemaSet> attempts to import a schema for the `http://www.contoso.com` namespace by loading it from the `http://www.contoso.com/schema.xsd` URL.</span></span> <span data-ttu-id="78363-174"><xref:System.Xml.Schema.XmlSchemaSet>`http://www.contoso.com` ad alanı için başka bir şema belgesi olsa da, yalnızca şema belgesinde belirtilen şema bildirimi ve türleri içeri aktarma şemasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="78363-174">Only the schema declaration and types declared in the schema document are available in the importing schema, even though there are other schema documents for the `http://www.contoso.com` namespace in the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="78363-175">`schema.xsd` dosyası `http://www.contoso.com/schema.xsd` URL 'sinde bulunamıyorsa, `http://www.contoso.com` ad alanı için bir şema içeri aktarma şemasına içeri aktarılmaz.</span><span class="sxs-lookup"><span data-stu-id="78363-175">If the `schema.xsd` file cannot be located at the `http://www.contoso.com/schema.xsd` URL, no schema for the `http://www.contoso.com` namespace is imported into the importing schema.</span></span>  
  
## <a name="validating-xml-documents"></a><span data-ttu-id="78363-176">XML belgelerini doğrulama</span><span class="sxs-lookup"><span data-stu-id="78363-176">Validating XML Documents</span></span>  
 <span data-ttu-id="78363-177">XML belgeleri, bir <xref:System.Xml.Schema.XmlSchemaSet>şemalara karşı doğrulanabilir.</span><span class="sxs-lookup"><span data-stu-id="78363-177">XML documents can be validated against schemas in an <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="78363-178">Bir <xref:System.Xml.XmlReaderSettings> nesnesinin <xref:System.Xml.Schema.XmlSchemaSet><xref:System.Xml.XmlReaderSettings.Schemas%2A> özelliğine bir şema ekleyerek veya bir <xref:System.Xml.XmlReaderSettings.Schemas%2A> nesnesinin <xref:System.Xml.XmlReaderSettings> özelliğine bir <xref:System.Xml.Schema.XmlSchemaSet> ekleyerek bir XML belgesini doğrularsınız.</span><span class="sxs-lookup"><span data-stu-id="78363-178">You validate an XML document by adding a schema to the <xref:System.Xml.Schema.XmlSchemaSet><xref:System.Xml.XmlReaderSettings.Schemas%2A> property of an <xref:System.Xml.XmlReaderSettings> object, or by adding an <xref:System.Xml.Schema.XmlSchemaSet> to the <xref:System.Xml.XmlReaderSettings.Schemas%2A> property of an <xref:System.Xml.XmlReaderSettings> object.</span></span> <span data-ttu-id="78363-179"><xref:System.Xml.XmlReaderSettings> nesnesi daha sonra bir <xref:System.Xml.XmlReader> nesnesi oluşturmak ve XML belgesini doğrulamak için <xref:System.Xml.XmlReader> sınıfının <xref:System.Xml.XmlReader.Create%2A> yöntemi tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="78363-179">The <xref:System.Xml.XmlReaderSettings> object is then used by the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> class to create an <xref:System.Xml.XmlReader> object and validate the XML document.</span></span>  
  
 <span data-ttu-id="78363-180"><xref:System.Xml.Schema.XmlSchemaSet>kullanarak XML belgelerinin doğrulanması hakkında daha fazla bilgi için, bkz. [XmlSchemaSet Ile xml şeması (xsd) doğrulaması](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemaset.md).</span><span class="sxs-lookup"><span data-stu-id="78363-180">For more information about validating XML documents using an <xref:System.Xml.Schema.XmlSchemaSet>, see [XML Schema (XSD) Validation with XmlSchemaSet](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemaset.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78363-181">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="78363-181">See also</span></span>

- <xref:System.Xml.Schema.XmlSchemaSet.Add%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A>
- [<span data-ttu-id="78363-182">Şema önbelleği olarak XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="78363-182">XmlSchemaSet as a Schema Cache</span></span>](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
- [<span data-ttu-id="78363-183">XmlSchemaSet ile XML Şeması (XSD) Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="78363-183">XML Schema (XSD) Validation with XmlSchemaSet</span></span>](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemaset.md)
