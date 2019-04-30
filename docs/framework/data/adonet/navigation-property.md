---
title: Gezinme özelliğinin - ADO.NET
ms.date: 03/30/2017
ms.assetid: d0bf1a6a-1d84-484c-b7c3-b410fd8dc0b1
ms.openlocfilehash: b57ecf9329aa9ea8afc07507613c9e3961bfd0a9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61772272"
---
# <a name="navigation-property"></a><span data-ttu-id="784ca-102">Gezinme özelliği</span><span class="sxs-lookup"><span data-stu-id="784ca-102">Navigation property</span></span>

<span data-ttu-id="784ca-103">A *gezinti özelliği* üzerinde isteğe bağlı bir özellik olan bir [varlık türü](entity-type.md) olanak tanıyan bir gezinti için [son](association-end.md) , bir [ilişkilendirme](association-type.md) için diğer sonu.</span><span class="sxs-lookup"><span data-stu-id="784ca-103">A *navigation property* is an optional property on an [entity type](entity-type.md) that allows for navigation from one [end](association-end.md) of an [association](association-type.md) to the other end.</span></span> <span data-ttu-id="784ca-104">Diğer aksine [özellikleri](property.md), gezinti özellikleri veri taşıyan değil.</span><span class="sxs-lookup"><span data-stu-id="784ca-104">Unlike other [properties](property.md), navigation properties do not carry data.</span></span>

<span data-ttu-id="784ca-105">Bir gezinti özelliği tanımı aşağıdakileri içerir:</span><span class="sxs-lookup"><span data-stu-id="784ca-105">A navigation property definition includes the following:</span></span>

- <span data-ttu-id="784ca-106">Bir ad.</span><span class="sxs-lookup"><span data-stu-id="784ca-106">A name.</span></span> <span data-ttu-id="784ca-107">(Gerekli)</span><span class="sxs-lookup"><span data-stu-id="784ca-107">(Required)</span></span>

- <span data-ttu-id="784ca-108">Bu varlıklardan ilişkilendirme.</span><span class="sxs-lookup"><span data-stu-id="784ca-108">The association that it navigates.</span></span> <span data-ttu-id="784ca-109">(Gerekli)</span><span class="sxs-lookup"><span data-stu-id="784ca-109">(Required)</span></span>

- <span data-ttu-id="784ca-110">Bu varlıklardan ilişkilendirmenin sona erer.</span><span class="sxs-lookup"><span data-stu-id="784ca-110">The ends of the association that it navigates.</span></span> <span data-ttu-id="784ca-111">(Gerekli)</span><span class="sxs-lookup"><span data-stu-id="784ca-111">(Required)</span></span>

<span data-ttu-id="784ca-112">Gezinti özellikleri her iki varlık türlerini ilişkilendirme ucunda isteğe bağlı olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="784ca-112">Note that navigation properties are optional on both entity types at the ends of an association.</span></span> <span data-ttu-id="784ca-113">İlişkilendirme sonunda bir varlık türünün gezinme özelliğinin tanımlarsanız, ilişkinin diğer ucundaki varlık türünün gezinme özelliğinin tanımlamak zorunda değil.</span><span class="sxs-lookup"><span data-stu-id="784ca-113">If you define a navigation property on one entity type at the end of an association, you do not have to define a navigation property on the entity type at the other end of the association.</span></span>

<span data-ttu-id="784ca-114">Veri türü bir gezinti özelliği tarafından belirlenir [çoğulluk](association-end-multiplicity.md) kendi uzak [ilişkilendirme end](association-end.md).</span><span class="sxs-lookup"><span data-stu-id="784ca-114">The data type of a navigation property is determined by the [multiplicity](association-end-multiplicity.md) of its remote [association end](association-end.md).</span></span> <span data-ttu-id="784ca-115">Örneğin, bir gezinti özelliği varsayalım `OrdersNavProp`, bulunuyor. bir `Customer` varlık türü ve arasında bir-çok ilişkisi gider `Customer` ve `Order`.</span><span class="sxs-lookup"><span data-stu-id="784ca-115">For example, suppose a navigation property, `OrdersNavProp`, exists on a `Customer` entity type and navigates a one-to-many association between `Customer` and `Order`.</span></span> <span data-ttu-id="784ca-116">Gezinti özelliği için Uzak ilişkilendirme end çok çeşitlilik sahip olduğundan (\*), kendi veri türüne koleksiyonudur (, `Order`).</span><span class="sxs-lookup"><span data-stu-id="784ca-116">Because the remote association end for the navigation property has multiplicity of many (\*), its data type is a collection (of `Order`).</span></span> <span data-ttu-id="784ca-117">Benzer şekilde, bir gezinti özelliği, `CustomerNavProp`, bulunuyor `Order` varlık türü, veri türü olacak `Customer`, uzak uç çokluğu bir (1) olduğundan.</span><span class="sxs-lookup"><span data-stu-id="784ca-117">Similarly, if a navigation property, `CustomerNavProp`, exists on the `Order` entity type, its data type would be `Customer`, because the multiplicity of the remote end is one (1).</span></span>

## <a name="example"></a><span data-ttu-id="784ca-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="784ca-118">Example</span></span>

<span data-ttu-id="784ca-119">Varlık üç kavramsal bir modelle Aşağıdaki diyagramda gösterilmektedir: `Book`, `Publisher`, ve `Author`.</span><span class="sxs-lookup"><span data-stu-id="784ca-119">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span> <span data-ttu-id="784ca-120">Gezinti özellikleri `Publisher` ve `Authors`, kitap varlık türünde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="784ca-120">Navigation properties, `Publisher` and `Authors`, are defined on the Book entity type.</span></span> <span data-ttu-id="784ca-121">Gezinti özelliği `Books` hem Yayımcı varlık türü üzerinde tanımlanan ve `Author` varlık türü.</span><span class="sxs-lookup"><span data-stu-id="784ca-121">Navigation property `Books` is defined on both the Publisher entity type and the `Author` entity type.</span></span>

 ![Kavramsal bir modelle üç varlık türlerini gösteren diyagram.](./media/navigation-property/conceptual-model-entity-types-associations.gif)  

<span data-ttu-id="784ca-123">[ADO.NET Entity Framework](./ef/index.md) kavramsal şema tanım dili olarak adlandırılan bir etki alanına özgü dil (DSL) kullanır ([CSDL](./ef/language-reference/csdl-specification.md)) kavramsal modeller tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="784ca-123">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](./ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="784ca-124">Aşağıdaki CSDL tanımlar `Book` Yukarıdaki diyagramda gösterilen varlık türü:</span><span class="sxs-lookup"><span data-stu-id="784ca-124">The following CSDL defines the `Book` entity type shown in the diagram above:</span></span>

[!code-xml[EDM_Example_Model#EntityExample](~/samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]

<span data-ttu-id="784ca-125">XML özniteliği bir gezinti özelliği tanımlamak gereken bilgileri iletişim kurmak için kullanıldığını unutmayın: Öznitelik `Name` özelliğin adını içeren `Relationship` bunu gider, ilişkilendirmenin adı içerir ve `FromRole` ve `ToRole` ilişki sonu içerir.</span><span class="sxs-lookup"><span data-stu-id="784ca-125">Note that XML attributes are used to communicate the information necessary to define a navigation property: The attribute `Name` contains the name of the property, `Relationship` contains the name of the association it navigates, and `FromRole` and `ToRole` contain the ends of the association.</span></span>

## <a name="see-also"></a><span data-ttu-id="784ca-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="784ca-126">See also</span></span>

- [<span data-ttu-id="784ca-127">Varlık Veri Modeli Temel Kavramları</span><span class="sxs-lookup"><span data-stu-id="784ca-127">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="784ca-128">Varlık Veri Modeli</span><span class="sxs-lookup"><span data-stu-id="784ca-128">Entity Data Model</span></span>](entity-data-model.md)
- [<span data-ttu-id="784ca-129">İlişkiler, gezinti özellikleri ve yabancı anahtarlar</span><span class="sxs-lookup"><span data-stu-id="784ca-129">Relationships, navigation properties and foreign keys</span></span>](/ef/ef6/fundamentals/relationships)
