---
description: 'Daha fazla bilgi edinin: adlandırılmış tür Oluşturucusu (Entity SQL)'
title: Adlandırılmış tür Oluşturucusu (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 549dea04-d93d-4c87-a292-f81b1598dbfd
ms.openlocfilehash: e5ec811f814898661cf8de28de1fb8406647332d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696548"
---
# <a name="named-type-constructor-entity-sql"></a><span data-ttu-id="0d118-103">Adlandırılmış tür Oluşturucusu (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="0d118-103">Named Type Constructor (Entity SQL)</span></span>

<span data-ttu-id="0d118-104">Varlık veya karmaşık türler gibi kavramsal model nominal türlerin örneklerini oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0d118-104">Used to create instances of conceptual model nominal types such as Entity or Complex types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d118-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="0d118-105">Syntax</span></span>  
  
```sql  
[{identifier. }] identifier( [expression [{, expression }]] )  
```  
  
## <a name="arguments"></a><span data-ttu-id="0d118-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="0d118-106">Arguments</span></span>  

 `identifier`  
 <span data-ttu-id="0d118-107">Basit veya tırnaklı bir tanımlayıcı değeri.</span><span class="sxs-lookup"><span data-stu-id="0d118-107">Value that is a simple or quoted identifier.</span></span> <span data-ttu-id="0d118-108">Daha fazla bilgi için bkz. [tanımlayıcılar](identifiers-entity-sql.md)</span><span class="sxs-lookup"><span data-stu-id="0d118-108">For more information see, [Identifiers](identifiers-entity-sql.md)</span></span>  
  
 `expression`  
 <span data-ttu-id="0d118-109">Türün bildiriminde göründükleri sırada olduğu varsayılacak olan türün öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="0d118-109">Attributes of the type that are assumed to be in the same order as they appear in the declaration of the type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0d118-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0d118-110">Return Value</span></span>  

 <span data-ttu-id="0d118-111">Adlandırılmış karmaşık türlerin örnekleri ve varlık türleri.</span><span class="sxs-lookup"><span data-stu-id="0d118-111">Instances of named complex types and entity types.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0d118-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0d118-112">Remarks</span></span>  

 <span data-ttu-id="0d118-113">Aşağıdaki örneklerde nominal ve karmaşık türlerin nasıl oluşturulacağı gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="0d118-113">The following examples show how to construct nominal and complex types:</span></span>  
  
 <span data-ttu-id="0d118-114">Aşağıdaki ifade bir türün örneğini oluşturur `Person` :</span><span class="sxs-lookup"><span data-stu-id="0d118-114">The expression below creates an instance of a `Person` type:</span></span>  
  
 `Person("abc", 12)`  
  
 <span data-ttu-id="0d118-115">Aşağıdaki ifade, karmaşık bir türün bir örneğini oluşturur:</span><span class="sxs-lookup"><span data-stu-id="0d118-115">The expression below creates an instance of a complex type:</span></span>  
  
 `MyModel.ZipCode(‘98118’, ‘4567’)`  
  
 <span data-ttu-id="0d118-116">Aşağıdaki ifade, iç içe geçmiş karmaşık türün bir örneğini oluşturur:</span><span class="sxs-lookup"><span data-stu-id="0d118-116">The expression below creates an instance of a nested complex type:</span></span>  
  
 `MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567'))`  
  
 <span data-ttu-id="0d118-117">Aşağıdaki ifade, iç içe geçmiş karmaşık türe sahip bir varlığın örneğini oluşturur:</span><span class="sxs-lookup"><span data-stu-id="0d118-117">The expression below creates an instance of an entity with a nested complex type:</span></span>  
  
 `MyModel.Person("Bill", MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567')))`  
  
 <span data-ttu-id="0d118-118">Aşağıdaki örnek, bir karmaşık türün özelliğinin null olarak nasıl başlatılacağını göstermektedir:`MyModel.ZipCode(‘98118’, null)`</span><span class="sxs-lookup"><span data-stu-id="0d118-118">The following example shows how to initialize a property of a complex type to null:`MyModel.ZipCode(‘98118’, null)`</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d118-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="0d118-119">Example</span></span>  

 <span data-ttu-id="0d118-120">Aşağıdaki Entity SQL sorgusu, kavramsal model türünün bir örneğini oluşturmak için adlandırılmış tür oluşturucusunu kullanır.</span><span class="sxs-lookup"><span data-stu-id="0d118-120">The following Entity SQL query uses the named type constructor to create an instance of a conceptual model type.</span></span> <span data-ttu-id="0d118-121">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="0d118-121">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="0d118-122">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="0d118-122">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="0d118-123">[Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="0d118-123">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="0d118-124">Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="0d118-124">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#NAMED_TYPE_CONSTRUCTOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#named_type_constructor)]  
  
## <a name="see-also"></a><span data-ttu-id="0d118-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0d118-125">See also</span></span>

- [<span data-ttu-id="0d118-126">Oluşturma Türleri</span><span class="sxs-lookup"><span data-stu-id="0d118-126">Constructing Types</span></span>](constructing-types-entity-sql.md)
- [<span data-ttu-id="0d118-127">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="0d118-127">Entity SQL Reference</span></span>](entity-sql-reference.md)
