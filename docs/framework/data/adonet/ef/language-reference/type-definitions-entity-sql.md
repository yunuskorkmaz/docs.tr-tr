---
title: Tür tanımları (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 306b204a-ade5-47ef-95b5-c785d2da4a7e
ms.openlocfilehash: 2e068db0ce202c26cad36c8ed7adf0acdfb8e363
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59096029"
---
# <a name="type-definitions-entity-sql"></a><span data-ttu-id="9e8e8-102">Tür tanımları (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="9e8e8-102">Type Definitions (Entity SQL)</span></span>
<span data-ttu-id="9e8e8-103">Bir tür tanımı bildirim deyiminde kullanılan bir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] satır içi işlev.</span><span class="sxs-lookup"><span data-stu-id="9e8e8-103">A type definition is used in the declaration statement of an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Inline function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9e8e8-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9e8e8-104">Remarks</span></span>  
 <span data-ttu-id="9e8e8-105">Bildirim deyimindeki bir satır içi işlevinin oluşan [işlevi](../../../../../../docs/framework/data/adonet/ef/language-reference/function-entity-sql.md) ayracından (parametre tanımı listesinde işlev adından (örneğin, "MyAvg") temsil eden tanımlayıcı ardından anahtar sözcüğü Örneğin, "Collection(Decimal)") sonu.</span><span class="sxs-lookup"><span data-stu-id="9e8e8-105">The declaration statement for an inline function consists of the [FUNCTION](../../../../../../docs/framework/data/adonet/ef/language-reference/function-entity-sql.md) keyword followed by the identifier representing the function name (for example, "MyAvg") followed by a parameter definition list in parenthesis (for example, "dues Collection(Decimal)").</span></span>  
  
 <span data-ttu-id="9e8e8-106">Sıfır veya daha fazla parametre tanımını parametre tanımı listesinden oluşur.</span><span class="sxs-lookup"><span data-stu-id="9e8e8-106">The parameter definition list consists of zero or more parameter definitions.</span></span> <span data-ttu-id="9e8e8-107">Her parametre tanımında bir tür tanımı (örneğin, "Collection(Decimal)"). ardından bir tanımlayıcı (örneğin, "sonu" işlevine parametrenin adı) oluşur</span><span class="sxs-lookup"><span data-stu-id="9e8e8-107">Each parameter definition consists of an identifier (the name of the parameter to the function, for example, "dues") followed by a type definition (for example, "Collection(Decimal)").</span></span>  
  
 <span data-ttu-id="9e8e8-108">Tür tanımlarını şöyle olabilir:</span><span class="sxs-lookup"><span data-stu-id="9e8e8-108">The type definitions can be either:</span></span>  
  
-   <span data-ttu-id="9e8e8-109">Tanımlayıcı (örneğin, "Int32" veya "AdventureWorks.Order") türü.</span><span class="sxs-lookup"><span data-stu-id="9e8e8-109">The type of the identifier (for example, "Int32" or "AdventureWorks.Order").</span></span>  
  
-   <span data-ttu-id="9e8e8-110">Anahtar sözcüğü `COLLECTION` parantez (örneğin, "Collection(AdventureWorks.Order)"). başka bir tür tanımında ardından</span><span class="sxs-lookup"><span data-stu-id="9e8e8-110">The keyword `COLLECTION` followed by another type definition in parenthesis (for example, "Collection(AdventureWorks.Order)").</span></span>  
  
-   <span data-ttu-id="9e8e8-111">Anahtar sözcüğü satır parantez (örneğin, "Row(x AdventureWorks.Order)") içinde özellik tanımları listesi tarafından izlenen.</span><span class="sxs-lookup"><span data-stu-id="9e8e8-111">The keyword ROW followed by a list of property definitions in parenthesis (for example, "Row(x AdventureWorks.Order)").</span></span> <span data-ttu-id="9e8e8-112">Özellik tanımları sahip bir biçimi gibi "`identifier type_definition`, `identifier type_definition`,...".</span><span class="sxs-lookup"><span data-stu-id="9e8e8-112">Property definitions have a format such as "`identifier type_definition`, `identifier type_definition`, ...".</span></span>  
  
-   <span data-ttu-id="9e8e8-113">Türü (örneğin, "Ref(AdventureWorks.Order)"). parantez içinde tanımlayıcısının arkasından REF anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="9e8e8-113">The keyword REF followed by the type of the identifier in parenthesis (for example, "Ref(AdventureWorks.Order)").</span></span> <span data-ttu-id="9e8e8-114">Başvuru türü tanımı işleci, bağımsız değişken olarak bir varlık türü gerektirir.</span><span class="sxs-lookup"><span data-stu-id="9e8e8-114">The REF type definition operator requires an entity type as the argument.</span></span> <span data-ttu-id="9e8e8-115">Basit bir tür bağımsız değişkeni olarak belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="9e8e8-115">You cannot specify a primitive type as the argument.</span></span>  
  
 <span data-ttu-id="9e8e8-116">Tür tanımları da iç içe geçirebilirsiniz (örneğin, "koleksiyonu (Row(x Ref(AdventureWorks.Order)))").</span><span class="sxs-lookup"><span data-stu-id="9e8e8-116">You can also nest type definitions (for example, "Collection(Row(x Ref(AdventureWorks.Order)))").</span></span>  
  
 <span data-ttu-id="9e8e8-117">Tür tanımı seçenekleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="9e8e8-117">The type definition options are:</span></span>  
  
-   `IdentifierName supported_type`<span data-ttu-id="9e8e8-118">, veya</span><span class="sxs-lookup"><span data-stu-id="9e8e8-118">, or</span></span>  
  
-   `IdentifierName` <span data-ttu-id="9e8e8-119">KOLEKSİYON (`type_definition`), veya</span><span class="sxs-lookup"><span data-stu-id="9e8e8-119">COLLECTION(`type_definition`), or</span></span>  
  
-   `IdentifierName` <span data-ttu-id="9e8e8-120">SATIR (`property_definition`), veya</span><span class="sxs-lookup"><span data-stu-id="9e8e8-120">ROW(`property_definition`), or</span></span>  
  
-   `IdentifierName` <span data-ttu-id="9e8e8-121">REF (`supported_entity_type`)</span><span class="sxs-lookup"><span data-stu-id="9e8e8-121">REF(`supported_entity_type`)</span></span>  
  
 <span data-ttu-id="9e8e8-122">Özellik tanımı seçeneği `IdentifierName type_definition`.</span><span class="sxs-lookup"><span data-stu-id="9e8e8-122">The property definition option is `IdentifierName type_definition`.</span></span>  
  
 <span data-ttu-id="9e8e8-123">Geçerli ad alanındaki herhangi bir türü desteklenen türleridir.</span><span class="sxs-lookup"><span data-stu-id="9e8e8-123">Supported types are any types in the current namespace.</span></span> <span data-ttu-id="9e8e8-124">Bunlar, hem temel hem de varlık türleri içerir.</span><span class="sxs-lookup"><span data-stu-id="9e8e8-124">These include both primitive and entity types.</span></span>  
  
 <span data-ttu-id="9e8e8-125">Varlık türleri yalnızca varlık türleri geçerli ad alanındaki bakın desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="9e8e8-125">Supported entity types refer to only entity types in the current namespace.</span></span> <span data-ttu-id="9e8e8-126">İlkel türler dahil değildir.</span><span class="sxs-lookup"><span data-stu-id="9e8e8-126">They do not include primitive types.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="9e8e8-127">Örnekler</span><span class="sxs-lookup"><span data-stu-id="9e8e8-127">Examples</span></span>  
 <span data-ttu-id="9e8e8-128">Bir basit tür tanımı, bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="9e8e8-128">The following is an example of a simple type definition.</span></span>  
  
```  
USING Microsoft.Samples.Entity  
Function MyRound(p1 EDM.Decimal) AS (  
   Round(p1)  
)  
MyRound(CAST(1.7 as EDM.Decimal))  
```  
  
 <span data-ttu-id="9e8e8-129">Aşağıdaki KOLEKSİYON türü tanımı örneğidir.</span><span class="sxs-lookup"><span data-stu-id="9e8e8-129">The following is an example of a COLLECTION type definition.</span></span>  
  
```  
USING Microsoft.Samples.Entity  
Function MyRound(p1 Collection(EDM.Decimal)) AS (  
   Select Round(p1) from p1  
)  
MyRound({CAST(1.7 as EDM.Decimal), CAST(2.7 as EDM.Decimal)})  
```  
  
 <span data-ttu-id="9e8e8-130">Satır türü tanımı bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="9e8e8-130">The following is an example of a ROW type definition.</span></span>  
  
```  
USING Microsoft.Samples.Entity  
Function MyRound(p1 Row(x EDM.Decimal)) AS (  
   Round(p1.x)  
)  
select MyRound(row(a as x)) from {CAST(1.7 as EDM.Decimal), CAST(2.7 as EDM.Decimal)} as a  
```  
  
 <span data-ttu-id="9e8e8-131">Başvuru türü tanımı bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="9e8e8-131">The following is an example of a REF type definition.</span></span>  
  
```  
USING Microsoft.Samples.Entity  
Function UnReference(p1 Ref(AdventureWorks.Order)) AS (  
   Deref(p1)  
)  
select Ref(x) from AdventureWorksEntities.SalesOrderHeaders as x  
```  
  
## <a name="see-also"></a><span data-ttu-id="9e8e8-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9e8e8-132">See also</span></span>

- [<span data-ttu-id="9e8e8-133">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9e8e8-133">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [<span data-ttu-id="9e8e8-134">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="9e8e8-134">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
