---
title: özellik
ms.date: 03/30/2017
ms.assetid: a941c53f-fc97-42c2-8832-0fb9f1d55c06
ms.openlocfilehash: 97d934ac581e7b1a923bf77dcf46121782fe8eab
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783178"
---
# <a name="property"></a><span data-ttu-id="72e03-102">özellik</span><span class="sxs-lookup"><span data-stu-id="72e03-102">property</span></span>
<span data-ttu-id="72e03-103">*Özellikler* [varlık türlerinin](entity-type.md) ve [karmaşık türlerin](complex-type.md)temel yapı taşlarıdır.</span><span class="sxs-lookup"><span data-stu-id="72e03-103">*Properties* are the fundamental building blocks of [entity types](entity-type.md) and [complex types](complex-type.md).</span></span> <span data-ttu-id="72e03-104">Özellikler bir varlık türü örneği veya karmaşık tür örneği içereceği verilerin şeklini ve özelliklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="72e03-104">Properties define the shape and characteristics of data that an entity type instance or complex type instance will contain.</span></span> <span data-ttu-id="72e03-105">Kavramsal modeldeki özellikler, bir sınıfta tanımlanan özelliklerle benzerdir.</span><span class="sxs-lookup"><span data-stu-id="72e03-105">Properties in a conceptual model are analogous to properties defined on a class.</span></span> <span data-ttu-id="72e03-106">Bir sınıftaki özellikler, sınıfın şeklini tanımlar ve nesneler hakkında bilgi taşıyan bir kavramsal modeldeki Özellikler bir varlık türünün şeklini tanımlar ve varlık türü örnekleri hakkında bilgi taşır.</span><span class="sxs-lookup"><span data-stu-id="72e03-106">In the same way that properties on a class define the shape of the class and carry information about objects, properties in a conceptual model define the shape of an entity type and carry information about entity type instances.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="72e03-107">Bu konu başlığı altında açıklandığı gibi özellikler, gezinti özelliklerinden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="72e03-107">Properties, as described in this topic, are different from navigation properties.</span></span> <span data-ttu-id="72e03-108">Daha fazla bilgi için bkz. [gezinme özellikleri](navigation-property.md).</span><span class="sxs-lookup"><span data-stu-id="72e03-108">For more information, see [navigation properties](navigation-property.md).</span></span>  
  
 <span data-ttu-id="72e03-109">Bir özellik tanımı aşağıdaki bilgileri içerir:</span><span class="sxs-lookup"><span data-stu-id="72e03-109">A property definition contains the following information:</span></span>  
  
- <span data-ttu-id="72e03-110">Özellik adı.</span><span class="sxs-lookup"><span data-stu-id="72e03-110">A property name.</span></span> <span data-ttu-id="72e03-111">Istenir</span><span class="sxs-lookup"><span data-stu-id="72e03-111">(Required)</span></span>  
  
- <span data-ttu-id="72e03-112">Bir özellik türü.</span><span class="sxs-lookup"><span data-stu-id="72e03-112">A property type.</span></span> <span data-ttu-id="72e03-113">Istenir</span><span class="sxs-lookup"><span data-stu-id="72e03-113">(Required)</span></span>  
  
- <span data-ttu-id="72e03-114">Bir dizi [model](facet.md).</span><span class="sxs-lookup"><span data-stu-id="72e03-114">A set of [facets](facet.md).</span></span> <span data-ttu-id="72e03-115">(İsteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="72e03-115">(Optional)</span></span>  
  
 <span data-ttu-id="72e03-116">Bir özellik, ilkel veriler (örneğin, bir dize, bir tamsayı veya Boole değeri) veya yapılandırılmış veriler (karmaşık bir tür gibi) içerebilir.</span><span class="sxs-lookup"><span data-stu-id="72e03-116">A property can contain primitive data (such as a string, an integer, or a Boolean value), or structured data (such as a complex type).</span></span> <span data-ttu-id="72e03-117">İlkel türdeki özellikler de skaler özellikler olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="72e03-117">Properties that are of primitive type are also called scalar properties.</span></span> <span data-ttu-id="72e03-118">Daha fazla bilgi için bkz [. varlık veri modeli: İlkel veri türleri](entity-data-model-primitive-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="72e03-118">For more information, see [Entity Data Model: Primitive Data Types](entity-data-model-primitive-data-types.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="72e03-119">Karmaşık bir tür, karmaşık türler olan özelliklere sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="72e03-119">A complex type can, itself, have properties that are complex types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="72e03-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="72e03-120">Example</span></span>  
 <span data-ttu-id="72e03-121">Aşağıdaki diyagramda üç varlık türü olan kavramsal model gösterilmektedir: `Book`, `Publisher`, ve `Author`.</span><span class="sxs-lookup"><span data-stu-id="72e03-121">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span> <span data-ttu-id="72e03-122">Her varlık türünün bazı özellikleri vardır, ancak her bir özelliğin tür bilgisi diyagramda verilmez.</span><span class="sxs-lookup"><span data-stu-id="72e03-122">Each entity type has several properties, although type information for each property is not conveyed in the diagram.</span></span> <span data-ttu-id="72e03-123">[Varlık anahtarları](entity-key.md) olan Özellikler (anahtar) ile gösterilir.</span><span class="sxs-lookup"><span data-stu-id="72e03-123">Properties that are [entity keys](entity-key.md) are denoted with (Key).</span></span>  
  
 ![Üç varlık türüne sahip örnek model](./media/property/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="72e03-125">[ADO.NET Entity Framework](./ef/index.md) kavramsal model tanımlamak için kavramsal şema tanım dili ([csdl](./ef/language-reference/csdl-specification.md)) adlı bir etki ALANıNA özgü dil (DSL) kullanır.</span><span class="sxs-lookup"><span data-stu-id="72e03-125">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](./ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="72e03-126">Aşağıdaki csdl `Book` varlık türünü tanımlar (Yukarıdaki diyagramda gösterildiği gibi) ve XML özniteliklerini kullanarak her bir özelliğin türünü ve adını gösterir.</span><span class="sxs-lookup"><span data-stu-id="72e03-126">The following CSDL defines the `Book` entity type (as shown in the diagram above) and indicates the type and name of each property by using XML attributes.</span></span> <span data-ttu-id="72e03-127">İsteğe bağlı bir model `Nullable`, XML özniteliği kullanılarak da tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="72e03-127">An optional facet, `Nullable`, is also defined by using an XML attribute.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
 <span data-ttu-id="72e03-128">Diyagramda gösterilen özelliklerden biri karmaşık tür özelliği olabilir.</span><span class="sxs-lookup"><span data-stu-id="72e03-128">It is possible that one of the properties shown in the diagram is a complex type property.</span></span> <span data-ttu-id="72e03-129">`Address` Örneğin, `StreetAddress` varlıktüründeki`StateOrProvince`özelliği ,`Country`,,, ve`PostalCode`gibi çeşitli skaler özelliklerden oluşan karmaşık bir tür özelliği olabilir. `City` `Publisher`</span><span class="sxs-lookup"><span data-stu-id="72e03-129">For example, the `Address` property on the `Publisher` entity type could be a complex type property composed of several scalar properties, such as `StreetAddress`, `City`, `StateOrProvince`, `Country`, and `PostalCode`.</span></span> <span data-ttu-id="72e03-130">Böyle bir karmaşık türün CSDL temsili aşağıdaki gibi olacaktır:</span><span class="sxs-lookup"><span data-stu-id="72e03-130">The CSDL representation of such a complex type would be as follows:</span></span>  
  
 [!code-xml[EDM_Example_Model#ComplexTypeExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#complextypeexample)]  
  
## <a name="see-also"></a><span data-ttu-id="72e03-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="72e03-131">See also</span></span>

- [<span data-ttu-id="72e03-132">Varlık Veri Modeli Temel Kavramları</span><span class="sxs-lookup"><span data-stu-id="72e03-132">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="72e03-133">Varlık Veri Modeli</span><span class="sxs-lookup"><span data-stu-id="72e03-133">Entity Data Model</span></span>](entity-data-model.md)
