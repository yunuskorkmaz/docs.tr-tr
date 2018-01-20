---
title: "Model bildirilen işlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aba87f13-5685-4f6b-ad14-918e8a7d5c2a
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 37c6b04fbea69f62aaf7bc148ee04ace5a5a349c
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="model-declared-function"></a><span data-ttu-id="19740-102">Model bildirilen işlevi</span><span class="sxs-lookup"><span data-stu-id="19740-102">model-declared function</span></span>
<span data-ttu-id="19740-103">A *modeli bildirilen işlevi* kavramsal modelde bildirildi, ancak bu kavramsal modelde tanımlı değil bir işlevdir.</span><span class="sxs-lookup"><span data-stu-id="19740-103">A *model-declared function* is a function that is declared in a conceptual model, but is not defined in that conceptual model.</span></span> <span data-ttu-id="19740-104">İşlev barındırma veya depolama ortamında tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="19740-104">The function might be defined in the hosting or storage environment.</span></span> <span data-ttu-id="19740-105">Örneğin, bir model bildirilen işlevi böylece kavramsal modelde sunucu tarafı işlevselliği kullanıma sunan bir veritabanında tanımlı bir işlev eşleştirilmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="19740-105">For example, a model-declared function might be mapped to a function that is defined in a database, thus exposing server-side functionality in the conceptual model.</span></span>  
  
 <span data-ttu-id="19740-106">Model bildirilen bir işlevin bildirimi aşağıdaki bilgileri içerir:</span><span class="sxs-lookup"><span data-stu-id="19740-106">The declaration of a model-declared function contains the following information:</span></span>  
  
-   <span data-ttu-id="19740-107">İşlevin adı.</span><span class="sxs-lookup"><span data-stu-id="19740-107">The name of the function.</span></span> <span data-ttu-id="19740-108">(Gerekli)</span><span class="sxs-lookup"><span data-stu-id="19740-108">(Required)</span></span>  
  
-   <span data-ttu-id="19740-109">Döndürülen değerin türü.</span><span class="sxs-lookup"><span data-stu-id="19740-109">The type of the return value.</span></span> <span data-ttu-id="19740-110">(İsteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="19740-110">(Optional)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="19740-111">Hiçbir değer döndürmeyen belirtilmişse, dönüş türü void alır.</span><span class="sxs-lookup"><span data-stu-id="19740-111">If no return value is specified, the return type is void.</span></span>  
  
-   <span data-ttu-id="19740-112">Parametre adı ve türü dahil olmak üzere parametre bilgileri.</span><span class="sxs-lookup"><span data-stu-id="19740-112">Parameter information, including parameter name and type.</span></span> <span data-ttu-id="19740-113">(İsteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="19740-113">(Optional)</span></span>  
  
## <a name="example"></a><span data-ttu-id="19740-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="19740-114">Example</span></span>  
 <span data-ttu-id="19740-115">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) kavramsal şema tanım dili adlı bir etki alanına özgü dil (DSL) kullanır ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) kavramsal modeller tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="19740-115">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="19740-116">CSDL model bildirilen işlevi bir uygulamasıdır bir [işlev içeri aktarması](http://msdn.microsoft.com/library/125704ae-56c7-4233-80b7-389a10f3a65d).</span><span class="sxs-lookup"><span data-stu-id="19740-116">In CSDL, one implementation of a model-declared function is a [function import](http://msdn.microsoft.com/library/125704ae-56c7-4233-80b7-389a10f3a65d).</span></span> <span data-ttu-id="19740-117">Aşağıdaki CSDL bir işlev içeri aktarma tanımını içeren bir varlık kapsayıcı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="19740-117">The following CSDL defines an entity container with a function import definition.</span></span> <span data-ttu-id="19740-118">Dönüş türü belirtilen beri işlevi için dönüş türü void olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="19740-118">Note that the return type for the function is void since no return type is specified.</span></span>  
  
 [!code-xml[EDM_Example_Model#FunctionImport](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#functionimport)]  
  
## <a name="see-also"></a><span data-ttu-id="19740-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="19740-119">See Also</span></span>  
 [<span data-ttu-id="19740-120">Varlık Veri Modeli Temel Kavramları</span><span class="sxs-lookup"><span data-stu-id="19740-120">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="19740-121">Varlık Veri Modeli</span><span class="sxs-lookup"><span data-stu-id="19740-121">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
