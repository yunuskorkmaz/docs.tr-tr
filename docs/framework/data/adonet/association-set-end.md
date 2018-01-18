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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 85b4bd732d9de987676bae70f7749a1dd9dc76c5
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="association-set-end"></a><span data-ttu-id="47052-102">İlişki sonu Ayarla</span><span class="sxs-lookup"><span data-stu-id="47052-102">association set end</span></span>
<span data-ttu-id="47052-103">Bir *ilişkilendirme kümesi son* tanımlayan [varlık türü](../../../../docs/framework/data/adonet/entity-type.md) ve [varlık kümesini](../../../../docs/framework/data/adonet/entity-set.md) sonunda bir [ilişkilendirme kümesi](../../../../docs/framework/data/adonet/association-set.md).</span><span class="sxs-lookup"><span data-stu-id="47052-103">An *association set end* identifies the [entity type](../../../../docs/framework/data/adonet/entity-type.md) and the [entity set](../../../../docs/framework/data/adonet/entity-set.md) at the end of an [association set](../../../../docs/framework/data/adonet/association-set.md).</span></span> <span data-ttu-id="47052-104">İlişkilendirme kümesi uçları bir ilişkilendirme kümesinin bir parçası tanımlanan; bir ilişkilendirme kümesine tam olarak iki ilişkilendirme kümesi uçları sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="47052-104">Association set ends are defined as part of an association set; an association set must have exactly two association set ends.</span></span>  
  
 <span data-ttu-id="47052-105">Bir ilişkilendirme kümesi son tanımı aşağıdaki bilgileri içerir:</span><span class="sxs-lookup"><span data-stu-id="47052-105">An association set end definition contains the following information:</span></span>  
  
-   <span data-ttu-id="47052-106">Bir ilişkide ilgili varlık türlerinin ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="47052-106">One of the entity types involved in the association set.</span></span> <span data-ttu-id="47052-107">(Gerekli)</span><span class="sxs-lookup"><span data-stu-id="47052-107">(Required)</span></span>  
  
-   <span data-ttu-id="47052-108">Varlık için varlık türü ilişkilendirme kümesine dahil edilen kümesi.</span><span class="sxs-lookup"><span data-stu-id="47052-108">The entity set for the entity type involved in the association set.</span></span> <span data-ttu-id="47052-109">(Gerekli)</span><span class="sxs-lookup"><span data-stu-id="47052-109">(Required)</span></span>  
  
## <a name="example"></a><span data-ttu-id="47052-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="47052-110">Example</span></span>  
 <span data-ttu-id="47052-111">Aşağıdaki diyagramda iki ilişkilendirmeleri kavramsal modelle gösterir: `WrittenBy` ve `PublishedBy`.</span><span class="sxs-lookup"><span data-stu-id="47052-111">The diagram below shows a conceptual model with two associations: `WrittenBy` and `PublishedBy`.</span></span>  
  
 <span data-ttu-id="47052-112">![Örnek modeli](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span><span class="sxs-lookup"><span data-stu-id="47052-112">![Example Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span></span>  
  
 <span data-ttu-id="47052-113">Aşağıdaki diyagramda bir ilişkilendirme kümesine gösterir (`PublishedBy`) ve iki varlık kümeleri (`Books` ve `Publishers`) yukarıda gösterilen kavramsal model göre.</span><span class="sxs-lookup"><span data-stu-id="47052-113">The following diagram shows an association set (`PublishedBy`) and two entity sets (`Books` and `Publishers`) based on the conceptual model shown above.</span></span> <span data-ttu-id="47052-114">İlişkilendirme kümesi uçları olan `Books` ve `Publishers` varlık kümeleri.</span><span class="sxs-lookup"><span data-stu-id="47052-114">The association set ends are the `Books` and `Publishers` entity sets.</span></span> <span data-ttu-id="47052-115">İçinde bi `Books` varlık kümesini temsil eden bir örneğini `Book` çalışma zamanında varlık türü.</span><span class="sxs-lookup"><span data-stu-id="47052-115">Bi in the `Books` entity set represents an instance of the `Book` entity type at run time.</span></span> <span data-ttu-id="47052-116">Benzer şekilde, Pj temsil eden bir `Publisher` örneğini `Publishers` varlık kümesi.</span><span class="sxs-lookup"><span data-stu-id="47052-116">Similarly, Pj represents a `Publisher` instance in the `Publishers` entity set.</span></span> <span data-ttu-id="47052-117">BiPj örneğini temsil eder `PublishedBy` ilişkilendirme `PublishedBy` ilişkilendirme kümesi.</span><span class="sxs-lookup"><span data-stu-id="47052-117">BiPj represents an instance of the `PublishedBy` association in the `PublishedBy` association set.</span></span>  
  
 <span data-ttu-id="47052-118">![Örnek ayarlar](../../../../docs/framework/data/adonet/media/setsexample.gif "SetsExample")</span><span class="sxs-lookup"><span data-stu-id="47052-118">![Sets Example](../../../../docs/framework/data/adonet/media/setsexample.gif "SetsExample")</span></span>  
  
 <span data-ttu-id="47052-119">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) kavramsal şema tanım dili olarak adlandırılan bir DSL kullanır ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) kavramsal modeller tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="47052-119">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a DSL called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="47052-120">Aşağıdaki CSDL bir ilişkilendirme için yukarıdaki diyagramdaki her bir ilişkilendirme kümesine sahip bir varlık kapsayıcı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="47052-120">The following CSDL defines an entity container with one association set for each association in the diagram above.</span></span> <span data-ttu-id="47052-121">İlişkilendirme kümesi uçları her ilişkilendirme kümesi tanımının bir parçası tanımlanan unutmayın.</span><span class="sxs-lookup"><span data-stu-id="47052-121">Note that association set ends are defined as part of each association set definition.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
## <a name="see-also"></a><span data-ttu-id="47052-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="47052-122">See Also</span></span>  
 [<span data-ttu-id="47052-123">Varlık Veri Modeli Temel Kavramları</span><span class="sxs-lookup"><span data-stu-id="47052-123">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="47052-124">Varlık Veri Modeli</span><span class="sxs-lookup"><span data-stu-id="47052-124">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
