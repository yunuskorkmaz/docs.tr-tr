---
description: 'Hakkında daha fazla bilgi edinin: varlık türü'
title: entity type
ms.date: 03/30/2017
ms.assetid: a6dee9ab-9e4a-48f2-a169-3f79cc15821c
ms.openlocfilehash: fb801ca8565fce01466f30bddc8c14c39af568c6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99724368"
---
# <a name="entity-type"></a><span data-ttu-id="f6875-103">entity type</span><span class="sxs-lookup"><span data-stu-id="f6875-103">entity type</span></span>

<span data-ttu-id="f6875-104">*Varlık türü* , VARLıK VERI MODELI (EDM) ile veri yapısını açıklamak için temel yapı taşdır.</span><span class="sxs-lookup"><span data-stu-id="f6875-104">The *entity type* is the fundamental building block for describing the structure of data with the Entity Data Model (EDM).</span></span> <span data-ttu-id="f6875-105">Kavramsal modelde, varlık türü, müşteriler veya siparişler gibi üst düzey kavramların yapısını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f6875-105">In a conceptual model, an entity type represents the structure of top-level concepts, such as customers or orders.</span></span> <span data-ttu-id="f6875-106">Varlık türü, varlık türü örnekleri için bir şablondur.</span><span class="sxs-lookup"><span data-stu-id="f6875-106">An entity type is a template for entity type instances.</span></span> <span data-ttu-id="f6875-107">Her şablon aşağıdaki bilgileri içerir:</span><span class="sxs-lookup"><span data-stu-id="f6875-107">Each template contains the following information:</span></span>  
  
- <span data-ttu-id="f6875-108">Benzersiz bir ad.</span><span class="sxs-lookup"><span data-stu-id="f6875-108">A unique name.</span></span> <span data-ttu-id="f6875-109">(Gerekli.)</span><span class="sxs-lookup"><span data-stu-id="f6875-109">(Required.)</span></span>  
  
- <span data-ttu-id="f6875-110">Bir veya daha fazla özellik tarafından tanımlanan bir [varlık anahtarı](entity-key.md) .</span><span class="sxs-lookup"><span data-stu-id="f6875-110">An [entity key](entity-key.md) defined by one or more properties.</span></span> <span data-ttu-id="f6875-111">(Gerekli.)</span><span class="sxs-lookup"><span data-stu-id="f6875-111">(Required.)</span></span>  
  
- <span data-ttu-id="f6875-112">[Özellikler](property.md)biçimindeki veriler.</span><span class="sxs-lookup"><span data-stu-id="f6875-112">Data in the form of [properties](property.md).</span></span> <span data-ttu-id="f6875-113">(İsteğe bağlı.)</span><span class="sxs-lookup"><span data-stu-id="f6875-113">(Optional.)</span></span>  
  
- <span data-ttu-id="f6875-114">Bir [ilişkinin](association-type.md) bir [sonundan](association-end.md) diğer uçtan gezintiye izin veren [Gezinti özellikleri](navigation-property.md) .</span><span class="sxs-lookup"><span data-stu-id="f6875-114">[Navigation properties](navigation-property.md) that allow for navigation from one [end](association-end.md) of an [association](association-type.md) to the other end.</span></span> <span data-ttu-id="f6875-115">(İsteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="f6875-115">(Optional)</span></span>  
  
 <span data-ttu-id="f6875-116">Bir uygulamada, varlık türünün bir örneği belirli bir nesneyi (örneğin, belirli bir müşteri veya sipariş) temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f6875-116">In an application, an instance of an entity type represents a specific object (such as a specific customer or order).</span></span> <span data-ttu-id="f6875-117">Bir varlık türünün her örneğinin bir [varlık kümesi](entity-set.md)içinde benzersiz bir [varlık anahtarı](entity-key.md) olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f6875-117">Each instance of an entity type must have a unique [entity key](entity-key.md) within an [entity set](entity-set.md).</span></span>  
  
 <span data-ttu-id="f6875-118">İki varlık türü örneği, yalnızca aynı türde olmaları durumunda ve varlık anahtarlarının değerleri aynı ise eşit olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="f6875-118">Two entity type instances are considered equal only if they are of the same type and the values of their entity keys are the same.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6875-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="f6875-119">Example</span></span>  

 <span data-ttu-id="f6875-120">Aşağıdaki diyagramda üç varlık türü olan bir kavramsal model gösterilmektedir: `Book` , `Publisher` ve `Author` :</span><span class="sxs-lookup"><span data-stu-id="f6875-120">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`:</span></span>  
  
 ![Üç varlık türüne sahip örnek model](./media/entity-type/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="f6875-122">Varlık anahtarını oluşturan her varlık türünün özelliklerinin "(Key)" ile birlikte gösterilir.</span><span class="sxs-lookup"><span data-stu-id="f6875-122">Note that the properties of each entity type that make up its entity key are denoted with "(Key)".</span></span>  
  
 <span data-ttu-id="f6875-123">[ADO.NET Entity Framework](./ef/index.md) kavramsal model tanımlamak için kavramsal şema tanım dili ([csdl](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) adlı bir etki ALANıNA özgü dil (DSL) kullanır.</span><span class="sxs-lookup"><span data-stu-id="f6875-123">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="f6875-124">Aşağıdaki CSDL, `Book` Yukarıdaki diyagramda gösterilen varlık türünü tanımlar:</span><span class="sxs-lookup"><span data-stu-id="f6875-124">The following CSDL defines the `Book` entity type shown in the diagram above:</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
## <a name="see-also"></a><span data-ttu-id="f6875-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f6875-125">See also</span></span>

- [<span data-ttu-id="f6875-126">Varlık Veri Modeli Temel Kavramları</span><span class="sxs-lookup"><span data-stu-id="f6875-126">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="f6875-127">Varlık Veri Modeli</span><span class="sxs-lookup"><span data-stu-id="f6875-127">Entity Data Model</span></span>](entity-data-model.md)
- [<span data-ttu-id="f6875-128">facet</span><span class="sxs-lookup"><span data-stu-id="f6875-128">facet</span></span>](facet.md)
