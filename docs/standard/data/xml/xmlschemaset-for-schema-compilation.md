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
# <a name="xmlschemaset-for-schema-compilation"></a><span data-ttu-id="d9c28-102">Şema Derleme için XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="d9c28-102">XmlSchemaSet for Schema Compilation</span></span>
<span data-ttu-id="d9c28-103"><xref:System.Xml.Schema.XmlSchemaSet>XML şeması tanım DILI (xsd) şemaları depolanabilecek ve doğrulanabilen bir önbellek tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d9c28-103">Describes the <xref:System.Xml.Schema.XmlSchemaSet>, a cache where XML Schema definition language (XSD) schemas can be stored and validated.</span></span>  
  
## <a name="the-xmlschemaset-class"></a><span data-ttu-id="d9c28-104">XmlSchemaSet sınıfı</span><span class="sxs-lookup"><span data-stu-id="d9c28-104">The XmlSchemaSet Class</span></span>  
 <span data-ttu-id="d9c28-105"><xref:System.Xml.Schema.XmlSchemaSet> XML şeması tanım DILI (xsd) şemaları depolanabilecek ve doğrulanabilen bir önbelleğidir.</span><span class="sxs-lookup"><span data-stu-id="d9c28-105">The <xref:System.Xml.Schema.XmlSchemaSet> is a cache where XML Schema definition language (XSD) schemas can be stored and validated.</span></span>  
  
 <span data-ttu-id="d9c28-106">Sürüm <xref:System.Xml?displayProperty=nameWithType> 1,0 ' de, XML şemaları bir <xref:System.Xml.Schema.XmlSchemaCollection> sınıfa bir şema kitaplığı olarak yüklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="d9c28-106">In <xref:System.Xml?displayProperty=nameWithType> version 1.0, XML schemas were loaded into an <xref:System.Xml.Schema.XmlSchemaCollection> class as a library of schemas.</span></span> <span data-ttu-id="d9c28-107">Sürüm <xref:System.Xml?displayProperty=nameWithType> 2,0 ' de, <xref:System.Xml.XmlValidatingReader> ve <xref:System.Xml.Schema.XmlSchemaCollection> sınıfları kullanılmıyor ve sırasıyla <xref:System.Xml.XmlReader.Create%2A> Yöntemler ve <xref:System.Xml.Schema.XmlSchemaSet> sınıf ile değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d9c28-107">In <xref:System.Xml?displayProperty=nameWithType> version 2.0, the <xref:System.Xml.XmlValidatingReader> and the <xref:System.Xml.Schema.XmlSchemaCollection> classes are obsolete, and have been replaced by the <xref:System.Xml.XmlReader.Create%2A> methods, and the <xref:System.Xml.Schema.XmlSchemaSet> class respectively.</span></span>  
  
 <span data-ttu-id="d9c28-108">, <xref:System.Xml.Schema.XmlSchemaSet> Standart uyumluluk, performans ve kullanılmayan Microsoft XML verileri AZALTıLMıŞ (xdr) şema biçimi gibi birçok sorunu gidermeye yönelik olarak sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="d9c28-108">The <xref:System.Xml.Schema.XmlSchemaSet> has been introduced to fix a number of issues including standards compatibility, performance, and the obsolete Microsoft XML-Data Reduced (XDR) schema format.</span></span>  
  
 <span data-ttu-id="d9c28-109">Aşağıda, <xref:System.Xml.Schema.XmlSchemaCollection> sınıfı ve <xref:System.Xml.Schema.XmlSchemaSet> sınıfı arasında bir karşılaştırma bulunur.</span><span class="sxs-lookup"><span data-stu-id="d9c28-109">The following is a comparison between the <xref:System.Xml.Schema.XmlSchemaCollection> class and the <xref:System.Xml.Schema.XmlSchemaSet> class.</span></span>  
  
|<span data-ttu-id="d9c28-110">XmlSchemaCollection</span><span class="sxs-lookup"><span data-stu-id="d9c28-110">XmlSchemaCollection</span></span>|<span data-ttu-id="d9c28-111">XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="d9c28-111">XmlSchemaSet</span></span>|  
|-------------------------|------------------|  
|<span data-ttu-id="d9c28-112">Microsoft XDR ve W3C XML şemalarını destekler.</span><span class="sxs-lookup"><span data-stu-id="d9c28-112">Supports Microsoft XDR and W3C XML schemas.</span></span>|<span data-ttu-id="d9c28-113">Yalnızca W3C XML şemalarını destekler.</span><span class="sxs-lookup"><span data-stu-id="d9c28-113">Only supports W3C XML schemas.</span></span>|  
|<span data-ttu-id="d9c28-114">Şemaları, <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> yöntemi çağrıldığında derlenir.</span><span class="sxs-lookup"><span data-stu-id="d9c28-114">Schemas are compiled when the <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> method is called.</span></span>|<span data-ttu-id="d9c28-115"><xref:System.Xml.Schema.XmlSchemaSet.Add%2A> Yöntem çağrıldığında şemalar derlenmez.</span><span class="sxs-lookup"><span data-stu-id="d9c28-115">Schemas are not compiled when the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method is called.</span></span> <span data-ttu-id="d9c28-116">Bu, şema kitaplığının oluşturulması sırasında bir performans geliştirmesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="d9c28-116">This provides a performance improvement during creation of the schema library.</span></span>|  
|<span data-ttu-id="d9c28-117">Her şema, "Schema Adaları" ile sonuçlanabileceğinden bağımsız bir derlenmiş sürüm oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d9c28-117">Each schema generates an individual compiled version that can result in "schema islands."</span></span> <span data-ttu-id="d9c28-118">Sonuç olarak, tüm dahil ve içeri aktarmalar yalnızca o şemanın içinde kapsamlandırılır.</span><span class="sxs-lookup"><span data-stu-id="d9c28-118">As a result, all includes and imports are scoped only within that schema.</span></span>|<span data-ttu-id="d9c28-119">Derlenmiş şemalar, şemaların "kümesi" olan tek bir mantıksal şema oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d9c28-119">Compiled schemas generate a single logical schema, a "set" of schemas.</span></span> <span data-ttu-id="d9c28-120">Kümesine eklenen bir şema içindeki tüm içeri aktarılan şemalar doğrudan kümesine eklenir.</span><span class="sxs-lookup"><span data-stu-id="d9c28-120">Any imported schemas within a schema that are added to the set are directly added to the set themselves.</span></span> <span data-ttu-id="d9c28-121">Bu, tüm türlerin tüm şemalarda kullanılabildiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="d9c28-121">This means that all types are available to all schemas.</span></span>|  
|<span data-ttu-id="d9c28-122">Koleksiyonda belirli bir hedef ad alanı için yalnızca bir şema bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="d9c28-122">Only one schema for a particular target namespace can exist in the collection.</span></span>|<span data-ttu-id="d9c28-123">Aynı hedef ad alanı için birden çok şema, tür çakışması olmadığı sürece eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="d9c28-123">Multiple schemas for the same target namespace can be added as long as there are no type conflicts.</span></span>|  
  
## <a name="migrating-to-the-xmlschemaset"></a><span data-ttu-id="d9c28-124">XmlSchemaSet 'e geçiş</span><span class="sxs-lookup"><span data-stu-id="d9c28-124">Migrating to the XmlSchemaSet</span></span>  
 <span data-ttu-id="d9c28-125">Aşağıdaki kod örneği, eski <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.Schema.XmlSchemaCollection> sınıftan yeni sınıfa geçiş yapmak için bir kılavuz sağlar.</span><span class="sxs-lookup"><span data-stu-id="d9c28-125">The following code example provides a guide to migrating to the new <xref:System.Xml.Schema.XmlSchemaSet> class from the obsolete <xref:System.Xml.Schema.XmlSchemaCollection> class.</span></span> <span data-ttu-id="d9c28-126">Kod örneği, iki sınıf arasındaki aşağıdaki önemli farklılıkları gösterir.</span><span class="sxs-lookup"><span data-stu-id="d9c28-126">The code example illustrates the following major differences between the two classes.</span></span>  
  
- <span data-ttu-id="d9c28-127"><xref:System.Xml.Schema.XmlSchemaCollection> Sınıfının <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> yönteminden farklı olarak,, <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> <xref:System.Xml.Schema.XmlSchemaSet>yöntemi çağrılırken şemalar derlenmez.</span><span class="sxs-lookup"><span data-stu-id="d9c28-127">Unlike the <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> method of the <xref:System.Xml.Schema.XmlSchemaCollection> class, schemas are not compiled when calling the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="d9c28-128"><xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> Yöntemi <xref:System.Xml.Schema.XmlSchemaSet> , örnek kodda açıkça çağırılır.</span><span class="sxs-lookup"><span data-stu-id="d9c28-128">The <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet> is explicitly called in the example code.</span></span>  
  
- <span data-ttu-id="d9c28-129">Bir <xref:System.Xml.Schema.XmlSchemaSet>üzerinde yinelemek için, öğesinin <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> özelliğini kullanmanız gerekir. <xref:System.Xml.Schema.XmlSchemaSet></span><span class="sxs-lookup"><span data-stu-id="d9c28-129">To iterate over an <xref:System.Xml.Schema.XmlSchemaSet>, you must use the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
 <span data-ttu-id="d9c28-130">Eski <xref:System.Xml.Schema.XmlSchemaCollection> kod örneği aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d9c28-130">The following is the obsolete <xref:System.Xml.Schema.XmlSchemaCollection> code example.</span></span>  
  
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
  
 <span data-ttu-id="d9c28-131">Aşağıda eşdeğer <xref:System.Xml.Schema.XmlSchemaSet> kod örneği verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d9c28-131">The following is the equivalent <xref:System.Xml.Schema.XmlSchemaSet> code example.</span></span>  
  
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
  
## <a name="adding-and-retrieving-schemas"></a><span data-ttu-id="d9c28-132">Şemaları ekleme ve alma</span><span class="sxs-lookup"><span data-stu-id="d9c28-132">Adding and Retrieving Schemas</span></span>  
 <span data-ttu-id="d9c28-133">Şemaları, <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> <xref:System.Xml.Schema.XmlSchemaSet>öğesinin yöntemi kullanılarak öğesine eklenir.</span><span class="sxs-lookup"><span data-stu-id="d9c28-133">Schemas are added to an <xref:System.Xml.Schema.XmlSchemaSet> using the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="d9c28-134">Bir şema bir <xref:System.Xml.Schema.XmlSchemaSet>öğesine eklendiğinde, hedef ad alanı URI 'si ile ilişkilendirilir.</span><span class="sxs-lookup"><span data-stu-id="d9c28-134">When a schema is added to an <xref:System.Xml.Schema.XmlSchemaSet>, it is associated with a target namespace URI.</span></span> <span data-ttu-id="d9c28-135">Hedef ad alanı URI 'SI <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> metodun bir parametresi olarak belirtilebilir ya da hiçbir hedef ad alanı belirtilmemişse, şemada tanımlanan hedef ad alanını <xref:System.Xml.Schema.XmlSchemaSet> kullanır.</span><span class="sxs-lookup"><span data-stu-id="d9c28-135">The target namespace URI can either be specified as a parameter to the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method or if no target namespace is specified, the <xref:System.Xml.Schema.XmlSchemaSet> uses the target namespace defined in the schema.</span></span>  
  
 <span data-ttu-id="d9c28-136">Şemaları, <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> <xref:System.Xml.Schema.XmlSchemaSet>öğesinin özelliğini kullanarak bir öğesinden alınır.</span><span class="sxs-lookup"><span data-stu-id="d9c28-136">Schemas are retrieved from an <xref:System.Xml.Schema.XmlSchemaSet> using the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="d9c28-137">Öğesinin <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> özelliği içinde yer <xref:System.Xml.Schema.XmlSchemaSet> alan <xref:System.Xml.Schema.XmlSchema> nesneler üzerinde yineleme yapmanızı sağlar <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="d9c28-137">The <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet> allows you to iterate over the <xref:System.Xml.Schema.XmlSchema> objects contained in the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="d9c28-138"><xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> Özelliği, veya içinde <xref:System.Xml.Schema.XmlSchemaSet>içerilen tüm <xref:System.Xml.Schema.XmlSchema> nesneleri döndürür veya hedef ad alanı parametresi verildiğinde, hedef ad alanına ait tüm <xref:System.Xml.Schema.XmlSchema> nesneleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="d9c28-138">The <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property either returns all the <xref:System.Xml.Schema.XmlSchema> objects contained in the <xref:System.Xml.Schema.XmlSchemaSet>, or, given a target namespace parameter, returns all the <xref:System.Xml.Schema.XmlSchema> objects that belong to the target namespace.</span></span> <span data-ttu-id="d9c28-139">`null` Hedef ad alanı parametresi olarak belirtilmişse, <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> özelliği ad alanı olmayan tüm şemaları döndürür.</span><span class="sxs-lookup"><span data-stu-id="d9c28-139">If `null` is specified as the target namespace parameter, the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property returns all schemas without a namespace.</span></span>  
  
 <span data-ttu-id="d9c28-140">Aşağıdaki örnek, `books.xsd` `http://www.contoso.com/books` <xref:System.Xml.Schema.XmlSchemaSet>ad alanındaki şemayı öğesine ekler, öğesinden `http://www.contoso.com/books` <xref:System.Xml.Schema.XmlSchemaSet>ad alanına ait olan tüm şemaları alır ve ardından bu şemaları öğesine yazar. <xref:System.Console></span><span class="sxs-lookup"><span data-stu-id="d9c28-140">The following example adds the `books.xsd` schema in the `http://www.contoso.com/books` namespace to an <xref:System.Xml.Schema.XmlSchemaSet>, retrieves all schemas that belong to the `http://www.contoso.com/books` namespace from the <xref:System.Xml.Schema.XmlSchemaSet>, and then writes those schemas to the <xref:System.Console>.</span></span>  
  
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
  
 <span data-ttu-id="d9c28-141">Bir <xref:System.Xml.Schema.XmlSchemaSet> nesneden şemaları ekleme ve alma hakkında daha fazla bilgi için, bkz. <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> yöntemi ve <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> özellik başvurusu belgeleri.</span><span class="sxs-lookup"><span data-stu-id="d9c28-141">For more information about adding and retrieving schemas from an <xref:System.Xml.Schema.XmlSchemaSet> object, see the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method and the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property reference documentation.</span></span>  
  
## <a name="compiling-schemas"></a><span data-ttu-id="d9c28-142">Şemaları derleme</span><span class="sxs-lookup"><span data-stu-id="d9c28-142">Compiling Schemas</span></span>  
 <span data-ttu-id="d9c28-143">İçindeki <xref:System.Xml.Schema.XmlSchemaSet> şemalar, <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> <xref:System.Xml.Schema.XmlSchemaSet>yöntemi tarafından bir mantıksal şemaya derlenir.</span><span class="sxs-lookup"><span data-stu-id="d9c28-143">Schemas in an <xref:System.Xml.Schema.XmlSchemaSet> are compiled into one logical schema by the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d9c28-144">Eski <xref:System.Xml.Schema.XmlSchemaCollection> sınıftan farklı olarak, <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> yöntem çağrıldığında şemalar derlenmez.</span><span class="sxs-lookup"><span data-stu-id="d9c28-144">Unlike the obsolete <xref:System.Xml.Schema.XmlSchemaCollection> class, schemas are not compiled when the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method is called.</span></span>  
  
 <span data-ttu-id="d9c28-145"><xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> Yöntem başarıyla yürütülüyorsa öğesinin <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> <xref:System.Xml.Schema.XmlSchemaSet> özelliği olarak `true`ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="d9c28-145">If the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method executes successfully, the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet> is set to `true`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d9c28-146">İçinde <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> şemalar düzenlenirse Özellik etkilenmez <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="d9c28-146">The <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property is not affected if schemas are edited while in the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="d9c28-147">İçindeki <xref:System.Xml.Schema.XmlSchemaSet> tek tek şemaların güncelleştirmeleri izlenmez.</span><span class="sxs-lookup"><span data-stu-id="d9c28-147">Updates of the individual schemas in the <xref:System.Xml.Schema.XmlSchemaSet> are not tracked.</span></span> <span data-ttu-id="d9c28-148">Sonuç <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> `true` olarak, içinde <xref:System.Xml.Schema.XmlSchemaSet> bulunan şemalardan biri, ' den eklenen veya kaldırılan hiçbir şema olmadığı sürece değiştirilmiş olabilir. <xref:System.Xml.Schema.XmlSchemaSet></span><span class="sxs-lookup"><span data-stu-id="d9c28-148">As a result, the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property can be `true` even though one of the schemas contained in the <xref:System.Xml.Schema.XmlSchemaSet> has been altered, as long as no schemas were added or removed from the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
 <span data-ttu-id="d9c28-149">Aşağıdaki örnek `books.xsd` dosyasını öğesine ekler <xref:System.Xml.Schema.XmlSchemaSet> ve sonra <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="d9c28-149">The following example adds the `books.xsd` file to the <xref:System.Xml.Schema.XmlSchemaSet> and then calls the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method.</span></span>  
  
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
  
 <span data-ttu-id="d9c28-150">İçindeki <xref:System.Xml.Schema.XmlSchemaSet>şemaları derleme hakkında daha fazla bilgi için bkz. <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> Yöntem başvurusu belgeleri.</span><span class="sxs-lookup"><span data-stu-id="d9c28-150">For more information about compiling schemas in an <xref:System.Xml.Schema.XmlSchemaSet>, see the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method reference documentation.</span></span>  
  
## <a name="reprocessing-schemas"></a><span data-ttu-id="d9c28-151">Şemaları yeniden işleme</span><span class="sxs-lookup"><span data-stu-id="d9c28-151">Reprocessing Schemas</span></span>  
 <span data-ttu-id="d9c28-152">Bir <xref:System.Xml.Schema.XmlSchemaSet> şemanın ' de yeniden işlenmesi, <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> yöntemi <xref:System.Xml.Schema.XmlSchemaSet> çağrıldığında bir şemada gerçekleştirilen tüm ön işleme adımlarını gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="d9c28-152">Reprocessing a schema in an <xref:System.Xml.Schema.XmlSchemaSet> performs all the preprocessing steps performed on a schema when the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet> is called.</span></span> <span data-ttu-id="d9c28-153"><xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> Yöntemine yapılan çağrı başarılı olursa öğesinin <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> <xref:System.Xml.Schema.XmlSchemaSet> özelliği olarak `false`ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="d9c28-153">If the call to the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method is successful, the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet> is set to `false`.</span></span>  
  
 <span data-ttu-id="d9c28-154"><xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> Yöntemi, derleme gerçekleştirildikten sonra <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.Schema.XmlSchemaSet> içindeki bir şema değiştirildiğinde kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d9c28-154">The <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method should be used when a schema in the <xref:System.Xml.Schema.XmlSchemaSet> has been modified after the <xref:System.Xml.Schema.XmlSchemaSet> has performed compilation.</span></span>  
  
 <span data-ttu-id="d9c28-155">Aşağıdaki örnek, <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> yöntemi kullanılarak öğesine eklenen bir şemanın yeniden işlenmesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d9c28-155">The following example illustrates reprocessing a schema added to the <xref:System.Xml.Schema.XmlSchemaSet> using the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method.</span></span> <span data-ttu-id="d9c28-156"><xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> <xref:System.Xml.Schema.XmlSchemaSet> Yöntemi kullanılarak derlendikten ve öğesine eklenen şema değiştirilirse, içindeki bir şema değiştirilse bile özelliği olarak `true` <xref:System.Xml.Schema.XmlSchemaSet> ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="d9c28-156">After the <xref:System.Xml.Schema.XmlSchemaSet> is compiled using the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method, and the schema added to the <xref:System.Xml.Schema.XmlSchemaSet> is modified, the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property is set to `true` even though a schema in the <xref:System.Xml.Schema.XmlSchemaSet> has been modified.</span></span> <span data-ttu-id="d9c28-157"><xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> Yöntemi <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> çağırmak yöntemi tarafından gerçekleştirilen tüm ön işleme gerçekleştirir ve <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> özelliğini olarak `false`ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d9c28-157">Calling the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method performs all the preprocessing performed by the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method, and sets the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property to `false`.</span></span>  
  
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
  
 <span data-ttu-id="d9c28-158">Bir şemayı bir <xref:System.Xml.Schema.XmlSchemaSet>içinde yeniden işleme hakkında daha fazla bilgi için bkz. <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> Yöntem başvurusu belgeleri.</span><span class="sxs-lookup"><span data-stu-id="d9c28-158">For more information about reprocessing a schema in an <xref:System.Xml.Schema.XmlSchemaSet>, see the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method reference documentation.</span></span>  
  
## <a name="checking-for-a-schema"></a><span data-ttu-id="d9c28-159">Şema denetleniyor</span><span class="sxs-lookup"><span data-stu-id="d9c28-159">Checking for a Schema</span></span>  
 <span data-ttu-id="d9c28-160">Bir şemanın içinde içerildiğini denetlemek <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> <xref:System.Xml.Schema.XmlSchemaSet> için ' ın metodunu kullanabilirsiniz. <xref:System.Xml.Schema.XmlSchemaSet></span><span class="sxs-lookup"><span data-stu-id="d9c28-160">You can use the <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet> to check if a schema is contained within an <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="d9c28-161">Yöntemi <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> , denetlenecek bir hedef ad alanı ya da <xref:System.Xml.Schema.XmlSchema> nesne alır.</span><span class="sxs-lookup"><span data-stu-id="d9c28-161">The <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> method takes either a target namespace or an <xref:System.Xml.Schema.XmlSchema> object to check for.</span></span> <span data-ttu-id="d9c28-162">Her iki durumda da, <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> şema içinde `true` içerilse, yöntemi döndürür <xref:System.Xml.Schema.XmlSchemaSet>. Aksi takdirde, döndürür `false`.</span><span class="sxs-lookup"><span data-stu-id="d9c28-162">In either case, the <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> method returns `true` if the schema is contained within the <xref:System.Xml.Schema.XmlSchemaSet>; otherwise, it returns `false`.</span></span>  
  
 <span data-ttu-id="d9c28-163">Bir şemayı denetleme hakkında daha fazla bilgi için bkz. <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> Yöntem başvurusu belgeleri.</span><span class="sxs-lookup"><span data-stu-id="d9c28-163">For more information about checking for a schema, see the <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> method reference documentation.</span></span>  
  
## <a name="removing-schemas"></a><span data-ttu-id="d9c28-164">Şemaları kaldırma</span><span class="sxs-lookup"><span data-stu-id="d9c28-164">Removing Schemas</span></span>  
 <span data-ttu-id="d9c28-165"><xref:System.Xml.Schema.XmlSchemaSet> Şemaları, <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> <xref:System.Xml.Schema.XmlSchemaSet>ve <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> yöntemleri kullanılarak bir öğesinden kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="d9c28-165">Schemas are removed from an <xref:System.Xml.Schema.XmlSchemaSet> using the <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> and <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> methods of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="d9c28-166"><xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> Yöntemi belirtilen şemayı öğesinden kaldırır <xref:System.Xml.Schema.XmlSchemaSet>, ancak <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> yöntem belirtilen şemayı ve içeri aktardığı tüm şemaları kaldırır <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="d9c28-166">The <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> method removes the specified schema from the <xref:System.Xml.Schema.XmlSchemaSet>, while the <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> method removes the specified schema and all the schemas it imports from the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
 <span data-ttu-id="d9c28-167">Aşağıdaki örnek, bir <xref:System.Xml.Schema.XmlSchemaSet>öğesine birden çok şema eklemeyi ve sonra şemadan birini <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> ve içeri aktardığı tüm şemaları kaldırmak için yöntemini kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="d9c28-167">The following example illustrates adding multiple schemas to an <xref:System.Xml.Schema.XmlSchemaSet>, then using the <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> method to remove one of the schemas and all the schemas it imports.</span></span>  
  
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
  
 <span data-ttu-id="d9c28-168">İçindeki şemaları kaldırma hakkında daha fazla bilgi için <xref:System.Xml.Schema.XmlSchemaSet>, <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> ve <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> yöntemleri başvuru belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="d9c28-168">For more information about removing schemas from an <xref:System.Xml.Schema.XmlSchemaSet>, see the <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> and <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> methods reference documentation.</span></span>  
  
## <a name="schema-resolution-and-xsimport"></a><span data-ttu-id="d9c28-169">Şema çözünürlüğü ve xs: import</span><span class="sxs-lookup"><span data-stu-id="d9c28-169">Schema Resolution and xs:import</span></span>  
 <span data-ttu-id="d9c28-170">Aşağıdaki örneklerde, içinde verilen <xref:System.Xml.Schema.XmlSchemaSet> bir ad alanı için birden çok şema olduğunda şemaları içeri aktarma davranışı açıklanır <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="d9c28-170">The following examples describe the <xref:System.Xml.Schema.XmlSchemaSet> behavior for importing schemas when multiple schemas for a given namespace exist in an <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
 <span data-ttu-id="d9c28-171">Örneğin, `http://www.contoso.com` ad alanı için <xref:System.Xml.Schema.XmlSchemaSet> birden çok şema içeren bir düşünün.</span><span class="sxs-lookup"><span data-stu-id="d9c28-171">For example, consider an <xref:System.Xml.Schema.XmlSchemaSet> that contains multiple schemas for the `http://www.contoso.com` namespace.</span></span> <span data-ttu-id="d9c28-172">Aşağıdaki `xs:import` yönergeyle bir şema öğesine eklenmiştir <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="d9c28-172">A schema with the following `xs:import` directive is added to the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
```xml  
<xs:import namespace="http://www.contoso.com" schemaLocation="http://www.contoso.com/schema.xsd" />  
```  
  
 <span data-ttu-id="d9c28-173">URL 'den yükleyerek <xref:System.Xml.Schema.XmlSchemaSet> `http://www.contoso.com` ad alanı için bir şemayı içeri aktarmaya çalışır. `http://www.contoso.com/schema.xsd`</span><span class="sxs-lookup"><span data-stu-id="d9c28-173">The <xref:System.Xml.Schema.XmlSchemaSet> attempts to import a schema for the `http://www.contoso.com` namespace by loading it from the `http://www.contoso.com/schema.xsd` URL.</span></span> <span data-ttu-id="d9c28-174">İçindeki `http://www.contoso.com` ad alanı için başka bir şema belgesi olsa da, yalnızca şema belgesinde belirtilen şema bildirimi ve türleri içeri aktarma şemasında kullanılabilir <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="d9c28-174">Only the schema declaration and types declared in the schema document are available in the importing schema, even though there are other schema documents for the `http://www.contoso.com` namespace in the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="d9c28-175">`schema.xsd` Dosya `http://www.contoso.com/schema.xsd` URL 'de bulunamıyorsa, `http://www.contoso.com` ad alanı için bir şema içeri aktarma şemasına içeri aktarılmaz.</span><span class="sxs-lookup"><span data-stu-id="d9c28-175">If the `schema.xsd` file cannot be located at the `http://www.contoso.com/schema.xsd` URL, no schema for the `http://www.contoso.com` namespace is imported into the importing schema.</span></span>  
  
## <a name="validating-xml-documents"></a><span data-ttu-id="d9c28-176">XML belgelerini doğrulama</span><span class="sxs-lookup"><span data-stu-id="d9c28-176">Validating XML Documents</span></span>  
 <span data-ttu-id="d9c28-177">XML belgeleri, içindeki şemalara karşı doğrulanabilir <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="d9c28-177">XML documents can be validated against schemas in an <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="d9c28-178"><xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.XmlReaderSettings.Schemas%2A> Bir <xref:System.Xml.XmlReaderSettings> nesnenin özelliğine bir şema ekleyerek veya bir <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.XmlReaderSettings.Schemas%2A> <xref:System.Xml.XmlReaderSettings> nesnenin özelliğine bir nesne ekleyerek bir XML belgesini doğrularsınız.</span><span class="sxs-lookup"><span data-stu-id="d9c28-178">You validate an XML document by adding a schema to the <xref:System.Xml.Schema.XmlSchemaSet><xref:System.Xml.XmlReaderSettings.Schemas%2A> property of an <xref:System.Xml.XmlReaderSettings> object, or by adding an <xref:System.Xml.Schema.XmlSchemaSet> to the <xref:System.Xml.XmlReaderSettings.Schemas%2A> property of an <xref:System.Xml.XmlReaderSettings> object.</span></span> <span data-ttu-id="d9c28-179">Daha <xref:System.Xml.XmlReaderSettings> sonra nesnesi, <xref:System.Xml.XmlReader.Create%2A> <xref:System.Xml.XmlReader> sınıfının YÖNTEMI tarafından bir <xref:System.Xml.XmlReader> nesne oluşturmak ve XML belgesini doğrulamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d9c28-179">The <xref:System.Xml.XmlReaderSettings> object is then used by the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> class to create an <xref:System.Xml.XmlReader> object and validate the XML document.</span></span>  
  
 <span data-ttu-id="d9c28-180">XML belgelerinin bir <xref:System.Xml.Schema.XmlSchemaSet>kullanarak doğrulanması hakkında daha fazla bilgi için bkz. [XmlSchemaSet ile XML şeması (xsd) doğrulaması](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemaset.md).</span><span class="sxs-lookup"><span data-stu-id="d9c28-180">For more information about validating XML documents using an <xref:System.Xml.Schema.XmlSchemaSet>, see [XML Schema (XSD) Validation with XmlSchemaSet](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemaset.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9c28-181">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d9c28-181">See also</span></span>

- <xref:System.Xml.Schema.XmlSchemaSet.Add%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A>
- [<span data-ttu-id="d9c28-182">Şema önbelleği olarak XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="d9c28-182">XmlSchemaSet as a Schema Cache</span></span>](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
- [<span data-ttu-id="d9c28-183">XmlSchemaSet ile XML Şeması (XSD) Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="d9c28-183">XML Schema (XSD) Validation with XmlSchemaSet</span></span>](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemaset.md)
