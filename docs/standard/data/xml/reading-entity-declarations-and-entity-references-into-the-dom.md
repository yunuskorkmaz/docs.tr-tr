---
description: "Hakkında daha fazla bilgi edinin: DOM 'a varlık bildirimleri ve varlık başvuruları okuma"
title: DOM’da Varlık Bildirimleri ve Varlık Başvuruları Okuma
ms.date: 03/30/2017
ms.assetid: 86dba977-5cc4-4567-964f-027ffabc47b2
ms.openlocfilehash: 312fd215076f4b0eee280767b8c367d34ffe6bb6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783228"
---
# <a name="reading-entity-declarations-and-entity-references-into-the-dom"></a><span data-ttu-id="2dc76-103">DOM’da Varlık Bildirimleri ve Varlık Başvuruları Okuma</span><span class="sxs-lookup"><span data-stu-id="2dc76-103">Reading Entity Declarations and Entity References into the DOM</span></span>

<span data-ttu-id="2dc76-104">Varlık, içerik veya biçimlendirme yerine XML 'de kullanılacak adı belirten bir bildirimidir.</span><span class="sxs-lookup"><span data-stu-id="2dc76-104">An entity is a declaration that states a name to be used in the XML in place of content or markup.</span></span> <span data-ttu-id="2dc76-105">Varlıkların iki bölümü vardır.</span><span class="sxs-lookup"><span data-stu-id="2dc76-105">There are two parts to entities.</span></span> <span data-ttu-id="2dc76-106">İlk olarak, bir varlık bildirimi kullanarak bir adı değiştirme içeriğine bağlamamalısınız.</span><span class="sxs-lookup"><span data-stu-id="2dc76-106">First, you must tie a name to the replacement content using an entity declaration.</span></span> <span data-ttu-id="2dc76-107">Bir varlık bildirimi, `<!ENTITY name "value">` bir belge türü tanımı (DTD) veya XML şemasında sözdizimi kullanılarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="2dc76-107">An entity declaration is created by using the `<!ENTITY name "value">` syntax in a document type definition (DTD) or XML schema.</span></span> <span data-ttu-id="2dc76-108">İkinci olarak, varlık bildiriminde tanımlanan ad daha sonra XML 'de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2dc76-108">Secondly, the name defined in the entity declaration is subsequently used in the XML.</span></span> <span data-ttu-id="2dc76-109">XML 'de kullanıldığında, bir varlık başvurusu olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="2dc76-109">When used in the XML, it is called an entity reference.</span></span> <span data-ttu-id="2dc76-110">Örneğin, aşağıdaki varlık bildirimi `publisher` "Microsoft Press" içeriğiyle ilişkili olan adın bir varlığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="2dc76-110">For example, the following entity declaration declares an entity of the name `publisher` being associated with the content of "Microsoft Press".</span></span>  
  
```xml  
<!ENTITY publisher "Microsoft Press">  
```  
  
 <span data-ttu-id="2dc76-111">Aşağıdaki örnek bir varlık başvurusu olarak XML 'de bu varlık bildiriminin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2dc76-111">The following example shows the use of this entity declaration in XML as an entity reference.</span></span>  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 <span data-ttu-id="2dc76-112">Bazı çözümleyiciler, bir belge belleğe yüklendiğinde varlıkları otomatik olarak genişletir.</span><span class="sxs-lookup"><span data-stu-id="2dc76-112">Some parsers automatically expand entities when a document is loaded into memory.</span></span> <span data-ttu-id="2dc76-113">Bu nedenle, XML belleğe okunmakta olduğunda, varlık bildirimleri hatırlanır ve kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="2dc76-113">Therefore, when the XML is being read into memory, entity declarations are remembered and saved.</span></span> <span data-ttu-id="2dc76-114">Ayrıştırıcı daha sonra `&;` genel bir varlık başvurusunu tanımlayan karakterlerle karşılaştığında, ayrıştırıcı bu adı bir varlık bildirim tablosunda arar.</span><span class="sxs-lookup"><span data-stu-id="2dc76-114">When the parser subsequently encounters `&;` characters, which identify a general entity reference, the parser looks up that name in an entity declaration table.</span></span> <span data-ttu-id="2dc76-115">Başvuru, `&publisher;` gösterdiği içerikle değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="2dc76-115">The reference, `&publisher;` is replaced by the content that it represents.</span></span> <span data-ttu-id="2dc76-116">Aşağıdaki XML 'i kullanarak</span><span class="sxs-lookup"><span data-stu-id="2dc76-116">Using the following XML,</span></span>  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 <span data-ttu-id="2dc76-117">varlık başvurusunu genişletmek ve `&publisher;` Microsoft Press içeriğiyle değiştirmek, aşağıdaki GENIŞLETILMIŞ XML 'yi sağlar.</span><span class="sxs-lookup"><span data-stu-id="2dc76-117">expanding the entity reference and replacing the `&publisher;` with the Microsoft Press content gives the following expanded XML.</span></span>  
  
 <span data-ttu-id="2dc76-118">**Çıktı**</span><span class="sxs-lookup"><span data-stu-id="2dc76-118">**Output**</span></span>  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by Microsoft Press</pubinfo>  
```  
  
 <span data-ttu-id="2dc76-119">Birçok varlık türü vardır.</span><span class="sxs-lookup"><span data-stu-id="2dc76-119">There are many kinds of entities.</span></span> <span data-ttu-id="2dc76-120">Aşağıdaki diyagramda, varlık türlerinin ve terminolojinin dökümü gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2dc76-120">The following diagram shows the breakdown of entity types and terminology.</span></span>  
  
 <span data-ttu-id="2dc76-121">![varlık türü hiyerarşisinin akış grafiği](media/entity-hierarchy.gif "Entity_hierarchy")</span><span class="sxs-lookup"><span data-stu-id="2dc76-121">![flow chart of entity type hierarchy](media/entity-hierarchy.gif "Entity_hierarchy")</span></span>  
  
 <span data-ttu-id="2dc76-122">XML Belge Nesne Modeli (DOM) Microsoft .NET Framework uygulamasının varsayılan örneği, varlıkların başvurularını korumasıdır ve XML yüklendiğinde varlıkları genişletmez.</span><span class="sxs-lookup"><span data-stu-id="2dc76-122">The default for the Microsoft .NET Framework implementation of the XML Document Object Model (DOM) is to preserve the entities references and not expand the entities when the XML is loaded.</span></span> <span data-ttu-id="2dc76-123">Bu, DOM 'da bir belge yüklendiği için,  `&publisher;` DTD 'de bildirildiği varlıktaki içeriği temsil eden alt düğümler ile başvuru değişkenini içeren bir XmlEntityReference düğümü oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="2dc76-123">The implication of this is that as a document is loaded in the DOM, an **XmlEntityReference** node containing the reference variable `&publisher;` is created, with child nodes representing the content in the entity declared in the DTD.</span></span>  
  
 <span data-ttu-id="2dc76-124">`<!ENTITY publisher "Microsoft Press">`Varlık bildirimini kullanarak, aşağıdaki diyagramda bu bildirimden oluşturulan **XmlEntity** ve **XmlText** düğümleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2dc76-124">Using the `<!ENTITY publisher "Microsoft Press">` entity declaration, the following diagram shows the **XmlEntity** and **XmlText** nodes created from this declaration.</span></span>  
  
 <span data-ttu-id="2dc76-125">![varlık bildiriminden oluşturulan düğümler](media/xml-entitydeclaration-node2.png "xml_entitydeclaration_node2")</span><span class="sxs-lookup"><span data-stu-id="2dc76-125">![nodes created from entity declaration](media/xml-entitydeclaration-node2.png "xml_entitydeclaration_node2")</span></span>  
  
 <span data-ttu-id="2dc76-126">Varlık başvurularının genişletilme ve bu durumlarda, DOM ağacında bellek içinde oluşturulan düğümlerin bir farkı olmayan farklar.</span><span class="sxs-lookup"><span data-stu-id="2dc76-126">The differences when entity references are expanded and when they are not makes a difference in what nodes are generated in the DOM tree, in memory.</span></span> <span data-ttu-id="2dc76-127">Oluşturulan düğümlerdeki fark, [varlık başvuruları korunur](entity-references-are-preserved.md) ve [varlık başvuruları genişletilir ve korunmaz](entity-references-are-expanded-and-not-preserved.md).</span><span class="sxs-lookup"><span data-stu-id="2dc76-127">The difference in the nodes that are generated is explained in the topics [Entity References are Preserved](entity-references-are-preserved.md) and [Entity References are Expanded and Not Preserved](entity-references-are-expanded-and-not-preserved.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2dc76-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2dc76-128">See also</span></span>

- [<span data-ttu-id="2dc76-129">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="2dc76-129">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
