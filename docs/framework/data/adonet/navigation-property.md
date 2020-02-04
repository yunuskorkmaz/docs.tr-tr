---
title: Gezinti özelliği
ms.date: 03/30/2017
ms.assetid: d0bf1a6a-1d84-484c-b7c3-b410fd8dc0b1
ms.openlocfilehash: b6c286e63322a66be0407c864295a20685df2b7f
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/04/2020
ms.locfileid: "76980164"
---
# <a name="navigation-property"></a><span data-ttu-id="7e6ea-102">Gezinti özelliği</span><span class="sxs-lookup"><span data-stu-id="7e6ea-102">Navigation property</span></span>

<span data-ttu-id="7e6ea-103">Bir *gezinti özelliği* , bir [ilişkinin](association-type.md) bir [sonundan](association-end.md) diğer bir uca gezinmesine izin veren bir [varlık türü](entity-type.md) üzerinde isteğe bağlı bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="7e6ea-103">A *navigation property* is an optional property on an [entity type](entity-type.md) that allows for navigation from one [end](association-end.md) of an [association](association-type.md) to the other end.</span></span> <span data-ttu-id="7e6ea-104">Diğer [özelliklerden](property.md)farklı olarak, gezinti özellikleri verileri taşımaz.</span><span class="sxs-lookup"><span data-stu-id="7e6ea-104">Unlike other [properties](property.md), navigation properties do not carry data.</span></span>

<span data-ttu-id="7e6ea-105">Bir gezinti özelliği tanımı şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="7e6ea-105">A navigation property definition includes the following:</span></span>

- <span data-ttu-id="7e6ea-106">Bir ad.</span><span class="sxs-lookup"><span data-stu-id="7e6ea-106">A name.</span></span> <span data-ttu-id="7e6ea-107">Istenir</span><span class="sxs-lookup"><span data-stu-id="7e6ea-107">(Required)</span></span>

- <span data-ttu-id="7e6ea-108">Gittiği ilişki.</span><span class="sxs-lookup"><span data-stu-id="7e6ea-108">The association that it navigates.</span></span> <span data-ttu-id="7e6ea-109">Istenir</span><span class="sxs-lookup"><span data-stu-id="7e6ea-109">(Required)</span></span>

- <span data-ttu-id="7e6ea-110">Gezindiğinde ilişkilendirmenin uçları.</span><span class="sxs-lookup"><span data-stu-id="7e6ea-110">The ends of the association that it navigates.</span></span> <span data-ttu-id="7e6ea-111">Istenir</span><span class="sxs-lookup"><span data-stu-id="7e6ea-111">(Required)</span></span>

<span data-ttu-id="7e6ea-112">Gezinti özelliklerinin, bir ilişkinin sonundaki her iki varlık türü üzerinde isteğe bağlı olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="7e6ea-112">Note that navigation properties are optional on both entity types at the ends of an association.</span></span> <span data-ttu-id="7e6ea-113">Bir ilişkinin sonundaki bir varlık türünde bir gezinti özelliği tanımlarsanız, ilişkilendirmenin diğer sonundaki varlık türünde bir gezinti özelliği tanımlamanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="7e6ea-113">If you define a navigation property on one entity type at the end of an association, you do not have to define a navigation property on the entity type at the other end of the association.</span></span>

<span data-ttu-id="7e6ea-114">Gezinti özelliğinin veri türü, uzak [ilişki ucunun](association-end.md) [çoğulluğu](association-end-multiplicity.md) tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="7e6ea-114">The data type of a navigation property is determined by the [multiplicity](association-end-multiplicity.md) of its remote [association end](association-end.md).</span></span> <span data-ttu-id="7e6ea-115">Örneğin, bir `Customer` varlık türünde `OrdersNavProp`bir gezinti özelliği olduğunu varsayalım ve `Customer` ile `Order`arasında bire çok ilişkilendirmeyi gider.</span><span class="sxs-lookup"><span data-stu-id="7e6ea-115">For example, suppose a navigation property, `OrdersNavProp`, exists on a `Customer` entity type and navigates a one-to-many association between `Customer` and `Order`.</span></span> <span data-ttu-id="7e6ea-116">Gezinti özelliği için uzak ilişki ucunun çok sayıda (\*) çoğulluğu olduğundan, veri türü bir koleksiyon (`Order`) olur.</span><span class="sxs-lookup"><span data-stu-id="7e6ea-116">Because the remote association end for the navigation property has multiplicity of many (\*), its data type is a collection (of `Order`).</span></span> <span data-ttu-id="7e6ea-117">Benzer şekilde, `Order` varlık türünde bir gezinti özelliği varsa `CustomerNavProp`, uzak uçtaki çoğulluğu bir (1) olduğundan, veri türü `Customer`olur.</span><span class="sxs-lookup"><span data-stu-id="7e6ea-117">Similarly, if a navigation property, `CustomerNavProp`, exists on the `Order` entity type, its data type would be `Customer`, because the multiplicity of the remote end is one (1).</span></span>

## <a name="example"></a><span data-ttu-id="7e6ea-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="7e6ea-118">Example</span></span>

<span data-ttu-id="7e6ea-119">Aşağıdaki diyagramda üç varlık türü olan kavramsal bir model gösterilmektedir: `Book`, `Publisher`ve `Author`.</span><span class="sxs-lookup"><span data-stu-id="7e6ea-119">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span> <span data-ttu-id="7e6ea-120">Gezinti özellikleri, `Publisher` ve `Authors`, kitap varlık türü üzerinde tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="7e6ea-120">Navigation properties, `Publisher` and `Authors`, are defined on the Book entity type.</span></span> <span data-ttu-id="7e6ea-121">Gezinti özelliği `Books` hem Yayımcı varlık türü hem de `Author` varlık türü üzerinde tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="7e6ea-121">Navigation property `Books` is defined on both the Publisher entity type and the `Author` entity type.</span></span>

 ![Üç varlık türü ile kavramsal bir modeli gösteren diyagram.](./media/navigation-property/conceptual-model-entity-types-associations.gif)  

<span data-ttu-id="7e6ea-123">[ADO.NET Entity Framework](./ef/index.md) kavramsal model tanımlamak için kavramsal şema tanım dili ([csdl](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) adlı bir etki ALANıNA özgü dil (DSL) kullanır.</span><span class="sxs-lookup"><span data-stu-id="7e6ea-123">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="7e6ea-124">Aşağıdaki CSDL, Yukarıdaki diyagramda gösterilen `Book` varlık türünü tanımlar:</span><span class="sxs-lookup"><span data-stu-id="7e6ea-124">The following CSDL defines the `Book` entity type shown in the diagram above:</span></span>

[!code-xml[EDM_Example_Model#EntityExample](~/samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]

<span data-ttu-id="7e6ea-125">XML özniteliklerinin bir gezinti özelliği tanımlamak için gereken bilgileri iletmek için kullanıldığını unutmayın: öznitelik `Name` özelliğin adını, `Relationship` gezindiği ilişkinin adını içerir ve `FromRole` ve `ToRole` ilişkinin uçlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="7e6ea-125">Note that XML attributes are used to communicate the information necessary to define a navigation property: The attribute `Name` contains the name of the property, `Relationship` contains the name of the association it navigates, and `FromRole` and `ToRole` contain the ends of the association.</span></span>

## <a name="see-also"></a><span data-ttu-id="7e6ea-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7e6ea-126">See also</span></span>

- [<span data-ttu-id="7e6ea-127">Varlık Veri Modeli Temel Kavramları</span><span class="sxs-lookup"><span data-stu-id="7e6ea-127">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="7e6ea-128">Varlık Veri Modeli</span><span class="sxs-lookup"><span data-stu-id="7e6ea-128">Entity Data Model</span></span>](entity-data-model.md)
- [<span data-ttu-id="7e6ea-129">İlişkiler, gezinti özellikleri ve yabancı anahtarlar</span><span class="sxs-lookup"><span data-stu-id="7e6ea-129">Relationships, navigation properties and foreign keys</span></span>](/ef/ef6/fundamentals/relationships)
