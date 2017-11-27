---
title: "Gezinme özelliği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d0bf1a6a-1d84-484c-b7c3-b410fd8dc0b1
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 1677ab1be071eeabd72b29c7ce61d01aaf6164a1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="navigation-property"></a><span data-ttu-id="e1e67-102">Gezinme özelliği</span><span class="sxs-lookup"><span data-stu-id="e1e67-102">navigation property</span></span>
<span data-ttu-id="e1e67-103">A *gezinti özelliği* üzerinde isteğe bağlı bir özellik olan bir [varlık türü](../../../../docs/framework/data/adonet/entity-type.md) izin veren bir gezinti için [son](../../../../docs/framework/data/adonet/association-end.md) , bir [ilişkilendirme](../../../../docs/framework/data/adonet/association-type.md) için diğer sonu.</span><span class="sxs-lookup"><span data-stu-id="e1e67-103">A *navigation property* is an optional property on an [entity type](../../../../docs/framework/data/adonet/entity-type.md) that allows for navigation from one [end](../../../../docs/framework/data/adonet/association-end.md) of an [association](../../../../docs/framework/data/adonet/association-type.md) to the other end.</span></span> <span data-ttu-id="e1e67-104">Diğer aksine [özellikleri](../../../../docs/framework/data/adonet/property.md), gezinti özellikleri veri taşımak değil.</span><span class="sxs-lookup"><span data-stu-id="e1e67-104">Unlike other [properties](../../../../docs/framework/data/adonet/property.md), navigation properties do not carry data.</span></span>  
  
 <span data-ttu-id="e1e67-105">Bir gezinti özelliği tanımı aşağıdakileri içerir:</span><span class="sxs-lookup"><span data-stu-id="e1e67-105">A navigation property definition includes the following:</span></span>  
  
-   <span data-ttu-id="e1e67-106">Bir ad.</span><span class="sxs-lookup"><span data-stu-id="e1e67-106">A name.</span></span> <span data-ttu-id="e1e67-107">(Gerekli)</span><span class="sxs-lookup"><span data-stu-id="e1e67-107">(Required)</span></span>  
  
-   <span data-ttu-id="e1e67-108">Bu gider ilişkilendirme.</span><span class="sxs-lookup"><span data-stu-id="e1e67-108">The association that it navigates.</span></span> <span data-ttu-id="e1e67-109">(Gerekli)</span><span class="sxs-lookup"><span data-stu-id="e1e67-109">(Required)</span></span>  
  
-   <span data-ttu-id="e1e67-110">Bu gider ilişkilendirme ucunun.</span><span class="sxs-lookup"><span data-stu-id="e1e67-110">The ends of the association that it navigates.</span></span> <span data-ttu-id="e1e67-111">(Gerekli)</span><span class="sxs-lookup"><span data-stu-id="e1e67-111">(Required)</span></span>  
  
 <span data-ttu-id="e1e67-112">Gezinti özellikleri her iki varlık türü bir ilişki ucundaki isteğe bağlı olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="e1e67-112">Note that navigation properties are optional on both entity types at the ends of an association.</span></span> <span data-ttu-id="e1e67-113">Bir ilişkilendirme sonunda bir varlık türünde bir gezinti özelliği tanımlarsanız, ilişkinin diğer ucundaki varlık türünde bir gezinti özelliği tanımlamak gerekmez.</span><span class="sxs-lookup"><span data-stu-id="e1e67-113">If you define a navigation property on one entity type at the end of an association, you do not have to define a navigation property on the entity type at the other end of the association.</span></span>  
  
 <span data-ttu-id="e1e67-114">Veri türü bir gezinti özelliği tarafından belirlendiği [Çokluk](../../../../docs/framework/data/adonet/association-end-multiplicity.md) kendi uzak [ilişki ucu](../../../../docs/framework/data/adonet/association-end.md).</span><span class="sxs-lookup"><span data-stu-id="e1e67-114">The data type of a navigation property is determined by the [multiplicity](../../../../docs/framework/data/adonet/association-end-multiplicity.md) of its remote [association end](../../../../docs/framework/data/adonet/association-end.md).</span></span> <span data-ttu-id="e1e67-115">Örneğin, bir gezinti özelliği varsayalım `OrdersNavProp`, var. bir `Customer` varlık türü ve arasında bir-çok ilişkisi gider `Customer` ve `Order`.</span><span class="sxs-lookup"><span data-stu-id="e1e67-115">For example, suppose a navigation property, `OrdersNavProp`, exists on a `Customer` entity type and navigates a one-to-many association between `Customer` and `Order`.</span></span> <span data-ttu-id="e1e67-116">Gezinme özelliği için Uzak ilişkilendirme ucunun çokluğu birçok (*) sahip olduğundan, veri türü bir koleksiyonudur (biri `Order`).</span><span class="sxs-lookup"><span data-stu-id="e1e67-116">Because the remote association end for the navigation property has multiplicity of many (*), its data type is a collection (of `Order`).</span></span> <span data-ttu-id="e1e67-117">Benzer şekilde, bir gezinti özelliği, `CustomerNavProp`, var. `Order` varlık türü, veri türü olacaktır `Customer`, çünkü uzak ucunun çokluğu bir (1).</span><span class="sxs-lookup"><span data-stu-id="e1e67-117">Similarly, if a navigation property, `CustomerNavProp`, exists on the `Order` entity type, its data type would be `Customer`, because the multiplicity of the remote end is one (1).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e1e67-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="e1e67-118">Example</span></span>  
 <span data-ttu-id="e1e67-119">Aşağıdaki diyagram üç varlık türleriyle kavramsal model gösterir: `Book`, `Publisher`, ve `Author`.</span><span class="sxs-lookup"><span data-stu-id="e1e67-119">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span> <span data-ttu-id="e1e67-120">Gezinti özellikleri `Publisher` ve `Authors`, kitap varlık türünde tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="e1e67-120">Navigation properties, `Publisher` and `Authors`, are defined on the Book entity type.</span></span> <span data-ttu-id="e1e67-121">Gezinti özelliği `Books` hem Yayımcı varlık türü üzerinde tanımlanan ve `Author` varlık türü.</span><span class="sxs-lookup"><span data-stu-id="e1e67-121">Navigation property `Books` is defined on both the Publisher entity type and the `Author` entity type.</span></span>  
  
 <span data-ttu-id="e1e67-122">![Model Gezinti özellikleri ile](../../../../docs/framework/data/adonet/media/modelwithnavprops.gif "ModelWithNavProps")</span><span class="sxs-lookup"><span data-stu-id="e1e67-122">![Model with Navigation Properties](../../../../docs/framework/data/adonet/media/modelwithnavprops.gif "ModelWithNavProps")</span></span>  
  
 <span data-ttu-id="e1e67-123">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) kavramsal şema tanım dili adlı bir etki alanına özgü dil (DSL) kullanır ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) kavramsal modeller tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="e1e67-123">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="e1e67-124">Aşağıdaki CSDL tanımlar `Book` Yukarıdaki diyagramda gösterildiği varlık türü:</span><span class="sxs-lookup"><span data-stu-id="e1e67-124">The following CSDL defines the `Book` entity type shown in the diagram above:</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
 <span data-ttu-id="e1e67-125">XML öznitelikleri bir gezinti özelliği tanımlamak gerekli bilgileri iletişim kurmak için kullanılır unutmayın: öznitelik `Name` özelliğinin adını içeren `Relationship` , gider, ilişkilendirme adını içerir ve `FromRole` ve `ToRole` ilişkilendirme ucunun içerir.</span><span class="sxs-lookup"><span data-stu-id="e1e67-125">Note that XML attributes are used to communicate the information necessary to define a navigation property: The attribute `Name` contains the name of the property, `Relationship` contains the name of the association it navigates, and `FromRole` and `ToRole` contain the ends of the association.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1e67-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e1e67-126">See Also</span></span>  
 [<span data-ttu-id="e1e67-127">Varlık veri modeli temel kavramları</span><span class="sxs-lookup"><span data-stu-id="e1e67-127">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="e1e67-128">Varlık veri modeli</span><span class="sxs-lookup"><span data-stu-id="e1e67-128">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
