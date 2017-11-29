---
title: "İlişki sonu Ayarla"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fe4bf1d3-047a-4a37-98c5-a66e70811346
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 20810eddda98403d244f6104807504489dde71cc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="association-set-end"></a><span data-ttu-id="20e70-102">İlişki sonu Ayarla</span><span class="sxs-lookup"><span data-stu-id="20e70-102">association set end</span></span>
<span data-ttu-id="20e70-103">Bir *ilişkilendirme kümesi son* tanımlayan [varlık türü](../../../../docs/framework/data/adonet/entity-type.md) ve [varlık kümesini](../../../../docs/framework/data/adonet/entity-set.md) sonunda bir [ilişkilendirme kümesi](../../../../docs/framework/data/adonet/association-set.md).</span><span class="sxs-lookup"><span data-stu-id="20e70-103">An *association set end* identifies the [entity type](../../../../docs/framework/data/adonet/entity-type.md) and the [entity set](../../../../docs/framework/data/adonet/entity-set.md) at the end of an [association set](../../../../docs/framework/data/adonet/association-set.md).</span></span> <span data-ttu-id="20e70-104">İlişkilendirme kümesi uçları bir ilişkilendirme kümesinin bir parçası tanımlanan; bir ilişkilendirme kümesine tam olarak iki ilişkilendirme kümesi uçları sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="20e70-104">Association set ends are defined as part of an association set; an association set must have exactly two association set ends.</span></span>  
  
 <span data-ttu-id="20e70-105">Bir ilişkilendirme kümesi son tanımı aşağıdaki bilgileri içerir:</span><span class="sxs-lookup"><span data-stu-id="20e70-105">An association set end definition contains the following information:</span></span>  
  
-   <span data-ttu-id="20e70-106">Bir ilişkide ilgili varlık türlerinin ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="20e70-106">One of the entity types involved in the association set.</span></span> <span data-ttu-id="20e70-107">(Gerekli)</span><span class="sxs-lookup"><span data-stu-id="20e70-107">(Required)</span></span>  
  
-   <span data-ttu-id="20e70-108">Varlık için varlık türü ilişkilendirme kümesine dahil edilen kümesi.</span><span class="sxs-lookup"><span data-stu-id="20e70-108">The entity set for the entity type involved in the association set.</span></span> <span data-ttu-id="20e70-109">(Gerekli)</span><span class="sxs-lookup"><span data-stu-id="20e70-109">(Required)</span></span>  
  
## <a name="example"></a><span data-ttu-id="20e70-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="20e70-110">Example</span></span>  
 <span data-ttu-id="20e70-111">Aşağıdaki diyagramda iki ilişkilendirmeleri kavramsal modelle gösterir: `WrittenBy` ve `PublishedBy`.</span><span class="sxs-lookup"><span data-stu-id="20e70-111">The diagram below shows a conceptual model with two associations: `WrittenBy` and `PublishedBy`.</span></span>  
  
 <span data-ttu-id="20e70-112">![Örnek modeli](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span><span class="sxs-lookup"><span data-stu-id="20e70-112">![Example Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span></span>  
  
 <span data-ttu-id="20e70-113">Aşağıdaki diyagramda bir ilişkilendirme kümesine gösterir (`PublishedBy`) ve iki varlık kümeleri (`Books` ve `Publishers`) yukarıda gösterilen kavramsal model göre.</span><span class="sxs-lookup"><span data-stu-id="20e70-113">The following diagram shows an association set (`PublishedBy`) and two entity sets (`Books` and `Publishers`) based on the conceptual model shown above.</span></span> <span data-ttu-id="20e70-114">İlişkilendirme kümesi uçları olan `Books` ve `Publishers` varlık kümeleri.</span><span class="sxs-lookup"><span data-stu-id="20e70-114">The association set ends are the `Books` and `Publishers` entity sets.</span></span> <span data-ttu-id="20e70-115">İçinde bi `Books` varlık kümesini temsil eden bir örneğini `Book` çalışma zamanında varlık türü.</span><span class="sxs-lookup"><span data-stu-id="20e70-115">Bi in the `Books` entity set represents an instance of the `Book` entity type at run time.</span></span> <span data-ttu-id="20e70-116">Benzer şekilde, Pj temsil eden bir `Publisher` örneğini `Publishers` varlık kümesi.</span><span class="sxs-lookup"><span data-stu-id="20e70-116">Similarly, Pj represents a `Publisher` instance in the `Publishers` entity set.</span></span> <span data-ttu-id="20e70-117">BiPj örneğini temsil eder `PublishedBy` ilişkilendirme `PublishedBy` ilişkilendirme kümesi.</span><span class="sxs-lookup"><span data-stu-id="20e70-117">BiPj represents an instance of the `PublishedBy` association in the `PublishedBy` association set.</span></span>  
  
 <span data-ttu-id="20e70-118">![Örnek ayarlar](../../../../docs/framework/data/adonet/media/setsexample.gif "SetsExample")</span><span class="sxs-lookup"><span data-stu-id="20e70-118">![Sets Example](../../../../docs/framework/data/adonet/media/setsexample.gif "SetsExample")</span></span>  
  
 <span data-ttu-id="20e70-119">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) kavramsal şema tanım dili olarak adlandırılan bir DSL kullanır ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) kavramsal modeller tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="20e70-119">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a DSL called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="20e70-120">Aşağıdaki CSDL bir ilişkilendirme için yukarıdaki diyagramdaki her bir ilişkilendirme kümesine sahip bir varlık kapsayıcı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="20e70-120">The following CSDL defines an entity container with one association set for each association in the diagram above.</span></span> <span data-ttu-id="20e70-121">İlişkilendirme kümesi uçları her ilişkilendirme kümesi tanımının bir parçası tanımlanan unutmayın.</span><span class="sxs-lookup"><span data-stu-id="20e70-121">Note that association set ends are defined as part of each association set definition.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
## <a name="see-also"></a><span data-ttu-id="20e70-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="20e70-122">See Also</span></span>  
 [<span data-ttu-id="20e70-123">Varlık veri modeli temel kavramları</span><span class="sxs-lookup"><span data-stu-id="20e70-123">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="20e70-124">Varlık veri modeli</span><span class="sxs-lookup"><span data-stu-id="20e70-124">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
