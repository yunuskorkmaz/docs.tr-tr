---
title: association type
ms.date: 03/30/2017
ms.assetid: 26c409f6-06e8-4441-ac78-1b1076a3c005
ms.openlocfilehash: 6f6eb91d4f292c7e98b8c9a1d814ed6bf71b7370
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198762"
---
# <a name="association-type"></a><span data-ttu-id="c1f96-102">association type</span><span class="sxs-lookup"><span data-stu-id="c1f96-102">association type</span></span>

<span data-ttu-id="c1f96-103">İlişki *türü* (ilişki olarak da bilinir) VARLıK VERI MODELI (EDM) içindeki ilişkileri açıklamak için temel yapı taşdır.</span><span class="sxs-lookup"><span data-stu-id="c1f96-103">An *association type* (also called an association) is the fundamental building block for describing relationships in the Entity Data Model (EDM).</span></span> <span data-ttu-id="c1f96-104">Kavramsal modelde, ilişki iki [varlık türü](entity-type.md) (ve gibi) arasındaki ilişkiyi temsil eder `Customer` `Order` .</span><span class="sxs-lookup"><span data-stu-id="c1f96-104">In a conceptual model, an association represents a relationship between two [entity types](entity-type.md) (such as `Customer` and `Order`).</span></span> <span data-ttu-id="c1f96-105">Bir uygulamada, bir ilişkinin örneği belirli bir ilişkilendirmeyi temsil eder (bir örneği `Customer` ve bir örneği arasındaki ilişki gibi `Order` ).</span><span class="sxs-lookup"><span data-stu-id="c1f96-105">In an application, an instance of an association represents a specific association (such as an association between an instance of `Customer` and an instance of `Order`).</span></span> <span data-ttu-id="c1f96-106">İlişki örnekleri bir [ilişki kümesinde](association-set.md)mantıksal olarak gruplandırılır.</span><span class="sxs-lookup"><span data-stu-id="c1f96-106">Association instances are logically grouped in an [association set](association-set.md).</span></span>  
  
 <span data-ttu-id="c1f96-107">Bir ilişki tanımı aşağıdaki bilgileri içerir:</span><span class="sxs-lookup"><span data-stu-id="c1f96-107">An association definition contains the following information:</span></span>  
  
- <span data-ttu-id="c1f96-108">Benzersiz bir ad.</span><span class="sxs-lookup"><span data-stu-id="c1f96-108">A unique name.</span></span> <span data-ttu-id="c1f96-109">Istenir</span><span class="sxs-lookup"><span data-stu-id="c1f96-109">(Required)</span></span>  
  
- <span data-ttu-id="c1f96-110">İlişki içindeki her varlık türü için bir tane olmak üzere iki [ilişkilendirme sonlanır](association-end.md).</span><span class="sxs-lookup"><span data-stu-id="c1f96-110">Two [association ends](association-end.md), one for each entity type in the relationship.</span></span> <span data-ttu-id="c1f96-111">Istenir</span><span class="sxs-lookup"><span data-stu-id="c1f96-111">(Required)</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="c1f96-112">İlişki ikiden fazla varlık türü arasındaki ilişkiyi temsil edemez.</span><span class="sxs-lookup"><span data-stu-id="c1f96-112">An association cannot represent a relationship among more than two entity types.</span></span> <span data-ttu-id="c1f96-113">Bununla birlikte bir ilişkilendirme, ilişki uçları her biri için aynı varlık türünü belirterek kendi kendine ilişki tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="c1f96-113">An association can, however, define a self-relationship by specifying the same entity type for each of its association ends.</span></span>  
  
- <span data-ttu-id="c1f96-114">[Başvurusal bütünlük kısıtlaması](referential-integrity-constraint.md).</span><span class="sxs-lookup"><span data-stu-id="c1f96-114">A [referential integrity constraint](referential-integrity-constraint.md).</span></span> <span data-ttu-id="c1f96-115">(İsteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="c1f96-115">(Optional)</span></span>  
  
 <span data-ttu-id="c1f96-116">Her ilişkilendirme ucu, ilişkilendirmenin bir ucunda olabilecek varlık türü örneklerinin sayısını gösteren bir [ilişki ucu çeşitliliği](association-end-multiplicity.md) belirtmelidir.</span><span class="sxs-lookup"><span data-stu-id="c1f96-116">Each association end must specify an [association end multiplicity](association-end-multiplicity.md) that indicates the number of entity type instances that can be at one end of the association.</span></span> <span data-ttu-id="c1f96-117">Bir ilişki uç çoğulluğu bir (1), sıfır veya bir (0.. 1) veya çok () değerine sahip olabilir \* .</span><span class="sxs-lookup"><span data-stu-id="c1f96-117">An association end multiplicity can have a value of one (1), zero or one (0..1), or many (\*).</span></span> <span data-ttu-id="c1f96-118">Bir ilişkinin bir sonundaki varlık türü örneklerine, bir varlık türü üzerinde gösterilmeleri durumunda [Gezinti özellikleri](navigation-property.md) veya yabancı anahtarlar üzerinden erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="c1f96-118">Entity type instances at one end of an association can be accessed through [navigation properties](navigation-property.md) or foreign keys if they are exposed on an entity type.</span></span> <span data-ttu-id="c1f96-119">Daha fazla bilgi için bkz. [varlık veri modeli: yabancı anahtarlar](foreign-key-property.md).</span><span class="sxs-lookup"><span data-stu-id="c1f96-119">For more information, see [Entity Data Model: Foreign Keys](foreign-key-property.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1f96-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="c1f96-120">Example</span></span>  

 <span data-ttu-id="c1f96-121">Aşağıdaki diyagramda iki ilişkiye sahip kavramsal bir model gösterilmektedir: `PublishedBy` ve `WrittenBy` .</span><span class="sxs-lookup"><span data-stu-id="c1f96-121">The diagram below shows a conceptual model with two associations: `PublishedBy` and `WrittenBy`.</span></span> <span data-ttu-id="c1f96-122">İlişkilendirme için ilişkilendirme sonlanır `PublishedBy` `Book` ve `Publisher` varlık türleridir.</span><span class="sxs-lookup"><span data-stu-id="c1f96-122">The association ends for the `PublishedBy` association are the `Book` and `Publisher` entity types.</span></span> <span data-ttu-id="c1f96-123">Ucun çoğulluğu `Publisher` bir (1) ve ucun çoğulluğu `Book` birçok (), bir \* yayımcının çok sayıda kitap yayımladığını ve bir kitabın bir yayımcı tarafından yayımlandığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c1f96-123">The multiplicity of the `Publisher` end is one (1) and the multiplicity of the `Book` end is many (\*), indicating that a publisher publishes many books and a book is published by one publisher.</span></span>  
  
 ![Üç varlık türüne sahip örnek model](./media/association-type/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="c1f96-125">[ADO.NET Entity Framework](./ef/index.md) kavramsal model tanımlamak için kavramsal şema tanım dili ([csdl](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) adlı bir etki ALANıNA özgü dil (DSL) kullanır.</span><span class="sxs-lookup"><span data-stu-id="c1f96-125">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="c1f96-126">Aşağıdaki CSDL, `PublishedBy` Yukarıdaki diyagramda gösterilen ilişkilendirmeyi tanımlar:</span><span class="sxs-lookup"><span data-stu-id="c1f96-126">The following CSDL defines the `PublishedBy` association shown in the diagram above:</span></span>  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## <a name="see-also"></a><span data-ttu-id="c1f96-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c1f96-127">See also</span></span>

- [<span data-ttu-id="c1f96-128">Varlık Veri Modeli Temel Kavramları</span><span class="sxs-lookup"><span data-stu-id="c1f96-128">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="c1f96-129">Varlık Veri Modeli</span><span class="sxs-lookup"><span data-stu-id="c1f96-129">Entity Data Model</span></span>](entity-data-model.md)
