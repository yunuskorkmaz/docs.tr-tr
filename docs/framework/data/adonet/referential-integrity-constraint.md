---
title: referential integrity constraint
description: Varlık türleri arasında geçerli ilişkilerin her zaman mevcut olduğundan emin olmak Varlık Veri Modeli, bilgi tutarlılığı kısıtlamalarını öğrenin.
ms.date: 03/30/2017
ms.assetid: 3d3ba44b-4302-40d8-a7a9-62932e0395e5
ms.openlocfilehash: 65c811b2a12a64870107ff771d5acc64e86f2c1f
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286630"
---
# <a name="referential-integrity-constraint"></a><span data-ttu-id="bd5c8-103">referential integrity constraint</span><span class="sxs-lookup"><span data-stu-id="bd5c8-103">referential integrity constraint</span></span>
<span data-ttu-id="bd5c8-104">Varlık Veri Modeli (EDM) içindeki bir *başvurusal bütünlük kısıtlaması* , ilişkisel bir veritabanındaki başvurusal bütünlük kısıtlamasına benzerdir.</span><span class="sxs-lookup"><span data-stu-id="bd5c8-104">A *referential integrity constraint* in the Entity Data Model (EDM) is similar to a referential integrity constraint in a relational database.</span></span> <span data-ttu-id="bd5c8-105">Bir veritabanı tablosundaki bir sütunun (veya sütunlarının) başka bir tablonun birincil anahtarına başvurmasına benzer şekilde, bir [varlık türünün](entity-type.md) [özelliği](property.md) (veya özellikleri) başka bir varlık türünün [varlık anahtarına](entity-key.md) başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="bd5c8-105">In the same way that a column (or columns) from a database table can reference the primary key of another table, a [property](property.md) (or properties) of an [entity type](entity-type.md) can reference the [entity key](entity-key.md) of another entity type.</span></span> <span data-ttu-id="bd5c8-106">Başvurulan varlık türüne kısıtlamanın *asıl sonu* denir.</span><span class="sxs-lookup"><span data-stu-id="bd5c8-106">The entity type that is referenced is called the *principal end* of the constraint.</span></span> <span data-ttu-id="bd5c8-107">Asıl ucuna başvuran varlık türüne kısıtlamanın *bağımlı sonu* denir.</span><span class="sxs-lookup"><span data-stu-id="bd5c8-107">The entity type that references the principal end is called the *dependent end* of the constraint.</span></span>  
  
 <span data-ttu-id="bd5c8-108">Başvurusal bütünlük kısıtlaması, iki varlık türü arasındaki [ilişkinin](association-type.md) parçası olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="bd5c8-108">A referential integrity constraint is defined as part of an [association](association-type.md) between two entity types.</span></span> <span data-ttu-id="bd5c8-109">Başvurusal bütünlük kısıtlamasının tanımı aşağıdaki bilgileri belirtir:</span><span class="sxs-lookup"><span data-stu-id="bd5c8-109">The definition for a referential integrity constraint specifies the following information:</span></span>  
  
- <span data-ttu-id="bd5c8-110">Kısıtlamanın ana ucu.</span><span class="sxs-lookup"><span data-stu-id="bd5c8-110">The principal end of the constraint.</span></span> <span data-ttu-id="bd5c8-111">(Varlık anahtarına bağımlı uç tarafından başvurulan bir varlık türü.)</span><span class="sxs-lookup"><span data-stu-id="bd5c8-111">(An entity type whose entity key is referenced by the dependent end.)</span></span>  
  
- <span data-ttu-id="bd5c8-112">Sorumlu ucunun varlık anahtarı.</span><span class="sxs-lookup"><span data-stu-id="bd5c8-112">The entity key of the principal end.</span></span>  
  
- <span data-ttu-id="bd5c8-113">Kısıtlamanın bağımlı sonu.</span><span class="sxs-lookup"><span data-stu-id="bd5c8-113">The dependent end of the constraint.</span></span> <span data-ttu-id="bd5c8-114">(Asıl ucunun varlık anahtarına başvuran bir özelliği veya özellikleri olan varlık türü.)</span><span class="sxs-lookup"><span data-stu-id="bd5c8-114">(An entity type that has a property or properties that reference the entity key of the principal end.)</span></span>  
  
- <span data-ttu-id="bd5c8-115">Bağımlı ucun başvuran özelliği veya özellikleri.</span><span class="sxs-lookup"><span data-stu-id="bd5c8-115">The referencing property or properties of the dependent end.</span></span>  
  
 <span data-ttu-id="bd5c8-116">EDM 'daki başvuru bütünlüğü kısıtlamalarının amacı, geçerli ilişkilerin her zaman mevcut olmasını sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="bd5c8-116">The purpose of referential integrity constraints in the EDM is to ensure that valid associations always exist.</span></span> <span data-ttu-id="bd5c8-117">Daha fazla bilgi için bkz. [yabancı anahtar özelliği](foreign-key-property.md).</span><span class="sxs-lookup"><span data-stu-id="bd5c8-117">For more information, see [foreign key property](foreign-key-property.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bd5c8-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="bd5c8-118">Example</span></span>  
 <span data-ttu-id="bd5c8-119">Aşağıdaki diyagramda iki ilişkiye sahip kavramsal bir model gösterilmektedir: `WrittenBy` ve `PublishedBy` .</span><span class="sxs-lookup"><span data-stu-id="bd5c8-119">The diagram below shows a conceptual model with two associations: `WrittenBy` and `PublishedBy`.</span></span> <span data-ttu-id="bd5c8-120">`Book`Varlık türü, `PublisherId` `Publisher` ilişkide bir başvurusal bütünlük kısıtlaması tanımlarken varlık türünün varlık anahtarına başvuran bir özelliğine sahiptir `PublishedBy` .</span><span class="sxs-lookup"><span data-stu-id="bd5c8-120">The `Book` entity type has a property, `PublisherId`, that references the entity key of the `Publisher` entity type when you define a referential integrity constraint on the `PublishedBy` association.</span></span>  
  
 <span data-ttu-id="bd5c8-121">![RefConstraintModel](./media/referential-integrity-constraint/reference-constraint-model.gif "Başvuru kısıtlama modeli örneği")</span><span class="sxs-lookup"><span data-stu-id="bd5c8-121">![RefConstraintModel](./media/referential-integrity-constraint/reference-constraint-model.gif "Example of a referential constraint model")</span></span>  
  
 <span data-ttu-id="bd5c8-122">[ADO.NET Entity Framework](./ef/index.md) kavramsal model tanımlamak için kavramsal şema tanım dili ([csdl](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) adlı bir etki ALANıNA özgü dil (DSL) kullanır.</span><span class="sxs-lookup"><span data-stu-id="bd5c8-122">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="bd5c8-123">Aşağıdaki CSDL, `PublishedBy` Yukarıdaki kavramsal modelde gösterilen ilişkide bir başvurusal bütünlük kısıtlaması tanımlıyor.</span><span class="sxs-lookup"><span data-stu-id="bd5c8-123">The following CSDL defines a referential integrity constraint on the `PublishedBy` association shown in the conceptual model above.</span></span>  
  
 [!code-xml[EDM_Example_Model#RefConstraint](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#refconstraint)]  
  
## <a name="see-also"></a><span data-ttu-id="bd5c8-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bd5c8-124">See also</span></span>

- [<span data-ttu-id="bd5c8-125">Varlık Veri Modeli Temel Kavramları</span><span class="sxs-lookup"><span data-stu-id="bd5c8-125">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="bd5c8-126">Varlık Veri Modeli</span><span class="sxs-lookup"><span data-stu-id="bd5c8-126">Entity Data Model</span></span>](entity-data-model.md)
