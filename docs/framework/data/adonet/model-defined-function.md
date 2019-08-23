---
title: model-defined function
ms.date: 03/30/2017
ms.assetid: 8bb2edc8-e8e7-44c2-adc7-f44e11bda4f0
ms.openlocfilehash: 05a44e86a118b649490cde849c8ca2c2bb0d2f15
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934517"
---
# <a name="model-defined-function"></a><span data-ttu-id="8e784-102">model-defined function</span><span class="sxs-lookup"><span data-stu-id="8e784-102">model-defined function</span></span>
<span data-ttu-id="8e784-103">*Model tanımlı bir işlev* , kavramsal modelde tanımlanan bir işlevdir.</span><span class="sxs-lookup"><span data-stu-id="8e784-103">A *model-defined function* is a function that is defined in a conceptual model.</span></span> <span data-ttu-id="8e784-104">Model tanımlı bir işlevin gövdesi [Entity SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)ifade edilir ve bu, işlevin veri kaynağında desteklenen kurallardan veya dillerden bağımsız olarak ifade etmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="8e784-104">The body of a model-defined function is expressed in [Entity SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md), which allows for the function to be expressed independently of rules or languages supported in the data source.</span></span>  
  
 <span data-ttu-id="8e784-105">Model tanımlı bir işlev için bir tanım aşağıdaki bilgileri içerir:</span><span class="sxs-lookup"><span data-stu-id="8e784-105">A definition for a model-defined function contains the following information:</span></span>  
  
- <span data-ttu-id="8e784-106">Bir işlev adı.</span><span class="sxs-lookup"><span data-stu-id="8e784-106">A function name.</span></span> <span data-ttu-id="8e784-107">Istenir</span><span class="sxs-lookup"><span data-stu-id="8e784-107">(Required)</span></span>  
  
- <span data-ttu-id="8e784-108">Dönüş değerinin türü.</span><span class="sxs-lookup"><span data-stu-id="8e784-108">The type of the return value.</span></span> <span data-ttu-id="8e784-109">(İsteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="8e784-109">(Optional)</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="8e784-110">Dönüş türü belirtilmemişse, dönüş değeri void olur.</span><span class="sxs-lookup"><span data-stu-id="8e784-110">If no return type is specified, the return value is void.</span></span>  
  
- <span data-ttu-id="8e784-111">Parametre bilgileri.</span><span class="sxs-lookup"><span data-stu-id="8e784-111">Parameter information.</span></span> <span data-ttu-id="8e784-112">(İsteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="8e784-112">(Optional)</span></span>  
  
- <span data-ttu-id="8e784-113">İşlevin gövdesini tanımlayan bir [Entity SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md) ifadesi.</span><span class="sxs-lookup"><span data-stu-id="8e784-113">An [Entity SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md) expression that defines the body of the function.</span></span>  
  
 <span data-ttu-id="8e784-114">Model tanımlı işlevlerin çıkış parametrelerini desteklemediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="8e784-114">Note that model-defined functions do not support output parameters.</span></span> <span data-ttu-id="8e784-115">Bu kısıtlama, model tanımlı işlevlerin birleştirilebilmesi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8e784-115">This restriction is in place so that model-defined functions can be composed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8e784-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="8e784-116">Example</span></span>  
 <span data-ttu-id="8e784-117">Aşağıdaki diyagramda üç varlık türü olan kavramsal model gösterilmektedir: `Book`, `Publisher`, ve `Author`.</span><span class="sxs-lookup"><span data-stu-id="8e784-117">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span>  
  
 ![Yayımlanma tarihi olan bir modeli gösteren ekran görüntüsü.](./media/model-defined-function/model-published-date-three-entity-types.gif)  
  
 <span data-ttu-id="8e784-119">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) kavramsal model tanımlamak için kavramsal şema tanım dili ([csdl](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) adlı bir etki ALANıNA özgü dil (DSL) kullanır.</span><span class="sxs-lookup"><span data-stu-id="8e784-119">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="8e784-120">Aşağıdaki csdl, bir (Yukarıdaki diyagramda) bir `Book` örneği yayımlandığı için yıl sayılarını döndüren kavramsal modelde bir işlevi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8e784-120">The following CSDL defines a function in the conceptual model that returns the numbers of years since an instance of a `Book` (in the diagram above) was published.</span></span>  
  
 [!code-xml[EDM_Example_Model#ModelDefinedFunction](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#modeldefinedfunction)]  
  
## <a name="see-also"></a><span data-ttu-id="8e784-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8e784-121">See also</span></span>

- [<span data-ttu-id="8e784-122">Varlık Veri Modeli Temel Kavramları</span><span class="sxs-lookup"><span data-stu-id="8e784-122">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [<span data-ttu-id="8e784-123">Varlık Veri Modeli</span><span class="sxs-lookup"><span data-stu-id="8e784-123">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
- [<span data-ttu-id="8e784-124">Varlık Veri Modeli: İlkel veri türleri</span><span class="sxs-lookup"><span data-stu-id="8e784-124">Entity Data Model: Primitive Data Types</span></span>](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md)
