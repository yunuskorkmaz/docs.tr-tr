---
title: LINQ to XML sınıflara genel bakış
description: Bu makale, her birinin açıklamalarıyla birlikte LINQ to XML sınıflarının bir listesini sağlar.
ms.date: 07/20/2015
ms.assetid: bf666100-5392-4968-97f4-f6b9d3287d7b
ms.openlocfilehash: 83258425b464d8547def5cce6a3e8da19ef21966
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553350"
---
# <a name="linq-to-xml-classes-overview"></a><span data-ttu-id="0a893-103">LINQ to XML sınıflara genel bakış</span><span class="sxs-lookup"><span data-stu-id="0a893-103">LINQ to XML classes overview</span></span>

<span data-ttu-id="0a893-104">Bu makale, ad alanındaki LINQ to XML sınıflarının bir listesini <xref:System.Xml.Linq> ve her birinin kısa bir açıklamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="0a893-104">This article provides a list of the LINQ to XML classes in the <xref:System.Xml.Linq> namespace, and a short description of each.</span></span>

## <a name="linq-to-xml-classes"></a><span data-ttu-id="0a893-105">LINQ to XML sınıfları</span><span class="sxs-lookup"><span data-stu-id="0a893-105">LINQ to XML classes</span></span>

### <a name="xattribute-class"></a><span data-ttu-id="0a893-106">XAttribute sınıfı</span><span class="sxs-lookup"><span data-stu-id="0a893-106">XAttribute class</span></span>

<span data-ttu-id="0a893-107"><xref:System.Xml.Linq.XAttribute> bir XML özniteliğini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="0a893-107"><xref:System.Xml.Linq.XAttribute> represents an XML attribute.</span></span> <span data-ttu-id="0a893-108">Ayrıntılı bilgi ve örnekler için bkz. [XAttribute sınıfına genel bakış](xattribute-class-overview.md).</span><span class="sxs-lookup"><span data-stu-id="0a893-108">For detailed information and examples, see [XAttribute class overview](xattribute-class-overview.md).</span></span>

### <a name="xcdata-class"></a><span data-ttu-id="0a893-109">XCData sınıfı</span><span class="sxs-lookup"><span data-stu-id="0a893-109">XCData class</span></span>

<span data-ttu-id="0a893-110"><xref:System.Xml.Linq.XCData> CDATA metin düğümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="0a893-110"><xref:System.Xml.Linq.XCData> represents a CDATA text node.</span></span>

### <a name="xcomment-class"></a><span data-ttu-id="0a893-111">XComment sınıfı</span><span class="sxs-lookup"><span data-stu-id="0a893-111">XComment class</span></span>

<span data-ttu-id="0a893-112"><xref:System.Xml.Linq.XComment> bir XML açıklamasını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="0a893-112"><xref:System.Xml.Linq.XComment> represents an XML comment.</span></span>

### <a name="xcontainer-class"></a><span data-ttu-id="0a893-113">XContainer sınıfı</span><span class="sxs-lookup"><span data-stu-id="0a893-113">XContainer class</span></span>

<span data-ttu-id="0a893-114"><xref:System.Xml.Linq.XContainer> , alt düğümlere sahip olan tüm düğümler için soyut bir temel sınıftır.</span><span class="sxs-lookup"><span data-stu-id="0a893-114"><xref:System.Xml.Linq.XContainer> is an abstract base class for all nodes that can have child nodes.</span></span> <span data-ttu-id="0a893-115">Aşağıdaki sınıflar <xref:System.Xml.Linq.XContainer> sınıfından türetilir:</span><span class="sxs-lookup"><span data-stu-id="0a893-115">The following classes derive from the <xref:System.Xml.Linq.XContainer> class:</span></span>

- <xref:System.Xml.Linq.XElement>
- <xref:System.Xml.Linq.XDocument>

### <a name="xdeclaration-class"></a><span data-ttu-id="0a893-116">XDeclaration sınıfı</span><span class="sxs-lookup"><span data-stu-id="0a893-116">XDeclaration class</span></span>

<span data-ttu-id="0a893-117"><xref:System.Xml.Linq.XDeclaration> bir XML bildirimini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="0a893-117"><xref:System.Xml.Linq.XDeclaration> represents an XML declaration.</span></span> <span data-ttu-id="0a893-118">XML bildirimi, XML sürümünü ve bir belgenin kodlamasını bildirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0a893-118">An XML declaration is used to declare the XML version and the encoding of a document.</span></span> <span data-ttu-id="0a893-119">Ayrıca, XML bildirimi XML belgesinin tek başına olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0a893-119">In addition, an XML declaration specifies whether the XML document is stand-alone.</span></span> <span data-ttu-id="0a893-120">Bir belge bağımsız ise, dış bir DTD 'de ya da iç alt kümeden başvurulan bir dış parametre varlığında dış biçimlendirme bildirimleri yoktur.</span><span class="sxs-lookup"><span data-stu-id="0a893-120">If a document is stand-alone, there are no external markup declarations, either in an external DTD, or in an external parameter entity referenced from the internal subset.</span></span>

### <a name="xdocument-class"></a><span data-ttu-id="0a893-121">XDocument sınıfı</span><span class="sxs-lookup"><span data-stu-id="0a893-121">XDocument class</span></span>

<span data-ttu-id="0a893-122"><xref:System.Xml.Linq.XDocument> bir XML belgesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="0a893-122"><xref:System.Xml.Linq.XDocument> represents an XML document.</span></span> <span data-ttu-id="0a893-123">Ayrıntılı bilgi ve örnekler için bkz. [XDocument sınıfına genel bakış](xdocument-class-overview.md).</span><span class="sxs-lookup"><span data-stu-id="0a893-123">For detailed information and examples, see [XDocument class overview](xdocument-class-overview.md).</span></span>

### <a name="xdocumenttype-class"></a><span data-ttu-id="0a893-124">XDocumentType sınıfı</span><span class="sxs-lookup"><span data-stu-id="0a893-124">XDocumentType class</span></span>

<span data-ttu-id="0a893-125"><xref:System.Xml.Linq.XDocumentType> bir XML belge türü tanımını (DTD) temsil eder.</span><span class="sxs-lookup"><span data-stu-id="0a893-125"><xref:System.Xml.Linq.XDocumentType> represents an XML Document Type Definition (DTD).</span></span>

### <a name="xelement-class"></a><span data-ttu-id="0a893-126">XElement sınıfı</span><span class="sxs-lookup"><span data-stu-id="0a893-126">XElement class</span></span>

<span data-ttu-id="0a893-127"><xref:System.Xml.Linq.XElement> bir XML öğesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="0a893-127"><xref:System.Xml.Linq.XElement> represents an XML element.</span></span> <span data-ttu-id="0a893-128">Ayrıntılı bilgi ve örnekler için bkz. [XElement sınıfına genel bakış](xelement-class-overview.md).</span><span class="sxs-lookup"><span data-stu-id="0a893-128">For detailed information and examples, see [XElement class overview](xelement-class-overview.md).</span></span>

### <a name="xname-class"></a><span data-ttu-id="0a893-129">XName sınıfı</span><span class="sxs-lookup"><span data-stu-id="0a893-129">XName class</span></span>

<span data-ttu-id="0a893-130"><xref:System.Xml.Linq.XName> öğelerin ( <xref:System.Xml.Linq.XElement> ) ve özniteliklerin () adlarını temsil eder <xref:System.Xml.Linq.XAttribute> .</span><span class="sxs-lookup"><span data-stu-id="0a893-130"><xref:System.Xml.Linq.XName> represents names of elements (<xref:System.Xml.Linq.XElement>) and attributes (<xref:System.Xml.Linq.XAttribute>).</span></span> <span data-ttu-id="0a893-131">Ayrıntılı bilgi ve örnekler için bkz. [XDocument sınıfına genel bakış](xdocument-class-overview.md).</span><span class="sxs-lookup"><span data-stu-id="0a893-131">For detailed information and examples, see [XDocument class overview](xdocument-class-overview.md).</span></span>

<span data-ttu-id="0a893-132">LINQ to XML, XML adlarını mümkün olduğunca kolay hale getirmek için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="0a893-132">LINQ to XML is designed to make XML names as straightforward as possible.</span></span> <span data-ttu-id="0a893-133">XML adları, karmaşıklığı nedeniyle XML 'de gelişmiş bir makale olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="0a893-133">Due to their complexity, XML names are often considered to be an advanced article in XML.</span></span> <span data-ttu-id="0a893-134">Bu karmaşıklık, geliştiricilerin programlama içinde düzenli olarak kullanıldığı, ancak ad alanı öneklerinden bağımsız olarak, ad alanlarından değildir.</span><span class="sxs-lookup"><span data-stu-id="0a893-134">Arguably, this complexity comes not from namespaces, which developers use regularly in programming, but from namespace prefixes.</span></span> <span data-ttu-id="0a893-135">Ad alanı önekleri, XML girişi yaparken veya XML 'in okunması daha kolay hale getirmek için gereken tuş vuruşlarını azaltmak için faydalı olabilir.</span><span class="sxs-lookup"><span data-stu-id="0a893-135">Namespace prefixes can be useful to reduce the keystrokes required when you input XML, or to make XML easier to read.</span></span> <span data-ttu-id="0a893-136">Ancak, ön ekler genellikle tam XML ad alanını kullanmak için bir kısayoldur ve çoğu durumda gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="0a893-136">However, prefixes are often just a shortcut for using the full XML namespace, and aren't required in most cases.</span></span> <span data-ttu-id="0a893-137">LINQ to XML, tüm ön ekleri karşılık gelen XML ad uzayına çözümleyerek XML adlarını basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="0a893-137">LINQ to XML simplifies XML names by resolving all prefixes to their corresponding XML namespace.</span></span> <span data-ttu-id="0a893-138">Zorunlu olmaları durumunda, ön ekler, yöntemi aracılığıyla kullanılabilir <xref:System.Xml.Linq.XElement.GetPrefixOfNamespace%2A> .</span><span class="sxs-lookup"><span data-stu-id="0a893-138">Prefixes are available, if they're required, through the <xref:System.Xml.Linq.XElement.GetPrefixOfNamespace%2A> method.</span></span>

<span data-ttu-id="0a893-139">gerekirse, ad alanı öneklerini denetlemek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="0a893-139">it's possible, if necessary, to control namespace prefixes.</span></span> <span data-ttu-id="0a893-140">Bazı durumlarda, XSLT veya XAML gibi diğer XML sistemleriyle çalışıyorsanız, ad alanı öneklerini kontrol etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="0a893-140">In some circumstances, if you're working with other XML systems, such as XSLT or XAML, you need to control namespace prefixes.</span></span> <span data-ttu-id="0a893-141">Örneğin, ad alanı öneklerini kullanan ve XSLT stil sayfasına gömülü bir XPath ifadeniz varsa, XML belgenizin XPath ifadesinde kullanılanlarla eşleşen ad alanı önekleri ile serileştirildiğinizden emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0a893-141">For example, if you have an XPath expression that uses namespace prefixes and is embedded in an XSLT stylesheet, you must make sure that your XML document is serialized with namespace prefixes that match those used in the XPath expression.</span></span>

### <a name="xnamespace-class"></a><span data-ttu-id="0a893-142">XNamespace sınıfı</span><span class="sxs-lookup"><span data-stu-id="0a893-142">XNamespace class</span></span>

<span data-ttu-id="0a893-143"><xref:System.Xml.Linq.XNamespace> or için bir ad alanı temsil eder <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XAttribute> .</span><span class="sxs-lookup"><span data-stu-id="0a893-143"><xref:System.Xml.Linq.XNamespace> represents a namespace for an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute>.</span></span> <span data-ttu-id="0a893-144">Ad alanları bir bileşenidir <xref:System.Xml.Linq.XName> .</span><span class="sxs-lookup"><span data-stu-id="0a893-144">Namespaces are a component of an <xref:System.Xml.Linq.XName>.</span></span>

### <a name="xnode-class"></a><span data-ttu-id="0a893-145">XNode sınıfı</span><span class="sxs-lookup"><span data-stu-id="0a893-145">XNode class</span></span>

<span data-ttu-id="0a893-146"><xref:System.Xml.Linq.XNode> , bir XML ağacının düğümlerini temsil eden soyut bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="0a893-146"><xref:System.Xml.Linq.XNode> is an abstract class that represents the nodes of an XML tree.</span></span> <span data-ttu-id="0a893-147">Aşağıdaki sınıflar <xref:System.Xml.Linq.XNode> sınıfından türetilir:</span><span class="sxs-lookup"><span data-stu-id="0a893-147">The following classes derive from the <xref:System.Xml.Linq.XNode> class:</span></span>

- <xref:System.Xml.Linq.XText>
- <xref:System.Xml.Linq.XContainer>
- <xref:System.Xml.Linq.XComment>
- <xref:System.Xml.Linq.XProcessingInstruction>
- <xref:System.Xml.Linq.XDocumentType>

### <a name="xnodedocumentordercomparer-class"></a><span data-ttu-id="0a893-148">XNodeDocumentOrderComparer sınıfı</span><span class="sxs-lookup"><span data-stu-id="0a893-148">XNodeDocumentOrderComparer class</span></span>

<span data-ttu-id="0a893-149"><xref:System.Xml.Linq.XNodeDocumentOrderComparer> düğümlerini Belge sıralarına göre karşılaştırmak için işlevsellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="0a893-149"><xref:System.Xml.Linq.XNodeDocumentOrderComparer> provides functionality to compare nodes for their document order.</span></span>

### <a name="xnodeequalitycomparer-class"></a><span data-ttu-id="0a893-150">XNodeEqualityComparer sınıfı</span><span class="sxs-lookup"><span data-stu-id="0a893-150">XNodeEqualityComparer class</span></span>

<span data-ttu-id="0a893-151"><xref:System.Xml.Linq.XNodeEqualityComparer> değer eşitliği için düğümleri karşılaştırmak için işlevsellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="0a893-151"><xref:System.Xml.Linq.XNodeEqualityComparer> provides functionality to compare nodes for value equality.</span></span>

### <a name="xobject-class"></a><span data-ttu-id="0a893-152">XObject sınıfı</span><span class="sxs-lookup"><span data-stu-id="0a893-152">XObject class</span></span>

<span data-ttu-id="0a893-153"><xref:System.Xml.Linq.XObject> , ve öğesinin soyut taban sınıfıdır <xref:System.Xml.Linq.XNode> <xref:System.Xml.Linq.XAttribute> .</span><span class="sxs-lookup"><span data-stu-id="0a893-153"><xref:System.Xml.Linq.XObject> is an abstract base class of <xref:System.Xml.Linq.XNode> and <xref:System.Xml.Linq.XAttribute>.</span></span> <span data-ttu-id="0a893-154">Ek açıklama ve olay işlevselliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="0a893-154">It provides annotation and event functionality.</span></span>

### <a name="xobjectchange-class"></a><span data-ttu-id="0a893-155">XObjectChange sınıfı</span><span class="sxs-lookup"><span data-stu-id="0a893-155">XObjectChange class</span></span>

<span data-ttu-id="0a893-156"><xref:System.Xml.Linq.XObjectChange> bir olay oluşturulduğunda olay türünü belirtir <xref:System.Xml.Linq.XObject> .</span><span class="sxs-lookup"><span data-stu-id="0a893-156"><xref:System.Xml.Linq.XObjectChange> specifies the event type when an event is raised for an <xref:System.Xml.Linq.XObject>.</span></span>

### <a name="xobjectchangeeventargs-class"></a><span data-ttu-id="0a893-157">XObjectChangeEventArgs sınıfı</span><span class="sxs-lookup"><span data-stu-id="0a893-157">XObjectChangeEventArgs class</span></span>

<span data-ttu-id="0a893-158"><xref:System.Xml.Linq.XObjectChangeEventArgs> ve olayları için veri <xref:System.Xml.Linq.XObject.Changing> sağlar <xref:System.Xml.Linq.XObject.Changed> .</span><span class="sxs-lookup"><span data-stu-id="0a893-158"><xref:System.Xml.Linq.XObjectChangeEventArgs> provides data for the <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed> events.</span></span>

### <a name="xprocessinginstruction-class"></a><span data-ttu-id="0a893-159">XProcessingInstruction sınıfı</span><span class="sxs-lookup"><span data-stu-id="0a893-159">XProcessingInstruction class</span></span>

<span data-ttu-id="0a893-160"><xref:System.Xml.Linq.XProcessingInstruction> bir XML işleme yönergesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="0a893-160"><xref:System.Xml.Linq.XProcessingInstruction> represents an XML processing instruction.</span></span> <span data-ttu-id="0a893-161">Bir işleme yönergesi, XML 'i işleyen bir uygulamayla ilgili bilgiler iletir.</span><span class="sxs-lookup"><span data-stu-id="0a893-161">A processing instruction communicates information to an application that processes the XML.</span></span>

### <a name="xtext-class"></a><span data-ttu-id="0a893-162">XText sınıfı</span><span class="sxs-lookup"><span data-stu-id="0a893-162">XText class</span></span>

<span data-ttu-id="0a893-163"><xref:System.Xml.Linq.XText> bir metin düğümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="0a893-163"><xref:System.Xml.Linq.XText> represents a text node.</span></span> <span data-ttu-id="0a893-164">Çoğu durumda, bu sınıfı kullanmak zorunda kalmazsınız.</span><span class="sxs-lookup"><span data-stu-id="0a893-164">In most cases, you don't have to use this class.</span></span> <span data-ttu-id="0a893-165">Bu sınıf öncelikle karışık içerik için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0a893-165">This class is primarily used for mixed content.</span></span>
