---
title: İlişki sonu Ayarla
ms.date: 03/30/2017
ms.assetid: fe4bf1d3-047a-4a37-98c5-a66e70811346
ms.openlocfilehash: 61dc00e6c349a25767f6221bed56ef8b65f823d9
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2019
ms.locfileid: "58412012"
---
# <a name="association-set-end"></a><span data-ttu-id="82c2d-102">İlişki sonu Ayarla</span><span class="sxs-lookup"><span data-stu-id="82c2d-102">association set end</span></span>
<span data-ttu-id="82c2d-103">Bir *ilişkilendirme ayarlanmış son* tanımlayan [varlık türü](../../../../docs/framework/data/adonet/entity-type.md) ve [varlık kümesi](../../../../docs/framework/data/adonet/entity-set.md) sonunda bir [ilişki kümesi](../../../../docs/framework/data/adonet/association-set.md).</span><span class="sxs-lookup"><span data-stu-id="82c2d-103">An *association set end* identifies the [entity type](../../../../docs/framework/data/adonet/entity-type.md) and the [entity set](../../../../docs/framework/data/adonet/entity-set.md) at the end of an [association set](../../../../docs/framework/data/adonet/association-set.md).</span></span> <span data-ttu-id="82c2d-104">İlişki kümesi uçlarının bir ilişkilendirme kümesinin bir parçası tanımlanır; bir ilişki kümesi tam olarak iki ilişki kümesi uçlarının olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="82c2d-104">Association set ends are defined as part of an association set; an association set must have exactly two association set ends.</span></span>  
  
 <span data-ttu-id="82c2d-105">Bir ilişkilendirme kümesi son tanımı, şu bilgileri içerir:</span><span class="sxs-lookup"><span data-stu-id="82c2d-105">An association set end definition contains the following information:</span></span>  
  
-   <span data-ttu-id="82c2d-106">İlişkilendirmesine katılan varlık türlerinden birini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="82c2d-106">One of the entity types involved in the association set.</span></span> <span data-ttu-id="82c2d-107">(Gerekli)</span><span class="sxs-lookup"><span data-stu-id="82c2d-107">(Required)</span></span>  
  
-   <span data-ttu-id="82c2d-108">Varlık için varlık türü ilişkilendirme kümesine katılan kümesi.</span><span class="sxs-lookup"><span data-stu-id="82c2d-108">The entity set for the entity type involved in the association set.</span></span> <span data-ttu-id="82c2d-109">(Gerekli)</span><span class="sxs-lookup"><span data-stu-id="82c2d-109">(Required)</span></span>  
  
## <a name="example"></a><span data-ttu-id="82c2d-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="82c2d-110">Example</span></span>  
 <span data-ttu-id="82c2d-111">Aşağıdaki diyagramda iki ilişkilendirmeleri kavramsal bir modelle gösterilmektedir: `WrittenBy` ve `PublishedBy`.</span><span class="sxs-lookup"><span data-stu-id="82c2d-111">The diagram below shows a conceptual model with two associations: `WrittenBy` and `PublishedBy`.</span></span>  
  
 ![Üç varlık türleri ile örnek modeli](./media/association-set-end/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="82c2d-113">Aşağıdaki diyagramda bir ilişki kümesi gösterilmektedir (`PublishedBy`) ve iki varlık kümeleri (`Books` ve `Publishers`) yukarıda gösterilen kavramsal model göre.</span><span class="sxs-lookup"><span data-stu-id="82c2d-113">The following diagram shows an association set (`PublishedBy`) and two entity sets (`Books` and `Publishers`) based on the conceptual model shown above.</span></span> <span data-ttu-id="82c2d-114">İlişki kümesi uçlarının olan `Books` ve `Publishers` varlık kümesi.</span><span class="sxs-lookup"><span data-stu-id="82c2d-114">The association set ends are the `Books` and `Publishers` entity sets.</span></span> <span data-ttu-id="82c2d-115">İçinde BI `Books` varlık kümesini temsil eden bir örneğini `Book` çalışma zamanında varlık türü.</span><span class="sxs-lookup"><span data-stu-id="82c2d-115">Bi in the `Books` entity set represents an instance of the `Book` entity type at run time.</span></span> <span data-ttu-id="82c2d-116">Benzer şekilde, Pj temsil eden bir `Publisher` örneğini `Publishers` varlık kümesi.</span><span class="sxs-lookup"><span data-stu-id="82c2d-116">Similarly, Pj represents a `Publisher` instance in the `Publishers` entity set.</span></span> <span data-ttu-id="82c2d-117">BiPj örneğini temsil eder `PublishedBy` ilişkilendirmeyi `PublishedBy` ilişki kümesi.</span><span class="sxs-lookup"><span data-stu-id="82c2d-117">BiPj represents an instance of the `PublishedBy` association in the `PublishedBy` association set.</span></span>  
  
 ![Kümeleri örnek gösteren ekran görüntüsü.](./media/association-set-end/sets-example-association.gif)  
  
 <span data-ttu-id="82c2d-119">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) kavramsal şema tanım dili olarak adlandırılan bir DSL kullanır ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) kavramsal modeller tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="82c2d-119">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a DSL called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="82c2d-120">Aşağıdaki CSDL, yukarıdaki diyagramda her bir ilişkilendirme için bir ilişki ile varlık kapsayıcısı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="82c2d-120">The following CSDL defines an entity container with one association set for each association in the diagram above.</span></span> <span data-ttu-id="82c2d-121">İlişki kümesi uçlarının her ilişki kümesi tanımının bir parçası tanımlandığına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="82c2d-121">Note that association set ends are defined as part of each association set definition.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
## <a name="see-also"></a><span data-ttu-id="82c2d-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="82c2d-122">See also</span></span>
- [<span data-ttu-id="82c2d-123">Varlık Veri Modeli Temel Kavramları</span><span class="sxs-lookup"><span data-stu-id="82c2d-123">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [<span data-ttu-id="82c2d-124">Varlık Veri Modeli</span><span class="sxs-lookup"><span data-stu-id="82c2d-124">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
