---
title: DOM’da Varlık Bildirimleri ve Varlık Başvuruları Okuma
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 86dba977-5cc4-4567-964f-027ffabc47b2
ms.openlocfilehash: fa650e75d7661eeafea74146f5cbb61878978575
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710407"
---
# <a name="reading-entity-declarations-and-entity-references-into-the-dom"></a><span data-ttu-id="06b36-102">DOM’da Varlık Bildirimleri ve Varlık Başvuruları Okuma</span><span class="sxs-lookup"><span data-stu-id="06b36-102">Reading Entity Declarations and Entity References into the DOM</span></span>
<span data-ttu-id="06b36-103">Varlık, içerik veya biçimlendirme yerine XML 'de kullanılacak adı belirten bir bildirimidir.</span><span class="sxs-lookup"><span data-stu-id="06b36-103">An entity is a declaration that states a name to be used in the XML in place of content or markup.</span></span> <span data-ttu-id="06b36-104">Varlıkların iki bölümü vardır.</span><span class="sxs-lookup"><span data-stu-id="06b36-104">There are two parts to entities.</span></span> <span data-ttu-id="06b36-105">İlk olarak, bir varlık bildirimi kullanarak bir adı değiştirme içeriğine bağlamamalısınız.</span><span class="sxs-lookup"><span data-stu-id="06b36-105">First, you must tie a name to the replacement content using an entity declaration.</span></span> <span data-ttu-id="06b36-106">Bir varlık bildirimi, bir belge türü tanımı `<!ENTITY name "value">` (DTD) veya XML şemasında sözdizimi kullanılarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="06b36-106">An entity declaration is created by using the `<!ENTITY name "value">` syntax in a document type definition (DTD) or XML schema.</span></span> <span data-ttu-id="06b36-107">İkinci olarak, varlık bildiriminde tanımlanan ad daha sonra XML 'de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="06b36-107">Secondly, the name defined in the entity declaration is subsequently used in the XML.</span></span> <span data-ttu-id="06b36-108">XML 'de kullanıldığında, bir varlık başvurusu olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="06b36-108">When used in the XML, it is called an entity reference.</span></span> <span data-ttu-id="06b36-109">Örneğin, aşağıdaki varlık bildirimi "Microsoft Press" içeriğiyle ilişkili olan adın `publisher` bir varlığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="06b36-109">For example, the following entity declaration declares an entity of the name `publisher` being associated with the content of "Microsoft Press".</span></span>  
  
```xml  
<!ENTITY publisher "Microsoft Press">  
```  
  
 <span data-ttu-id="06b36-110">Aşağıdaki örnek bir varlık başvurusu olarak XML 'de bu varlık bildiriminin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="06b36-110">The following example shows the use of this entity declaration in XML as an entity reference.</span></span>  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 <span data-ttu-id="06b36-111">Bazı çözümleyiciler, bir belge belleğe yüklendiğinde varlıkları otomatik olarak genişletir.</span><span class="sxs-lookup"><span data-stu-id="06b36-111">Some parsers automatically expand entities when a document is loaded into memory.</span></span> <span data-ttu-id="06b36-112">Bu nedenle, XML belleğe okunmakta olduğunda, varlık bildirimleri hatırlanır ve kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="06b36-112">Therefore, when the XML is being read into memory, entity declarations are remembered and saved.</span></span> <span data-ttu-id="06b36-113">Ayrıştırıcı daha sonra genel bir `&;` varlık başvurusunu tanımlayan karakterlerle karşılaştığında, ayrıştırıcı bu adı bir varlık bildirim tablosunda arar.</span><span class="sxs-lookup"><span data-stu-id="06b36-113">When the parser subsequently encounters `&;` characters, which identify a general entity reference, the parser looks up that name in an entity declaration table.</span></span> <span data-ttu-id="06b36-114">Başvuru, `&publisher;` gösterdiği içerikle değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="06b36-114">The reference, `&publisher;` is replaced by the content that it represents.</span></span> <span data-ttu-id="06b36-115">Aşağıdaki XML 'i kullanarak</span><span class="sxs-lookup"><span data-stu-id="06b36-115">Using the following XML,</span></span>  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 <span data-ttu-id="06b36-116">varlık başvurusunu genişletmek ve Microsoft Press içeriğiyle `&publisher;` değiştirmek, AŞAĞıDAKI Genişletilmiş XML 'yi sağlar.</span><span class="sxs-lookup"><span data-stu-id="06b36-116">expanding the entity reference and replacing the `&publisher;` with the Microsoft Press content gives the following expanded XML.</span></span>  
  
 <span data-ttu-id="06b36-117">**Çıktı**</span><span class="sxs-lookup"><span data-stu-id="06b36-117">**Output**</span></span>  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by Microsoft Press</pubinfo>  
```  
  
 <span data-ttu-id="06b36-118">Birçok varlık türü vardır.</span><span class="sxs-lookup"><span data-stu-id="06b36-118">There are many kinds of entities.</span></span> <span data-ttu-id="06b36-119">Aşağıdaki diyagramda, varlık türlerinin ve terminolojinin dökümü gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="06b36-119">The following diagram shows the breakdown of entity types and terminology.</span></span>  
  
 <span data-ttu-id="06b36-120">![varlık türü hiyerarşisinin akış grafiği](../../../../docs/standard/data/xml/media/entity-hierarchy.gif "Entity_hierarchy")</span><span class="sxs-lookup"><span data-stu-id="06b36-120">![flow chart of entity type hierarchy](../../../../docs/standard/data/xml/media/entity-hierarchy.gif "Entity_hierarchy")</span></span>  
  
 <span data-ttu-id="06b36-121">XML Belge Nesne Modeli (DOM) Microsoft .NET Framework uygulamasının varsayılan örneği, varlıkların başvurularını korumasıdır ve XML yüklendiğinde varlıkları genişletmez.</span><span class="sxs-lookup"><span data-stu-id="06b36-121">The default for the Microsoft .NET Framework implementation of the XML Document Object Model (DOM) is to preserve the entities references and not expand the entities when the XML is loaded.</span></span> <span data-ttu-id="06b36-122">Bu, DOM 'da bir belge yüklendiği için, DTD 'de bildirildiği varlıktaki içeriği temsil eden alt **XmlEntityReference** düğümler ile başvuru değişkenini `&publisher;` içeren bir XmlEntityReference düğümü oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="06b36-122">The implication of this is that as a document is loaded in the DOM, an **XmlEntityReference** node containing the reference variable `&publisher;` is created, with child nodes representing the content in the entity declared in the DTD.</span></span>  
  
 <span data-ttu-id="06b36-123">`<!ENTITY publisher "Microsoft Press">` Varlık bildirimini kullanarak, aşağıdaki diyagramda bu bildirimden oluşturulan **XmlEntity** ve **XmlText** düğümleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="06b36-123">Using the `<!ENTITY publisher "Microsoft Press">` entity declaration, the following diagram shows the **XmlEntity** and **XmlText** nodes created from this declaration.</span></span>  
  
 <span data-ttu-id="06b36-124">![varlık bildiriminden oluşturulan düğümler](../../../../docs/standard/data/xml/media/xml-entitydeclaration-node2.png "xml_entitydeclaration_node2")</span><span class="sxs-lookup"><span data-stu-id="06b36-124">![nodes created from entity declaration](../../../../docs/standard/data/xml/media/xml-entitydeclaration-node2.png "xml_entitydeclaration_node2")</span></span>  
  
 <span data-ttu-id="06b36-125">Varlık başvurularının genişletilme ve bu durumlarda, DOM ağacında bellek içinde oluşturulan düğümlerin bir farkı olmayan farklar.</span><span class="sxs-lookup"><span data-stu-id="06b36-125">The differences when entity references are expanded and when they are not makes a difference in what nodes are generated in the DOM tree, in memory.</span></span> <span data-ttu-id="06b36-126">Oluşturulan düğümlerdeki fark, [varlık başvuruları korunur](../../../../docs/standard/data/xml/entity-references-are-preserved.md) ve [varlık başvuruları genişletilir ve korunmaz](../../../../docs/standard/data/xml/entity-references-are-expanded-and-not-preserved.md).</span><span class="sxs-lookup"><span data-stu-id="06b36-126">The difference in the nodes that are generated is explained in the topics [Entity References are Preserved](../../../../docs/standard/data/xml/entity-references-are-preserved.md) and [Entity References are Expanded and Not Preserved](../../../../docs/standard/data/xml/entity-references-are-expanded-and-not-preserved.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06b36-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="06b36-127">See also</span></span>

- [<span data-ttu-id="06b36-128">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="06b36-128">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
