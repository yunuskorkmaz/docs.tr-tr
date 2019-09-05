---
title: Adlandırılmış tür Oluşturucusu (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 549dea04-d93d-4c87-a292-f81b1598dbfd
ms.openlocfilehash: c7027614e5667acedb02d871a09df1ac9d799405
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250013"
---
# <a name="named-type-constructor-entity-sql"></a><span data-ttu-id="bfc49-102">Adlandırılmış tür Oluşturucusu (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="bfc49-102">Named Type Constructor (Entity SQL)</span></span>
<span data-ttu-id="bfc49-103">Varlık veya karmaşık türler gibi kavramsal model nominal türlerin örneklerini oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bfc49-103">Used to create instances of conceptual model nominal types such as Entity or Complex types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bfc49-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bfc49-104">Syntax</span></span>  
  
```  
[{identifier. }] identifier( [expression [{, expression }]] )  
```  
  
## <a name="arguments"></a><span data-ttu-id="bfc49-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="bfc49-105">Arguments</span></span>  
 `identifier`  
 <span data-ttu-id="bfc49-106">Basit veya tırnaklı bir tanımlayıcı değeri.</span><span class="sxs-lookup"><span data-stu-id="bfc49-106">Value that is a simple or quoted identifier.</span></span> <span data-ttu-id="bfc49-107">Daha fazla bilgi için bkz. [tanımlayıcılar](identifiers-entity-sql.md)</span><span class="sxs-lookup"><span data-stu-id="bfc49-107">For more information see, [Identifiers](identifiers-entity-sql.md)</span></span>  
  
 `expression`  
 <span data-ttu-id="bfc49-108">Türün bildiriminde göründükleri sırada olduğu varsayılacak olan türün öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="bfc49-108">Attributes of the type that are assumed to be in the same order as they appear in the declaration of the type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bfc49-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="bfc49-109">Return Value</span></span>  
 <span data-ttu-id="bfc49-110">Adlandırılmış karmaşık türlerin örnekleri ve varlık türleri.</span><span class="sxs-lookup"><span data-stu-id="bfc49-110">Instances of named complex types and entity types.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bfc49-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bfc49-111">Remarks</span></span>  
 <span data-ttu-id="bfc49-112">Aşağıdaki örneklerde nominal ve karmaşık türlerin nasıl oluşturulacağı gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="bfc49-112">The following examples show how to construct nominal and complex types:</span></span>  
  
 <span data-ttu-id="bfc49-113">Aşağıdaki ifade bir `Person` türün örneğini oluşturur:</span><span class="sxs-lookup"><span data-stu-id="bfc49-113">The expression below creates an instance of a `Person` type:</span></span>  
  
 `Person("abc", 12)`  
  
 <span data-ttu-id="bfc49-114">Aşağıdaki ifade, karmaşık bir türün bir örneğini oluşturur:</span><span class="sxs-lookup"><span data-stu-id="bfc49-114">The expression below creates an instance of a complex type:</span></span>  
  
 `MyModel.ZipCode(‘98118’, ‘4567’)`  
  
 <span data-ttu-id="bfc49-115">Aşağıdaki ifade, iç içe geçmiş karmaşık türün bir örneğini oluşturur:</span><span class="sxs-lookup"><span data-stu-id="bfc49-115">The expression below creates an instance of a nested complex type:</span></span>  
  
 `MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567'))`  
  
 <span data-ttu-id="bfc49-116">Aşağıdaki ifade, iç içe geçmiş karmaşık türe sahip bir varlığın örneğini oluşturur:</span><span class="sxs-lookup"><span data-stu-id="bfc49-116">The expression below creates an instance of an entity with a nested complex type:</span></span>  
  
 `MyModel.Person("Bill", MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567')))`  
  
 <span data-ttu-id="bfc49-117">Aşağıdaki örnek, bir karmaşık türün özelliğinin null olarak nasıl başlatılacağını göstermektedir:`MyModel.ZipCode(‘98118’, null)`</span><span class="sxs-lookup"><span data-stu-id="bfc49-117">The following example shows how to initialize a property of a complex type to null:`MyModel.ZipCode(‘98118’, null)`</span></span>  
  
## <a name="example"></a><span data-ttu-id="bfc49-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="bfc49-118">Example</span></span>  
 <span data-ttu-id="bfc49-119">Aşağıdaki Entity SQL sorgusu, kavramsal model türünün bir örneğini oluşturmak için adlandırılmış tür oluşturucusunu kullanır.</span><span class="sxs-lookup"><span data-stu-id="bfc49-119">The following Entity SQL query uses the named type constructor to create an instance of a conceptual model type.</span></span> <span data-ttu-id="bfc49-120">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="bfc49-120">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="bfc49-121">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="bfc49-121">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="bfc49-122">[Aşağıdaki adımları uygulayın: StructuralType sonuçları](../how-to-execute-a-query-that-returns-structuraltype-results.md)döndüren bir sorgu yürütün.</span><span class="sxs-lookup"><span data-stu-id="bfc49-122">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="bfc49-123">Aşağıdaki sorguyu `ExecuteStructuralTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:</span><span class="sxs-lookup"><span data-stu-id="bfc49-123">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#NAMED_TYPE_CONSTRUCTOR](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#named_type_constructor)]  
  
## <a name="see-also"></a><span data-ttu-id="bfc49-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bfc49-124">See also</span></span>

- [<span data-ttu-id="bfc49-125">Oluşturma Türleri</span><span class="sxs-lookup"><span data-stu-id="bfc49-125">Constructing Types</span></span>](constructing-types-entity-sql.md)
- [<span data-ttu-id="bfc49-126">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="bfc49-126">Entity SQL Reference</span></span>](entity-sql-reference.md)
