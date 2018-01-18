---
title: "Varlık veri modeli: devralma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 42c7ef24-710a-4af9-8493-cd41c399ecb0
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 6e6207087524a1ec1201511a91a810f02449e610
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="entity-data-model-inheritance"></a><span data-ttu-id="d4da0-102">Varlık veri modeli: devralma</span><span class="sxs-lookup"><span data-stu-id="d4da0-102">Entity Data Model: Inheritance</span></span>
<span data-ttu-id="d4da0-103">Varlık veri modeli (EDM) için devralma destekleyen [varlık türleri](../../../../docs/framework/data/adonet/entity-type.md).</span><span class="sxs-lookup"><span data-stu-id="d4da0-103">The Entity Data Model (EDM) supports inheritance for [entity types](../../../../docs/framework/data/adonet/entity-type.md).</span></span> <span data-ttu-id="d4da0-104">EDM devralma nesne odaklı programlama dillerinde sınıfları için devralma benzer.</span><span class="sxs-lookup"><span data-stu-id="d4da0-104">Inheritance in the EDM is similar to inheritance for classes in object-oriented programming languages.</span></span> <span data-ttu-id="d4da0-105">Nesne odaklı dillerde sınıflarıyla kavramsal modelde bir varlık türü tanımlayabilirsiniz gibi (bir *türetilen türün*) başka bir varlık türünden devralan ( *temel türü*).</span><span class="sxs-lookup"><span data-stu-id="d4da0-105">Like with classes in object-oriented languages, in a conceptual model you can define an entity type (a *derived type*) that inherits from another entity type (the *base type*).</span></span> <span data-ttu-id="d4da0-106">Ancak, nesne odaklı programlama sınıflarında, kavramsal modelde türetilmiş bir tür her zaman tüm devralır [özellikleri](../../../../docs/framework/data/adonet/property.md) ve [Gezinti özellikleri](../../../../docs/framework/data/adonet/navigation-property.md) temel türü.</span><span class="sxs-lookup"><span data-stu-id="d4da0-106">However, unlike classes in object-oriented programming, in a conceptual model the derived type always inherits all the [properties](../../../../docs/framework/data/adonet/property.md) and [navigation properties](../../../../docs/framework/data/adonet/navigation-property.md) of the base type.</span></span> <span data-ttu-id="d4da0-107">Türetilmiş bir tür devralınan özelliklerinde geçersiz kılamaz.</span><span class="sxs-lookup"><span data-stu-id="d4da0-107">You cannot override inherited properties in a derived type.</span></span>  
  
 <span data-ttu-id="d4da0-108">Kavramsal modelde devralma Hiyerarşiler türetilmiş bir tür başka bir türetilmiş türden devralan oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d4da0-108">In a conceptual model you can build inheritance hierarchies in which a derived type inherits from another derived type.</span></span> <span data-ttu-id="d4da0-109">(Türetilmiş bir tür değil hiyerarşideki bir türü) hiyerarşinin üstündeki türü olarak adlandırılır *kök türü*.</span><span class="sxs-lookup"><span data-stu-id="d4da0-109">The type at the top of the hierarchy (the one type in the hierarchy that is not a derived type) is called the *root type*.</span></span> <span data-ttu-id="d4da0-110">Bir devralma hiyerarşisinde [Varlık anahtarı](../../../../docs/framework/data/adonet/entity-key.md) kök türünde tanımlanmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d4da0-110">In an inheritance hierarchy, the [entity key](../../../../docs/framework/data/adonet/entity-key.md) must be defined on the root type.</span></span>  
  
 <span data-ttu-id="d4da0-111">Devralma Hiyerarşiler türetilmiş bir tür birden fazla türünden devralan oluşturamaz.</span><span class="sxs-lookup"><span data-stu-id="d4da0-111">You cannot build inheritance hierarchies in which a derived type inherits from more than one type.</span></span> <span data-ttu-id="d4da0-112">Örneğin, bir modeldeki kavramsal ile bir `Book` varlık türü, türetilmiş türler tanımlayabilirsiniz `FictionBook` ve `NonFictionBook` her öğesinden devralmalı `Book`.</span><span class="sxs-lookup"><span data-stu-id="d4da0-112">For example, in a conceptual model with a `Book` entity type, you could define derived types `FictionBook` and `NonFictionBook` that each inherit from `Book`.</span></span> <span data-ttu-id="d4da0-113">Ancak, daha sonra hem de devralan bir tür tanımlayabilirsiniz değil `FictionBook` ve `NonFictionBook` türleri.</span><span class="sxs-lookup"><span data-stu-id="d4da0-113">However, you could not then define a type that inherits from both the `FictionBook` and `NonFictionBook` types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d4da0-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="d4da0-114">Example</span></span>  
 <span data-ttu-id="d4da0-115">Aşağıdaki çizimde dört varlık türleriyle kavramsal model gösterir: `Book`, `FictionBook`, `Publisher`, ve `Author`.</span><span class="sxs-lookup"><span data-stu-id="d4da0-115">The diagram below shows a conceptual model with four entity types: `Book`, `FictionBook`, `Publisher`, and `Author`.</span></span> <span data-ttu-id="d4da0-116">`FictionBook` Varlık türü olduğu kaynağından türetilmiş bir tür `Book` varlık türü.</span><span class="sxs-lookup"><span data-stu-id="d4da0-116">The `FictionBook` entity type is a derived type, inheriting from the `Book` entity type.</span></span> <span data-ttu-id="d4da0-117">`FictionBook` Türü devralır `ISBN (Key)`, `Title`, ve `Revision` özelliklerini ve adlı bir ek özellik tanımlar `Genre`.</span><span class="sxs-lookup"><span data-stu-id="d4da0-117">The `FictionBook` type inherits the `ISBN (Key)`, `Title`, and `Revision` properties, and defines an additional property called `Genre`.</span></span>  
  
 <span data-ttu-id="d4da0-118">![Devralma](../../../../docs/framework/data/adonet/media/inheritanceexample.gif "InheritanceExample")</span><span class="sxs-lookup"><span data-stu-id="d4da0-118">![Inheritance](../../../../docs/framework/data/adonet/media/inheritanceexample.gif "InheritanceExample")</span></span>  
  
 <span data-ttu-id="d4da0-119">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) kavramsal şema tanım dili adlı bir etki alanına özgü dil (DSL) kullanır ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) kavramsal modeller tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="d4da0-119">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="d4da0-120">Bir varlık türü aşağıdaki CSDL tanımlar `FictionBook`, devraldığı `Book` türü (örneğin, yukarıdaki diyagramda):</span><span class="sxs-lookup"><span data-stu-id="d4da0-120">The following CSDL defines an entity type, `FictionBook`, that inherits from the `Book` type (as in the diagram above):</span></span>  
  
 [!code-xml[EDM_Example_Model#DerivedType](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books5.edmx#derivedtype)]  
  
## <a name="see-also"></a><span data-ttu-id="d4da0-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d4da0-121">See Also</span></span>  
 [<span data-ttu-id="d4da0-122">Varlık Veri Modeli Temel Kavramları</span><span class="sxs-lookup"><span data-stu-id="d4da0-122">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="d4da0-123">Varlık Veri Modeli</span><span class="sxs-lookup"><span data-stu-id="d4da0-123">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
