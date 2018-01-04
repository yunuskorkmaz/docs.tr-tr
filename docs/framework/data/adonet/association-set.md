---
title: "ilişkilendirme kümesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a65247b6-ce59-44ea-974c-14ae20a7995f
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 5be982d25a4ab135d2b521b558e809b306b88230
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="association-set"></a><span data-ttu-id="7486b-102">ilişkilendirme kümesi</span><span class="sxs-lookup"><span data-stu-id="7486b-102">association set</span></span>
<span data-ttu-id="7486b-103">Bir *ilişkilendirme kümesi* için mantıksal bir kapsayıcısıdır [ilişkilendirme](../../../../docs/framework/data/adonet/association-type.md) örnekleri aynı türde.</span><span class="sxs-lookup"><span data-stu-id="7486b-103">An *association set* is a logical container for [association](../../../../docs/framework/data/adonet/association-type.md) instances of the same type.</span></span> <span data-ttu-id="7486b-104">Bir ilişkilendirme kümesi yapı modelleme veri değil; diğer bir deyişle, verileri veya ilişkileri yapısını açıklamaz.</span><span class="sxs-lookup"><span data-stu-id="7486b-104">An association set is not a data modeling construct; that is, it does not describe the structure of data or relationships.</span></span> <span data-ttu-id="7486b-105">Böylece bir veri deposuna eşlenen bunun yerine, bir ilişkilendirme kümesine bir yapı için (örneğin, ortak dil çalışma zamanı veya SQL Server veritabanı) barındıran veya depolama bir ortam grubu ilişkisi örneklerine sağlar.</span><span class="sxs-lookup"><span data-stu-id="7486b-105">Instead, an association set provides a construct for a hosting or storage environment (such as the common language runtime or a SQL Server database) to group association instances so that they can be mapped to a data store.</span></span>  
  
 <span data-ttu-id="7486b-106">Bir ilişkilendirme kümesi içinde tanımlanan bir [varlık kapsayıcısının](../../../../docs/framework/data/adonet/entity-container.md), mantıksal bir gruplandırması olan [varlık kümeleri](../../../../docs/framework/data/adonet/entity-set.md) ve ilişki kümeleri.</span><span class="sxs-lookup"><span data-stu-id="7486b-106">An association set is defined within an [entity container](../../../../docs/framework/data/adonet/entity-container.md), which is a logical grouping of [entity sets](../../../../docs/framework/data/adonet/entity-set.md) and association sets.</span></span>  
  
 <span data-ttu-id="7486b-107">Bir ilişkilendirme kümesi için bir tanım aşağıdaki bilgileri içerir:</span><span class="sxs-lookup"><span data-stu-id="7486b-107">A definition for an association set contains the following information:</span></span>  
  
-   <span data-ttu-id="7486b-108">İlişki kümesi adı.</span><span class="sxs-lookup"><span data-stu-id="7486b-108">The association set name.</span></span> <span data-ttu-id="7486b-109">(Gerekli)</span><span class="sxs-lookup"><span data-stu-id="7486b-109">(Required)</span></span>  
  
-   <span data-ttu-id="7486b-110">Hangi örnekleri içerecek ilişki.</span><span class="sxs-lookup"><span data-stu-id="7486b-110">The association of which it will contain instances.</span></span> <span data-ttu-id="7486b-111">(Gerekli)</span><span class="sxs-lookup"><span data-stu-id="7486b-111">(Required)</span></span>  
  
-   <span data-ttu-id="7486b-112">İki [ilişki uçları kümesi](../../../../docs/framework/data/adonet/association-set-end.md).</span><span class="sxs-lookup"><span data-stu-id="7486b-112">Two [association set ends](../../../../docs/framework/data/adonet/association-set-end.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7486b-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="7486b-113">Example</span></span>  
 <span data-ttu-id="7486b-114">Aşağıdaki diyagramda iki ilişkilendirmeleri kavramsal modelle gösterir: `PublishedBy`, ve `WrittenBy`.</span><span class="sxs-lookup"><span data-stu-id="7486b-114">The diagram below shows a conceptual model with two associations: `PublishedBy`, and `WrittenBy`.</span></span> <span data-ttu-id="7486b-115">İlişki kümeleri hakkında bilgi diyagramda ilettiği değil de, sonraki diyagramda ilişkilendirme ayarlar ve bu modelini temel varlık kümeleri örneği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7486b-115">Although information about association sets is not conveyed in the diagram, the next diagram shows an example of association sets and entity sets based on this model.</span></span>  
  
 <span data-ttu-id="7486b-116">![Örnek modeli](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span><span class="sxs-lookup"><span data-stu-id="7486b-116">![Example Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span></span>  
  
 <span data-ttu-id="7486b-117">Aşağıdaki örnek, bir ilişkilendirme kümesine gösterir (`PublishedBy`) ve iki varlık kümeleri (`Books` ve `Publishers`) yukarıda gösterilen kavramsal model göre.</span><span class="sxs-lookup"><span data-stu-id="7486b-117">The following example shows an association set (`PublishedBy`) and two entity sets (`Books` and `Publishers`) based on the conceptual model shown above.</span></span> <span data-ttu-id="7486b-118">İçinde bi `Books` varlık kümesini temsil eden bir örneğini `Book` çalışma zamanında varlık türü.</span><span class="sxs-lookup"><span data-stu-id="7486b-118">Bi in the `Books` entity set represents an instance of the `Book` entity type at run time.</span></span> <span data-ttu-id="7486b-119">Benzer şekilde, Pj temsil eden bir `Publisher` örneğini `Publishers` varlık kümesi.</span><span class="sxs-lookup"><span data-stu-id="7486b-119">Similarly, Pj represents a `Publisher` instance in the `Publishers` entity set.</span></span> <span data-ttu-id="7486b-120">BiPj örneğini temsil eder `PublishedBy` ilişkilendirme `PublishedBy` ilişkilendirme kümesi.</span><span class="sxs-lookup"><span data-stu-id="7486b-120">BiPj represents an instance of the `PublishedBy` association in the `PublishedBy` association set.</span></span>  
  
 <span data-ttu-id="7486b-121">![Örnek ayarlar](../../../../docs/framework/data/adonet/media/setsexample.gif "SetsExample")</span><span class="sxs-lookup"><span data-stu-id="7486b-121">![Sets Example](../../../../docs/framework/data/adonet/media/setsexample.gif "SetsExample")</span></span>  
  
 <span data-ttu-id="7486b-122">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) kavramsal şema tanım dili adlı bir etki alanına özgü dil (DSL) kullanır ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) kavramsal modeller tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="7486b-122">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="7486b-123">Aşağıdaki CSDL bir ilişkilendirme için yukarıdaki diyagramdaki her bir ilişkilendirme kümesine sahip bir varlık kapsayıcı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7486b-123">The following CSDL defines an entity container with one association set for each association in the diagram above.</span></span> <span data-ttu-id="7486b-124">Her bir ilişkilendirme için ilişkilendirme ve adını ayarlayın Not XML öznitelikleri kullanılarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="7486b-124">Note that the name and association for each association set are defined using XML attributes.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
 <span data-ttu-id="7486b-125">Association, hiçbir iki ilişki kümeleri paylaşımı olarak uzunluğunda başına birden çok ilişkilendirme kümesi tanımlamak mümkündür bir [ilişkilendirme kümesi son](../../../../docs/framework/data/adonet/association-set-end.md).</span><span class="sxs-lookup"><span data-stu-id="7486b-125">It is possible to define multiple association sets per association, as long as no two association sets share an [association set end](../../../../docs/framework/data/adonet/association-set-end.md).</span></span> <span data-ttu-id="7486b-126">Bir varlık kapsayıcısı için iki ilişkilendirme kümeleriyle aşağıdaki CSDL tanımlar `WrittenBy` ilişkilendirme.</span><span class="sxs-lookup"><span data-stu-id="7486b-126">The following CSDL defines an entity container with two association sets for the `WrittenBy` association.</span></span> <span data-ttu-id="7486b-127">Birden çok varlık kümesi için tanımlanmış bildirim `Book` ve `Author` varlık türleri ve ilişkisi olmayan bir ilişki paylaşımları kümesi son ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="7486b-127">Notice that multiple entity sets have been defined for the `Book` and `Author` entity types and that no association set shares an association set end.</span></span>  
  
 [!code-xml[EDM_Example_Model#MultipleAssociationSets](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#multipleassociationsets)]  
  
## <a name="see-also"></a><span data-ttu-id="7486b-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7486b-128">See Also</span></span>  
 [<span data-ttu-id="7486b-129">Varlık Veri Modeli Temel Kavramları</span><span class="sxs-lookup"><span data-stu-id="7486b-129">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="7486b-130">Varlık Veri Modeli</span><span class="sxs-lookup"><span data-stu-id="7486b-130">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)  
 [<span data-ttu-id="7486b-131">foreign key property</span><span class="sxs-lookup"><span data-stu-id="7486b-131">foreign key property</span></span>](../../../../docs/framework/data/adonet/foreign-key-property.md)
