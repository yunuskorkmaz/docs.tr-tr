---
title: "Değişmez değerler ve tür çıkarma (varlık SQL) null"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: edd56afb-af1b-4e7d-b210-cb8998143426
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 5a8b921db06d600430fd4e10466070910119626d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="null-literals-and-type-inference-entity-sql"></a><span data-ttu-id="4cfd7-102">Değişmez değerler ve tür çıkarma (varlık SQL) null</span><span class="sxs-lookup"><span data-stu-id="4cfd7-102">Null Literals and Type Inference (Entity SQL)</span></span>
<span data-ttu-id="4cfd7-103">Null değişmez değerleri herhangi bir türü ile uyumlu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sistem yazın.</span><span class="sxs-lookup"><span data-stu-id="4cfd7-103">Null literals are compatible with any type in the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] type system.</span></span> <span data-ttu-id="4cfd7-104">Ancak, bir null hazır değeri doğru çıkarımı yapılan tür için [!INCLUDE[esql](../../../../../../includes/esql-md.md)] bir null hazır değeri kullanıldığı belirli kısıtlamaları getirir.</span><span class="sxs-lookup"><span data-stu-id="4cfd7-104">However, for the type of a null literal to be inferred correctly, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] imposes certain constraints on where a null literal can be used.</span></span>  
  
## <a name="typed-nulls"></a><span data-ttu-id="4cfd7-105">Tür null</span><span class="sxs-lookup"><span data-stu-id="4cfd7-105">Typed Nulls</span></span>  
 <span data-ttu-id="4cfd7-106">Tür null her yerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4cfd7-106">Typed nulls can be used anywhere.</span></span> <span data-ttu-id="4cfd7-107">Türü bilindiğinden tür çıkarımı tür null için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="4cfd7-107">Type inference is not required for typed nulls because the type is known.</span></span> <span data-ttu-id="4cfd7-108">Örneğin, aşağıdaki Int16 türünde bir null oluşturabileceğiniz [!INCLUDE[esql](../../../../../../includes/esql-md.md)] oluşturun:</span><span class="sxs-lookup"><span data-stu-id="4cfd7-108">For example, you can construct a null of type Int16 with the following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] construct:</span></span>  
  
 `(cast(null as Int16))`  
  
## <a name="free-floating-null-literals"></a><span data-ttu-id="4cfd7-109">Serbest kaydırılan Null değişmez değerleri</span><span class="sxs-lookup"><span data-stu-id="4cfd7-109">Free-Floating Null Literals</span></span>  
 <span data-ttu-id="4cfd7-110">Serbest kaydırılan null değişmez değerleri aşağıdaki bağlamlarında kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="4cfd7-110">Free-floating null literals can be used in the following contexts:</span></span>  
  
-   <span data-ttu-id="4cfd7-111">Bir bağımsız değişkeni bir CAST veya kabul ifadesi.</span><span class="sxs-lookup"><span data-stu-id="4cfd7-111">As an argument to a CAST or TREAT expression.</span></span> <span data-ttu-id="4cfd7-112">Türü belirtilmiş bir null ifadesi üretmek için önerilen yöntem budur.</span><span class="sxs-lookup"><span data-stu-id="4cfd7-112">This is the recommended way to produce a typed null expression.</span></span>  
  
-   <span data-ttu-id="4cfd7-113">Bağımsız değişken olarak bir yöntem veya bir işlev.</span><span class="sxs-lookup"><span data-stu-id="4cfd7-113">As an argument to a method or a function.</span></span> <span data-ttu-id="4cfd7-114">Standart aşırı kurallar geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="4cfd7-114">Standard overload rules apply.</span></span>  
  
-   <span data-ttu-id="4cfd7-115">Gibi aritmetik bir ifade bağımsız değişkenlerinden biri olarak +, -, veya /.</span><span class="sxs-lookup"><span data-stu-id="4cfd7-115">As one of the arguments to an arithmetic expression such as +, -, or /.</span></span> <span data-ttu-id="4cfd7-116">Başka bir bağımsız değişken null değişmez değerleri olamaz, aksi takdirde tür çıkarımı mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="4cfd7-116">The other arguments cannot be null literals, otherwise type inference is not possible.</span></span>  
  
-   <span data-ttu-id="4cfd7-117">Mantıksal bir ifade bağımsız değişkenlerden biri olarak (AND, OR veya değil).</span><span class="sxs-lookup"><span data-stu-id="4cfd7-117">As any of the arguments to a logical expression (AND, OR, or NOT).</span></span> <span data-ttu-id="4cfd7-118">Tüm bağımsız değişkenler, Boolean türünde bilinmektedir.</span><span class="sxs-lookup"><span data-stu-id="4cfd7-118">All the arguments are known to be of type Boolean.</span></span>  
  
-   <span data-ttu-id="4cfd7-119">Bağımsız değişkeni bir IS NULL veya IS NOT NULL ifadesi.</span><span class="sxs-lookup"><span data-stu-id="4cfd7-119">As the argument to an IS NULL or IS NOT NULL expression.</span></span>  
  
-   <span data-ttu-id="4cfd7-120">Bir veya daha fazlası için benzer bir ifade bağımsız.</span><span class="sxs-lookup"><span data-stu-id="4cfd7-120">As one or more of the arguments to a LIKE expression.</span></span> <span data-ttu-id="4cfd7-121">Tüm bağımsız değişkenler dizeleri olması beklenir.</span><span class="sxs-lookup"><span data-stu-id="4cfd7-121">All arguments are expected to be strings.</span></span>  
  
-   <span data-ttu-id="4cfd7-122">Bir veya daha fazla adlı Tür oluşturucu bağımsız.</span><span class="sxs-lookup"><span data-stu-id="4cfd7-122">As one or more of the arguments to a named-type constructor.</span></span>  
  
-   <span data-ttu-id="4cfd7-123">Bir veya daha çok kümeli oluşturucuya bağımsız.</span><span class="sxs-lookup"><span data-stu-id="4cfd7-123">As one or more of the arguments to a multiset constructor.</span></span> <span data-ttu-id="4cfd7-124">Çok kümeli Oluşturucusu en az bir bağımsız değişkeni bir null hazır değeri olmayan bir ifade olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4cfd7-124">At least one argument to the multiset constructor must be an expression that is not a null literal.</span></span>  
  
-   <span data-ttu-id="4cfd7-125">Bir veya daha fazla sonra veya başka bir servis talebi ifadesinde ifadeleri.</span><span class="sxs-lookup"><span data-stu-id="4cfd7-125">As one or more of the THEN or ELSE expressions in a CASE expression.</span></span> <span data-ttu-id="4cfd7-126">SONRA veya başka büyük ifade ifadelerinde en az biri null sabit değer dışında bir ifade olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4cfd7-126">At least one of the THEN or ELSE expressions in the CASE expression must be an expression other than a null literal.</span></span>  
  
 <span data-ttu-id="4cfd7-127">Diğer senaryolarda serbest kaydırılan null değişmez değerler kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="4cfd7-127">Free-floating null literals cannot be used in other scenarios.</span></span> <span data-ttu-id="4cfd7-128">Örneğin, bunlar bir satır oluşturucusunda bağımsız değişken olarak kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="4cfd7-128">For example,  they cannot be used as arguments to a row constructor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cfd7-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4cfd7-129">See Also</span></span>  
 [<span data-ttu-id="4cfd7-130">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="4cfd7-130">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
