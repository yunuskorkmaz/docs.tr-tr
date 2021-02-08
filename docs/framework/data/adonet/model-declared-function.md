---
description: 'Daha fazla bilgi edinin: model tarafından belirtilen işlev'
title: model-declared function
ms.date: 03/30/2017
ms.assetid: aba87f13-5685-4f6b-ad14-918e8a7d5c2a
ms.openlocfilehash: c9a5cedb8c9706aa0d299635f60f762b92ca6d78
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786270"
---
# <a name="model-declared-function"></a><span data-ttu-id="dd626-103">model-declared function</span><span class="sxs-lookup"><span data-stu-id="dd626-103">model-declared function</span></span>

<span data-ttu-id="dd626-104">Model olarak tanımlanmış bir *işlev* , kavramsal modelde belirtilen ancak bu kavramsal modelde tanımlı olmayan bir işlevdir.</span><span class="sxs-lookup"><span data-stu-id="dd626-104">A *model-declared function* is a function that is declared in a conceptual model, but is not defined in that conceptual model.</span></span> <span data-ttu-id="dd626-105">İşlev barındırma veya depolama ortamında tanımlanmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="dd626-105">The function might be defined in the hosting or storage environment.</span></span> <span data-ttu-id="dd626-106">Örneğin, model tarafından tanımlanan bir işlev, veritabanında tanımlanmış bir işlevle eşleştirilebilir ve bu nedenle kavramsal modelde sunucu tarafı işlevselliği ortaya çıkabilir.</span><span class="sxs-lookup"><span data-stu-id="dd626-106">For example, a model-declared function might be mapped to a function that is defined in a database, thus exposing server-side functionality in the conceptual model.</span></span>  
  
 <span data-ttu-id="dd626-107">Model tarafından tanımlanan bir işlevin bildirimi, aşağıdaki bilgileri içerir:</span><span class="sxs-lookup"><span data-stu-id="dd626-107">The declaration of a model-declared function contains the following information:</span></span>  
  
- <span data-ttu-id="dd626-108">İşlevin adı.</span><span class="sxs-lookup"><span data-stu-id="dd626-108">The name of the function.</span></span> <span data-ttu-id="dd626-109">Istenir</span><span class="sxs-lookup"><span data-stu-id="dd626-109">(Required)</span></span>  
  
- <span data-ttu-id="dd626-110">Dönüş değerinin türü.</span><span class="sxs-lookup"><span data-stu-id="dd626-110">The type of the return value.</span></span> <span data-ttu-id="dd626-111">(İsteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="dd626-111">(Optional)</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="dd626-112">Dönüş değeri belirtilmemişse, dönüş türü void olur.</span><span class="sxs-lookup"><span data-stu-id="dd626-112">If no return value is specified, the return type is void.</span></span>  
  
- <span data-ttu-id="dd626-113">Parametre adı ve türü dahil olmak üzere parametre bilgileri.</span><span class="sxs-lookup"><span data-stu-id="dd626-113">Parameter information, including parameter name and type.</span></span> <span data-ttu-id="dd626-114">(İsteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="dd626-114">(Optional)</span></span>  
  
## <a name="example"></a><span data-ttu-id="dd626-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="dd626-115">Example</span></span>  

 <span data-ttu-id="dd626-116">[ADO.NET Entity Framework](./ef/index.md) kavramsal model tanımlamak için kavramsal şema tanım dili ([csdl](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) adlı bir etki ALANıNA özgü dil (DSL) kullanır.</span><span class="sxs-lookup"><span data-stu-id="dd626-116">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="dd626-117">CSDL 'de, model tarafından tanımlanan bir işlevin bir uygulamasý bir işlev içeri aktarmasıdır ( [FunctionImport öğesi](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#functionimport-element-csdl)kullanılarak).</span><span class="sxs-lookup"><span data-stu-id="dd626-117">In CSDL, one implementation of a model-declared function is a function import (using the [FunctionImport element](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#functionimport-element-csdl)).</span></span> <span data-ttu-id="dd626-118">Aşağıdaki CSDL, bir işlev içeri aktarma tanımına sahip bir varlık kapsayıcısını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="dd626-118">The following CSDL defines an entity container with a function import definition.</span></span> <span data-ttu-id="dd626-119">Dönüş türü belirtilmediği için işlevin dönüş türünün void olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="dd626-119">Note that the return type for the function is void since no return type is specified.</span></span>  
  
 [!code-xml[EDM_Example_Model#FunctionImport](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#functionimport)]  
  
## <a name="see-also"></a><span data-ttu-id="dd626-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dd626-120">See also</span></span>

- [<span data-ttu-id="dd626-121">Varlık Veri Modeli Temel Kavramları</span><span class="sxs-lookup"><span data-stu-id="dd626-121">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="dd626-122">Varlık Veri Modeli</span><span class="sxs-lookup"><span data-stu-id="dd626-122">Entity Data Model</span></span>](entity-data-model.md)
