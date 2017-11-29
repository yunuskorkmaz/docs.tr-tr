---
title: "Sayısal ve Karşılaştırma işleçleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 25b4a26a-06f2-4f80-87a9-76705ed46197
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f77cb612468b401f6aa526e46cc7481d0b47d385
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="numeric-and-comparison-operators"></a><span data-ttu-id="1ed27-102">Sayısal ve Karşılaştırma işleçleri</span><span class="sxs-lookup"><span data-stu-id="1ed27-102">Numeric and Comparison Operators</span></span>
<span data-ttu-id="1ed27-103">Aritmetik ve Karşılaştırma işleçleri ortak dil çalışma zamanı (CLR) gibi beklendiği gibi çalışır:</span><span class="sxs-lookup"><span data-stu-id="1ed27-103">Arithmetic and comparison operators work as expected in the common language runtime (CLR) except as follows:</span></span>  
  
-   <span data-ttu-id="1ed27-104">SQL modulus işleci kayan nokta sayıları üzerinde desteklemez.</span><span class="sxs-lookup"><span data-stu-id="1ed27-104">SQL does not support the modulus operator on floating-point numbers.</span></span>  
  
-   <span data-ttu-id="1ed27-105">SQL denetlenmeyen aritmetik desteklemez.</span><span class="sxs-lookup"><span data-stu-id="1ed27-105">SQL does not support unchecked arithmetic.</span></span>  
  
-   <span data-ttu-id="1ed27-106">SQL'de yinelenemez ve bu nedenle, desteklenmez ifadelerde kullandığınızda artırma ve azaltma işleçleri yan etkileri neden.</span><span class="sxs-lookup"><span data-stu-id="1ed27-106">Increment and decrement operators cause side-effects when you use them in expressions that cannot be replicated in SQL and are, therefore, not supported.</span></span>  
  
## <a name="supported-operators"></a><span data-ttu-id="1ed27-107">Desteklenen işleçleri</span><span class="sxs-lookup"><span data-stu-id="1ed27-107">Supported Operators</span></span>  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="1ed27-108">Aşağıdaki işleçleri destekler.</span><span class="sxs-lookup"><span data-stu-id="1ed27-108"> supports the following operators.</span></span>  
  
-   <span data-ttu-id="1ed27-109">Temel aritmetik işleçler:</span><span class="sxs-lookup"><span data-stu-id="1ed27-109">Basic arithmetic operators:</span></span>  
  
    -   `+`  
  
    -   <span data-ttu-id="1ed27-110">`-`(çıkarma)</span><span class="sxs-lookup"><span data-stu-id="1ed27-110">`-` (subtraction)</span></span>  
  
    -   `*`  
  
    -   `/`  
  
    -   <span data-ttu-id="1ed27-111">Visual Basic tamsayı bölme (`\`)</span><span class="sxs-lookup"><span data-stu-id="1ed27-111">Visual Basic integer division (`\`)</span></span>  
  
    -   <span data-ttu-id="1ed27-112">`%`(Visual Basic `Mod`)</span><span class="sxs-lookup"><span data-stu-id="1ed27-112">`%` (Visual Basic `Mod`)</span></span>  
  
    -   `<<`  
  
    -   `>>`  
  
    -   <span data-ttu-id="1ed27-113">`-`(tekli değilleme)</span><span class="sxs-lookup"><span data-stu-id="1ed27-113">`-` (unary negation)</span></span>  
  
-   <span data-ttu-id="1ed27-114">Temel Karşılaştırma işleçleri:</span><span class="sxs-lookup"><span data-stu-id="1ed27-114">Basic comparison operators:</span></span>  
  
    -   <span data-ttu-id="1ed27-115">Visual Basic `=` ve C#`==`</span><span class="sxs-lookup"><span data-stu-id="1ed27-115">Visual Basic `=` and C# `==`</span></span>  
  
    -   <span data-ttu-id="1ed27-116">Visual Basic `<>` ve C#`!=`</span><span class="sxs-lookup"><span data-stu-id="1ed27-116">Visual Basic `<>` and C# `!=`</span></span>  
  
    -   <span data-ttu-id="1ed27-117">Visual Basic`Is/IsNot`</span><span class="sxs-lookup"><span data-stu-id="1ed27-117">Visual Basic `Is/IsNot`</span></span>  
  
    -   `<`  
  
    -   `<=`  
  
    -   `>`  
  
    -   `>=`  
  
## <a name="see-also"></a><span data-ttu-id="1ed27-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1ed27-118">See Also</span></span>  
 [<span data-ttu-id="1ed27-119">Veri türleri ve işlevleri</span><span class="sxs-lookup"><span data-stu-id="1ed27-119">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)  
 [<span data-ttu-id="1ed27-120">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="1ed27-120">C# Operators</span></span>](http://msdn.microsoft.com/library/0301e31f-22ad-49af-ac3c-d5eae7f0ac43)  
 [<span data-ttu-id="1ed27-121">İşleçler</span><span class="sxs-lookup"><span data-stu-id="1ed27-121">Operators</span></span>](../../../../../visual-basic/language-reference/operators/index.md)
