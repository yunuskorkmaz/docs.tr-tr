---
title: Tür tanımları (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 306b204a-ade5-47ef-95b5-c785d2da4a7e
ms.openlocfilehash: 7abbe5dfed005a10955a385cadf12725a9450512
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32761161"
---
# <a name="type-definitions-entity-sql"></a><span data-ttu-id="a637d-102">Tür tanımları (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="a637d-102">Type Definitions (Entity SQL)</span></span>
<span data-ttu-id="a637d-103">Bir tür tanımı bildirimi deyiminde kullanılan bir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] satır içi işlev.</span><span class="sxs-lookup"><span data-stu-id="a637d-103">A type definition is used in the declaration statement of an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Inline function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a637d-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a637d-104">Remarks</span></span>  
 <span data-ttu-id="a637d-105">Satır içi işlev bildirimi deyimi oluşan [işlevi](../../../../../../docs/framework/data/adonet/ef/language-reference/function-entity-sql.md) parantez (için parametre tanımı listesinde işlevi adından (örneğin, "MyAvg") temsil eden tanımlayıcı arkasından anahtar sözcüğü Örneğin, "nedeniyle Collection(Decimal)").</span><span class="sxs-lookup"><span data-stu-id="a637d-105">The declaration statement for an inline function consists of the [FUNCTION](../../../../../../docs/framework/data/adonet/ef/language-reference/function-entity-sql.md) keyword followed by the identifier representing the function name (for example, "MyAvg") followed by a parameter definition list in parenthesis (for example, "dues Collection(Decimal)").</span></span>  
  
 <span data-ttu-id="a637d-106">Parametre tanımı listesi sıfır veya daha fazla parametre tanımlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="a637d-106">The parameter definition list consists of zero or more parameter definitions.</span></span> <span data-ttu-id="a637d-107">Her parametre tanımı bir tür tanımı (örneğin, "Collection(Decimal)"). ardından bir tanımlayıcı (örneğin, "sonu" işlevi için parametre adı) oluşur</span><span class="sxs-lookup"><span data-stu-id="a637d-107">Each parameter definition consists of an identifier (the name of the parameter to the function, for example, "dues") followed by a type definition (for example, "Collection(Decimal)").</span></span>  
  
 <span data-ttu-id="a637d-108">Tür tanımları birini kullanabilir:</span><span class="sxs-lookup"><span data-stu-id="a637d-108">The type definitions can be either:</span></span>  
  
-   <span data-ttu-id="a637d-109">Tanımlayıcı (örneğin, "Int32" veya "AdventureWorks.Order") türü.</span><span class="sxs-lookup"><span data-stu-id="a637d-109">The type of the identifier (for example, "Int32" or "AdventureWorks.Order").</span></span>  
  
-   <span data-ttu-id="a637d-110">Anahtar sözcüğü `COLLECTION` parantez (örneğin, "Collection(AdventureWorks.Order)"). başka bir tür tanımında ve ardından</span><span class="sxs-lookup"><span data-stu-id="a637d-110">The keyword `COLLECTION` followed by another type definition in parenthesis (for example, "Collection(AdventureWorks.Order)").</span></span>  
  
-   <span data-ttu-id="a637d-111">Anahtar özellik tanımları parantez (örneğin, "Row(x AdventureWorks.Order)") içinde listesini satır arkasından.</span><span class="sxs-lookup"><span data-stu-id="a637d-111">The keyword ROW followed by a list of property definitions in parenthesis (for example, "Row(x AdventureWorks.Order)").</span></span> <span data-ttu-id="a637d-112">Özellik tanımları olan bir biçim gibi "`identifier type_definition`, `identifier type_definition`,...".</span><span class="sxs-lookup"><span data-stu-id="a637d-112">Property definitions have a format such as "`identifier type_definition`, `identifier type_definition`, ...".</span></span>  
  
-   <span data-ttu-id="a637d-113">Parantez (örneğin, "Ref(AdventureWorks.Order)"). tanımlayıcıda türünü ve ardından REF anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="a637d-113">The keyword REF followed by the type of the identifier in parenthesis (for example, "Ref(AdventureWorks.Order)").</span></span> <span data-ttu-id="a637d-114">REF türü tanımı işleci bağımsız değişken olarak bir varlık türü gerektirir.</span><span class="sxs-lookup"><span data-stu-id="a637d-114">The REF type definition operator requires an entity type as the argument.</span></span> <span data-ttu-id="a637d-115">Bağımsız değişken olarak bir ilkel türü belirtilemez.</span><span class="sxs-lookup"><span data-stu-id="a637d-115">You cannot specify a primitive type as the argument.</span></span>  
  
 <span data-ttu-id="a637d-116">Tür tanımları içe kullanabilirsiniz (örneğin, "koleksiyonu (Row(x Ref(AdventureWorks.Order)))").</span><span class="sxs-lookup"><span data-stu-id="a637d-116">You can also nest type definitions (for example, "Collection(Row(x Ref(AdventureWorks.Order)))").</span></span>  
  
 <span data-ttu-id="a637d-117">Tür tanımı Seçenekler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="a637d-117">The type definition options are:</span></span>  
  
-   <span data-ttu-id="a637d-118">`IdentifierName supported_type`, veya</span><span class="sxs-lookup"><span data-stu-id="a637d-118">`IdentifierName supported_type`, or</span></span>  
  
-   <span data-ttu-id="a637d-119">`IdentifierName` KOLEKSİYON (`type_definition`), veya</span><span class="sxs-lookup"><span data-stu-id="a637d-119">`IdentifierName` COLLECTION(`type_definition`), or</span></span>  
  
-   <span data-ttu-id="a637d-120">`IdentifierName` SATIR (`property_definition`), veya</span><span class="sxs-lookup"><span data-stu-id="a637d-120">`IdentifierName` ROW(`property_definition`), or</span></span>  
  
-   <span data-ttu-id="a637d-121">`IdentifierName` REF (`supported_entity_type`)</span><span class="sxs-lookup"><span data-stu-id="a637d-121">`IdentifierName` REF(`supported_entity_type`)</span></span>  
  
 <span data-ttu-id="a637d-122">Özellik tanımı seçenek `IdentifierName type_definition`.</span><span class="sxs-lookup"><span data-stu-id="a637d-122">The property definition option is `IdentifierName type_definition`.</span></span>  
  
 <span data-ttu-id="a637d-123">Desteklenen türler geçerli ad alanındaki tüm türleridir.</span><span class="sxs-lookup"><span data-stu-id="a637d-123">Supported types are any types in the current namespace.</span></span> <span data-ttu-id="a637d-124">Bunlar, ilkel ve varlık türleri içerir.</span><span class="sxs-lookup"><span data-stu-id="a637d-124">These include both primitive and entity types.</span></span>  
  
 <span data-ttu-id="a637d-125">Yalnızca varlık türleri geçerli ad alanındaki türler başvurmak varlık desteklenir.</span><span class="sxs-lookup"><span data-stu-id="a637d-125">Supported entity types refer to only entity types in the current namespace.</span></span> <span data-ttu-id="a637d-126">İlkel türler içermez.</span><span class="sxs-lookup"><span data-stu-id="a637d-126">They do not include primitive types.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="a637d-127">Örnekler</span><span class="sxs-lookup"><span data-stu-id="a637d-127">Examples</span></span>  
 <span data-ttu-id="a637d-128">Aşağıda, bir basit tür tanımı bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="a637d-128">The following is an example of a simple type definition.</span></span>  
  
```  
USING Microsoft.Samples.Entity  
Function MyRound(p1 EDM.Decimal) AS (  
   Round(p1)  
)  
MyRound(CAST(1.7 as EDM.Decimal))  
```  
  
 <span data-ttu-id="a637d-129">Bir KOLEKSİYON türü tanımının bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="a637d-129">The following is an example of a COLLECTION type definition.</span></span>  
  
```  
USING Microsoft.Samples.Entity  
Function MyRound(p1 Collection(EDM.Decimal)) AS (  
   Select Round(p1) from p1  
)  
MyRound({CAST(1.7 as EDM.Decimal), CAST(2.7 as EDM.Decimal)})  
```  
  
 <span data-ttu-id="a637d-130">Satır türü tanımı bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="a637d-130">The following is an example of a ROW type definition.</span></span>  
  
```  
USING Microsoft.Samples.Entity  
Function MyRound(p1 Row(x EDM.Decimal)) AS (  
   Round(p1.x)  
)  
select MyRound(row(a as x)) from {CAST(1.7 as EDM.Decimal), CAST(2.7 as EDM.Decimal)} as a  
```  
  
 <span data-ttu-id="a637d-131">REF türü tanımı bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="a637d-131">The following is an example of a REF type definition.</span></span>  
  
```  
USING Microsoft.Samples.Entity  
Function UnReference(p1 Ref(AdventureWorks.Order)) AS (  
   Deref(p1)  
)  
select Ref(x) from AdventureWorksEntities.SalesOrderHeaders as x  
```  
  
## <a name="see-also"></a><span data-ttu-id="a637d-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a637d-132">See Also</span></span>  
 [<span data-ttu-id="a637d-133">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a637d-133">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [<span data-ttu-id="a637d-134">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="a637d-134">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
