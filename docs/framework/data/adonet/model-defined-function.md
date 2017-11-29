---
title: "Model tanımlı işlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8bb2edc8-e8e7-44c2-adc7-f44e11bda4f0
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 8e311d6e9c67a30636bdeaea7982057605678684
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="model-defined-function"></a><span data-ttu-id="f1bd6-102">Model tanımlı işlevi</span><span class="sxs-lookup"><span data-stu-id="f1bd6-102">model-defined function</span></span>
<span data-ttu-id="f1bd6-103">A *modeli tanımlı işlev* kavramsal modelde tanımlanan bir işlev değil.</span><span class="sxs-lookup"><span data-stu-id="f1bd6-103">A *model-defined function* is a function that is defined in a conceptual model.</span></span> <span data-ttu-id="f1bd6-104">Model tanımlı bir işlev gövdesi olarak ifade edilen [varlık SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md), işlevin bağımsız ifade veren kuralları veya veri kaynağında desteklenen diller.</span><span class="sxs-lookup"><span data-stu-id="f1bd6-104">The body of a model-defined function is expressed in [Entity SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md), which allows for the function to be expressed independently of rules or languages supported in the data source.</span></span>  
  
 <span data-ttu-id="f1bd6-105">Model tanımlı bir işlev için bir tanım aşağıdaki bilgileri içerir:</span><span class="sxs-lookup"><span data-stu-id="f1bd6-105">A definition for a model-defined function contains the following information:</span></span>  
  
-   <span data-ttu-id="f1bd6-106">İşlev adı.</span><span class="sxs-lookup"><span data-stu-id="f1bd6-106">A function name.</span></span> <span data-ttu-id="f1bd6-107">(Gerekli)</span><span class="sxs-lookup"><span data-stu-id="f1bd6-107">(Required)</span></span>  
  
-   <span data-ttu-id="f1bd6-108">Döndürülen değerin türü.</span><span class="sxs-lookup"><span data-stu-id="f1bd6-108">The type of the return value.</span></span> <span data-ttu-id="f1bd6-109">(İsteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="f1bd6-109">(Optional)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f1bd6-110">Dönüş türü belirtilmişse, döndürülen değer geçersizdir.</span><span class="sxs-lookup"><span data-stu-id="f1bd6-110">If no return type is specified, the return value is void.</span></span>  
  
-   <span data-ttu-id="f1bd6-111">Parametre bilgileri.</span><span class="sxs-lookup"><span data-stu-id="f1bd6-111">Parameter information.</span></span> <span data-ttu-id="f1bd6-112">(İsteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="f1bd6-112">(Optional)</span></span>  
  
-   <span data-ttu-id="f1bd6-113">Bir [varlık SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md) işlevinin gövdesini tanımlayan ifade.</span><span class="sxs-lookup"><span data-stu-id="f1bd6-113">An [Entity SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md) expression that defines the body of the function.</span></span>  
  
 <span data-ttu-id="f1bd6-114">Model tanımlı işlevler çıkış parametreleri desteklemez unutmayın.</span><span class="sxs-lookup"><span data-stu-id="f1bd6-114">Note that model-defined functions do not support output parameters.</span></span> <span data-ttu-id="f1bd6-115">Böylece model tanımlı işlevler birleştirilebilen bu kısıtlama yerdir.</span><span class="sxs-lookup"><span data-stu-id="f1bd6-115">This restriction is in place so that model-defined functions can be composed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f1bd6-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="f1bd6-116">Example</span></span>  
 <span data-ttu-id="f1bd6-117">Aşağıdaki diyagram üç varlık türleriyle kavramsal model gösterir: `Book`, `Publisher`, ve `Author`.</span><span class="sxs-lookup"><span data-stu-id="f1bd6-117">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span>  
  
 <span data-ttu-id="f1bd6-118">![Yayımlanma tarihi ile model](../../../../docs/framework/data/adonet/media/modelwithpublisheddate.gif "ModelWithPublishedDate")</span><span class="sxs-lookup"><span data-stu-id="f1bd6-118">![Model With Published Date](../../../../docs/framework/data/adonet/media/modelwithpublisheddate.gif "ModelWithPublishedDate")</span></span>  
  
 <span data-ttu-id="f1bd6-119">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) kavramsal şema tanım dili adlı bir etki alanına özgü dil (DSL) kullanır ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) kavramsal modeller tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="f1bd6-119">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="f1bd6-120">Aşağıdaki CSDL örneği itibaren yıl numaraları döndürür kavramsal modelde bir işlevi tanımlayan bir `Book` (Yukarıdaki diyagramda) yayımlandı.</span><span class="sxs-lookup"><span data-stu-id="f1bd6-120">The following CSDL defines a function in the conceptual model that returns the numbers of years since an instance of a `Book` (in the diagram above) was published.</span></span>  
  
 [!code-xml[EDM_Example_Model#ModelDefinedFunction](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#modeldefinedfunction)]  
  
## <a name="see-also"></a><span data-ttu-id="f1bd6-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f1bd6-121">See Also</span></span>  
 [<span data-ttu-id="f1bd6-122">Varlık veri modeli temel kavramları</span><span class="sxs-lookup"><span data-stu-id="f1bd6-122">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="f1bd6-123">Varlık veri modeli</span><span class="sxs-lookup"><span data-stu-id="f1bd6-123">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)  
 [<span data-ttu-id="f1bd6-124">Varlık veri modeli: Basit veri türleri</span><span class="sxs-lookup"><span data-stu-id="f1bd6-124">Entity Data Model: Primitive Data Types</span></span>](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md)
