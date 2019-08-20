---
title: LINQ to XML sınıflara genel bakışC#()
ms.date: 07/20/2015
ms.assetid: bf666100-5392-4968-97f4-f6b9d3287d7b
ms.openlocfilehash: 55be666fc0db0becb12ec8b525e7fc443536e1df
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69591891"
---
# <a name="linq-to-xml-classes-overview-c"></a><span data-ttu-id="142cd-102">LINQ to XML sınıflara genel bakışC#()</span><span class="sxs-lookup"><span data-stu-id="142cd-102">LINQ to XML Classes Overview (C#)</span></span>
<span data-ttu-id="142cd-103">Bu konu, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq> ad alanındaki sınıfların bir listesini ve her birinin kısa bir açıklamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="142cd-103">This topic provides a list of the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] classes in the <xref:System.Xml.Linq> namespace, and a short description of each.</span></span>  
  
## <a name="linq-to-xml-classes"></a><span data-ttu-id="142cd-104">LINQ to XML sınıfları</span><span class="sxs-lookup"><span data-stu-id="142cd-104">LINQ to XML Classes</span></span>  
  
### <a name="xattribute-class"></a><span data-ttu-id="142cd-105">XAttribute sınıfı</span><span class="sxs-lookup"><span data-stu-id="142cd-105">XAttribute Class</span></span>  
 <span data-ttu-id="142cd-106"><xref:System.Xml.Linq.XAttribute>bir XML özniteliğini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="142cd-106"><xref:System.Xml.Linq.XAttribute> represents an XML attribute.</span></span> <span data-ttu-id="142cd-107">Ayrıntılı bilgi ve örnekler için bkz. [XAttribute sınıfına genel bakışC#()](./xattribute-class-overview.md).</span><span class="sxs-lookup"><span data-stu-id="142cd-107">For detailed information and examples, see [XAttribute Class Overview (C#)](./xattribute-class-overview.md).</span></span>  
  
### <a name="xcdata-class"></a><span data-ttu-id="142cd-108">XCData sınıfı</span><span class="sxs-lookup"><span data-stu-id="142cd-108">XCData Class</span></span>  
 <span data-ttu-id="142cd-109"><xref:System.Xml.Linq.XCData>CDATA metin düğümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="142cd-109"><xref:System.Xml.Linq.XCData> represents a CDATA text node.</span></span>  
  
### <a name="xcomment-class"></a><span data-ttu-id="142cd-110">XComment sınıfı</span><span class="sxs-lookup"><span data-stu-id="142cd-110">XComment Class</span></span>  
 <span data-ttu-id="142cd-111"><xref:System.Xml.Linq.XComment>bir XML açıklamasını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="142cd-111"><xref:System.Xml.Linq.XComment> represents an XML comment.</span></span>  
  
### <a name="xcontainer-class"></a><span data-ttu-id="142cd-112">XContainer sınıfı</span><span class="sxs-lookup"><span data-stu-id="142cd-112">XContainer Class</span></span>  
 <span data-ttu-id="142cd-113"><xref:System.Xml.Linq.XContainer>, alt düğümlere sahip olan tüm düğümler için soyut bir temel sınıftır.</span><span class="sxs-lookup"><span data-stu-id="142cd-113"><xref:System.Xml.Linq.XContainer> is an abstract base class for all nodes that can have child nodes.</span></span> <span data-ttu-id="142cd-114">Aşağıdaki sınıflar <xref:System.Xml.Linq.XContainer> sınıfından türetilir:</span><span class="sxs-lookup"><span data-stu-id="142cd-114">The following classes derive from the <xref:System.Xml.Linq.XContainer> class:</span></span>  
  
- <xref:System.Xml.Linq.XElement>  
  
- <xref:System.Xml.Linq.XDocument>  
  
### <a name="xdeclaration-class"></a><span data-ttu-id="142cd-115">XDeclaration sınıfı</span><span class="sxs-lookup"><span data-stu-id="142cd-115">XDeclaration Class</span></span>  
 <span data-ttu-id="142cd-116"><xref:System.Xml.Linq.XDeclaration>bir XML bildirimini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="142cd-116"><xref:System.Xml.Linq.XDeclaration> represents an XML declaration.</span></span> <span data-ttu-id="142cd-117">XML bildirimi, XML sürümünü ve bir belgenin kodlamasını bildirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="142cd-117">An XML declaration is used to declare the XML version and the encoding of a document.</span></span> <span data-ttu-id="142cd-118">Ayrıca, XML bildirimi XML belgesinin tek başına olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="142cd-118">In addition, an XML declaration specifies whether the XML document is stand-alone.</span></span> <span data-ttu-id="142cd-119">Bir belge bağımsız ise, dış bir DTD 'de ya da iç alt kümeden başvurulan bir dış parametre varlığında dış biçimlendirme bildirimleri yoktur.</span><span class="sxs-lookup"><span data-stu-id="142cd-119">If a document is stand-alone, there are no external markup declarations, either in an external DTD, or in an external parameter entity referenced from the internal subset.</span></span>  
  
### <a name="xdocument-class"></a><span data-ttu-id="142cd-120">XDocument sınıfı</span><span class="sxs-lookup"><span data-stu-id="142cd-120">XDocument Class</span></span>  
 <span data-ttu-id="142cd-121"><xref:System.Xml.Linq.XDocument>bir XML belgesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="142cd-121"><xref:System.Xml.Linq.XDocument> represents an XML document.</span></span> <span data-ttu-id="142cd-122">Ayrıntılı bilgi ve örnekler için bkz. [XDocument sınıfına genel bakışC#()](./xdocument-class-overview.md).</span><span class="sxs-lookup"><span data-stu-id="142cd-122">For detailed information and examples, see [XDocument Class Overview (C#)](./xdocument-class-overview.md).</span></span>  
  
### <a name="xdocumenttype-class"></a><span data-ttu-id="142cd-123">XDocumentType sınıfı</span><span class="sxs-lookup"><span data-stu-id="142cd-123">XDocumentType Class</span></span>  
 <span data-ttu-id="142cd-124"><xref:System.Xml.Linq.XDocumentType>bir XML belge türü tanımını (DTD) temsil eder.</span><span class="sxs-lookup"><span data-stu-id="142cd-124"><xref:System.Xml.Linq.XDocumentType> represents an XML Document Type Definition (DTD).</span></span>  
  
### <a name="xelement-class"></a><span data-ttu-id="142cd-125">XElement sınıfı</span><span class="sxs-lookup"><span data-stu-id="142cd-125">XElement Class</span></span>  
 <span data-ttu-id="142cd-126"><xref:System.Xml.Linq.XElement>bir XML öğesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="142cd-126"><xref:System.Xml.Linq.XElement> represents an XML element.</span></span> <span data-ttu-id="142cd-127">Ayrıntılı bilgi ve örnekler için bkz. [XElement sınıfına genel bakışC#()](./xelement-class-overview.md).</span><span class="sxs-lookup"><span data-stu-id="142cd-127">For detailed information and examples, see [XElement Class Overview (C#)](./xelement-class-overview.md).</span></span>  
  
### <a name="xname-class"></a><span data-ttu-id="142cd-128">XName sınıfı</span><span class="sxs-lookup"><span data-stu-id="142cd-128">XName Class</span></span>  
 <span data-ttu-id="142cd-129"><xref:System.Xml.Linq.XName>öğelerin (<xref:System.Xml.Linq.XElement>) ve özniteliklerin (<xref:System.Xml.Linq.XAttribute>) adlarını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="142cd-129"><xref:System.Xml.Linq.XName> represents names of elements (<xref:System.Xml.Linq.XElement>) and attributes (<xref:System.Xml.Linq.XAttribute>).</span></span> <span data-ttu-id="142cd-130">Ayrıntılı bilgi ve örnekler için bkz. [XDocument sınıfına genel bakışC#()](./xdocument-class-overview.md).</span><span class="sxs-lookup"><span data-stu-id="142cd-130">For detailed information and examples, see [XDocument Class Overview (C#)](./xdocument-class-overview.md).</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="142cd-131">XML adlarını mümkün olduğunca kolay hale getirmek için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="142cd-131">is designed to make XML names as straightforward as possible.</span></span> <span data-ttu-id="142cd-132">Karmaşıklığı nedeniyle XML adları genellikle XML 'de gelişmiş bir konu olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="142cd-132">Due to their complexity, XML names are often considered to be an advanced topic in XML.</span></span> <span data-ttu-id="142cd-133">Bu karmaşıklık, geliştiricilerin programlama içinde düzenli olarak kullanıldığı, ancak ad alanı öneklerinden bağımsız olarak, ad alanlarından değildir.</span><span class="sxs-lookup"><span data-stu-id="142cd-133">Arguably, this complexity comes not from namespaces, which developers use regularly in programming, but from namespace prefixes.</span></span> <span data-ttu-id="142cd-134">Ad alanı önekleri, XML girişi yaparken veya XML 'in okunması daha kolay hale getirmek için gereken tuş vuruşlarını azaltmak için faydalı olabilir.</span><span class="sxs-lookup"><span data-stu-id="142cd-134">Namespace prefixes can be useful to reduce the keystrokes required when you input XML, or to make XML easier to read.</span></span> <span data-ttu-id="142cd-135">Ancak, ön ekler genellikle tam XML ad alanını kullanmak için bir kısayoldur ve çoğu durumda gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="142cd-135">However, prefixes are often just a shortcut for using the full XML namespace, and are not required in most cases.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="142cd-136">Tüm ön ekleri karşılık gelen XML ad uzayına çözümleyerek XML adlarını basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="142cd-136">simplifies XML names by resolving all prefixes to their corresponding XML namespace.</span></span> <span data-ttu-id="142cd-137">Zorunlu olmaları durumunda, ön ekler, <xref:System.Xml.Linq.XElement.GetPrefixOfNamespace%2A> yöntemi aracılığıyla kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="142cd-137">Prefixes are available, if they are required, through the <xref:System.Xml.Linq.XElement.GetPrefixOfNamespace%2A> method.</span></span>  
  
 <span data-ttu-id="142cd-138">Gerekirse, ad alanı öneklerini denetlemek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="142cd-138">It is possible, if necessary, to control namespace prefixes.</span></span> <span data-ttu-id="142cd-139">Bazı durumlarda, XSLT veya XAML gibi diğer XML sistemleriyle çalışıyorsanız, ad alanı öneklerini kontrol etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="142cd-139">In some circumstances, if you are working with other XML systems, such as XSLT or XAML, you need to control namespace prefixes.</span></span> <span data-ttu-id="142cd-140">Örneğin, ad alanı öneklerini kullanan ve XSLT stil sayfasına gömülü bir XPath ifadeniz varsa, XML belgenizin XPath ifadesinde kullanılanlarla eşleşen ad alanı önekleri ile serileştirildiğinizden emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="142cd-140">For example, if you have an XPath expression that uses namespace prefixes and is embedded in an XSLT stylesheet, you must make sure that your XML document is serialized with namespace prefixes that match those used in the XPath expression.</span></span>  
  
### <a name="xnamespace-class"></a><span data-ttu-id="142cd-141">XNamespace sınıfı</span><span class="sxs-lookup"><span data-stu-id="142cd-141">XNamespace Class</span></span>  
 <span data-ttu-id="142cd-142"><xref:System.Xml.Linq.XNamespace><xref:System.Xml.Linq.XElement> or<xref:System.Xml.Linq.XAttribute>için bir ad alanı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="142cd-142"><xref:System.Xml.Linq.XNamespace> represents a namespace for an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute>.</span></span> <span data-ttu-id="142cd-143">Ad alanları bir <xref:System.Xml.Linq.XName>bileşenidir.</span><span class="sxs-lookup"><span data-stu-id="142cd-143">Namespaces are a component of an <xref:System.Xml.Linq.XName>.</span></span>  
  
### <a name="xnode-class"></a><span data-ttu-id="142cd-144">XNode sınıfı</span><span class="sxs-lookup"><span data-stu-id="142cd-144">XNode Class</span></span>  
 <span data-ttu-id="142cd-145"><xref:System.Xml.Linq.XNode>, bir XML ağacının düğümlerini temsil eden soyut bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="142cd-145"><xref:System.Xml.Linq.XNode> is an abstract class that represents the nodes of an XML tree.</span></span> <span data-ttu-id="142cd-146">Aşağıdaki sınıflar <xref:System.Xml.Linq.XNode> sınıfından türetilir:</span><span class="sxs-lookup"><span data-stu-id="142cd-146">The following classes derive from the <xref:System.Xml.Linq.XNode> class:</span></span>  
  
- <xref:System.Xml.Linq.XText>  
  
- <xref:System.Xml.Linq.XContainer>  
  
- <xref:System.Xml.Linq.XComment>  
  
- <xref:System.Xml.Linq.XProcessingInstruction>  
  
- <xref:System.Xml.Linq.XDocumentType>  
  
### <a name="xnodedocumentordercomparer-class"></a><span data-ttu-id="142cd-147">XNodeDocumentOrderComparer sınıfı</span><span class="sxs-lookup"><span data-stu-id="142cd-147">XNodeDocumentOrderComparer Class</span></span>  
 <span data-ttu-id="142cd-148"><xref:System.Xml.Linq.XNodeDocumentOrderComparer>düğümlerini Belge sıralarına göre karşılaştırmak için işlevsellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="142cd-148"><xref:System.Xml.Linq.XNodeDocumentOrderComparer> provides functionality to compare nodes for their document order.</span></span>  
  
### <a name="xnodeequalitycomparer-class"></a><span data-ttu-id="142cd-149">XNodeEqualityComparer sınıfı</span><span class="sxs-lookup"><span data-stu-id="142cd-149">XNodeEqualityComparer Class</span></span>  
 <span data-ttu-id="142cd-150"><xref:System.Xml.Linq.XNodeEqualityComparer>değer eşitliği için düğümleri karşılaştırmak için işlevsellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="142cd-150"><xref:System.Xml.Linq.XNodeEqualityComparer> provides functionality to compare nodes for value equality.</span></span>  
  
### <a name="xobject-class"></a><span data-ttu-id="142cd-151">XObject sınıfı</span><span class="sxs-lookup"><span data-stu-id="142cd-151">XObject Class</span></span>  
 <span data-ttu-id="142cd-152"><xref:System.Xml.Linq.XObject>, ve <xref:System.Xml.Linq.XNode> <xref:System.Xml.Linq.XAttribute>öğesinin soyut taban sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="142cd-152"><xref:System.Xml.Linq.XObject> is an abstract base class of <xref:System.Xml.Linq.XNode> and <xref:System.Xml.Linq.XAttribute>.</span></span> <span data-ttu-id="142cd-153">Ek açıklama ve olay işlevselliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="142cd-153">It provides annotation and event functionality.</span></span>  
  
### <a name="xobjectchange-class"></a><span data-ttu-id="142cd-154">XObjectChange sınıfı</span><span class="sxs-lookup"><span data-stu-id="142cd-154">XObjectChange Class</span></span>  
 <span data-ttu-id="142cd-155"><xref:System.Xml.Linq.XObjectChange>bir <xref:System.Xml.Linq.XObject>olay oluşturulduğunda olay türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="142cd-155"><xref:System.Xml.Linq.XObjectChange> specifies the event type when an event is raised for an <xref:System.Xml.Linq.XObject>.</span></span>  
  
### <a name="xobjectchangeeventargs-class"></a><span data-ttu-id="142cd-156">XObjectChangeEventArgs sınıfı</span><span class="sxs-lookup"><span data-stu-id="142cd-156">XObjectChangeEventArgs Class</span></span>  
 <span data-ttu-id="142cd-157"><xref:System.Xml.Linq.XObjectChangeEventArgs><xref:System.Xml.Linq.XObject.Changing> ve<xref:System.Xml.Linq.XObject.Changed> olayları için veri sağlar.</span><span class="sxs-lookup"><span data-stu-id="142cd-157"><xref:System.Xml.Linq.XObjectChangeEventArgs> provides data for the <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed> events.</span></span>  
  
### <a name="xprocessinginstruction-class"></a><span data-ttu-id="142cd-158">XProcessingInstruction sınıfı</span><span class="sxs-lookup"><span data-stu-id="142cd-158">XProcessingInstruction Class</span></span>  
 <span data-ttu-id="142cd-159"><xref:System.Xml.Linq.XProcessingInstruction>bir XML işleme yönergesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="142cd-159"><xref:System.Xml.Linq.XProcessingInstruction> represents an XML processing instruction.</span></span> <span data-ttu-id="142cd-160">Bir işleme yönergesi, XML 'i işleyen bir uygulamayla ilgili bilgiler iletir.</span><span class="sxs-lookup"><span data-stu-id="142cd-160">A processing instruction communicates information to an application that processes the XML.</span></span>  
  
### <a name="xtext-class"></a><span data-ttu-id="142cd-161">XText sınıfı</span><span class="sxs-lookup"><span data-stu-id="142cd-161">XText Class</span></span>  
 <span data-ttu-id="142cd-162"><xref:System.Xml.Linq.XText>bir metin düğümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="142cd-162"><xref:System.Xml.Linq.XText> represents a text node.</span></span> <span data-ttu-id="142cd-163">Çoğu durumda, bu sınıfı kullanmak zorunda değilsiniz.</span><span class="sxs-lookup"><span data-stu-id="142cd-163">In most cases, you do not have to use this class.</span></span> <span data-ttu-id="142cd-164">Bu sınıf öncelikle karışık içerik için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="142cd-164">This class is primarily used for mixed content.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="142cd-165">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="142cd-165">See also</span></span>

- [<span data-ttu-id="142cd-166">LINQ to XML programlamaya genel bakışC#()</span><span class="sxs-lookup"><span data-stu-id="142cd-166">LINQ to XML Programming Overview (C#)</span></span>](./linq-to-xml-overview.md)
