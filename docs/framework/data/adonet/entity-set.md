---
title: "Varlık kümesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59ec6ab0-88e5-4d25-b112-7a4eccbe61f0
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 050c73d3fd9146c8eee83baf1bd504acc18c8718
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="entity-set"></a><span data-ttu-id="59b46-102">Varlık kümesi</span><span class="sxs-lookup"><span data-stu-id="59b46-102">entity set</span></span>
<span data-ttu-id="59b46-103">Bir *varlık kümesini* için mantıksal bir kapsayıcısıdır örnekleri bir [varlık türü](../../../../docs/framework/data/adonet/entity-type.md) ve örnekleri bu varlık türünden türetilmiş herhangi bir türde.</span><span class="sxs-lookup"><span data-stu-id="59b46-103">An *entity set* is a logical container for instances of an [entity type](../../../../docs/framework/data/adonet/entity-type.md) and instances of any type derived from that entity type.</span></span> <span data-ttu-id="59b46-104">(Türetilmiş türler hakkında daha fazla bilgi için bkz: [varlık veri modeli: Devralma](../../../../docs/framework/data/adonet/entity-data-model-inheritance.md).) Bir satır ve ilişkisel bir veritabanındaki bir tablo arasındaki ilişki için bir varlık türünün varlık kümesi arasındaki ilişkiyi benzerdir: bir satır gibi bir varlık türü veri yapısını açıklar ve bir tablo gibi bir varlık kümesini verilen bir yapının örneklerini içerir.</span><span class="sxs-lookup"><span data-stu-id="59b46-104">(For information about derived types, see [Entity Data Model: Inheritance](../../../../docs/framework/data/adonet/entity-data-model-inheritance.md).) The relationship between an entity type and an entity set is analogous to the relationship between a row and a table in a relational database: Like a row, an entity type describes data structure, and, like a table, an entity set contains instances of a given structure.</span></span> <span data-ttu-id="59b46-105">Bir varlık kümesini yapı modelleme veri değil; verilerin yapısını açıklamaz.</span><span class="sxs-lookup"><span data-stu-id="59b46-105">An entity set is not a data modeling construct; it does not describe the structure of data.</span></span> <span data-ttu-id="59b46-106">Böylece bir veri deposuna eşlenen bunun yerine, bir varlık kümesini bir yapı (örneğin, ortak dil çalışma zamanı veya SQL Server veritabanı) barındıran veya depolama bir ortam için Grup varlık türü örnekleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="59b46-106">Instead, an entity set provides a construct for a hosting or storage environment (such as the common language runtime or a SQL Server database) to group entity type instances so that they can be mapped to a data store.</span></span>  
  
 <span data-ttu-id="59b46-107">Bir varlık kümesi içinde tanımlanan bir [varlık kapsayıcısının](../../../../docs/framework/data/adonet/entity-container.md), varlık kümeleri mantıksal bir gruplandırması olan ve [ilişki kümeleri](../../../../docs/framework/data/adonet/association-set.md).</span><span class="sxs-lookup"><span data-stu-id="59b46-107">An entity set is defined within an [entity container](../../../../docs/framework/data/adonet/entity-container.md), which is a logical grouping of entity sets and [association sets](../../../../docs/framework/data/adonet/association-set.md).</span></span>  
  
 <span data-ttu-id="59b46-108">Bir varlık kümesinde var varlık türü için bir örneği, aşağıdakilerin doğru olması gerekir:</span><span class="sxs-lookup"><span data-stu-id="59b46-108">For an entity type instance to exist in an entity set, the following must be true:</span></span>  
  
-   <span data-ttu-id="59b46-109">Örnek türü ya da'varlık kümesi tabanlı veya örnek varlık türünün bir alt türünde varlık türü olarak aynıdır.</span><span class="sxs-lookup"><span data-stu-id="59b46-109">The type of the instance is either the same as the entity type on which the entity set is based, or the type of the instance is a subtype of the entity type.</span></span>  
  
-   <span data-ttu-id="59b46-110">[Varlık anahtarı](../../../../docs/framework/data/adonet/entity-key.md) için varlık kümesi içinde benzersiz bir örneğidir.</span><span class="sxs-lookup"><span data-stu-id="59b46-110">The [entity key](../../../../docs/framework/data/adonet/entity-key.md) for the instance is unique within the entity set.</span></span>  
  
-   <span data-ttu-id="59b46-111">Örneği başka bir varlık kümesinde yok.</span><span class="sxs-lookup"><span data-stu-id="59b46-111">The instance does not exist in any other entity set.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="59b46-112">Birden çok varlık kümesine aynı varlık türü kullanılarak tanımlanabilir, ancak belirtilen varlık türünün bir örneği yalnızca tek bir varlık kümesinde var olabilir.</span><span class="sxs-lookup"><span data-stu-id="59b46-112">Multiple entity sets can be defined using the same entity type, but an instance of a given entity type can only exist in one entity set.</span></span>  
  
 <span data-ttu-id="59b46-113">Bir varlık için kavramsal modeldeki her bir varlık türü kümesine tanımlamak zorunda değildir.</span><span class="sxs-lookup"><span data-stu-id="59b46-113">You do not have to define an entity set for each entity type in a conceptual model.</span></span>  
  
## <a name="example"></a><span data-ttu-id="59b46-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="59b46-114">Example</span></span>  
 <span data-ttu-id="59b46-115">Aşağıdaki diyagram üç varlık türleriyle kavramsal model gösterir: `Book`, `Publisher`, ve `Author`.</span><span class="sxs-lookup"><span data-stu-id="59b46-115">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span>  
  
 <span data-ttu-id="59b46-116">![Örnek modeli](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span><span class="sxs-lookup"><span data-stu-id="59b46-116">![Example Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span></span>  
  
 <span data-ttu-id="59b46-117">Aşağıdaki diyagramda iki varlık kümelerini gösterir (`Books` ve `Publishers`) ve bir ilişkilendirme kümesine (`PublishedBy`) yukarıda gösterilen kavramsal model göre.</span><span class="sxs-lookup"><span data-stu-id="59b46-117">The following diagram shows two entity sets (`Books` and `Publishers`) and an association set (`PublishedBy`) based on the conceptual model shown above.</span></span> <span data-ttu-id="59b46-118">İçinde bi `Books` varlık kümesini temsil eden bir örneğini `Book` çalışma zamanında varlık türü.</span><span class="sxs-lookup"><span data-stu-id="59b46-118">Bi in the `Books` entity set represents an instance of the `Book` entity type at run time.</span></span> <span data-ttu-id="59b46-119">Benzer şekilde, Pj temsil eden bir `Publisher` örneğini `Publishers` varlık kümesi.</span><span class="sxs-lookup"><span data-stu-id="59b46-119">Similarly, Pj represent a `Publisher` instance in the `Publishers` entity set.</span></span> <span data-ttu-id="59b46-120">BiPj örneğini temsil eder `PublishedBy` ilişkilendirme `PublishedBy` ilişkilendirme kümesi.</span><span class="sxs-lookup"><span data-stu-id="59b46-120">BiPj represents an instance of the `PublishedBy` association in the `PublishedBy` association set.</span></span>  
  
 <span data-ttu-id="59b46-121">![Örnek ayarlar](../../../../docs/framework/data/adonet/media/setsexample.gif "SetsExample")</span><span class="sxs-lookup"><span data-stu-id="59b46-121">![Sets Example](../../../../docs/framework/data/adonet/media/setsexample.gif "SetsExample")</span></span>  
  
 <span data-ttu-id="59b46-122">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) kavramsal şema tanım dili adlı bir etki alanına özgü dil (DSL) kullanır ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) kavramsal modeller tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="59b46-122">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="59b46-123">Aşağıdaki CSDL yukarıda gösterilen kavramsal modeldeki her bir varlık türü için ayarlanmış bir varlığı olan bir varlık kapsayıcı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="59b46-123">The following CSDL defines an entity container with one entity set for each entity type in the conceptual model shown above.</span></span> <span data-ttu-id="59b46-124">Her varlık kümesi için ad ve varlık türü Not XML özniteliği kullanılarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="59b46-124">Note that the name and entity type for each entity set are defined using XML attributes.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
 <span data-ttu-id="59b46-125">Tür (MEST) başına birden çok varlık kümesine tanımlamak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="59b46-125">It is possible to define multiple entity sets per type (MEST).</span></span> <span data-ttu-id="59b46-126">Bir varlık kapsayıcısı için iki varlık kümeleri ile aşağıdaki CSDL tanımlar `Book` varlık türü:</span><span class="sxs-lookup"><span data-stu-id="59b46-126">The following CSDL defines an entity container with two entity sets for the `Book` entity type:</span></span>  
  
 [!code-xml[EDM_Example_Model#MESTExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#mestexample)]  
  
## <a name="see-also"></a><span data-ttu-id="59b46-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="59b46-127">See Also</span></span>  
 [<span data-ttu-id="59b46-128">Varlık Veri Modeli Temel Kavramları</span><span class="sxs-lookup"><span data-stu-id="59b46-128">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="59b46-129">Varlık Veri Modeli</span><span class="sxs-lookup"><span data-stu-id="59b46-129">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
