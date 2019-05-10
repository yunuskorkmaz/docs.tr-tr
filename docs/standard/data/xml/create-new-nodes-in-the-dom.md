---
title: DOM’da Yeni Düğümler Oluşturma
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 6c2b9789-b61a-49f9-b33f-db01a945edf2
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 59ac88b2e7c6b3ecd4d06c0183a2f8a7f4a9e2d4
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64590259"
---
# <a name="create-new-nodes-in-the-dom"></a><span data-ttu-id="14162-102">DOM’da Yeni Düğümler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="14162-102">Create New Nodes in the DOM</span></span>
<span data-ttu-id="14162-103"><xref:System.Xml.XmlDocument> Tüm düğüm türü için bir oluşturma yöntemi vardır.</span><span class="sxs-lookup"><span data-stu-id="14162-103">The <xref:System.Xml.XmlDocument> has a create method for all of the node types.</span></span> <span data-ttu-id="14162-104">Gerekli olduğunda bir ada sahip yöntem sağlamanız ve içerik veya diğer parametreler (örneğin, bir metin düğümü) içeriğe sahip düğümleri ve düğüm için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="14162-104">Supply the method with a name when required, and content or other parameters for those nodes that have content (for example, a text node), and the node is created.</span></span> <span data-ttu-id="14162-105">Aşağıdaki yöntemlerden bir ada ihtiyacınız olanları ve uygun bir düğüm oluşturmak için doldurulmuş birkaç diğer parametreleri var.</span><span class="sxs-lookup"><span data-stu-id="14162-105">The following methods are ones that need a name and a few other parameters filled to create an appropriate node.</span></span>  
  
- <xref:System.Xml.XmlDocument.CreateCDataSection%2A>  
  
- <xref:System.Xml.XmlDocument.CreateComment%2A>  
  
- <xref:System.Xml.XmlDocument.CreateDocumentFragment%2A>  
  
- <xref:System.Xml.XmlDocument.CreateDocumentType%2A>  
  
- <xref:System.Xml.XmlDocument.CreateElement%2A>  
  
- <xref:System.Xml.XmlDocument.CreateNode%2A>  
  
- <xref:System.Xml.XmlDocument.CreateProcessingInstruction%2A>  
  
- <xref:System.Xml.XmlDocument.CreateSignificantWhitespace%2A>  
  
- <xref:System.Xml.XmlDocument.CreateTextNode%2A>  
  
- <xref:System.Xml.XmlDocument.CreateWhitespace%2A>  
  
- <xref:System.Xml.XmlDocument.CreateXmlDeclaration%2A>  
  
 <span data-ttu-id="14162-106">Diğer düğüm türleri yalnızca parametreleri için veri sağlama değerinden daha fazla gereksinimleri vardır.</span><span class="sxs-lookup"><span data-stu-id="14162-106">Other node types have more requirements than just providing data to parameters.</span></span>  
  
 <span data-ttu-id="14162-107">Öznitelikler hakkında daha fazla bilgi için bkz. [DOM öğeleri için yeni öznitelikler oluşturma](../../../../docs/standard/data/xml/creating-new-attributes-for-elements-in-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="14162-107">For information on attributes, see [Creating New Attributes for Elements in the DOM](../../../../docs/standard/data/xml/creating-new-attributes-for-elements-in-the-dom.md).</span></span> <span data-ttu-id="14162-108">Öğe ve öznitelik adı doğrulaması hakkında daha fazla bilgi için bkz: [XML öğesi ve öznitelik adı doğrulaması oluştururken, yeni düğümleri](../../../../docs/standard/data/xml/xml-element-and-attribute-name-verification-when-creating-new-nodes.md).</span><span class="sxs-lookup"><span data-stu-id="14162-108">For information on element and attribute name validation, see [XML Element and Attribute Name Verification when Creating New Nodes](../../../../docs/standard/data/xml/xml-element-and-attribute-name-verification-when-creating-new-nodes.md).</span></span> <span data-ttu-id="14162-109">Varlık başvuruları oluşturmak için bkz: [yeni öğe başvuruları oluşturma](../../../../docs/standard/data/xml/creating-new-entity-references.md).</span><span class="sxs-lookup"><span data-stu-id="14162-109">For creating entity references, see [Creating New Entity References](../../../../docs/standard/data/xml/creating-new-entity-references.md).</span></span> <span data-ttu-id="14162-110">Ad alanları genişletme ve varlık başvuruları nasıl etkilediği hakkında daha fazla bilgi için bkz: [Namespace etkiler içeren yeni düğümler öğeler ve öznitelikler için varlık başvurusu genişlemesine](../../../../docs/standard/data/xml/namespace-affect-on-entity-ref-expansion-for-new-nodes.md).</span><span class="sxs-lookup"><span data-stu-id="14162-110">For information on how namespaces affect the expansion of entity references, see [Namespace Affect on Entity Reference Expansion for New Nodes Containing Elements and Attributes](../../../../docs/standard/data/xml/namespace-affect-on-entity-ref-expansion-for-new-nodes.md).</span></span>  
  
 <span data-ttu-id="14162-111">Yeni düğümleri oluşturulduktan sonra bunları ağacına eklemek kullanılabilir olan çeşitli yöntemler vardır.</span><span class="sxs-lookup"><span data-stu-id="14162-111">Once new nodes are created, there are several methods available to insert them into the tree.</span></span> <span data-ttu-id="14162-112">Tabloda yeni bir düğüm XML belge nesne modeli (DOM) göründüğü açıklaması ile yöntemler listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="14162-112">The table lists the methods with a description of where the new node appears in the XML Document Object Model (DOM).</span></span>  
  
|<span data-ttu-id="14162-113">Yöntem</span><span class="sxs-lookup"><span data-stu-id="14162-113">Method</span></span>|<span data-ttu-id="14162-114">Düğüm yerleştirme</span><span class="sxs-lookup"><span data-stu-id="14162-114">Node placement</span></span>|  
|------------|--------------------|  
|<xref:System.Xml.XmlNode.InsertBefore%2A>|<span data-ttu-id="14162-115">Referans düğümün önce eklenmiş.</span><span class="sxs-lookup"><span data-stu-id="14162-115">Inserted before the reference node.</span></span> <span data-ttu-id="14162-116">Örneğin, 5 konumda yeni düğümü eklemek için şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="14162-116">For example, to insert the new node in position 5:</span></span><br /><br /> `Dim refChild As XmlNode = node.ChildNodes(4) 'The reference is zero-based.node.InsertBefore(newChild, refChild);`<br /><br /> `XmlNode refChild = node.ChildNodes[4]; //The reference is zero-based. node.InsertBefore(newChild, refChild);`<br /><br /> <span data-ttu-id="14162-117">Daha fazla bilgi için <xref:System.Xml.XmlNode.InsertBefore%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="14162-117">For more information, see the <xref:System.Xml.XmlNode.InsertBefore%2A> method.</span></span>|  
|<xref:System.Xml.XmlNode.InsertAfter%2A>|<span data-ttu-id="14162-118">Referans düğümün sonra eklenir.</span><span class="sxs-lookup"><span data-stu-id="14162-118">Inserted after the reference node.</span></span> <span data-ttu-id="14162-119">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="14162-119">For example:</span></span><br /><br /> `node.InsertAfter(newChild, refChild)`<br /><br /> `node.InsertAfter(newChild, refChild);`<br /><br /> <span data-ttu-id="14162-120">Daha fazla bilgi için <xref:System.Xml.XmlNode.InsertAfter%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="14162-120">For more information, see the <xref:System.Xml.XmlNode.InsertAfter%2A> method.</span></span>|  
|<xref:System.Xml.XmlNode.AppendChild%2A>|<span data-ttu-id="14162-121">Düğüm belirtilen düğümün alt düğümü listesinin sonuna ekler.</span><span class="sxs-lookup"><span data-stu-id="14162-121">Adds the node to the end of the list of child nodes for the given node.</span></span> <span data-ttu-id="14162-122">Olan düğüm eklendiğinde, bir <xref:System.Xml.XmlDocumentFragment>, belge parça öğesinin tüm içeriğini bu düğümün alt listesine taşınır.</span><span class="sxs-lookup"><span data-stu-id="14162-122">If the node being added is an <xref:System.Xml.XmlDocumentFragment>, the entire contents of the document fragment are moved into the child list of this node.</span></span> <span data-ttu-id="14162-123">Daha fazla bilgi için <xref:System.Xml.XmlNode.AppendChild%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="14162-123">For more information, see the <xref:System.Xml.XmlNode.AppendChild%2A> method.</span></span>|  
|<xref:System.Xml.XmlNode.PrependChild%2A>|<span data-ttu-id="14162-124">Düğüm başına verilen düğüm alt düğüm listesi ekler.</span><span class="sxs-lookup"><span data-stu-id="14162-124">Adds the node to the beginning of the list of child nodes of the given node.</span></span> <span data-ttu-id="14162-125">Olan düğüm eklendiğinde, bir <xref:System.Xml.XmlDocumentFragment>, belge parça öğesinin tüm içeriğini bu düğümün alt listesine taşınır.</span><span class="sxs-lookup"><span data-stu-id="14162-125">If the node being added is an <xref:System.Xml.XmlDocumentFragment>, the entire contents of the document fragment are moved into the child list of this node.</span></span> <span data-ttu-id="14162-126">Daha fazla bilgi için <xref:System.Xml.XmlNode.PrependChild%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="14162-126">For more information, see the <xref:System.Xml.XmlNode.PrependChild%2A> method.</span></span>|  
|<xref:System.Xml.XmlAttributeCollection.Append%2A>|<span data-ttu-id="14162-127">Ekler bir <xref:System.Xml.XmlAttribute> sonuna bir öğe ile ilgili öznitelik koleksiyonu düğümü.</span><span class="sxs-lookup"><span data-stu-id="14162-127">Appends an <xref:System.Xml.XmlAttribute> node to the end of the attribute collection associated with an element.</span></span> <span data-ttu-id="14162-128">Daha fazla bilgi için <xref:System.Xml.XmlAttributeCollection.Append%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="14162-128">For more information, see the <xref:System.Xml.XmlAttributeCollection.Append%2A> method.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="14162-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="14162-129">See also</span></span>

- [<span data-ttu-id="14162-130">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="14162-130">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
