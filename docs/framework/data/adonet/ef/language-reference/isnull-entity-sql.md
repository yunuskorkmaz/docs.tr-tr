---
title: ISNULL (Entity SQL)
ms.date: 03/30/2017
ms.assetid: dc7a0173-3664-4c90-a57b-5cbb0a8ed7ee
ms.openlocfilehash: 9066f9fb68ce2c50e9523881cfa0dd930cd0b52e
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319726"
---
# <a name="isnull-entity-sql"></a><span data-ttu-id="da361-102">ISNULL (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="da361-102">ISNULL (Entity SQL)</span></span>
<span data-ttu-id="da361-103">Sorgu ifadesinin null olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="da361-103">Determines if a query expression is null.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da361-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="da361-104">Syntax</span></span>  
  
```sql  
expression IS [ NOT ] NULL  
```  
  
## <a name="arguments"></a><span data-ttu-id="da361-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="da361-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="da361-106">Herhangi bir geçerli sorgu ifadesi.</span><span class="sxs-lookup"><span data-stu-id="da361-106">Any valid query expression.</span></span> <span data-ttu-id="da361-107">Koleksiyon, koleksiyon üyeleri veya koleksiyon türü özellikleri olan bir kayıt türü olamaz.</span><span class="sxs-lookup"><span data-stu-id="da361-107">Cannot be a collection, have collection members, or a record type with collection type properties.</span></span>  
  
 <span data-ttu-id="da361-108">BAŞLATıLMADı</span><span class="sxs-lookup"><span data-stu-id="da361-108">NOT</span></span>  
 <span data-ttu-id="da361-109">EDM 'yi geçersiz kılar. Boolean sonucu NULL.</span><span class="sxs-lookup"><span data-stu-id="da361-109">Negates the EDM.Boolean result of IS NULL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="da361-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="da361-110">Return Value</span></span>  
 <span data-ttu-id="da361-111">`expression` null döndürürse `true`; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="da361-111">`true` if `expression` returns null; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="da361-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="da361-112">Remarks</span></span>  
 <span data-ttu-id="da361-113">Dış birleştirmenin öğesinin null olup olmadığını anlamak için `IS NULL` kullanın:</span><span class="sxs-lookup"><span data-stu-id="da361-113">Use `IS NULL` to determine if the element of an outer join is null:</span></span>  
  
```sql  
select c   
      from LOB.Customers as c left outer join LOB.Orders as o   
                              on c.ID = o.CustomerID    
      where o is not null and o.OrderQuantity = @x  
```  
  
 <span data-ttu-id="da361-114">Üyenin gerçek bir değere sahip olup olmadığını anlamak için `IS NULL` kullanın:</span><span class="sxs-lookup"><span data-stu-id="da361-114">Use `IS NULL` to determine if a member has an actual value:</span></span>  
  
```sql  
select c from LOB.Customer as c where c.DOB is not null  
```  
  
 <span data-ttu-id="da361-115">Aşağıdaki tabloda bazı desenlerdeki `IS NULL` ' ın davranışı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="da361-115">The following table shows the behavior of `IS NULL` over some patterns.</span></span> <span data-ttu-id="da361-116">Sağlayıcı çağrılmadan önce istemci tarafında tüm özel durumlar atılır:</span><span class="sxs-lookup"><span data-stu-id="da361-116">All exceptions are thrown from the client side before the provider gets invoked:</span></span>  
  
|<span data-ttu-id="da361-117">Desen</span><span class="sxs-lookup"><span data-stu-id="da361-117">Pattern</span></span>|<span data-ttu-id="da361-118">Davranış</span><span class="sxs-lookup"><span data-stu-id="da361-118">Behavior</span></span>|  
|-------------|--------------|  
|<span data-ttu-id="da361-119">NULL NULL</span><span class="sxs-lookup"><span data-stu-id="da361-119">null IS NULL</span></span>|<span data-ttu-id="da361-120">@No__t-0 döndürür.</span><span class="sxs-lookup"><span data-stu-id="da361-120">Returns `true`.</span></span>|  
|<span data-ttu-id="da361-121">DAVRAN (EntityType olarak null) NULL</span><span class="sxs-lookup"><span data-stu-id="da361-121">TREAT (null AS EntityType) IS NULL</span></span>|<span data-ttu-id="da361-122">@No__t-0 döndürür.</span><span class="sxs-lookup"><span data-stu-id="da361-122">Returns `true`.</span></span>|  
|<span data-ttu-id="da361-123">DAVRAN (ComplexType olarak null) NULL</span><span class="sxs-lookup"><span data-stu-id="da361-123">TREAT (null AS ComplexType) IS NULL</span></span>|<span data-ttu-id="da361-124">Bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="da361-124">Throws an error.</span></span>|  
|<span data-ttu-id="da361-125">DEĞERLENDIRIN (RowType olarak null) NULL</span><span class="sxs-lookup"><span data-stu-id="da361-125">TREAT (null AS RowType) IS NULL</span></span>|<span data-ttu-id="da361-126">Bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="da361-126">Throws an error.</span></span>|  
|<span data-ttu-id="da361-127">EntityType NULL</span><span class="sxs-lookup"><span data-stu-id="da361-127">EntityType IS NULL</span></span>|<span data-ttu-id="da361-128">@No__t-0 veya `false` döndürür.</span><span class="sxs-lookup"><span data-stu-id="da361-128">Returns `true` or `false`.</span></span>|  
|<span data-ttu-id="da361-129">ComplexType NULL</span><span class="sxs-lookup"><span data-stu-id="da361-129">ComplexType IS NULL</span></span>|<span data-ttu-id="da361-130">Bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="da361-130">Throws an error.</span></span>|  
|<span data-ttu-id="da361-131">RowType NULL</span><span class="sxs-lookup"><span data-stu-id="da361-131">RowType IS NULL</span></span>|<span data-ttu-id="da361-132">Bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="da361-132">Throws an error.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="da361-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="da361-133">Example</span></span>  
 <span data-ttu-id="da361-134">Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgusu, bir sorgu ifadesinin null olmadığını anlamak için NULL işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="da361-134">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the IS NOT NULL operator to determine if a query expression is not null.</span></span> <span data-ttu-id="da361-135">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="da361-135">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="da361-136">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="da361-136">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="da361-137">[Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="da361-137">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="da361-138">Aşağıdaki sorguyu `ExecuteStructuralTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:</span><span class="sxs-lookup"><span data-stu-id="da361-138">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#ISNULL](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#isnull)]  
  
## <a name="see-also"></a><span data-ttu-id="da361-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="da361-139">See also</span></span>

- [<span data-ttu-id="da361-140">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="da361-140">Entity SQL Reference</span></span>](entity-sql-reference.md)
