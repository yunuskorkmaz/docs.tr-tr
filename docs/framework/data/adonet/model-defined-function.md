---
title: Model tanımlı işlevi
ms.date: 03/30/2017
ms.assetid: 8bb2edc8-e8e7-44c2-adc7-f44e11bda4f0
ms.openlocfilehash: 5c91c221735f3385370ec2fbb532d5b3c5dd2898
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32763780"
---
# <a name="model-defined-function"></a><span data-ttu-id="2faa7-102">Model tanımlı işlevi</span><span class="sxs-lookup"><span data-stu-id="2faa7-102">model-defined function</span></span>
<span data-ttu-id="2faa7-103">A *modeli tanımlı işlev* kavramsal modelde tanımlanan bir işlev değil.</span><span class="sxs-lookup"><span data-stu-id="2faa7-103">A *model-defined function* is a function that is defined in a conceptual model.</span></span> <span data-ttu-id="2faa7-104">Model tanımlı bir işlev gövdesi olarak ifade edilen [varlık SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md), işlevin bağımsız ifade veren kuralları veya veri kaynağında desteklenen diller.</span><span class="sxs-lookup"><span data-stu-id="2faa7-104">The body of a model-defined function is expressed in [Entity SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md), which allows for the function to be expressed independently of rules or languages supported in the data source.</span></span>  
  
 <span data-ttu-id="2faa7-105">Model tanımlı bir işlev için bir tanım aşağıdaki bilgileri içerir:</span><span class="sxs-lookup"><span data-stu-id="2faa7-105">A definition for a model-defined function contains the following information:</span></span>  
  
-   <span data-ttu-id="2faa7-106">İşlev adı.</span><span class="sxs-lookup"><span data-stu-id="2faa7-106">A function name.</span></span> <span data-ttu-id="2faa7-107">(Gerekli)</span><span class="sxs-lookup"><span data-stu-id="2faa7-107">(Required)</span></span>  
  
-   <span data-ttu-id="2faa7-108">Döndürülen değerin türü.</span><span class="sxs-lookup"><span data-stu-id="2faa7-108">The type of the return value.</span></span> <span data-ttu-id="2faa7-109">(İsteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="2faa7-109">(Optional)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2faa7-110">Dönüş türü belirtilmişse, döndürülen değer geçersizdir.</span><span class="sxs-lookup"><span data-stu-id="2faa7-110">If no return type is specified, the return value is void.</span></span>  
  
-   <span data-ttu-id="2faa7-111">Parametre bilgileri.</span><span class="sxs-lookup"><span data-stu-id="2faa7-111">Parameter information.</span></span> <span data-ttu-id="2faa7-112">(İsteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="2faa7-112">(Optional)</span></span>  
  
-   <span data-ttu-id="2faa7-113">Bir [varlık SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md) işlevinin gövdesini tanımlayan ifade.</span><span class="sxs-lookup"><span data-stu-id="2faa7-113">An [Entity SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md) expression that defines the body of the function.</span></span>  
  
 <span data-ttu-id="2faa7-114">Model tanımlı işlevler çıkış parametreleri desteklemez unutmayın.</span><span class="sxs-lookup"><span data-stu-id="2faa7-114">Note that model-defined functions do not support output parameters.</span></span> <span data-ttu-id="2faa7-115">Böylece model tanımlı işlevler birleştirilebilen bu kısıtlama yerdir.</span><span class="sxs-lookup"><span data-stu-id="2faa7-115">This restriction is in place so that model-defined functions can be composed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2faa7-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="2faa7-116">Example</span></span>  
 <span data-ttu-id="2faa7-117">Aşağıdaki diyagram üç varlık türleriyle kavramsal model gösterir: `Book`, `Publisher`, ve `Author`.</span><span class="sxs-lookup"><span data-stu-id="2faa7-117">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span>  
  
 <span data-ttu-id="2faa7-118">![Yayımlanma tarihi ile model](../../../../docs/framework/data/adonet/media/modelwithpublisheddate.gif "ModelWithPublishedDate")</span><span class="sxs-lookup"><span data-stu-id="2faa7-118">![Model With Published Date](../../../../docs/framework/data/adonet/media/modelwithpublisheddate.gif "ModelWithPublishedDate")</span></span>  
  
 <span data-ttu-id="2faa7-119">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) kavramsal şema tanım dili adlı bir etki alanına özgü dil (DSL) kullanır ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) kavramsal modeller tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="2faa7-119">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="2faa7-120">Aşağıdaki CSDL örneği itibaren yıl numaraları döndürür kavramsal modelde bir işlevi tanımlayan bir `Book` (Yukarıdaki diyagramda) yayımlandı.</span><span class="sxs-lookup"><span data-stu-id="2faa7-120">The following CSDL defines a function in the conceptual model that returns the numbers of years since an instance of a `Book` (in the diagram above) was published.</span></span>  
  
 [!code-xml[EDM_Example_Model#ModelDefinedFunction](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#modeldefinedfunction)]  
  
## <a name="see-also"></a><span data-ttu-id="2faa7-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2faa7-121">See Also</span></span>  
 [<span data-ttu-id="2faa7-122">Varlık Veri Modeli Temel Kavramları</span><span class="sxs-lookup"><span data-stu-id="2faa7-122">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="2faa7-123">Varlık Veri Modeli</span><span class="sxs-lookup"><span data-stu-id="2faa7-123">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)  
 [<span data-ttu-id="2faa7-124">Varlık Veri Modeli: Basit Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="2faa7-124">Entity Data Model: Primitive Data Types</span></span>](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md)
