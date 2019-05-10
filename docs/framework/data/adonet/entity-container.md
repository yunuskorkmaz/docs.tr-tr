---
title: entity container
ms.date: 03/30/2017
ms.assetid: 16e80405-2c75-42fc-b0e4-b1df53b1c584
ms.openlocfilehash: 58642c6cc794f931387ac7a76dd64d368957f14b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64586957"
---
# <a name="entity-container"></a><span data-ttu-id="056cf-102">entity container</span><span class="sxs-lookup"><span data-stu-id="056cf-102">entity container</span></span>
<span data-ttu-id="056cf-103">Bir *varlık kapsayıcısı* mantıksal bir gruplandırmasıdır [varlık kümeleri](../../../../docs/framework/data/adonet/entity-set.md), [ilişki Setleri](../../../../docs/framework/data/adonet/association-set.md), ve [işlev içeri aktarmalar](../../../../docs/framework/data/adonet/model-declared-function.md).</span><span class="sxs-lookup"><span data-stu-id="056cf-103">An *entity container* is a logical grouping of [entity sets](../../../../docs/framework/data/adonet/entity-set.md), [association sets](../../../../docs/framework/data/adonet/association-set.md), and [function imports](../../../../docs/framework/data/adonet/model-declared-function.md).</span></span>  
  
 <span data-ttu-id="056cf-104">Aşağıdaki kavramsal modelde tanımlı bir varlık kapsayıcısının true olması gerekir:</span><span class="sxs-lookup"><span data-stu-id="056cf-104">The following must be true of an entity container defined in a conceptual model:</span></span>  
  
- <span data-ttu-id="056cf-105">En az bir varlık kapsayıcısı her kavramsal modelde tanımlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="056cf-105">At least one entity container must be defined in each conceptual model.</span></span>  
  
- <span data-ttu-id="056cf-106">Varlık kapsayıcısının her kavramsal model içinde benzersiz bir adı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="056cf-106">The entity container must have a unique name within each conceptual model.</span></span>  
  
 <span data-ttu-id="056cf-107">Varlık kapsayıcısı varlık kümeleri veya varlık türleri veya bir veya daha fazla ad alanı içinde tanımlanan ilişkileri kullanın ve ilişki Setleri tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="056cf-107">An entity container can define entity sets or association sets that use entity types or associations defined in one or more namespaces.</span></span> <span data-ttu-id="056cf-108">Daha fazla bilgi için [varlık veri modeli: Ad alanları](../../../../docs/framework/data/adonet/entity-data-model-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="056cf-108">For more information, see [Entity Data Model: Namespaces](../../../../docs/framework/data/adonet/entity-data-model-namespaces.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="056cf-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="056cf-109">Example</span></span>  
 <span data-ttu-id="056cf-110">Varlık üç kavramsal bir modelle Aşağıdaki diyagramda gösterilmektedir: `Book`, `Publisher`, ve `Author`.</span><span class="sxs-lookup"><span data-stu-id="056cf-110">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span>  <span data-ttu-id="056cf-111">Daha fazla bilgi için sonraki örneğe bakın.</span><span class="sxs-lookup"><span data-stu-id="056cf-111">See the next example for more information.</span></span>  
  
 ![Üç varlık türleri ile örnek modeli](./media/entity-container/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="056cf-113">Diyagram varlık kapsayıcı bilgilerini sağlamadığından olsa da, kavramsal modelin varlık kapsayıcısı tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="056cf-113">Although the diagram does not convey entity container information, the conceptual model must define an entity container.</span></span> <span data-ttu-id="056cf-114">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) kavramsal şema tanım dili olarak adlandırılan bir DSL kullanır ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) kavramsal modeller tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="056cf-114">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a DSL called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="056cf-115">Yukarıdaki diyagramda gösterilen kavramsal modelin varlık kapsayıcısı aşağıdaki CSDL tanımlar.</span><span class="sxs-lookup"><span data-stu-id="056cf-115">The following CSDL defines an entity container for the conceptual model shown in the diagram above.</span></span> <span data-ttu-id="056cf-116">Varlık kapsayıcı adı bir XML özniteliği tanımlandığını aklınızda bulundurun.</span><span class="sxs-lookup"><span data-stu-id="056cf-116">Note that the entity container name is defined in an XML attribute.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
## <a name="see-also"></a><span data-ttu-id="056cf-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="056cf-117">See also</span></span>

- [<span data-ttu-id="056cf-118">Varlık Veri Modeli Temel Kavramları</span><span class="sxs-lookup"><span data-stu-id="056cf-118">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [<span data-ttu-id="056cf-119">Varlık Veri Modeli</span><span class="sxs-lookup"><span data-stu-id="056cf-119">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
