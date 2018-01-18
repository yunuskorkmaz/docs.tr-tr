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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 1d703b2467d508324f3eb39b822c239484ac1c6e
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="bitwise-canonical-functions"></a><span data-ttu-id="ffe86-102">Bit düzeyinde kurallı işlevleri</span><span class="sxs-lookup"><span data-stu-id="ffe86-102">Bitwise Canonical Functions</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="ffe86-103">bit düzeyinde kurallı işlevler içerir.</span><span class="sxs-lookup"><span data-stu-id="ffe86-103"> includes bitwise canonical functions.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ffe86-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ffe86-104">Remarks</span></span>  
 <span data-ttu-id="ffe86-105">Aşağıdaki tabloda bitwise gösterilmektedir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kurallı işlevleri.</span><span class="sxs-lookup"><span data-stu-id="ffe86-105">The following table shows the bitwise [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span> <span data-ttu-id="ffe86-106">Bu işlevler döndürülecek `Null` varsa `Null` giriş sağlanır.</span><span class="sxs-lookup"><span data-stu-id="ffe86-106">These functions will return `Null` if `Null` input is provided.</span></span> <span data-ttu-id="ffe86-107">İşlev dönüş türü, bağımsız değişken türleri ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="ffe86-107">The return type of the functions is the same as the argument type(s).</span></span> <span data-ttu-id="ffe86-108">İşlev birden fazla bağımsız değişkeni alır, bağımsız değişkenleri aynı türde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ffe86-108">Arguments must be of the same type, if the function takes more than one argument.</span></span> <span data-ttu-id="ffe86-109">Farklı türleri arasında bit düzeyinde işlemler gerçekleştirmek için aynı açıkça türe gerekir.</span><span class="sxs-lookup"><span data-stu-id="ffe86-109">To perform bitwise operations across different types, you need to cast to the same type explicitly.</span></span>  
  
|<span data-ttu-id="ffe86-110">İşlev</span><span class="sxs-lookup"><span data-stu-id="ffe86-110">Function</span></span>|<span data-ttu-id="ffe86-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ffe86-111">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="ffe86-112">`BitWiseAnd (` `value1` `,`  `value2` `)`</span><span class="sxs-lookup"><span data-stu-id="ffe86-112">`BitWiseAnd (` `value1` `,`  `value2` `)`</span></span>|<span data-ttu-id="ffe86-113">Bit düzeyinde birlikte, döndürür `value1` ve `value2` türü olarak `value1` ve `value2`.</span><span class="sxs-lookup"><span data-stu-id="ffe86-113">Returns the bitwise conjunction of `value1` and `value2` as the type of `value1` and `value2`.</span></span><br /><br /> <span data-ttu-id="ffe86-114">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="ffe86-114">**Arguments**</span></span><br /><br /> <span data-ttu-id="ffe86-115">A `Byte`, `Int16`, `Int32`, ve `Int64`.</span><span class="sxs-lookup"><span data-stu-id="ffe86-115">A `Byte`, `Int16`, `Int32`, and `Int64`.</span></span><br /><br /> <span data-ttu-id="ffe86-116">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="ffe86-116">**Example**</span></span><br /><br /> `-- The following example returns 1.`<br /><br /> `BitWiseAnd(1,3)`|  
|<span data-ttu-id="ffe86-117">`BitWiseNot (` `value` `)`</span><span class="sxs-lookup"><span data-stu-id="ffe86-117">`BitWiseNot (` `value` `)`</span></span>|<span data-ttu-id="ffe86-118">Bit düzeyinde değilleme işlemi döndürür `value`.</span><span class="sxs-lookup"><span data-stu-id="ffe86-118">Returns the bitwise negation of `value`.</span></span><br /><br /> <span data-ttu-id="ffe86-119">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="ffe86-119">**Arguments**</span></span><br /><br /> <span data-ttu-id="ffe86-120">A `Byte`, `Int16`, `Int32`, ve `Int64`.</span><span class="sxs-lookup"><span data-stu-id="ffe86-120">A `Byte`, `Int16`, `Int32`, and `Int64`.</span></span><br /><br /> <span data-ttu-id="ffe86-121">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="ffe86-121">**Example**</span></span><br /><br /> `-- The following example returns -4.`<br /><br /> `BitWiseNot(3)`|  
|<span data-ttu-id="ffe86-122">`BitWiseOr (` `value1` `,`  `value2` `)`</span><span class="sxs-lookup"><span data-stu-id="ffe86-122">`BitWiseOr (` `value1` `,`  `value2` `)`</span></span>|<span data-ttu-id="ffe86-123">Bit düzeyinde ayrım, döndürür `value1` ve `value2` türü olarak `value1` ve `value2`.</span><span class="sxs-lookup"><span data-stu-id="ffe86-123">Returns the bitwise disjunction of `value1` and `value2` as the type of `value1` and `value2`.</span></span><br /><br /> <span data-ttu-id="ffe86-124">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="ffe86-124">**Arguments**</span></span><br /><br /> <span data-ttu-id="ffe86-125">A `Byte`, `Int16`, `Int32` ve `Int64`.</span><span class="sxs-lookup"><span data-stu-id="ffe86-125">A `Byte`, `Int16`, `Int32` and `Int64`.</span></span><br /><br /> <span data-ttu-id="ffe86-126">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="ffe86-126">**Example**</span></span><br /><br /> `-- The following example returns 3.`<br /><br /> `BitWiseOr(1,3)`|  
|<span data-ttu-id="ffe86-127">`BitWiseXor (` `value1` `,`  `value2` `)`</span><span class="sxs-lookup"><span data-stu-id="ffe86-127">`BitWiseXor (` `value1` `,`  `value2` `)`</span></span>|<span data-ttu-id="ffe86-128">Bit düzeyinde özel ayrım, döndürür `value1` ve `value2` türü olarak `value1` ve `value2`.</span><span class="sxs-lookup"><span data-stu-id="ffe86-128">Returns the bitwise exclusive disjunction of `value1` and `value2` as the type of `value1` and `value2`.</span></span><br /><br /> <span data-ttu-id="ffe86-129">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="ffe86-129">**Arguments**</span></span><br /><br /> <span data-ttu-id="ffe86-130">A `Byte`, `Int16`, `Int32` ve `Int64`.</span><span class="sxs-lookup"><span data-stu-id="ffe86-130">A `Byte`, `Int16`, `Int32` and `Int64`.</span></span><br /><br /> <span data-ttu-id="ffe86-131">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="ffe86-131">**Example**</span></span><br /><br /> `-- The following example returns 2.`<br /><br /> `BitWiseXor (1,3)`|  
  
## <a name="see-also"></a><span data-ttu-id="ffe86-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ffe86-132">See Also</span></span>  
 [<span data-ttu-id="ffe86-133">Kurallı İşlevler</span><span class="sxs-lookup"><span data-stu-id="ffe86-133">Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
