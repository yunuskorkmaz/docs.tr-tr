---
title: XML Belgeleri ve Verileri
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: e695047f-3c0f-4045-8708-5baea91cc380
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 073b28d353bb7ea43775c7e20ddf7241cabf7d9a
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67664011"
---
# <a name="xml-documents-and-data"></a><span data-ttu-id="7901b-102">XML Belgeleri ve Verileri</span><span class="sxs-lookup"><span data-stu-id="7901b-102">XML Documents and Data</span></span>

<span data-ttu-id="7901b-103">.NET Framework XML algılayan uygulamaları kolayca oluşturmanıza olanak tanıyan sınıf kapsamlı ve tümleşik kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="7901b-103">The .NET Framework provides a comprehensive and integrated set of classes that enable you to build XML-aware apps easily.</span></span> <span data-ttu-id="7901b-104">Aşağıdaki ad alanındaki sınıflar, ayrıştırma ve XML, bellek, veri doğrulama ve XSLT dönüşümü XML verilerini düzenleme yazma desteği.</span><span class="sxs-lookup"><span data-stu-id="7901b-104">The classes in the following namespaces support parsing and writing XML, editing XML data in memory, data validation, and XSLT transformation.</span></span>

- <xref:System.Xml>

- <xref:System.Xml.XPath>

- <xref:System.Xml.Xsl>

- <xref:System.Xml.Schema>

- <xref:System.Xml.Linq>

<span data-ttu-id="7901b-105">Tam listesi için "System.Xml" için arama [.NET API browser](https://docs.microsoft.com/dotnet/api/?term=system.xml).</span><span class="sxs-lookup"><span data-stu-id="7901b-105">For a full list, search for "System.Xml" on the [.NET API browser](https://docs.microsoft.com/dotnet/api/?term=system.xml).</span></span>

<span data-ttu-id="7901b-106">Bu ad alanındaki sınıflar, World Wide Web Consortium (W3C) önerileri destekler.</span><span class="sxs-lookup"><span data-stu-id="7901b-106">The classes in these namespaces support World Wide Web Consortium (W3C) recommendations.</span></span> <span data-ttu-id="7901b-107">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="7901b-107">For example:</span></span>

- <span data-ttu-id="7901b-108"><xref:System.Xml.XmlDocument?displayProperty=nameWithType> Sınıfının Implements [W3C belge nesne modeli (DOM) Düzey 1 çekirdek](https://www.w3.org/TR/REC-DOM-Level-1/) ve [DOM düzeyi 2 Çekirdek](https://www.w3.org/TR/DOM-Level-2-Core/) öneriler.</span><span class="sxs-lookup"><span data-stu-id="7901b-108">The <xref:System.Xml.XmlDocument?displayProperty=nameWithType> class implements the [W3C Document Object Model (DOM) Level 1 Core](https://www.w3.org/TR/REC-DOM-Level-1/) and [DOM Level 2 Core](https://www.w3.org/TR/DOM-Level-2-Core/) recommendations.</span></span>

- <span data-ttu-id="7901b-109"><xref:System.Xml.XmlReader?displayProperty=nameWithType> Ve <xref:System.Xml.XmlWriter?displayProperty=nameWithType> destek sınıfları [W3C XML 1.0](https://www.w3.org/TR/2006/REC-xml-20060816/) ve [ad alanları XML](https://www.w3.org/TR/REC-xml-names/) öneriler.</span><span class="sxs-lookup"><span data-stu-id="7901b-109">The <xref:System.Xml.XmlReader?displayProperty=nameWithType> and <xref:System.Xml.XmlWriter?displayProperty=nameWithType> classes support the [W3C XML 1.0](https://www.w3.org/TR/2006/REC-xml-20060816/) and the [Namespaces in XML](https://www.w3.org/TR/REC-xml-names/) recommendations.</span></span>

- <span data-ttu-id="7901b-110">Şemalarda <xref:System.Xml.Schema.XmlSchemaSet?displayProperty=nameWithType> sınıf destek [W3C XML Şeması Kısım 1: Yapıları](https://www.w3.org/TR/xmlschema-1/) ve [XML şema bölümü 2: Veri türleri](https://www.w3.org/TR/xmlschema-2/) öneriler.</span><span class="sxs-lookup"><span data-stu-id="7901b-110">Schemas in the <xref:System.Xml.Schema.XmlSchemaSet?displayProperty=nameWithType> class support the [W3C XML Schema Part 1: Structures](https://www.w3.org/TR/xmlschema-1/) and [XML Schema Part 2: Datatypes](https://www.w3.org/TR/xmlschema-2/) recommendations.</span></span>

- <span data-ttu-id="7901b-111">Sınıflar <xref:System.Xml.Xsl?displayProperty=nameWithType> uygun ad alanı desteği XSLT dönüşümleri [W3C XSLT 1.0](https://www.w3.org/TR/xslt) öneri.</span><span class="sxs-lookup"><span data-stu-id="7901b-111">Classes in the <xref:System.Xml.Xsl?displayProperty=nameWithType> namespace support XSLT transformations that conform to the [W3C XSLT 1.0](https://www.w3.org/TR/xslt) recommendation.</span></span>

<span data-ttu-id="7901b-112">.NET Framework XML sınıflarda aşağıdaki avantajları sağlar:</span><span class="sxs-lookup"><span data-stu-id="7901b-112">The XML classes in the .NET Framework provide these benefits:</span></span>

- <span data-ttu-id="7901b-113">**Üretkenlik.**</span><span class="sxs-lookup"><span data-stu-id="7901b-113">**Productivity.**</span></span> <span data-ttu-id="7901b-114">[LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) ve [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md) XML programla kolaylaştırır ve SQL'e benzeyen bir sorgu deneyimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="7901b-114">[LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) and [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md) makes it easier to program with XML and provides a query experience that is similar to SQL.</span></span>

- <span data-ttu-id="7901b-115">**Genişletilebilirlik.**</span><span class="sxs-lookup"><span data-stu-id="7901b-115">**Extensibility.**</span></span> <span data-ttu-id="7901b-116">.NET Framework'te XML sınıflarının soyut temel sınıflar ve sanal yöntemleri kullanılarak genişletilebilir.</span><span class="sxs-lookup"><span data-stu-id="7901b-116">The XML classes in the .NET Framework are extensible through the use of abstract base classes and virtual methods.</span></span> <span data-ttu-id="7901b-117">Örneğin, türetilmiş bir sınıf oluşturabilirsiniz <xref:System.Xml.XmlUrlResolver> yerel disk önbellek akışa depolayan sınıf.</span><span class="sxs-lookup"><span data-stu-id="7901b-117">For example, you can create a derived class of the <xref:System.Xml.XmlUrlResolver> class that stores the cache stream to the local disk.</span></span>

- <span data-ttu-id="7901b-118">**Eklenebilir mimari.**</span><span class="sxs-lookup"><span data-stu-id="7901b-118">**Pluggable architecture.**</span></span> <span data-ttu-id="7901b-119">.NET Framework bileşenleri, birbirleriyle kullanabilir ve bileşenler arasında verilerin gönderilebilen bir mimari sağlar.</span><span class="sxs-lookup"><span data-stu-id="7901b-119">The .NET Framework provides an architecture in which components can utilize one another, and data can be streamed between components.</span></span> <span data-ttu-id="7901b-120">Örneğin, bir veri deposu gibi bir <xref:System.Xml.XPath.XPathDocument> veya <xref:System.Xml.XmlDocument> nesne, ile dönüştürülebilir <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı ve çıktısını ardından olabilir ya da başka bir depoya akış yoluyla veya bir web hizmetinden bir akış olarak döndürdü.</span><span class="sxs-lookup"><span data-stu-id="7901b-120">For example, a data store, such as an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object, can be transformed with the <xref:System.Xml.Xsl.XslCompiledTransform> class, and the output can then be streamed either into another store or returned as a stream from a web service.</span></span>

- <span data-ttu-id="7901b-121">**Performans.**</span><span class="sxs-lookup"><span data-stu-id="7901b-121">**Performance.**</span></span> <span data-ttu-id="7901b-122">Daha iyi uygulama performansını için .NET Framework XML sınıflarda bazıları aşağıdaki özelliklere sahip bir akış tabanlı model destekler:</span><span class="sxs-lookup"><span data-stu-id="7901b-122">For better app performance, some of the XML classes in the .NET Framework support a streaming-based model with the following characteristics:</span></span>

  - <span data-ttu-id="7901b-123">Yalnızca iletme, çekme modeli ayrıştırmak için en az önbelleğe alma (<xref:System.Xml.XmlReader>).</span><span class="sxs-lookup"><span data-stu-id="7901b-123">Minimal caching for forward-only, pull-model parsing (<xref:System.Xml.XmlReader>).</span></span>

  - <span data-ttu-id="7901b-124">Yalnızca iletme doğrulama (<xref:System.Xml.XmlReader>).</span><span class="sxs-lookup"><span data-stu-id="7901b-124">Forward-only validation (<xref:System.Xml.XmlReader>).</span></span>

  - <span data-ttu-id="7901b-125">Tek bir sanal düğüm için düğüm oluşturma belge için rastgele erişim sağlarken en aza indirir, imleç stil Gezinti (<xref:System.Xml.XPath.XPathNavigator>).</span><span class="sxs-lookup"><span data-stu-id="7901b-125">Cursor style navigation that minimizes node creation to a single virtual node while providing random access to the document (<xref:System.Xml.XPath.XPathNavigator>).</span></span>

  <span data-ttu-id="7901b-126">Daha iyi performans için XSLT işleme gerektiğinde kullanabileceğiniz <xref:System.Xml.XPath.XPathDocument> bir XPath sorguları ile verimli bir şekilde çalışmak üzere tasarlanmış için iyileştirilmiş, salt okunur depo sınıfını <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="7901b-126">For better performance whenever XSLT processing is required, you can use the <xref:System.Xml.XPath.XPathDocument> class, which is an optimized, read-only store for XPath queries designed to work efficiently with the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>

- <span data-ttu-id="7901b-127">**ADO.NET ile tümleştirme.**</span><span class="sxs-lookup"><span data-stu-id="7901b-127">**Integration with ADO.NET.**</span></span> <span data-ttu-id="7901b-128">XML sınıfları ve [ADO.NET](../../../../docs/framework/data/adonet/index.md) ilişkisel veriler ve XML bir araya getirmek için sıkı bir şekilde tümleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="7901b-128">The XML classes and [ADO.NET](../../../../docs/framework/data/adonet/index.md) are tightly integrated to bring together relational data and XML.</span></span> <span data-ttu-id="7901b-129"><xref:System.Data.DataSet> Sınıfı, bir bellek içi önbelleği bir veritabanından alınan veri.</span><span class="sxs-lookup"><span data-stu-id="7901b-129">The <xref:System.Data.DataSet> class is an in-memory cache of data retrieved from a database.</span></span> <span data-ttu-id="7901b-130"><xref:System.Data.DataSet> Sınıfında okuma ve XML kullanarak yazma olanağı <xref:System.Xml.XmlReader> ve <xref:System.Xml.XmlWriter> sınıfları, iç ilişkisel şema yapısını XML şemaları (XSD) kalıcı hale getirmek için ve bir XML belgesi şema yapısını çıkarsamak için.</span><span class="sxs-lookup"><span data-stu-id="7901b-130">The <xref:System.Data.DataSet> class has the ability to read and write XML by using the <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter> classes, to persist its internal relational schema structure as XML schemas (XSD), and to infer the schema structure of an XML document.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="7901b-131">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="7901b-131">In This Section</span></span>

<span data-ttu-id="7901b-132">[XML işleme seçenekleri](../../../../docs/standard/data/xml/xml-processing-options.md) XML verilerini işlemek için seçenekleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="7901b-132">[XML Processing Options](../../../../docs/standard/data/xml/xml-processing-options.md) Discusses options for processing XML data.</span></span>

<span data-ttu-id="7901b-133">[XML verilerini bellek içi işleme](../../../../docs/standard/data/xml/processing-xml-data-in-memory.md) XML verileri bellek içinde işleme için üç model açıklanmaktadır: [LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml.md) ve [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md), <xref:System.Xml.XmlDocument> (W3C belge nesnesi modeline dayalı), sınıf ve <xref:System.Xml.XPath.XPathDocument> sınıfı (XPath veri modelini temel).</span><span class="sxs-lookup"><span data-stu-id="7901b-133">[Processing XML Data In-Memory](../../../../docs/standard/data/xml/processing-xml-data-in-memory.md) Discusses the three models for processing XML data in-memory: [LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml.md) and [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md), the <xref:System.Xml.XmlDocument> class (based on the W3C Document Object Model), and the <xref:System.Xml.XPath.XPathDocument> class (based on the XPath data model).</span></span>

<span data-ttu-id="7901b-134">[XSLT dönüşümleri](../../../../docs/standard/data/xml/xslt-transformations.md)</span><span class="sxs-lookup"><span data-stu-id="7901b-134">[XSLT Transformations](../../../../docs/standard/data/xml/xslt-transformations.md)</span></span>\
<span data-ttu-id="7901b-135">XSLT işlemci kullanmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="7901b-135">Describes how to use the XSLT processor.</span></span>

<span data-ttu-id="7901b-136">[XML şema nesne modeli (SOM)](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)</span><span class="sxs-lookup"><span data-stu-id="7901b-136">[XML Schema Object Model (SOM)](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)</span></span>\
<span data-ttu-id="7901b-137">XML şemaları (XSD) sağlayarak düzenleme ve oluşturma için kullanılan sınıfları açıklar bir <xref:System.Xml.Schema.XmlSchema> yüklemek ve bir şema düzenlemek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="7901b-137">Describes the classes used for building and manipulating XML Schemas (XSD) by providing an <xref:System.Xml.Schema.XmlSchema> class to load and edit a schema.</span></span>

<span data-ttu-id="7901b-138">[İlişkisel veriler ve ADO.NET ile XML tümleştirmesi](../../../../docs/standard/data/xml/xml-integration-with-relational-data-and-adonet.md)</span><span class="sxs-lookup"><span data-stu-id="7901b-138">[XML Integration with Relational Data and ADO.NET](../../../../docs/standard/data/xml/xml-integration-with-relational-data-and-adonet.md)</span></span>\
<span data-ttu-id="7901b-139">.NET Framework verilerine ilişkisel ve hiyerarşik temsillerini gerçek zamanlı, zaman uyumlu erişimi nasıl sağladığını açıklar <xref:System.Data.DataSet> nesne ve <xref:System.Xml.XmlDataDocument> nesne.</span><span class="sxs-lookup"><span data-stu-id="7901b-139">Describes how the .NET Framework enables real-time, synchronous access to both the relational and hierarchical representations of data through the <xref:System.Data.DataSet> object and the <xref:System.Xml.XmlDataDocument> object.</span></span>

<span data-ttu-id="7901b-140">[XML belgesinde ad alanlarını yönetme](../../../../docs/standard/data/xml/managing-namespaces-in-an-xml-document.md)</span><span class="sxs-lookup"><span data-stu-id="7901b-140">[Managing Namespaces in an XML Document](../../../../docs/standard/data/xml/managing-namespaces-in-an-xml-document.md)</span></span>\
<span data-ttu-id="7901b-141">Açıklayan nasıl <xref:System.Xml.XmlNamespaceManager> sınıfı depolamak ve ad alanı bilgileri korumak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7901b-141">Describes how the <xref:System.Xml.XmlNamespaceManager> class is used to store and maintain namespace information.</span></span>

<span data-ttu-id="7901b-142">[System.Xml sınıflarında tür desteği](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)</span><span class="sxs-lookup"><span data-stu-id="7901b-142">[Type Support in the System.Xml Classes](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)</span></span>\
<span data-ttu-id="7901b-143">Nasıl XML veri türü eşlemesi için CLR türleri, XML veri türleri ve diğer tür destek özellikleri nasıl dönüştürme yapılacağını açıklar <xref:System.Xml> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="7901b-143">Describes how XML data types map to CLR types, how to convert XML data types, and other type support features in the <xref:System.Xml> classes.</span></span>

## <a name="related-sections"></a><span data-ttu-id="7901b-144">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="7901b-144">Related Sections</span></span>

<span data-ttu-id="7901b-145">[ADO.NET](../../../../docs/framework/data/adonet/index.md)</span><span class="sxs-lookup"><span data-stu-id="7901b-145">[ADO.NET](../../../../docs/framework/data/adonet/index.md)</span></span>\
<span data-ttu-id="7901b-146">ADO.NET kullanarak veri erişim hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="7901b-146">Provides information on how to access data using ADO.NET.</span></span>

<span data-ttu-id="7901b-147">[Güvenlik](../../../../docs/standard/security/index.md)</span><span class="sxs-lookup"><span data-stu-id="7901b-147">[Security](../../../../docs/standard/security/index.md)</span></span>\
<span data-ttu-id="7901b-148">.NET Framework güvenlik sistemini genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="7901b-148">Provides an overview of the .NET Framework security system.</span></span>
