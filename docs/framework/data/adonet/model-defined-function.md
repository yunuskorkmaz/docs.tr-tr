---
title: model-defined function
ms.date: 03/30/2017
ms.assetid: 8bb2edc8-e8e7-44c2-adc7-f44e11bda4f0
ms.openlocfilehash: 77152e8f37b009cbc3e72f053ead867914768d3d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59226644"
---
# <a name="model-defined-function"></a><span data-ttu-id="3d932-102">model-defined function</span><span class="sxs-lookup"><span data-stu-id="3d932-102">model-defined function</span></span>
<span data-ttu-id="3d932-103">A *model tanımlı işlev* kavramsal modelde tanımlı bir işlev değil.</span><span class="sxs-lookup"><span data-stu-id="3d932-103">A *model-defined function* is a function that is defined in a conceptual model.</span></span> <span data-ttu-id="3d932-104">Model tanımlı bir işlev gövdesini gösterdiğini [varlık SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md), işlevin bağımsız ifade sağlayan kuralları veya veri kaynağındaki desteklenen diller.</span><span class="sxs-lookup"><span data-stu-id="3d932-104">The body of a model-defined function is expressed in [Entity SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md), which allows for the function to be expressed independently of rules or languages supported in the data source.</span></span>  
  
 <span data-ttu-id="3d932-105">Bir model tanımlı işlev tanımı, şu bilgileri içerir:</span><span class="sxs-lookup"><span data-stu-id="3d932-105">A definition for a model-defined function contains the following information:</span></span>  
  
-   <span data-ttu-id="3d932-106">Bir işlev adı.</span><span class="sxs-lookup"><span data-stu-id="3d932-106">A function name.</span></span> <span data-ttu-id="3d932-107">(Gerekli)</span><span class="sxs-lookup"><span data-stu-id="3d932-107">(Required)</span></span>  
  
-   <span data-ttu-id="3d932-108">Dönüş değerinin türü.</span><span class="sxs-lookup"><span data-stu-id="3d932-108">The type of the return value.</span></span> <span data-ttu-id="3d932-109">(İsteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="3d932-109">(Optional)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3d932-110">Dönüş değeri, dönüş türü belirtilirse, geçersizdir.</span><span class="sxs-lookup"><span data-stu-id="3d932-110">If no return type is specified, the return value is void.</span></span>  
  
-   <span data-ttu-id="3d932-111">Parametre bilgileri.</span><span class="sxs-lookup"><span data-stu-id="3d932-111">Parameter information.</span></span> <span data-ttu-id="3d932-112">(İsteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="3d932-112">(Optional)</span></span>  
  
-   <span data-ttu-id="3d932-113">Bir [varlık SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md) işlevinin gövdesi tanımlayan ifade.</span><span class="sxs-lookup"><span data-stu-id="3d932-113">An [Entity SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md) expression that defines the body of the function.</span></span>  
  
 <span data-ttu-id="3d932-114">Not model tanımlı işlevleri çıkış parametreleri desteklemez.</span><span class="sxs-lookup"><span data-stu-id="3d932-114">Note that model-defined functions do not support output parameters.</span></span> <span data-ttu-id="3d932-115">Böylece model tanımlı işlevleri oluşan bu kısıtlama yerdir.</span><span class="sxs-lookup"><span data-stu-id="3d932-115">This restriction is in place so that model-defined functions can be composed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3d932-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="3d932-116">Example</span></span>  
 <span data-ttu-id="3d932-117">Varlık üç kavramsal bir modelle Aşağıdaki diyagramda gösterilmektedir: `Book`, `Publisher`, ve `Author`.</span><span class="sxs-lookup"><span data-stu-id="3d932-117">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span>  
  
 ![Yayımlanma tarihi modeliyle gösteren ekran görüntüsü.](./media/model-defined-function/model-published-date-three-entity-types.gif)  
  
 <span data-ttu-id="3d932-119">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) kavramsal şema tanım dili olarak adlandırılan bir etki alanına özgü dil (DSL) kullanır ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) kavramsal modeller tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="3d932-119">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="3d932-120">Aşağıdaki CSDL örneği itibaren bir yıl sayılarını döndüren kavramsal modeldeki bir işlevi tanımlayan bir `Book` (Yukarıdaki diyagramda) olarak yayımlandı.</span><span class="sxs-lookup"><span data-stu-id="3d932-120">The following CSDL defines a function in the conceptual model that returns the numbers of years since an instance of a `Book` (in the diagram above) was published.</span></span>  
  
 [!code-xml[EDM_Example_Model#ModelDefinedFunction](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#modeldefinedfunction)]  
  
## <a name="see-also"></a><span data-ttu-id="3d932-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3d932-121">See also</span></span>

- [<span data-ttu-id="3d932-122">Varlık Veri Modeli Temel Kavramları</span><span class="sxs-lookup"><span data-stu-id="3d932-122">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [<span data-ttu-id="3d932-123">Varlık Veri Modeli</span><span class="sxs-lookup"><span data-stu-id="3d932-123">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
- [<span data-ttu-id="3d932-124">Varlık veri modeli: Basit veri türleri</span><span class="sxs-lookup"><span data-stu-id="3d932-124">Entity Data Model: Primitive Data Types</span></span>](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md)
