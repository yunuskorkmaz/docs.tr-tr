---
title: DOM’da Varlık Bildirimleri ve Varlık Başvuruları Okuma
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 86dba977-5cc4-4567-964f-027ffabc47b2
ms.openlocfilehash: 41d88de9ee988a29c54c6e2c6c437963b9f79cf8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289882"
---
# <a name="reading-entity-declarations-and-entity-references-into-the-dom"></a><span data-ttu-id="4083c-102">DOM’da Varlık Bildirimleri ve Varlık Başvuruları Okuma</span><span class="sxs-lookup"><span data-stu-id="4083c-102">Reading Entity Declarations and Entity References into the DOM</span></span>
<span data-ttu-id="4083c-103">Varlık, içerik veya biçimlendirme yerine XML 'de kullanılacak adı belirten bir bildirimidir.</span><span class="sxs-lookup"><span data-stu-id="4083c-103">An entity is a declaration that states a name to be used in the XML in place of content or markup.</span></span> <span data-ttu-id="4083c-104">Varlıkların iki bölümü vardır.</span><span class="sxs-lookup"><span data-stu-id="4083c-104">There are two parts to entities.</span></span> <span data-ttu-id="4083c-105">İlk olarak, bir varlık bildirimi kullanarak bir adı değiştirme içeriğine bağlamamalısınız.</span><span class="sxs-lookup"><span data-stu-id="4083c-105">First, you must tie a name to the replacement content using an entity declaration.</span></span> <span data-ttu-id="4083c-106">Bir varlık bildirimi, `<!ENTITY name "value">` bir belge türü tanımı (DTD) veya XML şemasında sözdizimi kullanılarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="4083c-106">An entity declaration is created by using the `<!ENTITY name "value">` syntax in a document type definition (DTD) or XML schema.</span></span> <span data-ttu-id="4083c-107">İkinci olarak, varlık bildiriminde tanımlanan ad daha sonra XML 'de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4083c-107">Secondly, the name defined in the entity declaration is subsequently used in the XML.</span></span> <span data-ttu-id="4083c-108">XML 'de kullanıldığında, bir varlık başvurusu olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="4083c-108">When used in the XML, it is called an entity reference.</span></span> <span data-ttu-id="4083c-109">Örneğin, aşağıdaki varlık bildirimi `publisher` "Microsoft Press" içeriğiyle ilişkili olan adın bir varlığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="4083c-109">For example, the following entity declaration declares an entity of the name `publisher` being associated with the content of "Microsoft Press".</span></span>  
  
```xml  
<!ENTITY publisher "Microsoft Press">  
```  
  
 <span data-ttu-id="4083c-110">Aşağıdaki örnek bir varlık başvurusu olarak XML 'de bu varlık bildiriminin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="4083c-110">The following example shows the use of this entity declaration in XML as an entity reference.</span></span>  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 <span data-ttu-id="4083c-111">Bazı çözümleyiciler, bir belge belleğe yüklendiğinde varlıkları otomatik olarak genişletir.</span><span class="sxs-lookup"><span data-stu-id="4083c-111">Some parsers automatically expand entities when a document is loaded into memory.</span></span> <span data-ttu-id="4083c-112">Bu nedenle, XML belleğe okunmakta olduğunda, varlık bildirimleri hatırlanır ve kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="4083c-112">Therefore, when the XML is being read into memory, entity declarations are remembered and saved.</span></span> <span data-ttu-id="4083c-113">Ayrıştırıcı daha sonra `&;` genel bir varlık başvurusunu tanımlayan karakterlerle karşılaştığında, ayrıştırıcı bu adı bir varlık bildirim tablosunda arar.</span><span class="sxs-lookup"><span data-stu-id="4083c-113">When the parser subsequently encounters `&;` characters, which identify a general entity reference, the parser looks up that name in an entity declaration table.</span></span> <span data-ttu-id="4083c-114">Başvuru, `&publisher;` gösterdiği içerikle değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="4083c-114">The reference, `&publisher;` is replaced by the content that it represents.</span></span> <span data-ttu-id="4083c-115">Aşağıdaki XML 'i kullanarak</span><span class="sxs-lookup"><span data-stu-id="4083c-115">Using the following XML,</span></span>  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 <span data-ttu-id="4083c-116">varlık başvurusunu genişletmek ve `&publisher;` Microsoft Press içeriğiyle değiştirmek, aşağıdaki GENIŞLETILMIŞ XML 'yi sağlar.</span><span class="sxs-lookup"><span data-stu-id="4083c-116">expanding the entity reference and replacing the `&publisher;` with the Microsoft Press content gives the following expanded XML.</span></span>  
  
 <span data-ttu-id="4083c-117">**Çıktı**</span><span class="sxs-lookup"><span data-stu-id="4083c-117">**Output**</span></span>  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by Microsoft Press</pubinfo>  
```  
  
 <span data-ttu-id="4083c-118">Birçok varlık türü vardır.</span><span class="sxs-lookup"><span data-stu-id="4083c-118">There are many kinds of entities.</span></span> <span data-ttu-id="4083c-119">Aşağıdaki diyagramda, varlık türlerinin ve terminolojinin dökümü gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="4083c-119">The following diagram shows the breakdown of entity types and terminology.</span></span>  
  
 <span data-ttu-id="4083c-120">![varlık türü hiyerarşisinin akış grafiği](media/entity-hierarchy.gif "Entity_hierarchy")</span><span class="sxs-lookup"><span data-stu-id="4083c-120">![flow chart of entity type hierarchy](media/entity-hierarchy.gif "Entity_hierarchy")</span></span>  
  
 <span data-ttu-id="4083c-121">XML Belge Nesne Modeli (DOM) Microsoft .NET Framework uygulamasının varsayılan örneği, varlıkların başvurularını korumasıdır ve XML yüklendiğinde varlıkları genişletmez.</span><span class="sxs-lookup"><span data-stu-id="4083c-121">The default for the Microsoft .NET Framework implementation of the XML Document Object Model (DOM) is to preserve the entities references and not expand the entities when the XML is loaded.</span></span> <span data-ttu-id="4083c-122">Bu, DOM 'da bir belge yüklendiği için, **XmlEntityReference** `&publisher;` DTD 'de bildirildiği varlıktaki içeriği temsil eden alt düğümler ile başvuru değişkenini içeren bir XmlEntityReference düğümü oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="4083c-122">The implication of this is that as a document is loaded in the DOM, an **XmlEntityReference** node containing the reference variable `&publisher;` is created, with child nodes representing the content in the entity declared in the DTD.</span></span>  
  
 <span data-ttu-id="4083c-123">`<!ENTITY publisher "Microsoft Press">`Varlık bildirimini kullanarak, aşağıdaki diyagramda bu bildirimden oluşturulan **XmlEntity** ve **XmlText** düğümleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="4083c-123">Using the `<!ENTITY publisher "Microsoft Press">` entity declaration, the following diagram shows the **XmlEntity** and **XmlText** nodes created from this declaration.</span></span>  
  
 <span data-ttu-id="4083c-124">![varlık bildiriminden oluşturulan düğümler](media/xml-entitydeclaration-node2.png "xml_entitydeclaration_node2")</span><span class="sxs-lookup"><span data-stu-id="4083c-124">![nodes created from entity declaration](media/xml-entitydeclaration-node2.png "xml_entitydeclaration_node2")</span></span>  
  
 <span data-ttu-id="4083c-125">Varlık başvurularının genişletilme ve bu durumlarda, DOM ağacında bellek içinde oluşturulan düğümlerin bir farkı olmayan farklar.</span><span class="sxs-lookup"><span data-stu-id="4083c-125">The differences when entity references are expanded and when they are not makes a difference in what nodes are generated in the DOM tree, in memory.</span></span> <span data-ttu-id="4083c-126">Oluşturulan düğümlerdeki fark, [varlık başvuruları korunur](entity-references-are-preserved.md) ve [varlık başvuruları genişletilir ve korunmaz](entity-references-are-expanded-and-not-preserved.md).</span><span class="sxs-lookup"><span data-stu-id="4083c-126">The difference in the nodes that are generated is explained in the topics [Entity References are Preserved](entity-references-are-preserved.md) and [Entity References are Expanded and Not Preserved](entity-references-are-expanded-and-not-preserved.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4083c-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4083c-127">See also</span></span>

- [<span data-ttu-id="4083c-128">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="4083c-128">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
