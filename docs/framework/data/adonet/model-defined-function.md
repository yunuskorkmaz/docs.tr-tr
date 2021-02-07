---
description: 'Daha fazla bilgi edinin: model tanımlı işlev'
title: model-defined function
ms.date: 03/30/2017
ms.assetid: 8bb2edc8-e8e7-44c2-adc7-f44e11bda4f0
ms.openlocfilehash: 146ef4a8ad8c38897b8e56b6bc1485e1e40754cb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723749"
---
# <a name="model-defined-function"></a><span data-ttu-id="61df9-103">model-defined function</span><span class="sxs-lookup"><span data-stu-id="61df9-103">model-defined function</span></span>

<span data-ttu-id="61df9-104">*Model tanımlı bir işlev* , kavramsal modelde tanımlanan bir işlevdir.</span><span class="sxs-lookup"><span data-stu-id="61df9-104">A *model-defined function* is a function that is defined in a conceptual model.</span></span> <span data-ttu-id="61df9-105">Model tanımlı bir işlevin gövdesi [Entity SQL](./ef/language-reference/entity-sql-language.md)ifade edilir ve bu, işlevin veri kaynağında desteklenen kurallardan veya dillerden bağımsız olarak ifade etmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="61df9-105">The body of a model-defined function is expressed in [Entity SQL](./ef/language-reference/entity-sql-language.md), which allows for the function to be expressed independently of rules or languages supported in the data source.</span></span>  
  
 <span data-ttu-id="61df9-106">Model tanımlı bir işlev için bir tanım aşağıdaki bilgileri içerir:</span><span class="sxs-lookup"><span data-stu-id="61df9-106">A definition for a model-defined function contains the following information:</span></span>  
  
- <span data-ttu-id="61df9-107">İşlev adı.</span><span class="sxs-lookup"><span data-stu-id="61df9-107">A function name.</span></span> <span data-ttu-id="61df9-108">Istenir</span><span class="sxs-lookup"><span data-stu-id="61df9-108">(Required)</span></span>  
  
- <span data-ttu-id="61df9-109">Dönüş değerinin türü.</span><span class="sxs-lookup"><span data-stu-id="61df9-109">The type of the return value.</span></span> <span data-ttu-id="61df9-110">(İsteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="61df9-110">(Optional)</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="61df9-111">Dönüş türü belirtilmemişse, dönüş değeri void olur.</span><span class="sxs-lookup"><span data-stu-id="61df9-111">If no return type is specified, the return value is void.</span></span>  
  
- <span data-ttu-id="61df9-112">Parametre bilgileri.</span><span class="sxs-lookup"><span data-stu-id="61df9-112">Parameter information.</span></span> <span data-ttu-id="61df9-113">(İsteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="61df9-113">(Optional)</span></span>  
  
- <span data-ttu-id="61df9-114">İşlevin gövdesini tanımlayan bir [Entity SQL](./ef/language-reference/entity-sql-language.md) ifadesi.</span><span class="sxs-lookup"><span data-stu-id="61df9-114">An [Entity SQL](./ef/language-reference/entity-sql-language.md) expression that defines the body of the function.</span></span>  
  
 <span data-ttu-id="61df9-115">Model tanımlı işlevlerin çıkış parametrelerini desteklemediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="61df9-115">Note that model-defined functions do not support output parameters.</span></span> <span data-ttu-id="61df9-116">Bu kısıtlama, model tanımlı işlevlerin birleştirilebilmesi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="61df9-116">This restriction is in place so that model-defined functions can be composed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="61df9-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="61df9-117">Example</span></span>  

 <span data-ttu-id="61df9-118">Aşağıdaki diyagramda üç varlık türü olan kavramsal model gösterilmektedir: `Book` , `Publisher` , ve `Author` .</span><span class="sxs-lookup"><span data-stu-id="61df9-118">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span>  
  
 ![Yayımlanma tarihi olan bir modeli gösteren ekran görüntüsü.](./media/model-defined-function/model-published-date-three-entity-types.gif)  
  
 <span data-ttu-id="61df9-120">[ADO.NET Entity Framework](./ef/index.md) kavramsal model tanımlamak için kavramsal şema tanım dili ([csdl](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) adlı bir etki ALANıNA özgü dil (DSL) kullanır.</span><span class="sxs-lookup"><span data-stu-id="61df9-120">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="61df9-121">Aşağıdaki CSDL, bir `Book` (Yukarıdaki diyagramda) bir örneği yayımlandığı için yıl sayılarını döndüren kavramsal modelde bir işlevi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="61df9-121">The following CSDL defines a function in the conceptual model that returns the numbers of years since an instance of a `Book` (in the diagram above) was published.</span></span>  
  
 [!code-xml[EDM_Example_Model#ModelDefinedFunction](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#modeldefinedfunction)]  
  
## <a name="see-also"></a><span data-ttu-id="61df9-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="61df9-122">See also</span></span>

- [<span data-ttu-id="61df9-123">Varlık Veri Modeli Temel Kavramları</span><span class="sxs-lookup"><span data-stu-id="61df9-123">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="61df9-124">Varlık Veri Modeli</span><span class="sxs-lookup"><span data-stu-id="61df9-124">Entity Data Model</span></span>](entity-data-model.md)
- [<span data-ttu-id="61df9-125">Varlık Veri Modeli: Basit Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="61df9-125">Entity Data Model: Primitive Data Types</span></span>](entity-data-model-primitive-data-types.md)
