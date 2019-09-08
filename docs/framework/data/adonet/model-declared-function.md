---
title: model-declared function
ms.date: 03/30/2017
ms.assetid: aba87f13-5685-4f6b-ad14-918e8a7d5c2a
ms.openlocfilehash: cb2fca52604bd57f25469f5621c292a27638c76f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794803"
---
# <a name="model-declared-function"></a><span data-ttu-id="9a27d-102">model-declared function</span><span class="sxs-lookup"><span data-stu-id="9a27d-102">model-declared function</span></span>
<span data-ttu-id="9a27d-103">Model olarak tanımlanmış bir *işlev* , kavramsal modelde belirtilen ancak bu kavramsal modelde tanımlı olmayan bir işlevdir.</span><span class="sxs-lookup"><span data-stu-id="9a27d-103">A *model-declared function* is a function that is declared in a conceptual model, but is not defined in that conceptual model.</span></span> <span data-ttu-id="9a27d-104">İşlev barındırma veya depolama ortamında tanımlanmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="9a27d-104">The function might be defined in the hosting or storage environment.</span></span> <span data-ttu-id="9a27d-105">Örneğin, model tarafından tanımlanan bir işlev, veritabanında tanımlanmış bir işlevle eşleştirilebilir ve bu nedenle kavramsal modelde sunucu tarafı işlevselliği ortaya çıkabilir.</span><span class="sxs-lookup"><span data-stu-id="9a27d-105">For example, a model-declared function might be mapped to a function that is defined in a database, thus exposing server-side functionality in the conceptual model.</span></span>  
  
 <span data-ttu-id="9a27d-106">Model tarafından tanımlanan bir işlevin bildirimi, aşağıdaki bilgileri içerir:</span><span class="sxs-lookup"><span data-stu-id="9a27d-106">The declaration of a model-declared function contains the following information:</span></span>  
  
- <span data-ttu-id="9a27d-107">İşlevin adı.</span><span class="sxs-lookup"><span data-stu-id="9a27d-107">The name of the function.</span></span> <span data-ttu-id="9a27d-108">Istenir</span><span class="sxs-lookup"><span data-stu-id="9a27d-108">(Required)</span></span>  
  
- <span data-ttu-id="9a27d-109">Dönüş değerinin türü.</span><span class="sxs-lookup"><span data-stu-id="9a27d-109">The type of the return value.</span></span> <span data-ttu-id="9a27d-110">(İsteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="9a27d-110">(Optional)</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="9a27d-111">Dönüş değeri belirtilmemişse, dönüş türü void olur.</span><span class="sxs-lookup"><span data-stu-id="9a27d-111">If no return value is specified, the return type is void.</span></span>  
  
- <span data-ttu-id="9a27d-112">Parametre adı ve türü dahil olmak üzere parametre bilgileri.</span><span class="sxs-lookup"><span data-stu-id="9a27d-112">Parameter information, including parameter name and type.</span></span> <span data-ttu-id="9a27d-113">(İsteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="9a27d-113">(Optional)</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a27d-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="9a27d-114">Example</span></span>  
 <span data-ttu-id="9a27d-115">[ADO.NET Entity Framework](./ef/index.md) kavramsal model tanımlamak için kavramsal şema tanım dili ([csdl](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) adlı bir etki ALANıNA özgü dil (DSL) kullanır.</span><span class="sxs-lookup"><span data-stu-id="9a27d-115">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="9a27d-116">CSDL 'de, model tarafından tanımlanan bir işlevin bir uygulamasý bir işlev içeri aktarmasıdır ( [FunctionImport öğesi](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#functionimport-element-csdl)kullanılarak).</span><span class="sxs-lookup"><span data-stu-id="9a27d-116">In CSDL, one implementation of a model-declared function is a function import (using the [FunctionImport element](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#functionimport-element-csdl)).</span></span> <span data-ttu-id="9a27d-117">Aşağıdaki CSDL, bir işlev içeri aktarma tanımına sahip bir varlık kapsayıcısını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9a27d-117">The following CSDL defines an entity container with a function import definition.</span></span> <span data-ttu-id="9a27d-118">Dönüş türü belirtilmediği için işlevin dönüş türünün void olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="9a27d-118">Note that the return type for the function is void since no return type is specified.</span></span>  
  
 [!code-xml[EDM_Example_Model#FunctionImport](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#functionimport)]  
  
## <a name="see-also"></a><span data-ttu-id="9a27d-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9a27d-119">See also</span></span>

- [<span data-ttu-id="9a27d-120">Varlık Veri Modeli Temel Kavramları</span><span class="sxs-lookup"><span data-stu-id="9a27d-120">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="9a27d-121">Varlık Veri Modeli</span><span class="sxs-lookup"><span data-stu-id="9a27d-121">Entity Data Model</span></span>](entity-data-model.md)
