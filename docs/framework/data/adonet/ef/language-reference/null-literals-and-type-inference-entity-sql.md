---
title: Null değişmez değerler ve tür çıkarımı (varlık SQL)
ms.date: 03/30/2017
ms.assetid: edd56afb-af1b-4e7d-b210-cb8998143426
ms.openlocfilehash: 22b548f2fc889b20f76a41001438f75c25f99c00
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61760408"
---
# <a name="null-literals-and-type-inference-entity-sql"></a><span data-ttu-id="fc62e-102">Null değişmez değerler ve tür çıkarımı (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="fc62e-102">Null Literals and Type Inference (Entity SQL)</span></span>
<span data-ttu-id="fc62e-103">Null değişmez değerler herhangi bir türü ile uyumlu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tür sistemi.</span><span class="sxs-lookup"><span data-stu-id="fc62e-103">Null literals are compatible with any type in the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] type system.</span></span> <span data-ttu-id="fc62e-104">Ancak, doğru bir şekilde çıkarılan bir null sabit değer türü için [!INCLUDE[esql](../../../../../../includes/esql-md.md)] üzerinde bir null sabit değer kullanıldığı bazı kısıtlamalar getirir.</span><span class="sxs-lookup"><span data-stu-id="fc62e-104">However, for the type of a null literal to be inferred correctly, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] imposes certain constraints on where a null literal can be used.</span></span>  
  
## <a name="typed-nulls"></a><span data-ttu-id="fc62e-105">Türü belirlenmiş null</span><span class="sxs-lookup"><span data-stu-id="fc62e-105">Typed Nulls</span></span>  
 <span data-ttu-id="fc62e-106">Türü belirlenmiş null değerlere her yerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fc62e-106">Typed nulls can be used anywhere.</span></span> <span data-ttu-id="fc62e-107">Türü bilinen için tür çıkarımı yazılı null değerler için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="fc62e-107">Type inference is not required for typed nulls because the type is known.</span></span> <span data-ttu-id="fc62e-108">Örneğin, aşağıdaki Int16 türü null oluşturabilirsiniz [!INCLUDE[esql](../../../../../../includes/esql-md.md)] oluşturun:</span><span class="sxs-lookup"><span data-stu-id="fc62e-108">For example, you can construct a null of type Int16 with the following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] construct:</span></span>  
  
 `(cast(null as Int16))`  
  
## <a name="free-floating-null-literals"></a><span data-ttu-id="fc62e-109">Takılı Null değişmez değerler</span><span class="sxs-lookup"><span data-stu-id="fc62e-109">Free-Floating Null Literals</span></span>  
 <span data-ttu-id="fc62e-110">Takılı null değişmez değerler, aşağıdaki bağlamlarında kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="fc62e-110">Free-floating null literals can be used in the following contexts:</span></span>  
  
- <span data-ttu-id="fc62e-111">Tür dönüştürme veya kabul ifade bir bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="fc62e-111">As an argument to a CAST or TREAT expression.</span></span> <span data-ttu-id="fc62e-112">Türü belirtilmiş bir null ifadesi oluşturmak için önerilen yöntem budur.</span><span class="sxs-lookup"><span data-stu-id="fc62e-112">This is the recommended way to produce a typed null expression.</span></span>  
  
- <span data-ttu-id="fc62e-113">Bağımsız değişken olarak bir yöntem veya işlev.</span><span class="sxs-lookup"><span data-stu-id="fc62e-113">As an argument to a method or a function.</span></span> <span data-ttu-id="fc62e-114">Standart aşırı kuralları geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="fc62e-114">Standard overload rules apply.</span></span>  
  
- <span data-ttu-id="fc62e-115">Tek bir aritmetik ifade gibi bağımsız değişken olarak +, -, veya /.</span><span class="sxs-lookup"><span data-stu-id="fc62e-115">As one of the arguments to an arithmetic expression such as +, -, or /.</span></span> <span data-ttu-id="fc62e-116">Null değişmez değerler diğer bağımsız değişkenleri olamaz, aksi takdirde tür çıkarımı mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="fc62e-116">The other arguments cannot be null literals, otherwise type inference is not possible.</span></span>  
  
- <span data-ttu-id="fc62e-117">Mantıksal bir ifadeyi bağımsız değişkenlerden biri olarak (AND, OR veya değil).</span><span class="sxs-lookup"><span data-stu-id="fc62e-117">As any of the arguments to a logical expression (AND, OR, or NOT).</span></span> <span data-ttu-id="fc62e-118">Tüm bağımsız değişkenler'Boolean türünde bilinmektedir.</span><span class="sxs-lookup"><span data-stu-id="fc62e-118">All the arguments are known to be of type Boolean.</span></span>  
  
- <span data-ttu-id="fc62e-119">Bağımsız değişken boş veya NULL değil bir ifade.</span><span class="sxs-lookup"><span data-stu-id="fc62e-119">As the argument to an IS NULL or IS NOT NULL expression.</span></span>  
  
- <span data-ttu-id="fc62e-120">Bir veya daha fazla bağımsız değişken gibi bir ifade.</span><span class="sxs-lookup"><span data-stu-id="fc62e-120">As one or more of the arguments to a LIKE expression.</span></span> <span data-ttu-id="fc62e-121">Tüm bağımsız değişkenler, dizeleri olmaları beklenir.</span><span class="sxs-lookup"><span data-stu-id="fc62e-121">All arguments are expected to be strings.</span></span>  
  
- <span data-ttu-id="fc62e-122">Bir veya daha fazla bir adlandırılmış Tür oluşturucu bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="fc62e-122">As one or more of the arguments to a named-type constructor.</span></span>  
  
- <span data-ttu-id="fc62e-123">Bir veya daha fazla multıset oluşturucu bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="fc62e-123">As one or more of the arguments to a multiset constructor.</span></span> <span data-ttu-id="fc62e-124">Multıset Oluşturucu en az bir bağımsız değişkeni null bir sabit değer olmayan bir ifade olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fc62e-124">At least one argument to the multiset constructor must be an expression that is not a null literal.</span></span>  
  
- <span data-ttu-id="fc62e-125">Bir veya daha fazla sonra veya başka bir CASE ifadesi ifadelerinde.</span><span class="sxs-lookup"><span data-stu-id="fc62e-125">As one or more of the THEN or ELSE expressions in a CASE expression.</span></span> <span data-ttu-id="fc62e-126">CASE ifadesi ifadelerinde yoksa daha sonra en az biri null bir sabit değer dışında bir ifade olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fc62e-126">At least one of the THEN or ELSE expressions in the CASE expression must be an expression other than a null literal.</span></span>  
  
 <span data-ttu-id="fc62e-127">Diğer senaryolarda takılı null değişmez değerler kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="fc62e-127">Free-floating null literals cannot be used in other scenarios.</span></span> <span data-ttu-id="fc62e-128">Örneğin, bunlar bir satır oluşturucusunda bağımsız değişken olarak kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="fc62e-128">For example,  they cannot be used as arguments to a row constructor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc62e-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fc62e-129">See also</span></span>

- [<span data-ttu-id="fc62e-130">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="fc62e-130">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
