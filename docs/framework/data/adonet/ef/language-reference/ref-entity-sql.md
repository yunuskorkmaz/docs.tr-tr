---
title: REF (Varlık SQL)
ms.date: 03/30/2017
ms.assetid: c5f4cb35-69e9-44cc-b63b-ee38922bbda1
ms.openlocfilehash: 40a5afd7eb99dba7cae8fe14ed0a45213fda94a0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149953"
---
# <a name="ref-entity-sql"></a><span data-ttu-id="c56cb-102">REF (Varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="c56cb-102">REF (Entity SQL)</span></span>
<span data-ttu-id="c56cb-103">Bir varlık örneğine başvuru verir.</span><span class="sxs-lookup"><span data-stu-id="c56cb-103">Returns a reference to an entity instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c56cb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c56cb-104">Syntax</span></span>  
  
```sql  
REF( expression )
```  
  
## <a name="arguments"></a><span data-ttu-id="c56cb-105">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="c56cb-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="c56cb-106">Varlık türü örneği veren geçerli bir ifade.</span><span class="sxs-lookup"><span data-stu-id="c56cb-106">Any valid expression that yields an instance of an entity type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c56cb-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c56cb-107">Return Value</span></span>  
 <span data-ttu-id="c56cb-108">Belirtilen varlık örneğine bir başvuru.</span><span class="sxs-lookup"><span data-stu-id="c56cb-108">A reference to the specified entity instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c56cb-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c56cb-109">Remarks</span></span>  
 <span data-ttu-id="c56cb-110">Varlık başvurusu varlık anahtarı ve varlık kümesi adından oluşur.</span><span class="sxs-lookup"><span data-stu-id="c56cb-110">An entity reference consists of the entity key and an entity set name.</span></span> <span data-ttu-id="c56cb-111">Farklı varlık kümeleri aynı varlık türüne dayalı olabileceğinden, belirli bir varlık anahtarı birden çok varlık kümesinde görünebilir.</span><span class="sxs-lookup"><span data-stu-id="c56cb-111">Because different entity sets can be based on the same entity type, a particular entity key can appear in multiple entity sets.</span></span> <span data-ttu-id="c56cb-112">Ancak, bir varlık başvurusu her zaman benzersizdir.</span><span class="sxs-lookup"><span data-stu-id="c56cb-112">However, an entity reference is always unique.</span></span> <span data-ttu-id="c56cb-113">Giriş ifadesi kalıcı bir varlığı temsil ediyorsa, bu varlığa yapılan bir başvuru döndürülür.</span><span class="sxs-lookup"><span data-stu-id="c56cb-113">If the input expression represents a persisted entity, a reference to this entity will be returned.</span></span> <span data-ttu-id="c56cb-114">Giriş ifadesi kalıcı bir varlık değilse, null başvurusu döndürülür.</span><span class="sxs-lookup"><span data-stu-id="c56cb-114">If the input expression is not a persisted entity, a null reference will be returned.</span></span>  
  
 <span data-ttu-id="c56cb-115">Özellik çıkarma işleci (.) bir varlığın özelliğine erişmek için kullanılırsa, başvuru otomatik olarak başvurudan çıkarılatır.</span><span class="sxs-lookup"><span data-stu-id="c56cb-115">If the property extraction operator (.) is used to access a property of an entity, the reference is automatically dereferenced.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c56cb-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="c56cb-116">Example</span></span>  
 <span data-ttu-id="c56cb-117">Aşağıdaki Entity SQL sorgusu, bir giriş varlık bağımsız değişkeni için başvuruyu döndürmek için REF işleci kullanır.</span><span class="sxs-lookup"><span data-stu-id="c56cb-117">The following Entity SQL query uses the REF operator to return the reference for an input entity argument.</span></span> <span data-ttu-id="c56cb-118">Ürün varlığının bir özelliğine erişmek için bir özellik çıkarma işlemi (.) kullandığımız için aynı sorgu başvuruyu dereferences.</span><span class="sxs-lookup"><span data-stu-id="c56cb-118">The same query dereferences the reference because we are using a property extraction operation (.) to access a property of the Product entity.</span></span> <span data-ttu-id="c56cb-119">Sorgu AdventureWorks Satış Modeli dayanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c56cb-119">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="c56cb-120">Bu sorguyı derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="c56cb-120">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="c56cb-121">[İlkel Tip Sonuçlarını Döndüren Bir Sorguyu Yürütme](../how-to-execute-a-query-that-returns-primitivetype-results.md): Nasıl Yapılır'daki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="c56cb-121">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="c56cb-122">Aşağıdaki sorguyu bağımsız değişken `ExecutePrimitiveTypeQuery` olarak yönteme geçirin:</span><span class="sxs-lookup"><span data-stu-id="c56cb-122">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#REF](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#ref)]  
  
## <a name="see-also"></a><span data-ttu-id="c56cb-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c56cb-123">See also</span></span>

- [<span data-ttu-id="c56cb-124">DEREF</span><span class="sxs-lookup"><span data-stu-id="c56cb-124">DEREF</span></span>](deref-entity-sql.md)
- [<span data-ttu-id="c56cb-125">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="c56cb-125">CREATEREF</span></span>](createref-entity-sql.md)
- [<span data-ttu-id="c56cb-126">Anahtar</span><span class="sxs-lookup"><span data-stu-id="c56cb-126">KEY</span></span>](key-entity-sql.md)
- [<span data-ttu-id="c56cb-127">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="c56cb-127">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="c56cb-128">Tür Tanımları</span><span class="sxs-lookup"><span data-stu-id="c56cb-128">Type Definitions</span></span>](type-definitions-entity-sql.md)
