---
description: 'Daha fazla bilgi edinin: ilişkilendirme türü'
title: association type
ms.date: 03/30/2017
ms.assetid: 26c409f6-06e8-4441-ac78-1b1076a3c005
ms.openlocfilehash: 4df84d97c798e9f2d06e0f5dce442e05cb4c67b5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99697562"
---
# <a name="association-type"></a><span data-ttu-id="bc599-103">association type</span><span class="sxs-lookup"><span data-stu-id="bc599-103">association type</span></span>

<span data-ttu-id="bc599-104">İlişki *türü* (ilişki olarak da bilinir) VARLıK VERI MODELI (EDM) içindeki ilişkileri açıklamak için temel yapı taşdır.</span><span class="sxs-lookup"><span data-stu-id="bc599-104">An *association type* (also called an association) is the fundamental building block for describing relationships in the Entity Data Model (EDM).</span></span> <span data-ttu-id="bc599-105">Kavramsal modelde, ilişki iki [varlık türü](entity-type.md) (ve gibi) arasındaki ilişkiyi temsil eder `Customer` `Order` .</span><span class="sxs-lookup"><span data-stu-id="bc599-105">In a conceptual model, an association represents a relationship between two [entity types](entity-type.md) (such as `Customer` and `Order`).</span></span> <span data-ttu-id="bc599-106">Bir uygulamada, bir ilişkinin örneği belirli bir ilişkilendirmeyi temsil eder (bir örneği `Customer` ve bir örneği arasındaki ilişki gibi `Order` ).</span><span class="sxs-lookup"><span data-stu-id="bc599-106">In an application, an instance of an association represents a specific association (such as an association between an instance of `Customer` and an instance of `Order`).</span></span> <span data-ttu-id="bc599-107">İlişki örnekleri bir [ilişki kümesinde](association-set.md)mantıksal olarak gruplandırılır.</span><span class="sxs-lookup"><span data-stu-id="bc599-107">Association instances are logically grouped in an [association set](association-set.md).</span></span>  
  
 <span data-ttu-id="bc599-108">Bir ilişki tanımı aşağıdaki bilgileri içerir:</span><span class="sxs-lookup"><span data-stu-id="bc599-108">An association definition contains the following information:</span></span>  
  
- <span data-ttu-id="bc599-109">Benzersiz bir ad.</span><span class="sxs-lookup"><span data-stu-id="bc599-109">A unique name.</span></span> <span data-ttu-id="bc599-110">Istenir</span><span class="sxs-lookup"><span data-stu-id="bc599-110">(Required)</span></span>  
  
- <span data-ttu-id="bc599-111">İlişki içindeki her varlık türü için bir tane olmak üzere iki [ilişkilendirme sonlanır](association-end.md).</span><span class="sxs-lookup"><span data-stu-id="bc599-111">Two [association ends](association-end.md), one for each entity type in the relationship.</span></span> <span data-ttu-id="bc599-112">Istenir</span><span class="sxs-lookup"><span data-stu-id="bc599-112">(Required)</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="bc599-113">İlişki ikiden fazla varlık türü arasındaki ilişkiyi temsil edemez.</span><span class="sxs-lookup"><span data-stu-id="bc599-113">An association cannot represent a relationship among more than two entity types.</span></span> <span data-ttu-id="bc599-114">Bununla birlikte bir ilişkilendirme, ilişki uçları her biri için aynı varlık türünü belirterek kendi kendine ilişki tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="bc599-114">An association can, however, define a self-relationship by specifying the same entity type for each of its association ends.</span></span>  
  
- <span data-ttu-id="bc599-115">[Başvurusal bütünlük kısıtlaması](referential-integrity-constraint.md).</span><span class="sxs-lookup"><span data-stu-id="bc599-115">A [referential integrity constraint](referential-integrity-constraint.md).</span></span> <span data-ttu-id="bc599-116">(İsteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="bc599-116">(Optional)</span></span>  
  
 <span data-ttu-id="bc599-117">Her ilişkilendirme ucu, ilişkilendirmenin bir ucunda olabilecek varlık türü örneklerinin sayısını gösteren bir [ilişki ucu çeşitliliği](association-end-multiplicity.md) belirtmelidir.</span><span class="sxs-lookup"><span data-stu-id="bc599-117">Each association end must specify an [association end multiplicity](association-end-multiplicity.md) that indicates the number of entity type instances that can be at one end of the association.</span></span> <span data-ttu-id="bc599-118">Bir ilişki uç çoğulluğu bir (1), sıfır veya bir (0.. 1) veya çok () değerine sahip olabilir \* .</span><span class="sxs-lookup"><span data-stu-id="bc599-118">An association end multiplicity can have a value of one (1), zero or one (0..1), or many (\*).</span></span> <span data-ttu-id="bc599-119">Bir ilişkinin bir sonundaki varlık türü örneklerine, bir varlık türü üzerinde gösterilmeleri durumunda [Gezinti özellikleri](navigation-property.md) veya yabancı anahtarlar üzerinden erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="bc599-119">Entity type instances at one end of an association can be accessed through [navigation properties](navigation-property.md) or foreign keys if they are exposed on an entity type.</span></span> <span data-ttu-id="bc599-120">Daha fazla bilgi için bkz. [varlık veri modeli: yabancı anahtarlar](foreign-key-property.md).</span><span class="sxs-lookup"><span data-stu-id="bc599-120">For more information, see [Entity Data Model: Foreign Keys](foreign-key-property.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc599-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="bc599-121">Example</span></span>  

 <span data-ttu-id="bc599-122">Aşağıdaki diyagramda iki ilişkiye sahip kavramsal bir model gösterilmektedir: `PublishedBy` ve `WrittenBy` .</span><span class="sxs-lookup"><span data-stu-id="bc599-122">The diagram below shows a conceptual model with two associations: `PublishedBy` and `WrittenBy`.</span></span> <span data-ttu-id="bc599-123">İlişkilendirme için ilişkilendirme sonlanır `PublishedBy` `Book` ve `Publisher` varlık türleridir.</span><span class="sxs-lookup"><span data-stu-id="bc599-123">The association ends for the `PublishedBy` association are the `Book` and `Publisher` entity types.</span></span> <span data-ttu-id="bc599-124">Ucun çoğulluğu `Publisher` bir (1) ve ucun çoğulluğu `Book` birçok (), bir \* yayımcının çok sayıda kitap yayımladığını ve bir kitabın bir yayımcı tarafından yayımlandığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="bc599-124">The multiplicity of the `Publisher` end is one (1) and the multiplicity of the `Book` end is many (\*), indicating that a publisher publishes many books and a book is published by one publisher.</span></span>  
  
 ![Üç varlık türüne sahip örnek model](./media/association-type/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="bc599-126">[ADO.NET Entity Framework](./ef/index.md) kavramsal model tanımlamak için kavramsal şema tanım dili ([csdl](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) adlı bir etki ALANıNA özgü dil (DSL) kullanır.</span><span class="sxs-lookup"><span data-stu-id="bc599-126">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="bc599-127">Aşağıdaki CSDL, `PublishedBy` Yukarıdaki diyagramda gösterilen ilişkilendirmeyi tanımlar:</span><span class="sxs-lookup"><span data-stu-id="bc599-127">The following CSDL defines the `PublishedBy` association shown in the diagram above:</span></span>  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## <a name="see-also"></a><span data-ttu-id="bc599-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bc599-128">See also</span></span>

- [<span data-ttu-id="bc599-129">Varlık Veri Modeli Temel Kavramları</span><span class="sxs-lookup"><span data-stu-id="bc599-129">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="bc599-130">Varlık Veri Modeli</span><span class="sxs-lookup"><span data-stu-id="bc599-130">Entity Data Model</span></span>](entity-data-model.md)
