---
title: IsNull (varlık SQL)
ms.date: 03/30/2017
ms.assetid: dc7a0173-3664-4c90-a57b-5cbb0a8ed7ee
ms.openlocfilehash: aaecce3ff74d64b8e07b31329ced5b5e581fca5b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59295100"
---
# <a name="isnull-entity-sql"></a><span data-ttu-id="8a10c-102">IsNull (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="8a10c-102">ISNULL (Entity SQL)</span></span>
<span data-ttu-id="8a10c-103">Sorgu ifadesi null olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="8a10c-103">Determines if a query expression is null.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a10c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8a10c-104">Syntax</span></span>  
  
```  
expression IS [ NOT ] NULL  
```  
  
## <a name="arguments"></a><span data-ttu-id="8a10c-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="8a10c-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="8a10c-106">Herhangi bir geçerli ifade.</span><span class="sxs-lookup"><span data-stu-id="8a10c-106">Any valid query expression.</span></span> <span data-ttu-id="8a10c-107">Olamaz, bir koleksiyon, koleksiyon üyeleri veya bir kayıt türü ile toplama türü özellikleri vardır.</span><span class="sxs-lookup"><span data-stu-id="8a10c-107">Cannot be a collection, have collection members, or a record type with collection type properties.</span></span>  
  
 <span data-ttu-id="8a10c-108">DEĞİL</span><span class="sxs-lookup"><span data-stu-id="8a10c-108">NOT</span></span>  
 <span data-ttu-id="8a10c-109">EDM olumsuz duruma getirir. IS NULL, Boolean sonucu.</span><span class="sxs-lookup"><span data-stu-id="8a10c-109">Negates the EDM.Boolean result of IS NULL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8a10c-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8a10c-110">Return Value</span></span>  
 <span data-ttu-id="8a10c-111">`true` varsa `expression` döndürür, aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="8a10c-111">`true` if `expression` returns null; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8a10c-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8a10c-112">Remarks</span></span>  
 <span data-ttu-id="8a10c-113">Kullanım `IS NULL` dış birleşim öğesinin boş olup olmadığını belirlemek için:</span><span class="sxs-lookup"><span data-stu-id="8a10c-113">Use `IS NULL` to determine if the element of an outer join is null:</span></span>  
  
```  
select c   
      from LOB.Customers as c left outer join LOB.Orders as o   
                              on c.ID = o.CustomerID    
      where o is not null and o.OrderQuantity = @x  
```  
  
 <span data-ttu-id="8a10c-114">Kullanım `IS NULL` üyesi gerçek bir değer olup olmadığını belirlemek için:</span><span class="sxs-lookup"><span data-stu-id="8a10c-114">Use `IS NULL` to determine if a member has an actual value:</span></span>  
  
```  
select c from LOB.Customer as c where c.DOB is not null  
```  
  
 <span data-ttu-id="8a10c-115">Aşağıdaki tabloda davranışını gösteren `IS NULL` bazı desenleri üzerinden.</span><span class="sxs-lookup"><span data-stu-id="8a10c-115">The following table shows the behavior of `IS NULL` over some patterns.</span></span> <span data-ttu-id="8a10c-116">Sağlayıcı çağrılır önce tüm istemci tarafında özel durumlar:</span><span class="sxs-lookup"><span data-stu-id="8a10c-116">All exceptions are thrown from the client side before the provider gets invoked:</span></span>  
  
|<span data-ttu-id="8a10c-117">Desen</span><span class="sxs-lookup"><span data-stu-id="8a10c-117">Pattern</span></span>|<span data-ttu-id="8a10c-118">Davranış</span><span class="sxs-lookup"><span data-stu-id="8a10c-118">Behavior</span></span>|  
|-------------|--------------|  
|<span data-ttu-id="8a10c-119">Is Null NULL</span><span class="sxs-lookup"><span data-stu-id="8a10c-119">null IS NULL</span></span>|<span data-ttu-id="8a10c-120">Döndürür `true`.</span><span class="sxs-lookup"><span data-stu-id="8a10c-120">Returns `true`.</span></span>|  
|<span data-ttu-id="8a10c-121">IS NULL DAVRANMA (null AS EntityType)</span><span class="sxs-lookup"><span data-stu-id="8a10c-121">TREAT (null AS EntityType) IS NULL</span></span>|<span data-ttu-id="8a10c-122">Döndürür `true`.</span><span class="sxs-lookup"><span data-stu-id="8a10c-122">Returns `true`.</span></span>|  
|<span data-ttu-id="8a10c-123">IS NULL DAVRANMA (null AS ComplexType)</span><span class="sxs-lookup"><span data-stu-id="8a10c-123">TREAT (null AS ComplexType) IS NULL</span></span>|<span data-ttu-id="8a10c-124">Bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8a10c-124">Throws an error.</span></span>|  
|<span data-ttu-id="8a10c-125">IS NULL DAVRANMA (null AS RowType)</span><span class="sxs-lookup"><span data-stu-id="8a10c-125">TREAT (null AS RowType) IS NULL</span></span>|<span data-ttu-id="8a10c-126">Bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8a10c-126">Throws an error.</span></span>|  
|<span data-ttu-id="8a10c-127">EntityType IS NULL</span><span class="sxs-lookup"><span data-stu-id="8a10c-127">EntityType IS NULL</span></span>|<span data-ttu-id="8a10c-128">Döndürür `true` veya `false`.</span><span class="sxs-lookup"><span data-stu-id="8a10c-128">Returns `true` or `false`.</span></span>|  
|<span data-ttu-id="8a10c-129">ComplexType null</span><span class="sxs-lookup"><span data-stu-id="8a10c-129">ComplexType IS NULL</span></span>|<span data-ttu-id="8a10c-130">Bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8a10c-130">Throws an error.</span></span>|  
|<span data-ttu-id="8a10c-131">RowType IS NULL</span><span class="sxs-lookup"><span data-stu-id="8a10c-131">RowType IS NULL</span></span>|<span data-ttu-id="8a10c-132">Bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8a10c-132">Throws an error.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="8a10c-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="8a10c-133">Example</span></span>  
 <span data-ttu-id="8a10c-134">Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu IS NOT NULL işleci bir sorgu ifadesi null değilse belirlemek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="8a10c-134">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the IS NOT NULL operator to determine if a query expression is not null.</span></span> <span data-ttu-id="8a10c-135">Sorgu, AdventureWorks satış modelini temel alıyor.</span><span class="sxs-lookup"><span data-stu-id="8a10c-135">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="8a10c-136">Derleme ve bu sorguyu çalıştırmak için bu adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="8a10c-136">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="8a10c-137">Verilen yordamı izleyin [nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="8a10c-137">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="8a10c-138">Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="8a10c-138">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#ISNULL](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#isnull)]  
  
## <a name="see-also"></a><span data-ttu-id="8a10c-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8a10c-139">See also</span></span>

- [<span data-ttu-id="8a10c-140">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="8a10c-140">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
