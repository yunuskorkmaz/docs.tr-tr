---
title: entity type
ms.date: 03/30/2017
ms.assetid: a6dee9ab-9e4a-48f2-a169-3f79cc15821c
ms.openlocfilehash: efd3ea0972148e885d4b22b49040640539bb28cd
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795123"
---
# <a name="entity-type"></a><span data-ttu-id="3759c-102">entity type</span><span class="sxs-lookup"><span data-stu-id="3759c-102">entity type</span></span>
<span data-ttu-id="3759c-103">*Varlık türü* , VARLıK VERI MODELI (EDM) ile veri yapısını açıklamak için temel yapı taşdır.</span><span class="sxs-lookup"><span data-stu-id="3759c-103">The *entity type* is the fundamental building block for describing the structure of data with the Entity Data Model (EDM).</span></span> <span data-ttu-id="3759c-104">Kavramsal modelde, varlık türü, müşteriler veya siparişler gibi üst düzey kavramların yapısını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3759c-104">In a conceptual model, an entity type represents the structure of top-level concepts, such as customers or orders.</span></span> <span data-ttu-id="3759c-105">Varlık türü, varlık türü örnekleri için bir şablondur.</span><span class="sxs-lookup"><span data-stu-id="3759c-105">An entity type is a template for entity type instances.</span></span> <span data-ttu-id="3759c-106">Her şablon aşağıdaki bilgileri içerir:</span><span class="sxs-lookup"><span data-stu-id="3759c-106">Each template contains the following information:</span></span>  
  
- <span data-ttu-id="3759c-107">Benzersiz bir ad.</span><span class="sxs-lookup"><span data-stu-id="3759c-107">A unique name.</span></span> <span data-ttu-id="3759c-108">(Gerekli.)</span><span class="sxs-lookup"><span data-stu-id="3759c-108">(Required.)</span></span>  
  
- <span data-ttu-id="3759c-109">Bir veya daha fazla özellik tarafından tanımlanan bir [varlık anahtarı](entity-key.md) .</span><span class="sxs-lookup"><span data-stu-id="3759c-109">An [entity key](entity-key.md) defined by one or more properties.</span></span> <span data-ttu-id="3759c-110">(Gerekli.)</span><span class="sxs-lookup"><span data-stu-id="3759c-110">(Required.)</span></span>  
  
- <span data-ttu-id="3759c-111">[Özellikler](property.md)biçimindeki veriler.</span><span class="sxs-lookup"><span data-stu-id="3759c-111">Data in the form of [properties](property.md).</span></span> <span data-ttu-id="3759c-112">(İsteğe bağlı.)</span><span class="sxs-lookup"><span data-stu-id="3759c-112">(Optional.)</span></span>  
  
- <span data-ttu-id="3759c-113">Bir [ilişkinin](association-type.md) bir [sonundan](association-end.md) diğer uçtan gezintiye izin veren [Gezinti özellikleri](navigation-property.md) .</span><span class="sxs-lookup"><span data-stu-id="3759c-113">[Navigation properties](navigation-property.md) that allow for navigation from one [end](association-end.md) of an [association](association-type.md) to the other end.</span></span> <span data-ttu-id="3759c-114">(İsteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="3759c-114">(Optional)</span></span>  
  
 <span data-ttu-id="3759c-115">Bir uygulamada, varlık türünün bir örneği belirli bir nesneyi (örneğin, belirli bir müşteri veya sipariş) temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3759c-115">In an application, an instance of an entity type represents a specific object (such as a specific customer or order).</span></span> <span data-ttu-id="3759c-116">Bir varlık türünün her örneğinin bir [varlık kümesi](entity-set.md)içinde benzersiz bir [varlık anahtarı](entity-key.md) olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3759c-116">Each instance of an entity type must have a unique [entity key](entity-key.md) within an [entity set](entity-set.md).</span></span>  
  
 <span data-ttu-id="3759c-117">İki varlık türü örneği, yalnızca aynı türde olmaları durumunda ve varlık anahtarlarının değerleri aynı ise eşit olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="3759c-117">Two entity type instances are considered equal only if they are of the same type and the values of their entity keys are the same.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3759c-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="3759c-118">Example</span></span>  
 <span data-ttu-id="3759c-119">Aşağıdaki diyagramda üç varlık türü olan bir kavramsal model gösterilmektedir: `Book`, `Publisher`ve `Author`:</span><span class="sxs-lookup"><span data-stu-id="3759c-119">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`:</span></span>  
  
 ![Üç varlık türüne sahip örnek model](./media/entity-type/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="3759c-121">Varlık anahtarını oluşturan her varlık türünün özelliklerinin "(Key)" ile birlikte gösterilir.</span><span class="sxs-lookup"><span data-stu-id="3759c-121">Note that the properties of each entity type that make up its entity key are denoted with "(Key)".</span></span>  
  
 <span data-ttu-id="3759c-122">[ADO.NET Entity Framework](./ef/index.md) kavramsal model tanımlamak için kavramsal şema tanım dili ([csdl](./ef/language-reference/csdl-specification.md)) adlı bir etki ALANıNA özgü dil (DSL) kullanır.</span><span class="sxs-lookup"><span data-stu-id="3759c-122">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](./ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="3759c-123">Aşağıdaki csdl, Yukarıdaki diyagramda `Book` gösterilen varlık türünü tanımlar:</span><span class="sxs-lookup"><span data-stu-id="3759c-123">The following CSDL defines the `Book` entity type shown in the diagram above:</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
## <a name="see-also"></a><span data-ttu-id="3759c-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3759c-124">See also</span></span>

- [<span data-ttu-id="3759c-125">Varlık Veri Modeli Temel Kavramları</span><span class="sxs-lookup"><span data-stu-id="3759c-125">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="3759c-126">Varlık Veri Modeli</span><span class="sxs-lookup"><span data-stu-id="3759c-126">Entity Data Model</span></span>](entity-data-model.md)
- [<span data-ttu-id="3759c-127">facet</span><span class="sxs-lookup"><span data-stu-id="3759c-127">facet</span></span>](facet.md)
