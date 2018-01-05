---
title: "Bit düzeyinde kurallı işlevleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 993868ca-16e3-47b6-9915-c29cd63b0a21
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: a4311b610859b36f1587e5e3f85e2a5f06503e1d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="bitwise-canonical-functions"></a><span data-ttu-id="e1a43-102">Bit düzeyinde kurallı işlevleri</span><span class="sxs-lookup"><span data-stu-id="e1a43-102">Bitwise Canonical Functions</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="e1a43-103">bit düzeyinde kurallı işlevler içerir.</span><span class="sxs-lookup"><span data-stu-id="e1a43-103"> includes bitwise canonical functions.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e1a43-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e1a43-104">Remarks</span></span>  
 <span data-ttu-id="e1a43-105">Aşağıdaki tabloda bitwise gösterilmektedir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kurallı işlevleri.</span><span class="sxs-lookup"><span data-stu-id="e1a43-105">The following table shows the bitwise [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span> <span data-ttu-id="e1a43-106">Bu işlevler döndürülecek `Null` varsa `Null` giriş sağlanır.</span><span class="sxs-lookup"><span data-stu-id="e1a43-106">These functions will return `Null` if `Null` input is provided.</span></span> <span data-ttu-id="e1a43-107">İşlev dönüş türü, bağımsız değişken türleri ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="e1a43-107">The return type of the functions is the same as the argument type(s).</span></span> <span data-ttu-id="e1a43-108">İşlev birden fazla bağımsız değişkeni alır, bağımsız değişkenleri aynı türde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e1a43-108">Arguments must be of the same type, if the function takes more than one argument.</span></span> <span data-ttu-id="e1a43-109">Farklı türleri arasında bit düzeyinde işlemler gerçekleştirmek için aynı açıkça türe gerekir.</span><span class="sxs-lookup"><span data-stu-id="e1a43-109">To perform bitwise operations across different types, you need to cast to the same type explicitly.</span></span>  
  
|<span data-ttu-id="e1a43-110">İşlev</span><span class="sxs-lookup"><span data-stu-id="e1a43-110">Function</span></span>|<span data-ttu-id="e1a43-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e1a43-111">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="e1a43-112">`BitWiseAnd (` `value1` `,`  `value2` `)`</span><span class="sxs-lookup"><span data-stu-id="e1a43-112">`BitWiseAnd (` `value1` `,`  `value2` `)`</span></span>|<span data-ttu-id="e1a43-113">Bit düzeyinde birlikte, döndürür `value1` ve `value2` türü olarak `value1` ve `value2`.</span><span class="sxs-lookup"><span data-stu-id="e1a43-113">Returns the bitwise conjunction of `value1` and `value2` as the type of `value1` and `value2`.</span></span><br /><br /> <span data-ttu-id="e1a43-114">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="e1a43-114">**Arguments**</span></span><br /><br /> <span data-ttu-id="e1a43-115">A `Byte`, `Int16`, `Int32`, ve `Int64`.</span><span class="sxs-lookup"><span data-stu-id="e1a43-115">A `Byte`, `Int16`, `Int32`, and `Int64`.</span></span><br /><br /> <span data-ttu-id="e1a43-116">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="e1a43-116">**Example**</span></span><br /><br /> `-- The following example returns 1.`<br /><br /> `BitWiseAnd(1,3)`|  
|<span data-ttu-id="e1a43-117">`BitWiseNot (` `value` `)`</span><span class="sxs-lookup"><span data-stu-id="e1a43-117">`BitWiseNot (` `value` `)`</span></span>|<span data-ttu-id="e1a43-118">Bit düzeyinde değilleme işlemi döndürür `value`.</span><span class="sxs-lookup"><span data-stu-id="e1a43-118">Returns the bitwise negation of `value`.</span></span><br /><br /> <span data-ttu-id="e1a43-119">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="e1a43-119">**Arguments**</span></span><br /><br /> <span data-ttu-id="e1a43-120">A `Byte`, `Int16`, `Int32`, ve `Int64`.</span><span class="sxs-lookup"><span data-stu-id="e1a43-120">A `Byte`, `Int16`, `Int32`, and `Int64`.</span></span><br /><br /> <span data-ttu-id="e1a43-121">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="e1a43-121">**Example**</span></span><br /><br /> `-- The following example returns -4.`<br /><br /> `BitWiseNot(3)`|  
|<span data-ttu-id="e1a43-122">`BitWiseOr (` `value1` `,`  `value2` `)`</span><span class="sxs-lookup"><span data-stu-id="e1a43-122">`BitWiseOr (` `value1` `,`  `value2` `)`</span></span>|<span data-ttu-id="e1a43-123">Bit düzeyinde ayrım, döndürür `value1` ve `value2` türü olarak `value1` ve `value2`.</span><span class="sxs-lookup"><span data-stu-id="e1a43-123">Returns the bitwise disjunction of `value1` and `value2` as the type of `value1` and `value2`.</span></span><br /><br /> <span data-ttu-id="e1a43-124">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="e1a43-124">**Arguments**</span></span><br /><br /> <span data-ttu-id="e1a43-125">A `Byte`, `Int16`, `Int32` ve `Int64`.</span><span class="sxs-lookup"><span data-stu-id="e1a43-125">A `Byte`, `Int16`, `Int32` and `Int64`.</span></span><br /><br /> <span data-ttu-id="e1a43-126">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="e1a43-126">**Example**</span></span><br /><br /> `-- The following example returns 3.`<br /><br /> `BitWiseOr(1,3)`|  
|<span data-ttu-id="e1a43-127">`BitWiseXor (` `value1` `,`  `value2` `)`</span><span class="sxs-lookup"><span data-stu-id="e1a43-127">`BitWiseXor (` `value1` `,`  `value2` `)`</span></span>|<span data-ttu-id="e1a43-128">Bit düzeyinde özel ayrım, döndürür `value1` ve `value2` türü olarak `value1` ve `value2`.</span><span class="sxs-lookup"><span data-stu-id="e1a43-128">Returns the bitwise exclusive disjunction of `value1` and `value2` as the type of `value1` and `value2`.</span></span><br /><br /> <span data-ttu-id="e1a43-129">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="e1a43-129">**Arguments**</span></span><br /><br /> <span data-ttu-id="e1a43-130">A `Byte`, `Int16`, `Int32` ve `Int64`.</span><span class="sxs-lookup"><span data-stu-id="e1a43-130">A `Byte`, `Int16`, `Int32` and `Int64`.</span></span><br /><br /> <span data-ttu-id="e1a43-131">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="e1a43-131">**Example**</span></span><br /><br /> `-- The following example returns 2.`<br /><br /> `BitWiseXor (1,3)`|  
  
## <a name="see-also"></a><span data-ttu-id="e1a43-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e1a43-132">See Also</span></span>  
 [<span data-ttu-id="e1a43-133">Kurallı İşlevler</span><span class="sxs-lookup"><span data-stu-id="e1a43-133">Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
