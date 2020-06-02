---
title: XML Belgeleri ve Verileri
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: e695047f-3c0f-4045-8708-5baea91cc380
ms.openlocfilehash: a752d634141a56df1caa61eb5d375dd2a402832f
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287694"
---
# <a name="xml-documents-and-data"></a><span data-ttu-id="7b79f-102">XML Belgeleri ve Verileri</span><span class="sxs-lookup"><span data-stu-id="7b79f-102">XML Documents and Data</span></span>

<span data-ttu-id="7b79f-103">.NET Framework, XML kullanan uygulamaları kolayca oluşturmanıza olanak tanıyan kapsamlı ve tümleşik bir sınıf kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="7b79f-103">The .NET Framework provides a comprehensive and integrated set of classes that enable you to build XML-aware apps easily.</span></span> <span data-ttu-id="7b79f-104">Aşağıdaki ad alanlarındaki sınıflar, XML 'i ayrıştırmayı ve yazmayı, bellekte XML verilerini düzenlemenizi, veri doğrulamayı ve XSLT dönüşümünü destekler.</span><span class="sxs-lookup"><span data-stu-id="7b79f-104">The classes in the following namespaces support parsing and writing XML, editing XML data in memory, data validation, and XSLT transformation.</span></span>

- <xref:System.Xml>

- <xref:System.Xml.XPath>

- <xref:System.Xml.Xsl>

- <xref:System.Xml.Schema>

- <xref:System.Xml.Linq>

<span data-ttu-id="7b79f-105">Tam liste için [.NET API tarayıcısı](https://docs.microsoft.com/dotnet/api/?term=system.xml)üzerinde "System. xml" araması yapın.</span><span class="sxs-lookup"><span data-stu-id="7b79f-105">For a full list, search for "System.Xml" on the [.NET API browser](https://docs.microsoft.com/dotnet/api/?term=system.xml).</span></span>

<span data-ttu-id="7b79f-106">Bu ad alanındaki sınıflar World Wide Web Konsorsiyumu (W3C) önerilerini destekler.</span><span class="sxs-lookup"><span data-stu-id="7b79f-106">The classes in these namespaces support World Wide Web Consortium (W3C) recommendations.</span></span> <span data-ttu-id="7b79f-107">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="7b79f-107">For example:</span></span>

- <span data-ttu-id="7b79f-108"><xref:System.Xml.XmlDocument?displayProperty=nameWithType>Sınıfı, [W3C belge nesne MODELI (DOM) düzey 1 Core](https://www.w3.org/TR/REC-DOM-Level-1/) ve [DOM düzey 2 temel](https://www.w3.org/TR/DOM-Level-2-Core/) önerilerini uygular.</span><span class="sxs-lookup"><span data-stu-id="7b79f-108">The <xref:System.Xml.XmlDocument?displayProperty=nameWithType> class implements the [W3C Document Object Model (DOM) Level 1 Core](https://www.w3.org/TR/REC-DOM-Level-1/) and [DOM Level 2 Core](https://www.w3.org/TR/DOM-Level-2-Core/) recommendations.</span></span>

- <span data-ttu-id="7b79f-109"><xref:System.Xml.XmlReader?displayProperty=nameWithType>Ve <xref:System.Xml.XmlWriter?displayProperty=nameWithType> SıNıFLARı [W3C XML 1,0](https://www.w3.org/TR/2006/REC-xml-20060816/) ' i ve XML önerilerinde [ad alanlarını](https://www.w3.org/TR/REC-xml-names/) destekler.</span><span class="sxs-lookup"><span data-stu-id="7b79f-109">The <xref:System.Xml.XmlReader?displayProperty=nameWithType> and <xref:System.Xml.XmlWriter?displayProperty=nameWithType> classes support the [W3C XML 1.0](https://www.w3.org/TR/2006/REC-xml-20060816/) and the [Namespaces in XML](https://www.w3.org/TR/REC-xml-names/) recommendations.</span></span>

- <span data-ttu-id="7b79f-110"><xref:System.Xml.Schema.XmlSchemaSet?displayProperty=nameWithType>Sınıftaki şemalar [W3C XML şeması Bölüm 1: yapılar](https://www.w3.org/TR/xmlschema-1/) ve [XML şeması Bölüm 2: veri türleri](https://www.w3.org/TR/xmlschema-2/) önerilerini destekler.</span><span class="sxs-lookup"><span data-stu-id="7b79f-110">Schemas in the <xref:System.Xml.Schema.XmlSchemaSet?displayProperty=nameWithType> class support the [W3C XML Schema Part 1: Structures](https://www.w3.org/TR/xmlschema-1/) and [XML Schema Part 2: Datatypes](https://www.w3.org/TR/xmlschema-2/) recommendations.</span></span>

- <span data-ttu-id="7b79f-111"><xref:System.Xml.Xsl?displayProperty=nameWithType>Ad alanındaki sınıflar, [W3C XSLT 1,0](https://www.w3.org/TR/xslt) ÖNERISI ile uyumlu XSLT dönüştürmelerini destekler.</span><span class="sxs-lookup"><span data-stu-id="7b79f-111">Classes in the <xref:System.Xml.Xsl?displayProperty=nameWithType> namespace support XSLT transformations that conform to the [W3C XSLT 1.0](https://www.w3.org/TR/xslt) recommendation.</span></span>

<span data-ttu-id="7b79f-112">.NET Framework XML sınıfları şu avantajları sağlar:</span><span class="sxs-lookup"><span data-stu-id="7b79f-112">The XML classes in the .NET Framework provide these benefits:</span></span>

- <span data-ttu-id="7b79f-113">**Kişilere.**</span><span class="sxs-lookup"><span data-stu-id="7b79f-113">**Productivity.**</span></span> <span data-ttu-id="7b79f-114">[LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) ve [LINQ to XML (VISUAL BASIC)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md) , XML ile PROGRAMLANMASıNı kolaylaştırır ve SQL 'e benzer bir sorgu deneyimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="7b79f-114">[LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) and [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md) makes it easier to program with XML and provides a query experience that is similar to SQL.</span></span>

- <span data-ttu-id="7b79f-115">**Genişletme.**</span><span class="sxs-lookup"><span data-stu-id="7b79f-115">**Extensibility.**</span></span> <span data-ttu-id="7b79f-116">.NET Framework XML sınıfları soyut temel sınıfların ve Sanal yöntemlerin kullanımı ile genişletilebilir.</span><span class="sxs-lookup"><span data-stu-id="7b79f-116">The XML classes in the .NET Framework are extensible through the use of abstract base classes and virtual methods.</span></span> <span data-ttu-id="7b79f-117">Örneğin, <xref:System.Xml.XmlUrlResolver> önbellek akışını yerel diske depolayan sınıfın türetilmiş bir sınıfını oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7b79f-117">For example, you can create a derived class of the <xref:System.Xml.XmlUrlResolver> class that stores the cache stream to the local disk.</span></span>

- <span data-ttu-id="7b79f-118">**Takılabilir mimari.**</span><span class="sxs-lookup"><span data-stu-id="7b79f-118">**Pluggable architecture.**</span></span> <span data-ttu-id="7b79f-119">.NET Framework, bileşenlerin bir diğeri tarafından kullanılabilecek bir mimari sağlar ve verilerin bileşenler arasında akışı yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="7b79f-119">The .NET Framework provides an architecture in which components can utilize one another, and data can be streamed between components.</span></span> <span data-ttu-id="7b79f-120">Örneğin, bir veya nesnesi gibi bir veri deposu <xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XmlDocument> <xref:System.Xml.Xsl.XslCompiledTransform> sınıfıyla dönüştürülebilir ve daha sonra çıktı, başka bir depoya akışı yapılabilir veya bir Web hizmetinden akış olarak döndürülür.</span><span class="sxs-lookup"><span data-stu-id="7b79f-120">For example, a data store, such as an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object, can be transformed with the <xref:System.Xml.Xsl.XslCompiledTransform> class, and the output can then be streamed either into another store or returned as a stream from a web service.</span></span>

- <span data-ttu-id="7b79f-121">**Mının.**</span><span class="sxs-lookup"><span data-stu-id="7b79f-121">**Performance.**</span></span> <span data-ttu-id="7b79f-122">Daha iyi uygulama performansı için .NET Framework bazı XML sınıfları aşağıdaki özelliklerle akış tabanlı bir modeli destekler:</span><span class="sxs-lookup"><span data-stu-id="7b79f-122">For better app performance, some of the XML classes in the .NET Framework support a streaming-based model with the following characteristics:</span></span>

  - <span data-ttu-id="7b79f-123">Yalnızca iletme, çekme modeli ayrıştırma () için en az önbelleğe alma <xref:System.Xml.XmlReader> .</span><span class="sxs-lookup"><span data-stu-id="7b79f-123">Minimal caching for forward-only, pull-model parsing (<xref:System.Xml.XmlReader>).</span></span>

  - <span data-ttu-id="7b79f-124">Yalnızca ileri doğrulama ( <xref:System.Xml.XmlReader> ).</span><span class="sxs-lookup"><span data-stu-id="7b79f-124">Forward-only validation (<xref:System.Xml.XmlReader>).</span></span>

  - <span data-ttu-id="7b79f-125">Belgeye rastgele erişim sağlarken, düğüm oluşturmayı tek bir sanal düğüme en aza indiren imleç stili gezintisi <xref:System.Xml.XPath.XPathNavigator> .</span><span class="sxs-lookup"><span data-stu-id="7b79f-125">Cursor style navigation that minimizes node creation to a single virtual node while providing random access to the document (<xref:System.Xml.XPath.XPathNavigator>).</span></span>

  <span data-ttu-id="7b79f-126">XSLT işleme gerektiğinde daha iyi performans için, <xref:System.Xml.XPath.XPathDocument> sınıfıyla verimli şekilde çalışacak şekilde tasarlanan XPath sorguları için iyileştirilmiş, salt okunurdur bir depo olan sınıfını kullanabilirsiniz <xref:System.Xml.Xsl.XslCompiledTransform> .</span><span class="sxs-lookup"><span data-stu-id="7b79f-126">For better performance whenever XSLT processing is required, you can use the <xref:System.Xml.XPath.XPathDocument> class, which is an optimized, read-only store for XPath queries designed to work efficiently with the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>

- <span data-ttu-id="7b79f-127">**ADO.NET ile tümleştirme.**</span><span class="sxs-lookup"><span data-stu-id="7b79f-127">**Integration with ADO.NET.**</span></span> <span data-ttu-id="7b79f-128">XML sınıfları ve [ADO.net](../../../framework/data/adonet/index.md) , ilişkisel VERILERI ve XML 'yi biraraya getirmek için sıkı bir şekilde tümleşiktir.</span><span class="sxs-lookup"><span data-stu-id="7b79f-128">The XML classes and [ADO.NET](../../../framework/data/adonet/index.md) are tightly integrated to bring together relational data and XML.</span></span> <span data-ttu-id="7b79f-129"><xref:System.Data.DataSet>Sınıfı, bir veritabanından alınan verilerin bellek içi önbelleğidir.</span><span class="sxs-lookup"><span data-stu-id="7b79f-129">The <xref:System.Data.DataSet> class is an in-memory cache of data retrieved from a database.</span></span> <span data-ttu-id="7b79f-130"><xref:System.Data.DataSet>Sınıfı, ve sınıflarını kullanarak XML okuma ve yazma özelliğine sahiptir <xref:System.Xml.XmlReader> <xref:System.Xml.XmlWriter> , iç ILIŞKISEL şema yapısını XML şemaları (xsd) olarak kalıcı hale getırmek ve bir XML belgesinin şema yapısını çıkarması için.</span><span class="sxs-lookup"><span data-stu-id="7b79f-130">The <xref:System.Data.DataSet> class has the ability to read and write XML by using the <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter> classes, to persist its internal relational schema structure as XML schemas (XSD), and to infer the schema structure of an XML document.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="7b79f-131">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="7b79f-131">In This Section</span></span>

<span data-ttu-id="7b79f-132">[XML Işleme seçenekleri](xml-processing-options.md) XML verilerini işlemeye yönelik seçenekleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="7b79f-132">[XML Processing Options](xml-processing-options.md) Discusses options for processing XML data.</span></span>

<span data-ttu-id="7b79f-133">[XML verilerini bellek Içinde işleme](processing-xml-data-in-memory.md) XML verilerini bellek içinde işlemeye yönelik üç modeli açıklar: [LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) ve [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md), <xref:System.Xml.XmlDocument> sınıfı (W3C belge nesne modeli göre) ve <xref:System.Xml.XPath.XPathDocument> sınıfı (XPath veri modeline göre).</span><span class="sxs-lookup"><span data-stu-id="7b79f-133">[Processing XML Data In-Memory](processing-xml-data-in-memory.md) Discusses the three models for processing XML data in-memory: [LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) and [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md), the <xref:System.Xml.XmlDocument> class (based on the W3C Document Object Model), and the <xref:System.Xml.XPath.XPathDocument> class (based on the XPath data model).</span></span>

<span data-ttu-id="7b79f-134">[XSLT dönüşümleri](xslt-transformations.md)</span><span class="sxs-lookup"><span data-stu-id="7b79f-134">[XSLT Transformations](xslt-transformations.md)</span></span>\
<span data-ttu-id="7b79f-135">XSLT işlemcisinin nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="7b79f-135">Describes how to use the XSLT processor.</span></span>

<span data-ttu-id="7b79f-136">[XML şema nesne modeli (SOM)](xml-schema-object-model-som.md)</span><span class="sxs-lookup"><span data-stu-id="7b79f-136">[XML Schema Object Model (SOM)](xml-schema-object-model-som.md)</span></span>\
<span data-ttu-id="7b79f-137"><xref:System.Xml.Schema.XmlSchema>Bir şemayı yüklemek ve düzenlemek için bir sınıf sağlayarak xml şemaları (xsd) oluşturmak ve işlemek için kullanılan sınıfları açıklar.</span><span class="sxs-lookup"><span data-stu-id="7b79f-137">Describes the classes used for building and manipulating XML Schemas (XSD) by providing an <xref:System.Xml.Schema.XmlSchema> class to load and edit a schema.</span></span>

<span data-ttu-id="7b79f-138">[Ilişkisel verilerle XML tümleştirmesi ve ADO.NET](xml-integration-with-relational-data-and-adonet.md)</span><span class="sxs-lookup"><span data-stu-id="7b79f-138">[XML Integration with Relational Data and ADO.NET](xml-integration-with-relational-data-and-adonet.md)</span></span>\
<span data-ttu-id="7b79f-139">.NET Framework, nesne ve nesne aracılığıyla hem ilişkisel hem de hiyerarşik veri temsillerine gerçek zamanlı, zaman uyumlu erişim nasıl olanak sağladığını açıklar <xref:System.Data.DataSet> <xref:System.Xml.XmlDataDocument> .</span><span class="sxs-lookup"><span data-stu-id="7b79f-139">Describes how the .NET Framework enables real-time, synchronous access to both the relational and hierarchical representations of data through the <xref:System.Data.DataSet> object and the <xref:System.Xml.XmlDataDocument> object.</span></span>

<span data-ttu-id="7b79f-140">[XML belgesinde ad alanlarını yönetme](managing-namespaces-in-an-xml-document.md)</span><span class="sxs-lookup"><span data-stu-id="7b79f-140">[Managing Namespaces in an XML Document](managing-namespaces-in-an-xml-document.md)</span></span>\
<span data-ttu-id="7b79f-141"><xref:System.Xml.XmlNamespaceManager>Sınıfının ad alanı bilgilerini depolamak ve korumak için nasıl kullanıldığını açıklar.</span><span class="sxs-lookup"><span data-stu-id="7b79f-141">Describes how the <xref:System.Xml.XmlNamespaceManager> class is used to store and maintain namespace information.</span></span>

<span data-ttu-id="7b79f-142">[System. xml sınıflarında destek yazın](type-support-in-the-system-xml-classes.md)</span><span class="sxs-lookup"><span data-stu-id="7b79f-142">[Type Support in the System.Xml Classes](type-support-in-the-system-xml-classes.md)</span></span>\
<span data-ttu-id="7b79f-143">XML veri türlerinin CLR türleriyle nasıl eşlendikleri, XML veri türlerinin nasıl dönüştürüleceği ve sınıflardaki diğer tür desteğinin nasıl değiştirileceği açıklanmaktadır <xref:System.Xml> .</span><span class="sxs-lookup"><span data-stu-id="7b79f-143">Describes how XML data types map to CLR types, how to convert XML data types, and other type support features in the <xref:System.Xml> classes.</span></span>

## <a name="related-sections"></a><span data-ttu-id="7b79f-144">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="7b79f-144">Related Sections</span></span>

<span data-ttu-id="7b79f-145">[ADO.NET](../../../framework/data/adonet/index.md)</span><span class="sxs-lookup"><span data-stu-id="7b79f-145">[ADO.NET](../../../framework/data/adonet/index.md)</span></span>\
<span data-ttu-id="7b79f-146">ADO.NET kullanarak verilere erişme hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="7b79f-146">Provides information on how to access data using ADO.NET.</span></span>

<span data-ttu-id="7b79f-147">[Güven](../../security/index.md)</span><span class="sxs-lookup"><span data-stu-id="7b79f-147">[Security](../../security/index.md)</span></span>\
<span data-ttu-id="7b79f-148">.NET Framework güvenlik sistemine genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="7b79f-148">Provides an overview of the .NET Framework security system.</span></span>
