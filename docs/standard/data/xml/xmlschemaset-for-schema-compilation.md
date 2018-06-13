---
title: Şema derleme için XmlSchemaSet
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 55c4b175-3170-4071-9d60-dd5a42f79b54
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 91835006925f9768c25ad1a984a3b189e3e4c58c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33579086"
---
# <a name="xmlschemaset-for-schema-compilation"></a><span data-ttu-id="f5583-102">Şema derleme için XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="f5583-102">XmlSchemaSet for Schema Compilation</span></span>
<span data-ttu-id="f5583-103">Açıklar <xref:System.Xml.Schema.XmlSchemaSet>, bir önbellek burada XML Şeması Tanım Dili (XSD) şemaları depolanabilir ve doğrulandı.</span><span class="sxs-lookup"><span data-stu-id="f5583-103">Describes the <xref:System.Xml.Schema.XmlSchemaSet>, a cache where XML Schema definition language (XSD) schemas can be stored and validated.</span></span>  
  
## <a name="the-xmlschemaset-class"></a><span data-ttu-id="f5583-104">XmlSchemaSet sınıfı</span><span class="sxs-lookup"><span data-stu-id="f5583-104">The XmlSchemaSet Class</span></span>  
 <span data-ttu-id="f5583-105"><xref:System.Xml.Schema.XmlSchemaSet> Burada XML Şeması Tanım Dili (XSD) şemaları depolanabilir ve doğrulanmış bir önbelleğidir.</span><span class="sxs-lookup"><span data-stu-id="f5583-105">The <xref:System.Xml.Schema.XmlSchemaSet> is a cache where XML Schema definition language (XSD) schemas can be stored and validated.</span></span>  
  
 <span data-ttu-id="f5583-106">İçinde <xref:System.Xml?displayProperty=nameWithType> XML şemaları sürüm 1.0, yüklenen içine bir <xref:System.Xml.Schema.XmlSchemaCollection> şemaların kitaplık olarak sınıfı.</span><span class="sxs-lookup"><span data-stu-id="f5583-106">In <xref:System.Xml?displayProperty=nameWithType> version 1.0, XML schemas were loaded into an <xref:System.Xml.Schema.XmlSchemaCollection> class as a library of schemas.</span></span> <span data-ttu-id="f5583-107">İçinde <xref:System.Xml?displayProperty=nameWithType> sürüm 2.0, <xref:System.Xml.XmlValidatingReader> ve <xref:System.Xml.Schema.XmlSchemaCollection> sınıfları eskidir ve almıştır <xref:System.Xml.XmlReader.Create%2A> yöntemleri ve <xref:System.Xml.Schema.XmlSchemaSet> sırasıyla sınıfı.</span><span class="sxs-lookup"><span data-stu-id="f5583-107">In <xref:System.Xml?displayProperty=nameWithType> version 2.0, the <xref:System.Xml.XmlValidatingReader> and the <xref:System.Xml.Schema.XmlSchemaCollection> classes are obsolete, and have been replaced by the <xref:System.Xml.XmlReader.Create%2A> methods, and the <xref:System.Xml.Schema.XmlSchemaSet> class respectively.</span></span>  
  
 <span data-ttu-id="f5583-108"><xref:System.Xml.Schema.XmlSchemaSet> Birkaç standartları uyumluluğu, performans ve Microsoft XML verileri azaltılmış (XDR) şema biçimi geçersiz dahil olmak üzere sorunları düzeltmek için sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="f5583-108">The <xref:System.Xml.Schema.XmlSchemaSet> has been introduced to fix a number of issues including standards compatibility, performance, and the obsolete Microsoft XML-Data Reduced (XDR) schema format.</span></span>  
  
 <span data-ttu-id="f5583-109">Arasında bir karşılaştırma aşağıdadır <xref:System.Xml.Schema.XmlSchemaCollection> sınıfı ve <xref:System.Xml.Schema.XmlSchemaSet> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="f5583-109">The following is a comparison between the <xref:System.Xml.Schema.XmlSchemaCollection> class and the <xref:System.Xml.Schema.XmlSchemaSet> class.</span></span>  
  
|<span data-ttu-id="f5583-110">XmlSchemaCollection</span><span class="sxs-lookup"><span data-stu-id="f5583-110">XmlSchemaCollection</span></span>|<span data-ttu-id="f5583-111">XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="f5583-111">XmlSchemaSet</span></span>|  
|-------------------------|------------------|  
|<span data-ttu-id="f5583-112">Microsoft XDR ve W3C XML şemalarını destekler.</span><span class="sxs-lookup"><span data-stu-id="f5583-112">Supports Microsoft XDR and W3C XML schemas.</span></span>|<span data-ttu-id="f5583-113">Yalnızca W3C XML şemaları destekler.</span><span class="sxs-lookup"><span data-stu-id="f5583-113">Only supports W3C XML schemas.</span></span>|  
|<span data-ttu-id="f5583-114">Şemalar derlenen zaman <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="f5583-114">Schemas are compiled when the <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> method is called.</span></span>|<span data-ttu-id="f5583-115">Şemalar olmayan zaman derlenmiş <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="f5583-115">Schemas are not compiled when the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method is called.</span></span> <span data-ttu-id="f5583-116">Bu şema kitaplığı oluşturulması sırasında performans geliştirmesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="f5583-116">This provides a performance improvement during creation of the schema library.</span></span>|  
|<span data-ttu-id="f5583-117">"İçinde şema Adaları." sonuçlanabilir tek tek bir derlenmiş sürüm her şema oluşturur</span><span class="sxs-lookup"><span data-stu-id="f5583-117">Each schema generates an individual compiled version that can result in "schema islands."</span></span> <span data-ttu-id="f5583-118">Sonuç olarak, tüm içerir ve içeri aktarmalar içinde yalnızca o şeması kapsamına eklenir.</span><span class="sxs-lookup"><span data-stu-id="f5583-118">As a result, all includes and imports are scoped only within that schema.</span></span>|<span data-ttu-id="f5583-119">Derlenmiş şema bir "şemaları ayarlama" tek bir mantıksal şema oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f5583-119">Compiled schemas generate a single logical schema, a "set" of schemas.</span></span> <span data-ttu-id="f5583-120">Kümeye eklenen tüm içeri aktarılan bir şema şemalarında kümesine kendilerini doğrudan eklenir.</span><span class="sxs-lookup"><span data-stu-id="f5583-120">Any imported schemas within a schema that are added to the set are directly added to the set themselves.</span></span> <span data-ttu-id="f5583-121">Başka bir deyişle, tüm şemaları tüm türleri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f5583-121">This means that all types are available to all schemas.</span></span>|  
|<span data-ttu-id="f5583-122">Belirli hedef ad alanı için yalnızca bir şema koleksiyonunda var olabilir.</span><span class="sxs-lookup"><span data-stu-id="f5583-122">Only one schema for a particular target namespace can exist in the collection.</span></span>|<span data-ttu-id="f5583-123">Aynı hedef ad alanı için birden çok şema türü çakışmalar var olduğu sürece eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="f5583-123">Multiple schemas for the same target namespace can be added as long as there are no type conflicts.</span></span>|  
  
## <a name="migrating-to-the-xmlschemaset"></a><span data-ttu-id="f5583-124">XmlSchemaSet geçirme</span><span class="sxs-lookup"><span data-stu-id="f5583-124">Migrating to the XmlSchemaSet</span></span>  
 <span data-ttu-id="f5583-125">Aşağıdaki kod örneğinde yeni geçiş için bir kılavuz sağlar <xref:System.Xml.Schema.XmlSchemaSet> eski sınıfından <xref:System.Xml.Schema.XmlSchemaCollection> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="f5583-125">The following code example provides a guide to migrating to the new <xref:System.Xml.Schema.XmlSchemaSet> class from the obsolete <xref:System.Xml.Schema.XmlSchemaCollection> class.</span></span> <span data-ttu-id="f5583-126">Kod örneği iki sınıf arasında aşağıdaki temel farklılıkları gösterir.</span><span class="sxs-lookup"><span data-stu-id="f5583-126">The code example illustrates the following major differences between the two classes.</span></span>  
  
-   <span data-ttu-id="f5583-127">Farklı <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> yöntemi <xref:System.Xml.Schema.XmlSchemaCollection> sınıfı, şemalar değil çağrılırken derlenmiş <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> yöntemi <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="f5583-127">Unlike the <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> method of the <xref:System.Xml.Schema.XmlSchemaCollection> class, schemas are not compiled when calling the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="f5583-128"><xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> Yöntemi <xref:System.Xml.Schema.XmlSchemaSet> örnek kodda açık olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="f5583-128">The <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet> is explicitly called in the example code.</span></span>  
  
-   <span data-ttu-id="f5583-129">Üzerinden yineleme yapmak için bir <xref:System.Xml.Schema.XmlSchemaSet>, kullanmalısınız <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> özelliği <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="f5583-129">To iterate over an <xref:System.Xml.Schema.XmlSchemaSet>, you must use the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
 <span data-ttu-id="f5583-130">Aşağıdaki kullanılmıyor <xref:System.Xml.Schema.XmlSchemaCollection> kod örneği.</span><span class="sxs-lookup"><span data-stu-id="f5583-130">The following is the obsolete <xref:System.Xml.Schema.XmlSchemaCollection> code example.</span></span>  
  
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
  
 <span data-ttu-id="f5583-131">Aşağıdaki eşdeğerdir <xref:System.Xml.Schema.XmlSchemaSet> kod örneği.</span><span class="sxs-lookup"><span data-stu-id="f5583-131">The following is the equivalent <xref:System.Xml.Schema.XmlSchemaSet> code example.</span></span>  
  
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
  
## <a name="adding-and-retrieving-schemas"></a><span data-ttu-id="f5583-132">Ekleme ve şemaları alma</span><span class="sxs-lookup"><span data-stu-id="f5583-132">Adding and Retrieving Schemas</span></span>  
 <span data-ttu-id="f5583-133">Şemalar eklenir bir <xref:System.Xml.Schema.XmlSchemaSet> kullanarak <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> yöntemi <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="f5583-133">Schemas are added to an <xref:System.Xml.Schema.XmlSchemaSet> using the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="f5583-134">İçin bir şema eklendiğinde bir <xref:System.Xml.Schema.XmlSchemaSet>, hedef ad alanı URI ile ilişkilidir.</span><span class="sxs-lookup"><span data-stu-id="f5583-134">When a schema is added to an <xref:System.Xml.Schema.XmlSchemaSet>, it is associated with a target namespace URI.</span></span> <span data-ttu-id="f5583-135">URI ya da belirtilebilir parametre olarak hedef ad alanı <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> yöntemi veya hiçbir hedef ad alanı belirtilmiş olup olmadığını <xref:System.Xml.Schema.XmlSchemaSet> şemada tanımlanan hedef ad alanı kullanır.</span><span class="sxs-lookup"><span data-stu-id="f5583-135">The target namespace URI can either be specified as a parameter to the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method or if no target namespace is specified, the <xref:System.Xml.Schema.XmlSchemaSet> uses the target namespace defined in the schema.</span></span>  
  
 <span data-ttu-id="f5583-136">Öğesinden alınan şemaları bir <xref:System.Xml.Schema.XmlSchemaSet> kullanarak <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> özelliği <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="f5583-136">Schemas are retrieved from an <xref:System.Xml.Schema.XmlSchemaSet> using the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="f5583-137"><xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> Özelliği <xref:System.Xml.Schema.XmlSchemaSet> üzerinden yineleme sayesinde <xref:System.Xml.Schema.XmlSchema> içinde yer alan nesneler <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="f5583-137">The <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet> allows you to iterate over the <xref:System.Xml.Schema.XmlSchema> objects contained in the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="f5583-138"><xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> Özelliği ya da döndürür tüm <xref:System.Xml.Schema.XmlSchema> içinde yer alan nesneler <xref:System.Xml.Schema.XmlSchemaSet>, veya hedef ad alanı parametre, tüm döndürür <xref:System.Xml.Schema.XmlSchema> hedef ad alanına ait nesneleri.</span><span class="sxs-lookup"><span data-stu-id="f5583-138">The <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property either returns all the <xref:System.Xml.Schema.XmlSchema> objects contained in the <xref:System.Xml.Schema.XmlSchemaSet>, or, given a target namespace parameter, returns all the <xref:System.Xml.Schema.XmlSchema> objects that belong to the target namespace.</span></span> <span data-ttu-id="f5583-139">Varsa `null` hedef ad alanı parametre olarak belirtilen <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> özelliği, bir ad alanı olmayan tüm şemalarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="f5583-139">If `null` is specified as the target namespace parameter, the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property returns all schemas without a namespace.</span></span>  
  
 <span data-ttu-id="f5583-140">Aşağıdaki örnek, `books.xsd` şemada `http://www.contoso.com/books` ad alanına bir <xref:System.Xml.Schema.XmlSchemaSet>, ait tüm şemaları alır `http://www.contoso.com/books` ad alanından <xref:System.Xml.Schema.XmlSchemaSet>ve ardından bu şemaya Yazar <xref:System.Console>.</span><span class="sxs-lookup"><span data-stu-id="f5583-140">The following example adds the `books.xsd` schema in the `http://www.contoso.com/books` namespace to an <xref:System.Xml.Schema.XmlSchemaSet>, retrieves all schemas that belong to the `http://www.contoso.com/books` namespace from the <xref:System.Xml.Schema.XmlSchemaSet>, and then writes those schemas to the <xref:System.Console>.</span></span>  
  
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
  
 <span data-ttu-id="f5583-141">Ekleme ve gelen şemaları alma hakkında daha fazla bilgi için bir <xref:System.Xml.Schema.XmlSchemaSet> nesne için bkz: <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> yöntemi ve <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> özelliği başvuru belgeleri.</span><span class="sxs-lookup"><span data-stu-id="f5583-141">For more information about adding and retrieving schemas from an <xref:System.Xml.Schema.XmlSchemaSet> object, see the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method and the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property reference documentation.</span></span>  
  
## <a name="compiling-schemas"></a><span data-ttu-id="f5583-142">Şema derleme</span><span class="sxs-lookup"><span data-stu-id="f5583-142">Compiling Schemas</span></span>  
 <span data-ttu-id="f5583-143">Şemalarda bir <xref:System.Xml.Schema.XmlSchemaSet> tarafından bir mantıksal şema içine derlenmiş <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> yöntemi <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="f5583-143">Schemas in an <xref:System.Xml.Schema.XmlSchemaSet> are compiled into one logical schema by the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f5583-144">Artık kullanılmayan aksine <xref:System.Xml.Schema.XmlSchemaCollection> sınıfı, şemalar olmayan zaman derlenmiş <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="f5583-144">Unlike the obsolete <xref:System.Xml.Schema.XmlSchemaCollection> class, schemas are not compiled when the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method is called.</span></span>  
  
 <span data-ttu-id="f5583-145">Varsa <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> yöntemini yürütür başarıyla <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> özelliği <xref:System.Xml.Schema.XmlSchemaSet> ayarlanır `true`.</span><span class="sxs-lookup"><span data-stu-id="f5583-145">If the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method executes successfully, the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet> is set to `true`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f5583-146"><xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> Özelliği şemaları düzenlediyseniz etkilenmez while içinde <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="f5583-146">The <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property is not affected if schemas are edited while in the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="f5583-147">Güncelleştirmeleri tek tek şemalardan <xref:System.Xml.Schema.XmlSchemaSet> değil izlenir.</span><span class="sxs-lookup"><span data-stu-id="f5583-147">Updates of the individual schemas in the <xref:System.Xml.Schema.XmlSchemaSet> are not tracked.</span></span> <span data-ttu-id="f5583-148">Sonuç olarak, <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> özelliği `true` şemalardan birine yer alan olsa bile <xref:System.Xml.Schema.XmlSchemaSet> şema eklendi veya korumadan kaldırıldı sürece, değiştirilmiş <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="f5583-148">As a result, the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property can be `true` even though one of the schemas contained in the <xref:System.Xml.Schema.XmlSchemaSet> has been altered, as long as no schemas were added or removed from the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
 <span data-ttu-id="f5583-149">Aşağıdaki örnek, `books.xsd` dosya <xref:System.Xml.Schema.XmlSchemaSet> ve çağırır <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f5583-149">The following example adds the `books.xsd` file to the <xref:System.Xml.Schema.XmlSchemaSet> and then calls the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method.</span></span>  
  
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
  
 <span data-ttu-id="f5583-150">Şemalarda derleme hakkında daha fazla bilgi için bir <xref:System.Xml.Schema.XmlSchemaSet>, bkz: <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> yöntemi başvuru belgeleri.</span><span class="sxs-lookup"><span data-stu-id="f5583-150">For more information about compiling schemas in an <xref:System.Xml.Schema.XmlSchemaSet>, see the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method reference documentation.</span></span>  
  
## <a name="reprocessing-schemas"></a><span data-ttu-id="f5583-151">Yeniden işlemenin şemaları</span><span class="sxs-lookup"><span data-stu-id="f5583-151">Reprocessing Schemas</span></span>  
 <span data-ttu-id="f5583-152">Şemada yeniden işlemenin bir <xref:System.Xml.Schema.XmlSchemaSet> şemayı gerçekleştirilen tüm önişlem adımları gerçekleştirir, <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> yöntemi <xref:System.Xml.Schema.XmlSchemaSet> olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="f5583-152">Reprocessing a schema in an <xref:System.Xml.Schema.XmlSchemaSet> performs all the preprocessing steps performed on a schema when the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet> is called.</span></span> <span data-ttu-id="f5583-153">Varsa çağrısı <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> yöntemdir başarılı <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> özelliği <xref:System.Xml.Schema.XmlSchemaSet> ayarlanır `false`.</span><span class="sxs-lookup"><span data-stu-id="f5583-153">If the call to the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method is successful, the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet> is set to `false`.</span></span>  
  
 <span data-ttu-id="f5583-154"><xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> Yöntemi şemada zaman kullanılmalıdır <xref:System.Xml.Schema.XmlSchemaSet> sonra değiştirilen <xref:System.Xml.Schema.XmlSchemaSet> derleme gerçekleştirdi.</span><span class="sxs-lookup"><span data-stu-id="f5583-154">The <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method should be used when a schema in the <xref:System.Xml.Schema.XmlSchemaSet> has been modified after the <xref:System.Xml.Schema.XmlSchemaSet> has performed compilation.</span></span>  
  
 <span data-ttu-id="f5583-155">Aşağıdaki örnekte, eklenen bir şema yeniden işlemeyerek gösterilmektedir <xref:System.Xml.Schema.XmlSchemaSet> kullanarak <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f5583-155">The following example illustrates reprocessing a schema added to the <xref:System.Xml.Schema.XmlSchemaSet> using the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method.</span></span> <span data-ttu-id="f5583-156">Sonra <xref:System.Xml.Schema.XmlSchemaSet> derlenip <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> yöntemi ve eklenen şema <xref:System.Xml.Schema.XmlSchemaSet> değiştirildiğinde <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> özelliği ayarlanmış `true` dahi şemada <xref:System.Xml.Schema.XmlSchemaSet> değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="f5583-156">After the <xref:System.Xml.Schema.XmlSchemaSet> is compiled using the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method, and the schema added to the <xref:System.Xml.Schema.XmlSchemaSet> is modified, the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property is set to `true` even though a schema in the <xref:System.Xml.Schema.XmlSchemaSet> has been modified.</span></span> <span data-ttu-id="f5583-157">Çağırma <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> yöntemi gerçekleştirir tüm tarafından gerçekleştirilen ön işleme <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> yöntemi ve kümelerini <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> özelliğine `false`.</span><span class="sxs-lookup"><span data-stu-id="f5583-157">Calling the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method performs all the preprocessing performed by the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method, and sets the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property to `false`.</span></span>  
  
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
  
 <span data-ttu-id="f5583-158">Şemada yeniden işleme hakkında daha fazla bilgi için bir <xref:System.Xml.Schema.XmlSchemaSet>, bkz: <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> yöntemi başvuru belgeleri.</span><span class="sxs-lookup"><span data-stu-id="f5583-158">For more information about reprocessing a schema in an <xref:System.Xml.Schema.XmlSchemaSet>, see the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method reference documentation.</span></span>  
  
## <a name="checking-for-a-schema"></a><span data-ttu-id="f5583-159">İçin bir şema denetleniyor</span><span class="sxs-lookup"><span data-stu-id="f5583-159">Checking for a Schema</span></span>  
 <span data-ttu-id="f5583-160">Kullanabileceğiniz <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> yöntemi <xref:System.Xml.Schema.XmlSchemaSet> bir şema içinde dahil olup olmadığını denetlemek için bir <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="f5583-160">You can use the <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet> to check if a schema is contained within an <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="f5583-161"><xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> Yöntemi alır ya da, bir hedef ad alanı veya bir <xref:System.Xml.Schema.XmlSchema> denetlemek için nesne.</span><span class="sxs-lookup"><span data-stu-id="f5583-161">The <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> method takes either a target namespace or an <xref:System.Xml.Schema.XmlSchema> object to check for.</span></span> <span data-ttu-id="f5583-162">Her iki durumda da <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> yöntemi döndürür `true` şema içinde yer alıyorsa <xref:System.Xml.Schema.XmlSchemaSet>; Aksi takdirde döndürdüğü `false`.</span><span class="sxs-lookup"><span data-stu-id="f5583-162">In either case, the <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> method returns `true` if the schema is contained within the <xref:System.Xml.Schema.XmlSchemaSet>; otherwise, it returns `false`.</span></span>  
  
 <span data-ttu-id="f5583-163">İçin bir şema denetimi hakkında daha fazla bilgi için bkz: <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> yöntemi başvuru belgeleri.</span><span class="sxs-lookup"><span data-stu-id="f5583-163">For more information about checking for a schema, see the <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> method reference documentation.</span></span>  
  
## <a name="removing-schemas"></a><span data-ttu-id="f5583-164">Şemalar kaldırma</span><span class="sxs-lookup"><span data-stu-id="f5583-164">Removing Schemas</span></span>  
 <span data-ttu-id="f5583-165">Şemalar kaldırılma bir <xref:System.Xml.Schema.XmlSchemaSet> kullanarak <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> ve <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> yöntemlerini <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="f5583-165">Schemas are removed from an <xref:System.Xml.Schema.XmlSchemaSet> using the <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> and <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> methods of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="f5583-166"><xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> Yöntemi, belirtilen şemasından kaldırır <xref:System.Xml.Schema.XmlSchemaSet>, sırada <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> yöntemi, belirtilen şema ve bunu aktarır tüm şemaları kaldırır <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="f5583-166">The <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> method removes the specified schema from the <xref:System.Xml.Schema.XmlSchemaSet>, while the <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> method removes the specified schema and all the schemas it imports from the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
 <span data-ttu-id="f5583-167">Aşağıdaki örnekte, birden çok şema ekleme gösterilmektedir bir <xref:System.Xml.Schema.XmlSchemaSet>, ardından kullanarak <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> şemalardan birine ve bunu aktarır tüm şemaları kaldırmak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="f5583-167">The following example illustrates adding multiple schemas to an <xref:System.Xml.Schema.XmlSchemaSet>, then using the <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> method to remove one of the schemas and all the schemas it imports.</span></span>  
  
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
  
 <span data-ttu-id="f5583-168">Gelen şemaları kaldırma hakkında daha fazla bilgi için bir <xref:System.Xml.Schema.XmlSchemaSet>, bkz: <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> ve <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> yöntemleri başvuru belgelerini.</span><span class="sxs-lookup"><span data-stu-id="f5583-168">For more information about removing schemas from an <xref:System.Xml.Schema.XmlSchemaSet>, see the <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> and <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> methods reference documentation.</span></span>  
  
## <a name="schema-resolution-and-xsimport"></a><span data-ttu-id="f5583-169">Şema çözümlemesi ve xs:import</span><span class="sxs-lookup"><span data-stu-id="f5583-169">Schema Resolution and xs:import</span></span>  
 <span data-ttu-id="f5583-170">Aşağıdaki örnekler açıklar <xref:System.Xml.Schema.XmlSchemaSet> şemalarını içeri aktarma için belirli bir ad için birden çok şema mevcut olduğunda davranışı bir <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="f5583-170">The following examples describe the <xref:System.Xml.Schema.XmlSchemaSet> behavior for importing schemas when multiple schemas for a given namespace exist in an <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
 <span data-ttu-id="f5583-171">Örneğin, göz önünde bulundurun bir <xref:System.Xml.Schema.XmlSchemaSet> için birden çok şema içeren `http://www.contoso.com` ad alanı.</span><span class="sxs-lookup"><span data-stu-id="f5583-171">For example, consider an <xref:System.Xml.Schema.XmlSchemaSet> that contains multiple schemas for the `http://www.contoso.com` namespace.</span></span> <span data-ttu-id="f5583-172">Aşağıdaki şema `xs:import` yönergesi eklenir <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="f5583-172">A schema with the following `xs:import` directive is added to the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
```xml  
<xs:import namespace="http://www.contoso.com" schemaLocation="http://www.contoso.com/schema.xsd" />  
```  
  
 <span data-ttu-id="f5583-173"><xref:System.Xml.Schema.XmlSchemaSet> İçin bir şema alma girişiminde `http://www.contoso.com` şuradan yükleniyor tarafından ad alanı `http://www.contoso.com/schema.xsd` URL.</span><span class="sxs-lookup"><span data-stu-id="f5583-173">The <xref:System.Xml.Schema.XmlSchemaSet> attempts to import a schema for the `http://www.contoso.com` namespace by loading it from the `http://www.contoso.com/schema.xsd` URL.</span></span> <span data-ttu-id="f5583-174">Diğer şema belgeler için olsa bile şema bildirimi ve şema belgesinde bildirilen türler alma şemada yalnızca kullanılabilir `http://www.contoso.com` ad alanında <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="f5583-174">Only the schema declaration and types declared in the schema document are available in the importing schema, even though there are other schema documents for the `http://www.contoso.com` namespace in the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="f5583-175">Varsa `schema.xsd` dosya adresindedir olamaz `http://www.contoso.com/schema.xsd` URL için şema yok `http://www.contoso.com` ad alanı içeri aktarma şemaya alınır.</span><span class="sxs-lookup"><span data-stu-id="f5583-175">If the `schema.xsd` file cannot be located at the `http://www.contoso.com/schema.xsd` URL, no schema for the `http://www.contoso.com` namespace is imported into the importing schema.</span></span>  
  
## <a name="validating-xml-documents"></a><span data-ttu-id="f5583-176">XML belgeleri doğrulanıyor</span><span class="sxs-lookup"><span data-stu-id="f5583-176">Validating XML Documents</span></span>  
 <span data-ttu-id="f5583-177">XML belgeleri doğrulanmış şemalarda karşı bir <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="f5583-177">XML documents can be validated against schemas in an <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="f5583-178">Bir şemaya ekleyerek bir XML belgesi doğrulamak <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.XmlReaderSettings.Schemas%2A> özelliği bir <xref:System.Xml.XmlReaderSettings> nesne veya ekleyerek bir <xref:System.Xml.Schema.XmlSchemaSet> için <xref:System.Xml.XmlReaderSettings.Schemas%2A> özelliği bir <xref:System.Xml.XmlReaderSettings> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="f5583-178">You validate an XML document by adding a schema to the <xref:System.Xml.Schema.XmlSchemaSet><xref:System.Xml.XmlReaderSettings.Schemas%2A> property of an <xref:System.Xml.XmlReaderSettings> object, or by adding an <xref:System.Xml.Schema.XmlSchemaSet> to the <xref:System.Xml.XmlReaderSettings.Schemas%2A> property of an <xref:System.Xml.XmlReaderSettings> object.</span></span> <span data-ttu-id="f5583-179"><xref:System.Xml.XmlReaderSettings> Nesnesi tarafından kullanılan sonra <xref:System.Xml.XmlReader.Create%2A> yöntemi <xref:System.Xml.XmlReader> sınıfı oluşturmak için bir <xref:System.Xml.XmlReader> nesne ve XML belgesi doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="f5583-179">The <xref:System.Xml.XmlReaderSettings> object is then used by the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> class to create an <xref:System.Xml.XmlReader> object and validate the XML document.</span></span>  
  
 <span data-ttu-id="f5583-180">XML doğrulama hakkında daha fazla bilgi için belgeleri kullanarak bir <xref:System.Xml.Schema.XmlSchemaSet>, bkz: [XmlSchemaSet ile XML Şeması (XSD) doğrulama](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemaset.md).</span><span class="sxs-lookup"><span data-stu-id="f5583-180">For more information about validating XML documents using an <xref:System.Xml.Schema.XmlSchemaSet>, see [XML Schema (XSD) Validation with XmlSchemaSet](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemaset.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5583-181">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f5583-181">See Also</span></span>  
 <xref:System.Xml.Schema.XmlSchemaSet.Add%2A>  
 <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A>  
 <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A>  
 <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A>  
 <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A>  
 <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A>  
 <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A>  
 [<span data-ttu-id="f5583-182">Bir şema önbelleği olarak XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="f5583-182">XmlSchemaSet as a Schema Cache</span></span>](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
 [<span data-ttu-id="f5583-183">XmlSchemaSet ile XML Şeması (XSD) Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="f5583-183">XML Schema (XSD) Validation with XmlSchemaSet</span></span>](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemaset.md)
