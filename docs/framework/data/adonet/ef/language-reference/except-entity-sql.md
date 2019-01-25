---
title: (Varlık SQL) dışında
ms.date: 03/30/2017
ms.assetid: 69cc23e5-3f8f-4b49-b20e-2f84ff11c80d
ms.openlocfilehash: 1e7ab2c29b6418e86fc1b6f0ed2aad92a18ee7e5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54671323"
---
# <a name="except-entity-sql"></a><span data-ttu-id="b7b46-102">(Varlık SQL) dışında</span><span class="sxs-lookup"><span data-stu-id="b7b46-102">EXCEPT (Entity SQL)</span></span>
<span data-ttu-id="b7b46-103">Ayrıca sorgu ifadesinden EXCEPT işlecinin sağa döndürülmez EXCEPT işlecinin sol sorgu ifadesinden farklı değerleri koleksiyonunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="b7b46-103">Returns a collection of any distinct values from the query expression to the left of the EXCEPT operand that are not also returned from the query expression to the right of the EXCEPT operand.</span></span> <span data-ttu-id="b7b46-104">Tüm ifadeler aynı türde veya ortak bir temel veya türetilmiş tür olarak olmalıdır `expression`.</span><span class="sxs-lookup"><span data-stu-id="b7b46-104">All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7b46-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b7b46-105">Syntax</span></span>  
  
```  
expression EXCEPT expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="b7b46-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="b7b46-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="b7b46-107">Başka bir sorgu ifadesinden döndürülen koleksiyon karşılaştırmak için bir koleksiyon döndürür herhangi bir geçerli ifade.</span><span class="sxs-lookup"><span data-stu-id="b7b46-107">Any valid query expression that returns a collection to compare with the collection returned from another query expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b7b46-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b7b46-108">Return Value</span></span>  
 <span data-ttu-id="b7b46-109">Bir koleksiyonu aynı türde veya ortak bir temel veya türetilmiş tür `expression`.</span><span class="sxs-lookup"><span data-stu-id="b7b46-109">A collection of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b7b46-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b7b46-110">Remarks</span></span>  
 <span data-ttu-id="b7b46-111">DIŞINDA biridir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] işleçleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b7b46-111">EXCEPT is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="b7b46-112">Tüm [!INCLUDE[esql](../../../../../../includes/esql-md.md)] küme işleci soldan sağa doğru değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="b7b46-112">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="b7b46-113">Aşağıdaki tablo önceliği gösterir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] işleçleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b7b46-113">The following table shows the precedence of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span>  
  
|<span data-ttu-id="b7b46-114">Önceliği</span><span class="sxs-lookup"><span data-stu-id="b7b46-114">Precedence</span></span>|<span data-ttu-id="b7b46-115">İşleçler</span><span class="sxs-lookup"><span data-stu-id="b7b46-115">Operators</span></span>|  
|----------------|---------------|  
|<span data-ttu-id="b7b46-116">En yüksek</span><span class="sxs-lookup"><span data-stu-id="b7b46-116">Highest</span></span>|<span data-ttu-id="b7b46-117">INTERSECT</span><span class="sxs-lookup"><span data-stu-id="b7b46-117">INTERSECT</span></span>|  
||<span data-ttu-id="b7b46-118">UNION</span><span class="sxs-lookup"><span data-stu-id="b7b46-118">UNION</span></span><br /><br /> <span data-ttu-id="b7b46-119">UNION ALL</span><span class="sxs-lookup"><span data-stu-id="b7b46-119">UNION ALL</span></span>|  
||<span data-ttu-id="b7b46-120">EXCEPT</span><span class="sxs-lookup"><span data-stu-id="b7b46-120">EXCEPT</span></span>|  
|<span data-ttu-id="b7b46-121">En düşük</span><span class="sxs-lookup"><span data-stu-id="b7b46-121">Lowest</span></span>|<span data-ttu-id="b7b46-122">VAR.</span><span class="sxs-lookup"><span data-stu-id="b7b46-122">EXISTS</span></span><br /><br /> <span data-ttu-id="b7b46-123">ÇAKIŞIYOR</span><span class="sxs-lookup"><span data-stu-id="b7b46-123">OVERLAPS</span></span><br /><br /> <span data-ttu-id="b7b46-124">FLATTEN</span><span class="sxs-lookup"><span data-stu-id="b7b46-124">FLATTEN</span></span><br /><br /> <span data-ttu-id="b7b46-125">AYARLAYIN</span><span class="sxs-lookup"><span data-stu-id="b7b46-125">SET</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b7b46-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="b7b46-126">Example</span></span>  
 <span data-ttu-id="b7b46-127">Aşağıdaki varlık SQL sorgusu EXCEPT işlecinin herhangi ayrı değerler koleksiyonu gelen iki sorgu ifadeleri döndürmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="b7b46-127">The following Entity SQL query uses the EXCEPT operator to return a collection of any distinct values from two query expressions.</span></span> <span data-ttu-id="b7b46-128">Sorgu, AdventureWorks satış modelini temel alıyor.</span><span class="sxs-lookup"><span data-stu-id="b7b46-128">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="b7b46-129">Derleme ve bu sorguyu çalıştırmak için bu adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="b7b46-129">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="b7b46-130">Verilen yordamı izleyin [nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="b7b46-130">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="b7b46-131">Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="b7b46-131">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#EXCEPT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#except)]  
  
## <a name="see-also"></a><span data-ttu-id="b7b46-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b7b46-132">See also</span></span>
- [<span data-ttu-id="b7b46-133">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="b7b46-133">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
