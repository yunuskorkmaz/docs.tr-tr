---
title: entity set
ms.date: 03/30/2017
ms.assetid: 59ec6ab0-88e5-4d25-b112-7a4eccbe61f0
ms.openlocfilehash: 5a2465801c270813dd7bca2144d05fa202571153
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738428"
---
# <a name="entity-set"></a><span data-ttu-id="74e2d-102">entity set</span><span class="sxs-lookup"><span data-stu-id="74e2d-102">entity set</span></span>
<span data-ttu-id="74e2d-103">*Varlık kümesi* , [varlık türü](entity-type.md) örnekleri ve bu varlık türünden türetilmiş herhangi bir türün örnekleri için mantıksal bir kapsayıcıdır.</span><span class="sxs-lookup"><span data-stu-id="74e2d-103">An *entity set* is a logical container for instances of an [entity type](entity-type.md) and instances of any type derived from that entity type.</span></span> <span data-ttu-id="74e2d-104">(Türetilmiş türler hakkında bilgi için bkz. [varlık veri modeli: devralma](entity-data-model-inheritance.md).) Bir varlık türü ve bir varlık kümesi arasındaki ilişki, bir satır ile ilişkisel veritabanındaki bir tablo arasındaki ilişkiye benzerdir: bir satır gibi, bir varlık türü veri yapısını tanımlar ve tablo gibi bir varlık kümesi, belirli bir yapının örneklerini içerir.</span><span class="sxs-lookup"><span data-stu-id="74e2d-104">(For information about derived types, see [Entity Data Model: Inheritance](entity-data-model-inheritance.md).) The relationship between an entity type and an entity set is analogous to the relationship between a row and a table in a relational database: Like a row, an entity type describes data structure, and, like a table, an entity set contains instances of a given structure.</span></span> <span data-ttu-id="74e2d-105">Bir varlık kümesi, bir veri modelleme yapısı değildir; verilerin yapısını tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="74e2d-105">An entity set is not a data modeling construct; it does not describe the structure of data.</span></span> <span data-ttu-id="74e2d-106">Bunun yerine, bir varlık kümesi, varlık türü örneklerinin bir veri deposuyla eşleştiribilecekleri şekilde gruplandırılması için bir barındırma veya depolama ortamı (ortak dil çalışma zamanı veya bir SQL Server veritabanı gibi) için bir yapı sağlar.</span><span class="sxs-lookup"><span data-stu-id="74e2d-106">Instead, an entity set provides a construct for a hosting or storage environment (such as the common language runtime or a SQL Server database) to group entity type instances so that they can be mapped to a data store.</span></span>  
  
 <span data-ttu-id="74e2d-107">Varlık kümesi, varlık kümelerinin ve [ilişkilendirme kümelerinin](association-set.md)mantıksal bir gruplandırması olan bir [varlık kapsayıcısı](entity-container.md)içinde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="74e2d-107">An entity set is defined within an [entity container](entity-container.md), which is a logical grouping of entity sets and [association sets](association-set.md).</span></span>  
  
 <span data-ttu-id="74e2d-108">Bir varlık kümesinde bir varlık türü örneğinin mevcut olması için, aşağıdakilerin doğru olması gerekir:</span><span class="sxs-lookup"><span data-stu-id="74e2d-108">For an entity type instance to exist in an entity set, the following must be true:</span></span>  
  
- <span data-ttu-id="74e2d-109">Örneğin türü, varlık kümesinin temel aldığı varlık türü ile aynı veya örneğin türü varlık türünün bir alt türü.</span><span class="sxs-lookup"><span data-stu-id="74e2d-109">The type of the instance is either the same as the entity type on which the entity set is based, or the type of the instance is a subtype of the entity type.</span></span>  
  
- <span data-ttu-id="74e2d-110">Örnek için [varlık anahtarı](entity-key.md) varlık kümesi içinde benzersizdir.</span><span class="sxs-lookup"><span data-stu-id="74e2d-110">The [entity key](entity-key.md) for the instance is unique within the entity set.</span></span>  
  
- <span data-ttu-id="74e2d-111">Örnek başka bir varlık kümesinde yok.</span><span class="sxs-lookup"><span data-stu-id="74e2d-111">The instance does not exist in any other entity set.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="74e2d-112">Birden çok varlık kümesi aynı varlık türü kullanılarak tanımlanabilir, ancak belirli bir varlık türünün bir örneği yalnızca bir varlık kümesinde bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="74e2d-112">Multiple entity sets can be defined using the same entity type, but an instance of a given entity type can only exist in one entity set.</span></span>  
  
 <span data-ttu-id="74e2d-113">Kavramsal modeldeki her varlık türü için bir varlık kümesi tanımlamanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="74e2d-113">You do not have to define an entity set for each entity type in a conceptual model.</span></span>  
  
## <a name="example"></a><span data-ttu-id="74e2d-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="74e2d-114">Example</span></span>  
 <span data-ttu-id="74e2d-115">Aşağıdaki diyagramda üç varlık türü olan kavramsal bir model gösterilmektedir: `Book`, `Publisher`ve `Author`.</span><span class="sxs-lookup"><span data-stu-id="74e2d-115">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span>  
  
 ![Üç varlık türüne sahip örnek model](./media/entity-set/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="74e2d-117">Aşağıdaki diyagramda, yukarıda gösterilen kavramsal modele göre iki varlık kümesi (`Books` ve `Publishers`) ve bir ilişki kümesi (`PublishedBy`) gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="74e2d-117">The following diagram shows two entity sets (`Books` and `Publishers`) and an association set (`PublishedBy`) based on the conceptual model shown above.</span></span> <span data-ttu-id="74e2d-118">`Books` varlık kümesindeki bı, çalışma zamanında `Book` varlık türünün bir örneğini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="74e2d-118">Bi in the `Books` entity set represents an instance of the `Book` entity type at run time.</span></span> <span data-ttu-id="74e2d-119">Benzer şekilde, PJ, `Publishers` varlık kümesindeki bir `Publisher` örneğini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="74e2d-119">Similarly, Pj represent a `Publisher` instance in the `Publishers` entity set.</span></span> <span data-ttu-id="74e2d-120">BiPj, `PublishedBy` ilişkilendirme kümesindeki `PublishedBy` ilişkisinin bir örneğini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="74e2d-120">BiPj represents an instance of the `PublishedBy` association in the `PublishedBy` association set.</span></span>  
  
 ![Bir küme örneği gösteren ekran görüntüsü.](./media/entity-set/sets-example-association.gif)  
  
 <span data-ttu-id="74e2d-122">[ADO.NET Entity Framework](./ef/index.md) kavramsal model tanımlamak için kavramsal şema tanım dili ([csdl](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) adlı bir etki ALANıNA özgü dil (DSL) kullanır.</span><span class="sxs-lookup"><span data-stu-id="74e2d-122">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="74e2d-123">Aşağıdaki CSDL, yukarıda gösterilen kavramsal modeldeki her bir varlık türü için tek bir varlık kümesine sahip bir varlık kapsayıcısını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="74e2d-123">The following CSDL defines an entity container with one entity set for each entity type in the conceptual model shown above.</span></span> <span data-ttu-id="74e2d-124">Her bir varlık kümesi için ad ve varlık türünün XML öznitelikleri kullanılarak tanımlandığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="74e2d-124">Note that the name and entity type for each entity set are defined using XML attributes.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
 <span data-ttu-id="74e2d-125">Tür başına birden çok varlık kümesi tanımlamak mümkündür (MEST).</span><span class="sxs-lookup"><span data-stu-id="74e2d-125">It is possible to define multiple entity sets per type (MEST).</span></span> <span data-ttu-id="74e2d-126">Aşağıdaki CSDL `Book` varlık türü için iki varlık kümesiyle bir varlık kapsayıcısını tanımlar:</span><span class="sxs-lookup"><span data-stu-id="74e2d-126">The following CSDL defines an entity container with two entity sets for the `Book` entity type:</span></span>  
  
 [!code-xml[EDM_Example_Model#MESTExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#mestexample)]  
  
## <a name="see-also"></a><span data-ttu-id="74e2d-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="74e2d-127">See also</span></span>

- [<span data-ttu-id="74e2d-128">Varlık Veri Modeli Temel Kavramları</span><span class="sxs-lookup"><span data-stu-id="74e2d-128">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="74e2d-129">Varlık Veri Modeli</span><span class="sxs-lookup"><span data-stu-id="74e2d-129">Entity Data Model</span></span>](entity-data-model.md)
