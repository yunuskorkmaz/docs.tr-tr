---
title: REF (varlık SQL)
ms.date: 03/30/2017
ms.assetid: c5f4cb35-69e9-44cc-b63b-ee38922bbda1
ms.openlocfilehash: 15a78558789ef998d31d704a3fcfbf43dc364757
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54517038"
---
# <a name="ref-entity-sql"></a><span data-ttu-id="a77c3-102">REF (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="a77c3-102">REF (Entity SQL)</span></span>
<span data-ttu-id="a77c3-103">Bir varlık örneği için bir başvuru döndürür.</span><span class="sxs-lookup"><span data-stu-id="a77c3-103">Returns a reference to an entity instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a77c3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a77c3-104">Syntax</span></span>  
  
```  
REF( expression )   
```  
  
## <a name="arguments"></a><span data-ttu-id="a77c3-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="a77c3-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="a77c3-106">Bir varlık türünün bir örneği döndüren herhangi bir geçerli ifade.</span><span class="sxs-lookup"><span data-stu-id="a77c3-106">Any valid expression that yields an instance of an entity type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a77c3-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a77c3-107">Return Value</span></span>  
 <span data-ttu-id="a77c3-108">Belirtilen varlık örneğine başvuru.</span><span class="sxs-lookup"><span data-stu-id="a77c3-108">A reference to the specified entity instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a77c3-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a77c3-109">Remarks</span></span>  
 <span data-ttu-id="a77c3-110">Varlık anahtarı bir varlık başvurusu oluşur ve bir varlık kümesinin adı.</span><span class="sxs-lookup"><span data-stu-id="a77c3-110">An entity reference consists of the entity key and an entity set name.</span></span> <span data-ttu-id="a77c3-111">Farklı varlık kümeleri, aynı varlık türüne göre çünkü bir özel varlık anahtarı birden çok varlık kümelerinde görünebilir.</span><span class="sxs-lookup"><span data-stu-id="a77c3-111">Because different entity sets can be based on the same entity type, a particular entity key can appear in multiple entity sets.</span></span> <span data-ttu-id="a77c3-112">Ancak, bir varlık başvurusu her zaman benzersizdir.</span><span class="sxs-lookup"><span data-stu-id="a77c3-112">However, an entity reference is always unique.</span></span> <span data-ttu-id="a77c3-113">Giriş ifadesi kalıcı bir varlığı temsil ediyorsa, bu varlık için bir başvuru döndürülür.</span><span class="sxs-lookup"><span data-stu-id="a77c3-113">If the input expression represents a persisted entity, a reference to this entity will be returned.</span></span> <span data-ttu-id="a77c3-114">Giriş ifadesi kalıcı bir varlık değil ise, bir null başvurusu döndürülür.</span><span class="sxs-lookup"><span data-stu-id="a77c3-114">If the input expression is not a persisted entity, a null reference will be returned.</span></span>  
  
 <span data-ttu-id="a77c3-115">Özellik çıkarma işleci (.), bir varlığın bir özelliğe erişmek için kullanılır, otomatik olarak başvurusu kaldırılmış bir başvurudur.</span><span class="sxs-lookup"><span data-stu-id="a77c3-115">If the property extraction operator (.) is used to access a property of an entity, the reference is automatically dereferenced.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a77c3-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="a77c3-116">Example</span></span>  
 <span data-ttu-id="a77c3-117">Aşağıdaki varlık SQL sorgusu için giriş varlığı bağımsız değişken başvuru döndürmek için başvuru işleci kullanır.</span><span class="sxs-lookup"><span data-stu-id="a77c3-117">The following Entity SQL query uses the REF operator to return the reference for an input entity argument.</span></span> <span data-ttu-id="a77c3-118">Bir ürün varlığı özelliğine erişmek için bir özelliği ayıklama işlemi (.) kullanıyoruz çünkü aynı sorgu başvuru başvurusunu kaldırır.</span><span class="sxs-lookup"><span data-stu-id="a77c3-118">The same query dereferences the reference because we are using a property extraction operation (.) to access a property of the Product entity.</span></span> <span data-ttu-id="a77c3-119">Sorgu, AdventureWorks satış modelini temel alıyor.</span><span class="sxs-lookup"><span data-stu-id="a77c3-119">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="a77c3-120">Derleme ve bu sorguyu çalıştırmak için bu adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="a77c3-120">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="a77c3-121">Verilen yordamı izleyin [nasıl yapılır: PrimitiveType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="a77c3-121">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="a77c3-122">Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecutePrimitiveTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="a77c3-122">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#REF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#ref)]  
  
## <a name="see-also"></a><span data-ttu-id="a77c3-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a77c3-123">See also</span></span>
- [<span data-ttu-id="a77c3-124">DEREF</span><span class="sxs-lookup"><span data-stu-id="a77c3-124">DEREF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)
- [<span data-ttu-id="a77c3-125">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="a77c3-125">CREATEREF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)
- [<span data-ttu-id="a77c3-126">KEY</span><span class="sxs-lookup"><span data-stu-id="a77c3-126">KEY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)
- [<span data-ttu-id="a77c3-127">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="a77c3-127">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="a77c3-128">Tür Tanımları</span><span class="sxs-lookup"><span data-stu-id="a77c3-128">Type Definitions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/type-definitions-entity-sql.md)
