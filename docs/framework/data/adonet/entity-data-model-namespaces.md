---
title: 'Varlık Veri Modeli: Ad Alanları'
ms.date: 03/30/2017
ms.assetid: 98ab4226-bb9f-44e7-af46-61a9b1a4e47c
ms.openlocfilehash: 1e5f9527ec208c5650c68fe35bb758e0850b7700
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91194836"
---
# <a name="entity-data-model-namespaces"></a><span data-ttu-id="e8644-102">Varlık Veri Modeli: Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="e8644-102">Entity Data Model: Namespaces</span></span>

<span data-ttu-id="e8644-103">Varlık Veri Modeli (EDM) içindeki bir ad alanı, [varlık türleri](entity-type.md), [karmaşık türler](complex-type.md)ve [ilişkilendirmeler](association-type.md)için soyut bir kapsayıcıdır.</span><span class="sxs-lookup"><span data-stu-id="e8644-103">A namespace in the Entity Data Model (EDM) is an abstract container for [entity types](entity-type.md), [complex types](complex-type.md), and [associations](association-type.md).</span></span> <span data-ttu-id="e8644-104">EDM 'daki ad alanları, bir programlama dilinde ad alanlarına benzerdir: içerdikleri nesneler için bağlam sağlar ve aynı ada sahip nesneleri belirsizliğini (ancak farklı ad alanlarında bulunan) ayırt etmek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="e8644-104">Namespaces in the EDM are similar to namespaces in a programming language: they provide context for the objects that they contain and they provide a way to disambiguate objects that have the same name (but are contained in different namespaces).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8644-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="e8644-105">Example</span></span>  

 <span data-ttu-id="e8644-106">[ADO.NET Entity Framework](./ef/index.md) kavramsal model tanımlamak için kavramsal şema tanım dili ([csdl](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) adlı bir etki ALANıNA özgü dil (DSL) kullanır.</span><span class="sxs-lookup"><span data-stu-id="e8644-106">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="e8644-107">Aşağıdaki CSDL kodu, farklı bir kavramsal modelde tanımlanan bir türü tanımlamak için bir ad alanı kullanır.</span><span class="sxs-lookup"><span data-stu-id="e8644-107">The following CSDL code uses a namespace to identify a type that is defined in a different conceptual model.</span></span> <span data-ttu-id="e8644-108">Örnek, `Publisher` `Address` ad alanından içeri aktarılan karmaşık tür özelliğine () sahip bir varlık türü () tanımlar `ExtendedBooksModel` .</span><span class="sxs-lookup"><span data-stu-id="e8644-108">The example defines an entity type (`Publisher`) that has a complex type property (`Address`) that is imported from the `ExtendedBooksModel` namespace.</span></span> <span data-ttu-id="e8644-109">`Using`Öğesinin bir ad alanının içeri aktarıldığını olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="e8644-109">Note that the `Using` element indicates that a namespace has been imported.</span></span> <span data-ttu-id="e8644-110">Ayrıca, özelliğin türünün, `Address` `ExtendedBooksModel.Address` Bu türün ad alanında tanımlandığını belirten tam adı () kullanılarak tanımlandığını unutmayın `ExtendedBooksModel` .</span><span class="sxs-lookup"><span data-stu-id="e8644-110">Also note that the type of the `Address` property is defined by using its fully qualified name (`ExtendedBooksModel.Address`), indicating that this type is defined in the `ExtendedBooksModel` namespace.</span></span>  
  
 [!code-xml[EDM_Example_Model#ImportedNamespace](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books6.edmx#importednamespace)]  
  
## <a name="see-also"></a><span data-ttu-id="e8644-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e8644-111">See also</span></span>

- [<span data-ttu-id="e8644-112">Varlık Veri Modeli Temel Kavramları</span><span class="sxs-lookup"><span data-stu-id="e8644-112">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="e8644-113">Varlık Veri Modeli</span><span class="sxs-lookup"><span data-stu-id="e8644-113">Entity Data Model</span></span>](entity-data-model.md)
