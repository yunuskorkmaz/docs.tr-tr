---
description: 'Hakkında daha fazla bilgi edinin: tür tanımları (Entity SQL)'
title: Tür tanımları (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 306b204a-ade5-47ef-95b5-c785d2da4a7e
ms.openlocfilehash: e5a66ed9ea456733bab9c68d96ef5c176dad5651
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99673420"
---
# <a name="type-definitions-entity-sql"></a><span data-ttu-id="effe9-103">Tür tanımları (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="effe9-103">Type Definitions (Entity SQL)</span></span>

<span data-ttu-id="effe9-104">Bir tür tanımı, bir satır içi işlevin bildirim ifadesinde kullanılır [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="effe9-104">A type definition is used in the declaration statement of an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Inline function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="effe9-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="effe9-105">Remarks</span></span>  

 <span data-ttu-id="effe9-106">Satır içi işlev için bildirim [bildirimi, Function anahtar sözcüğünden](function-entity-sql.md) ve ardından işlev adını temsil eden tanımlayıcıyı (örneğin, "MyAvg") ve ardından parantez içindeki bir parametre tanım listesini (örneğin, "Dues Collection (Decimal)") içerir.</span><span class="sxs-lookup"><span data-stu-id="effe9-106">The declaration statement for an inline function consists of the [FUNCTION](function-entity-sql.md) keyword followed by the identifier representing the function name (for example, "MyAvg") followed by a parameter definition list in parenthesis (for example, "dues Collection(Decimal)").</span></span>  
  
 <span data-ttu-id="effe9-107">Parametre tanımı listesi sıfır veya daha fazla parametre tanımından oluşur.</span><span class="sxs-lookup"><span data-stu-id="effe9-107">The parameter definition list consists of zero or more parameter definitions.</span></span> <span data-ttu-id="effe9-108">Her parametre tanımı, bir tanımlayıcı (örneğin, işlevin parametresinin adı, örneğin, "Dues") ve ardından bir tür tanımı (örneğin, "Collection (Decimal)") oluşur.</span><span class="sxs-lookup"><span data-stu-id="effe9-108">Each parameter definition consists of an identifier (the name of the parameter to the function, for example, "dues") followed by a type definition (for example, "Collection(Decimal)").</span></span>  
  
 <span data-ttu-id="effe9-109">Tür tanımları şunlardan biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="effe9-109">The type definitions can be either:</span></span>  
  
- <span data-ttu-id="effe9-110">Tanımlayıcının türü (örneğin, "Int32" veya "AdventureWorks. Order").</span><span class="sxs-lookup"><span data-stu-id="effe9-110">The type of the identifier (for example, "Int32" or "AdventureWorks.Order").</span></span>  
  
- <span data-ttu-id="effe9-111">Anahtar sözcüğü, `COLLECTION` parantez içinde başka bir tür tanımı tarafından gelir (örneğin, "koleksiyon (AdventureWorks. Order)").</span><span class="sxs-lookup"><span data-stu-id="effe9-111">The keyword `COLLECTION` followed by another type definition in parenthesis (for example, "Collection(AdventureWorks.Order)").</span></span>  
  
- <span data-ttu-id="effe9-112">Anahtar sözcük SATıRı, parantez içindeki Özellik tanımlarının bir listesi gelir (örneğin, "satır (x AdventureWorks. Order)").</span><span class="sxs-lookup"><span data-stu-id="effe9-112">The keyword ROW followed by a list of property definitions in parenthesis (for example, "Row(x AdventureWorks.Order)").</span></span> <span data-ttu-id="effe9-113">Özellik tanımlarının " `identifier type_definition` , `identifier type_definition` ,..." gibi bir biçimi vardır.</span><span class="sxs-lookup"><span data-stu-id="effe9-113">Property definitions have a format such as "`identifier type_definition`, `identifier type_definition`, ...".</span></span>  
  
- <span data-ttu-id="effe9-114">Anahtar sözcük başvurusu, parantez içindeki tanımlayıcının türü tarafından izlenir (örneğin, "ref (AdventureWorks. Order)").</span><span class="sxs-lookup"><span data-stu-id="effe9-114">The keyword REF followed by the type of the identifier in parenthesis (for example, "Ref(AdventureWorks.Order)").</span></span> <span data-ttu-id="effe9-115">BAŞVURU türü tanımı işleci bağımsız değişken olarak bir varlık türü gerektirir.</span><span class="sxs-lookup"><span data-stu-id="effe9-115">The REF type definition operator requires an entity type as the argument.</span></span> <span data-ttu-id="effe9-116">Bağımsız değişken olarak ilkel bir tür belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="effe9-116">You cannot specify a primitive type as the argument.</span></span>  
  
 <span data-ttu-id="effe9-117">Ayrıca tür tanımlarını iç içe geçirebilirsiniz (örneğin, "koleksiyon (satır (x ref (AdventureWorks. Order))") ").</span><span class="sxs-lookup"><span data-stu-id="effe9-117">You can also nest type definitions (for example, "Collection(Row(x Ref(AdventureWorks.Order)))").</span></span>  
  
 <span data-ttu-id="effe9-118">Tür tanımı seçenekleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="effe9-118">The type definition options are:</span></span>  
  
- <span data-ttu-id="effe9-119">`IdentifierName supported_type`veya</span><span class="sxs-lookup"><span data-stu-id="effe9-119">`IdentifierName supported_type`, or</span></span>  
  
- <span data-ttu-id="effe9-120">`IdentifierName` KOLEKSIYON ( `type_definition` ) veya</span><span class="sxs-lookup"><span data-stu-id="effe9-120">`IdentifierName` COLLECTION(`type_definition`), or</span></span>  
  
- <span data-ttu-id="effe9-121">`IdentifierName` SATıR ( `property_definition` ) veya</span><span class="sxs-lookup"><span data-stu-id="effe9-121">`IdentifierName` ROW(`property_definition`), or</span></span>  
  
- <span data-ttu-id="effe9-122">`IdentifierName` REF ( `supported_entity_type` )</span><span class="sxs-lookup"><span data-stu-id="effe9-122">`IdentifierName` REF(`supported_entity_type`)</span></span>  
  
 <span data-ttu-id="effe9-123">Özellik tanımı seçeneği `IdentifierName type_definition` .</span><span class="sxs-lookup"><span data-stu-id="effe9-123">The property definition option is `IdentifierName type_definition`.</span></span>  
  
 <span data-ttu-id="effe9-124">Desteklenen türler geçerli ad alanındaki türlerdir.</span><span class="sxs-lookup"><span data-stu-id="effe9-124">Supported types are any types in the current namespace.</span></span> <span data-ttu-id="effe9-125">Bunlar hem ilkel hem de varlık türlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="effe9-125">These include both primitive and entity types.</span></span>  
  
 <span data-ttu-id="effe9-126">Desteklenen varlık türleri yalnızca geçerli ad alanındaki varlık türlerine başvurur.</span><span class="sxs-lookup"><span data-stu-id="effe9-126">Supported entity types refer to only entity types in the current namespace.</span></span> <span data-ttu-id="effe9-127">İlkel türler içermez.</span><span class="sxs-lookup"><span data-stu-id="effe9-127">They do not include primitive types.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="effe9-128">Örnekler</span><span class="sxs-lookup"><span data-stu-id="effe9-128">Examples</span></span>  

 <span data-ttu-id="effe9-129">Aşağıda basit tür tanımının bir örneği verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="effe9-129">The following is an example of a simple type definition.</span></span>  
  
```sql  
USING Microsoft.Samples.Entity  
Function MyRound(p1 EDM.Decimal) AS (  
   Round(p1)  
)  
MyRound(CAST(1.7 as EDM.Decimal))  
```  
  
 <span data-ttu-id="effe9-130">Aşağıda, bir koleksıyon türü tanımının bir örneği verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="effe9-130">The following is an example of a COLLECTION type definition.</span></span>  
  
```sql  
USING Microsoft.Samples.Entity  
Function MyRound(p1 Collection(EDM.Decimal)) AS (  
   Select Round(p1) from p1  
)  
MyRound({CAST(1.7 as EDM.Decimal), CAST(2.7 as EDM.Decimal)})  
```  
  
 <span data-ttu-id="effe9-131">Aşağıda satır türü tanımının bir örneği verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="effe9-131">The following is an example of a ROW type definition.</span></span>  
  
```sql  
USING Microsoft.Samples.Entity  
Function MyRound(p1 Row(x EDM.Decimal)) AS (  
   Round(p1.x)  
)  
select MyRound(row(a as x)) from {CAST(1.7 as EDM.Decimal), CAST(2.7 as EDM.Decimal)} as a  
```  
  
 <span data-ttu-id="effe9-132">Aşağıda başvuru türü tanımının bir örneği verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="effe9-132">The following is an example of a REF type definition.</span></span>  
  
```sql  
USING Microsoft.Samples.Entity  
Function UnReference(p1 Ref(AdventureWorks.Order)) AS (  
   Deref(p1)  
)  
select Ref(x) from AdventureWorksEntities.SalesOrderHeaders as x  
```  
  
## <a name="see-also"></a><span data-ttu-id="effe9-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="effe9-133">See also</span></span>

- [<span data-ttu-id="effe9-134">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="effe9-134">Entity SQL Overview</span></span>](entity-sql-overview.md)
- [<span data-ttu-id="effe9-135">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="effe9-135">Entity SQL Reference</span></span>](entity-sql-reference.md)
