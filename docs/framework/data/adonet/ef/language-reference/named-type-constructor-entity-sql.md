---
title: "Adlı Tür oluşturucu (varlık SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 549dea04-d93d-4c87-a292-f81b1598dbfd
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 72a19094beb03982448a102a4c7362a026d9e611
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="named-type-constructor-entity-sql"></a><span data-ttu-id="d7d87-102">Adlı Tür oluşturucu (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="d7d87-102">Named Type Constructor (Entity SQL)</span></span>
<span data-ttu-id="d7d87-103">Kavramsal model nominal türleri gibi varlık veya karmaşık türler örneklerini oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d7d87-103">Used to create instances of conceptual model nominal types such as Entity or Complex types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7d87-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d7d87-104">Syntax</span></span>  
  
```  
[{identifier. }] identifier( [expression [{, expression }]] )  
```  
  
## <a name="arguments"></a><span data-ttu-id="d7d87-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="d7d87-105">Arguments</span></span>  
 `identifier`  
 <span data-ttu-id="d7d87-106">Bir basit ya da alıntı tanımlayıcısı değeri.</span><span class="sxs-lookup"><span data-stu-id="d7d87-106">Value that is a simple or quoted identifier.</span></span> <span data-ttu-id="d7d87-107">Daha fazla bilgi için [tanımlayıcıları](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)</span><span class="sxs-lookup"><span data-stu-id="d7d87-107">For more information see, [Identifiers](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)</span></span>  
  
 `expression`  
 <span data-ttu-id="d7d87-108">Türü bildiriminde göründükleri gibi aynı sırada olduğu varsayılır türü öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="d7d87-108">Attributes of the type that are assumed to be in the same order as they appear in the declaration of the type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d7d87-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d7d87-109">Return Value</span></span>  
 <span data-ttu-id="d7d87-110">Adlandırılmış karmaşık türleri ve varlık türleri örnekleri.</span><span class="sxs-lookup"><span data-stu-id="d7d87-110">Instances of named complex types and entity types.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d7d87-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d7d87-111">Remarks</span></span>  
 <span data-ttu-id="d7d87-112">Aşağıdaki örnekler nasıl nominal ve karmaşık türleri oluşturulacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="d7d87-112">The following examples show how to construct nominal and complex types:</span></span>  
  
 <span data-ttu-id="d7d87-113">İfade bir örneğini oluşturur bir `Person` türü:</span><span class="sxs-lookup"><span data-stu-id="d7d87-113">The expression below creates an instance of a `Person` type:</span></span>  
  
 `Person("abc", 12)`  
  
 <span data-ttu-id="d7d87-114">İfade karmaşık türün bir örneğini oluşturur:</span><span class="sxs-lookup"><span data-stu-id="d7d87-114">The expression below creates an instance of a complex type:</span></span>  
  
 `MyModel.ZipCode(‘98118’, ‘4567’)`  
  
 <span data-ttu-id="d7d87-115">Aşağıdaki ifade, iç içe geçmiş bir karmaşık tür bir örneğini oluşturur:</span><span class="sxs-lookup"><span data-stu-id="d7d87-115">The expression below creates an instance of a nested complex type:</span></span>  
  
 `MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567'))`  
  
 <span data-ttu-id="d7d87-116">İfade bir varlık örneği ile iç içe geçmiş bir karmaşık tür oluşturur:</span><span class="sxs-lookup"><span data-stu-id="d7d87-116">The expression below creates an instance of an entity with a nested complex type:</span></span>  
  
 `MyModel.Person("Bill", MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567')))`  
  
 <span data-ttu-id="d7d87-117">Aşağıdaki örnekte, bir özelliği null karmaşık türün başlatmak gösterilmektedir:`MyModel.ZipCode(‘98118’, null)`</span><span class="sxs-lookup"><span data-stu-id="d7d87-117">The following example shows how to initialize a property of a complex type to null:`MyModel.ZipCode(‘98118’, null)`</span></span>  
  
## <a name="example"></a><span data-ttu-id="d7d87-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="d7d87-118">Example</span></span>  
 <span data-ttu-id="d7d87-119">Aşağıdaki varlık SQL sorgusunu adlandırılmış Tür oluşturucu kavramsal model türünün bir örneği oluşturmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="d7d87-119">The following Entity SQL query uses the named type constructor to create an instance of a conceptual model type.</span></span> <span data-ttu-id="d7d87-120">Sorgu AdventureWorks satış modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="d7d87-120">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="d7d87-121">Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="d7d87-121">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="d7d87-122">Yordamı izleyin [nasıl yapılır: Sorgu döndürür StructuralType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="d7d87-122">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="d7d87-123">Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="d7d87-123">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#NAMED_TYPE_CONSTRUCTOR](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#named_type_constructor)]  
  
## <a name="see-also"></a><span data-ttu-id="d7d87-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d7d87-124">See Also</span></span>  
 [<span data-ttu-id="d7d87-125">Türleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="d7d87-125">Constructing Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)  
 [<span data-ttu-id="d7d87-126">Varlık SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="d7d87-126">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
