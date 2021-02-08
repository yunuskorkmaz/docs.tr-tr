---
description: 'Daha fazla bilgi edinin: gezinti özelliği'
title: Gezinti özelliği
ms.date: 03/30/2017
ms.assetid: d0bf1a6a-1d84-484c-b7c3-b410fd8dc0b1
ms.openlocfilehash: 4655c8ef1b18972697e41fa1c7c6185945335aa1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786244"
---
# <a name="navigation-property"></a><span data-ttu-id="182f9-103">Gezinti özelliği</span><span class="sxs-lookup"><span data-stu-id="182f9-103">Navigation property</span></span>

<span data-ttu-id="182f9-104">Bir *gezinti özelliği* , bir [ilişkinin](association-type.md) bir [sonundan](association-end.md) diğer bir uca gezinmesine izin veren bir [varlık türü](entity-type.md) üzerinde isteğe bağlı bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="182f9-104">A *navigation property* is an optional property on an [entity type](entity-type.md) that allows for navigation from one [end](association-end.md) of an [association](association-type.md) to the other end.</span></span> <span data-ttu-id="182f9-105">Diğer [özelliklerden](property.md)farklı olarak, gezinti özellikleri verileri taşımaz.</span><span class="sxs-lookup"><span data-stu-id="182f9-105">Unlike other [properties](property.md), navigation properties do not carry data.</span></span>

<span data-ttu-id="182f9-106">Bir gezinti özelliği tanımı şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="182f9-106">A navigation property definition includes the following:</span></span>

- <span data-ttu-id="182f9-107">Bir ad.</span><span class="sxs-lookup"><span data-stu-id="182f9-107">A name.</span></span> <span data-ttu-id="182f9-108">Istenir</span><span class="sxs-lookup"><span data-stu-id="182f9-108">(Required)</span></span>

- <span data-ttu-id="182f9-109">Gittiği ilişki.</span><span class="sxs-lookup"><span data-stu-id="182f9-109">The association that it navigates.</span></span> <span data-ttu-id="182f9-110">Istenir</span><span class="sxs-lookup"><span data-stu-id="182f9-110">(Required)</span></span>

- <span data-ttu-id="182f9-111">Gezindiğinde ilişkilendirmenin uçları.</span><span class="sxs-lookup"><span data-stu-id="182f9-111">The ends of the association that it navigates.</span></span> <span data-ttu-id="182f9-112">Istenir</span><span class="sxs-lookup"><span data-stu-id="182f9-112">(Required)</span></span>

<span data-ttu-id="182f9-113">Gezinme özellikleri, bir ilişkilendirmenin sonundaki her iki varlık türü için isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="182f9-113">Navigation properties are optional on both entity types at the ends of an association.</span></span> <span data-ttu-id="182f9-114">Bir ilişkinin sonundaki bir varlık türünde bir gezinti özelliği tanımlarsanız, ilişkilendirmenin diğer sonundaki varlık türünde bir gezinti özelliği tanımlamanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="182f9-114">If you define a navigation property on one entity type at the end of an association, you do not have to define a navigation property on the entity type at the other end of the association.</span></span>

<span data-ttu-id="182f9-115">Gezinti özelliğinin veri türü, uzak [ilişki ucunun](association-end.md) [çoğulluğu](association-end-multiplicity.md) tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="182f9-115">The data type of a navigation property is determined by the [multiplicity](association-end-multiplicity.md) of its remote [association end](association-end.md).</span></span> <span data-ttu-id="182f9-116">Örneğin, bir gezinti özelliğinin bir `OrdersNavProp` `Customer` varlık türünde var olduğunu ve ve arasında bire çok ilişkilendirmesi gezindiğini varsayalım `Customer` `Order` .</span><span class="sxs-lookup"><span data-stu-id="182f9-116">For example, suppose a navigation property, `OrdersNavProp`, exists on a `Customer` entity type and navigates a one-to-many association between `Customer` and `Order`.</span></span> <span data-ttu-id="182f9-117">Gezinti özelliği için uzak ilişki ucunun çok sayıda () çoğulluğu olduğundan \* , veri türü bir koleksiyon (/) olur `Order` .</span><span class="sxs-lookup"><span data-stu-id="182f9-117">Because the remote association end for the navigation property has multiplicity of many (\*), its data type is a collection (of `Order`).</span></span> <span data-ttu-id="182f9-118">Benzer şekilde, bir gezinti özelliği `CustomerNavProp` `Order` varlık türünde varsa, `Customer` uzak uçtaki çoğulluğu bir (1) olduğundan, veri türü olacaktır.</span><span class="sxs-lookup"><span data-stu-id="182f9-118">Similarly, if a navigation property, `CustomerNavProp`, exists on the `Order` entity type, its data type would be `Customer`, because the multiplicity of the remote end is one (1).</span></span>

## <a name="example"></a><span data-ttu-id="182f9-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="182f9-119">Example</span></span>

<span data-ttu-id="182f9-120">Aşağıdaki diyagramda üç varlık türü olan kavramsal model gösterilmektedir: `Book` , `Publisher` , ve `Author` .</span><span class="sxs-lookup"><span data-stu-id="182f9-120">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span> <span data-ttu-id="182f9-121">Gezinti özellikleri `Publisher` ve `Authors` kitap varlık türü üzerinde tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="182f9-121">The navigation properties `Publisher` and `Authors` are defined on the Book entity type.</span></span> <span data-ttu-id="182f9-122">Gezinti özelliği `Books` hem Yayımcı varlık türü hem de varlık türü üzerinde tanımlanmıştır `Author` .</span><span class="sxs-lookup"><span data-stu-id="182f9-122">Navigation property `Books` is defined on both the Publisher entity type and the `Author` entity type.</span></span>

![Üç varlık türü ile kavramsal bir modeli gösteren diyagram.](./media/navigation-property/conceptual-model-entity-types-associations.gif)  

<span data-ttu-id="182f9-124">[ADO.NET Entity Framework](./ef/index.md) kavramsal model tanımlamak için kavramsal şema tanım dili ([csdl](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) adlı bir etki ALANıNA özgü dil (DSL) kullanır.</span><span class="sxs-lookup"><span data-stu-id="182f9-124">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="182f9-125">Aşağıdaki CSDL, `Book` Yukarıdaki diyagramda gösterilen varlık türünü tanımlar:</span><span class="sxs-lookup"><span data-stu-id="182f9-125">The following CSDL defines the `Book` entity type shown in the diagram above:</span></span>

[!code-xml[EDM_Example_Model#EntityExample](~/samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]

<span data-ttu-id="182f9-126">XML öznitelikleri, bir gezinti özelliği tanımlamak için gereken bilgileri iletmek için kullanılır: öznitelik, `Name` özelliğin adını içerir, `Relationship` gezindiği ilişkinin adını içerir ve `FromRole` `ToRole` ilişkinin uçlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="182f9-126">XML attributes are used to communicate the information necessary to define a navigation property: The attribute `Name` contains the name of the property, `Relationship` contains the name of the association it navigates, and `FromRole` and `ToRole` contain the ends of the association.</span></span>

## <a name="see-also"></a><span data-ttu-id="182f9-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="182f9-127">See also</span></span>

- [<span data-ttu-id="182f9-128">Varlık Veri Modeli Temel Kavramları</span><span class="sxs-lookup"><span data-stu-id="182f9-128">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="182f9-129">Varlık Veri Modeli</span><span class="sxs-lookup"><span data-stu-id="182f9-129">Entity Data Model</span></span>](entity-data-model.md)
- [<span data-ttu-id="182f9-130">İlişkiler, gezinti özellikleri ve yabancı anahtarlar</span><span class="sxs-lookup"><span data-stu-id="182f9-130">Relationships, navigation properties, and foreign keys</span></span>](/ef/ef6/fundamentals/relationships)
