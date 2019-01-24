---
title: Karmaşık tür
ms.date: 03/30/2017
ms.assetid: 63efbd23-11d4-4871-bc88-ad01b9837553
ms.openlocfilehash: 4e18ecf18399f57769dcdfc77192e72ec47f5df3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54555446"
---
# <a name="complex-type"></a><span data-ttu-id="aca54-102">Karmaşık tür</span><span class="sxs-lookup"><span data-stu-id="aca54-102">complex type</span></span>
<span data-ttu-id="aca54-103">A *karmaşık tür* üzerinde zengin, yapısal özellikleri tanımlamak için bir şablon [varlık türleri](../../../../docs/framework/data/adonet/entity-type.md) veya diğer karmaşık türler.</span><span class="sxs-lookup"><span data-stu-id="aca54-103">A *complex type* is a template for defining rich, structured properties on [entity types](../../../../docs/framework/data/adonet/entity-type.md) or on other complex types.</span></span> <span data-ttu-id="aca54-104">Her şablon şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="aca54-104">Each template contains the following:</span></span>  
  
-   <span data-ttu-id="aca54-105">Benzersiz bir ad.</span><span class="sxs-lookup"><span data-stu-id="aca54-105">A unique name.</span></span> <span data-ttu-id="aca54-106">(Gerekli)</span><span class="sxs-lookup"><span data-stu-id="aca54-106">(Required)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="aca54-107">Karmaşık bir tür adı aynı ad alanı içinde bir varlık türü adı ile aynı olamaz.</span><span class="sxs-lookup"><span data-stu-id="aca54-107">The name of a complex type cannot be the same as an entity type name within the same namespace.</span></span>  
  
-   <span data-ttu-id="aca54-108">Bir veya daha fazla bilgi formu verilerinde [özellikleri](../../../../docs/framework/data/adonet/property.md).</span><span class="sxs-lookup"><span data-stu-id="aca54-108">Data in the form of one or more [properties](../../../../docs/framework/data/adonet/property.md).</span></span> <span data-ttu-id="aca54-109">(İsteğe bağlı.)</span><span class="sxs-lookup"><span data-stu-id="aca54-109">(Optional.)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="aca54-110">Karmaşık bir türün bir özelliği başka bir karmaşık türü olabilir.</span><span class="sxs-lookup"><span data-stu-id="aca54-110">A property of a complex type can be another complex type.</span></span>  
  
 <span data-ttu-id="aca54-111">Bir karmaşık türü bir veri yükü formun ilkel tür özellikleri veya diğer karmaşık türler taşıyabilir, bir karmaşık türü bir varlık türüne benzerdir.</span><span class="sxs-lookup"><span data-stu-id="aca54-111">A complex type is similar to an entity type in that a complex type can carry a data payload in the form of primitive type properties or other complex types.</span></span> <span data-ttu-id="aca54-112">Ancak, karmaşık türlerden ve varlık türleri arasındaki bazı temel farklar vardır:</span><span class="sxs-lookup"><span data-stu-id="aca54-112">However, there are some key differences between complex types and entity types:</span></span>  
  
-   <span data-ttu-id="aca54-113">Karmaşık türler kimliklere sahip değildir ve bu nedenle bağımsız olarak var olamaz.</span><span class="sxs-lookup"><span data-stu-id="aca54-113">Complex types do not have identities and therefore cannot exist independently.</span></span> <span data-ttu-id="aca54-114">Karmaşık türler yalnızca varlık türleri veya diğer karmaşık türler özellikleri olarak bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="aca54-114">Complex types can only exist as properties on entity types or other complex types.</span></span>  
  
-   <span data-ttu-id="aca54-115">Karmaşık türler içinde katılamaz [ilişkilendirmeleri](../../../../docs/framework/data/adonet/association-type.md).</span><span class="sxs-lookup"><span data-stu-id="aca54-115">Complex types cannot participate in [associations](../../../../docs/framework/data/adonet/association-type.md).</span></span> <span data-ttu-id="aca54-116">Bir ilişkilendirmenin hiçbiri son karmaşık bir tür olabilir ve bu nedenle [Gezinti özellikleri](../../../../docs/framework/data/adonet/navigation-property.md) karmaşık türlerde tanımlanamaz.</span><span class="sxs-lookup"><span data-stu-id="aca54-116">Neither end of an association can be a complex type, and therefore [navigation properties](../../../../docs/framework/data/adonet/navigation-property.md) cannot be defined on complex types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aca54-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="aca54-117">Example</span></span>  
 <span data-ttu-id="aca54-118">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) kavramsal şema tanım dili olarak adlandırılan bir etki alanına özgü dil (DSL) kullanır ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) kavramsal modeller tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="aca54-118">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="aca54-119">Aşağıdaki CSDL bir karmaşık tür adresi, ilkel türü özellikleri ile tanımlar `StreetAddress`, `City`, `StateOrProvince`, `Country`, ve `PostalCode`.</span><span class="sxs-lookup"><span data-stu-id="aca54-119">The following CSDL defines a complex type, Address, with the primitive type properties `StreetAddress`, `City`, `StateOrProvince`, `Country`, and `PostalCode`.</span></span>  
  
 [!code-xml[EDM_Example_Model#ComplexTypeExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#complextypeexample)]  
  
 <span data-ttu-id="aca54-120">Karmaşık tür tanımlamak için `Address` (yukarıda) bir varlık türü üzerindeki bir özellik olarak, özellik türü varlık tür tanımında bildirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="aca54-120">To define the complex type `Address` (above) as a property on an entity type, you must declare the property type in the entity type definition.</span></span> <span data-ttu-id="aca54-121">Aşağıdaki CSDL bildirir `Address` özelliği bir varlık türü (yayımcı) üzerinde karmaşık bir tür olarak:</span><span class="sxs-lookup"><span data-stu-id="aca54-121">The following CSDL declares the `Address` property as a complex type on an entity type (Publisher):</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityWithComplexType](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#entitywithcomplextype)]  
  
## <a name="see-also"></a><span data-ttu-id="aca54-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aca54-122">See also</span></span>
- [<span data-ttu-id="aca54-123">Varlık Veri Modeli Temel Kavramları</span><span class="sxs-lookup"><span data-stu-id="aca54-123">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [<span data-ttu-id="aca54-124">Varlık Veri Modeli</span><span class="sxs-lookup"><span data-stu-id="aca54-124">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
