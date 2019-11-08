---
title: foreign key property
ms.date: 03/30/2017
ms.assetid: 23cb6729-544d-4f67-9ee7-44e8a6545587
ms.openlocfilehash: a77f7479ce38cb34830377021157f312916baca4
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738402"
---
# <a name="foreign-key-property"></a><span data-ttu-id="44686-102">foreign key property</span><span class="sxs-lookup"><span data-stu-id="44686-102">foreign key property</span></span>
<span data-ttu-id="44686-103">Varlık Veri Modeli (EDM) içindeki bir *yabancı anahtar özelliği* , başka bir varlık türünün [varlık anahtarını](entity-key.md) içeren bir [varlık türünde](entity-type.md) temel bir tür [özelliğidir](property.md) (veya ilkel tür özellikleri kümesi).</span><span class="sxs-lookup"><span data-stu-id="44686-103">A *foreign key property* in the Entity Data Model (EDM) is a primitive type [property](property.md) (or a set of primitive type properties) on an [entity type](entity-type.md) that contains the [entity key](entity-key.md) of another entity type.</span></span>  
  
 <span data-ttu-id="44686-104">Yabancı anahtar özelliği, ilişkisel bir veritabanındaki yabancı anahtar sütunuyla benzerdir.</span><span class="sxs-lookup"><span data-stu-id="44686-104">A foreign key property is analogous to a foreign key column in a relational database.</span></span> <span data-ttu-id="44686-105">Tablolar arasında bir ilişki oluşturmak için bir ilişkisel veritabanında yabancı anahtar sütunlarının kullanıldığı şekilde, varlık türleri arasında [ilişkilendirmeler](association-type.md) kurmak için kavramsal modeldeki yabancı anahtar özellikleri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="44686-105">In the same way that foreign key columns are used in a relational database to create relationships between rows in tables, foreign key properties in a conceptual model are used to establish [associations](association-type.md) between entity types.</span></span> <span data-ttu-id="44686-106">Türlerden birinde yabancı anahtar özelliği olduğunda iki varlık türü arasındaki ilişkiyi tanımlamak için bir [başvurusal bütünlük kısıtlaması](referential-integrity-constraint.md) kullanılır.</span><span class="sxs-lookup"><span data-stu-id="44686-106">A [referential integrity constraint](referential-integrity-constraint.md) is used to define an association between two entity types when one of the types has a foreign key property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="44686-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="44686-107">Example</span></span>  
 <span data-ttu-id="44686-108">Aşağıdaki diyagramda üç varlık türü olan kavramsal bir model gösterilmektedir: `Book`, `Publisher`ve `Author`.</span><span class="sxs-lookup"><span data-stu-id="44686-108">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span> <span data-ttu-id="44686-109">`Book` varlık türü, `PublishedBy` ilişkilendirmesinde bir başvuru bütünlüğü kısıtlaması tanımlarken `Publisher` varlık türünün varlık anahtarına başvuran `PublisherId`bir özelliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="44686-109">The `Book` entity type has a property, `PublisherId`, that references the entity key of the `Publisher` entity type when you define a referential integrity constraint on the `PublishedBy` association.</span></span>  
  
 <span data-ttu-id="44686-110">![RefConstraintModel](./media/foreign-key-property/reference-constraint-model.gif "Başvuru kısıtlama modeli örneği")</span><span class="sxs-lookup"><span data-stu-id="44686-110">![RefConstraintModel](./media/foreign-key-property/reference-constraint-model.gif "Example of a referential constraint model")</span></span>  
  
 <span data-ttu-id="44686-111">[ADO.NET Entity Framework](./ef/index.md) kavramsal model tanımlamak için kavramsal şema tanım dili ([csdl](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) adlı bir etki ALANıNA özgü dil (DSL) kullanır.</span><span class="sxs-lookup"><span data-stu-id="44686-111">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="44686-112">Aşağıdaki CSDL, yukarıda gösterilen kavramsal modelde gösterilen `PublishedBy` ilişkilendirmesinde bir başvurusal bütünlük kısıtlaması tanımlamak için `PublisherId` yabancı anahtar özelliğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="44686-112">The following CSDL uses the foreign key property `PublisherId` to define a referential integrity constraint on the `PublishedBy` association shown in the conceptual model shown above.</span></span>  
  
 [!code-xml[EDM_Example_Model#RefConstraint](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#refconstraint)]  
  
## <a name="see-also"></a><span data-ttu-id="44686-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="44686-113">See also</span></span>

- [<span data-ttu-id="44686-114">Varlık Veri Modeli Temel Kavramları</span><span class="sxs-lookup"><span data-stu-id="44686-114">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="44686-115">Varlık Veri Modeli</span><span class="sxs-lookup"><span data-stu-id="44686-115">Entity Data Model</span></span>](entity-data-model.md)
