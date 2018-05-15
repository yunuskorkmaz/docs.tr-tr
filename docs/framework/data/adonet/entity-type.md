---
title: Varlık türü
ms.date: 03/30/2017
ms.assetid: a6dee9ab-9e4a-48f2-a169-3f79cc15821c
ms.openlocfilehash: c694f29d36988ea52aeca650cf2bba2c50c91e89
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="entity-type"></a><span data-ttu-id="c9245-102">Varlık türü</span><span class="sxs-lookup"><span data-stu-id="c9245-102">entity type</span></span>
<span data-ttu-id="c9245-103">*Varlık türü* verilerin varlık veri modeli (EDM) ile yapısını açıklamak için temel yapı bloğu.</span><span class="sxs-lookup"><span data-stu-id="c9245-103">The *entity type* is the fundamental building block for describing the structure of data with the Entity Data Model (EDM).</span></span> <span data-ttu-id="c9245-104">Kavramsal modelde, müşteriler veya siparişler gibi üst düzey kavramlarını yapısını bir varlık türünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c9245-104">In a conceptual model, an entity type represents the structure of top-level concepts, such as customers or orders.</span></span> <span data-ttu-id="c9245-105">Bir varlık türünün varlık türü örnekleri için bir şablondur.</span><span class="sxs-lookup"><span data-stu-id="c9245-105">An entity type is a template for entity type instances.</span></span> <span data-ttu-id="c9245-106">Her şablon aşağıdaki bilgileri içerir:</span><span class="sxs-lookup"><span data-stu-id="c9245-106">Each template contains the following information:</span></span>  
  
-   <span data-ttu-id="c9245-107">Benzersiz bir ad.</span><span class="sxs-lookup"><span data-stu-id="c9245-107">A unique name.</span></span> <span data-ttu-id="c9245-108">(Gerekli)</span><span class="sxs-lookup"><span data-stu-id="c9245-108">(Required.)</span></span>  
  
-   <span data-ttu-id="c9245-109">Bir [Varlık anahtarı](../../../../docs/framework/data/adonet/entity-key.md) bir veya daha fazla özellikleri tarafından tanımlanan.</span><span class="sxs-lookup"><span data-stu-id="c9245-109">An [entity key](../../../../docs/framework/data/adonet/entity-key.md) defined by one or more properties.</span></span> <span data-ttu-id="c9245-110">(Gerekli)</span><span class="sxs-lookup"><span data-stu-id="c9245-110">(Required.)</span></span>  
  
-   <span data-ttu-id="c9245-111">Veri biçiminde [özellikleri](../../../../docs/framework/data/adonet/property.md).</span><span class="sxs-lookup"><span data-stu-id="c9245-111">Data in the form of [properties](../../../../docs/framework/data/adonet/property.md).</span></span> <span data-ttu-id="c9245-112">(İsteğe bağlı.)</span><span class="sxs-lookup"><span data-stu-id="c9245-112">(Optional.)</span></span>  
  
-   <span data-ttu-id="c9245-113">[Gezinti özellikleri](../../../../docs/framework/data/adonet/navigation-property.md) izin veren bir gezinti için [son](../../../../docs/framework/data/adonet/association-end.md) , bir [ilişkilendirme](../../../../docs/framework/data/adonet/association-type.md) diğer bitiş.</span><span class="sxs-lookup"><span data-stu-id="c9245-113">[Navigation properties](../../../../docs/framework/data/adonet/navigation-property.md) that allow for navigation from one [end](../../../../docs/framework/data/adonet/association-end.md) of an [association](../../../../docs/framework/data/adonet/association-type.md) to the other end.</span></span> <span data-ttu-id="c9245-114">(İsteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="c9245-114">(Optional)</span></span>  
  
 <span data-ttu-id="c9245-115">Bir uygulamada bir varlık türünün bir örneği (örneğin, belirli bir müşteri veya sipariş) belirli bir nesneyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c9245-115">In an application, an instance of an entity type represents a specific object (such as a specific customer or order).</span></span> <span data-ttu-id="c9245-116">Her bir varlık türünün örneğini benzersiz olmalıdır [Varlık anahtarı](../../../../docs/framework/data/adonet/entity-key.md) içinde bir [varlık kümesi](../../../../docs/framework/data/adonet/entity-set.md).</span><span class="sxs-lookup"><span data-stu-id="c9245-116">Each instance of an entity type must have a unique [entity key](../../../../docs/framework/data/adonet/entity-key.md) within an [entity set](../../../../docs/framework/data/adonet/entity-set.md).</span></span>  
  
 <span data-ttu-id="c9245-117">İki varlık türü örnekleri yalnızca aynı türde olduğundan ve bunların varlık anahtarları aynı değerleri eşit olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="c9245-117">Two entity type instances are considered equal only if they are of the same type and the values of their entity keys are the same.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c9245-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="c9245-118">Example</span></span>  
 <span data-ttu-id="c9245-119">Aşağıdaki diyagram üç varlık türleriyle kavramsal model gösterir: `Book`, `Publisher`, ve `Author`:</span><span class="sxs-lookup"><span data-stu-id="c9245-119">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`:</span></span>  
  
 <span data-ttu-id="c9245-120">![Örnek modeli](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span><span class="sxs-lookup"><span data-stu-id="c9245-120">![Example Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span></span>  
  
 <span data-ttu-id="c9245-121">Kendi Varlık anahtarı oluşturan her bir varlık türü özelliklerini "(anahtar)" ile belirtilir unutmayın.</span><span class="sxs-lookup"><span data-stu-id="c9245-121">Note that the properties of each entity type that make up its entity key are denoted with "(Key)".</span></span>  
  
 <span data-ttu-id="c9245-122">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) kavramsal şema tanım dili adlı bir etki alanına özgü dil (DSL) kullanır ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) kavramsal modeller tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="c9245-122">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="c9245-123">Aşağıdaki CSDL tanımlar `Book` Yukarıdaki diyagramda gösterildiği varlık türü:</span><span class="sxs-lookup"><span data-stu-id="c9245-123">The following CSDL defines the `Book` entity type shown in the diagram above:</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
## <a name="see-also"></a><span data-ttu-id="c9245-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c9245-124">See Also</span></span>  
 [<span data-ttu-id="c9245-125">Varlık Veri Modeli Temel Kavramları</span><span class="sxs-lookup"><span data-stu-id="c9245-125">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="c9245-126">Varlık Veri Modeli</span><span class="sxs-lookup"><span data-stu-id="c9245-126">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)  
 [<span data-ttu-id="c9245-127">facet</span><span class="sxs-lookup"><span data-stu-id="c9245-127">facet</span></span>](../../../../docs/framework/data/adonet/facet.md)
