---
title: model-declared function
ms.date: 03/30/2017
ms.assetid: aba87f13-5685-4f6b-ad14-918e8a7d5c2a
ms.openlocfilehash: c9abf9a3340cd22ab5d654588b1d22e10b5c05fa
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59130552"
---
# <a name="model-declared-function"></a><span data-ttu-id="86d8c-102">model-declared function</span><span class="sxs-lookup"><span data-stu-id="86d8c-102">model-declared function</span></span>
<span data-ttu-id="86d8c-103">A *model olarak bildirilen işlev* kavramsal modelde bildirildi, ancak bu kavramsal modelde tanımlı değil, bir işlevdir.</span><span class="sxs-lookup"><span data-stu-id="86d8c-103">A *model-declared function* is a function that is declared in a conceptual model, but is not defined in that conceptual model.</span></span> <span data-ttu-id="86d8c-104">İşlevi barındırma veya depolama ortamında tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="86d8c-104">The function might be defined in the hosting or storage environment.</span></span> <span data-ttu-id="86d8c-105">Örneğin, bir model olarak bildirilen işlev dolayısıyla kavramsal modelde sunucu tarafında işlevselliği kullanıma sunma, bir veritabanında tanımlı bir işlev eşleştirilmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="86d8c-105">For example, a model-declared function might be mapped to a function that is defined in a database, thus exposing server-side functionality in the conceptual model.</span></span>  
  
 <span data-ttu-id="86d8c-106">Model olarak bildirilen bir işlevin bildirimi, aşağıdaki bilgileri içerir:</span><span class="sxs-lookup"><span data-stu-id="86d8c-106">The declaration of a model-declared function contains the following information:</span></span>  
  
-   <span data-ttu-id="86d8c-107">İşlevin adı.</span><span class="sxs-lookup"><span data-stu-id="86d8c-107">The name of the function.</span></span> <span data-ttu-id="86d8c-108">(Gerekli)</span><span class="sxs-lookup"><span data-stu-id="86d8c-108">(Required)</span></span>  
  
-   <span data-ttu-id="86d8c-109">Dönüş değerinin türü.</span><span class="sxs-lookup"><span data-stu-id="86d8c-109">The type of the return value.</span></span> <span data-ttu-id="86d8c-110">(İsteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="86d8c-110">(Optional)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="86d8c-111">Dönüş değeri belirtilmişse, dönüş türü void alır.</span><span class="sxs-lookup"><span data-stu-id="86d8c-111">If no return value is specified, the return type is void.</span></span>  
  
-   <span data-ttu-id="86d8c-112">Parametre adı ve türü de dahil olmak üzere, parametre bilgileri.</span><span class="sxs-lookup"><span data-stu-id="86d8c-112">Parameter information, including parameter name and type.</span></span> <span data-ttu-id="86d8c-113">(İsteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="86d8c-113">(Optional)</span></span>  
  
## <a name="example"></a><span data-ttu-id="86d8c-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="86d8c-114">Example</span></span>  
 <span data-ttu-id="86d8c-115">[ADO.NET Entity Framework](./ef/index.md) kavramsal şema tanım dili olarak adlandırılan bir etki alanına özgü dil (DSL) kullanır ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) kavramsal modeller tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="86d8c-115">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="86d8c-116">CSDL bir model olarak bildirilen bir işlevi bir işlev içeri aktarma uygulamasıdır (kullanarak [Functionımport öğesi](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#functionimport-element-csdl)).</span><span class="sxs-lookup"><span data-stu-id="86d8c-116">In CSDL, one implementation of a model-declared function is a function import (using the [FunctionImport element](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#functionimport-element-csdl)).</span></span> <span data-ttu-id="86d8c-117">Aşağıdaki CSDL işlev tanımını içeri aktarma ile varlık kapsayıcısı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="86d8c-117">The following CSDL defines an entity container with a function import definition.</span></span> <span data-ttu-id="86d8c-118">Dönüş türü belirtildiği işlevi için dönüş türü void olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="86d8c-118">Note that the return type for the function is void since no return type is specified.</span></span>  
  
 [!code-xml[EDM_Example_Model#FunctionImport](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#functionimport)]  
  
## <a name="see-also"></a><span data-ttu-id="86d8c-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="86d8c-119">See also</span></span>

- [<span data-ttu-id="86d8c-120">Varlık Veri Modeli Temel Kavramları</span><span class="sxs-lookup"><span data-stu-id="86d8c-120">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [<span data-ttu-id="86d8c-121">Varlık Veri Modeli</span><span class="sxs-lookup"><span data-stu-id="86d8c-121">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
