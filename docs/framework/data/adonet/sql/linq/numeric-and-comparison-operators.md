---
title: Sayısal ve Karşılaştırma İşleçleri
ms.date: 03/30/2017
ms.assetid: 25b4a26a-06f2-4f80-87a9-76705ed46197
ms.openlocfilehash: 7e7af725864aa191f092055fa32b403093321aa5
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781289"
---
# <a name="numeric-and-comparison-operators"></a><span data-ttu-id="8ac67-102">Sayısal ve Karşılaştırma İşleçleri</span><span class="sxs-lookup"><span data-stu-id="8ac67-102">Numeric and Comparison Operators</span></span>

<span data-ttu-id="8ac67-103">Aritmetik ve karşılaştırma işleçleri, ortak dil çalışma zamanında (CLR) beklenen şekilde aşağıdaki gibi çalışır:</span><span class="sxs-lookup"><span data-stu-id="8ac67-103">Arithmetic and comparison operators work as expected in the common language runtime (CLR) except as follows:</span></span>

- <span data-ttu-id="8ac67-104">SQL, kayan nokta numaralarında mod işlecini desteklemez.</span><span class="sxs-lookup"><span data-stu-id="8ac67-104">SQL does not support the modulus operator on floating-point numbers.</span></span>

- <span data-ttu-id="8ac67-105">SQL Denetlenmemiş aritmetiğini desteklemez.</span><span class="sxs-lookup"><span data-stu-id="8ac67-105">SQL does not support unchecked arithmetic.</span></span>

- <span data-ttu-id="8ac67-106">Artırma ve azaltma işleçleri, SQL 'de çoğaltılabilen ve bu nedenle desteklenmeyen ifadelerde kullandığınızda yan etkilere neden olur.</span><span class="sxs-lookup"><span data-stu-id="8ac67-106">Increment and decrement operators cause side-effects when you use them in expressions that cannot be replicated in SQL and are, therefore, not supported.</span></span>

## <a name="supported-operators"></a><span data-ttu-id="8ac67-107">Desteklenen Işleçler</span><span class="sxs-lookup"><span data-stu-id="8ac67-107">Supported Operators</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="8ac67-108">aşağıdaki işleçleri destekler.</span><span class="sxs-lookup"><span data-stu-id="8ac67-108">supports the following operators.</span></span>

- <span data-ttu-id="8ac67-109">Temel aritmetik işleçler:</span><span class="sxs-lookup"><span data-stu-id="8ac67-109">Basic arithmetic operators:</span></span>

  - `+`

  - <span data-ttu-id="8ac67-110">`-`strA</span><span class="sxs-lookup"><span data-stu-id="8ac67-110">`-` (subtraction)</span></span>

  - `*`

  - `/`

  - <span data-ttu-id="8ac67-111">Visual Basic tamsayı bölümü (`\`)</span><span class="sxs-lookup"><span data-stu-id="8ac67-111">Visual Basic integer division (`\`)</span></span>

  - <span data-ttu-id="8ac67-112">`%`(Visual Basic `Mod`)</span><span class="sxs-lookup"><span data-stu-id="8ac67-112">`%` (Visual Basic `Mod`)</span></span>

  - `<<`

  - `>>`

  - <span data-ttu-id="8ac67-113">`-`(birli olumsuzlama)</span><span class="sxs-lookup"><span data-stu-id="8ac67-113">`-` (unary negation)</span></span>

- <span data-ttu-id="8ac67-114">Temel karşılaştırma işleçleri:</span><span class="sxs-lookup"><span data-stu-id="8ac67-114">Basic comparison operators:</span></span>

  - <span data-ttu-id="8ac67-115">Visual Basic `=` ve C#`==`</span><span class="sxs-lookup"><span data-stu-id="8ac67-115">Visual Basic `=` and C# `==`</span></span>

  - <span data-ttu-id="8ac67-116">Visual Basic `<>` ve C#`!=`</span><span class="sxs-lookup"><span data-stu-id="8ac67-116">Visual Basic `<>` and C# `!=`</span></span>

  - <span data-ttu-id="8ac67-117">Visual Basic`Is/IsNot`</span><span class="sxs-lookup"><span data-stu-id="8ac67-117">Visual Basic `Is/IsNot`</span></span>

  - `<`

  - `<=`

  - `>`

  - `>=`

## <a name="see-also"></a><span data-ttu-id="8ac67-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8ac67-118">See also</span></span>

- [<span data-ttu-id="8ac67-119">Veri Türleri ve İşlevleri</span><span class="sxs-lookup"><span data-stu-id="8ac67-119">Data Types and Functions</span></span>](data-types-and-functions.md)
- [<span data-ttu-id="8ac67-120">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="8ac67-120">C# Operators</span></span>](../../../../../csharp/language-reference/operators/index.md)
- [<span data-ttu-id="8ac67-121">İşleçler</span><span class="sxs-lookup"><span data-stu-id="8ac67-121">Operators</span></span>](../../../../../visual-basic/language-reference/operators/index.md)
