---
title: "LINQ-XML sınıfları genel bakış (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f11b62b5-d522-4c23-92ae-23186dc16447
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f22f1b7e4f94acda3a9279baf92fbce0840e55ba
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="linq-to-xml-classes-overview-visual-basic"></a><span data-ttu-id="e36c3-102">LINQ-XML sınıfları genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e36c3-102">LINQ to XML Classes Overview (Visual Basic)</span></span>
<span data-ttu-id="e36c3-103">Bu konu bir listesini sağlar [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sınıfları <xref:System.Xml.Linq> ad alanı ve her kısa bir açıklaması.</span><span class="sxs-lookup"><span data-stu-id="e36c3-103">This topic provides a list of the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] classes in the <xref:System.Xml.Linq> namespace, and a short description of each.</span></span>  
  
## <a name="linq-to-xml-classes"></a><span data-ttu-id="e36c3-104">LINQ-XML sınıfları</span><span class="sxs-lookup"><span data-stu-id="e36c3-104">LINQ to XML Classes</span></span>  
  
### <a name="xattribute-class"></a><span data-ttu-id="e36c3-105">XAttribute sınıfı</span><span class="sxs-lookup"><span data-stu-id="e36c3-105">XAttribute Class</span></span>  
 <span data-ttu-id="e36c3-106"><xref:System.Xml.Linq.XAttribute>bir XML özniteliği temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e36c3-106"><xref:System.Xml.Linq.XAttribute> represents an XML attribute.</span></span> <span data-ttu-id="e36c3-107">Ayrıntılı bilgi ve örnekler için bkz: [XAttribute sınıfına genel bakış (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/xattribute-class-overview.md).</span><span class="sxs-lookup"><span data-stu-id="e36c3-107">For detailed information and examples, see [XAttribute Class Overview (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/xattribute-class-overview.md).</span></span>  
  
### <a name="xcdata-class"></a><span data-ttu-id="e36c3-108">XCData sınıfı</span><span class="sxs-lookup"><span data-stu-id="e36c3-108">XCData Class</span></span>  
 <span data-ttu-id="e36c3-109"><xref:System.Xml.Linq.XCData>CDATA metin düğümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e36c3-109"><xref:System.Xml.Linq.XCData> represents a CDATA text node.</span></span>  
  
### <a name="xcomment-class"></a><span data-ttu-id="e36c3-110">XComment sınıfı</span><span class="sxs-lookup"><span data-stu-id="e36c3-110">XComment Class</span></span>  
 <span data-ttu-id="e36c3-111"><xref:System.Xml.Linq.XComment>bir XML açıklama temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e36c3-111"><xref:System.Xml.Linq.XComment> represents an XML comment.</span></span>  
  
### <a name="xcontainer-class"></a><span data-ttu-id="e36c3-112">XContainer sınıfı</span><span class="sxs-lookup"><span data-stu-id="e36c3-112">XContainer Class</span></span>  
 <span data-ttu-id="e36c3-113"><xref:System.Xml.Linq.XContainer>alt düğümleri bulunabilir tüm düğümler için Özet temel sınıf olur.</span><span class="sxs-lookup"><span data-stu-id="e36c3-113"><xref:System.Xml.Linq.XContainer> is an abstract base class for all nodes that can have child nodes.</span></span> <span data-ttu-id="e36c3-114">Aşağıdaki sınıflar türetmek <xref:System.Xml.Linq.XContainer> sınıfı:</span><span class="sxs-lookup"><span data-stu-id="e36c3-114">The following classes derive from the <xref:System.Xml.Linq.XContainer> class:</span></span>  
  
-   <xref:System.Xml.Linq.XElement>  
  
-   <xref:System.Xml.Linq.XDocument>  
  
### <a name="xdeclaration-class"></a><span data-ttu-id="e36c3-115">XDeclaration sınıfı</span><span class="sxs-lookup"><span data-stu-id="e36c3-115">XDeclaration Class</span></span>  
 <span data-ttu-id="e36c3-116"><xref:System.Xml.Linq.XDeclaration>bir XML bildirimi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e36c3-116"><xref:System.Xml.Linq.XDeclaration> represents an XML declaration.</span></span> <span data-ttu-id="e36c3-117">Bir XML bildirimi XML sürümü ve bir belgeyi kodlama bildirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e36c3-117">An XML declaration is used to declare the XML version and the encoding of a document.</span></span> <span data-ttu-id="e36c3-118">Ayrıca, bir XML bildirimi XML belgesi tek başına olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e36c3-118">In addition, an XML declaration specifies whether the XML document is stand-alone.</span></span> <span data-ttu-id="e36c3-119">Bir belge tek başına ise, bir dış DTD, veya bir iç alt başvurulan bir dış parametre varlık hiçbir dış biçimlendirme bildirimleri vardır.</span><span class="sxs-lookup"><span data-stu-id="e36c3-119">If a document is stand-alone, there are no external markup declarations, either in an external DTD, or in an external parameter entity referenced from the internal subset.</span></span>  
  
### <a name="xdocument-class"></a><span data-ttu-id="e36c3-120">XDocument sınıfı</span><span class="sxs-lookup"><span data-stu-id="e36c3-120">XDocument Class</span></span>  
 <span data-ttu-id="e36c3-121"><xref:System.Xml.Linq.XDocument>bir XML belgesi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e36c3-121"><xref:System.Xml.Linq.XDocument> represents an XML document.</span></span> <span data-ttu-id="e36c3-122">Ayrıntılı bilgi ve örnekler için bkz: [XDocument sınıfına genel bakış (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/xdocument-class-overview.md).</span><span class="sxs-lookup"><span data-stu-id="e36c3-122">For detailed information and examples, see [XDocument Class Overview (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/xdocument-class-overview.md).</span></span>  
  
### <a name="xdocumenttype-class"></a><span data-ttu-id="e36c3-123">XDocumentType sınıfı</span><span class="sxs-lookup"><span data-stu-id="e36c3-123">XDocumentType Class</span></span>  
 <span data-ttu-id="e36c3-124"><xref:System.Xml.Linq.XDocumentType>bir XML belge türü tanımı (DTD) temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e36c3-124"><xref:System.Xml.Linq.XDocumentType> represents an XML Document Type Definition (DTD).</span></span>  
  
### <a name="xelement-class"></a><span data-ttu-id="e36c3-125">XElement sınıfı</span><span class="sxs-lookup"><span data-stu-id="e36c3-125">XElement Class</span></span>  
 <span data-ttu-id="e36c3-126"><xref:System.Xml.Linq.XElement>bir XML öğesi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e36c3-126"><xref:System.Xml.Linq.XElement> represents an XML element.</span></span> <span data-ttu-id="e36c3-127">Ayrıntılı bilgi ve örnekler için bkz: [XElement sınıfına genel bakış (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/xelement-class-overview.md).</span><span class="sxs-lookup"><span data-stu-id="e36c3-127">For detailed information and examples, see [XElement Class Overview (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/xelement-class-overview.md).</span></span>  
  
### <a name="xname-class"></a><span data-ttu-id="e36c3-128">XName sınıfı</span><span class="sxs-lookup"><span data-stu-id="e36c3-128">XName Class</span></span>  
 <span data-ttu-id="e36c3-129"><xref:System.Xml.Linq.XName>öğelerinin adlarını temsil eder (<xref:System.Xml.Linq.XElement>) ve öznitelikler (<xref:System.Xml.Linq.XAttribute>).</span><span class="sxs-lookup"><span data-stu-id="e36c3-129"><xref:System.Xml.Linq.XName> represents names of elements (<xref:System.Xml.Linq.XElement>) and attributes (<xref:System.Xml.Linq.XAttribute>).</span></span> <span data-ttu-id="e36c3-130">Ayrıntılı bilgi ve örnekler için bkz: [XDocument sınıfına genel bakış (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/xdocument-class-overview.md).</span><span class="sxs-lookup"><span data-stu-id="e36c3-130">For detailed information and examples, see [XDocument Class Overview (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/xdocument-class-overview.md).</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="e36c3-131">XML adları kadar basit hale getirecek şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="e36c3-131"> is designed to make XML names as straightforward as possible.</span></span> <span data-ttu-id="e36c3-132">Kendi karmaşıklığı nedeniyle XML adları genellikle XML Gelişmiş bir konu olduğu kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="e36c3-132">Due to their complexity, XML names are often considered to be an advanced topic in XML.</span></span> <span data-ttu-id="e36c3-133">Bu karmaşıklık tartışmaya açık bir şekilde, geliştiricilerin düzenli olarak programlamada kullanın, olmayan ad alanlarını, ancak ad alanı öneklerini birlikte gelir.</span><span class="sxs-lookup"><span data-stu-id="e36c3-133">Arguably, this complexity comes not from namespaces, which developers use regularly in programming, but from namespace prefixes.</span></span> <span data-ttu-id="e36c3-134">Namespace önekleri XML girdikten sonra gerekli tuş vuruşları azaltmak veya XML okunmasını kolaylaştırmak için yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="e36c3-134">Namespace prefixes can be useful to reduce the keystrokes required when you input XML, or to make XML easier to read.</span></span> <span data-ttu-id="e36c3-135">Ancak, ön eklerin genellikle tam XML ad alanı kullanmak için yalnızca bir kısayol bağlıdır ve çoğu durumda gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="e36c3-135">However, prefixes are often just a shortcut for using the full XML namespace, and are not required in most cases.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="e36c3-136">XML adları, bunların karşılık gelen XML ad alanı için tüm ön eklerin çözülerek basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="e36c3-136"> simplifies XML names by resolving all prefixes to their corresponding XML namespace.</span></span> <span data-ttu-id="e36c3-137">Önekleri kullanılabilir aracılığıyla gerekli iseler, <xref:System.Xml.Linq.XElement.GetPrefixOfNamespace%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e36c3-137">Prefixes are available, if they are required, through the <xref:System.Xml.Linq.XElement.GetPrefixOfNamespace%2A> method.</span></span>  
  
 <span data-ttu-id="e36c3-138">Gerekirse denetimi ad alanı öneklerini, mümkündür.</span><span class="sxs-lookup"><span data-stu-id="e36c3-138">It is possible, if necessary, to control namespace prefixes.</span></span> <span data-ttu-id="e36c3-139">Bazı durumlarda, XSLT veya XAML gibi diğer XML sistemleriyle çalışıyorsanız ad alanı öneklerini denetlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e36c3-139">In some circumstances, if you are working with other XML systems, such as XSLT or XAML, you need to control namespace prefixes.</span></span> <span data-ttu-id="e36c3-140">Örneğin, ad alanı öneklerini kullanan ve XSLT stil sayfasında katıştırılmış bir XPath ifadesi varsa, XML belgeniz XPath ifadesinde kullanılanlarla aynı ad alanı öneklerini serileştirilmişse emin olmalısınız.</span><span class="sxs-lookup"><span data-stu-id="e36c3-140">For example, if you have an XPath expression that uses namespace prefixes and is embedded in an XSLT stylesheet, you must make sure that your XML document is serialized with namespace prefixes that match those used in the XPath expression.</span></span>  
  
### <a name="xnamespace-class"></a><span data-ttu-id="e36c3-141">XNamespace sınıfı</span><span class="sxs-lookup"><span data-stu-id="e36c3-141">XNamespace Class</span></span>  
 <span data-ttu-id="e36c3-142"><xref:System.Xml.Linq.XNamespace>bir ad alanı için temsil eden bir <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XAttribute>.</span><span class="sxs-lookup"><span data-stu-id="e36c3-142"><xref:System.Xml.Linq.XNamespace> represents a namespace for an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute>.</span></span> <span data-ttu-id="e36c3-143">Ad alanları'nin bir bileşeni olan bir <xref:System.Xml.Linq.XName>.</span><span class="sxs-lookup"><span data-stu-id="e36c3-143">Namespaces are a component of an <xref:System.Xml.Linq.XName>.</span></span>  
  
### <a name="xnode-class"></a><span data-ttu-id="e36c3-144">XNode sınıfı</span><span class="sxs-lookup"><span data-stu-id="e36c3-144">XNode Class</span></span>  
 <span data-ttu-id="e36c3-145"><xref:System.Xml.Linq.XNode>bir XML ağaç düğümleri temsil eden bir soyut sınıftır.</span><span class="sxs-lookup"><span data-stu-id="e36c3-145"><xref:System.Xml.Linq.XNode> is an abstract class that represents the nodes of an XML tree.</span></span> <span data-ttu-id="e36c3-146">Aşağıdaki sınıflar türetmek <xref:System.Xml.Linq.XNode> sınıfı:</span><span class="sxs-lookup"><span data-stu-id="e36c3-146">The following classes derive from the <xref:System.Xml.Linq.XNode> class:</span></span>  
  
-   <xref:System.Xml.Linq.XText>  
  
-   <xref:System.Xml.Linq.XContainer>  
  
-   <xref:System.Xml.Linq.XComment>  
  
-   <xref:System.Xml.Linq.XProcessingInstruction>  
  
-   <xref:System.Xml.Linq.XDocumentType>  
  
### <a name="xnodedocumentordercomparer-class"></a><span data-ttu-id="e36c3-147">XNodeDocumentOrderComparer sınıfı</span><span class="sxs-lookup"><span data-stu-id="e36c3-147">XNodeDocumentOrderComparer Class</span></span>  
 <span data-ttu-id="e36c3-148"><xref:System.Xml.Linq.XNodeDocumentOrderComparer>Belge sıralarına için düğümleri karşılaştırmak için işlevsellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="e36c3-148"><xref:System.Xml.Linq.XNodeDocumentOrderComparer> provides functionality to compare nodes for their document order.</span></span>  
  
### <a name="xnodeequalitycomparer-class"></a><span data-ttu-id="e36c3-149">XNodeEqualityComparer sınıfı</span><span class="sxs-lookup"><span data-stu-id="e36c3-149">XNodeEqualityComparer Class</span></span>  
 <span data-ttu-id="e36c3-150"><xref:System.Xml.Linq.XNodeEqualityComparer>düğümleri için değer eşitliği karşılaştırmak için işlevsellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="e36c3-150"><xref:System.Xml.Linq.XNodeEqualityComparer> provides functionality to compare nodes for value equality.</span></span>  
  
### <a name="xobject-class"></a><span data-ttu-id="e36c3-151">XObject sınıfı</span><span class="sxs-lookup"><span data-stu-id="e36c3-151">XObject Class</span></span>  
 <span data-ttu-id="e36c3-152"><xref:System.Xml.Linq.XObject>bir Özet temel sınıf olarak <xref:System.Xml.Linq.XNode> ve <xref:System.Xml.Linq.XAttribute>.</span><span class="sxs-lookup"><span data-stu-id="e36c3-152"><xref:System.Xml.Linq.XObject> is an abstract base class of <xref:System.Xml.Linq.XNode> and <xref:System.Xml.Linq.XAttribute>.</span></span> <span data-ttu-id="e36c3-153">Ek açıklama ve olay işlevselliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="e36c3-153">It provides annotation and event functionality.</span></span>  
  
### <a name="xobjectchange-class"></a><span data-ttu-id="e36c3-154">XObjectChange sınıfı</span><span class="sxs-lookup"><span data-stu-id="e36c3-154">XObjectChange Class</span></span>  
 <span data-ttu-id="e36c3-155"><xref:System.Xml.Linq.XObjectChange>için bir olay oluşturulduğunda olay türünü belirten bir <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="e36c3-155"><xref:System.Xml.Linq.XObjectChange> specifies the event type when an event is raised for an <xref:System.Xml.Linq.XObject>.</span></span>  
  
### <a name="xobjectchangeeventargs-class"></a><span data-ttu-id="e36c3-156">XObjectChangeEventArgs sınıfı</span><span class="sxs-lookup"><span data-stu-id="e36c3-156">XObjectChangeEventArgs Class</span></span>  
 <span data-ttu-id="e36c3-157"><xref:System.Xml.Linq.XObjectChangeEventArgs>veriler için sağlar <xref:System.Xml.Linq.XObject.Changing> ve <xref:System.Xml.Linq.XObject.Changed> olaylar.</span><span class="sxs-lookup"><span data-stu-id="e36c3-157"><xref:System.Xml.Linq.XObjectChangeEventArgs> provides data for the <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed> events.</span></span>  
  
### <a name="xprocessinginstruction-class"></a><span data-ttu-id="e36c3-158">XProcessingInstruction sınıfı</span><span class="sxs-lookup"><span data-stu-id="e36c3-158">XProcessingInstruction Class</span></span>  
 <span data-ttu-id="e36c3-159"><xref:System.Xml.Linq.XProcessingInstruction>XML işleme talimatı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e36c3-159"><xref:System.Xml.Linq.XProcessingInstruction> represents an XML processing instruction.</span></span> <span data-ttu-id="e36c3-160">Bir işleme yönergesi XML işleyen bir uygulama için bilgi iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="e36c3-160">A processing instruction communicates information to an application that processes the XML.</span></span>  
  
### <a name="xtext-class"></a><span data-ttu-id="e36c3-161">XText sınıfı</span><span class="sxs-lookup"><span data-stu-id="e36c3-161">XText Class</span></span>  
 <span data-ttu-id="e36c3-162"><xref:System.Xml.Linq.XText>bir metin düğümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e36c3-162"><xref:System.Xml.Linq.XText> represents a text node.</span></span> <span data-ttu-id="e36c3-163">Çoğu durumda, bu sınıfı kullanmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="e36c3-163">In most cases, you do not have to use this class.</span></span> <span data-ttu-id="e36c3-164">Bu sınıf, öncelikle karışık içerik için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e36c3-164">This class is primarily used for mixed content.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e36c3-165">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e36c3-165">See Also</span></span>  
 [<span data-ttu-id="e36c3-166">LINQ-XML programlamaya genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e36c3-166">LINQ to XML Programming Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
