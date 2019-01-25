---
title: İlişki sonu Ayarla
ms.date: 03/30/2017
ms.assetid: fe4bf1d3-047a-4a37-98c5-a66e70811346
ms.openlocfilehash: 9a71fd434bea87a75e259a3d5caa902fbecf8a57
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54701644"
---
# <a name="association-set-end"></a><span data-ttu-id="b8368-102">İlişki sonu Ayarla</span><span class="sxs-lookup"><span data-stu-id="b8368-102">association set end</span></span>
<span data-ttu-id="b8368-103">Bir *ilişkilendirme ayarlanmış son* tanımlayan [varlık türü](../../../../docs/framework/data/adonet/entity-type.md) ve [varlık kümesi](../../../../docs/framework/data/adonet/entity-set.md) sonunda bir [ilişki kümesi](../../../../docs/framework/data/adonet/association-set.md).</span><span class="sxs-lookup"><span data-stu-id="b8368-103">An *association set end* identifies the [entity type](../../../../docs/framework/data/adonet/entity-type.md) and the [entity set](../../../../docs/framework/data/adonet/entity-set.md) at the end of an [association set](../../../../docs/framework/data/adonet/association-set.md).</span></span> <span data-ttu-id="b8368-104">İlişki kümesi uçlarının bir ilişkilendirme kümesinin bir parçası tanımlanır; bir ilişki kümesi tam olarak iki ilişki kümesi uçlarının olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b8368-104">Association set ends are defined as part of an association set; an association set must have exactly two association set ends.</span></span>  
  
 <span data-ttu-id="b8368-105">Bir ilişkilendirme kümesi son tanımı, şu bilgileri içerir:</span><span class="sxs-lookup"><span data-stu-id="b8368-105">An association set end definition contains the following information:</span></span>  
  
-   <span data-ttu-id="b8368-106">İlişkilendirmesine katılan varlık türlerinden birini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b8368-106">One of the entity types involved in the association set.</span></span> <span data-ttu-id="b8368-107">(Gerekli)</span><span class="sxs-lookup"><span data-stu-id="b8368-107">(Required)</span></span>  
  
-   <span data-ttu-id="b8368-108">Varlık için varlık türü ilişkilendirme kümesine katılan kümesi.</span><span class="sxs-lookup"><span data-stu-id="b8368-108">The entity set for the entity type involved in the association set.</span></span> <span data-ttu-id="b8368-109">(Gerekli)</span><span class="sxs-lookup"><span data-stu-id="b8368-109">(Required)</span></span>  
  
## <a name="example"></a><span data-ttu-id="b8368-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="b8368-110">Example</span></span>  
 <span data-ttu-id="b8368-111">Aşağıdaki diyagramda iki ilişkilendirmeleri kavramsal bir modelle gösterilmektedir: `WrittenBy` ve `PublishedBy`.</span><span class="sxs-lookup"><span data-stu-id="b8368-111">The diagram below shows a conceptual model with two associations: `WrittenBy` and `PublishedBy`.</span></span>  
  
 <span data-ttu-id="b8368-112">![Örnek Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span><span class="sxs-lookup"><span data-stu-id="b8368-112">![Example Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span></span>  
  
 <span data-ttu-id="b8368-113">Aşağıdaki diyagramda bir ilişki kümesi gösterilmektedir (`PublishedBy`) ve iki varlık kümeleri (`Books` ve `Publishers`) yukarıda gösterilen kavramsal model göre.</span><span class="sxs-lookup"><span data-stu-id="b8368-113">The following diagram shows an association set (`PublishedBy`) and two entity sets (`Books` and `Publishers`) based on the conceptual model shown above.</span></span> <span data-ttu-id="b8368-114">İlişki kümesi uçlarının olan `Books` ve `Publishers` varlık kümesi.</span><span class="sxs-lookup"><span data-stu-id="b8368-114">The association set ends are the `Books` and `Publishers` entity sets.</span></span> <span data-ttu-id="b8368-115">İçinde BI `Books` varlık kümesini temsil eden bir örneğini `Book` çalışma zamanında varlık türü.</span><span class="sxs-lookup"><span data-stu-id="b8368-115">Bi in the `Books` entity set represents an instance of the `Book` entity type at run time.</span></span> <span data-ttu-id="b8368-116">Benzer şekilde, Pj temsil eden bir `Publisher` örneğini `Publishers` varlık kümesi.</span><span class="sxs-lookup"><span data-stu-id="b8368-116">Similarly, Pj represents a `Publisher` instance in the `Publishers` entity set.</span></span> <span data-ttu-id="b8368-117">BiPj örneğini temsil eder `PublishedBy` ilişkilendirmeyi `PublishedBy` ilişki kümesi.</span><span class="sxs-lookup"><span data-stu-id="b8368-117">BiPj represents an instance of the `PublishedBy` association in the `PublishedBy` association set.</span></span>  
  
 <span data-ttu-id="b8368-118">![Örnek ayarlar](../../../../docs/framework/data/adonet/media/setsexample.gif "SetsExample")</span><span class="sxs-lookup"><span data-stu-id="b8368-118">![Sets Example](../../../../docs/framework/data/adonet/media/setsexample.gif "SetsExample")</span></span>  
  
 <span data-ttu-id="b8368-119">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) kavramsal şema tanım dili olarak adlandırılan bir DSL kullanır ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) kavramsal modeller tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="b8368-119">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a DSL called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="b8368-120">Aşağıdaki CSDL, yukarıdaki diyagramda her bir ilişkilendirme için bir ilişki ile varlık kapsayıcısı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b8368-120">The following CSDL defines an entity container with one association set for each association in the diagram above.</span></span> <span data-ttu-id="b8368-121">İlişki kümesi uçlarının her ilişki kümesi tanımının bir parçası tanımlandığına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="b8368-121">Note that association set ends are defined as part of each association set definition.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
## <a name="see-also"></a><span data-ttu-id="b8368-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b8368-122">See also</span></span>
- [<span data-ttu-id="b8368-123">Varlık Veri Modeli Temel Kavramları</span><span class="sxs-lookup"><span data-stu-id="b8368-123">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [<span data-ttu-id="b8368-124">Varlık Veri Modeli</span><span class="sxs-lookup"><span data-stu-id="b8368-124">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
