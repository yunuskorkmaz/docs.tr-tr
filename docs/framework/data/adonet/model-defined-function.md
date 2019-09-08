---
title: model-defined function
ms.date: 03/30/2017
ms.assetid: 8bb2edc8-e8e7-44c2-adc7-f44e11bda4f0
ms.openlocfilehash: 1418eccecea647204620455969696c6390bd4a18
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783620"
---
# <a name="model-defined-function"></a><span data-ttu-id="4f6c7-102">model-defined function</span><span class="sxs-lookup"><span data-stu-id="4f6c7-102">model-defined function</span></span>
<span data-ttu-id="4f6c7-103">*Model tanımlı bir işlev* , kavramsal modelde tanımlanan bir işlevdir.</span><span class="sxs-lookup"><span data-stu-id="4f6c7-103">A *model-defined function* is a function that is defined in a conceptual model.</span></span> <span data-ttu-id="4f6c7-104">Model tanımlı bir işlevin gövdesi [Entity SQL](./ef/language-reference/entity-sql-language.md)ifade edilir ve bu, işlevin veri kaynağında desteklenen kurallardan veya dillerden bağımsız olarak ifade etmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="4f6c7-104">The body of a model-defined function is expressed in [Entity SQL](./ef/language-reference/entity-sql-language.md), which allows for the function to be expressed independently of rules or languages supported in the data source.</span></span>  
  
 <span data-ttu-id="4f6c7-105">Model tanımlı bir işlev için bir tanım aşağıdaki bilgileri içerir:</span><span class="sxs-lookup"><span data-stu-id="4f6c7-105">A definition for a model-defined function contains the following information:</span></span>  
  
- <span data-ttu-id="4f6c7-106">Bir işlev adı.</span><span class="sxs-lookup"><span data-stu-id="4f6c7-106">A function name.</span></span> <span data-ttu-id="4f6c7-107">Istenir</span><span class="sxs-lookup"><span data-stu-id="4f6c7-107">(Required)</span></span>  
  
- <span data-ttu-id="4f6c7-108">Dönüş değerinin türü.</span><span class="sxs-lookup"><span data-stu-id="4f6c7-108">The type of the return value.</span></span> <span data-ttu-id="4f6c7-109">(İsteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="4f6c7-109">(Optional)</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="4f6c7-110">Dönüş türü belirtilmemişse, dönüş değeri void olur.</span><span class="sxs-lookup"><span data-stu-id="4f6c7-110">If no return type is specified, the return value is void.</span></span>  
  
- <span data-ttu-id="4f6c7-111">Parametre bilgileri.</span><span class="sxs-lookup"><span data-stu-id="4f6c7-111">Parameter information.</span></span> <span data-ttu-id="4f6c7-112">(İsteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="4f6c7-112">(Optional)</span></span>  
  
- <span data-ttu-id="4f6c7-113">İşlevin gövdesini tanımlayan bir [Entity SQL](./ef/language-reference/entity-sql-language.md) ifadesi.</span><span class="sxs-lookup"><span data-stu-id="4f6c7-113">An [Entity SQL](./ef/language-reference/entity-sql-language.md) expression that defines the body of the function.</span></span>  
  
 <span data-ttu-id="4f6c7-114">Model tanımlı işlevlerin çıkış parametrelerini desteklemediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="4f6c7-114">Note that model-defined functions do not support output parameters.</span></span> <span data-ttu-id="4f6c7-115">Bu kısıtlama, model tanımlı işlevlerin birleştirilebilmesi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4f6c7-115">This restriction is in place so that model-defined functions can be composed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4f6c7-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="4f6c7-116">Example</span></span>  
 <span data-ttu-id="4f6c7-117">Aşağıdaki diyagramda üç varlık türü olan kavramsal model gösterilmektedir: `Book`, `Publisher`, ve `Author`.</span><span class="sxs-lookup"><span data-stu-id="4f6c7-117">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span>  
  
 ![Yayımlanma tarihi olan bir modeli gösteren ekran görüntüsü.](./media/model-defined-function/model-published-date-three-entity-types.gif)  
  
 <span data-ttu-id="4f6c7-119">[ADO.NET Entity Framework](./ef/index.md) kavramsal model tanımlamak için kavramsal şema tanım dili ([csdl](./ef/language-reference/csdl-specification.md)) adlı bir etki ALANıNA özgü dil (DSL) kullanır.</span><span class="sxs-lookup"><span data-stu-id="4f6c7-119">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](./ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="4f6c7-120">Aşağıdaki csdl, bir (Yukarıdaki diyagramda) bir `Book` örneği yayımlandığı için yıl sayılarını döndüren kavramsal modelde bir işlevi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4f6c7-120">The following CSDL defines a function in the conceptual model that returns the numbers of years since an instance of a `Book` (in the diagram above) was published.</span></span>  
  
 [!code-xml[EDM_Example_Model#ModelDefinedFunction](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#modeldefinedfunction)]  
  
## <a name="see-also"></a><span data-ttu-id="4f6c7-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4f6c7-121">See also</span></span>

- [<span data-ttu-id="4f6c7-122">Varlık Veri Modeli Temel Kavramları</span><span class="sxs-lookup"><span data-stu-id="4f6c7-122">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="4f6c7-123">Varlık Veri Modeli</span><span class="sxs-lookup"><span data-stu-id="4f6c7-123">Entity Data Model</span></span>](entity-data-model.md)
- [<span data-ttu-id="4f6c7-124">Varlık Veri Modeli: İlkel veri türleri</span><span class="sxs-lookup"><span data-stu-id="4f6c7-124">Entity Data Model: Primitive Data Types</span></span>](entity-data-model-primitive-data-types.md)
