---
title: DOM'da varlık bildirimleri ve varlık başvuruları okuma
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 86dba977-5cc4-4567-964f-027ffabc47b2
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e30b52b8cdfb4d185687d58c80f4475730031c86
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45748687"
---
# <a name="reading-entity-declarations-and-entity-references-into-the-dom"></a><span data-ttu-id="bbd1f-102">DOM'da varlık bildirimleri ve varlık başvuruları okuma</span><span class="sxs-lookup"><span data-stu-id="bbd1f-102">Reading Entity Declarations and Entity References into the DOM</span></span>
<span data-ttu-id="bbd1f-103">XML içeriği veya biçimlendirme yerine kullanılmak üzere bir adını belirten bir bildirimi bir varlıktır.</span><span class="sxs-lookup"><span data-stu-id="bbd1f-103">An entity is a declaration that states a name to be used in the XML in place of content or markup.</span></span> <span data-ttu-id="bbd1f-104">Varlıkları iki bölümü vardır.</span><span class="sxs-lookup"><span data-stu-id="bbd1f-104">There are two parts to entities.</span></span> <span data-ttu-id="bbd1f-105">İlk olarak, bir ad kullanarak bir varlık bildirimi değiştirme içerik bağlamak gerekir.</span><span class="sxs-lookup"><span data-stu-id="bbd1f-105">First, you must tie a name to the replacement content using an entity declaration.</span></span> <span data-ttu-id="bbd1f-106">Bir varlık bildirimi kullanılarak oluşturulan `<!ENTITY name "value">` belge türü tanımı (DTD'nin) veya XML şema söz dizimi.</span><span class="sxs-lookup"><span data-stu-id="bbd1f-106">An entity declaration is created by using the `<!ENTITY name "value">` syntax in a document type definition (DTD) or XML schema.</span></span> <span data-ttu-id="bbd1f-107">İkincisi, varlık bildiriminde tanımlanan adını XML bundan sonra kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bbd1f-107">Secondly, the name defined in the entity declaration is subsequently used in the XML.</span></span> <span data-ttu-id="bbd1f-108">XML'de kullanıldığında, bir varlık başvurusu adı verilir.</span><span class="sxs-lookup"><span data-stu-id="bbd1f-108">When used in the XML, it is called an entity reference.</span></span> <span data-ttu-id="bbd1f-109">Örneğin, aşağıdaki varlık bildirimi varlığın adını bildirir `publisher` "Microsoft Press" içeriğini ile ilişkilendiriliyor.</span><span class="sxs-lookup"><span data-stu-id="bbd1f-109">For example, the following entity declaration declares an entity of the name `publisher` being associated with the content of "Microsoft Press".</span></span>  
  
```xml  
<!ENTITY publisher "Microsoft Press">  
```  
  
 <span data-ttu-id="bbd1f-110">Aşağıdaki örnek, bir varlık başvurusu XML içinde bu varlık bildirim kullanımını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="bbd1f-110">The following example shows the use of this entity declaration in XML as an entity reference.</span></span>  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 <span data-ttu-id="bbd1f-111">Bir belge belleğe yüklendiğinde bazı Çözümleyicileri varlıkları otomatik olarak genişletin.</span><span class="sxs-lookup"><span data-stu-id="bbd1f-111">Some parsers automatically expand entities when a document is loaded into memory.</span></span> <span data-ttu-id="bbd1f-112">XML belleğe okuyun, bu nedenle, varlık bildirimleri anımsanacak kaydedildi ve.</span><span class="sxs-lookup"><span data-stu-id="bbd1f-112">Therefore, when the XML is being read into memory, entity declarations are remembered and saved.</span></span> <span data-ttu-id="bbd1f-113">Daha sonra karşılaştığında `&;` , genel varlık başvurusu tanımlayın, karakterler ayrıştırıcı bir varlık bildirimi tablosunun ad arar.</span><span class="sxs-lookup"><span data-stu-id="bbd1f-113">When the parser subsequently encounters `&;` characters, which identify a general entity reference, the parser looks up that name in an entity declaration table.</span></span> <span data-ttu-id="bbd1f-114">Başvuru `&publisher;` temsil ettiği içerik ile değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="bbd1f-114">The reference, `&publisher;` is replaced by the content that it represents.</span></span> <span data-ttu-id="bbd1f-115">Aşağıdaki XML kullanarak</span><span class="sxs-lookup"><span data-stu-id="bbd1f-115">Using the following XML,</span></span>  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 <span data-ttu-id="bbd1f-116">Varlık başvurusu genişletme ve değiştirerek `&publisher;` ile Microsoft Press, şu genişletilmiş XML içeriği sağlar.</span><span class="sxs-lookup"><span data-stu-id="bbd1f-116">expanding the entity reference and replacing the `&publisher;` with the Microsoft Press content gives the following expanded XML.</span></span>  
  
 <span data-ttu-id="bbd1f-117">**Output**</span><span class="sxs-lookup"><span data-stu-id="bbd1f-117">**Output**</span></span>  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by Microsoft Press</pubinfo>  
```  
  
 <span data-ttu-id="bbd1f-118">Varlıkları birçok çeşit vardır.</span><span class="sxs-lookup"><span data-stu-id="bbd1f-118">There are many kinds of entities.</span></span> <span data-ttu-id="bbd1f-119">Aşağıdaki diyagramda, terminolojisi ve varlık türleri dökümünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="bbd1f-119">The following diagram shows the breakdown of entity types and terminology.</span></span>  
  
 <span data-ttu-id="bbd1f-120">![Akış Çizelgesi varlık türü hiyerarşisinin](../../../../docs/standard/data/xml/media/entity-hierarchy.gif "Entity_hierarchy")</span><span class="sxs-lookup"><span data-stu-id="bbd1f-120">![flow chart of entity type hierarchy](../../../../docs/standard/data/xml/media/entity-hierarchy.gif "Entity_hierarchy")</span></span>  
  
 <span data-ttu-id="bbd1f-121">Microsoft .NET Framework uygulaması XML belge nesne modeli (DOM) için varsayılan varlık başvuruları korur ve XML yüklendiğinde varlıkları genişletme değil sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="bbd1f-121">The default for the Microsoft .NET Framework implementation of the XML Document Object Model (DOM) is to preserve the entities references and not expand the entities when the XML is loaded.</span></span> <span data-ttu-id="bbd1f-122">Bir belge DOM, yüklü olan bu olduğu çıkarımında bir **XmlEntityReference** başvuru değişkenini içeren düğüm `&publisher;` oluşturulmuş, varlık içeriği temsil eden alt düğümler ile DTD'nin içinde bildirilmiş.</span><span class="sxs-lookup"><span data-stu-id="bbd1f-122">The implication of this is that as a document is loaded in the DOM, an **XmlEntityReference** node containing the reference variable `&publisher;` is created, with child nodes representing the content in the entity declared in the DTD.</span></span>  
  
 <span data-ttu-id="bbd1f-123">Kullanarak `<!ENTITY publisher "Microsoft Press">` varlık bildirimi, aşağıdaki diyagramda gösterilmiştir **XmlEntity** ve **XmlText** düğümleri bu bildirimden oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="bbd1f-123">Using the `<!ENTITY publisher "Microsoft Press">` entity declaration, the following diagram shows the **XmlEntity** and **XmlText** nodes created from this declaration.</span></span>  
  
 <span data-ttu-id="bbd1f-124">![Varlık bildiriminden oluşturulan düğümler](../../../../docs/standard/data/xml/media/xml-entitydeclaration-node2.png "xml_entitydeclaration_node2")</span><span class="sxs-lookup"><span data-stu-id="bbd1f-124">![nodes created from entity declaration](../../../../docs/standard/data/xml/media/xml-entitydeclaration-node2.png "xml_entitydeclaration_node2")</span></span>  
  
 <span data-ttu-id="bbd1f-125">Farklar varlık başvuruları genişletilir ve onlara hangi düğümleri DOM ağacında, bellekte oluşturulan içinde bir fark yapar.</span><span class="sxs-lookup"><span data-stu-id="bbd1f-125">The differences when entity references are expanded and when they are not makes a difference in what nodes are generated in the DOM tree, in memory.</span></span> <span data-ttu-id="bbd1f-126">Oluşturulan düğümler arasındaki fark konularında açıklanan [varlık başvuruları korunur](../../../../docs/standard/data/xml/entity-references-are-preserved.md) ve [varlık başvuruları genişletilir ve korunmaz olan](../../../../docs/standard/data/xml/entity-references-are-expanded-and-not-preserved.md).</span><span class="sxs-lookup"><span data-stu-id="bbd1f-126">The difference in the nodes that are generated is explained in the topics [Entity References are Preserved](../../../../docs/standard/data/xml/entity-references-are-preserved.md) and [Entity References are Expanded and Not Preserved](../../../../docs/standard/data/xml/entity-references-are-expanded-and-not-preserved.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbd1f-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bbd1f-127">See also</span></span>

- [<span data-ttu-id="bbd1f-128">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="bbd1f-128">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
