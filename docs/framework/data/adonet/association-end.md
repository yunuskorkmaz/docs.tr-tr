---
title: "ilişki ucu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2c345213-0296-4d90-ac6d-cef179798a75
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 53e52a09533f3e1ead240ec3284371603c82ce53
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="association-end"></a><span data-ttu-id="dc1c2-102">ilişki ucu</span><span class="sxs-lookup"><span data-stu-id="dc1c2-102">association end</span></span>
<span data-ttu-id="dc1c2-103">Bir *ilişki ucu* tanımlayan [varlık türü](../../../../docs/framework/data/adonet/entity-type.md) bir ucunda bir [ilişkilendirme](../../../../docs/framework/data/adonet/association-type.md) ve varlık sayısı bu ilişkilendirmeyi sonunda bulunabilir örnekleri yazın.</span><span class="sxs-lookup"><span data-stu-id="dc1c2-103">An *association end* identifies the [entity type](../../../../docs/framework/data/adonet/entity-type.md) on one end of an [association](../../../../docs/framework/data/adonet/association-type.md) and the number of entity type instances that can exist at that end of an association.</span></span> <span data-ttu-id="dc1c2-104">İlişki Uçları ilişkilendirme bir parçası olarak tanımlanan; bir ilişkilendirme tam olarak iki ilişki ucu olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="dc1c2-104">Association ends are defined as part of an association; an association must have exactly two association ends.</span></span> <span data-ttu-id="dc1c2-105">[Gezinti özellikleri](../../../../docs/framework/data/adonet/navigation-property.md) diğer gezinti bölmesinden bir ilişki ucu izin verir.</span><span class="sxs-lookup"><span data-stu-id="dc1c2-105">[Navigation properties](../../../../docs/framework/data/adonet/navigation-property.md) allow for navigation from one association end to the other.</span></span>  
  
 <span data-ttu-id="dc1c2-106">Bir ilişkilendirme end tanımı aşağıdaki bilgileri içerir:</span><span class="sxs-lookup"><span data-stu-id="dc1c2-106">An association end definition contains the following information:</span></span>  
  
-   <span data-ttu-id="dc1c2-107">İlişkide ilgili varlık türleri biri.</span><span class="sxs-lookup"><span data-stu-id="dc1c2-107">One of the entity types involved in the association.</span></span> <span data-ttu-id="dc1c2-108">(Gerekli)</span><span class="sxs-lookup"><span data-stu-id="dc1c2-108">(Required)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="dc1c2-109">Belirli bir ilişkilendirme için her ilişki ucu için belirtilen varlık türü aynı olabilir.</span><span class="sxs-lookup"><span data-stu-id="dc1c2-109">For a given association, the entity type specified for each association end can be the same.</span></span> <span data-ttu-id="dc1c2-110">Bu, kendi kendine bir ilişki oluşturur.</span><span class="sxs-lookup"><span data-stu-id="dc1c2-110">This creates a self-association.</span></span>  
  
-   <span data-ttu-id="dc1c2-111">Bir [ilişkilendirme son Çokluk](../../../../docs/framework/data/adonet/association-end-multiplicity.md) bir ilişki sonunda olabilir varlık türü örneklerinin sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="dc1c2-111">An [association end multiplicity](../../../../docs/framework/data/adonet/association-end-multiplicity.md) that indicates the number of entity type instances that can be at one end of the association.</span></span> <span data-ttu-id="dc1c2-112">Bir ilişkilendirme end Çokluk bir değer (0.. 1 çokluğa) bir (1), sıfır veya bir veya birçok (*) olabilir.</span><span class="sxs-lookup"><span data-stu-id="dc1c2-112">An association end multiplicity can have a value of one (1), zero or one (0..1), or many (*).</span></span>  
  
-   <span data-ttu-id="dc1c2-113">İlişki ucu için bir ad.</span><span class="sxs-lookup"><span data-stu-id="dc1c2-113">A name for the association end.</span></span> <span data-ttu-id="dc1c2-114">(İsteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="dc1c2-114">(Optional)</span></span>  
  
-   <span data-ttu-id="dc1c2-115">Cascade delete üzerinde gibi ilişki ucu üzerinde gerçekleştirilen işlemler hakkında bilgi.</span><span class="sxs-lookup"><span data-stu-id="dc1c2-115">Information about operations that are performed on the association end, such as cascade on delete.</span></span> <span data-ttu-id="dc1c2-116">(İsteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="dc1c2-116">(Optional)</span></span>  
  
## <a name="example"></a><span data-ttu-id="dc1c2-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="dc1c2-117">Example</span></span>  
 <span data-ttu-id="dc1c2-118">Aşağıdaki diyagramda iki ilişkilendirmeleri kavramsal modelle gösterir: `PublishedBy` ve `WrittenBy`.</span><span class="sxs-lookup"><span data-stu-id="dc1c2-118">The diagram below shows a conceptual model with two associations: `PublishedBy` and `WrittenBy`.</span></span> <span data-ttu-id="dc1c2-119">İlişkilendirme sona `PublishedBy` ilişkisi olan `Book` ve `Publisher` varlık türleri.</span><span class="sxs-lookup"><span data-stu-id="dc1c2-119">The association ends for the `PublishedBy` association are the `Book` and `Publisher` entity types.</span></span> <span data-ttu-id="dc1c2-120">Çokluğu `Publisher` sonudur bir (1) ve çokluğu `Book` sonudur birçok (*), bir yayımcı birçok books yayımlar ve kitap bir yayımcı tarafından yayımlanan gösteren.</span><span class="sxs-lookup"><span data-stu-id="dc1c2-120">The multiplicity of the `Publisher` end is one (1) and the multiplicity of the `Book` end is many (*), indicating that a publisher publishes many books and a book is published by one publisher.</span></span>  
  
 <span data-ttu-id="dc1c2-121">![Örnek modeli](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span><span class="sxs-lookup"><span data-stu-id="dc1c2-121">![Example Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span></span>  
  
 <span data-ttu-id="dc1c2-122">Kavramsal şema tanım dili adlı bir etki alanına özgü dil (DSL) ADO.NET Entity Framework kullanır ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) kavramsal modeller tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="dc1c2-122">The ADO.NET Entity Framework uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="dc1c2-123">CSDL tanımlar `PublishedBy` Yukarıdaki diyagramda gösterildiği ilişkilendirme.</span><span class="sxs-lookup"><span data-stu-id="dc1c2-123">The CSDL below defines the `PublishedBy` association shown in the diagram above.</span></span> <span data-ttu-id="dc1c2-124">Türü, adı ve her ilişkilendirme ucunun çokluğu XML özniteliği tarafından belirtilen unutmayın ( `Type`, `Role`, ve `Multiplicity` öznitelikleri, sırasıyla).</span><span class="sxs-lookup"><span data-stu-id="dc1c2-124">Note that the type, name, and multiplicity of each association end are specified by XML attributes (the `Type`, `Role`, and `Multiplicity` attributes, respectively).</span></span> <span data-ttu-id="dc1c2-125">Bir tarafta gerçekleştirilen işlemler hakkında isteğe bağlı bilgileri bir XML öğesi belirtilen ( `OnDelete` öğesi).</span><span class="sxs-lookup"><span data-stu-id="dc1c2-125">Optional information about operations performed on an end is specified in an XML element (the `OnDelete` element).</span></span> <span data-ttu-id="dc1c2-126">Bu durumda, bir yayımcı silinir, böylece tüm ilişkili books demektir.</span><span class="sxs-lookup"><span data-stu-id="dc1c2-126">In this case, if a publisher is deleted, so are all associated books.</span></span>  
  
 [!code-xml[EDM_Example_Model#AssociationEnd](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#associationend)]  
  
## <a name="see-also"></a><span data-ttu-id="dc1c2-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="dc1c2-127">See Also</span></span>  
 [<span data-ttu-id="dc1c2-128">Varlık Veri Modeli Temel Kavramları</span><span class="sxs-lookup"><span data-stu-id="dc1c2-128">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="dc1c2-129">Varlık Veri Modeli</span><span class="sxs-lookup"><span data-stu-id="dc1c2-129">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
