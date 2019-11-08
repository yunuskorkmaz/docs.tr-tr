---
title: association set end
ms.date: 03/30/2017
ms.assetid: fe4bf1d3-047a-4a37-98c5-a66e70811346
ms.openlocfilehash: f7ec1ca6fcdf299b9fcfc78f299ea4c6c5267cd3
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738622"
---
# <a name="association-set-end"></a><span data-ttu-id="a95ca-102">association set end</span><span class="sxs-lookup"><span data-stu-id="a95ca-102">association set end</span></span>
<span data-ttu-id="a95ca-103">*İlişki kümesi sonu* , [varlık türünü](entity-type.md) ve bir [ilişki kümesinin](association-set.md)sonunda [ayarlanan varlığı](entity-set.md) tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a95ca-103">An *association set end* identifies the [entity type](entity-type.md) and the [entity set](entity-set.md) at the end of an [association set](association-set.md).</span></span> <span data-ttu-id="a95ca-104">İlişki kümesi uçları bir ilişki kümesinin parçası olarak tanımlanır; bir ilişki kümesi, tam olarak iki ilişkilendirme kümesine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a95ca-104">Association set ends are defined as part of an association set; an association set must have exactly two association set ends.</span></span>  
  
 <span data-ttu-id="a95ca-105">Bir ilişki kümesi bitiş tanımı aşağıdaki bilgileri içerir:</span><span class="sxs-lookup"><span data-stu-id="a95ca-105">An association set end definition contains the following information:</span></span>  
  
- <span data-ttu-id="a95ca-106">İlişki kümesine dahil olan varlık türlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="a95ca-106">One of the entity types involved in the association set.</span></span> <span data-ttu-id="a95ca-107">Istenir</span><span class="sxs-lookup"><span data-stu-id="a95ca-107">(Required)</span></span>  
  
- <span data-ttu-id="a95ca-108">İlişki kümesine dahil edilen varlık türü için ayarlanan varlık.</span><span class="sxs-lookup"><span data-stu-id="a95ca-108">The entity set for the entity type involved in the association set.</span></span> <span data-ttu-id="a95ca-109">Istenir</span><span class="sxs-lookup"><span data-stu-id="a95ca-109">(Required)</span></span>  
  
## <a name="example"></a><span data-ttu-id="a95ca-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="a95ca-110">Example</span></span>  
 <span data-ttu-id="a95ca-111">Aşağıdaki diyagramda iki ilişkiye sahip bir kavramsal model görülmektedir: `WrittenBy` ve `PublishedBy`.</span><span class="sxs-lookup"><span data-stu-id="a95ca-111">The diagram below shows a conceptual model with two associations: `WrittenBy` and `PublishedBy`.</span></span>  
  
 ![Üç varlık türüne sahip örnek model](./media/association-set-end/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="a95ca-113">Aşağıdaki diyagramda, yukarıda gösterilen kavramsal modele bağlı olarak bir ilişki kümesi (`PublishedBy`) ve iki varlık kümesi (`Books` ve `Publishers`) gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a95ca-113">The following diagram shows an association set (`PublishedBy`) and two entity sets (`Books` and `Publishers`) based on the conceptual model shown above.</span></span> <span data-ttu-id="a95ca-114">İlişki kümesi sona erer `Books` ve `Publishers` varlık kümeleridir.</span><span class="sxs-lookup"><span data-stu-id="a95ca-114">The association set ends are the `Books` and `Publishers` entity sets.</span></span> <span data-ttu-id="a95ca-115">`Books` varlık kümesindeki bı, çalışma zamanında `Book` varlık türünün bir örneğini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a95ca-115">Bi in the `Books` entity set represents an instance of the `Book` entity type at run time.</span></span> <span data-ttu-id="a95ca-116">Benzer şekilde, PJ, `Publishers` varlık kümesindeki bir `Publisher` örneğini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a95ca-116">Similarly, Pj represents a `Publisher` instance in the `Publishers` entity set.</span></span> <span data-ttu-id="a95ca-117">BiPj, `PublishedBy` ilişkilendirme kümesindeki `PublishedBy` ilişkisinin bir örneğini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a95ca-117">BiPj represents an instance of the `PublishedBy` association in the `PublishedBy` association set.</span></span>  
  
 ![Bir küme örneği gösteren ekran görüntüsü.](./media/association-set-end/sets-example-association.gif)  
  
 <span data-ttu-id="a95ca-119">[ADO.NET Entity Framework](./ef/index.md) kavramsal modelleri tanımlamak için kavramsal şema tanım dili ([csdl](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) adlı bir DSL kullanır.</span><span class="sxs-lookup"><span data-stu-id="a95ca-119">The [ADO.NET Entity Framework](./ef/index.md) uses a DSL called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="a95ca-120">Aşağıdaki CSDL, Yukarıdaki diyagramda bulunan her ilişkilendirme için bir ilişki kümesiyle bir varlık kapsayıcısını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a95ca-120">The following CSDL defines an entity container with one association set for each association in the diagram above.</span></span> <span data-ttu-id="a95ca-121">İlişki kümesi uçlarının her ilişkilendirme kümesi tanımının bir parçası olarak tanımlandığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="a95ca-121">Note that association set ends are defined as part of each association set definition.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
## <a name="see-also"></a><span data-ttu-id="a95ca-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a95ca-122">See also</span></span>

- [<span data-ttu-id="a95ca-123">Varlık Veri Modeli Temel Kavramları</span><span class="sxs-lookup"><span data-stu-id="a95ca-123">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="a95ca-124">Varlık Veri Modeli</span><span class="sxs-lookup"><span data-stu-id="a95ca-124">Entity Data Model</span></span>](entity-data-model.md)
