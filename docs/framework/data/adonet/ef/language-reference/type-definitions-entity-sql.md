---
title: Tür tanımları (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 306b204a-ade5-47ef-95b5-c785d2da4a7e
ms.openlocfilehash: 7e4e6f0e9f64816d10a69a8b0639728e4cd7af80
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201024"
---
# <a name="type-definitions-entity-sql"></a><span data-ttu-id="1c0ab-102">Tür tanımları (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="1c0ab-102">Type Definitions (Entity SQL)</span></span>

<span data-ttu-id="1c0ab-103">Bir tür tanımı, bir satır içi işlevin bildirim ifadesinde kullanılır [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="1c0ab-103">A type definition is used in the declaration statement of an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Inline function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1c0ab-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1c0ab-104">Remarks</span></span>  

 <span data-ttu-id="1c0ab-105">Satır içi işlev için bildirim [bildirimi, Function anahtar sözcüğünden](function-entity-sql.md) ve ardından işlev adını temsil eden tanımlayıcıyı (örneğin, "MyAvg") ve ardından parantez içindeki bir parametre tanım listesini (örneğin, "Dues Collection (Decimal)") içerir.</span><span class="sxs-lookup"><span data-stu-id="1c0ab-105">The declaration statement for an inline function consists of the [FUNCTION](function-entity-sql.md) keyword followed by the identifier representing the function name (for example, "MyAvg") followed by a parameter definition list in parenthesis (for example, "dues Collection(Decimal)").</span></span>  
  
 <span data-ttu-id="1c0ab-106">Parametre tanımı listesi sıfır veya daha fazla parametre tanımından oluşur.</span><span class="sxs-lookup"><span data-stu-id="1c0ab-106">The parameter definition list consists of zero or more parameter definitions.</span></span> <span data-ttu-id="1c0ab-107">Her parametre tanımı, bir tanımlayıcı (örneğin, işlevin parametresinin adı, örneğin, "Dues") ve ardından bir tür tanımı (örneğin, "Collection (Decimal)") oluşur.</span><span class="sxs-lookup"><span data-stu-id="1c0ab-107">Each parameter definition consists of an identifier (the name of the parameter to the function, for example, "dues") followed by a type definition (for example, "Collection(Decimal)").</span></span>  
  
 <span data-ttu-id="1c0ab-108">Tür tanımları şunlardan biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="1c0ab-108">The type definitions can be either:</span></span>  
  
- <span data-ttu-id="1c0ab-109">Tanımlayıcının türü (örneğin, "Int32" veya "AdventureWorks. Order").</span><span class="sxs-lookup"><span data-stu-id="1c0ab-109">The type of the identifier (for example, "Int32" or "AdventureWorks.Order").</span></span>  
  
- <span data-ttu-id="1c0ab-110">Anahtar sözcüğü, `COLLECTION` parantez içinde başka bir tür tanımı tarafından gelir (örneğin, "koleksiyon (AdventureWorks. Order)").</span><span class="sxs-lookup"><span data-stu-id="1c0ab-110">The keyword `COLLECTION` followed by another type definition in parenthesis (for example, "Collection(AdventureWorks.Order)").</span></span>  
  
- <span data-ttu-id="1c0ab-111">Anahtar sözcük SATıRı, parantez içindeki Özellik tanımlarının bir listesi gelir (örneğin, "satır (x AdventureWorks. Order)").</span><span class="sxs-lookup"><span data-stu-id="1c0ab-111">The keyword ROW followed by a list of property definitions in parenthesis (for example, "Row(x AdventureWorks.Order)").</span></span> <span data-ttu-id="1c0ab-112">Özellik tanımlarının " `identifier type_definition` , `identifier type_definition` ,..." gibi bir biçimi vardır.</span><span class="sxs-lookup"><span data-stu-id="1c0ab-112">Property definitions have a format such as "`identifier type_definition`, `identifier type_definition`, ...".</span></span>  
  
- <span data-ttu-id="1c0ab-113">Anahtar sözcük başvurusu, parantez içindeki tanımlayıcının türü tarafından izlenir (örneğin, "ref (AdventureWorks. Order)").</span><span class="sxs-lookup"><span data-stu-id="1c0ab-113">The keyword REF followed by the type of the identifier in parenthesis (for example, "Ref(AdventureWorks.Order)").</span></span> <span data-ttu-id="1c0ab-114">BAŞVURU türü tanımı işleci bağımsız değişken olarak bir varlık türü gerektirir.</span><span class="sxs-lookup"><span data-stu-id="1c0ab-114">The REF type definition operator requires an entity type as the argument.</span></span> <span data-ttu-id="1c0ab-115">Bağımsız değişken olarak ilkel bir tür belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="1c0ab-115">You cannot specify a primitive type as the argument.</span></span>  
  
 <span data-ttu-id="1c0ab-116">Ayrıca tür tanımlarını iç içe geçirebilirsiniz (örneğin, "koleksiyon (satır (x ref (AdventureWorks. Order))") ").</span><span class="sxs-lookup"><span data-stu-id="1c0ab-116">You can also nest type definitions (for example, "Collection(Row(x Ref(AdventureWorks.Order)))").</span></span>  
  
 <span data-ttu-id="1c0ab-117">Tür tanımı seçenekleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="1c0ab-117">The type definition options are:</span></span>  
  
- <span data-ttu-id="1c0ab-118">`IdentifierName supported_type`veya</span><span class="sxs-lookup"><span data-stu-id="1c0ab-118">`IdentifierName supported_type`, or</span></span>  
  
- <span data-ttu-id="1c0ab-119">`IdentifierName` KOLEKSIYON ( `type_definition` ) veya</span><span class="sxs-lookup"><span data-stu-id="1c0ab-119">`IdentifierName` COLLECTION(`type_definition`), or</span></span>  
  
- <span data-ttu-id="1c0ab-120">`IdentifierName` SATıR ( `property_definition` ) veya</span><span class="sxs-lookup"><span data-stu-id="1c0ab-120">`IdentifierName` ROW(`property_definition`), or</span></span>  
  
- <span data-ttu-id="1c0ab-121">`IdentifierName` REF ( `supported_entity_type` )</span><span class="sxs-lookup"><span data-stu-id="1c0ab-121">`IdentifierName` REF(`supported_entity_type`)</span></span>  
  
 <span data-ttu-id="1c0ab-122">Özellik tanımı seçeneği `IdentifierName type_definition` .</span><span class="sxs-lookup"><span data-stu-id="1c0ab-122">The property definition option is `IdentifierName type_definition`.</span></span>  
  
 <span data-ttu-id="1c0ab-123">Desteklenen türler geçerli ad alanındaki türlerdir.</span><span class="sxs-lookup"><span data-stu-id="1c0ab-123">Supported types are any types in the current namespace.</span></span> <span data-ttu-id="1c0ab-124">Bunlar hem ilkel hem de varlık türlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="1c0ab-124">These include both primitive and entity types.</span></span>  
  
 <span data-ttu-id="1c0ab-125">Desteklenen varlık türleri yalnızca geçerli ad alanındaki varlık türlerine başvurur.</span><span class="sxs-lookup"><span data-stu-id="1c0ab-125">Supported entity types refer to only entity types in the current namespace.</span></span> <span data-ttu-id="1c0ab-126">İlkel türler içermez.</span><span class="sxs-lookup"><span data-stu-id="1c0ab-126">They do not include primitive types.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="1c0ab-127">Örnekler</span><span class="sxs-lookup"><span data-stu-id="1c0ab-127">Examples</span></span>  

 <span data-ttu-id="1c0ab-128">Aşağıda basit tür tanımının bir örneği verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="1c0ab-128">The following is an example of a simple type definition.</span></span>  
  
```sql  
USING Microsoft.Samples.Entity  
Function MyRound(p1 EDM.Decimal) AS (  
   Round(p1)  
)  
MyRound(CAST(1.7 as EDM.Decimal))  
```  
  
 <span data-ttu-id="1c0ab-129">Aşağıda, bir koleksıyon türü tanımının bir örneği verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="1c0ab-129">The following is an example of a COLLECTION type definition.</span></span>  
  
```sql  
USING Microsoft.Samples.Entity  
Function MyRound(p1 Collection(EDM.Decimal)) AS (  
   Select Round(p1) from p1  
)  
MyRound({CAST(1.7 as EDM.Decimal), CAST(2.7 as EDM.Decimal)})  
```  
  
 <span data-ttu-id="1c0ab-130">Aşağıda satır türü tanımının bir örneği verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="1c0ab-130">The following is an example of a ROW type definition.</span></span>  
  
```sql  
USING Microsoft.Samples.Entity  
Function MyRound(p1 Row(x EDM.Decimal)) AS (  
   Round(p1.x)  
)  
select MyRound(row(a as x)) from {CAST(1.7 as EDM.Decimal), CAST(2.7 as EDM.Decimal)} as a  
```  
  
 <span data-ttu-id="1c0ab-131">Aşağıda başvuru türü tanımının bir örneği verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="1c0ab-131">The following is an example of a REF type definition.</span></span>  
  
```sql  
USING Microsoft.Samples.Entity  
Function UnReference(p1 Ref(AdventureWorks.Order)) AS (  
   Deref(p1)  
)  
select Ref(x) from AdventureWorksEntities.SalesOrderHeaders as x  
```  
  
## <a name="see-also"></a><span data-ttu-id="1c0ab-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1c0ab-132">See also</span></span>

- [<span data-ttu-id="1c0ab-133">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="1c0ab-133">Entity SQL Overview</span></span>](entity-sql-overview.md)
- [<span data-ttu-id="1c0ab-134">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="1c0ab-134">Entity SQL Reference</span></span>](entity-sql-reference.md)
