---
description: ': Özelliği hakkında daha fazla bilgi'
title: özellik
ms.date: 03/30/2017
ms.assetid: a941c53f-fc97-42c2-8832-0fb9f1d55c06
ms.openlocfilehash: 8b25c19b0673817945fa6cc786589346462f7e61
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754332"
---
# <a name="property"></a><span data-ttu-id="46995-103">özellik</span><span class="sxs-lookup"><span data-stu-id="46995-103">property</span></span>

<span data-ttu-id="46995-104">*Özellikler* [varlık türlerinin](entity-type.md) ve [karmaşık türlerin](complex-type.md)temel yapı taşlarıdır.</span><span class="sxs-lookup"><span data-stu-id="46995-104">*Properties* are the fundamental building blocks of [entity types](entity-type.md) and [complex types](complex-type.md).</span></span> <span data-ttu-id="46995-105">Özellikler bir varlık türü örneği veya karmaşık tür örneği içereceği verilerin şeklini ve özelliklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="46995-105">Properties define the shape and characteristics of data that an entity type instance or complex type instance will contain.</span></span> <span data-ttu-id="46995-106">Kavramsal modeldeki özellikler, bir sınıfta tanımlanan özelliklerle benzerdir.</span><span class="sxs-lookup"><span data-stu-id="46995-106">Properties in a conceptual model are analogous to properties defined on a class.</span></span> <span data-ttu-id="46995-107">Bir sınıftaki özellikler, sınıfın şeklini tanımlar ve nesneler hakkında bilgi taşıyan bir kavramsal modeldeki Özellikler bir varlık türünün şeklini tanımlar ve varlık türü örnekleri hakkında bilgi taşır.</span><span class="sxs-lookup"><span data-stu-id="46995-107">In the same way that properties on a class define the shape of the class and carry information about objects, properties in a conceptual model define the shape of an entity type and carry information about entity type instances.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="46995-108">Bu konu başlığı altında açıklandığı gibi özellikler, gezinti özelliklerinden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="46995-108">Properties, as described in this topic, are different from navigation properties.</span></span> <span data-ttu-id="46995-109">Daha fazla bilgi için bkz. [gezinme özellikleri](navigation-property.md).</span><span class="sxs-lookup"><span data-stu-id="46995-109">For more information, see [navigation properties](navigation-property.md).</span></span>  
  
 <span data-ttu-id="46995-110">Bir özellik tanımı aşağıdaki bilgileri içerir:</span><span class="sxs-lookup"><span data-stu-id="46995-110">A property definition contains the following information:</span></span>  
  
- <span data-ttu-id="46995-111">Özellik adı.</span><span class="sxs-lookup"><span data-stu-id="46995-111">A property name.</span></span> <span data-ttu-id="46995-112">Istenir</span><span class="sxs-lookup"><span data-stu-id="46995-112">(Required)</span></span>  
  
- <span data-ttu-id="46995-113">Bir özellik türü.</span><span class="sxs-lookup"><span data-stu-id="46995-113">A property type.</span></span> <span data-ttu-id="46995-114">Istenir</span><span class="sxs-lookup"><span data-stu-id="46995-114">(Required)</span></span>  
  
- <span data-ttu-id="46995-115">Bir dizi [model](facet.md).</span><span class="sxs-lookup"><span data-stu-id="46995-115">A set of [facets](facet.md).</span></span> <span data-ttu-id="46995-116">(İsteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="46995-116">(Optional)</span></span>  
  
 <span data-ttu-id="46995-117">Bir özellik, ilkel veriler (örneğin, bir dize, bir tamsayı veya Boole değeri) veya yapılandırılmış veriler (karmaşık bir tür gibi) içerebilir.</span><span class="sxs-lookup"><span data-stu-id="46995-117">A property can contain primitive data (such as a string, an integer, or a Boolean value), or structured data (such as a complex type).</span></span> <span data-ttu-id="46995-118">İlkel türdeki özellikler de skaler özellikler olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="46995-118">Properties that are of primitive type are also called scalar properties.</span></span> <span data-ttu-id="46995-119">Daha fazla bilgi için bkz. [varlık veri modeli: Ilkel veri türleri](entity-data-model-primitive-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="46995-119">For more information, see [Entity Data Model: Primitive Data Types](entity-data-model-primitive-data-types.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="46995-120">Karmaşık bir tür, karmaşık türler olan özelliklere sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="46995-120">A complex type can, itself, have properties that are complex types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="46995-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="46995-121">Example</span></span>  

 <span data-ttu-id="46995-122">Aşağıdaki diyagramda üç varlık türü olan kavramsal model gösterilmektedir: `Book` , `Publisher` , ve `Author` .</span><span class="sxs-lookup"><span data-stu-id="46995-122">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span> <span data-ttu-id="46995-123">Her varlık türünün bazı özellikleri vardır, ancak her bir özelliğin tür bilgisi diyagramda verilmez.</span><span class="sxs-lookup"><span data-stu-id="46995-123">Each entity type has several properties, although type information for each property is not conveyed in the diagram.</span></span> <span data-ttu-id="46995-124">[Varlık anahtarları](entity-key.md) olan Özellikler (anahtar) ile gösterilir.</span><span class="sxs-lookup"><span data-stu-id="46995-124">Properties that are [entity keys](entity-key.md) are denoted with (Key).</span></span>  
  
 ![Üç varlık türüne sahip örnek model](./media/property/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="46995-126">[ADO.NET Entity Framework](./ef/index.md) kavramsal model tanımlamak için kavramsal şema tanım dili ([csdl](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) adlı bir etki ALANıNA özgü dil (DSL) kullanır.</span><span class="sxs-lookup"><span data-stu-id="46995-126">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="46995-127">Aşağıdaki CSDL `Book` varlık türünü tanımlar (Yukarıdaki diyagramda gösterildiği gibi) ve XML özniteliklerini kullanarak her bir özelliğin türünü ve adını gösterir.</span><span class="sxs-lookup"><span data-stu-id="46995-127">The following CSDL defines the `Book` entity type (as shown in the diagram above) and indicates the type and name of each property by using XML attributes.</span></span> <span data-ttu-id="46995-128">İsteğe bağlı bir model, `Nullable` XML özniteliği kullanılarak da tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="46995-128">An optional facet, `Nullable`, is also defined by using an XML attribute.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
 <span data-ttu-id="46995-129">Diyagramda gösterilen özelliklerden biri karmaşık tür özelliği olabilir.</span><span class="sxs-lookup"><span data-stu-id="46995-129">It is possible that one of the properties shown in the diagram is a complex type property.</span></span> <span data-ttu-id="46995-130">Örneğin, `Address` varlık türündeki özelliği,,,, `Publisher` ve gibi çeşitli skaler özelliklerden oluşan karmaşık bir tür özelliği olabilir `StreetAddress` `City` `StateOrProvince` `Country` `PostalCode` .</span><span class="sxs-lookup"><span data-stu-id="46995-130">For example, the `Address` property on the `Publisher` entity type could be a complex type property composed of several scalar properties, such as `StreetAddress`, `City`, `StateOrProvince`, `Country`, and `PostalCode`.</span></span> <span data-ttu-id="46995-131">Böyle bir karmaşık türün CSDL temsili aşağıdaki gibi olacaktır:</span><span class="sxs-lookup"><span data-stu-id="46995-131">The CSDL representation of such a complex type would be as follows:</span></span>  
  
 [!code-xml[EDM_Example_Model#ComplexTypeExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#complextypeexample)]  
  
## <a name="see-also"></a><span data-ttu-id="46995-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="46995-132">See also</span></span>

- [<span data-ttu-id="46995-133">Varlık Veri Modeli Temel Kavramları</span><span class="sxs-lookup"><span data-stu-id="46995-133">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="46995-134">Varlık Veri Modeli</span><span class="sxs-lookup"><span data-stu-id="46995-134">Entity Data Model</span></span>](entity-data-model.md)
