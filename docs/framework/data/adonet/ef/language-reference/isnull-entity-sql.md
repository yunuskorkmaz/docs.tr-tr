---
title: IsNull (varlık SQL)
ms.date: 03/30/2017
ms.assetid: dc7a0173-3664-4c90-a57b-5cbb0a8ed7ee
ms.openlocfilehash: 894d3ab91623aa4246bf7735fb1b7d04e066825a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59072642"
---
# <a name="isnull-entity-sql"></a><span data-ttu-id="39cfa-102">IsNull (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="39cfa-102">ISNULL (Entity SQL)</span></span>
<span data-ttu-id="39cfa-103">Sorgu ifadesi null olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="39cfa-103">Determines if a query expression is null.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39cfa-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="39cfa-104">Syntax</span></span>  
  
```  
expression IS [ NOT ] NULL  
```  
  
## <a name="arguments"></a><span data-ttu-id="39cfa-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="39cfa-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="39cfa-106">Herhangi bir geçerli ifade.</span><span class="sxs-lookup"><span data-stu-id="39cfa-106">Any valid query expression.</span></span> <span data-ttu-id="39cfa-107">Olamaz, bir koleksiyon, koleksiyon üyeleri veya bir kayıt türü ile toplama türü özellikleri vardır.</span><span class="sxs-lookup"><span data-stu-id="39cfa-107">Cannot be a collection, have collection members, or a record type with collection type properties.</span></span>  
  
 <span data-ttu-id="39cfa-108">DEĞİL</span><span class="sxs-lookup"><span data-stu-id="39cfa-108">NOT</span></span>  
 <span data-ttu-id="39cfa-109">EDM olumsuz duruma getirir. IS NULL, Boolean sonucu.</span><span class="sxs-lookup"><span data-stu-id="39cfa-109">Negates the EDM.Boolean result of IS NULL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="39cfa-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="39cfa-110">Return Value</span></span>  
 `true` <span data-ttu-id="39cfa-111">varsa `expression` döndürür, aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="39cfa-111">if `expression` returns null; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="39cfa-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="39cfa-112">Remarks</span></span>  
 <span data-ttu-id="39cfa-113">Kullanım `IS NULL` dış birleşim öğesinin boş olup olmadığını belirlemek için:</span><span class="sxs-lookup"><span data-stu-id="39cfa-113">Use `IS NULL` to determine if the element of an outer join is null:</span></span>  
  
```  
select c   
      from LOB.Customers as c left outer join LOB.Orders as o   
                              on c.ID = o.CustomerID    
      where o is not null and o.OrderQuantity = @x  
```  
  
 <span data-ttu-id="39cfa-114">Kullanım `IS NULL` üyesi gerçek bir değer olup olmadığını belirlemek için:</span><span class="sxs-lookup"><span data-stu-id="39cfa-114">Use `IS NULL` to determine if a member has an actual value:</span></span>  
  
```  
select c from LOB.Customer as c where c.DOB is not null  
```  
  
 <span data-ttu-id="39cfa-115">Aşağıdaki tabloda davranışını gösteren `IS NULL` bazı desenleri üzerinden.</span><span class="sxs-lookup"><span data-stu-id="39cfa-115">The following table shows the behavior of `IS NULL` over some patterns.</span></span> <span data-ttu-id="39cfa-116">Sağlayıcı çağrılır önce tüm istemci tarafında özel durumlar:</span><span class="sxs-lookup"><span data-stu-id="39cfa-116">All exceptions are thrown from the client side before the provider gets invoked:</span></span>  
  
|<span data-ttu-id="39cfa-117">Desen</span><span class="sxs-lookup"><span data-stu-id="39cfa-117">Pattern</span></span>|<span data-ttu-id="39cfa-118">Davranış</span><span class="sxs-lookup"><span data-stu-id="39cfa-118">Behavior</span></span>|  
|-------------|--------------|  
|<span data-ttu-id="39cfa-119">Is Null NULL</span><span class="sxs-lookup"><span data-stu-id="39cfa-119">null IS NULL</span></span>|<span data-ttu-id="39cfa-120">Döndürür `true`.</span><span class="sxs-lookup"><span data-stu-id="39cfa-120">Returns `true`.</span></span>|  
|<span data-ttu-id="39cfa-121">IS NULL DAVRANMA (null AS EntityType)</span><span class="sxs-lookup"><span data-stu-id="39cfa-121">TREAT (null AS EntityType) IS NULL</span></span>|<span data-ttu-id="39cfa-122">Döndürür `true`.</span><span class="sxs-lookup"><span data-stu-id="39cfa-122">Returns `true`.</span></span>|  
|<span data-ttu-id="39cfa-123">IS NULL DAVRANMA (null AS ComplexType)</span><span class="sxs-lookup"><span data-stu-id="39cfa-123">TREAT (null AS ComplexType) IS NULL</span></span>|<span data-ttu-id="39cfa-124">Bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="39cfa-124">Throws an error.</span></span>|  
|<span data-ttu-id="39cfa-125">IS NULL DAVRANMA (null AS RowType)</span><span class="sxs-lookup"><span data-stu-id="39cfa-125">TREAT (null AS RowType) IS NULL</span></span>|<span data-ttu-id="39cfa-126">Bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="39cfa-126">Throws an error.</span></span>|  
|<span data-ttu-id="39cfa-127">EntityType IS NULL</span><span class="sxs-lookup"><span data-stu-id="39cfa-127">EntityType IS NULL</span></span>|<span data-ttu-id="39cfa-128">Döndürür `true` veya `false`.</span><span class="sxs-lookup"><span data-stu-id="39cfa-128">Returns `true` or `false`.</span></span>|  
|<span data-ttu-id="39cfa-129">ComplexType null</span><span class="sxs-lookup"><span data-stu-id="39cfa-129">ComplexType IS NULL</span></span>|<span data-ttu-id="39cfa-130">Bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="39cfa-130">Throws an error.</span></span>|  
|<span data-ttu-id="39cfa-131">RowType IS NULL</span><span class="sxs-lookup"><span data-stu-id="39cfa-131">RowType IS NULL</span></span>|<span data-ttu-id="39cfa-132">Bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="39cfa-132">Throws an error.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="39cfa-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="39cfa-133">Example</span></span>  
 <span data-ttu-id="39cfa-134">Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu IS NOT NULL işleci bir sorgu ifadesi null değilse belirlemek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="39cfa-134">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the IS NOT NULL operator to determine if a query expression is not null.</span></span> <span data-ttu-id="39cfa-135">Sorgu, AdventureWorks satış modelini temel alıyor.</span><span class="sxs-lookup"><span data-stu-id="39cfa-135">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="39cfa-136">Derleme ve bu sorguyu çalıştırmak için bu adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="39cfa-136">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="39cfa-137">Verilen yordamı izleyin [nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="39cfa-137">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="39cfa-138">Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="39cfa-138">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#ISNULL](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#isnull)]  
  
## <a name="see-also"></a><span data-ttu-id="39cfa-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="39cfa-139">See also</span></span>

- [<span data-ttu-id="39cfa-140">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="39cfa-140">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
