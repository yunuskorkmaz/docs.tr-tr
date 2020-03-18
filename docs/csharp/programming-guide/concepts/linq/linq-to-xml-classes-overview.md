---
title: LINQ - XML Sınıflarına Genel Bakış (C#)
ms.date: 07/20/2015
ms.assetid: bf666100-5392-4968-97f4-f6b9d3287d7b
ms.openlocfilehash: 55be666fc0db0becb12ec8b525e7fc443536e1df
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69591891"
---
# <a name="linq-to-xml-classes-overview-c"></a><span data-ttu-id="00fe4-102">LINQ - XML Sınıflarına Genel Bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="00fe4-102">LINQ to XML Classes Overview (C#)</span></span>
<span data-ttu-id="00fe4-103">Bu konu, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq> ad alanındaki sınıfların bir listesini ve her birinin kısa bir açıklamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="00fe4-103">This topic provides a list of the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] classes in the <xref:System.Xml.Linq> namespace, and a short description of each.</span></span>  
  
## <a name="linq-to-xml-classes"></a><span data-ttu-id="00fe4-104">LINQ - XML Sınıfları</span><span class="sxs-lookup"><span data-stu-id="00fe4-104">LINQ to XML Classes</span></span>  
  
### <a name="xattribute-class"></a><span data-ttu-id="00fe4-105">XAttribute Sınıfı</span><span class="sxs-lookup"><span data-stu-id="00fe4-105">XAttribute Class</span></span>  
 <span data-ttu-id="00fe4-106"><xref:System.Xml.Linq.XAttribute>bir XML özniteliğini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="00fe4-106"><xref:System.Xml.Linq.XAttribute> represents an XML attribute.</span></span> <span data-ttu-id="00fe4-107">Ayrıntılı bilgi ve örnekler için Bkz. [XAttribute Sınıf Genel Bakış (C#)](./xattribute-class-overview.md).</span><span class="sxs-lookup"><span data-stu-id="00fe4-107">For detailed information and examples, see [XAttribute Class Overview (C#)](./xattribute-class-overview.md).</span></span>  
  
### <a name="xcdata-class"></a><span data-ttu-id="00fe4-108">XCData Sınıfı</span><span class="sxs-lookup"><span data-stu-id="00fe4-108">XCData Class</span></span>  
 <span data-ttu-id="00fe4-109"><xref:System.Xml.Linq.XCData>cdata metin düğümlerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="00fe4-109"><xref:System.Xml.Linq.XCData> represents a CDATA text node.</span></span>  
  
### <a name="xcomment-class"></a><span data-ttu-id="00fe4-110">XComment Sınıfı</span><span class="sxs-lookup"><span data-stu-id="00fe4-110">XComment Class</span></span>  
 <span data-ttu-id="00fe4-111"><xref:System.Xml.Linq.XComment>bir XML yorumunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="00fe4-111"><xref:System.Xml.Linq.XComment> represents an XML comment.</span></span>  
  
### <a name="xcontainer-class"></a><span data-ttu-id="00fe4-112">XContainer Sınıfı</span><span class="sxs-lookup"><span data-stu-id="00fe4-112">XContainer Class</span></span>  
 <span data-ttu-id="00fe4-113"><xref:System.Xml.Linq.XContainer>alt düğümleri olabilir tüm düğümler için soyut bir taban sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="00fe4-113"><xref:System.Xml.Linq.XContainer> is an abstract base class for all nodes that can have child nodes.</span></span> <span data-ttu-id="00fe4-114">Aşağıdaki sınıflar sınıftan <xref:System.Xml.Linq.XContainer> türetilmiştir:</span><span class="sxs-lookup"><span data-stu-id="00fe4-114">The following classes derive from the <xref:System.Xml.Linq.XContainer> class:</span></span>  
  
- <xref:System.Xml.Linq.XElement>  
  
- <xref:System.Xml.Linq.XDocument>  
  
### <a name="xdeclaration-class"></a><span data-ttu-id="00fe4-115">XDeclaration Sınıfı</span><span class="sxs-lookup"><span data-stu-id="00fe4-115">XDeclaration Class</span></span>  
 <span data-ttu-id="00fe4-116"><xref:System.Xml.Linq.XDeclaration>bir XML bildirimini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="00fe4-116"><xref:System.Xml.Linq.XDeclaration> represents an XML declaration.</span></span> <span data-ttu-id="00fe4-117">XML sürümünü ve belgenin kodlayıcısını bildirmek için bir XML bildirimi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="00fe4-117">An XML declaration is used to declare the XML version and the encoding of a document.</span></span> <span data-ttu-id="00fe4-118">Ayrıca, Bir XML bildirimi XML belgesinin tek başına olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="00fe4-118">In addition, an XML declaration specifies whether the XML document is stand-alone.</span></span> <span data-ttu-id="00fe4-119">Bir belge tek başınaysa, harici bir DTD'de veya iç alt kümeden başvurulan harici bir parametre varlığında dış biçimlendirme bildirimleri yoktur.</span><span class="sxs-lookup"><span data-stu-id="00fe4-119">If a document is stand-alone, there are no external markup declarations, either in an external DTD, or in an external parameter entity referenced from the internal subset.</span></span>  
  
### <a name="xdocument-class"></a><span data-ttu-id="00fe4-120">XDocument Sınıfı</span><span class="sxs-lookup"><span data-stu-id="00fe4-120">XDocument Class</span></span>  
 <span data-ttu-id="00fe4-121"><xref:System.Xml.Linq.XDocument>bir XML belgesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="00fe4-121"><xref:System.Xml.Linq.XDocument> represents an XML document.</span></span> <span data-ttu-id="00fe4-122">Ayrıntılı bilgi ve örnekler için Bkz. [XDocument Sınıf Genel Bakış (C#)](./xdocument-class-overview.md).</span><span class="sxs-lookup"><span data-stu-id="00fe4-122">For detailed information and examples, see [XDocument Class Overview (C#)](./xdocument-class-overview.md).</span></span>  
  
### <a name="xdocumenttype-class"></a><span data-ttu-id="00fe4-123">XDocumentType Sınıfı</span><span class="sxs-lookup"><span data-stu-id="00fe4-123">XDocumentType Class</span></span>  
 <span data-ttu-id="00fe4-124"><xref:System.Xml.Linq.XDocumentType>XML Belge Türü Tanımı'nı (DTD) temsil eder.</span><span class="sxs-lookup"><span data-stu-id="00fe4-124"><xref:System.Xml.Linq.XDocumentType> represents an XML Document Type Definition (DTD).</span></span>  
  
### <a name="xelement-class"></a><span data-ttu-id="00fe4-125">XElement Sınıfı</span><span class="sxs-lookup"><span data-stu-id="00fe4-125">XElement Class</span></span>  
 <span data-ttu-id="00fe4-126"><xref:System.Xml.Linq.XElement>bir XML öğesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="00fe4-126"><xref:System.Xml.Linq.XElement> represents an XML element.</span></span> <span data-ttu-id="00fe4-127">Ayrıntılı bilgi ve örnekler için [Bkz. XElement Sınıf Genel Bakış (C#)](./xelement-class-overview.md).</span><span class="sxs-lookup"><span data-stu-id="00fe4-127">For detailed information and examples, see [XElement Class Overview (C#)](./xelement-class-overview.md).</span></span>  
  
### <a name="xname-class"></a><span data-ttu-id="00fe4-128">XName Sınıfı</span><span class="sxs-lookup"><span data-stu-id="00fe4-128">XName Class</span></span>  
 <span data-ttu-id="00fe4-129"><xref:System.Xml.Linq.XName>öğelerin adlarını<xref:System.Xml.Linq.XElement>( )<xref:System.Xml.Linq.XAttribute>ve öznitelikleri ( temsil eder).</span><span class="sxs-lookup"><span data-stu-id="00fe4-129"><xref:System.Xml.Linq.XName> represents names of elements (<xref:System.Xml.Linq.XElement>) and attributes (<xref:System.Xml.Linq.XAttribute>).</span></span> <span data-ttu-id="00fe4-130">Ayrıntılı bilgi ve örnekler için Bkz. [XDocument Sınıf Genel Bakış (C#)](./xdocument-class-overview.md).</span><span class="sxs-lookup"><span data-stu-id="00fe4-130">For detailed information and examples, see [XDocument Class Overview (C#)](./xdocument-class-overview.md).</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="00fe4-131">XML adlarını olabildiğince basit hale getirmek için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="00fe4-131">is designed to make XML names as straightforward as possible.</span></span> <span data-ttu-id="00fe4-132">Karmaşıklıkları nedeniyle, XML adları genellikle XML'de gelişmiş bir konu olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="00fe4-132">Due to their complexity, XML names are often considered to be an advanced topic in XML.</span></span> <span data-ttu-id="00fe4-133">Bu karmaşıklık, geliştiricilerin programlamada düzenli olarak kullandıkları ad alanlarından değil, ad alanı öneklerinden gelir.</span><span class="sxs-lookup"><span data-stu-id="00fe4-133">Arguably, this complexity comes not from namespaces, which developers use regularly in programming, but from namespace prefixes.</span></span> <span data-ttu-id="00fe4-134">Ad alanı önekleri, XML girdiğinizde gereken tuş vuruşlarını azaltmak veya XML'nin okunmasını kolaylaştırmak için yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="00fe4-134">Namespace prefixes can be useful to reduce the keystrokes required when you input XML, or to make XML easier to read.</span></span> <span data-ttu-id="00fe4-135">Ancak, öneekler genellikle tam XML ad alanını kullanmak için kullanılan bir kısayoldur ve çoğu durumda gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="00fe4-135">However, prefixes are often just a shortcut for using the full XML namespace, and are not required in most cases.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="00fe4-136">tüm önekleri karşılık gelen XML ad alanına çözerek XML adlarını basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="00fe4-136">simplifies XML names by resolving all prefixes to their corresponding XML namespace.</span></span> <span data-ttu-id="00fe4-137">Önekler, <xref:System.Xml.Linq.XElement.GetPrefixOfNamespace%2A> gerekirse, yöntem aracılığıyla kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="00fe4-137">Prefixes are available, if they are required, through the <xref:System.Xml.Linq.XElement.GetPrefixOfNamespace%2A> method.</span></span>  
  
 <span data-ttu-id="00fe4-138">Gerekirse ad alanı önekleri denetlemek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="00fe4-138">It is possible, if necessary, to control namespace prefixes.</span></span> <span data-ttu-id="00fe4-139">Bazı durumlarda, XSLT veya XAML gibi diğer XML sistemleriyle çalışıyorsanız, ad alanı önekleri denetlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="00fe4-139">In some circumstances, if you are working with other XML systems, such as XSLT or XAML, you need to control namespace prefixes.</span></span> <span data-ttu-id="00fe4-140">Örneğin, ad alanı önekleri kullanan ve bir XSLT stil sayfasına katıştırılmış bir XPath ifadeniz varsa, XML belgenizin XPath ifadesinde kullanılanlarla eşleşen ad alanı önekleri ile seri hale getirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="00fe4-140">For example, if you have an XPath expression that uses namespace prefixes and is embedded in an XSLT stylesheet, you must make sure that your XML document is serialized with namespace prefixes that match those used in the XPath expression.</span></span>  
  
### <a name="xnamespace-class"></a><span data-ttu-id="00fe4-141">XNamespace Sınıfı</span><span class="sxs-lookup"><span data-stu-id="00fe4-141">XNamespace Class</span></span>  
 <span data-ttu-id="00fe4-142"><xref:System.Xml.Linq.XNamespace>bir <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XAttribute>. için bir ad alanını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="00fe4-142"><xref:System.Xml.Linq.XNamespace> represents a namespace for an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute>.</span></span> <span data-ttu-id="00fe4-143">Ad alanları bir <xref:System.Xml.Linq.XName>.</span><span class="sxs-lookup"><span data-stu-id="00fe4-143">Namespaces are a component of an <xref:System.Xml.Linq.XName>.</span></span>  
  
### <a name="xnode-class"></a><span data-ttu-id="00fe4-144">XNode Sınıfı</span><span class="sxs-lookup"><span data-stu-id="00fe4-144">XNode Class</span></span>  
 <span data-ttu-id="00fe4-145"><xref:System.Xml.Linq.XNode>bir XML ağacının düğümlerini temsil eden soyut bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="00fe4-145"><xref:System.Xml.Linq.XNode> is an abstract class that represents the nodes of an XML tree.</span></span> <span data-ttu-id="00fe4-146">Aşağıdaki sınıflar sınıftan <xref:System.Xml.Linq.XNode> türetilmiştir:</span><span class="sxs-lookup"><span data-stu-id="00fe4-146">The following classes derive from the <xref:System.Xml.Linq.XNode> class:</span></span>  
  
- <xref:System.Xml.Linq.XText>  
  
- <xref:System.Xml.Linq.XContainer>  
  
- <xref:System.Xml.Linq.XComment>  
  
- <xref:System.Xml.Linq.XProcessingInstruction>  
  
- <xref:System.Xml.Linq.XDocumentType>  
  
### <a name="xnodedocumentordercomparer-class"></a><span data-ttu-id="00fe4-147">XNodeDocumentOrderComparer Sınıfı</span><span class="sxs-lookup"><span data-stu-id="00fe4-147">XNodeDocumentOrderComparer Class</span></span>  
 <span data-ttu-id="00fe4-148"><xref:System.Xml.Linq.XNodeDocumentOrderComparer>kendi belge sırası için düğümleri karşılaştırmak için işlevsellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="00fe4-148"><xref:System.Xml.Linq.XNodeDocumentOrderComparer> provides functionality to compare nodes for their document order.</span></span>  
  
### <a name="xnodeequalitycomparer-class"></a><span data-ttu-id="00fe4-149">XNodeEqualityComparer Sınıfı</span><span class="sxs-lookup"><span data-stu-id="00fe4-149">XNodeEqualityComparer Class</span></span>  
 <span data-ttu-id="00fe4-150"><xref:System.Xml.Linq.XNodeEqualityComparer>değer eşitliği düğümlerini karşılaştırmak için işlevsellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="00fe4-150"><xref:System.Xml.Linq.XNodeEqualityComparer> provides functionality to compare nodes for value equality.</span></span>  
  
### <a name="xobject-class"></a><span data-ttu-id="00fe4-151">XObject Sınıfı</span><span class="sxs-lookup"><span data-stu-id="00fe4-151">XObject Class</span></span>  
 <span data-ttu-id="00fe4-152"><xref:System.Xml.Linq.XObject>soyut bir taban <xref:System.Xml.Linq.XNode> sınıf <xref:System.Xml.Linq.XAttribute>ve .</span><span class="sxs-lookup"><span data-stu-id="00fe4-152"><xref:System.Xml.Linq.XObject> is an abstract base class of <xref:System.Xml.Linq.XNode> and <xref:System.Xml.Linq.XAttribute>.</span></span> <span data-ttu-id="00fe4-153">Ek açıklama ve olay işlevselliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="00fe4-153">It provides annotation and event functionality.</span></span>  
  
### <a name="xobjectchange-class"></a><span data-ttu-id="00fe4-154">XObjectChange Sınıfı</span><span class="sxs-lookup"><span data-stu-id="00fe4-154">XObjectChange Class</span></span>  
 <span data-ttu-id="00fe4-155"><xref:System.Xml.Linq.XObjectChange>bir olay için yükseltildiğinde olay türünü <xref:System.Xml.Linq.XObject>belirtir.</span><span class="sxs-lookup"><span data-stu-id="00fe4-155"><xref:System.Xml.Linq.XObjectChange> specifies the event type when an event is raised for an <xref:System.Xml.Linq.XObject>.</span></span>  
  
### <a name="xobjectchangeeventargs-class"></a><span data-ttu-id="00fe4-156">XObjectChangeEventArgs Sınıfı</span><span class="sxs-lookup"><span data-stu-id="00fe4-156">XObjectChangeEventArgs Class</span></span>  
 <span data-ttu-id="00fe4-157"><xref:System.Xml.Linq.XObjectChangeEventArgs><xref:System.Xml.Linq.XObject.Changing> ve <xref:System.Xml.Linq.XObject.Changed> olaylar için veri sağlar.</span><span class="sxs-lookup"><span data-stu-id="00fe4-157"><xref:System.Xml.Linq.XObjectChangeEventArgs> provides data for the <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed> events.</span></span>  
  
### <a name="xprocessinginstruction-class"></a><span data-ttu-id="00fe4-158">XProcessingInstruction Sınıfı</span><span class="sxs-lookup"><span data-stu-id="00fe4-158">XProcessingInstruction Class</span></span>  
 <span data-ttu-id="00fe4-159"><xref:System.Xml.Linq.XProcessingInstruction>bir XML işleme yönergesi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="00fe4-159"><xref:System.Xml.Linq.XProcessingInstruction> represents an XML processing instruction.</span></span> <span data-ttu-id="00fe4-160">İşleme yönergesi, bilgileri XML'i işleyen bir uygulamaya iletir.</span><span class="sxs-lookup"><span data-stu-id="00fe4-160">A processing instruction communicates information to an application that processes the XML.</span></span>  
  
### <a name="xtext-class"></a><span data-ttu-id="00fe4-161">XText Sınıfı</span><span class="sxs-lookup"><span data-stu-id="00fe4-161">XText Class</span></span>  
 <span data-ttu-id="00fe4-162"><xref:System.Xml.Linq.XText>bir metin düğümüntemsil eder.</span><span class="sxs-lookup"><span data-stu-id="00fe4-162"><xref:System.Xml.Linq.XText> represents a text node.</span></span> <span data-ttu-id="00fe4-163">Çoğu durumda, bu sınıfı kullanmak zorunda değildir.</span><span class="sxs-lookup"><span data-stu-id="00fe4-163">In most cases, you do not have to use this class.</span></span> <span data-ttu-id="00fe4-164">Bu sınıf öncelikle karışık içerik için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="00fe4-164">This class is primarily used for mixed content.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00fe4-165">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="00fe4-165">See also</span></span>

- [<span data-ttu-id="00fe4-166">LINQ - XML Programlamaya Genel Bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="00fe4-166">LINQ to XML Programming Overview (C#)</span></span>](./linq-to-xml-overview.md)
