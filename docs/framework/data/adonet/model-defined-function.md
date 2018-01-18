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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: e1c9d438840a0b9c15597177ca4e6d870d526756
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="model-defined-function"></a><span data-ttu-id="b2272-102">Model tanımlı işlevi</span><span class="sxs-lookup"><span data-stu-id="b2272-102">model-defined function</span></span>
<span data-ttu-id="b2272-103">A *modeli tanımlı işlev* kavramsal modelde tanımlanan bir işlev değil.</span><span class="sxs-lookup"><span data-stu-id="b2272-103">A *model-defined function* is a function that is defined in a conceptual model.</span></span> <span data-ttu-id="b2272-104">Model tanımlı bir işlev gövdesi olarak ifade edilen [varlık SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md), işlevin bağımsız ifade veren kuralları veya veri kaynağında desteklenen diller.</span><span class="sxs-lookup"><span data-stu-id="b2272-104">The body of a model-defined function is expressed in [Entity SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md), which allows for the function to be expressed independently of rules or languages supported in the data source.</span></span>  
  
 <span data-ttu-id="b2272-105">Model tanımlı bir işlev için bir tanım aşağıdaki bilgileri içerir:</span><span class="sxs-lookup"><span data-stu-id="b2272-105">A definition for a model-defined function contains the following information:</span></span>  
  
-   <span data-ttu-id="b2272-106">İşlev adı.</span><span class="sxs-lookup"><span data-stu-id="b2272-106">A function name.</span></span> <span data-ttu-id="b2272-107">(Gerekli)</span><span class="sxs-lookup"><span data-stu-id="b2272-107">(Required)</span></span>  
  
-   <span data-ttu-id="b2272-108">Döndürülen değerin türü.</span><span class="sxs-lookup"><span data-stu-id="b2272-108">The type of the return value.</span></span> <span data-ttu-id="b2272-109">(İsteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="b2272-109">(Optional)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b2272-110">Dönüş türü belirtilmişse, döndürülen değer geçersizdir.</span><span class="sxs-lookup"><span data-stu-id="b2272-110">If no return type is specified, the return value is void.</span></span>  
  
-   <span data-ttu-id="b2272-111">Parametre bilgileri.</span><span class="sxs-lookup"><span data-stu-id="b2272-111">Parameter information.</span></span> <span data-ttu-id="b2272-112">(İsteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="b2272-112">(Optional)</span></span>  
  
-   <span data-ttu-id="b2272-113">Bir [varlık SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md) işlevinin gövdesini tanımlayan ifade.</span><span class="sxs-lookup"><span data-stu-id="b2272-113">An [Entity SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md) expression that defines the body of the function.</span></span>  
  
 <span data-ttu-id="b2272-114">Model tanımlı işlevler çıkış parametreleri desteklemez unutmayın.</span><span class="sxs-lookup"><span data-stu-id="b2272-114">Note that model-defined functions do not support output parameters.</span></span> <span data-ttu-id="b2272-115">Böylece model tanımlı işlevler birleştirilebilen bu kısıtlama yerdir.</span><span class="sxs-lookup"><span data-stu-id="b2272-115">This restriction is in place so that model-defined functions can be composed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b2272-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="b2272-116">Example</span></span>  
 <span data-ttu-id="b2272-117">Aşağıdaki diyagram üç varlık türleriyle kavramsal model gösterir: `Book`, `Publisher`, ve `Author`.</span><span class="sxs-lookup"><span data-stu-id="b2272-117">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span>  
  
 <span data-ttu-id="b2272-118">![Yayımlanma tarihi ile model](../../../../docs/framework/data/adonet/media/modelwithpublisheddate.gif "ModelWithPublishedDate")</span><span class="sxs-lookup"><span data-stu-id="b2272-118">![Model With Published Date](../../../../docs/framework/data/adonet/media/modelwithpublisheddate.gif "ModelWithPublishedDate")</span></span>  
  
 <span data-ttu-id="b2272-119">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) kavramsal şema tanım dili adlı bir etki alanına özgü dil (DSL) kullanır ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) kavramsal modeller tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="b2272-119">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="b2272-120">Aşağıdaki CSDL örneği itibaren yıl numaraları döndürür kavramsal modelde bir işlevi tanımlayan bir `Book` (Yukarıdaki diyagramda) yayımlandı.</span><span class="sxs-lookup"><span data-stu-id="b2272-120">The following CSDL defines a function in the conceptual model that returns the numbers of years since an instance of a `Book` (in the diagram above) was published.</span></span>  
  
 [!code-xml[EDM_Example_Model#ModelDefinedFunction](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#modeldefinedfunction)]  
  
## <a name="see-also"></a><span data-ttu-id="b2272-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b2272-121">See Also</span></span>  
 [<span data-ttu-id="b2272-122">Varlık Veri Modeli Temel Kavramları</span><span class="sxs-lookup"><span data-stu-id="b2272-122">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="b2272-123">Varlık Veri Modeli</span><span class="sxs-lookup"><span data-stu-id="b2272-123">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)  
 [<span data-ttu-id="b2272-124">Varlık Veri Modeli: Basit Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="b2272-124">Entity Data Model: Primitive Data Types</span></span>](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md)
