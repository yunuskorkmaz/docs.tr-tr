---
title: entity container
ms.date: 03/30/2017
ms.assetid: 16e80405-2c75-42fc-b0e4-b1df53b1c584
ms.openlocfilehash: 95fb59c86f951e75f0988f45219fd07cbb003c01
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91200829"
---
# <a name="entity-container"></a><span data-ttu-id="ab537-102">entity container</span><span class="sxs-lookup"><span data-stu-id="ab537-102">entity container</span></span>

<span data-ttu-id="ab537-103">Bir *varlık kapsayıcısı* , [varlık kümelerinin](entity-set.md), [ilişkilendirme kümelerinin](association-set.md)ve [işlev içeri aktarmalarının](model-declared-function.md)mantıksal gruplandırmasıdır.</span><span class="sxs-lookup"><span data-stu-id="ab537-103">An *entity container* is a logical grouping of [entity sets](entity-set.md), [association sets](association-set.md), and [function imports](model-declared-function.md).</span></span>  
  
 <span data-ttu-id="ab537-104">Aşağıdaki bir kavramsal modelde tanımlanan bir varlık kapsayıcısının doğru olması gerekir:</span><span class="sxs-lookup"><span data-stu-id="ab537-104">The following must be true of an entity container defined in a conceptual model:</span></span>  
  
- <span data-ttu-id="ab537-105">Her kavramsal modelde en az bir varlık kapsayıcısının tanımlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ab537-105">At least one entity container must be defined in each conceptual model.</span></span>  
  
- <span data-ttu-id="ab537-106">Varlık kapsayıcısının her kavramsal model içinde benzersiz bir adı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ab537-106">The entity container must have a unique name within each conceptual model.</span></span>  
  
 <span data-ttu-id="ab537-107">Bir varlık kapsayıcısı, bir veya daha fazla ad alanında tanımlanan varlık türlerini veya ilişkilerini kullanan varlık kümelerini veya ilişki kümelerini tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="ab537-107">An entity container can define entity sets or association sets that use entity types or associations defined in one or more namespaces.</span></span> <span data-ttu-id="ab537-108">Daha fazla bilgi için bkz. [varlık veri modeli: ad alanları](entity-data-model-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="ab537-108">For more information, see [Entity Data Model: Namespaces](entity-data-model-namespaces.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ab537-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="ab537-109">Example</span></span>  

 <span data-ttu-id="ab537-110">Aşağıdaki diyagramda üç varlık türü olan kavramsal model gösterilmektedir: `Book` , `Publisher` , ve `Author` .</span><span class="sxs-lookup"><span data-stu-id="ab537-110">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span>  <span data-ttu-id="ab537-111">Daha fazla bilgi için bkz. sonraki örnek.</span><span class="sxs-lookup"><span data-stu-id="ab537-111">See the next example for more information.</span></span>  
  
 ![Üç varlık türüne sahip örnek model](./media/entity-container/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="ab537-113">Diyagram varlık kapsayıcı bilgilerini iletmese de, kavramsal model bir varlık kapsayıcısı tanımlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="ab537-113">Although the diagram does not convey entity container information, the conceptual model must define an entity container.</span></span> <span data-ttu-id="ab537-114">[ADO.NET Entity Framework](./ef/index.md) kavramsal modelleri tanımlamak için kavramsal şema tanım dili ([csdl](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) adlı bir DSL kullanır.</span><span class="sxs-lookup"><span data-stu-id="ab537-114">The [ADO.NET Entity Framework](./ef/index.md) uses a DSL called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="ab537-115">Aşağıdaki CSDL, Yukarıdaki diyagramda gösterilen kavramsal model için bir varlık kapsayıcısı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ab537-115">The following CSDL defines an entity container for the conceptual model shown in the diagram above.</span></span> <span data-ttu-id="ab537-116">Varlık kapsayıcısı adının bir XML özniteliğinde tanımlandığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="ab537-116">Note that the entity container name is defined in an XML attribute.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
## <a name="see-also"></a><span data-ttu-id="ab537-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ab537-117">See also</span></span>

- [<span data-ttu-id="ab537-118">Varlık Veri Modeli Temel Kavramları</span><span class="sxs-lookup"><span data-stu-id="ab537-118">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="ab537-119">Varlık Veri Modeli</span><span class="sxs-lookup"><span data-stu-id="ab537-119">Entity Data Model</span></span>](entity-data-model.md)
