---
title: "Varlık anahtarı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0d447a6d-fa7a-4db0-8e7a-fd45e385fca0
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 184a55c3c5479f1999057e55dcc761a250051e5e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="entity-key"></a><span data-ttu-id="d6040-102">Varlık anahtarı</span><span class="sxs-lookup"><span data-stu-id="d6040-102">entity key</span></span>
<span data-ttu-id="d6040-103">Bir *Varlık anahtarı* olan bir [özelliği](../../../../docs/framework/data/adonet/property.md) veya özelliklerini kümesi bir [varlık türü](../../../../docs/framework/data/adonet/entity-type.md) kimliğini belirlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d6040-103">An *entity key* is a [property](../../../../docs/framework/data/adonet/property.md) or a set of properties of an [entity type](../../../../docs/framework/data/adonet/entity-type.md) that are used to determine identity.</span></span> <span data-ttu-id="d6040-104">Bir varlık anahtarı oluşturan özellikleri tasarım zamanında seçilir.</span><span class="sxs-lookup"><span data-stu-id="d6040-104">The properties that make up an entity key are chosen at design time.</span></span> <span data-ttu-id="d6040-105">Varlık anahtarı özelliklerinin değerlerini bir varlık türü örneği içinde tanımlamalıdır bir [varlık kümesini](../../../../docs/framework/data/adonet/entity-set.md) çalışma zamanında.</span><span class="sxs-lookup"><span data-stu-id="d6040-105">The values of entity key properties must uniquely identify an entity type instance within an [entity set](../../../../docs/framework/data/adonet/entity-set.md) at run time.</span></span> <span data-ttu-id="d6040-106">Bir varlık kümesindeki örnekleri benzersizliğini güvence altına almak için varlık anahtarı oluşturan özellikleri seçilmelidir.</span><span class="sxs-lookup"><span data-stu-id="d6040-106">The properties that make up an entity key should be chosen to guarantee uniqueness of instances in an entity set.</span></span>  
  
 <span data-ttu-id="d6040-107">Bir varlık anahtarı olması için bir özellikler kümesi için gereksinimleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="d6040-107">The following are the requirements for a set of properties to be an entity key:</span></span>  
  
-   <span data-ttu-id="d6040-108">Bir varlık kümesi içinde hiçbir iki varlık anahtarları aynı olabilir.</span><span class="sxs-lookup"><span data-stu-id="d6040-108">No two entity keys within an entity set can be identical.</span></span> <span data-ttu-id="d6040-109">Diğer bir deyişle, bir varlık kümesi içinde her iki varlıklar için bir anahtar oluşturan tüm özellikler için değerleri aynı olamaz.</span><span class="sxs-lookup"><span data-stu-id="d6040-109">That is, for any two entities within an entity set, the values for all of the properties that constitute a key cannot be the same.</span></span> <span data-ttu-id="d6040-110">Ancak, bazı (ancak tüm) bir varlık değerleri, anahtar aynı olabilir.</span><span class="sxs-lookup"><span data-stu-id="d6040-110">However, some (but not all) of the values that make up an entity key can be the same.</span></span>  
  
-   <span data-ttu-id="d6040-111">Bir varlık anahtarı null, sabit, kümesinden oluşmalıdır [ilkel tür özellikleri](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="d6040-111">An entity key must consist of a set of non-nullable, immutable, [primitive type properties](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md).</span></span>  
  
-   <span data-ttu-id="d6040-112">Belirtilen varlık türü için varlık anahtarı oluşturan özelliklerini değiştiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="d6040-112">The properties that make up an entity key for a given entity type cannot change.</span></span> <span data-ttu-id="d6040-113">Belirtilen varlık türü için birden fazla olası Varlık anahtarı izin veremez; yedek anahtarlar desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="d6040-113">You cannot allow more than one possible entity key for a given entity type; surrogate keys are not supported.</span></span>  
  
-   <span data-ttu-id="d6040-114">Bir varlık bir devralma hiyerarşisinde söz konusu olduğunda, kök varlığın varlık anahtarı oluşturan tüm özellikleri içermelidir ve varlık anahtarı kök varlık türünde tanımlanmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d6040-114">When an entity is involved in an inheritance hierarchy, the root entity must contain all the properties that make up the entity key, and the entity key must be defined on the root entity type.</span></span> <span data-ttu-id="d6040-115">Daha fazla bilgi için bkz: [varlık veri modeli: Devralma](../../../../docs/framework/data/adonet/entity-data-model-inheritance.md).</span><span class="sxs-lookup"><span data-stu-id="d6040-115">For more information, see [Entity Data Model: Inheritance](../../../../docs/framework/data/adonet/entity-data-model-inheritance.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d6040-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="d6040-116">Example</span></span>  
 <span data-ttu-id="d6040-117">Aşağıdaki diyagram üç varlık türleriyle kavramsal model gösterir: `Book`, `Publisher`, ve `Author`.</span><span class="sxs-lookup"><span data-stu-id="d6040-117">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span> <span data-ttu-id="d6040-118">Kendi Varlık anahtarı oluşturan her bir varlık türü özelliklerini "(anahtar)" ile gösterilir.</span><span class="sxs-lookup"><span data-stu-id="d6040-118">The properties of each entity type that make up its entity key are denoted with "(Key)".</span></span> <span data-ttu-id="d6040-119">Unutmayın `Author` varlık türüne sahip iki özelliklerini içeren varlık anahtarı `Name` ve `Address`.</span><span class="sxs-lookup"><span data-stu-id="d6040-119">Note that the `Author` entity type has an entity key that consists of two properties, `Name` and `Address`.</span></span>  
  
 <span data-ttu-id="d6040-120">![Örnek modeli](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span><span class="sxs-lookup"><span data-stu-id="d6040-120">![Example Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span></span>  
  
 <span data-ttu-id="d6040-121">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) kavramsal şema tanım dili adlı bir etki alanına özgü dil (DSL) kullanır ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) kavramsal modeller tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="d6040-121">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="d6040-122">CSDL tanımlar `Book` Yukarıdaki diyagramda gösterildiği varlık türü.</span><span class="sxs-lookup"><span data-stu-id="d6040-122">The CSDL below defines the `Book` entity type shown in the diagram above.</span></span> <span data-ttu-id="d6040-123">Varlık anahtarı başvurarak tanımlanır Not `ISBN` varlık türü özelliği.</span><span class="sxs-lookup"><span data-stu-id="d6040-123">Note that the entity key is defined by referencing the `ISBN` property of the entity type.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
 <span data-ttu-id="d6040-124">`ISBN` Özelliği olduğundan Varlık anahtarı için iyi bir seçimdir bir Uluslararası Standart Kitap numarası (ISBN) kitap benzersiz şekilde tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d6040-124">The `ISBN` property is a good choice for the entity key because an International Standard Book Number (ISBN) uniquely identifies a book.</span></span>  
  
 <span data-ttu-id="d6040-125">CSDL tanımlar `Author` Yukarıdaki diyagramda gösterildiği varlık türü.</span><span class="sxs-lookup"><span data-stu-id="d6040-125">The CSDL below defines the `Author` entity type shown in the diagram above.</span></span> <span data-ttu-id="d6040-126">Varlık anahtarı iki özelliklerini oluşur Not `Name` ve `Address`.</span><span class="sxs-lookup"><span data-stu-id="d6040-126">Note that the entity key consists of two properties, `Name` and `Address`.</span></span>  
  
 [!code-xml[EDM_Example_Model#CompositeKeyExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#compositekeyexample)]  
  
 <span data-ttu-id="d6040-127">Kullanarak `Name` ve `Address` aynı adı taşıyan iki yazarları aynı adresinde Canlı olası olduğundan varlık için makul bir seçim anahtarıdır.</span><span class="sxs-lookup"><span data-stu-id="d6040-127">Using `Name` and `Address` for the entity key is a reasonable choice, because two authors of the same name are unlikely to live at the same address.</span></span> <span data-ttu-id="d6040-128">Ancak, bu seçenek bir varlık anahtarı için bir varlık kümesindeki benzersiz varlık anahtarları kesinlikle garanti etmez.</span><span class="sxs-lookup"><span data-stu-id="d6040-128">However, this choice for an entity key does not absolutely guarantee unique entity keys in an entity set.</span></span> <span data-ttu-id="d6040-129">Bir özellik gibi ekleme `AuthorId`, benzersiz şekilde tanımlamak için kullanılabilirdi yazar bu durumda önerilen.</span><span class="sxs-lookup"><span data-stu-id="d6040-129">Adding a property, such as `AuthorId`, that could be used to uniquely identify an author would be recommended in this case.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6040-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d6040-130">See Also</span></span>  
 [<span data-ttu-id="d6040-131">Varlık Veri Modeli Temel Kavramları</span><span class="sxs-lookup"><span data-stu-id="d6040-131">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="d6040-132">Varlık Veri Modeli</span><span class="sxs-lookup"><span data-stu-id="d6040-132">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
