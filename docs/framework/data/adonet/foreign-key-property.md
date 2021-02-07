---
description: 'Daha fazla bilgi edinin: yabancı anahtar özelliği'
title: foreign key property
ms.date: 03/30/2017
ms.assetid: 23cb6729-544d-4f67-9ee7-44e8a6545587
ms.openlocfilehash: 1666e4477c09dd5d0ed3d2c35a93ca21824e8a0e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99724134"
---
# <a name="foreign-key-property"></a><span data-ttu-id="bdcdb-103">foreign key property</span><span class="sxs-lookup"><span data-stu-id="bdcdb-103">foreign key property</span></span>

<span data-ttu-id="bdcdb-104">Varlık Veri Modeli (EDM) içindeki bir *yabancı anahtar özelliği* , başka bir varlık türünün [varlık anahtarını](entity-key.md) içeren bir [varlık türünde](entity-type.md) temel bir tür [özelliğidir](property.md) (veya ilkel tür özellikleri kümesi).</span><span class="sxs-lookup"><span data-stu-id="bdcdb-104">A *foreign key property* in the Entity Data Model (EDM) is a primitive type [property](property.md) (or a set of primitive type properties) on an [entity type](entity-type.md) that contains the [entity key](entity-key.md) of another entity type.</span></span>  
  
 <span data-ttu-id="bdcdb-105">Yabancı anahtar özelliği, ilişkisel bir veritabanındaki yabancı anahtar sütunuyla benzerdir.</span><span class="sxs-lookup"><span data-stu-id="bdcdb-105">A foreign key property is analogous to a foreign key column in a relational database.</span></span> <span data-ttu-id="bdcdb-106">Tablolar arasında bir ilişki oluşturmak için bir ilişkisel veritabanında yabancı anahtar sütunlarının kullanıldığı şekilde, varlık türleri arasında [ilişkilendirmeler](association-type.md) kurmak için kavramsal modeldeki yabancı anahtar özellikleri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bdcdb-106">In the same way that foreign key columns are used in a relational database to create relationships between rows in tables, foreign key properties in a conceptual model are used to establish [associations](association-type.md) between entity types.</span></span> <span data-ttu-id="bdcdb-107">Türlerden birinde yabancı anahtar özelliği olduğunda iki varlık türü arasındaki ilişkiyi tanımlamak için bir [başvurusal bütünlük kısıtlaması](referential-integrity-constraint.md) kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bdcdb-107">A [referential integrity constraint](referential-integrity-constraint.md) is used to define an association between two entity types when one of the types has a foreign key property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bdcdb-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="bdcdb-108">Example</span></span>  

 <span data-ttu-id="bdcdb-109">Aşağıdaki diyagramda üç varlık türü olan kavramsal model gösterilmektedir: `Book` , `Publisher` , ve `Author` .</span><span class="sxs-lookup"><span data-stu-id="bdcdb-109">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span> <span data-ttu-id="bdcdb-110">`Book`Varlık türü, `PublisherId` `Publisher` ilişkide bir başvurusal bütünlük kısıtlaması tanımlarken varlık türünün varlık anahtarına başvuran bir özelliğine sahiptir `PublishedBy` .</span><span class="sxs-lookup"><span data-stu-id="bdcdb-110">The `Book` entity type has a property, `PublisherId`, that references the entity key of the `Publisher` entity type when you define a referential integrity constraint on the `PublishedBy` association.</span></span>  
  
 <span data-ttu-id="bdcdb-111">![RefConstraintModel](./media/foreign-key-property/reference-constraint-model.gif "Başvuru kısıtlama modeli örneği")</span><span class="sxs-lookup"><span data-stu-id="bdcdb-111">![RefConstraintModel](./media/foreign-key-property/reference-constraint-model.gif "Example of a referential constraint model")</span></span>  
  
 <span data-ttu-id="bdcdb-112">[ADO.NET Entity Framework](./ef/index.md) kavramsal model tanımlamak için kavramsal şema tanım dili ([csdl](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) adlı bir etki ALANıNA özgü dil (DSL) kullanır.</span><span class="sxs-lookup"><span data-stu-id="bdcdb-112">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="bdcdb-113">Aşağıdaki CSDL, `PublisherId` `PublishedBy` yukarıda gösterilen kavramsal modelde gösterilen ilişkide bir başvurusal bütünlük kısıtlaması tanımlamak için yabancı anahtar özelliğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="bdcdb-113">The following CSDL uses the foreign key property `PublisherId` to define a referential integrity constraint on the `PublishedBy` association shown in the conceptual model shown above.</span></span>  
  
 [!code-xml[EDM_Example_Model#RefConstraint](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#refconstraint)]  
  
## <a name="see-also"></a><span data-ttu-id="bdcdb-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bdcdb-114">See also</span></span>

- [<span data-ttu-id="bdcdb-115">Varlık Veri Modeli Temel Kavramları</span><span class="sxs-lookup"><span data-stu-id="bdcdb-115">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="bdcdb-116">Varlık Veri Modeli</span><span class="sxs-lookup"><span data-stu-id="bdcdb-116">Entity Data Model</span></span>](entity-data-model.md)
