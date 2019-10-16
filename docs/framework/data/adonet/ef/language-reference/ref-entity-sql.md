---
title: REF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c5f4cb35-69e9-44cc-b63b-ee38922bbda1
ms.openlocfilehash: 08bcaad4fdc0cf5324ff9976fcf48c23b206e72f
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319389"
---
# <a name="ref-entity-sql"></a><span data-ttu-id="cd902-102">REF (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="cd902-102">REF (Entity SQL)</span></span>
<span data-ttu-id="cd902-103">Bir varlık örneğine bir başvuru döndürür.</span><span class="sxs-lookup"><span data-stu-id="cd902-103">Returns a reference to an entity instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd902-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cd902-104">Syntax</span></span>  
  
```sql  
REF( expression )   
```  
  
## <a name="arguments"></a><span data-ttu-id="cd902-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="cd902-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="cd902-106">Bir varlık türünün örneğini veren geçerli bir ifade.</span><span class="sxs-lookup"><span data-stu-id="cd902-106">Any valid expression that yields an instance of an entity type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cd902-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="cd902-107">Return Value</span></span>  
 <span data-ttu-id="cd902-108">Belirtilen varlık örneğine bir başvuru.</span><span class="sxs-lookup"><span data-stu-id="cd902-108">A reference to the specified entity instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cd902-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cd902-109">Remarks</span></span>  
 <span data-ttu-id="cd902-110">Bir varlık başvurusu, Varlık anahtarından ve bir varlık kümesi adından oluşur.</span><span class="sxs-lookup"><span data-stu-id="cd902-110">An entity reference consists of the entity key and an entity set name.</span></span> <span data-ttu-id="cd902-111">Farklı varlık kümeleri aynı varlık türünü temel alan için, belirli bir varlık anahtarı birden fazla varlık kümesinde görünebilir.</span><span class="sxs-lookup"><span data-stu-id="cd902-111">Because different entity sets can be based on the same entity type, a particular entity key can appear in multiple entity sets.</span></span> <span data-ttu-id="cd902-112">Ancak, bir varlık başvurusu her zaman benzersizdir.</span><span class="sxs-lookup"><span data-stu-id="cd902-112">However, an entity reference is always unique.</span></span> <span data-ttu-id="cd902-113">Giriş ifadesi kalıcı bir varlığı temsil ediyorsa, bu varlığa yönelik bir başvuru döndürülür.</span><span class="sxs-lookup"><span data-stu-id="cd902-113">If the input expression represents a persisted entity, a reference to this entity will be returned.</span></span> <span data-ttu-id="cd902-114">Giriş ifadesi kalıcı olmayan bir varlık değilse, null bir başvuru döndürülür.</span><span class="sxs-lookup"><span data-stu-id="cd902-114">If the input expression is not a persisted entity, a null reference will be returned.</span></span>  
  
 <span data-ttu-id="cd902-115">Özellik ayıklama işleci (.) bir varlığın bir özelliğine erişmek için kullanılırsa, başvuru otomatik olarak başvuru yapılır.</span><span class="sxs-lookup"><span data-stu-id="cd902-115">If the property extraction operator (.) is used to access a property of an entity, the reference is automatically dereferenced.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd902-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="cd902-116">Example</span></span>  
 <span data-ttu-id="cd902-117">Aşağıdaki Entity SQL sorgusu, bir giriş varlığı bağımsız değişkeninin başvurusunu döndürmek için REF işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="cd902-117">The following Entity SQL query uses the REF operator to return the reference for an input entity argument.</span></span> <span data-ttu-id="cd902-118">Ürün varlığının bir özelliğine erişmek için bir özellik ayıklama işlemi (.) kullandığından aynı sorgu başvurunun başvurusunu kaldırır.</span><span class="sxs-lookup"><span data-stu-id="cd902-118">The same query dereferences the reference because we are using a property extraction operation (.) to access a property of the Product entity.</span></span> <span data-ttu-id="cd902-119">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="cd902-119">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="cd902-120">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="cd902-120">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="cd902-121">[Nasıl yapılır: PrimitiveType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-primitivetype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="cd902-121">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="cd902-122">Aşağıdaki sorguyu `ExecutePrimitiveTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:</span><span class="sxs-lookup"><span data-stu-id="cd902-122">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#REF](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#ref)]  
  
## <a name="see-also"></a><span data-ttu-id="cd902-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cd902-123">See also</span></span>

- [<span data-ttu-id="cd902-124">DEREF</span><span class="sxs-lookup"><span data-stu-id="cd902-124">DEREF</span></span>](deref-entity-sql.md)
- [<span data-ttu-id="cd902-125">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="cd902-125">CREATEREF</span></span>](createref-entity-sql.md)
- [<span data-ttu-id="cd902-126">KEY</span><span class="sxs-lookup"><span data-stu-id="cd902-126">KEY</span></span>](key-entity-sql.md)
- [<span data-ttu-id="cd902-127">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="cd902-127">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="cd902-128">Tür Tanımları</span><span class="sxs-lookup"><span data-stu-id="cd902-128">Type Definitions</span></span>](type-definitions-entity-sql.md)
