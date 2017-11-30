---
title: "başvuru bütünlüğü kısıtlaması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3d3ba44b-4302-40d8-a7a9-62932e0395e5
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 10e469838073b4cf1faba1704b88b47f30b8b3d0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="referential-integrity-constraint"></a><span data-ttu-id="e0369-102">başvuru bütünlüğü kısıtlaması</span><span class="sxs-lookup"><span data-stu-id="e0369-102">referential integrity constraint</span></span>
<span data-ttu-id="e0369-103">A *başvuru bütünlüğü kısıtlaması* varlık veri modeli (EDM) ilişkisel bir veritabanındaki bir başvuru bütünlüğü kısıtlaması benzer.</span><span class="sxs-lookup"><span data-stu-id="e0369-103">A *referential integrity constraint* in the Entity Data Model (EDM) is similar to a referential integrity constraint in a relational database.</span></span> <span data-ttu-id="e0369-104">Bir veritabanı tablodaki bir sütuna (veya sütun) başka bir tablonun birincil anahtarı başvurabilir aynı şekilde bir [özelliği](../../../../docs/framework/data/adonet/property.md) (veya Özellikler), bir [varlık türü](../../../../docs/framework/data/adonet/entity-type.md) başvurabilir [Varlık anahtarı ](../../../../docs/framework/data/adonet/entity-key.md) başka bir varlık türü.</span><span class="sxs-lookup"><span data-stu-id="e0369-104">In the same way that a column (or columns) from a database table can reference the primary key of another table, a [property](../../../../docs/framework/data/adonet/property.md) (or properties) of an [entity type](../../../../docs/framework/data/adonet/entity-type.md) can reference the [entity key](../../../../docs/framework/data/adonet/entity-key.md) of another entity type.</span></span> <span data-ttu-id="e0369-105">Başvurulan varlık türü olarak adlandırılan *asıl ucu* kısıtlaması.</span><span class="sxs-lookup"><span data-stu-id="e0369-105">The entity type that is referenced is called the *principal end* of the constraint.</span></span> <span data-ttu-id="e0369-106">Asıl ucu başvuruda bulunan varlık türü olarak adlandırılan *bağımlı uç* kısıtlaması.</span><span class="sxs-lookup"><span data-stu-id="e0369-106">The entity type that references the principal end is called the *dependent end* of the constraint.</span></span>  
  
 <span data-ttu-id="e0369-107">Bir başvuru bütünlüğü kısıtlamasının bir parçası olarak tanımlanan bir [ilişkilendirme](../../../../docs/framework/data/adonet/association-type.md) iki varlık türleri arasındaki.</span><span class="sxs-lookup"><span data-stu-id="e0369-107">A referential integrity constraint is defined as part of an [association](../../../../docs/framework/data/adonet/association-type.md) between two entity types.</span></span> <span data-ttu-id="e0369-108">Tanımı bir başvuru bütünlüğü kısıtlaması için aşağıdaki bilgileri belirtir:</span><span class="sxs-lookup"><span data-stu-id="e0369-108">The definition for a referential integrity constraint specifies the following information:</span></span>  
  
-   <span data-ttu-id="e0369-109">Kısıtlamasının asıl uç.</span><span class="sxs-lookup"><span data-stu-id="e0369-109">The principal end of the constraint.</span></span> <span data-ttu-id="e0369-110">(Yalnızca Varlık anahtarı bağımlı uç tarafından başvurulan bir varlık türü.)</span><span class="sxs-lookup"><span data-stu-id="e0369-110">(An entity type whose entity key is referenced by the dependent end.)</span></span>  
  
-   <span data-ttu-id="e0369-111">Asıl ucu Varlık anahtarı.</span><span class="sxs-lookup"><span data-stu-id="e0369-111">The entity key of the principal end.</span></span>  
  
-   <span data-ttu-id="e0369-112">Kısıtlamasının bağımlı uç.</span><span class="sxs-lookup"><span data-stu-id="e0369-112">The dependent end of the constraint.</span></span> <span data-ttu-id="e0369-113">(Bir özellik veya asıl ucu Varlık anahtarı başvuran özellikleri olan bir varlık türü.)</span><span class="sxs-lookup"><span data-stu-id="e0369-113">(An entity type that has a property or properties that reference the entity key of the principal end.)</span></span>  
  
-   <span data-ttu-id="e0369-114">Başvuruda bulunan özellik veya bağımlı uç özellikleri.</span><span class="sxs-lookup"><span data-stu-id="e0369-114">The referencing property or properties of the dependent end.</span></span>  
  
 <span data-ttu-id="e0369-115">EDM başvuru bütünlüğü kısıtlamalarını amacı geçerli ilişkilendirmeleri her zaman var olduğundan emin olmaktır.</span><span class="sxs-lookup"><span data-stu-id="e0369-115">The purpose of referential integrity constraints in the EDM is to ensure that valid associations always exist.</span></span> <span data-ttu-id="e0369-116">Daha fazla bilgi için bkz: [yabancı anahtar özelliği](../../../../docs/framework/data/adonet/foreign-key-property.md).</span><span class="sxs-lookup"><span data-stu-id="e0369-116">For more information, see [foreign key property](../../../../docs/framework/data/adonet/foreign-key-property.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0369-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="e0369-117">Example</span></span>  
 <span data-ttu-id="e0369-118">Aşağıdaki diyagramda iki ilişkilendirmeleri kavramsal modelle gösterir: `WrittenBy` ve `PublishedBy`.</span><span class="sxs-lookup"><span data-stu-id="e0369-118">The diagram below shows a conceptual model with two associations: `WrittenBy` and `PublishedBy`.</span></span> <span data-ttu-id="e0369-119">`Book` Varlık türüne sahip bir özellik `PublisherId`, varlık anahtarı başvuran `Publisher` bir başvuru bütünlüğü kısıtlaması tanımlarken varlık türü `PublishedBy` ilişkilendirme.</span><span class="sxs-lookup"><span data-stu-id="e0369-119">The `Book` entity type has a property, `PublisherId`, that references the entity key of the `Publisher` entity type when you define a referential integrity constraint on the `PublishedBy` association.</span></span>  
  
 <span data-ttu-id="e0369-120">![RefConstraintModel](../../../../docs/framework/data/adonet/media/refconstraintmodel.gif "RefConstraintModel")</span><span class="sxs-lookup"><span data-stu-id="e0369-120">![RefConstraintModel](../../../../docs/framework/data/adonet/media/refconstraintmodel.gif "RefConstraintModel")</span></span>  
  
 <span data-ttu-id="e0369-121">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) kavramsal şema tanım dili adlı bir etki alanına özgü dil (DSL) kullanır ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) kavramsal modeller tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="e0369-121">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="e0369-122">Aşağıdaki CSDL üzerindeki bir başvuru bütünlüğü kısıtlaması tanımlar `PublishedBy` yukarıdaki kavramsal modelde gösterilen ilişkilendirme.</span><span class="sxs-lookup"><span data-stu-id="e0369-122">The following CSDL defines a referential integrity constraint on the `PublishedBy` association shown in the conceptual model above.</span></span>  
  
 [!code-xml[EDM_Example_Model#RefConstraint](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#refconstraint)]  
  
## <a name="see-also"></a><span data-ttu-id="e0369-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e0369-123">See Also</span></span>  
 [<span data-ttu-id="e0369-124">Varlık veri modeli temel kavramları</span><span class="sxs-lookup"><span data-stu-id="e0369-124">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="e0369-125">Varlık veri modeli</span><span class="sxs-lookup"><span data-stu-id="e0369-125">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
