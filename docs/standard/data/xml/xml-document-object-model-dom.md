---
title: XML Belge Nesne Modeli (DOM)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b5e52844-4820-47c0-a61d-de2da33e9f54
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: af9473af6a315feb6b1f0a741525cbf42dd32d1d
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="xml-document-object-model-dom"></a><span data-ttu-id="e856f-102">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="e856f-102">XML Document Object Model (DOM)</span></span>
<span data-ttu-id="e856f-103">XML belge nesne modeli (DOM) sınıfı, bir XML belgesi bir bellek içi gösterimidir.</span><span class="sxs-lookup"><span data-stu-id="e856f-103">The XML Document Object Model (DOM) class is an in-memory representation of an XML document.</span></span> <span data-ttu-id="e856f-104">DOM program aracılığıyla okuyun, yönetmek ve bir XML belgesi değiştirmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="e856f-104">The DOM allows you to programmatically read, manipulate, and modify an XML document.</span></span> <span data-ttu-id="e856f-105">**XmlReader** sınıfı ayrıca XML okur; ancak, önbelleğe alınmamış salt iletme, salt okunur erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="e856f-105">The **XmlReader** class also reads XML; however, it provides non-cached, forward-only, read-only access.</span></span> <span data-ttu-id="e856f-106">Bu özniteliğin değerini veya bir öğenin veya ekleyin ve düğümleri kaldırma yeteneği içeriğini düzenlemek için özelliği yoktur anlamına gelir **XmlReader**.</span><span class="sxs-lookup"><span data-stu-id="e856f-106">This means that there are no capabilities to edit the values of an attribute or content of an element, or the ability to insert and remove nodes with the **XmlReader**.</span></span> <span data-ttu-id="e856f-107">DOM birincil işlevi olduğu düzenleme</span><span class="sxs-lookup"><span data-stu-id="e856f-107">Editing is the primary function of the DOM.</span></span> <span data-ttu-id="e856f-108">Gerçek XML verilerini bir dosya veya başka bir nesneden gelen doğrusal bir biçimde depolanır ancak ortak ve yapılandırılmış şekilde XML verileri bellekte temsil edilen adıdır.</span><span class="sxs-lookup"><span data-stu-id="e856f-108">It is the common and structured way that XML data is represented in memory, although the actual XML data is stored in a linear fashion when in a file or coming in from another object.</span></span> <span data-ttu-id="e856f-109">XML verilerini verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e856f-109">The following is XML data.</span></span>  
  
## <a name="input"></a><span data-ttu-id="e856f-110">Giriş</span><span class="sxs-lookup"><span data-stu-id="e856f-110">Input</span></span>  
  
```xml  
<?xml version="1.0"?>  
  <books>  
    <book>  
        <author>Carson</author>  
        <price format="dollar">31.95</price>  
        <pubdate>05/01/2001</pubdate>  
    </book>  
    <pubinfo>  
        <publisher>MSPress</publisher>  
        <state>WA</state>  
    </pubinfo>  
  </books>   
```  
  
 <span data-ttu-id="e856f-111">Aşağıdaki çizimde, bu XML verileri DOM yapısına okunduğunda bellek nasıl yapılandırıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e856f-111">The following illustration shows how memory is structured when this XML data is read into the DOM structure.</span></span>  
  
 <span data-ttu-id="e856f-112">![XML belge yapısı](../../../../docs/standard/data/xml/media/xml-to-domtree.gif "XML_To_DOMTree")</span><span class="sxs-lookup"><span data-stu-id="e856f-112">![XML document structure](../../../../docs/standard/data/xml/media/xml-to-domtree.gif "XML_To_DOMTree")</span></span>  
<span data-ttu-id="e856f-113">XML belge yapısı</span><span class="sxs-lookup"><span data-stu-id="e856f-113">XML document structure</span></span>  
  
 <span data-ttu-id="e856f-114">XML belge yapısında bu çizimdeki her bir daire olarak adlandırılan bir düğümü temsil eder. bir **XmlNode** nesnesi.</span><span class="sxs-lookup"><span data-stu-id="e856f-114">Within the XML document structure, each circle in this illustration represents a node, which is called an **XmlNode** object.</span></span> <span data-ttu-id="e856f-115">**XmlNode** nesnesi DOM ağacında temel nesnedir.</span><span class="sxs-lookup"><span data-stu-id="e856f-115">The **XmlNode** object is the basic object in the DOM tree.</span></span> <span data-ttu-id="e856f-116">**XmlDocument** sınıfını genişletir **XmlNode**, (örneğin, belleğe yükleme veya XML bir dosyaya kaydetmeyi. bir bütün olarak belge üzerinde işlem gerçekleştirmek için yöntemlerini destekler</span><span class="sxs-lookup"><span data-stu-id="e856f-116">The **XmlDocument** class, which extends **XmlNode**, supports methods for performing operations on the document as a whole (for example, loading it into memory or saving the XML to a file.</span></span> <span data-ttu-id="e856f-117">Ayrıca, **XmlDocument** görüntülemek ve tüm XML belgesi düğümlerin işlemek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="e856f-117">In addition, **XmlDocument** provides a means to view and manipulate the nodes in the entire XML document.</span></span> <span data-ttu-id="e856f-118">Her ikisi de **XmlNode** ve **XmlDocument** performans ve kullanılabilirlik geliştirmeleri ve yöntemleri ve özellikleri:</span><span class="sxs-lookup"><span data-stu-id="e856f-118">Both **XmlNode** and **XmlDocument** have performance and usability enhancements and have methods and properties to:</span></span>  
  
-   <span data-ttu-id="e856f-119">Erişim ve DOM öğesi düğümleri, varlık başvurusu düğümleri vb. gibi belirli düğümler değiştirin.</span><span class="sxs-lookup"><span data-stu-id="e856f-119">Access and modify nodes specific to the DOM, such as element nodes, entity reference nodes, and so on.</span></span>  
  
-   <span data-ttu-id="e856f-120">Bir öğe düğümü metinde gibi düğüm içerir bilgilerine ek olarak tüm düğümleri alır.</span><span class="sxs-lookup"><span data-stu-id="e856f-120">Retrieve entire nodes, in addition to the information the node contains, such as the text in an element node.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e856f-121">Bir uygulama yapısı veya DOM tarafından sağlanan özellikleri düzenleme gerektirmiyorsa **XmlReader** ve **XmlWriter** sınıfları XML önbelleğe alınmamış, yalnızca ileri akış erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="e856f-121">If an application does not require the structure or editing capabilities provided by the DOM, the **XmlReader** and **XmlWriter** classes provide non-cached, forward-only stream access to XML.</span></span> <span data-ttu-id="e856f-122">Daha fazla bilgi için bkz. <xref:System.Xml.XmlReader> ve <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="e856f-122">For more information, see <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="e856f-123">**Düğüm** nesnelerin yöntemleri ve özellikleri yanı sıra, temel ve iyi tanımlanmış özellikleri kümesi vardır.</span><span class="sxs-lookup"><span data-stu-id="e856f-123">**Node** objects have a set of methods and properties, as well as basic and well-defined characteristics.</span></span> <span data-ttu-id="e856f-124">Bu özelliklere bazıları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="e856f-124">Some of these characteristics are:</span></span>  
  
-   <span data-ttu-id="e856f-125">Düğümlerin tek üst düğümü, bir düğüm doğrudan yukarıda olan bir üst düğümü vardır.</span><span class="sxs-lookup"><span data-stu-id="e856f-125">Nodes have a single parent node, a parent node being a node directly above them.</span></span> <span data-ttu-id="e856f-126">Bir üst öğeye sahip değil yalnızca düğümler var. belge kökü en üst düzey düğüm ve belgenin kendisi ve belge parçalarını içerir</span><span class="sxs-lookup"><span data-stu-id="e856f-126">The only nodes that do not have a parent is the Document root, as it is the top-level node and contains the document itself and document fragments.</span></span>  
  
-   <span data-ttu-id="e856f-127">Çoğu düğümleri düğümler doğrudan altında birden çok alt düğümleri bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="e856f-127">Most nodes can have multiple child nodes, which are nodes directly below them.</span></span> <span data-ttu-id="e856f-128">Alt düğümleri bulunabilir düğüm türleri listesi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e856f-128">The following is a list of node types that can have child nodes.</span></span>  
  
    -   <span data-ttu-id="e856f-129">**Belge**</span><span class="sxs-lookup"><span data-stu-id="e856f-129">**Document**</span></span>  
  
    -   <span data-ttu-id="e856f-130">**DocumentFragment**</span><span class="sxs-lookup"><span data-stu-id="e856f-130">**DocumentFragment**</span></span>  
  
    -   <span data-ttu-id="e856f-131">**EntityReference**</span><span class="sxs-lookup"><span data-stu-id="e856f-131">**EntityReference**</span></span>  
  
    -   <span data-ttu-id="e856f-132">**Öğesi**</span><span class="sxs-lookup"><span data-stu-id="e856f-132">**Element**</span></span>  
  
    -   <span data-ttu-id="e856f-133">**Özniteliği**</span><span class="sxs-lookup"><span data-stu-id="e856f-133">**Attribute**</span></span>  
  
     <span data-ttu-id="e856f-134">**XmlDeclaration**, **gösterimi**, **varlık**, **CDATASection**, **metin**,  **Açıklama**, **instruction**, ve **DocumentType** düğümleri alt düğümleri sahip değil.</span><span class="sxs-lookup"><span data-stu-id="e856f-134">The **XmlDeclaration**, **Notation**, **Entity**, **CDATASection**, **Text**, **Comment**, **ProcessingInstruction**, and **DocumentType** nodes do not have child nodes.</span></span>  
  
-   <span data-ttu-id="e856f-135">Diyagram tarafından gösterilen aynı düzeyde olan düğümleri **defteri** ve **PubInfo** düğümleri, eşdüzey öğesi olan.</span><span class="sxs-lookup"><span data-stu-id="e856f-135">Nodes that are at the same level, represented in the diagram by the **book** and **pubinfo** nodes, are siblings.</span></span>  
  
 <span data-ttu-id="e856f-136">Bir DOM öznitelikleri nasıl işler özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="e856f-136">One characteristic of the DOM is how it handles attributes.</span></span> <span data-ttu-id="e856f-137">Öznitelikler üst, alt ve eşdüzey ilişkileri parçası olan düğümler değildir.</span><span class="sxs-lookup"><span data-stu-id="e856f-137">Attributes are not nodes that are part of the parent, child, and sibling relationships.</span></span> <span data-ttu-id="e856f-138">Öznitelikler öğesi düğümünün bir özellik olarak kabul edilir ve bir ad ve değer çifti oluşur.</span><span class="sxs-lookup"><span data-stu-id="e856f-138">Attributes are considered a property of the element node and are made up of a name and a value pair.</span></span> <span data-ttu-id="e856f-139">XML verilerini oluşan varsa, örneğin, `format="dollar`"öğeyle ilişkili `price`, word `format` adı ve değeri `format` özniteliği `dollar`.</span><span class="sxs-lookup"><span data-stu-id="e856f-139">For example, if you have XML data consisting of `format="dollar`" associated with the element `price`, the word `format` is the name, and the value of the `format` attribute is `dollar`.</span></span> <span data-ttu-id="e856f-140">Almak için `format="dollar"` özniteliği **fiyat** düğümü, çağrı **GetAttribute** imleci adresindedir yöntemi `price` öğe düğümü.</span><span class="sxs-lookup"><span data-stu-id="e856f-140">To retrieve the `format="dollar"` attribute of the **price** node, you call the **GetAttribute** method when the cursor is located at the `price` element node.</span></span> <span data-ttu-id="e856f-141">Daha fazla bilgi için bkz: [DOM öznitelikleri erişme](../../../../docs/standard/data/xml/accessing-attributes-in-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="e856f-141">For more information, see [Accessing Attributes in the DOM](../../../../docs/standard/data/xml/accessing-attributes-in-the-dom.md).</span></span>  
  
 <span data-ttu-id="e856f-142">XML belleğe okurken düğümleri oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e856f-142">As XML is read into memory, nodes are created.</span></span> <span data-ttu-id="e856f-143">Ancak, tüm düğümler aynı türdeyse.</span><span class="sxs-lookup"><span data-stu-id="e856f-143">However, not all nodes are the same type.</span></span> <span data-ttu-id="e856f-144">Bir öğenin farklı kurallar ve işlem yönergesi sözdizimi vardır.</span><span class="sxs-lookup"><span data-stu-id="e856f-144">An element in XML has different rules and syntax than a processing instruction.</span></span> <span data-ttu-id="e856f-145">Bu nedenle, çeşitli veri okuma gibi bir düğüm türü her düğüme atanır.</span><span class="sxs-lookup"><span data-stu-id="e856f-145">Therefore, as various data is read, a node type is assigned to each node.</span></span> <span data-ttu-id="e856f-146">Bu düğüm türü, özellikleri ve işlevleri düğümün belirler.</span><span class="sxs-lookup"><span data-stu-id="e856f-146">This node type determines the characteristics and functionality of the node.</span></span>  
  
 <span data-ttu-id="e856f-147">Bellekte oluşturulan düğüm türleri hakkında daha fazla bilgi için bkz: [XML düğümlerini türleri](../../../../docs/standard/data/xml/types-of-xml-nodes.md).</span><span class="sxs-lookup"><span data-stu-id="e856f-147">For more information on the types of nodes generated in memory, see [Types of XML Nodes](../../../../docs/standard/data/xml/types-of-xml-nodes.md).</span></span> <span data-ttu-id="e856f-148">Düğüm ağaçta oluşturulan nesneler hakkında daha fazla bilgi için bkz: [nesne hiyerarşisi XML verileri eşleştirmesi](../../../../docs/standard/data/xml/mapping-the-object-hierarchy-to-xml-data.md).</span><span class="sxs-lookup"><span data-stu-id="e856f-148">For more information on the objects created in the node tree, see [Mapping the Object Hierarchy to XML Data](../../../../docs/standard/data/xml/mapping-the-object-hierarchy-to-xml-data.md).</span></span>  
  
 <span data-ttu-id="e856f-149">Microsoft World Wide Web Konsorsiyumu (W3C) DOM düzey 1 ve Düzey 2 XML belgesiyle çalışması kolay hale getirmek için kullanılabilen API'leri genişletmiştir.</span><span class="sxs-lookup"><span data-stu-id="e856f-149">Microsoft has extended the APIs that are available in the World Wide Web Consortium (W3C) DOM Level 1 and Level 2 to make it easier to work with an XML document.</span></span> <span data-ttu-id="e856f-150">W3C standartlarını tam olarak desteklerken, ek sınıfları, yöntemleri ve özellikleri ekleme işlevselliği ne yapılabilir ötesine W3C XML DOM kullanma</span><span class="sxs-lookup"><span data-stu-id="e856f-150">While fully supporting the W3C standards, the additional classes, methods, and properties add functionality beyond what can be done using the W3C XML DOM.</span></span> <span data-ttu-id="e856f-151">Yeni sınıflar, aynı anda XML olarak verilerin açığa ADO.NET verilerle eşitlemek için yöntem vermiş ilişkisel veri erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="e856f-151">New classes enable you to access relational data, giving you methods for synchronizing with ADO.NET data, simultaneously exposing data as XML.</span></span> <span data-ttu-id="e856f-152">Daha fazla bilgi için bkz: [XmlDataDocument ile bir veri eşitleme](../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md).</span><span class="sxs-lookup"><span data-stu-id="e856f-152">For more information, see [Synchronizing a DataSet with an XmlDataDocument](../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md).</span></span>  
  
 <span data-ttu-id="e856f-153">DOM yapısını değiştirmek, ekleme veya düğümleri kaldırma veya bir öğenin bulunan metin olduğu gibi bir düğüm tarafından tutulan verileri değiştirmek için belleğe XML verileri okumak için kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="e856f-153">The DOM is most useful for reading XML data into memory to change its structure, to add or remove nodes, or to modify the data held by a node as in the text contained by an element.</span></span> <span data-ttu-id="e856f-154">Bununla birlikte, diğer sınıflar kullanılabilir olan diğer senaryolarda DOM hızlıdır.</span><span class="sxs-lookup"><span data-stu-id="e856f-154">However, other classes are available that are faster than the DOM in other scenarios.</span></span> <span data-ttu-id="e856f-155">XML için hızlı, önbelleğe alınmamış, yalnızca ileri akış erişimi için kullandığınız **XmlReader** ve **XmlWriter**.</span><span class="sxs-lookup"><span data-stu-id="e856f-155">For fast, non-cached, forward-only stream access to XML, use the **XmlReader** and **XmlWriter**.</span></span> <span data-ttu-id="e856f-156">İmleç modeliyle rastgele erişmesi gerekiyorsa ve **XPath**, kullanın **XPathNavigator** sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e856f-156">If you need random access with a cursor model and **XPath**, use the **XPathNavigator** class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e856f-157">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e856f-157">See Also</span></span>  
 [<span data-ttu-id="e856f-158">XML Düğüm Türleri</span><span class="sxs-lookup"><span data-stu-id="e856f-158">Types of XML Nodes</span></span>](../../../../docs/standard/data/xml/types-of-xml-nodes.md)  
 [<span data-ttu-id="e856f-159">XML Verilerine Nesne Hiyerarşisi Eşleme</span><span class="sxs-lookup"><span data-stu-id="e856f-159">Mapping the Object Hierarchy to XML Data</span></span>](../../../../docs/standard/data/xml/mapping-the-object-hierarchy-to-xml-data.md)
