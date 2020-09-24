---
title: model-declared function
ms.date: 03/30/2017
ms.assetid: aba87f13-5685-4f6b-ad14-918e8a7d5c2a
ms.openlocfilehash: fb30dd86c29d6a7fff6f2c71d5fd892326e1fda4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91147859"
---
# <a name="model-declared-function"></a><span data-ttu-id="f5c14-102">model-declared function</span><span class="sxs-lookup"><span data-stu-id="f5c14-102">model-declared function</span></span>

<span data-ttu-id="f5c14-103">Model olarak tanımlanmış bir *işlev* , kavramsal modelde belirtilen ancak bu kavramsal modelde tanımlı olmayan bir işlevdir.</span><span class="sxs-lookup"><span data-stu-id="f5c14-103">A *model-declared function* is a function that is declared in a conceptual model, but is not defined in that conceptual model.</span></span> <span data-ttu-id="f5c14-104">İşlev barındırma veya depolama ortamında tanımlanmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="f5c14-104">The function might be defined in the hosting or storage environment.</span></span> <span data-ttu-id="f5c14-105">Örneğin, model tarafından tanımlanan bir işlev, veritabanında tanımlanmış bir işlevle eşleştirilebilir ve bu nedenle kavramsal modelde sunucu tarafı işlevselliği ortaya çıkabilir.</span><span class="sxs-lookup"><span data-stu-id="f5c14-105">For example, a model-declared function might be mapped to a function that is defined in a database, thus exposing server-side functionality in the conceptual model.</span></span>  
  
 <span data-ttu-id="f5c14-106">Model tarafından tanımlanan bir işlevin bildirimi, aşağıdaki bilgileri içerir:</span><span class="sxs-lookup"><span data-stu-id="f5c14-106">The declaration of a model-declared function contains the following information:</span></span>  
  
- <span data-ttu-id="f5c14-107">İşlevin adı.</span><span class="sxs-lookup"><span data-stu-id="f5c14-107">The name of the function.</span></span> <span data-ttu-id="f5c14-108">Istenir</span><span class="sxs-lookup"><span data-stu-id="f5c14-108">(Required)</span></span>  
  
- <span data-ttu-id="f5c14-109">Dönüş değerinin türü.</span><span class="sxs-lookup"><span data-stu-id="f5c14-109">The type of the return value.</span></span> <span data-ttu-id="f5c14-110">(İsteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="f5c14-110">(Optional)</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="f5c14-111">Dönüş değeri belirtilmemişse, dönüş türü void olur.</span><span class="sxs-lookup"><span data-stu-id="f5c14-111">If no return value is specified, the return type is void.</span></span>  
  
- <span data-ttu-id="f5c14-112">Parametre adı ve türü dahil olmak üzere parametre bilgileri.</span><span class="sxs-lookup"><span data-stu-id="f5c14-112">Parameter information, including parameter name and type.</span></span> <span data-ttu-id="f5c14-113">(İsteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="f5c14-113">(Optional)</span></span>  
  
## <a name="example"></a><span data-ttu-id="f5c14-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="f5c14-114">Example</span></span>  

 <span data-ttu-id="f5c14-115">[ADO.NET Entity Framework](./ef/index.md) kavramsal model tanımlamak için kavramsal şema tanım dili ([csdl](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) adlı bir etki ALANıNA özgü dil (DSL) kullanır.</span><span class="sxs-lookup"><span data-stu-id="f5c14-115">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="f5c14-116">CSDL 'de, model tarafından tanımlanan bir işlevin bir uygulamasý bir işlev içeri aktarmasıdır ( [FunctionImport öğesi](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#functionimport-element-csdl)kullanılarak).</span><span class="sxs-lookup"><span data-stu-id="f5c14-116">In CSDL, one implementation of a model-declared function is a function import (using the [FunctionImport element](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#functionimport-element-csdl)).</span></span> <span data-ttu-id="f5c14-117">Aşağıdaki CSDL, bir işlev içeri aktarma tanımına sahip bir varlık kapsayıcısını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f5c14-117">The following CSDL defines an entity container with a function import definition.</span></span> <span data-ttu-id="f5c14-118">Dönüş türü belirtilmediği için işlevin dönüş türünün void olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="f5c14-118">Note that the return type for the function is void since no return type is specified.</span></span>  
  
 [!code-xml[EDM_Example_Model#FunctionImport](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#functionimport)]  
  
## <a name="see-also"></a><span data-ttu-id="f5c14-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f5c14-119">See also</span></span>

- [<span data-ttu-id="f5c14-120">Varlık Veri Modeli Temel Kavramları</span><span class="sxs-lookup"><span data-stu-id="f5c14-120">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="f5c14-121">Varlık Veri Modeli</span><span class="sxs-lookup"><span data-stu-id="f5c14-121">Entity Data Model</span></span>](entity-data-model.md)
