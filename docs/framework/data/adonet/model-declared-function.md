---
title: model olarak bildirilen işlev
ms.date: 03/30/2017
ms.assetid: aba87f13-5685-4f6b-ad14-918e8a7d5c2a
ms.openlocfilehash: f92bdfedaefca7182b5de72abae9852965d83ff7
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43511521"
---
# <a name="model-declared-function"></a><span data-ttu-id="e671e-102">model olarak bildirilen işlev</span><span class="sxs-lookup"><span data-stu-id="e671e-102">model-declared function</span></span>
<span data-ttu-id="e671e-103">A *model olarak bildirilen işlev* kavramsal modelde bildirildi, ancak bu kavramsal modelde tanımlı değil, bir işlevdir.</span><span class="sxs-lookup"><span data-stu-id="e671e-103">A *model-declared function* is a function that is declared in a conceptual model, but is not defined in that conceptual model.</span></span> <span data-ttu-id="e671e-104">İşlevi barındırma veya depolama ortamında tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="e671e-104">The function might be defined in the hosting or storage environment.</span></span> <span data-ttu-id="e671e-105">Örneğin, bir model olarak bildirilen işlev dolayısıyla kavramsal modelde sunucu tarafında işlevselliği kullanıma sunma, bir veritabanında tanımlı bir işlev eşleştirilmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="e671e-105">For example, a model-declared function might be mapped to a function that is defined in a database, thus exposing server-side functionality in the conceptual model.</span></span>  
  
 <span data-ttu-id="e671e-106">Model olarak bildirilen bir işlevin bildirimi, aşağıdaki bilgileri içerir:</span><span class="sxs-lookup"><span data-stu-id="e671e-106">The declaration of a model-declared function contains the following information:</span></span>  
  
-   <span data-ttu-id="e671e-107">İşlevin adı.</span><span class="sxs-lookup"><span data-stu-id="e671e-107">The name of the function.</span></span> <span data-ttu-id="e671e-108">(Gerekli)</span><span class="sxs-lookup"><span data-stu-id="e671e-108">(Required)</span></span>  
  
-   <span data-ttu-id="e671e-109">Dönüş değerinin türü.</span><span class="sxs-lookup"><span data-stu-id="e671e-109">The type of the return value.</span></span> <span data-ttu-id="e671e-110">(İsteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="e671e-110">(Optional)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e671e-111">Dönüş değeri belirtilmişse, dönüş türü void alır.</span><span class="sxs-lookup"><span data-stu-id="e671e-111">If no return value is specified, the return type is void.</span></span>  
  
-   <span data-ttu-id="e671e-112">Parametre adı ve türü de dahil olmak üzere, parametre bilgileri.</span><span class="sxs-lookup"><span data-stu-id="e671e-112">Parameter information, including parameter name and type.</span></span> <span data-ttu-id="e671e-113">(İsteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="e671e-113">(Optional)</span></span>  
  
## <a name="example"></a><span data-ttu-id="e671e-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="e671e-114">Example</span></span>  
 <span data-ttu-id="e671e-115">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) kavramsal şema tanım dili olarak adlandırılan bir etki alanına özgü dil (DSL) kullanır ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) kavramsal modeller tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="e671e-115">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="e671e-116">CSDL model olarak bildirilen bir işlevi bir uygulamasıdır bir [işlev içeri aktarma](https://msdn.microsoft.com/library/125704ae-56c7-4233-80b7-389a10f3a65d).</span><span class="sxs-lookup"><span data-stu-id="e671e-116">In CSDL, one implementation of a model-declared function is a [function import](https://msdn.microsoft.com/library/125704ae-56c7-4233-80b7-389a10f3a65d).</span></span> <span data-ttu-id="e671e-117">Aşağıdaki CSDL işlev tanımını içeri aktarma ile varlık kapsayıcısı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e671e-117">The following CSDL defines an entity container with a function import definition.</span></span> <span data-ttu-id="e671e-118">Dönüş türü belirtildiği işlevi için dönüş türü void olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="e671e-118">Note that the return type for the function is void since no return type is specified.</span></span>  
  
 [!code-xml[EDM_Example_Model#FunctionImport](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#functionimport)]  
  
## <a name="see-also"></a><span data-ttu-id="e671e-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e671e-119">See Also</span></span>  
 [<span data-ttu-id="e671e-120">Varlık Veri Modeli Temel Kavramları</span><span class="sxs-lookup"><span data-stu-id="e671e-120">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="e671e-121">Varlık Veri Modeli</span><span class="sxs-lookup"><span data-stu-id="e671e-121">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
