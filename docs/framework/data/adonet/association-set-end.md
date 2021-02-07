---
description: 'Daha fazla bilgi edinin: ilişkilendirme kümesi sonu'
title: association set end
ms.date: 03/30/2017
ms.assetid: fe4bf1d3-047a-4a37-98c5-a66e70811346
ms.openlocfilehash: 12e01a3fb947f6fabd5e1a93ef475132418963df
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99697679"
---
# <a name="association-set-end"></a><span data-ttu-id="6a38d-103">association set end</span><span class="sxs-lookup"><span data-stu-id="6a38d-103">association set end</span></span>

<span data-ttu-id="6a38d-104">*İlişki kümesi sonu* , [varlık türünü](entity-type.md) ve bir [ilişki kümesinin](association-set.md)sonunda [ayarlanan varlığı](entity-set.md) tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6a38d-104">An *association set end* identifies the [entity type](entity-type.md) and the [entity set](entity-set.md) at the end of an [association set](association-set.md).</span></span> <span data-ttu-id="6a38d-105">İlişki kümesi uçları bir ilişki kümesinin parçası olarak tanımlanır; bir ilişki kümesi, tam olarak iki ilişkilendirme kümesine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6a38d-105">Association set ends are defined as part of an association set; an association set must have exactly two association set ends.</span></span>  
  
 <span data-ttu-id="6a38d-106">Bir ilişki kümesi bitiş tanımı aşağıdaki bilgileri içerir:</span><span class="sxs-lookup"><span data-stu-id="6a38d-106">An association set end definition contains the following information:</span></span>  
  
- <span data-ttu-id="6a38d-107">İlişki kümesine dahil olan varlık türlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="6a38d-107">One of the entity types involved in the association set.</span></span> <span data-ttu-id="6a38d-108">Istenir</span><span class="sxs-lookup"><span data-stu-id="6a38d-108">(Required)</span></span>  
  
- <span data-ttu-id="6a38d-109">İlişki kümesine dahil edilen varlık türü için ayarlanan varlık.</span><span class="sxs-lookup"><span data-stu-id="6a38d-109">The entity set for the entity type involved in the association set.</span></span> <span data-ttu-id="6a38d-110">Istenir</span><span class="sxs-lookup"><span data-stu-id="6a38d-110">(Required)</span></span>  
  
## <a name="example"></a><span data-ttu-id="6a38d-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="6a38d-111">Example</span></span>  

 <span data-ttu-id="6a38d-112">Aşağıdaki diyagramda iki ilişkiye sahip kavramsal bir model gösterilmektedir: `WrittenBy` ve `PublishedBy` .</span><span class="sxs-lookup"><span data-stu-id="6a38d-112">The diagram below shows a conceptual model with two associations: `WrittenBy` and `PublishedBy`.</span></span>  
  
 ![Üç varlık türüne sahip örnek model](./media/association-set-end/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="6a38d-114">Aşağıdaki diyagramda, `PublishedBy` `Books` `Publishers` yukarıda gösterilen kavramsal modele bağlı olarak bir ilişki kümesi () ve iki varlık kümesi (ve) gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6a38d-114">The following diagram shows an association set (`PublishedBy`) and two entity sets (`Books` and `Publishers`) based on the conceptual model shown above.</span></span> <span data-ttu-id="6a38d-115">İlişki kümesi sonlanır `Books` ve `Publishers` varlık kümeleridir.</span><span class="sxs-lookup"><span data-stu-id="6a38d-115">The association set ends are the `Books` and `Publishers` entity sets.</span></span> <span data-ttu-id="6a38d-116">`Books`Varlık kümesindeki bı, `Book` çalışma zamanında varlık türünün bir örneğini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6a38d-116">Bi in the `Books` entity set represents an instance of the `Book` entity type at run time.</span></span> <span data-ttu-id="6a38d-117">Benzer şekilde, PJ `Publisher` varlık kümesindeki bir örneği temsil eder `Publishers` .</span><span class="sxs-lookup"><span data-stu-id="6a38d-117">Similarly, Pj represents a `Publisher` instance in the `Publishers` entity set.</span></span> <span data-ttu-id="6a38d-118">BiPj `PublishedBy` , ilişki kümesindeki ilişkilendirmenin bir örneğini temsil eder `PublishedBy` .</span><span class="sxs-lookup"><span data-stu-id="6a38d-118">BiPj represents an instance of the `PublishedBy` association in the `PublishedBy` association set.</span></span>  
  
 ![Bir küme örneği gösteren ekran görüntüsü.](./media/association-set-end/sets-example-association.gif)  
  
 <span data-ttu-id="6a38d-120">[ADO.NET Entity Framework](./ef/index.md) kavramsal modelleri tanımlamak için kavramsal şema tanım dili ([csdl](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) adlı bir DSL kullanır.</span><span class="sxs-lookup"><span data-stu-id="6a38d-120">The [ADO.NET Entity Framework](./ef/index.md) uses a DSL called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="6a38d-121">Aşağıdaki CSDL, Yukarıdaki diyagramda bulunan her ilişkilendirme için bir ilişki kümesiyle bir varlık kapsayıcısını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6a38d-121">The following CSDL defines an entity container with one association set for each association in the diagram above.</span></span> <span data-ttu-id="6a38d-122">İlişki kümesi uçlarının her ilişkilendirme kümesi tanımının bir parçası olarak tanımlandığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="6a38d-122">Note that association set ends are defined as part of each association set definition.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
## <a name="see-also"></a><span data-ttu-id="6a38d-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6a38d-123">See also</span></span>

- [<span data-ttu-id="6a38d-124">Varlık Veri Modeli Temel Kavramları</span><span class="sxs-lookup"><span data-stu-id="6a38d-124">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="6a38d-125">Varlık Veri Modeli</span><span class="sxs-lookup"><span data-stu-id="6a38d-125">Entity Data Model</span></span>](entity-data-model.md)
