---
title: "Varlık bildirimleri ve varlık başvuruları DOM okuma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 86dba977-5cc4-4567-964f-027ffabc47b2
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6370db06cbe7ff8d46258b0315059f5c37587fea
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="reading-entity-declarations-and-entity-references-into-the-dom"></a><span data-ttu-id="acf48-102">Varlık bildirimleri ve varlık başvuruları DOM okuma</span><span class="sxs-lookup"><span data-stu-id="acf48-102">Reading Entity Declarations and Entity References into the DOM</span></span>
<span data-ttu-id="acf48-103">Bir varlık XML içeriği veya işaretleme yerine kullanılacak bir ad bildiren bir bildirimidir.</span><span class="sxs-lookup"><span data-stu-id="acf48-103">An entity is a declaration that states a name to be used in the XML in place of content or markup.</span></span> <span data-ttu-id="acf48-104">Varlıkları iki bölümü vardır.</span><span class="sxs-lookup"><span data-stu-id="acf48-104">There are two parts to entities.</span></span> <span data-ttu-id="acf48-105">İlk olarak, bir varlık bildirimi kullanarak değiştirme içerik için bir ad tie gerekir.</span><span class="sxs-lookup"><span data-stu-id="acf48-105">First, you must tie a name to the replacement content using an entity declaration.</span></span> <span data-ttu-id="acf48-106">Bir varlık bildirimi kullanılarak oluşturulan `<!ENTITY name "value">` bir belge türü tanımı (DTD) veya XML Şeması sözdiziminde.</span><span class="sxs-lookup"><span data-stu-id="acf48-106">An entity declaration is created by using the `<!ENTITY name "value">` syntax in a document type definition (DTD) or XML schema.</span></span> <span data-ttu-id="acf48-107">İkincisi, varlık bildiriminde tanımlanan adını sonradan XML'de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="acf48-107">Secondly, the name defined in the entity declaration is subsequently used in the XML.</span></span> <span data-ttu-id="acf48-108">XML'de kullanıldığında, bir varlık başvurusunun adı verilir.</span><span class="sxs-lookup"><span data-stu-id="acf48-108">When used in the XML, it is called an entity reference.</span></span> <span data-ttu-id="acf48-109">Örneğin, bir varlığın adı aşağıdaki varlık bildirimi bildirir `publisher` "Microsoft Press" içerikle ilişkili olan.</span><span class="sxs-lookup"><span data-stu-id="acf48-109">For example, the following entity declaration declares an entity of the name `publisher` being associated with the content of "Microsoft Press".</span></span>  
  
```xml  
<!ENTITY publisher "Microsoft Press">  
```  
  
 <span data-ttu-id="acf48-110">Aşağıdaki örnek, bir varlık referans olarak XML'de bu varlık bildirim kullanımını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="acf48-110">The following example shows the use of this entity declaration in XML as an entity reference.</span></span>  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 <span data-ttu-id="acf48-111">Bir belge belleğe yüklendiğinde bazı ayrıştırıcıları varlıklar otomatik olarak genişletin.</span><span class="sxs-lookup"><span data-stu-id="acf48-111">Some parsers automatically expand entities when a document is loaded into memory.</span></span> <span data-ttu-id="acf48-112">XML belleğe okuyun, bu nedenle, varlık bildirimleri hatırlanan kaydedilmiş ve.</span><span class="sxs-lookup"><span data-stu-id="acf48-112">Therefore, when the XML is being read into memory, entity declarations are remembered and saved.</span></span> <span data-ttu-id="acf48-113">Daha sonra karşılaştığında `&;` genel varlık başvurusu tanımlamak, karakterleri ayrıştırıcı bir varlık bildirimi tablo ad arar.</span><span class="sxs-lookup"><span data-stu-id="acf48-113">When the parser subsequently encounters `&;` characters, which identify a general entity reference, the parser looks up that name in an entity declaration table.</span></span> <span data-ttu-id="acf48-114">Başvuru `&publisher;` temsil ettiği içerik tarafından değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="acf48-114">The reference, `&publisher;` is replaced by the content that it represents.</span></span> <span data-ttu-id="acf48-115">Aşağıdaki XML kullanarak</span><span class="sxs-lookup"><span data-stu-id="acf48-115">Using the following XML,</span></span>  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 <span data-ttu-id="acf48-116">Varlık başvurusu genişletme ve değiştirme `&publisher;` ile Microsoft Press aşağıdaki genişletilmiş XML içeriği sağlar.</span><span class="sxs-lookup"><span data-stu-id="acf48-116">expanding the entity reference and replacing the `&publisher;` with the Microsoft Press content gives the following expanded XML.</span></span>  
  
 <span data-ttu-id="acf48-117">**Çıktı**</span><span class="sxs-lookup"><span data-stu-id="acf48-117">**Output**</span></span>  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by Microsoft Press</pubinfo>  
```  
  
 <span data-ttu-id="acf48-118">Varlıkları birçok çeşit vardır.</span><span class="sxs-lookup"><span data-stu-id="acf48-118">There are many kinds of entities.</span></span> <span data-ttu-id="acf48-119">Aşağıdaki diyagramda, varlık türleri ve terminolojiyi dökümünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="acf48-119">The following diagram shows the breakdown of entity types and terminology.</span></span>  
  
 <span data-ttu-id="acf48-120">![varlık türü hiyerarşisinin akış çizelgesi](../../../../docs/standard/data/xml/media/entity-hierarchy.gif "Entity_hierarchy")</span><span class="sxs-lookup"><span data-stu-id="acf48-120">![flow chart of entity type hierarchy](../../../../docs/standard/data/xml/media/entity-hierarchy.gif "Entity_hierarchy")</span></span>  
  
 <span data-ttu-id="acf48-121">Varlık başvuruları korumak ve XML yüklendiğinde varlıkları genişletme değil Microsoft .NET Framework uygulamasını XML belge nesne modeli (DOM) için varsayılan değer.</span><span class="sxs-lookup"><span data-stu-id="acf48-121">The default for the Microsoft .NET Framework implementation of the XML Document Object Model (DOM) is to preserve the entities references and not expand the entities when the XML is loaded.</span></span> <span data-ttu-id="acf48-122">Bir belge DOM'da yüklendiği gibi olduğu çıkarımında bulunulur Bu, bir **XmlEntityReference** başvuru değişkenini içeren düğüm `&publisher;` oluşturulmuş, varlık içeriği temsil eden alt düğümler ile DTD içinde bildirilen.</span><span class="sxs-lookup"><span data-stu-id="acf48-122">The implication of this is that as a document is loaded in the DOM, an **XmlEntityReference** node containing the reference variable `&publisher;` is created, with child nodes representing the content in the entity declared in the DTD.</span></span>  
  
 <span data-ttu-id="acf48-123">Kullanarak `<!ENTITY publisher "Microsoft Press">` varlık bildirimi, aşağıdaki diyagramda gösterilmiştir **XmlEntity** ve **XmlText** bu bildiriminden oluşturulan düğümler.</span><span class="sxs-lookup"><span data-stu-id="acf48-123">Using the `<!ENTITY publisher "Microsoft Press">` entity declaration, the following diagram shows the **XmlEntity** and **XmlText** nodes created from this declaration.</span></span>  
  
 <span data-ttu-id="acf48-124">![Varlık bildiriminden oluşturulan düğümler](../../../../docs/standard/data/xml/media/xml-entitydeclaration-node2.png "xml_entitydeclaration_node2")</span><span class="sxs-lookup"><span data-stu-id="acf48-124">![nodes created from entity declaration](../../../../docs/standard/data/xml/media/xml-entitydeclaration-node2.png "xml_entitydeclaration_node2")</span></span>  
  
 <span data-ttu-id="acf48-125">Farkları varlık başvuruları genişletildiğinde ve olmadıkları zaman hangi düğümleri DOM ağaçta bellek oluşturulan içinde bir fark yapar.</span><span class="sxs-lookup"><span data-stu-id="acf48-125">The differences when entity references are expanded and when they are not makes a difference in what nodes are generated in the DOM tree, in memory.</span></span> <span data-ttu-id="acf48-126">Oluşturulan düğümler arasındaki fark konularında açıklanan [varlık başvuruları korunur](../../../../docs/standard/data/xml/entity-references-are-preserved.md) ve [varlık başvuruları: genişletilmiş ve korunmaz](../../../../docs/standard/data/xml/entity-references-are-expanded-and-not-preserved.md).</span><span class="sxs-lookup"><span data-stu-id="acf48-126">The difference in the nodes that are generated is explained in the topics [Entity References are Preserved](../../../../docs/standard/data/xml/entity-references-are-preserved.md) and [Entity References are Expanded and Not Preserved](../../../../docs/standard/data/xml/entity-references-are-expanded-and-not-preserved.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acf48-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="acf48-127">See Also</span></span>  
 [<span data-ttu-id="acf48-128">XML belge nesne modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="acf48-128">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
