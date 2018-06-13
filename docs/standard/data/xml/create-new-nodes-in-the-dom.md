---
title: Yeni düğümler DOM'da oluşturma
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 6c2b9789-b61a-49f9-b33f-db01a945edf2
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bbc8d6c1055afc1a0799522f341551d04bab4ace
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33569310"
---
# <a name="create-new-nodes-in-the-dom"></a><span data-ttu-id="2b543-102">Yeni düğümler DOM'da oluşturma</span><span class="sxs-lookup"><span data-stu-id="2b543-102">Create New Nodes in the DOM</span></span>
<span data-ttu-id="2b543-103"><xref:System.Xml.XmlDocument> Tüm düğüm türü için create yöntemi vardır.</span><span class="sxs-lookup"><span data-stu-id="2b543-103">The <xref:System.Xml.XmlDocument> has a create method for all of the node types.</span></span> <span data-ttu-id="2b543-104">Gerekli olduğunda bir adla yöntemi sağlayın ve içerik veya içeriğe (örneğin, bir metin düğümü) sahip düğümleri ve düğüm için başka parametre oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="2b543-104">Supply the method with a name when required, and content or other parameters for those nodes that have content (for example, a text node), and the node is created.</span></span> <span data-ttu-id="2b543-105">Aşağıdaki yöntemler, bir ada ihtiyacınız olanları ve uygun bir düğüm oluşturmak için doldurulmuş birkaç diğer parametreleri yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="2b543-105">The following methods are ones that need a name and a few other parameters filled to create an appropriate node.</span></span>  
  
-   <xref:System.Xml.XmlDocument.CreateCDataSection%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateComment%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateDocumentFragment%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateDocumentType%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateElement%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateNode%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateProcessingInstruction%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateSignificantWhitespace%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateTextNode%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateWhitespace%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateXmlDeclaration%2A>  
  
 <span data-ttu-id="2b543-106">Diğer düğüm türleri yalnızca veri parametrelerine sağlamaktan daha fazla gereksinimlere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="2b543-106">Other node types have more requirements than just providing data to parameters.</span></span>  
  
 <span data-ttu-id="2b543-107">Öznitelikleri hakkında daha fazla bilgi için bkz: [DOM öğeleri için yeni öznitelikler oluşturma](../../../../docs/standard/data/xml/creating-new-attributes-for-elements-in-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="2b543-107">For information on attributes, see [Creating New Attributes for Elements in the DOM](../../../../docs/standard/data/xml/creating-new-attributes-for-elements-in-the-dom.md).</span></span> <span data-ttu-id="2b543-108">Öğe ve öznitelik adı doğrulama hakkında daha fazla bilgi için bkz: [XML öğesi ve öznitelik adı oluştururken doğrulama yeni düğümler](../../../../docs/standard/data/xml/xml-element-and-attribute-name-verification-when-creating-new-nodes.md).</span><span class="sxs-lookup"><span data-stu-id="2b543-108">For information on element and attribute name validation, see [XML Element and Attribute Name Verification when Creating New Nodes](../../../../docs/standard/data/xml/xml-element-and-attribute-name-verification-when-creating-new-nodes.md).</span></span> <span data-ttu-id="2b543-109">Varlık başvuruları oluşturmak için bkz: [oluşturma yeni varlık başvuruları](../../../../docs/standard/data/xml/creating-new-entity-references.md).</span><span class="sxs-lookup"><span data-stu-id="2b543-109">For creating entity references, see [Creating New Entity References](../../../../docs/standard/data/xml/creating-new-entity-references.md).</span></span> <span data-ttu-id="2b543-110">Ad alanları varlık başvuruları genişletme etkilemesi hakkında daha fazla bilgi için bkz: [yeni düğümler içeren öğeleri ve öznitelikleri için varlık başvurusu genişletme Namespace güncelleştirmedikçe](../../../../docs/standard/data/xml/namespace-affect-on-entity-ref-expansion-for-new-nodes.md).</span><span class="sxs-lookup"><span data-stu-id="2b543-110">For information on how namespaces affect the expansion of entity references, see [Namespace Affect on Entity Reference Expansion for New Nodes Containing Elements and Attributes](../../../../docs/standard/data/xml/namespace-affect-on-entity-ref-expansion-for-new-nodes.md).</span></span>  
  
 <span data-ttu-id="2b543-111">Yeni düğümler oluşturulduktan sonra ağacına eklemek kullanılabilecek çeşitli yöntemler vardır.</span><span class="sxs-lookup"><span data-stu-id="2b543-111">Once new nodes are created, there are several methods available to insert them into the tree.</span></span> <span data-ttu-id="2b543-112">Tablo, yeni düğümü XML belge nesne modeli (DOM) göründüğü açıklaması yöntemleriyle listeler.</span><span class="sxs-lookup"><span data-stu-id="2b543-112">The table lists the methods with a description of where the new node appears in the XML Document Object Model (DOM).</span></span>  
  
|<span data-ttu-id="2b543-113">Yöntem</span><span class="sxs-lookup"><span data-stu-id="2b543-113">Method</span></span>|<span data-ttu-id="2b543-114">Düğüm yerleştirme</span><span class="sxs-lookup"><span data-stu-id="2b543-114">Node placement</span></span>|  
|------------|--------------------|  
|<xref:System.Xml.XmlNode.InsertBefore%2A>|<span data-ttu-id="2b543-115">Referans düğümün önce eklenir.</span><span class="sxs-lookup"><span data-stu-id="2b543-115">Inserted before the reference node.</span></span> <span data-ttu-id="2b543-116">Örneğin, 5. konumda yeni düğüm eklemek için şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="2b543-116">For example, to insert the new node in position 5:</span></span><br /><br /> `Dim refChild As XmlNode = node.ChildNodes(4) 'The reference is zero-based.node.InsertBefore(newChild, refChild);`<br /><br /> `XmlNode refChild = node.ChildNodes[4]; //The reference is zero-based. node.InsertBefore(newChild, refChild);`<br /><br /> <span data-ttu-id="2b543-117">Daha fazla bilgi için bkz: <xref:System.Xml.XmlNode.InsertBefore%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2b543-117">For more information, see the <xref:System.Xml.XmlNode.InsertBefore%2A> method.</span></span>|  
|<xref:System.Xml.XmlNode.InsertAfter%2A>|<span data-ttu-id="2b543-118">Referans düğümün sonra eklenir.</span><span class="sxs-lookup"><span data-stu-id="2b543-118">Inserted after the reference node.</span></span> <span data-ttu-id="2b543-119">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="2b543-119">For example:</span></span><br /><br /> `node.InsertAfter(newChild, refChild)`<br /><br /> `node.InsertAfter(newChild, refChild);`<br /><br /> <span data-ttu-id="2b543-120">Daha fazla bilgi için bkz: <xref:System.Xml.XmlNode.InsertAfter%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2b543-120">For more information, see the <xref:System.Xml.XmlNode.InsertAfter%2A> method.</span></span>|  
|<xref:System.Xml.XmlNode.AppendChild%2A>|<span data-ttu-id="2b543-121">Düğümün alt düğümleri verilen düğüm için listesinin sonuna ekler.</span><span class="sxs-lookup"><span data-stu-id="2b543-121">Adds the node to the end of the list of child nodes for the given node.</span></span> <span data-ttu-id="2b543-122">Düğümü olan eklenir, bir <xref:System.Xml.XmlDocumentFragment>, belge parça tüm içeriğini bu düğümün alt listesine taşınır.</span><span class="sxs-lookup"><span data-stu-id="2b543-122">If the node being added is an <xref:System.Xml.XmlDocumentFragment>, the entire contents of the document fragment are moved into the child list of this node.</span></span> <span data-ttu-id="2b543-123">Daha fazla bilgi için bkz: <xref:System.Xml.XmlNode.AppendChild%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2b543-123">For more information, see the <xref:System.Xml.XmlNode.AppendChild%2A> method.</span></span>|  
|<xref:System.Xml.XmlNode.PrependChild%2A>|<span data-ttu-id="2b543-124">Düğüm belirtilen düğümün alt öğelerinin listesi başlangıcına ekler.</span><span class="sxs-lookup"><span data-stu-id="2b543-124">Adds the node to the beginning of the list of child nodes of the given node.</span></span> <span data-ttu-id="2b543-125">Düğümü olan eklenir, bir <xref:System.Xml.XmlDocumentFragment>, belge parça tüm içeriğini bu düğümün alt listesine taşınır.</span><span class="sxs-lookup"><span data-stu-id="2b543-125">If the node being added is an <xref:System.Xml.XmlDocumentFragment>, the entire contents of the document fragment are moved into the child list of this node.</span></span> <span data-ttu-id="2b543-126">Daha fazla bilgi için bkz: <xref:System.Xml.XmlNode.PrependChild%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2b543-126">For more information, see the <xref:System.Xml.XmlNode.PrependChild%2A> method.</span></span>|  
|<xref:System.Xml.XmlAttributeCollection.Append%2A>|<span data-ttu-id="2b543-127">Ekler bir <xref:System.Xml.XmlAttribute> sonuna kadar bir öğesiyle ilişkili öznitelik koleksiyonu düğümü.</span><span class="sxs-lookup"><span data-stu-id="2b543-127">Appends an <xref:System.Xml.XmlAttribute> node to the end of the attribute collection associated with an element.</span></span> <span data-ttu-id="2b543-128">Daha fazla bilgi için bkz: <xref:System.Xml.XmlAttributeCollection.Append%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2b543-128">For more information, see the <xref:System.Xml.XmlAttributeCollection.Append%2A> method.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2b543-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2b543-129">See Also</span></span>  
 [<span data-ttu-id="2b543-130">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="2b543-130">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
