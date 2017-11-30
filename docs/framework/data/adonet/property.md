---
title: "özellik"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a941c53f-fc97-42c2-8832-0fb9f1d55c06
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c052c53488fde0ea767a46f51ef349dd6a7d2766
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="property"></a><span data-ttu-id="2afb2-102">özellik</span><span class="sxs-lookup"><span data-stu-id="2afb2-102">property</span></span>
<span data-ttu-id="2afb2-103">*Özellikler* temel yapı taşlarıdır [varlık türleri](../../../../docs/framework/data/adonet/entity-type.md) ve [karmaşık türler](../../../../docs/framework/data/adonet/complex-type.md).</span><span class="sxs-lookup"><span data-stu-id="2afb2-103">*Properties* are the fundamental building blocks of [entity types](../../../../docs/framework/data/adonet/entity-type.md) and [complex types](../../../../docs/framework/data/adonet/complex-type.md).</span></span> <span data-ttu-id="2afb2-104">Bir varlık türü örneği veya karmaşık türü örneği içeren veri özelliklerini ve Şekil özellikleri tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="2afb2-104">Properties define the shape and characteristics of data that an entity type instance or complex type instance will contain.</span></span> <span data-ttu-id="2afb2-105">Kavramsal model özelliklerinde bir sınıf üzerinde tanımlanan özellikleri benzer.</span><span class="sxs-lookup"><span data-stu-id="2afb2-105">Properties in a conceptual model are analogous to properties defined on a class.</span></span> <span data-ttu-id="2afb2-106">Aynı şekilde bir sınıfındaki özellikleri şekil sınıfının tanımlamak ve nesneler hakkındaki bilgileri taşımak, kavramsal model özelliklerinde bir varlık türü şeklini tanımlayın ve varlık türü örnekleri hakkında bilgi taşımak.</span><span class="sxs-lookup"><span data-stu-id="2afb2-106">In the same way that properties on a class define the shape of the class and carry information about objects, properties in a conceptual model define the shape of an entity type and carry information about entity type instances.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2afb2-107">Bu konuda açıklandığı gibi özellikleri, gezinti Özellikleri ' farklıdır.</span><span class="sxs-lookup"><span data-stu-id="2afb2-107">Properties, as described in this topic, are different from navigation properties.</span></span> <span data-ttu-id="2afb2-108">Daha fazla bilgi için bkz: [Gezinti özellikleri](../../../../docs/framework/data/adonet/navigation-property.md).</span><span class="sxs-lookup"><span data-stu-id="2afb2-108">For more information, see [navigation properties](../../../../docs/framework/data/adonet/navigation-property.md).</span></span>  
  
 <span data-ttu-id="2afb2-109">Özellik tanımı aşağıdaki bilgileri içerir:</span><span class="sxs-lookup"><span data-stu-id="2afb2-109">A property definition contains the following information:</span></span>  
  
-   <span data-ttu-id="2afb2-110">Bir özellik adı.</span><span class="sxs-lookup"><span data-stu-id="2afb2-110">A property name.</span></span> <span data-ttu-id="2afb2-111">(Gerekli)</span><span class="sxs-lookup"><span data-stu-id="2afb2-111">(Required)</span></span>  
  
-   <span data-ttu-id="2afb2-112">Bir özellik türü.</span><span class="sxs-lookup"><span data-stu-id="2afb2-112">A property type.</span></span> <span data-ttu-id="2afb2-113">(Gerekli)</span><span class="sxs-lookup"><span data-stu-id="2afb2-113">(Required)</span></span>  
  
-   <span data-ttu-id="2afb2-114">Bir dizi [modelleri](../../../../docs/framework/data/adonet/facet.md).</span><span class="sxs-lookup"><span data-stu-id="2afb2-114">A set of [facets](../../../../docs/framework/data/adonet/facet.md).</span></span> <span data-ttu-id="2afb2-115">(İsteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="2afb2-115">(Optional)</span></span>  
  
 <span data-ttu-id="2afb2-116">Bir özellik, temel verileri (örneğin, bir dize, tamsayı veya Boolean değeri) veya yapılandırılmış verileri (örneğin, bir karmaşık tür) içerebilir.</span><span class="sxs-lookup"><span data-stu-id="2afb2-116">A property can contain primitive data (such as a string, an integer, or a Boolean value), or structured data (such as a complex type).</span></span> <span data-ttu-id="2afb2-117">İlkel tür özellikleri, skaler özellikleri olarak da adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="2afb2-117">Properties that are of primitive type are also called scalar properties.</span></span> <span data-ttu-id="2afb2-118">Daha fazla bilgi için bkz: [varlık veri modeli: Basit veri türleri](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="2afb2-118">For more information, see [Entity Data Model: Primitive Data Types](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2afb2-119">Karmaşık bir tür kendisi, karmaşık türleri olan özellikler olabilir.</span><span class="sxs-lookup"><span data-stu-id="2afb2-119">A complex type can, itself, have properties that are complex types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2afb2-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="2afb2-120">Example</span></span>  
 <span data-ttu-id="2afb2-121">Aşağıdaki diyagram üç varlık türleriyle kavramsal model gösterir: `Book`, `Publisher`, ve `Author`.</span><span class="sxs-lookup"><span data-stu-id="2afb2-121">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span> <span data-ttu-id="2afb2-122">Tür bilgileri her bir özellik için diyagramda ilettiği değil ancak her bir varlık türü birçok özelliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="2afb2-122">Each entity type has several properties, although type information for each property is not conveyed in the diagram.</span></span> <span data-ttu-id="2afb2-123">Özellikler [varlık anahtarları](../../../../docs/framework/data/adonet/entity-key.md) (anahtarla) belirtilir.</span><span class="sxs-lookup"><span data-stu-id="2afb2-123">Properties that are [entity keys](../../../../docs/framework/data/adonet/entity-key.md) are denoted with (Key).</span></span>  
  
 <span data-ttu-id="2afb2-124">![Örnek modeli](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span><span class="sxs-lookup"><span data-stu-id="2afb2-124">![Example Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span></span>  
  
 <span data-ttu-id="2afb2-125">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) kavramsal şema tanım dili adlı bir etki alanına özgü dil (DSL) kullanır ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) kavramsal modeller tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="2afb2-125">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="2afb2-126">Aşağıdaki CSDL tanımlar `Book` varlık yazın (Yukarıdaki diyagramda gösterildiği gibi) ve XML öznitelikleri kullanarak her özelliğin adını ve türünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="2afb2-126">The following CSDL defines the `Book` entity type (as shown in the diagram above) and indicates the type and name of each property by using XML attributes.</span></span> <span data-ttu-id="2afb2-127">İsteğe bağlı bir model `Nullable`, ayrıca bir XML özniteliği kullanılarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="2afb2-127">An optional facet, `Nullable`, is also defined by using an XML attribute.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
 <span data-ttu-id="2afb2-128">Aşağıdaki çizimde gösterilen özellikleri biri bir karmaşık tür özelliği olduğunu mümkündür.</span><span class="sxs-lookup"><span data-stu-id="2afb2-128">It is possible that one of the properties shown in the diagram is a complex type property.</span></span> <span data-ttu-id="2afb2-129">Örneğin, `Address` özelliği `Publisher` varlık türü olabilir birkaç skaler özelliklerini oluşan bir karmaşık tür özelliği gibi `StreetAddress`, `City`, `StateOrProvince`, `Country`, ve `PostalCode`.</span><span class="sxs-lookup"><span data-stu-id="2afb2-129">For example, the `Address` property on the `Publisher` entity type could be a complex type property composed of several scalar properties, such as `StreetAddress`, `City`, `StateOrProvince`, `Country`, and `PostalCode`.</span></span> <span data-ttu-id="2afb2-130">Karmaşık bir tür CSDL gösterimini aşağıdaki gibi olur:</span><span class="sxs-lookup"><span data-stu-id="2afb2-130">The CSDL representation of such a complex type would be as follows:</span></span>  
  
 [!code-xml[EDM_Example_Model#ComplexTypeExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#complextypeexample)]  
  
## <a name="see-also"></a><span data-ttu-id="2afb2-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2afb2-131">See Also</span></span>  
 [<span data-ttu-id="2afb2-132">Varlık veri modeli temel kavramları</span><span class="sxs-lookup"><span data-stu-id="2afb2-132">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="2afb2-133">Varlık veri modeli</span><span class="sxs-lookup"><span data-stu-id="2afb2-133">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
