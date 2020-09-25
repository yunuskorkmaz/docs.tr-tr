---
title: complex type
ms.date: 03/30/2017
ms.assetid: 63efbd23-11d4-4871-bc88-ad01b9837553
ms.openlocfilehash: ef20de6a9e72d3123d745ef5501ecdb7fa63967d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203793"
---
# <a name="complex-type"></a><span data-ttu-id="2e7b8-102">complex type</span><span class="sxs-lookup"><span data-stu-id="2e7b8-102">complex type</span></span>

<span data-ttu-id="2e7b8-103">*Karmaşık tür* , [varlık türlerinde](entity-type.md) veya diğer karmaşık türlerde zengin, yapılandırılmış özellikleri tanımlamaya yönelik bir şablondur.</span><span class="sxs-lookup"><span data-stu-id="2e7b8-103">A *complex type* is a template for defining rich, structured properties on [entity types](entity-type.md) or on other complex types.</span></span> <span data-ttu-id="2e7b8-104">Her şablon şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="2e7b8-104">Each template contains the following:</span></span>  
  
- <span data-ttu-id="2e7b8-105">Benzersiz bir ad.</span><span class="sxs-lookup"><span data-stu-id="2e7b8-105">A unique name.</span></span> <span data-ttu-id="2e7b8-106">Istenir</span><span class="sxs-lookup"><span data-stu-id="2e7b8-106">(Required)</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="2e7b8-107">Karmaşık bir türün adı aynı ad alanı içindeki bir varlık türü adı ile aynı olamaz.</span><span class="sxs-lookup"><span data-stu-id="2e7b8-107">The name of a complex type cannot be the same as an entity type name within the same namespace.</span></span>  
  
- <span data-ttu-id="2e7b8-108">Bir veya daha fazla [özellik](property.md)biçimindeki veriler.</span><span class="sxs-lookup"><span data-stu-id="2e7b8-108">Data in the form of one or more [properties](property.md).</span></span> <span data-ttu-id="2e7b8-109">(İsteğe bağlı.)</span><span class="sxs-lookup"><span data-stu-id="2e7b8-109">(Optional.)</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="2e7b8-110">Karmaşık bir türün özelliği başka bir karmaşık tür olabilir.</span><span class="sxs-lookup"><span data-stu-id="2e7b8-110">A property of a complex type can be another complex type.</span></span>  
  
 <span data-ttu-id="2e7b8-111">Karmaşık bir tür, ilkel tür özellikleri veya diğer karmaşık türler biçiminde bir veri yükü taşıyamamakta olan bir varlık türüne benzerdir.</span><span class="sxs-lookup"><span data-stu-id="2e7b8-111">A complex type is similar to an entity type in that a complex type can carry a data payload in the form of primitive type properties or other complex types.</span></span> <span data-ttu-id="2e7b8-112">Ancak, karmaşık türler ve varlık türleri arasında bazı önemli farklılıklar vardır:</span><span class="sxs-lookup"><span data-stu-id="2e7b8-112">However, there are some key differences between complex types and entity types:</span></span>  
  
- <span data-ttu-id="2e7b8-113">Karmaşık türlerin kimlikleri yok ve bu nedenle bağımsız olarak bulunamaz.</span><span class="sxs-lookup"><span data-stu-id="2e7b8-113">Complex types do not have identities and therefore cannot exist independently.</span></span> <span data-ttu-id="2e7b8-114">Karmaşık türler yalnızca varlık türleri veya diğer karmaşık türlerde özellikler olarak bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="2e7b8-114">Complex types can only exist as properties on entity types or other complex types.</span></span>  
  
- <span data-ttu-id="2e7b8-115">Karmaşık türler [ilişkilendirmelere](association-type.md)katılamaz.</span><span class="sxs-lookup"><span data-stu-id="2e7b8-115">Complex types cannot participate in [associations](association-type.md).</span></span> <span data-ttu-id="2e7b8-116">İlişkinin sonu ne bir karmaşık tür olamaz, bu nedenle [Gezinti özellikleri](navigation-property.md) karmaşık türlerde tanımlanamaz.</span><span class="sxs-lookup"><span data-stu-id="2e7b8-116">Neither end of an association can be a complex type, and therefore [navigation properties](navigation-property.md) cannot be defined on complex types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2e7b8-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="2e7b8-117">Example</span></span>  

 <span data-ttu-id="2e7b8-118">[ADO.NET Entity Framework](./ef/index.md) kavramsal model tanımlamak için kavramsal şema tanım dili ([csdl](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) adlı bir etki ALANıNA özgü dil (DSL) kullanır.</span><span class="sxs-lookup"><span data-stu-id="2e7b8-118">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="2e7b8-119">Aşağıdaki csdl,,,, ve basit tür özellikleriyle karmaşık bir tür, adres `StreetAddress` tanımlar `City` `StateOrProvince` `Country` `PostalCode` .</span><span class="sxs-lookup"><span data-stu-id="2e7b8-119">The following CSDL defines a complex type, Address, with the primitive type properties `StreetAddress`, `City`, `StateOrProvince`, `Country`, and `PostalCode`.</span></span>  
  
 [!code-xml[EDM_Example_Model#ComplexTypeExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#complextypeexample)]  
  
 <span data-ttu-id="2e7b8-120">Karmaşık türü `Address` (yukarıdaki) bir varlık türünde bir özellik olarak tanımlamak için, varlık türü tanımında Özellik türünü bildirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="2e7b8-120">To define the complex type `Address` (above) as a property on an entity type, you must declare the property type in the entity type definition.</span></span> <span data-ttu-id="2e7b8-121">Aşağıdaki CSDL, `Address` özelliği bir varlık türü (yayımcı) üzerinde karmaşık bir tür olarak bildirir:</span><span class="sxs-lookup"><span data-stu-id="2e7b8-121">The following CSDL declares the `Address` property as a complex type on an entity type (Publisher):</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityWithComplexType](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#entitywithcomplextype)]  
  
## <a name="see-also"></a><span data-ttu-id="2e7b8-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2e7b8-122">See also</span></span>

- [<span data-ttu-id="2e7b8-123">Varlık Veri Modeli Temel Kavramları</span><span class="sxs-lookup"><span data-stu-id="2e7b8-123">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="2e7b8-124">Varlık Veri Modeli</span><span class="sxs-lookup"><span data-stu-id="2e7b8-124">Entity Data Model</span></span>](entity-data-model.md)
