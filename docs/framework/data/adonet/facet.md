---
title: facet
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 91c4e6aa-3e54-4b6c-a38a-abf27808cc85
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: e72ecd610951a42ceb5c3aa581bf70f255e5e2f7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="facet"></a><span data-ttu-id="4f9ec-102">facet</span><span class="sxs-lookup"><span data-stu-id="4f9ec-102">facet</span></span>
<span data-ttu-id="4f9ec-103">A *modeli* bir ilkel tür özelliği tanımına ayrıntı eklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4f9ec-103">A *facet* is used to add detail to a primitive type property definition.</span></span> <span data-ttu-id="4f9ec-104">A [özelliği](../../../../docs/framework/data/adonet/property.md) tanımını özellik türü hakkında bilgi içerir, ancak genellikle daha fazla ayrıntı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="4f9ec-104">A [property](../../../../docs/framework/data/adonet/property.md) definition contains information about the property type, but often more detail is necessary.</span></span> <span data-ttu-id="4f9ec-105">Örneğin, bir varlık türü kavramsal modelde türünde bir özellik olabilir `String` değeri ayarlanamıyor null.</span><span class="sxs-lookup"><span data-stu-id="4f9ec-105">For example, an entity type in a conceptual model might have a property of type `String` whose value cannot be set to null.</span></span> <span data-ttu-id="4f9ec-106">Modeller, bu düzeyde ayrıntı belirtmenize olanak verir.</span><span class="sxs-lookup"><span data-stu-id="4f9ec-106">Facets allow you to specify this level of detail.</span></span>  
  
 <span data-ttu-id="4f9ec-107">Aşağıdaki tabloda EDM desteklenen modellerle açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4f9ec-107">The table below describes the facets that are supported in the EDM.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4f9ec-108">Modelleri davranışlarını ve değerleri tam EDM uygulaması kullanan çalışma zamanı ortamı tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="4f9ec-108">The exact values and behaviors of facets are determined by the run-time environment that uses an EDM implementation.</span></span>  
  
|<span data-ttu-id="4f9ec-109">Modeli</span><span class="sxs-lookup"><span data-stu-id="4f9ec-109">Facet</span></span>|<span data-ttu-id="4f9ec-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4f9ec-110">Description</span></span>|<span data-ttu-id="4f9ec-111">Uygulandığı öğe:</span><span class="sxs-lookup"><span data-stu-id="4f9ec-111">Applies to</span></span>|  
|-----------|-----------------|----------------|  
|`Collation`|<span data-ttu-id="4f9ec-112">Harmanlama sırası (veya sıralama) yapılırken kullanılacak karşılaştırma gerçekleştirme ve özellik değerleri operations sıralama belirtir.</span><span class="sxs-lookup"><span data-stu-id="4f9ec-112">Specifies the collating sequence (or sorting sequence) to be used when performing comparison and ordering operations on values of the property.</span></span>|`String`|  
|`ConcurrencyMode`|<span data-ttu-id="4f9ec-113">Özelliğinin değeri iyimser eşzamanlılık denetimleri için kullanılması gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="4f9ec-113">Indicates that the value of the property should be used for optimistic concurrency checks.</span></span>|<span data-ttu-id="4f9ec-114">Tüm basit tür özellikleri</span><span class="sxs-lookup"><span data-stu-id="4f9ec-114">All primitive type properties</span></span>|  
|`Default`|<span data-ttu-id="4f9ec-115">Örnek oluşturma sırasında herhangi bir değer belirtilirse özelliğinin varsayılan değeri belirtir.</span><span class="sxs-lookup"><span data-stu-id="4f9ec-115">Specifies the default value of the property if no value is supplied upon instantiation.</span></span>|<span data-ttu-id="4f9ec-116">Tüm basit tür özellikleri</span><span class="sxs-lookup"><span data-stu-id="4f9ec-116">All primitive type properties</span></span>|  
|`FixedLength`|<span data-ttu-id="4f9ec-117">Özellik değerinin uzunluğu değişebilir olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4f9ec-117">Specifies whether the length of the property value can vary.</span></span>|<span data-ttu-id="4f9ec-118">`Binary`, `String`</span><span class="sxs-lookup"><span data-stu-id="4f9ec-118">`Binary`, `String`</span></span>|  
|`MaxLength`|<span data-ttu-id="4f9ec-119">Özellik değerinin uzunluk üst sınırını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4f9ec-119">Specifies the maximum length of the property value.</span></span>|<span data-ttu-id="4f9ec-120">`Binary`, `String`</span><span class="sxs-lookup"><span data-stu-id="4f9ec-120">`Binary`, `String`</span></span>|  
|`Nullable`|<span data-ttu-id="4f9ec-121">Özelliği bir null değere sahip olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4f9ec-121">Specifies whether the property can have a null value.</span></span>|<span data-ttu-id="4f9ec-122">Tüm basit tür özellikleri</span><span class="sxs-lookup"><span data-stu-id="4f9ec-122">All primitive type properties</span></span>|  
|`Precision`|<span data-ttu-id="4f9ec-123">Tür özellikleri için `Decimal`, bir özellik değeri olabilir basamak sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4f9ec-123">For properties of type `Decimal`, specifies the number of digits a property value can have.</span></span> <span data-ttu-id="4f9ec-124">Tür özellikleri için `Time`, `DateTime`, ve `DateTimeOffset`, özellik değerinin saniye kesirli kısmı için basamak sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4f9ec-124">For properties of type `Time`, `DateTime`, and `DateTimeOffset`, specifies the number of digits for the fractional part of seconds of the property value.</span></span>|<span data-ttu-id="4f9ec-125">`DateTime`, `DateTimeOffset`, `Decimal`, `Time`,</span><span class="sxs-lookup"><span data-stu-id="4f9ec-125">`DateTime`, `DateTimeOffset`, `Decimal`, `Time`,</span></span>|  
|`Scale`|<span data-ttu-id="4f9ec-126">Özellik değeri için ondalık basamak sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4f9ec-126">Specifies the number of digits to the right of the decimal point for the property value.</span></span>|<span data-ttu-id="4f9ec-127">Ondalık</span><span class="sxs-lookup"><span data-stu-id="4f9ec-127">Decimal</span></span>|  
|`Unicode`|<span data-ttu-id="4f9ec-128">Özellik değeri Unicode olarak depolanan olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="4f9ec-128">Indicates whether the property value is stored as Unicode.</span></span>|`String`|  
  
## <a name="example"></a><span data-ttu-id="4f9ec-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="4f9ec-129">Example</span></span>  
 <span data-ttu-id="4f9ec-130">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) kavramsal şema tanım dili adlı bir etki alanına özgü dil (DSL) kullanır ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) kavramsal modeller tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="4f9ec-130">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="4f9ec-131">Aşağıdaki CSDL tanımlayan bir `Book` varlık türü.</span><span class="sxs-lookup"><span data-stu-id="4f9ec-131">The following CSDL defines a `Book` entity type.</span></span> <span data-ttu-id="4f9ec-132">Modelleri XML öznitelikleri olarak uygulandığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="4f9ec-132">Note that facets are implemented as XML attributes.</span></span> <span data-ttu-id="4f9ec-133">Bir özellik ayarlanabilir, model değerleri gösterir null ve `Scale` ve `Precision` , `Revision` özelliği her ayarlanır 29 için.</span><span class="sxs-lookup"><span data-stu-id="4f9ec-133">The facet values indicate that no property can be set to null, and that the `Scale` and `Precision` of the `Revision` property are each set to 29.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
## <a name="see-also"></a><span data-ttu-id="4f9ec-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4f9ec-134">See Also</span></span>  
 [<span data-ttu-id="4f9ec-135">Varlık veri modeli temel kavramları</span><span class="sxs-lookup"><span data-stu-id="4f9ec-135">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="4f9ec-136">Varlık veri modeli</span><span class="sxs-lookup"><span data-stu-id="4f9ec-136">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
