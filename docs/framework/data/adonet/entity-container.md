---
title: Varlık kapsayıcı
ms.date: 03/30/2017
ms.assetid: 16e80405-2c75-42fc-b0e4-b1df53b1c584
ms.openlocfilehash: d2ad565ce73b2de4b10d2f15406b283a13bbef6e
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2019
ms.locfileid: "58409893"
---
# <a name="entity-container"></a><span data-ttu-id="e1e06-102">Varlık kapsayıcı</span><span class="sxs-lookup"><span data-stu-id="e1e06-102">entity container</span></span>
<span data-ttu-id="e1e06-103">Bir *varlık kapsayıcısı* mantıksal bir gruplandırmasıdır [varlık kümeleri](../../../../docs/framework/data/adonet/entity-set.md), [ilişki Setleri](../../../../docs/framework/data/adonet/association-set.md), ve [işlev içeri aktarmalar](../../../../docs/framework/data/adonet/model-declared-function.md).</span><span class="sxs-lookup"><span data-stu-id="e1e06-103">An *entity container* is a logical grouping of [entity sets](../../../../docs/framework/data/adonet/entity-set.md), [association sets](../../../../docs/framework/data/adonet/association-set.md), and [function imports](../../../../docs/framework/data/adonet/model-declared-function.md).</span></span>  
  
 <span data-ttu-id="e1e06-104">Aşağıdaki kavramsal modelde tanımlı bir varlık kapsayıcısının true olması gerekir:</span><span class="sxs-lookup"><span data-stu-id="e1e06-104">The following must be true of an entity container defined in a conceptual model:</span></span>  
  
-   <span data-ttu-id="e1e06-105">En az bir varlık kapsayıcısı her kavramsal modelde tanımlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e1e06-105">At least one entity container must be defined in each conceptual model.</span></span>  
  
-   <span data-ttu-id="e1e06-106">Varlık kapsayıcısının her kavramsal model içinde benzersiz bir adı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e1e06-106">The entity container must have a unique name within each conceptual model.</span></span>  
  
 <span data-ttu-id="e1e06-107">Varlık kapsayıcısı varlık kümeleri veya varlık türleri veya bir veya daha fazla ad alanı içinde tanımlanan ilişkileri kullanın ve ilişki Setleri tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e1e06-107">An entity container can define entity sets or association sets that use entity types or associations defined in one or more namespaces.</span></span> <span data-ttu-id="e1e06-108">Daha fazla bilgi için [varlık veri modeli: Ad alanları](../../../../docs/framework/data/adonet/entity-data-model-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="e1e06-108">For more information, see [Entity Data Model: Namespaces](../../../../docs/framework/data/adonet/entity-data-model-namespaces.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e1e06-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="e1e06-109">Example</span></span>  
 <span data-ttu-id="e1e06-110">Varlık üç kavramsal bir modelle Aşağıdaki diyagramda gösterilmektedir: `Book`, `Publisher`, ve `Author`.</span><span class="sxs-lookup"><span data-stu-id="e1e06-110">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span>  <span data-ttu-id="e1e06-111">Daha fazla bilgi için sonraki örneğe bakın.</span><span class="sxs-lookup"><span data-stu-id="e1e06-111">See the next example for more information.</span></span>  
  
 ![Üç varlık türleri ile örnek modeli](./media/entity-container/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="e1e06-113">Diyagram varlık kapsayıcı bilgilerini sağlamadığından olsa da, kavramsal modelin varlık kapsayıcısı tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e1e06-113">Although the diagram does not convey entity container information, the conceptual model must define an entity container.</span></span> <span data-ttu-id="e1e06-114">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) kavramsal şema tanım dili olarak adlandırılan bir DSL kullanır ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) kavramsal modeller tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="e1e06-114">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a DSL called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="e1e06-115">Yukarıdaki diyagramda gösterilen kavramsal modelin varlık kapsayıcısı aşağıdaki CSDL tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e1e06-115">The following CSDL defines an entity container for the conceptual model shown in the diagram above.</span></span> <span data-ttu-id="e1e06-116">Varlık kapsayıcı adı bir XML özniteliği tanımlandığını aklınızda bulundurun.</span><span class="sxs-lookup"><span data-stu-id="e1e06-116">Note that the entity container name is defined in an XML attribute.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
## <a name="see-also"></a><span data-ttu-id="e1e06-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e1e06-117">See also</span></span>
- [<span data-ttu-id="e1e06-118">Varlık Veri Modeli Temel Kavramları</span><span class="sxs-lookup"><span data-stu-id="e1e06-118">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [<span data-ttu-id="e1e06-119">Varlık Veri Modeli</span><span class="sxs-lookup"><span data-stu-id="e1e06-119">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
