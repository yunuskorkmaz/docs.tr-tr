---
title: XML Belgeleri ve Verileri
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e695047f-3c0f-4045-8708-5baea91cc380
caps.latest.revision: 9
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 0da27afc5509af6db510b5e622ffde461ae2e0a1
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
---
# <a name="xml-documents-and-data"></a><span data-ttu-id="f0930-102">XML Belgeleri ve Verileri</span><span class="sxs-lookup"><span data-stu-id="f0930-102">XML Documents and Data</span></span>
<span data-ttu-id="f0930-103">.NET Framework XML algılayan uygulamaları kolayca oluşturmanıza olanak tanıyan sınıflar kapsamlı ve tümleşik bir dizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="f0930-103">The .NET Framework provides a comprehensive and integrated set of classes that enable you to build XML-aware apps easily.</span></span> <span data-ttu-id="f0930-104">Aşağıdaki ad alanındaki sınıflar, ayrıştırma ve XML, bellek, veri doğrulama ve XSLT dönüşümü XML verileri düzenleme yazmayı destekler.</span><span class="sxs-lookup"><span data-stu-id="f0930-104">The classes in the following namespaces support parsing and writing XML, editing XML data in memory, data validation, and XSLT transformation.</span></span>  
  
-   <xref:System.Xml>  
  
-   <xref:System.Xml.XPath>  
  
-   <xref:System.Xml.Xsl>  
  
-   <xref:System.Xml.Schema>  
  
-   <xref:System.Xml.Linq>  
  
 <span data-ttu-id="f0930-105">Tam listesi için bkz: [System.Xml ad alanları](https://msdn.microsoft.com/library/gg145036.aspx) Web sayfası.</span><span class="sxs-lookup"><span data-stu-id="f0930-105">For a full list, see the [System.Xml Namespaces](https://msdn.microsoft.com/library/gg145036.aspx) webpage.</span></span>  
  
 <span data-ttu-id="f0930-106">Bu ad alanındaki sınıflar World Wide Web Konsorsiyumu (W3C) önerileri destekler.</span><span class="sxs-lookup"><span data-stu-id="f0930-106">The classes in these namespaces support World Wide Web Consortium (W3C) recommendations.</span></span> <span data-ttu-id="f0930-107">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="f0930-107">For example:</span></span>  
  
-   <span data-ttu-id="f0930-108"><xref:System.Xml.XmlDocument?displayProperty=nameWithType> Uygulayan sınıf [W3C belge nesne modeli (DOM) Düzey 1 çekirdek](https://www.w3.org/TR/REC-DOM-Level-1/) ve [DOM Düzey 2 Çekirdek](https://www.w3.org/TR/DOM-Level-2-Core/) öneriler.</span><span class="sxs-lookup"><span data-stu-id="f0930-108">The <xref:System.Xml.XmlDocument?displayProperty=nameWithType> class implements the [W3C Document Object Model (DOM) Level 1 Core](https://www.w3.org/TR/REC-DOM-Level-1/) and [DOM Level 2 Core](https://www.w3.org/TR/DOM-Level-2-Core/) recommendations.</span></span>  
  
-   <span data-ttu-id="f0930-109"><xref:System.Xml.XmlReader?displayProperty=nameWithType> Ve <xref:System.Xml.XmlWriter?displayProperty=nameWithType> sınıfları Destek [W3C XML 1.0](https://www.w3.org/TR/2006/REC-xml-20060816/) ve [XML ad alanları](https://www.w3.org/TR/REC-xml-names/) öneriler.</span><span class="sxs-lookup"><span data-stu-id="f0930-109">The <xref:System.Xml.XmlReader?displayProperty=nameWithType> and <xref:System.Xml.XmlWriter?displayProperty=nameWithType> classes support the [W3C XML 1.0](https://www.w3.org/TR/2006/REC-xml-20060816/) and the [Namespaces in XML](https://www.w3.org/TR/REC-xml-names/) recommendations.</span></span>  
  
-   <span data-ttu-id="f0930-110">Şemalarda <xref:System.Xml.Schema.XmlSchemaSet?displayProperty=nameWithType> sınıf destek [W3C XML Şeması Kısım 1: yapıları](https://www.w3.org/TR/xmlschema-1/) ve [XML Şeması Kısım 2: veri türleri](https://www.w3.org/TR/xmlschema-2/) öneriler.</span><span class="sxs-lookup"><span data-stu-id="f0930-110">Schemas in the <xref:System.Xml.Schema.XmlSchemaSet?displayProperty=nameWithType> class support the [W3C XML Schema Part 1: Structures](https://www.w3.org/TR/xmlschema-1/) and [XML Schema Part 2: Datatypes](https://www.w3.org/TR/xmlschema-2/) recommendations.</span></span>  
  
-   <span data-ttu-id="f0930-111">Sınıfları <xref:System.Xml.Xsl?displayProperty=nameWithType> uygun ad alanı destek XSLT dönüştürmeleri [W3C XSLT 1.0](http://www.w3.org/TR/xslt) öneri.</span><span class="sxs-lookup"><span data-stu-id="f0930-111">Classes in the <xref:System.Xml.Xsl?displayProperty=nameWithType> namespace support XSLT transformations that conform to the [W3C XSLT 1.0](http://www.w3.org/TR/xslt) recommendation.</span></span>  
  
 <span data-ttu-id="f0930-112">.NET Framework XML sınıflarda şu avantajları sağlar:</span><span class="sxs-lookup"><span data-stu-id="f0930-112">The XML classes in the .NET Framework provide these benefits:</span></span>  
  
-   <span data-ttu-id="f0930-113">**Verimliliği.**</span><span class="sxs-lookup"><span data-stu-id="f0930-113">**Productivity.**</span></span> <span data-ttu-id="f0930-114">[LINQ-XML](https://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13) XML programla kolaylaştırır ve SQL için benzer bir sorgu deneyimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="f0930-114">[LINQ to XML](https://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13) makes it easier to program with XML and provides a query experience that is similar to SQL.</span></span>  
  
-   <span data-ttu-id="f0930-115">**Genişletilebilirlik.**</span><span class="sxs-lookup"><span data-stu-id="f0930-115">**Extensibility.**</span></span> <span data-ttu-id="f0930-116">.NET Framework XML sınıflarının soyut taban sınıfları ve sanal yöntemler kullanılarak genişletilebilir.</span><span class="sxs-lookup"><span data-stu-id="f0930-116">The XML classes in the .NET Framework are extensible through the use of abstract base classes and virtual methods.</span></span> <span data-ttu-id="f0930-117">Örneğin, türetilen bir sınıftan oluşturabilirsiniz <xref:System.Xml.XmlUrlResolver> yerel disk önbelleği akışa depolayan sınıf.</span><span class="sxs-lookup"><span data-stu-id="f0930-117">For example, you can create a derived class of the <xref:System.Xml.XmlUrlResolver> class that stores the cache stream to the local disk.</span></span>  
  
-   <span data-ttu-id="f0930-118">**Eklenebilir mimari.**</span><span class="sxs-lookup"><span data-stu-id="f0930-118">**Pluggable architecture.**</span></span> <span data-ttu-id="f0930-119">.NET Framework bileşenlerini birbirine kullanabilir ve bileşenler arasında veri akışı bir mimari sağlar.</span><span class="sxs-lookup"><span data-stu-id="f0930-119">The .NET Framework provides an architecture in which components can utilize one another, and data can be streamed between components.</span></span> <span data-ttu-id="f0930-120">Örneğin, bir veri deposu gibi bir <xref:System.Xml.XPath.XPathDocument> veya <xref:System.Xml.XmlDocument> nesne, ile dönüştürülebilir <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı ve çıkış sonra olabilir ya da başka bir depoya akışı veya bir web hizmetinden bir akış olarak döndürdü.</span><span class="sxs-lookup"><span data-stu-id="f0930-120">For example, a data store, such as an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object, can be transformed with the <xref:System.Xml.Xsl.XslCompiledTransform> class, and the output can then be streamed either into another store or returned as a stream from a web service.</span></span>  
  
-   <span data-ttu-id="f0930-121">**Performans.**</span><span class="sxs-lookup"><span data-stu-id="f0930-121">**Performance.**</span></span> <span data-ttu-id="f0930-122">Daha iyi uygulama performans için .NET Framework'teki XML sınıfların bazıları aşağıdaki özelliklere sahip bir akış tabanlı modeli destekler:</span><span class="sxs-lookup"><span data-stu-id="f0930-122">For better app performance, some of the XML classes in the .NET Framework support a streaming-based model with the following characteristics:</span></span>  
  
    -   <span data-ttu-id="f0930-123">Yalnızca iletme, çekme modeli ayrıştırmak için en az önbelleğe alma (<xref:System.Xml.XmlReader>).</span><span class="sxs-lookup"><span data-stu-id="f0930-123">Minimal caching for forward-only, pull-model parsing (<xref:System.Xml.XmlReader>).</span></span>  
  
    -   <span data-ttu-id="f0930-124">Yalnızca iletme doğrulama (<xref:System.Xml.XmlReader>).</span><span class="sxs-lookup"><span data-stu-id="f0930-124">Forward-only validation (<xref:System.Xml.XmlReader>).</span></span>  
  
    -   <span data-ttu-id="f0930-125">Belge için rasgele erişim sağlarken düğümü oluşturmayı, tek bir sanal düğümü en aza indirir imleç stili Gezinti (<xref:System.Xml.XPath.XPathNavigator>).</span><span class="sxs-lookup"><span data-stu-id="f0930-125">Cursor style navigation that minimizes node creation to a single virtual node while providing random access to the document (<xref:System.Xml.XPath.XPathNavigator>).</span></span>  
  
     <span data-ttu-id="f0930-126">Daha iyi performans için XSLT işleme gerektiğinde kullanabileceğiniz <xref:System.Xml.XPath.XPathDocument> verimli bir şekilde çalışmak için tasarlanmış XPath sorguları için en iyi duruma getirilmiş, salt okunur bir depo sınıfı <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="f0930-126">For better performance whenever XSLT processing is required, you can use the <xref:System.Xml.XPath.XPathDocument> class, which is an optimized, read-only store for XPath queries designed to work efficiently with the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
-   <span data-ttu-id="f0930-127">**ADO.NET ile tümleştirme.**</span><span class="sxs-lookup"><span data-stu-id="f0930-127">**Integration with ADO.NET.**</span></span> <span data-ttu-id="f0930-128">XML sınıfları ve [ADO.NET](../../../../docs/framework/data/adonet/index.md) ilişkisel veri ve XML araya getirmek için sıkı bir şekilde tümleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f0930-128">The XML classes and [ADO.NET](../../../../docs/framework/data/adonet/index.md) are tightly integrated to bring together relational data and XML.</span></span> <span data-ttu-id="f0930-129"><xref:System.Data.DataSet> Sınıfı, bir bellek içi önbellek bir veritabanından alınan veri.</span><span class="sxs-lookup"><span data-stu-id="f0930-129">The <xref:System.Data.DataSet> class is an in-memory cache of data retrieved from a database.</span></span> <span data-ttu-id="f0930-130"><xref:System.Data.DataSet> Sınıfına sahip okuma ve XML kullanarak yazma yeteneği <xref:System.Xml.XmlReader> ve <xref:System.Xml.XmlWriter> sınıfları, iç ilişkisel şema yapısını XML şemaları (XSD) kalır ve bir XML belgesi şema yapısını anlamak için.</span><span class="sxs-lookup"><span data-stu-id="f0930-130">The <xref:System.Data.DataSet> class has the ability to read and write XML by using the <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter> classes, to persist its internal relational schema structure as XML schemas (XSD), and to infer the schema structure of an XML document.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f0930-131">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="f0930-131">In This Section</span></span>  
 [<span data-ttu-id="f0930-132">XML İşleme Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="f0930-132">XML Processing Options</span></span>](../../../../docs/standard/data/xml/xml-processing-options.md)  
 <span data-ttu-id="f0930-133">XML verilerini işlemek için seçenekleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="f0930-133">Discusses options for processing XML data.</span></span>  
  
 [<span data-ttu-id="f0930-134">XML Verilerini Bellek İçinde İşleme</span><span class="sxs-lookup"><span data-stu-id="f0930-134">Processing XML Data In-Memory</span></span>](../../../../docs/standard/data/xml/processing-xml-data-in-memory.md)  
 <span data-ttu-id="f0930-135">XML veri bellek içi işleme için üç modeli açıklanır.</span><span class="sxs-lookup"><span data-stu-id="f0930-135">Discusses the three models for processing XML data in-memory.</span></span> <span data-ttu-id="f0930-136">[LINQ-XML](https://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13), <xref:System.Xml.XmlDocument> (W3C belge nesne modeli üzerinde tabanlı), sınıf ve <xref:System.Xml.XPath.XPathDocument> sınıfı (XPath veri modeline bağlı).</span><span class="sxs-lookup"><span data-stu-id="f0930-136">[LINQ to XML](https://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13), the <xref:System.Xml.XmlDocument> class (based on the W3C Document Object Model), and the <xref:System.Xml.XPath.XPathDocument> class (based on the XPath data model).</span></span>  
  
 [<span data-ttu-id="f0930-137">XSLT Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="f0930-137">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)  
 <span data-ttu-id="f0930-138">XSLT işlemci kullanımını açıklar.</span><span class="sxs-lookup"><span data-stu-id="f0930-138">Describes how to use the XSLT processor.</span></span>  
  
 [<span data-ttu-id="f0930-139">XML Şema Nesne Modeli (SOM)</span><span class="sxs-lookup"><span data-stu-id="f0930-139">XML Schema Object Model (SOM)</span></span>](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)  
 <span data-ttu-id="f0930-140">Derleme ve sağlayarak XML şemaları (XSD) işlemek için kullanılan sınıflar açıklanmaktadır bir <xref:System.Xml.Schema.XmlSchema> yüklemek ve bir şema düzenlemek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="f0930-140">Describes the classes used for building and manipulating XML Schemas (XSD) by providing an <xref:System.Xml.Schema.XmlSchema> class to load and edit a schema.</span></span>  
  
 [<span data-ttu-id="f0930-141">İlişkisel Veriler ve ADO.NET ile XML Tümleştirmesi</span><span class="sxs-lookup"><span data-stu-id="f0930-141">XML Integration with Relational Data and ADO.NET</span></span>](../../../../docs/standard/data/xml/xml-integration-with-relational-data-and-adonet.md)  
 <span data-ttu-id="f0930-142">.NET Framework verilerine ilişkisel ve hiyerarşik gösterimlerini gerçek zamanlı, zaman uyumlu erişim nasıl sağladığını açıklar <xref:System.Data.DataSet> nesne ve <xref:System.Xml.XmlDataDocument> nesne.</span><span class="sxs-lookup"><span data-stu-id="f0930-142">Describes how the .NET Framework enables real-time, synchronous access to both the relational and hierarchical representations of data through the <xref:System.Data.DataSet> object and the <xref:System.Xml.XmlDataDocument> object.</span></span>  
  
 [<span data-ttu-id="f0930-143">XML Belgesinde Ad Alanlarını Yönetme</span><span class="sxs-lookup"><span data-stu-id="f0930-143">Managing Namespaces in an XML Document</span></span>](../../../../docs/standard/data/xml/managing-namespaces-in-an-xml-document.md)  
 <span data-ttu-id="f0930-144">Açıklar nasıl <xref:System.Xml.XmlNamespaceManager> sınıfı depolamak ve ad alanı bilgilerini korumak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f0930-144">Describes how the <xref:System.Xml.XmlNamespaceManager> class is used to store and maintain namespace information.</span></span>  
  
 [<span data-ttu-id="f0930-145">System.Xml Sınıflarında Tür Desteği</span><span class="sxs-lookup"><span data-stu-id="f0930-145">Type Support in the System.Xml Classes</span></span>](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)  
 <span data-ttu-id="f0930-146">Nasıl XML veri türü eşlemesi için CLR türleri, XML veri türleri ve diğer tür destek özellikleri dönüştürme açıklar <xref:System.Xml> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="f0930-146">Describes how XML data types map to CLR types, how to convert XML data types, and other type support features in the <xref:System.Xml> classes.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="f0930-147">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="f0930-147">Related Sections</span></span>  
 [<span data-ttu-id="f0930-148">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f0930-148">ADO.NET</span></span>](../../../../docs/framework/data/adonet/index.md)  
 <span data-ttu-id="f0930-149">ADO.NET kullanarak veri erişim hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="f0930-149">Provides information on how to access data using ADO.NET.</span></span>  
  
 [<span data-ttu-id="f0930-150">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="f0930-150">Security</span></span>](../../../../docs/standard/security/index.md)  
 <span data-ttu-id="f0930-151">.NET Framework güvenlik sistemi genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="f0930-151">Provides an overview of the .NET Framework security system.</span></span>  
  