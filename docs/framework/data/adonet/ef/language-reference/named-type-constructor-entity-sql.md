---
title: Adlandırılmış Tür oluşturucu (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 549dea04-d93d-4c87-a292-f81b1598dbfd
ms.openlocfilehash: 26fb2839f0cc7d645f6ce6daea2d27e35868b63c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59168798"
---
# <a name="named-type-constructor-entity-sql"></a><span data-ttu-id="29cb1-102">Adlandırılmış Tür oluşturucu (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="29cb1-102">Named Type Constructor (Entity SQL)</span></span>
<span data-ttu-id="29cb1-103">Varlık gibi kavramsal model nominal türü veya karmaşık türler örneklerini oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="29cb1-103">Used to create instances of conceptual model nominal types such as Entity or Complex types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29cb1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="29cb1-104">Syntax</span></span>  
  
```  
[{identifier. }] identifier( [expression [{, expression }]] )  
```  
  
## <a name="arguments"></a><span data-ttu-id="29cb1-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="29cb1-105">Arguments</span></span>  
 `identifier`  
 <span data-ttu-id="29cb1-106">Basit veya tırnak işaretli tanımlayıcı değeri.</span><span class="sxs-lookup"><span data-stu-id="29cb1-106">Value that is a simple or quoted identifier.</span></span> <span data-ttu-id="29cb1-107">Daha fazla bilgi edinmek, [tanımlayıcıları](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)</span><span class="sxs-lookup"><span data-stu-id="29cb1-107">For more information see, [Identifiers](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)</span></span>  
  
 `expression`  
 <span data-ttu-id="29cb1-108">Tür bildiriminde göründükleri gibi aynı sırada olduğu varsayılır öznitelikleri türü.</span><span class="sxs-lookup"><span data-stu-id="29cb1-108">Attributes of the type that are assumed to be in the same order as they appear in the declaration of the type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="29cb1-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="29cb1-109">Return Value</span></span>  
 <span data-ttu-id="29cb1-110">Adlandırılmış karmaşık türler ve varlık türleri örnekleri.</span><span class="sxs-lookup"><span data-stu-id="29cb1-110">Instances of named complex types and entity types.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="29cb1-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="29cb1-111">Remarks</span></span>  
 <span data-ttu-id="29cb1-112">Aşağıdaki örnekler, nominal ve karmaşık türler gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="29cb1-112">The following examples show how to construct nominal and complex types:</span></span>  
  
 <span data-ttu-id="29cb1-113">Aşağıdaki ifade bir örneğini oluşturur. bir `Person` türü:</span><span class="sxs-lookup"><span data-stu-id="29cb1-113">The expression below creates an instance of a `Person` type:</span></span>  
  
 `Person("abc", 12)`  
  
 <span data-ttu-id="29cb1-114">Aşağıdaki ifade, karmaşık bir türün örneğini oluşturur:</span><span class="sxs-lookup"><span data-stu-id="29cb1-114">The expression below creates an instance of a complex type:</span></span>  
  
 `MyModel.ZipCode(‘98118’, ‘4567’)`  
  
 <span data-ttu-id="29cb1-115">Aşağıdaki ifade, iç içe geçmiş bir karmaşık tür örneği oluşturur:</span><span class="sxs-lookup"><span data-stu-id="29cb1-115">The expression below creates an instance of a nested complex type:</span></span>  
  
 `MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567'))`  
  
 <span data-ttu-id="29cb1-116">Aşağıdaki ifade ile iç içe geçmiş bir karmaşık türü bir varlık örneği oluşturur:</span><span class="sxs-lookup"><span data-stu-id="29cb1-116">The expression below creates an instance of an entity with a nested complex type:</span></span>  
  
 `MyModel.Person("Bill", MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567')))`  
  
 <span data-ttu-id="29cb1-117">Aşağıdaki örnek, bir karmaşık türü null bir özelliğini başlatmak gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="29cb1-117">The following example shows how to initialize a property of a complex type to null:</span></span>`MyModel.ZipCode(‘98118’, null)`  
  
## <a name="example"></a><span data-ttu-id="29cb1-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="29cb1-118">Example</span></span>  
 <span data-ttu-id="29cb1-119">Aşağıdaki varlık SQL sorgusu adlandırılmış Tür oluşturucu kavramsal model türünün örneğini oluşturmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="29cb1-119">The following Entity SQL query uses the named type constructor to create an instance of a conceptual model type.</span></span> <span data-ttu-id="29cb1-120">Sorgu, AdventureWorks satış modelini temel alıyor.</span><span class="sxs-lookup"><span data-stu-id="29cb1-120">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="29cb1-121">Derleme ve bu sorguyu çalıştırmak için bu adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="29cb1-121">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="29cb1-122">Verilen yordamı izleyin [nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="29cb1-122">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="29cb1-123">Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="29cb1-123">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#NAMED_TYPE_CONSTRUCTOR](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#named_type_constructor)]  
  
## <a name="see-also"></a><span data-ttu-id="29cb1-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="29cb1-124">See also</span></span>

- [<span data-ttu-id="29cb1-125">Oluşturma Türleri</span><span class="sxs-lookup"><span data-stu-id="29cb1-125">Constructing Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)
- [<span data-ttu-id="29cb1-126">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="29cb1-126">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
