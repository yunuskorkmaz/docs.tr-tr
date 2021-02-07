---
description: 'Daha fazla bilgi edinin: sayısal ve karşılaştırma Işleçleri'
title: Sayısal ve Karşılaştırma İşleçleri
ms.date: 03/30/2017
ms.assetid: 25b4a26a-06f2-4f80-87a9-76705ed46197
ms.openlocfilehash: 5b17f19769436ac4e575ac974668eadc3b17b8f6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99695534"
---
# <a name="numeric-and-comparison-operators"></a><span data-ttu-id="72c36-103">Sayısal ve Karşılaştırma İşleçleri</span><span class="sxs-lookup"><span data-stu-id="72c36-103">Numeric and Comparison Operators</span></span>

<span data-ttu-id="72c36-104">Aritmetik ve karşılaştırma işleçleri, ortak dil çalışma zamanında (CLR) beklenen şekilde aşağıdaki gibi çalışır:</span><span class="sxs-lookup"><span data-stu-id="72c36-104">Arithmetic and comparison operators work as expected in the common language runtime (CLR) except as follows:</span></span>

- <span data-ttu-id="72c36-105">SQL, kayan nokta numaralarında mod işlecini desteklemez.</span><span class="sxs-lookup"><span data-stu-id="72c36-105">SQL does not support the modulus operator on floating-point numbers.</span></span>

- <span data-ttu-id="72c36-106">SQL Denetlenmemiş aritmetiğini desteklemez.</span><span class="sxs-lookup"><span data-stu-id="72c36-106">SQL does not support unchecked arithmetic.</span></span>

- <span data-ttu-id="72c36-107">Artırma ve azaltma işleçleri, SQL 'de çoğaltılabilen ve bu nedenle desteklenmeyen ifadelerde kullandığınızda yan etkilere neden olur.</span><span class="sxs-lookup"><span data-stu-id="72c36-107">Increment and decrement operators cause side-effects when you use them in expressions that cannot be replicated in SQL and are, therefore, not supported.</span></span>

## <a name="supported-operators"></a><span data-ttu-id="72c36-108">Desteklenen Işleçler</span><span class="sxs-lookup"><span data-stu-id="72c36-108">Supported Operators</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="72c36-109">aşağıdaki işleçleri destekler.</span><span class="sxs-lookup"><span data-stu-id="72c36-109">supports the following operators.</span></span>

- <span data-ttu-id="72c36-110">Temel aritmetik işleçler:</span><span class="sxs-lookup"><span data-stu-id="72c36-110">Basic arithmetic operators:</span></span>

  - `+`

  - <span data-ttu-id="72c36-111">`-` strA</span><span class="sxs-lookup"><span data-stu-id="72c36-111">`-` (subtraction)</span></span>

  - `*`

  - `/`

  - <span data-ttu-id="72c36-112">Visual Basic tamsayı bölümü ( `\` )</span><span class="sxs-lookup"><span data-stu-id="72c36-112">Visual Basic integer division (`\`)</span></span>

  - <span data-ttu-id="72c36-113">`%` (Visual Basic `Mod` )</span><span class="sxs-lookup"><span data-stu-id="72c36-113">`%` (Visual Basic `Mod`)</span></span>

  - `<<`

  - `>>`

  - <span data-ttu-id="72c36-114">`-` (birli olumsuzlama)</span><span class="sxs-lookup"><span data-stu-id="72c36-114">`-` (unary negation)</span></span>

- <span data-ttu-id="72c36-115">Temel karşılaştırma işleçleri:</span><span class="sxs-lookup"><span data-stu-id="72c36-115">Basic comparison operators:</span></span>

  - <span data-ttu-id="72c36-116">Visual Basic `=` ve C # `==`</span><span class="sxs-lookup"><span data-stu-id="72c36-116">Visual Basic `=` and C# `==`</span></span>

  - <span data-ttu-id="72c36-117">Visual Basic `<>` ve C # `!=`</span><span class="sxs-lookup"><span data-stu-id="72c36-117">Visual Basic `<>` and C# `!=`</span></span>

  - <span data-ttu-id="72c36-118">Visual Basic `Is/IsNot`</span><span class="sxs-lookup"><span data-stu-id="72c36-118">Visual Basic `Is/IsNot`</span></span>

  - `<`

  - `<=`

  - `>`

  - `>=`

## <a name="see-also"></a><span data-ttu-id="72c36-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="72c36-119">See also</span></span>

- [<span data-ttu-id="72c36-120">Veri Türleri ve İşlevleri</span><span class="sxs-lookup"><span data-stu-id="72c36-120">Data Types and Functions</span></span>](data-types-and-functions.md)
- [<span data-ttu-id="72c36-121">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="72c36-121">C# Operators</span></span>](../../../../../csharp/language-reference/operators/index.md)
- [<span data-ttu-id="72c36-122">İşleçler</span><span class="sxs-lookup"><span data-stu-id="72c36-122">Operators</span></span>](../../../../../visual-basic/language-reference/operators/index.md)
