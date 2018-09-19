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
ms.openlocfilehash: c24fe637514ba773cecc7824de276b1707a4e90c
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46288078"
---
# <a name="xmlschemaset-for-schema-compilation"></a><span data-ttu-id="8a775-102">Şema derleme için XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="8a775-102">XmlSchemaSet for Schema Compilation</span></span>
<span data-ttu-id="8a775-103">Açıklar <xref:System.Xml.Schema.XmlSchemaSet>, burada XML Şeması Tanım Dili (XSD) şemaları depolanabilir ve doğrulanmış bir önbellek.</span><span class="sxs-lookup"><span data-stu-id="8a775-103">Describes the <xref:System.Xml.Schema.XmlSchemaSet>, a cache where XML Schema definition language (XSD) schemas can be stored and validated.</span></span>  
  
## <a name="the-xmlschemaset-class"></a><span data-ttu-id="8a775-104">XmlSchemaSet sınıfı</span><span class="sxs-lookup"><span data-stu-id="8a775-104">The XmlSchemaSet Class</span></span>  
 <span data-ttu-id="8a775-105"><xref:System.Xml.Schema.XmlSchemaSet> Burada XML Şeması Tanım Dili (XSD) şemaları depolanabilir ve doğrulanmış bir önbellektir.</span><span class="sxs-lookup"><span data-stu-id="8a775-105">The <xref:System.Xml.Schema.XmlSchemaSet> is a cache where XML Schema definition language (XSD) schemas can be stored and validated.</span></span>  
  
 <span data-ttu-id="8a775-106">İçinde <xref:System.Xml?displayProperty=nameWithType> sürüm 1.0, XML şemaları yüklü içine bir <xref:System.Xml.Schema.XmlSchemaCollection> şemaların sınıf kitaplığı olarak.</span><span class="sxs-lookup"><span data-stu-id="8a775-106">In <xref:System.Xml?displayProperty=nameWithType> version 1.0, XML schemas were loaded into an <xref:System.Xml.Schema.XmlSchemaCollection> class as a library of schemas.</span></span> <span data-ttu-id="8a775-107">İçinde <xref:System.Xml?displayProperty=nameWithType> sürüm 2.0 <xref:System.Xml.XmlValidatingReader> ve <xref:System.Xml.Schema.XmlSchemaCollection> sınıfları eskidir ve almıştır <xref:System.Xml.XmlReader.Create%2A> yöntemleri ve <xref:System.Xml.Schema.XmlSchemaSet> sırasıyla sınıfı.</span><span class="sxs-lookup"><span data-stu-id="8a775-107">In <xref:System.Xml?displayProperty=nameWithType> version 2.0, the <xref:System.Xml.XmlValidatingReader> and the <xref:System.Xml.Schema.XmlSchemaCollection> classes are obsolete, and have been replaced by the <xref:System.Xml.XmlReader.Create%2A> methods, and the <xref:System.Xml.Schema.XmlSchemaSet> class respectively.</span></span>  
  
 <span data-ttu-id="8a775-108"><xref:System.Xml.Schema.XmlSchemaSet> Birkaç standartlara uyumluluk, performans ve eski Microsoft XML verileri azaltılmış (XDR) şema biçimi gibi sorunları düzeltmek için sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="8a775-108">The <xref:System.Xml.Schema.XmlSchemaSet> has been introduced to fix a number of issues including standards compatibility, performance, and the obsolete Microsoft XML-Data Reduced (XDR) schema format.</span></span>  
  
 <span data-ttu-id="8a775-109">Bir karşılaştırması aşağıdadır <xref:System.Xml.Schema.XmlSchemaCollection> sınıfı ve <xref:System.Xml.Schema.XmlSchemaSet> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="8a775-109">The following is a comparison between the <xref:System.Xml.Schema.XmlSchemaCollection> class and the <xref:System.Xml.Schema.XmlSchemaSet> class.</span></span>  
  
|<span data-ttu-id="8a775-110">XmlSchemaCollection</span><span class="sxs-lookup"><span data-stu-id="8a775-110">XmlSchemaCollection</span></span>|<span data-ttu-id="8a775-111">XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="8a775-111">XmlSchemaSet</span></span>|  
|-------------------------|------------------|  
|<span data-ttu-id="8a775-112">Microsoft XDR ve W3C XML şemalarını destekler.</span><span class="sxs-lookup"><span data-stu-id="8a775-112">Supports Microsoft XDR and W3C XML schemas.</span></span>|<span data-ttu-id="8a775-113">Yalnızca W3C XML şemaları destekler.</span><span class="sxs-lookup"><span data-stu-id="8a775-113">Only supports W3C XML schemas.</span></span>|  
|<span data-ttu-id="8a775-114">Şema derlenen olduğunda <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="8a775-114">Schemas are compiled when the <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> method is called.</span></span>|<span data-ttu-id="8a775-115">Şemaları olmayan zaman derlenmiş <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="8a775-115">Schemas are not compiled when the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method is called.</span></span> <span data-ttu-id="8a775-116">Bu, bir performans geliştirmesi sırasında Şema Kitaplığı oluşturulmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="8a775-116">This provides a performance improvement during creation of the schema library.</span></span>|  
|<span data-ttu-id="8a775-117">"Şema Adaları." neden olabilir bir bireysel derlenmiş sürüm her şeması oluşturur</span><span class="sxs-lookup"><span data-stu-id="8a775-117">Each schema generates an individual compiled version that can result in "schema islands."</span></span> <span data-ttu-id="8a775-118">Sonuç olarak, tüm içerir ve içeri aktarmalar yalnızca o şema içindeki belirlenir.</span><span class="sxs-lookup"><span data-stu-id="8a775-118">As a result, all includes and imports are scoped only within that schema.</span></span>|<span data-ttu-id="8a775-119">Bir "şemaları Ayarla" tek bir mantıksal şema derlenen şemalar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8a775-119">Compiled schemas generate a single logical schema, a "set" of schemas.</span></span> <span data-ttu-id="8a775-120">Kümeye eklenen bir şema içinde alınan şemalar doğrudan kümesine kendilerini eklenir.</span><span class="sxs-lookup"><span data-stu-id="8a775-120">Any imported schemas within a schema that are added to the set are directly added to the set themselves.</span></span> <span data-ttu-id="8a775-121">Başka bir deyişle, tüm şemalara tüm türleri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8a775-121">This means that all types are available to all schemas.</span></span>|  
|<span data-ttu-id="8a775-122">Belirli bir hedef ad alanı için yalnızca bir şema koleksiyonunda mevcut olabilir.</span><span class="sxs-lookup"><span data-stu-id="8a775-122">Only one schema for a particular target namespace can exist in the collection.</span></span>|<span data-ttu-id="8a775-123">Birden çok şema aynı hedef ad alanı için hiçbir tür çakışmalar var olduğu sürece eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="8a775-123">Multiple schemas for the same target namespace can be added as long as there are no type conflicts.</span></span>|  
  
## <a name="migrating-to-the-xmlschemaset"></a><span data-ttu-id="8a775-124">Geçiş için XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="8a775-124">Migrating to the XmlSchemaSet</span></span>  
 <span data-ttu-id="8a775-125">Aşağıdaki kod örneği yeni geçiş için bir kılavuz sağlar <xref:System.Xml.Schema.XmlSchemaSet> eski sınıftan <xref:System.Xml.Schema.XmlSchemaCollection> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="8a775-125">The following code example provides a guide to migrating to the new <xref:System.Xml.Schema.XmlSchemaSet> class from the obsolete <xref:System.Xml.Schema.XmlSchemaCollection> class.</span></span> <span data-ttu-id="8a775-126">Kod örneği, iki sınıf arasındaki aşağıdaki temel farklar gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8a775-126">The code example illustrates the following major differences between the two classes.</span></span>  
  
-   <span data-ttu-id="8a775-127">Farklı <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> yöntemi <xref:System.Xml.Schema.XmlSchemaCollection> sınıfı çağrılırken, şemalar derlenmiş değil <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> yöntemi <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="8a775-127">Unlike the <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> method of the <xref:System.Xml.Schema.XmlSchemaCollection> class, schemas are not compiled when calling the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="8a775-128"><xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> Yöntemi <xref:System.Xml.Schema.XmlSchemaSet> örnek kodda açıkça çağrılır.</span><span class="sxs-lookup"><span data-stu-id="8a775-128">The <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet> is explicitly called in the example code.</span></span>  
  
-   <span data-ttu-id="8a775-129">Üzerinden yinelemek için bir <xref:System.Xml.Schema.XmlSchemaSet>, kullanmanız gereken <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> özelliği <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="8a775-129">To iterate over an <xref:System.Xml.Schema.XmlSchemaSet>, you must use the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
 <span data-ttu-id="8a775-130">Aşağıdaki kullanılmıyor <xref:System.Xml.Schema.XmlSchemaCollection> kod örneği.</span><span class="sxs-lookup"><span data-stu-id="8a775-130">The following is the obsolete <xref:System.Xml.Schema.XmlSchemaCollection> code example.</span></span>  
  
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
  
 <span data-ttu-id="8a775-131">Aşağıdaki eşdeğerdir <xref:System.Xml.Schema.XmlSchemaSet> kod örneği.</span><span class="sxs-lookup"><span data-stu-id="8a775-131">The following is the equivalent <xref:System.Xml.Schema.XmlSchemaSet> code example.</span></span>  
  
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
  
## <a name="adding-and-retrieving-schemas"></a><span data-ttu-id="8a775-132">Ekleme ve şemaları alma</span><span class="sxs-lookup"><span data-stu-id="8a775-132">Adding and Retrieving Schemas</span></span>  
 <span data-ttu-id="8a775-133">Şemaları eklenir bir <xref:System.Xml.Schema.XmlSchemaSet> kullanarak <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> yöntemi <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="8a775-133">Schemas are added to an <xref:System.Xml.Schema.XmlSchemaSet> using the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="8a775-134">İçin bir şema eklendiğinde bir <xref:System.Xml.Schema.XmlSchemaSet>, bir hedef ad alanı URI ile ilişkilidir.</span><span class="sxs-lookup"><span data-stu-id="8a775-134">When a schema is added to an <xref:System.Xml.Schema.XmlSchemaSet>, it is associated with a target namespace URI.</span></span> <span data-ttu-id="8a775-135">Hedef ad alanı URI ya da belirtilebilir bir parametre olarak <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> yöntemi veya hiçbir hedef ad alanı belirtilmiş olup olmadığını <xref:System.Xml.Schema.XmlSchemaSet> şemasında tanımlanan hedef ad alanını kullanır.</span><span class="sxs-lookup"><span data-stu-id="8a775-135">The target namespace URI can either be specified as a parameter to the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method or if no target namespace is specified, the <xref:System.Xml.Schema.XmlSchemaSet> uses the target namespace defined in the schema.</span></span>  
  
 <span data-ttu-id="8a775-136">Şemaları öğesinden alınan bir <xref:System.Xml.Schema.XmlSchemaSet> kullanarak <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> özelliği <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="8a775-136">Schemas are retrieved from an <xref:System.Xml.Schema.XmlSchemaSet> using the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="8a775-137"><xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> Özelliği <xref:System.Xml.Schema.XmlSchemaSet> gezinilen sağlar <xref:System.Xml.Schema.XmlSchema> bulunan nesneleri <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="8a775-137">The <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet> allows you to iterate over the <xref:System.Xml.Schema.XmlSchema> objects contained in the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="8a775-138"><xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> Özellik ya da döndürür tüm <xref:System.Xml.Schema.XmlSchema> bulunan nesneleri <xref:System.Xml.Schema.XmlSchemaSet>, ya da bir hedef ad alanı parametresi, tüm döndürür <xref:System.Xml.Schema.XmlSchema> hedef ad alanına ait nesneleri.</span><span class="sxs-lookup"><span data-stu-id="8a775-138">The <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property either returns all the <xref:System.Xml.Schema.XmlSchema> objects contained in the <xref:System.Xml.Schema.XmlSchemaSet>, or, given a target namespace parameter, returns all the <xref:System.Xml.Schema.XmlSchema> objects that belong to the target namespace.</span></span> <span data-ttu-id="8a775-139">Varsa `null` hedef ad alanı parametre olarak belirtilen <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> özelliği ad alanı olmayan tüm şemalar döndürür.</span><span class="sxs-lookup"><span data-stu-id="8a775-139">If `null` is specified as the target namespace parameter, the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property returns all schemas without a namespace.</span></span>  
  
 <span data-ttu-id="8a775-140">Aşağıdaki örnek ekler `books.xsd` şemasında `http://www.contoso.com/books` ad alanına bir <xref:System.Xml.Schema.XmlSchemaSet>, ait tüm şemaları alır `http://www.contoso.com/books` ad alanından <xref:System.Xml.Schema.XmlSchemaSet>ve ardından bu şemaya Yazar <xref:System.Console>.</span><span class="sxs-lookup"><span data-stu-id="8a775-140">The following example adds the `books.xsd` schema in the `http://www.contoso.com/books` namespace to an <xref:System.Xml.Schema.XmlSchemaSet>, retrieves all schemas that belong to the `http://www.contoso.com/books` namespace from the <xref:System.Xml.Schema.XmlSchemaSet>, and then writes those schemas to the <xref:System.Console>.</span></span>  
  
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
  
 <span data-ttu-id="8a775-141">Ekleme ve şemalardan alma hakkında daha fazla bilgi için bir <xref:System.Xml.Schema.XmlSchemaSet> nesne, bkz: <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> yöntemi ve <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> özellik başvuru belgeleri.</span><span class="sxs-lookup"><span data-stu-id="8a775-141">For more information about adding and retrieving schemas from an <xref:System.Xml.Schema.XmlSchemaSet> object, see the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method and the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property reference documentation.</span></span>  
  
## <a name="compiling-schemas"></a><span data-ttu-id="8a775-142">Şemaları derlenirken</span><span class="sxs-lookup"><span data-stu-id="8a775-142">Compiling Schemas</span></span>  
 <span data-ttu-id="8a775-143">Şemalarda bir <xref:System.Xml.Schema.XmlSchemaSet> mantıksal bir şema tarafından derlenmiş <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> yöntemi <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="8a775-143">Schemas in an <xref:System.Xml.Schema.XmlSchemaSet> are compiled into one logical schema by the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8a775-144">Eski aksine <xref:System.Xml.Schema.XmlSchemaCollection> sınıfı şemaları olmayan zaman derlenmiş <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="8a775-144">Unlike the obsolete <xref:System.Xml.Schema.XmlSchemaCollection> class, schemas are not compiled when the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method is called.</span></span>  
  
 <span data-ttu-id="8a775-145">Varsa <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> yöntemini yürütür başarıyla <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> özelliği <xref:System.Xml.Schema.XmlSchemaSet> ayarlanır `true`.</span><span class="sxs-lookup"><span data-stu-id="8a775-145">If the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method executes successfully, the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet> is set to `true`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8a775-146"><xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> Şemaları düzenlediyseniz özelliği etkilenmez while <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="8a775-146">The <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property is not affected if schemas are edited while in the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="8a775-147">Güncelleştirmeleri tek tek şemalarda <xref:System.Xml.Schema.XmlSchemaSet> değil izlenir.</span><span class="sxs-lookup"><span data-stu-id="8a775-147">Updates of the individual schemas in the <xref:System.Xml.Schema.XmlSchemaSet> are not tracked.</span></span> <span data-ttu-id="8a775-148">Sonuç olarak, <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> özelliği `true` şemalardan birine bulunan olsa bile <xref:System.Xml.Schema.XmlSchemaSet> şema eklendi veya kaldırıldı sürece, değiştirilmiş <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="8a775-148">As a result, the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property can be `true` even though one of the schemas contained in the <xref:System.Xml.Schema.XmlSchemaSet> has been altered, as long as no schemas were added or removed from the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
 <span data-ttu-id="8a775-149">Aşağıdaki örnek ekler `books.xsd` dosyasını <xref:System.Xml.Schema.XmlSchemaSet> ve <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8a775-149">The following example adds the `books.xsd` file to the <xref:System.Xml.Schema.XmlSchemaSet> and then calls the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method.</span></span>  
  
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
  
 <span data-ttu-id="8a775-150">Şemalarda derleme hakkında daha fazla bilgi için bir <xref:System.Xml.Schema.XmlSchemaSet>, bkz: <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> yöntemi başvuru belgeleri.</span><span class="sxs-lookup"><span data-stu-id="8a775-150">For more information about compiling schemas in an <xref:System.Xml.Schema.XmlSchemaSet>, see the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method reference documentation.</span></span>  
  
## <a name="reprocessing-schemas"></a><span data-ttu-id="8a775-151">Şemaları yeniden işleniyor</span><span class="sxs-lookup"><span data-stu-id="8a775-151">Reprocessing Schemas</span></span>  
 <span data-ttu-id="8a775-152">Şemada yeniden işlemeyerek bir <xref:System.Xml.Schema.XmlSchemaSet> bir şema üzerinde gerçekleştirilen tüm ön işleme adımları gerçekleştirir, <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> yöntemi <xref:System.Xml.Schema.XmlSchemaSet> çağrılır.</span><span class="sxs-lookup"><span data-stu-id="8a775-152">Reprocessing a schema in an <xref:System.Xml.Schema.XmlSchemaSet> performs all the preprocessing steps performed on a schema when the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet> is called.</span></span> <span data-ttu-id="8a775-153">Çağrı <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> yöntemdir başarılı <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> özelliği <xref:System.Xml.Schema.XmlSchemaSet> ayarlanır `false`.</span><span class="sxs-lookup"><span data-stu-id="8a775-153">If the call to the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method is successful, the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet> is set to `false`.</span></span>  
  
 <span data-ttu-id="8a775-154"><xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> Yöntemi kullanılmalıdır şemada <xref:System.Xml.Schema.XmlSchemaSet> sonra değiştirilmiş <xref:System.Xml.Schema.XmlSchemaSet> derleme gerçekleştirdi.</span><span class="sxs-lookup"><span data-stu-id="8a775-154">The <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method should be used when a schema in the <xref:System.Xml.Schema.XmlSchemaSet> has been modified after the <xref:System.Xml.Schema.XmlSchemaSet> has performed compilation.</span></span>  
  
 <span data-ttu-id="8a775-155">Aşağıdaki örnekte, eklenen bir şema yeniden işlemeyerek gösterilmektedir <xref:System.Xml.Schema.XmlSchemaSet> kullanarak <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8a775-155">The following example illustrates reprocessing a schema added to the <xref:System.Xml.Schema.XmlSchemaSet> using the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method.</span></span> <span data-ttu-id="8a775-156">Sonra <xref:System.Xml.Schema.XmlSchemaSet> kullanılarak derlenmiş <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> yöntemi ve eklenen şemayı <xref:System.Xml.Schema.XmlSchemaSet> değiştirildiğinde <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> özelliği `true` şemada olsa bile <xref:System.Xml.Schema.XmlSchemaSet> değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="8a775-156">After the <xref:System.Xml.Schema.XmlSchemaSet> is compiled using the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method, and the schema added to the <xref:System.Xml.Schema.XmlSchemaSet> is modified, the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property is set to `true` even though a schema in the <xref:System.Xml.Schema.XmlSchemaSet> has been modified.</span></span> <span data-ttu-id="8a775-157">Çağırma <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> yöntemi gerçekleştirdiği tüm gerçekleştirdiği ön işleme <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> yöntemi ve kümelerini <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> özelliğini `false`.</span><span class="sxs-lookup"><span data-stu-id="8a775-157">Calling the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method performs all the preprocessing performed by the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method, and sets the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property to `false`.</span></span>  
  
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
  
 <span data-ttu-id="8a775-158">Şemada yeniden işlemeyerek hakkında daha fazla bilgi için bir <xref:System.Xml.Schema.XmlSchemaSet>, bkz: <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> yöntemi başvuru belgeleri.</span><span class="sxs-lookup"><span data-stu-id="8a775-158">For more information about reprocessing a schema in an <xref:System.Xml.Schema.XmlSchemaSet>, see the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method reference documentation.</span></span>  
  
## <a name="checking-for-a-schema"></a><span data-ttu-id="8a775-159">İçin bir şema denetleniyor</span><span class="sxs-lookup"><span data-stu-id="8a775-159">Checking for a Schema</span></span>  
 <span data-ttu-id="8a775-160">Kullanabileceğiniz <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> yöntemi <xref:System.Xml.Schema.XmlSchemaSet> bir şema içinde dahil olup olmadığını denetlemek için bir <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="8a775-160">You can use the <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet> to check if a schema is contained within an <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="8a775-161"><xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> Yöntemi alır ya da bir hedef ad alanı veya bir <xref:System.Xml.Schema.XmlSchema> denetlenecek nesne.</span><span class="sxs-lookup"><span data-stu-id="8a775-161">The <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> method takes either a target namespace or an <xref:System.Xml.Schema.XmlSchema> object to check for.</span></span> <span data-ttu-id="8a775-162">Her iki durumda da <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> yöntemi döndürür `true` şema içinde yer alıyorsa <xref:System.Xml.Schema.XmlSchemaSet>; Aksi halde döndürür `false`.</span><span class="sxs-lookup"><span data-stu-id="8a775-162">In either case, the <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> method returns `true` if the schema is contained within the <xref:System.Xml.Schema.XmlSchemaSet>; otherwise, it returns `false`.</span></span>  
  
 <span data-ttu-id="8a775-163">İçin bir şema denetleme hakkında daha fazla bilgi için bkz. <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> yöntemi başvuru belgeleri.</span><span class="sxs-lookup"><span data-stu-id="8a775-163">For more information about checking for a schema, see the <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> method reference documentation.</span></span>  
  
## <a name="removing-schemas"></a><span data-ttu-id="8a775-164">Şemaları kaldırılıyor</span><span class="sxs-lookup"><span data-stu-id="8a775-164">Removing Schemas</span></span>  
 <span data-ttu-id="8a775-165">Şemaları kaldırılma bir <xref:System.Xml.Schema.XmlSchemaSet> kullanarak <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> ve <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> yöntemlerinin <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="8a775-165">Schemas are removed from an <xref:System.Xml.Schema.XmlSchemaSet> using the <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> and <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> methods of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="8a775-166"><xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> Yöntemi, belirtilen şemasından kaldırır <xref:System.Xml.Schema.XmlSchemaSet>, ancak <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> yöntemi, belirtilen şemaya ve bunu içe aktaran tüm şemalar kaldırır <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="8a775-166">The <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> method removes the specified schema from the <xref:System.Xml.Schema.XmlSchemaSet>, while the <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> method removes the specified schema and all the schemas it imports from the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
 <span data-ttu-id="8a775-167">Ekleme için birden çok şema, aşağıdaki örnekte gösterilmiştir bir <xref:System.Xml.Schema.XmlSchemaSet>, ardından kullanarak <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> şemalardan birine ve bunu içe aktaran tüm şemalar kaldırmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8a775-167">The following example illustrates adding multiple schemas to an <xref:System.Xml.Schema.XmlSchemaSet>, then using the <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> method to remove one of the schemas and all the schemas it imports.</span></span>  
  
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
  
 <span data-ttu-id="8a775-168">Şemalardan kaldırma hakkında daha fazla bilgi için bir <xref:System.Xml.Schema.XmlSchemaSet>, bkz: <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> ve <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> yöntemleri başvuru belgeleri.</span><span class="sxs-lookup"><span data-stu-id="8a775-168">For more information about removing schemas from an <xref:System.Xml.Schema.XmlSchemaSet>, see the <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> and <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> methods reference documentation.</span></span>  
  
## <a name="schema-resolution-and-xsimport"></a><span data-ttu-id="8a775-169">Şema çözümleme ve xs:import</span><span class="sxs-lookup"><span data-stu-id="8a775-169">Schema Resolution and xs:import</span></span>  
 <span data-ttu-id="8a775-170">Aşağıdaki örnekler açıklar <xref:System.Xml.Schema.XmlSchemaSet> şemaları içeri aktarma için belirtilen bir ad alanı için birden çok şema mevcut olduğunda davranışı bir <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="8a775-170">The following examples describe the <xref:System.Xml.Schema.XmlSchemaSet> behavior for importing schemas when multiple schemas for a given namespace exist in an <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
 <span data-ttu-id="8a775-171">Örneğin, bir <xref:System.Xml.Schema.XmlSchemaSet> için birden çok şema içeren `http://www.contoso.com` ad alanı.</span><span class="sxs-lookup"><span data-stu-id="8a775-171">For example, consider an <xref:System.Xml.Schema.XmlSchemaSet> that contains multiple schemas for the `http://www.contoso.com` namespace.</span></span> <span data-ttu-id="8a775-172">Aşağıdaki şema `xs:import` yönergesi eklenir <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="8a775-172">A schema with the following `xs:import` directive is added to the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
```xml  
<xs:import namespace="http://www.contoso.com" schemaLocation="http://www.contoso.com/schema.xsd" />  
```  
  
 <span data-ttu-id="8a775-173"><xref:System.Xml.Schema.XmlSchemaSet> İçeri aktarmak için bir şema dener `http://www.contoso.com` ondan yükleme tarafından ad alanı `http://www.contoso.com/schema.xsd` URL'si.</span><span class="sxs-lookup"><span data-stu-id="8a775-173">The <xref:System.Xml.Schema.XmlSchemaSet> attempts to import a schema for the `http://www.contoso.com` namespace by loading it from the `http://www.contoso.com/schema.xsd` URL.</span></span> <span data-ttu-id="8a775-174">Diğer şeması belgeleri için olsa bile şema belgesi içinde bildirilen türleri ve şema bildirim alma şemada yalnızca kullanılabilir `http://www.contoso.com` ad alanında <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="8a775-174">Only the schema declaration and types declared in the schema document are available in the importing schema, even though there are other schema documents for the `http://www.contoso.com` namespace in the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="8a775-175">Varsa `schema.xsd` dosya konumu olamaz `http://www.contoso.com/schema.xsd` URL için şema `http://www.contoso.com` ad alanı alma şemasına aktarılır.</span><span class="sxs-lookup"><span data-stu-id="8a775-175">If the `schema.xsd` file cannot be located at the `http://www.contoso.com/schema.xsd` URL, no schema for the `http://www.contoso.com` namespace is imported into the importing schema.</span></span>  
  
## <a name="validating-xml-documents"></a><span data-ttu-id="8a775-176">XML belgeleri doğrulanıyor</span><span class="sxs-lookup"><span data-stu-id="8a775-176">Validating XML Documents</span></span>  
 <span data-ttu-id="8a775-177">XML belgeleri doğrulanmış şemalarda karşı bir <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="8a775-177">XML documents can be validated against schemas in an <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="8a775-178">Bir şema ekleyerek bir XML belgesi doğrulama <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.XmlReaderSettings.Schemas%2A> özelliği bir <xref:System.Xml.XmlReaderSettings> nesne veya ekleyerek bir <xref:System.Xml.Schema.XmlSchemaSet> için <xref:System.Xml.XmlReaderSettings.Schemas%2A> özelliği bir <xref:System.Xml.XmlReaderSettings> nesne.</span><span class="sxs-lookup"><span data-stu-id="8a775-178">You validate an XML document by adding a schema to the <xref:System.Xml.Schema.XmlSchemaSet><xref:System.Xml.XmlReaderSettings.Schemas%2A> property of an <xref:System.Xml.XmlReaderSettings> object, or by adding an <xref:System.Xml.Schema.XmlSchemaSet> to the <xref:System.Xml.XmlReaderSettings.Schemas%2A> property of an <xref:System.Xml.XmlReaderSettings> object.</span></span> <span data-ttu-id="8a775-179"><xref:System.Xml.XmlReaderSettings> Nesne tarafından kullanılan ardından <xref:System.Xml.XmlReader.Create%2A> yöntemi <xref:System.Xml.XmlReader> sınıfı oluşturmak için bir <xref:System.Xml.XmlReader> nesnesi ve bir XML belgesi doğrulama.</span><span class="sxs-lookup"><span data-stu-id="8a775-179">The <xref:System.Xml.XmlReaderSettings> object is then used by the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> class to create an <xref:System.Xml.XmlReader> object and validate the XML document.</span></span>  
  
 <span data-ttu-id="8a775-180">XML doğrulama hakkında daha fazla bilgi için belgeler kullanan bir <xref:System.Xml.Schema.XmlSchemaSet>, bkz: [XmlSchemaSet ile XML Şeması (XSD) doğrulaması](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemaset.md).</span><span class="sxs-lookup"><span data-stu-id="8a775-180">For more information about validating XML documents using an <xref:System.Xml.Schema.XmlSchemaSet>, see [XML Schema (XSD) Validation with XmlSchemaSet](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemaset.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a775-181">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8a775-181">See also</span></span>

- <xref:System.Xml.Schema.XmlSchemaSet.Add%2A>  
- <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A>  
- <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A>  
- <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A>  
- <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A>  
- <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A>  
- <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A>  
- [<span data-ttu-id="8a775-182">Şema önbelleği olarak XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="8a775-182">XmlSchemaSet as a Schema Cache</span></span>](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
- [<span data-ttu-id="8a775-183">XmlSchemaSet ile XML Şeması (XSD) Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="8a775-183">XML Schema (XSD) Validation with XmlSchemaSet</span></span>](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemaset.md)
