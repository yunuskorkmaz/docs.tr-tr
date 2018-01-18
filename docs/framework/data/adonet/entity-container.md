---
title: "Varlık kapsayıcısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 16e80405-2c75-42fc-b0e4-b1df53b1c584
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 10e10e0a5891e9383b3a8c6dafa6e19606486b33
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="entity-container"></a><span data-ttu-id="6ff82-102">Varlık kapsayıcısı</span><span class="sxs-lookup"><span data-stu-id="6ff82-102">entity container</span></span>
<span data-ttu-id="6ff82-103">Bir *varlık kapsayıcısının* mantıksal bir gruplandırmasıdır [varlık kümeleri](../../../../docs/framework/data/adonet/entity-set.md), [ilişki kümeleri](../../../../docs/framework/data/adonet/association-set.md), ve [işlev içeri aktarmalar](../../../../docs/framework/data/adonet/model-declared-function.md).</span><span class="sxs-lookup"><span data-stu-id="6ff82-103">An *entity container* is a logical grouping of [entity sets](../../../../docs/framework/data/adonet/entity-set.md), [association sets](../../../../docs/framework/data/adonet/association-set.md), and [function imports](../../../../docs/framework/data/adonet/model-declared-function.md).</span></span>  
  
 <span data-ttu-id="6ff82-104">Aşağıdaki kavramsal modelde tanımlanan bir varlık kapsayıcısının true olması gerekir:</span><span class="sxs-lookup"><span data-stu-id="6ff82-104">The following must be true of an entity container defined in a conceptual model:</span></span>  
  
-   <span data-ttu-id="6ff82-105">En az bir varlık kapsayıcısının her kavramsal modelde tanımlanmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6ff82-105">At least one entity container must be defined in each conceptual model.</span></span>  
  
-   <span data-ttu-id="6ff82-106">Varlık kapsayıcısının her kavramsal model içinde benzersiz bir adı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6ff82-106">The entity container must have a unique name within each conceptual model.</span></span>  
  
 <span data-ttu-id="6ff82-107">Bir varlık kapsayıcısı varlık kümesi veya varlık türleri veya bir veya daha fazla ad içinde tanımlanan ilişkileri kullanan ilişkilendirme kümeleri tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6ff82-107">An entity container can define entity sets or association sets that use entity types or associations defined in one or more namespaces.</span></span> <span data-ttu-id="6ff82-108">Daha fazla bilgi için bkz: [varlık veri modeli: ad alanları](../../../../docs/framework/data/adonet/entity-data-model-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="6ff82-108">For more information, see [Entity Data Model: Namespaces](../../../../docs/framework/data/adonet/entity-data-model-namespaces.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6ff82-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="6ff82-109">Example</span></span>  
 <span data-ttu-id="6ff82-110">Aşağıdaki diyagram üç varlık türleriyle kavramsal model gösterir: `Book`, `Publisher`, ve `Author`.</span><span class="sxs-lookup"><span data-stu-id="6ff82-110">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span>  <span data-ttu-id="6ff82-111">Sonraki örnek daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="6ff82-111">See the next example for more information.</span></span>  
  
 <span data-ttu-id="6ff82-112">![Örnek modeli](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span><span class="sxs-lookup"><span data-stu-id="6ff82-112">![Example Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span></span>  
  
 <span data-ttu-id="6ff82-113">Diyagram varlık kapsayıcı bilgileri iletmek değil de, kavramsal modele bir varlık kapsayıcısı tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6ff82-113">Although the diagram does not convey entity container information, the conceptual model must define an entity container.</span></span> <span data-ttu-id="6ff82-114">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) kavramsal şema tanım dili olarak adlandırılan bir DSL kullanır ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) kavramsal modeller tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="6ff82-114">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a DSL called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="6ff82-115">Aşağıdaki CSDL Yukarıdaki diyagramda gösterildiği kavramsal model için bir varlık kapsayıcı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6ff82-115">The following CSDL defines an entity container for the conceptual model shown in the diagram above.</span></span> <span data-ttu-id="6ff82-116">Kapsayıcı adı bir XML özniteliği tanımlanır unutmayın.</span><span class="sxs-lookup"><span data-stu-id="6ff82-116">Note that the entity container name is defined in an XML attribute.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
## <a name="see-also"></a><span data-ttu-id="6ff82-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6ff82-117">See Also</span></span>  
 [<span data-ttu-id="6ff82-118">Varlık Veri Modeli Temel Kavramları</span><span class="sxs-lookup"><span data-stu-id="6ff82-118">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="6ff82-119">Varlık Veri Modeli</span><span class="sxs-lookup"><span data-stu-id="6ff82-119">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
