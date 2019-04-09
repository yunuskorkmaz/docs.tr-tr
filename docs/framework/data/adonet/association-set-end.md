---
title: association set end
ms.date: 03/30/2017
ms.assetid: fe4bf1d3-047a-4a37-98c5-a66e70811346
ms.openlocfilehash: 7b6c646592c1878ea30396d98b4976dc8fa0be12
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59134634"
---
# <a name="association-set-end"></a><span data-ttu-id="ad77b-102">association set end</span><span class="sxs-lookup"><span data-stu-id="ad77b-102">association set end</span></span>
<span data-ttu-id="ad77b-103">Bir *ilişkilendirme ayarlanmış son* tanımlayan [varlık türü](../../../../docs/framework/data/adonet/entity-type.md) ve [varlık kümesi](../../../../docs/framework/data/adonet/entity-set.md) sonunda bir [ilişki kümesi](../../../../docs/framework/data/adonet/association-set.md).</span><span class="sxs-lookup"><span data-stu-id="ad77b-103">An *association set end* identifies the [entity type](../../../../docs/framework/data/adonet/entity-type.md) and the [entity set](../../../../docs/framework/data/adonet/entity-set.md) at the end of an [association set](../../../../docs/framework/data/adonet/association-set.md).</span></span> <span data-ttu-id="ad77b-104">İlişki kümesi uçlarının bir ilişkilendirme kümesinin bir parçası tanımlanır; bir ilişki kümesi tam olarak iki ilişki kümesi uçlarının olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ad77b-104">Association set ends are defined as part of an association set; an association set must have exactly two association set ends.</span></span>  
  
 <span data-ttu-id="ad77b-105">Bir ilişkilendirme kümesi son tanımı, şu bilgileri içerir:</span><span class="sxs-lookup"><span data-stu-id="ad77b-105">An association set end definition contains the following information:</span></span>  
  
-   <span data-ttu-id="ad77b-106">İlişkilendirmesine katılan varlık türlerinden birini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="ad77b-106">One of the entity types involved in the association set.</span></span> <span data-ttu-id="ad77b-107">(Gerekli)</span><span class="sxs-lookup"><span data-stu-id="ad77b-107">(Required)</span></span>  
  
-   <span data-ttu-id="ad77b-108">Varlık için varlık türü ilişkilendirme kümesine katılan kümesi.</span><span class="sxs-lookup"><span data-stu-id="ad77b-108">The entity set for the entity type involved in the association set.</span></span> <span data-ttu-id="ad77b-109">(Gerekli)</span><span class="sxs-lookup"><span data-stu-id="ad77b-109">(Required)</span></span>  
  
## <a name="example"></a><span data-ttu-id="ad77b-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="ad77b-110">Example</span></span>  
 <span data-ttu-id="ad77b-111">Aşağıdaki diyagramda iki ilişkilendirmeleri kavramsal bir modelle gösterilmektedir: `WrittenBy` ve `PublishedBy`.</span><span class="sxs-lookup"><span data-stu-id="ad77b-111">The diagram below shows a conceptual model with two associations: `WrittenBy` and `PublishedBy`.</span></span>  
  
 ![Üç varlık türleri ile örnek modeli](./media/association-set-end/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="ad77b-113">Aşağıdaki diyagramda bir ilişki kümesi gösterilmektedir (`PublishedBy`) ve iki varlık kümeleri (`Books` ve `Publishers`) yukarıda gösterilen kavramsal model göre.</span><span class="sxs-lookup"><span data-stu-id="ad77b-113">The following diagram shows an association set (`PublishedBy`) and two entity sets (`Books` and `Publishers`) based on the conceptual model shown above.</span></span> <span data-ttu-id="ad77b-114">İlişki kümesi uçlarının olan `Books` ve `Publishers` varlık kümesi.</span><span class="sxs-lookup"><span data-stu-id="ad77b-114">The association set ends are the `Books` and `Publishers` entity sets.</span></span> <span data-ttu-id="ad77b-115">İçinde BI `Books` varlık kümesini temsil eden bir örneğini `Book` çalışma zamanında varlık türü.</span><span class="sxs-lookup"><span data-stu-id="ad77b-115">Bi in the `Books` entity set represents an instance of the `Book` entity type at run time.</span></span> <span data-ttu-id="ad77b-116">Benzer şekilde, Pj temsil eden bir `Publisher` örneğini `Publishers` varlık kümesi.</span><span class="sxs-lookup"><span data-stu-id="ad77b-116">Similarly, Pj represents a `Publisher` instance in the `Publishers` entity set.</span></span> <span data-ttu-id="ad77b-117">BiPj örneğini temsil eder `PublishedBy` ilişkilendirmeyi `PublishedBy` ilişki kümesi.</span><span class="sxs-lookup"><span data-stu-id="ad77b-117">BiPj represents an instance of the `PublishedBy` association in the `PublishedBy` association set.</span></span>  
  
 ![Kümeleri örnek gösteren ekran görüntüsü.](./media/association-set-end/sets-example-association.gif)  
  
 <span data-ttu-id="ad77b-119">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) kavramsal şema tanım dili olarak adlandırılan bir DSL kullanır ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) kavramsal modeller tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="ad77b-119">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a DSL called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="ad77b-120">Aşağıdaki CSDL, yukarıdaki diyagramda her bir ilişkilendirme için bir ilişki ile varlık kapsayıcısı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ad77b-120">The following CSDL defines an entity container with one association set for each association in the diagram above.</span></span> <span data-ttu-id="ad77b-121">İlişki kümesi uçlarının her ilişki kümesi tanımının bir parçası tanımlandığına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="ad77b-121">Note that association set ends are defined as part of each association set definition.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
## <a name="see-also"></a><span data-ttu-id="ad77b-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ad77b-122">See also</span></span>

- [<span data-ttu-id="ad77b-123">Varlık Veri Modeli Temel Kavramları</span><span class="sxs-lookup"><span data-stu-id="ad77b-123">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [<span data-ttu-id="ad77b-124">Varlık Veri Modeli</span><span class="sxs-lookup"><span data-stu-id="ad77b-124">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
