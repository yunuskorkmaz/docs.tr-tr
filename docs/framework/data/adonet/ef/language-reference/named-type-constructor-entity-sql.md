---
title: Adlı Tür oluşturucu (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 549dea04-d93d-4c87-a292-f81b1598dbfd
ms.openlocfilehash: 9ffaf55ed54e8479a56e6f9fc4d7a5efe47f8e2a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="named-type-constructor-entity-sql"></a><span data-ttu-id="2459c-102">Adlı Tür oluşturucu (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="2459c-102">Named Type Constructor (Entity SQL)</span></span>
<span data-ttu-id="2459c-103">Kavramsal model nominal türleri gibi varlık veya karmaşık türler örneklerini oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2459c-103">Used to create instances of conceptual model nominal types such as Entity or Complex types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2459c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2459c-104">Syntax</span></span>  
  
```  
[{identifier. }] identifier( [expression [{, expression }]] )  
```  
  
## <a name="arguments"></a><span data-ttu-id="2459c-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="2459c-105">Arguments</span></span>  
 `identifier`  
 <span data-ttu-id="2459c-106">Bir basit ya da alıntı tanımlayıcısı değeri.</span><span class="sxs-lookup"><span data-stu-id="2459c-106">Value that is a simple or quoted identifier.</span></span> <span data-ttu-id="2459c-107">Daha fazla bilgi için [tanımlayıcıları](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)</span><span class="sxs-lookup"><span data-stu-id="2459c-107">For more information see, [Identifiers](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)</span></span>  
  
 `expression`  
 <span data-ttu-id="2459c-108">Türü bildiriminde göründükleri gibi aynı sırada olduğu varsayılır türü öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="2459c-108">Attributes of the type that are assumed to be in the same order as they appear in the declaration of the type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2459c-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2459c-109">Return Value</span></span>  
 <span data-ttu-id="2459c-110">Adlandırılmış karmaşık türleri ve varlık türleri örnekleri.</span><span class="sxs-lookup"><span data-stu-id="2459c-110">Instances of named complex types and entity types.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2459c-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2459c-111">Remarks</span></span>  
 <span data-ttu-id="2459c-112">Aşağıdaki örnekler nasıl nominal ve karmaşık türleri oluşturulacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="2459c-112">The following examples show how to construct nominal and complex types:</span></span>  
  
 <span data-ttu-id="2459c-113">İfade bir örneğini oluşturur bir `Person` türü:</span><span class="sxs-lookup"><span data-stu-id="2459c-113">The expression below creates an instance of a `Person` type:</span></span>  
  
 `Person("abc", 12)`  
  
 <span data-ttu-id="2459c-114">İfade karmaşık türün bir örneğini oluşturur:</span><span class="sxs-lookup"><span data-stu-id="2459c-114">The expression below creates an instance of a complex type:</span></span>  
  
 `MyModel.ZipCode(‘98118’, ‘4567’)`  
  
 <span data-ttu-id="2459c-115">Aşağıdaki ifade, iç içe geçmiş bir karmaşık tür bir örneğini oluşturur:</span><span class="sxs-lookup"><span data-stu-id="2459c-115">The expression below creates an instance of a nested complex type:</span></span>  
  
 `MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567'))`  
  
 <span data-ttu-id="2459c-116">İfade bir varlık örneği ile iç içe geçmiş bir karmaşık tür oluşturur:</span><span class="sxs-lookup"><span data-stu-id="2459c-116">The expression below creates an instance of an entity with a nested complex type:</span></span>  
  
 `MyModel.Person("Bill", MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567')))`  
  
 <span data-ttu-id="2459c-117">Aşağıdaki örnekte, bir özelliği null karmaşık türün başlatmak gösterilmektedir:`MyModel.ZipCode(‘98118’, null)`</span><span class="sxs-lookup"><span data-stu-id="2459c-117">The following example shows how to initialize a property of a complex type to null:`MyModel.ZipCode(‘98118’, null)`</span></span>  
  
## <a name="example"></a><span data-ttu-id="2459c-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="2459c-118">Example</span></span>  
 <span data-ttu-id="2459c-119">Aşağıdaki varlık SQL sorgusunu adlandırılmış Tür oluşturucu kavramsal model türünün bir örneği oluşturmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="2459c-119">The following Entity SQL query uses the named type constructor to create an instance of a conceptual model type.</span></span> <span data-ttu-id="2459c-120">Sorgu AdventureWorks satış modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="2459c-120">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="2459c-121">Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="2459c-121">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="2459c-122">Yordamı izleyin [nasıl yapılır: Sorgu döndürür StructuralType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="2459c-122">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="2459c-123">Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="2459c-123">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#NAMED_TYPE_CONSTRUCTOR](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#named_type_constructor)]  
  
## <a name="see-also"></a><span data-ttu-id="2459c-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2459c-124">See Also</span></span>  
 [<span data-ttu-id="2459c-125">Oluşturma Türleri</span><span class="sxs-lookup"><span data-stu-id="2459c-125">Constructing Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)  
 [<span data-ttu-id="2459c-126">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="2459c-126">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
