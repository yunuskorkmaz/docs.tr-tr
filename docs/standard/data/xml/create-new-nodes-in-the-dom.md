---
title: DOM’da Yeni Düğümler Oluşturma
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 6c2b9789-b61a-49f9-b33f-db01a945edf2
ms.openlocfilehash: d99a3c68c7554ab266d71a4cbf2e676bc6db8cbc
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289583"
---
# <a name="create-new-nodes-in-the-dom"></a><span data-ttu-id="0024c-102">DOM’da Yeni Düğümler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="0024c-102">Create New Nodes in the DOM</span></span>
<span data-ttu-id="0024c-103"><xref:System.Xml.XmlDocument>Tüm düğüm türleri için oluşturma yöntemine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="0024c-103">The <xref:System.Xml.XmlDocument> has a create method for all of the node types.</span></span> <span data-ttu-id="0024c-104">Gerektiğinde bir ada sahip bir ad ve içerik veya diğer parametre (örneğin, bir metin düğümü) ve düğüm oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="0024c-104">Supply the method with a name when required, and content or other parameters for those nodes that have content (for example, a text node), and the node is created.</span></span> <span data-ttu-id="0024c-105">Aşağıdaki yöntemler, uygun bir düğüm oluşturmak için bir ada ve diğer birkaç parametreye sahip olması gereken değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="0024c-105">The following methods are ones that need a name and a few other parameters filled to create an appropriate node.</span></span>  
  
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
  
 <span data-ttu-id="0024c-106">Diğer düğüm türleri yalnızca parametrelere veri sağlamaktan daha fazla gereksinimlere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="0024c-106">Other node types have more requirements than just providing data to parameters.</span></span>  
  
 <span data-ttu-id="0024c-107">Öznitelikler hakkında bilgi için bkz. [Dom 'Daki öğeler Için yeni öznitelikler oluşturma](creating-new-attributes-for-elements-in-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="0024c-107">For information on attributes, see [Creating New Attributes for Elements in the DOM](creating-new-attributes-for-elements-in-the-dom.md).</span></span> <span data-ttu-id="0024c-108">Öğe ve öznitelik adı doğrulama hakkında bilgi için, bkz. [yeni düğümler oluştururken XML öğesi ve öznitelik adı doğrulama](xml-element-and-attribute-name-verification-when-creating-new-nodes.md).</span><span class="sxs-lookup"><span data-stu-id="0024c-108">For information on element and attribute name validation, see [XML Element and Attribute Name Verification when Creating New Nodes](xml-element-and-attribute-name-verification-when-creating-new-nodes.md).</span></span> <span data-ttu-id="0024c-109">Varlık başvuruları oluşturmak için, bkz. [yeni varlık başvuruları oluşturma](creating-new-entity-references.md).</span><span class="sxs-lookup"><span data-stu-id="0024c-109">For creating entity references, see [Creating New Entity References](creating-new-entity-references.md).</span></span> <span data-ttu-id="0024c-110">Ad alanlarının varlık başvurularını genişletmesinin nasıl etkilediği hakkında daha fazla bilgi için, bkz. [öğeleri ve öznitelikleri Içeren yeni düğümler Için varlık başvurusu genişletmesi üzerinde ad alanı etkileri](namespace-affect-on-entity-ref-expansion-for-new-nodes.md).</span><span class="sxs-lookup"><span data-stu-id="0024c-110">For information on how namespaces affect the expansion of entity references, see [Namespace Affect on Entity Reference Expansion for New Nodes Containing Elements and Attributes](namespace-affect-on-entity-ref-expansion-for-new-nodes.md).</span></span>  
  
 <span data-ttu-id="0024c-111">Yeni düğümler oluşturulduktan sonra ağaca eklemek için kullanabileceğiniz çeşitli yöntemler vardır.</span><span class="sxs-lookup"><span data-stu-id="0024c-111">Once new nodes are created, there are several methods available to insert them into the tree.</span></span> <span data-ttu-id="0024c-112">Tabloda, yeni düğümün XML Belge Nesne Modeli (DOM) içinde göründüğü bir açıklama ile Yöntemler listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="0024c-112">The table lists the methods with a description of where the new node appears in the XML Document Object Model (DOM).</span></span>  
  
|<span data-ttu-id="0024c-113">Yöntem</span><span class="sxs-lookup"><span data-stu-id="0024c-113">Method</span></span>|<span data-ttu-id="0024c-114">Düğüm yerleşimi</span><span class="sxs-lookup"><span data-stu-id="0024c-114">Node placement</span></span>|  
|------------|--------------------|  
|<xref:System.Xml.XmlNode.InsertBefore%2A>|<span data-ttu-id="0024c-115">Başvuru düğümünden önce eklenirler.</span><span class="sxs-lookup"><span data-stu-id="0024c-115">Inserted before the reference node.</span></span> <span data-ttu-id="0024c-116">Örneğin, konum 5 ' te yeni düğümü eklemek için:</span><span class="sxs-lookup"><span data-stu-id="0024c-116">For example, to insert the new node in position 5:</span></span><br /><br /> `Dim refChild As XmlNode = node.ChildNodes(4) 'The reference is zero-based.node.InsertBefore(newChild, refChild);`<br /><br /> `XmlNode refChild = node.ChildNodes[4]; //The reference is zero-based. node.InsertBefore(newChild, refChild);`<br /><br /> <span data-ttu-id="0024c-117">Daha fazla bilgi için bkz <xref:System.Xml.XmlNode.InsertBefore%2A> . yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0024c-117">For more information, see the <xref:System.Xml.XmlNode.InsertBefore%2A> method.</span></span>|  
|<xref:System.Xml.XmlNode.InsertAfter%2A>|<span data-ttu-id="0024c-118">Başvuru düğümünden sonra eklenirler.</span><span class="sxs-lookup"><span data-stu-id="0024c-118">Inserted after the reference node.</span></span> <span data-ttu-id="0024c-119">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="0024c-119">For example:</span></span><br /><br /> `node.InsertAfter(newChild, refChild)`<br /><br /> `node.InsertAfter(newChild, refChild);`<br /><br /> <span data-ttu-id="0024c-120">Daha fazla bilgi için bkz <xref:System.Xml.XmlNode.InsertAfter%2A> . yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0024c-120">For more information, see the <xref:System.Xml.XmlNode.InsertAfter%2A> method.</span></span>|  
|<xref:System.Xml.XmlNode.AppendChild%2A>|<span data-ttu-id="0024c-121">Düğümü, verilen düğüm için alt düğümler listesinin sonuna ekler.</span><span class="sxs-lookup"><span data-stu-id="0024c-121">Adds the node to the end of the list of child nodes for the given node.</span></span> <span data-ttu-id="0024c-122">Eklenen düğüm bir ise <xref:System.Xml.XmlDocumentFragment> , belge parçasının tüm içeriği bu düğümün alt listesine taşınır.</span><span class="sxs-lookup"><span data-stu-id="0024c-122">If the node being added is an <xref:System.Xml.XmlDocumentFragment>, the entire contents of the document fragment are moved into the child list of this node.</span></span> <span data-ttu-id="0024c-123">Daha fazla bilgi için bkz <xref:System.Xml.XmlNode.AppendChild%2A> . yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0024c-123">For more information, see the <xref:System.Xml.XmlNode.AppendChild%2A> method.</span></span>|  
|<xref:System.Xml.XmlNode.PrependChild%2A>|<span data-ttu-id="0024c-124">Düğümü, belirtilen düğümün alt düğümleri listesinin başına ekler.</span><span class="sxs-lookup"><span data-stu-id="0024c-124">Adds the node to the beginning of the list of child nodes of the given node.</span></span> <span data-ttu-id="0024c-125">Eklenen düğüm bir ise <xref:System.Xml.XmlDocumentFragment> , belge parçasının tüm içeriği bu düğümün alt listesine taşınır.</span><span class="sxs-lookup"><span data-stu-id="0024c-125">If the node being added is an <xref:System.Xml.XmlDocumentFragment>, the entire contents of the document fragment are moved into the child list of this node.</span></span> <span data-ttu-id="0024c-126">Daha fazla bilgi için bkz <xref:System.Xml.XmlNode.PrependChild%2A> . yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0024c-126">For more information, see the <xref:System.Xml.XmlNode.PrependChild%2A> method.</span></span>|  
|<xref:System.Xml.XmlAttributeCollection.Append%2A>|<span data-ttu-id="0024c-127"><xref:System.Xml.XmlAttribute>Bir öğe ile ilişkili öznitelik koleksiyonunun sonuna bir düğüm ekler.</span><span class="sxs-lookup"><span data-stu-id="0024c-127">Appends an <xref:System.Xml.XmlAttribute> node to the end of the attribute collection associated with an element.</span></span> <span data-ttu-id="0024c-128">Daha fazla bilgi için bkz <xref:System.Xml.XmlAttributeCollection.Append%2A> . yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0024c-128">For more information, see the <xref:System.Xml.XmlAttributeCollection.Append%2A> method.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0024c-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0024c-129">See also</span></span>

- [<span data-ttu-id="0024c-130">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="0024c-130">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
