---
title: Adlandırılmış Tür oluşturucu (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 549dea04-d93d-4c87-a292-f81b1598dbfd
ms.openlocfilehash: f95f0dcb92068675b2efff0af7e97b349976bf42
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59329472"
---
# <a name="named-type-constructor-entity-sql"></a><span data-ttu-id="bb007-102">Adlandırılmış Tür oluşturucu (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="bb007-102">Named Type Constructor (Entity SQL)</span></span>
<span data-ttu-id="bb007-103">Varlık gibi kavramsal model nominal türü veya karmaşık türler örneklerini oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bb007-103">Used to create instances of conceptual model nominal types such as Entity or Complex types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb007-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bb007-104">Syntax</span></span>  
  
```  
[{identifier. }] identifier( [expression [{, expression }]] )  
```  
  
## <a name="arguments"></a><span data-ttu-id="bb007-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="bb007-105">Arguments</span></span>  
 `identifier`  
 <span data-ttu-id="bb007-106">Basit veya tırnak işaretli tanımlayıcı değeri.</span><span class="sxs-lookup"><span data-stu-id="bb007-106">Value that is a simple or quoted identifier.</span></span> <span data-ttu-id="bb007-107">Daha fazla bilgi edinmek, [tanımlayıcıları](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)</span><span class="sxs-lookup"><span data-stu-id="bb007-107">For more information see, [Identifiers](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)</span></span>  
  
 `expression`  
 <span data-ttu-id="bb007-108">Tür bildiriminde göründükleri gibi aynı sırada olduğu varsayılır öznitelikleri türü.</span><span class="sxs-lookup"><span data-stu-id="bb007-108">Attributes of the type that are assumed to be in the same order as they appear in the declaration of the type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bb007-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="bb007-109">Return Value</span></span>  
 <span data-ttu-id="bb007-110">Adlandırılmış karmaşık türler ve varlık türleri örnekleri.</span><span class="sxs-lookup"><span data-stu-id="bb007-110">Instances of named complex types and entity types.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bb007-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bb007-111">Remarks</span></span>  
 <span data-ttu-id="bb007-112">Aşağıdaki örnekler, nominal ve karmaşık türler gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="bb007-112">The following examples show how to construct nominal and complex types:</span></span>  
  
 <span data-ttu-id="bb007-113">Aşağıdaki ifade bir örneğini oluşturur. bir `Person` türü:</span><span class="sxs-lookup"><span data-stu-id="bb007-113">The expression below creates an instance of a `Person` type:</span></span>  
  
 `Person("abc", 12)`  
  
 <span data-ttu-id="bb007-114">Aşağıdaki ifade, karmaşık bir türün örneğini oluşturur:</span><span class="sxs-lookup"><span data-stu-id="bb007-114">The expression below creates an instance of a complex type:</span></span>  
  
 `MyModel.ZipCode(‘98118’, ‘4567’)`  
  
 <span data-ttu-id="bb007-115">Aşağıdaki ifade, iç içe geçmiş bir karmaşık tür örneği oluşturur:</span><span class="sxs-lookup"><span data-stu-id="bb007-115">The expression below creates an instance of a nested complex type:</span></span>  
  
 `MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567'))`  
  
 <span data-ttu-id="bb007-116">Aşağıdaki ifade ile iç içe geçmiş bir karmaşık türü bir varlık örneği oluşturur:</span><span class="sxs-lookup"><span data-stu-id="bb007-116">The expression below creates an instance of an entity with a nested complex type:</span></span>  
  
 `MyModel.Person("Bill", MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567')))`  
  
 <span data-ttu-id="bb007-117">Aşağıdaki örnek, bir karmaşık türü null bir özelliğini başlatmak gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="bb007-117">The following example shows how to initialize a property of a complex type to null:</span></span>`MyModel.ZipCode(‘98118’, null)`  
  
## <a name="example"></a><span data-ttu-id="bb007-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="bb007-118">Example</span></span>  
 <span data-ttu-id="bb007-119">Aşağıdaki varlık SQL sorgusu adlandırılmış Tür oluşturucu kavramsal model türünün örneğini oluşturmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="bb007-119">The following Entity SQL query uses the named type constructor to create an instance of a conceptual model type.</span></span> <span data-ttu-id="bb007-120">Sorgu, AdventureWorks satış modelini temel alıyor.</span><span class="sxs-lookup"><span data-stu-id="bb007-120">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="bb007-121">Derleme ve bu sorguyu çalıştırmak için bu adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="bb007-121">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="bb007-122">Verilen yordamı izleyin [nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="bb007-122">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="bb007-123">Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="bb007-123">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#NAMED_TYPE_CONSTRUCTOR](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#named_type_constructor)]  
  
## <a name="see-also"></a><span data-ttu-id="bb007-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bb007-124">See also</span></span>

- [<span data-ttu-id="bb007-125">Oluşturma Türleri</span><span class="sxs-lookup"><span data-stu-id="bb007-125">Constructing Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)
- [<span data-ttu-id="bb007-126">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="bb007-126">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
