---
title: "karmaşık türü"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 63efbd23-11d4-4871-bc88-ad01b9837553
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 6a7fbdace6403d2f1037beff8fe28d7c934d3174
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="complex-type"></a><span data-ttu-id="cc398-102">karmaşık türü</span><span class="sxs-lookup"><span data-stu-id="cc398-102">complex type</span></span>
<span data-ttu-id="cc398-103">A *karmaşık tür* üzerinde zengin, yapılandırılmış özelliklerini tanımlamak için bir şablon [varlık türleri](../../../../docs/framework/data/adonet/entity-type.md) veya başka karmaşık türler.</span><span class="sxs-lookup"><span data-stu-id="cc398-103">A *complex type* is a template for defining rich, structured properties on [entity types](../../../../docs/framework/data/adonet/entity-type.md) or on other complex types.</span></span> <span data-ttu-id="cc398-104">Her bir şablon aşağıdakileri içerir:</span><span class="sxs-lookup"><span data-stu-id="cc398-104">Each template contains the following:</span></span>  
  
-   <span data-ttu-id="cc398-105">Benzersiz bir ad.</span><span class="sxs-lookup"><span data-stu-id="cc398-105">A unique name.</span></span> <span data-ttu-id="cc398-106">(Gerekli)</span><span class="sxs-lookup"><span data-stu-id="cc398-106">(Required)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="cc398-107">Karmaşık bir tür adı aynı ad alanı içindeki bir varlık türü adı ile aynı olamaz.</span><span class="sxs-lookup"><span data-stu-id="cc398-107">The name of a complex type cannot be the same as an entity type name within the same namespace.</span></span>  
  
-   <span data-ttu-id="cc398-108">Bir veya daha fazla form verileri [özellikleri](../../../../docs/framework/data/adonet/property.md).</span><span class="sxs-lookup"><span data-stu-id="cc398-108">Data in the form of one or more [properties](../../../../docs/framework/data/adonet/property.md).</span></span> <span data-ttu-id="cc398-109">(İsteğe bağlı.)</span><span class="sxs-lookup"><span data-stu-id="cc398-109">(Optional.)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="cc398-110">Karmaşık türde bir özellik, başka bir karmaşık tür olabilir.</span><span class="sxs-lookup"><span data-stu-id="cc398-110">A property of a complex type can be another complex type.</span></span>  
  
 <span data-ttu-id="cc398-111">Karmaşık bir tür, karmaşık bir tür veri yükü ilkel tür özellikleri biçiminde veya başka karmaşık türler taşıyabilir, bir varlık türüne benzerdir.</span><span class="sxs-lookup"><span data-stu-id="cc398-111">A complex type is similar to an entity type in that a complex type can carry a data payload in the form of primitive type properties or other complex types.</span></span> <span data-ttu-id="cc398-112">Ancak, karmaşık türleri ve varlık türleri arasındaki bazı temel farklar vardır:</span><span class="sxs-lookup"><span data-stu-id="cc398-112">However, there are some key differences between complex types and entity types:</span></span>  
  
-   <span data-ttu-id="cc398-113">Karmaşık türler kimliklerine sahip değil ve bu nedenle bağımsız olarak bulunamaz.</span><span class="sxs-lookup"><span data-stu-id="cc398-113">Complex types do not have identities and therefore cannot exist independently.</span></span> <span data-ttu-id="cc398-114">Karmaşık türler yalnızca varlık türleri veya diğer karmaşık türler özellikleri olarak bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="cc398-114">Complex types can only exist as properties on entity types or other complex types.</span></span>  
  
-   <span data-ttu-id="cc398-115">Karmaşık türler olamaz katılmak [ilişkilendirmeleri](../../../../docs/framework/data/adonet/association-type.md).</span><span class="sxs-lookup"><span data-stu-id="cc398-115">Complex types cannot participate in [associations](../../../../docs/framework/data/adonet/association-type.md).</span></span> <span data-ttu-id="cc398-116">Bir ilişkilendirme hiçbiri sonuna bir karmaşık tür olabilir ve bu nedenle [Gezinti özellikleri](../../../../docs/framework/data/adonet/navigation-property.md) karmaşık türlerinde tanımlanamaz.</span><span class="sxs-lookup"><span data-stu-id="cc398-116">Neither end of an association can be a complex type, and therefore [navigation properties](../../../../docs/framework/data/adonet/navigation-property.md) cannot be defined on complex types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cc398-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="cc398-117">Example</span></span>  
 <span data-ttu-id="cc398-118">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) kavramsal şema tanım dili adlı bir etki alanına özgü dil (DSL) kullanır ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) kavramsal modeller tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="cc398-118">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="cc398-119">Aşağıdaki CSDL bir karmaşık türü, adres, ilkel türü özellikleri ile tanımlayan `StreetAddress`, `City`, `StateOrProvince`, `Country`, ve `PostalCode`.</span><span class="sxs-lookup"><span data-stu-id="cc398-119">The following CSDL defines a complex type, Address, with the primitive type properties `StreetAddress`, `City`, `StateOrProvince`, `Country`, and `PostalCode`.</span></span>  
  
 [!code-xml[EDM_Example_Model#ComplexTypeExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#complextypeexample)]  
  
 <span data-ttu-id="cc398-120">Karmaşık türü tanımlamak için `Address` (yukarıda) bir varlık türünde bir özellik olarak, özellik türü varlık türü tanımında belirtmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="cc398-120">To define the complex type `Address` (above) as a property on an entity type, you must declare the property type in the entity type definition.</span></span> <span data-ttu-id="cc398-121">Aşağıdaki CSDL bildirir `Address` özelliği bir karmaşık tür üzerinde bir varlık türü (yayımcı) olarak:</span><span class="sxs-lookup"><span data-stu-id="cc398-121">The following CSDL declares the `Address` property as a complex type on an entity type (Publisher):</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityWithComplexType](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#entitywithcomplextype)]  
  
## <a name="see-also"></a><span data-ttu-id="cc398-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cc398-122">See Also</span></span>  
 [<span data-ttu-id="cc398-123">Varlık Veri Modeli Temel Kavramları</span><span class="sxs-lookup"><span data-stu-id="cc398-123">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="cc398-124">Varlık Veri Modeli</span><span class="sxs-lookup"><span data-stu-id="cc398-124">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
