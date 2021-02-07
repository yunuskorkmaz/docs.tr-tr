---
description: 'Daha fazla bilgi edinin: karmaşık tür'
title: complex type
ms.date: 03/30/2017
ms.assetid: 63efbd23-11d4-4871-bc88-ad01b9837553
ms.openlocfilehash: 06bb6f54f488e4c6038382707a2ad3e85f000bc2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99663905"
---
# <a name="complex-type"></a><span data-ttu-id="f5e7a-103">complex type</span><span class="sxs-lookup"><span data-stu-id="f5e7a-103">complex type</span></span>

<span data-ttu-id="f5e7a-104">*Karmaşık tür* , [varlık türlerinde](entity-type.md) veya diğer karmaşık türlerde zengin, yapılandırılmış özellikleri tanımlamaya yönelik bir şablondur.</span><span class="sxs-lookup"><span data-stu-id="f5e7a-104">A *complex type* is a template for defining rich, structured properties on [entity types](entity-type.md) or on other complex types.</span></span> <span data-ttu-id="f5e7a-105">Her şablon şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="f5e7a-105">Each template contains the following:</span></span>  
  
- <span data-ttu-id="f5e7a-106">Benzersiz bir ad.</span><span class="sxs-lookup"><span data-stu-id="f5e7a-106">A unique name.</span></span> <span data-ttu-id="f5e7a-107">Istenir</span><span class="sxs-lookup"><span data-stu-id="f5e7a-107">(Required)</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="f5e7a-108">Karmaşık bir türün adı aynı ad alanı içindeki bir varlık türü adı ile aynı olamaz.</span><span class="sxs-lookup"><span data-stu-id="f5e7a-108">The name of a complex type cannot be the same as an entity type name within the same namespace.</span></span>  
  
- <span data-ttu-id="f5e7a-109">Bir veya daha fazla [özellik](property.md)biçimindeki veriler.</span><span class="sxs-lookup"><span data-stu-id="f5e7a-109">Data in the form of one or more [properties](property.md).</span></span> <span data-ttu-id="f5e7a-110">(İsteğe bağlı.)</span><span class="sxs-lookup"><span data-stu-id="f5e7a-110">(Optional.)</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="f5e7a-111">Karmaşık bir türün özelliği başka bir karmaşık tür olabilir.</span><span class="sxs-lookup"><span data-stu-id="f5e7a-111">A property of a complex type can be another complex type.</span></span>  
  
 <span data-ttu-id="f5e7a-112">Karmaşık bir tür, ilkel tür özellikleri veya diğer karmaşık türler biçiminde bir veri yükü taşıyamamakta olan bir varlık türüne benzerdir.</span><span class="sxs-lookup"><span data-stu-id="f5e7a-112">A complex type is similar to an entity type in that a complex type can carry a data payload in the form of primitive type properties or other complex types.</span></span> <span data-ttu-id="f5e7a-113">Ancak, karmaşık türler ve varlık türleri arasında bazı önemli farklılıklar vardır:</span><span class="sxs-lookup"><span data-stu-id="f5e7a-113">However, there are some key differences between complex types and entity types:</span></span>  
  
- <span data-ttu-id="f5e7a-114">Karmaşık türlerin kimlikleri yok ve bu nedenle bağımsız olarak bulunamaz.</span><span class="sxs-lookup"><span data-stu-id="f5e7a-114">Complex types do not have identities and therefore cannot exist independently.</span></span> <span data-ttu-id="f5e7a-115">Karmaşık türler yalnızca varlık türleri veya diğer karmaşık türlerde özellikler olarak bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="f5e7a-115">Complex types can only exist as properties on entity types or other complex types.</span></span>  
  
- <span data-ttu-id="f5e7a-116">Karmaşık türler [ilişkilendirmelere](association-type.md)katılamaz.</span><span class="sxs-lookup"><span data-stu-id="f5e7a-116">Complex types cannot participate in [associations](association-type.md).</span></span> <span data-ttu-id="f5e7a-117">İlişkinin sonu ne bir karmaşık tür olamaz, bu nedenle [Gezinti özellikleri](navigation-property.md) karmaşık türlerde tanımlanamaz.</span><span class="sxs-lookup"><span data-stu-id="f5e7a-117">Neither end of an association can be a complex type, and therefore [navigation properties](navigation-property.md) cannot be defined on complex types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f5e7a-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="f5e7a-118">Example</span></span>  

 <span data-ttu-id="f5e7a-119">[ADO.NET Entity Framework](./ef/index.md) kavramsal model tanımlamak için kavramsal şema tanım dili ([csdl](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) adlı bir etki ALANıNA özgü dil (DSL) kullanır.</span><span class="sxs-lookup"><span data-stu-id="f5e7a-119">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="f5e7a-120">Aşağıdaki csdl,,,, ve basit tür özellikleriyle karmaşık bir tür, adres `StreetAddress` tanımlar `City` `StateOrProvince` `Country` `PostalCode` .</span><span class="sxs-lookup"><span data-stu-id="f5e7a-120">The following CSDL defines a complex type, Address, with the primitive type properties `StreetAddress`, `City`, `StateOrProvince`, `Country`, and `PostalCode`.</span></span>  
  
 [!code-xml[EDM_Example_Model#ComplexTypeExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#complextypeexample)]  
  
 <span data-ttu-id="f5e7a-121">Karmaşık türü `Address` (yukarıdaki) bir varlık türünde bir özellik olarak tanımlamak için, varlık türü tanımında Özellik türünü bildirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f5e7a-121">To define the complex type `Address` (above) as a property on an entity type, you must declare the property type in the entity type definition.</span></span> <span data-ttu-id="f5e7a-122">Aşağıdaki CSDL, `Address` özelliği bir varlık türü (yayımcı) üzerinde karmaşık bir tür olarak bildirir:</span><span class="sxs-lookup"><span data-stu-id="f5e7a-122">The following CSDL declares the `Address` property as a complex type on an entity type (Publisher):</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityWithComplexType](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#entitywithcomplextype)]  
  
## <a name="see-also"></a><span data-ttu-id="f5e7a-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f5e7a-123">See also</span></span>

- [<span data-ttu-id="f5e7a-124">Varlık Veri Modeli Temel Kavramları</span><span class="sxs-lookup"><span data-stu-id="f5e7a-124">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="f5e7a-125">Varlık Veri Modeli</span><span class="sxs-lookup"><span data-stu-id="f5e7a-125">Entity Data Model</span></span>](entity-data-model.md)
