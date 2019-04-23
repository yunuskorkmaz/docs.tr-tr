---
title: Sayısal ve Karşılaştırma İşleçleri
ms.date: 03/30/2017
ms.assetid: 25b4a26a-06f2-4f80-87a9-76705ed46197
ms.openlocfilehash: b29f78a13d6d0313e0ad29754f6d13ac08be1092
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59973349"
---
# <a name="numeric-and-comparison-operators"></a><span data-ttu-id="754d2-102">Sayısal ve Karşılaştırma İşleçleri</span><span class="sxs-lookup"><span data-stu-id="754d2-102">Numeric and Comparison Operators</span></span>

<span data-ttu-id="754d2-103">Aritmetik ve Karşılaştırma işleçleri dışında ortak dil çalışma zamanı (CLR) gibi beklendiği gibi çalışmayabilir:</span><span class="sxs-lookup"><span data-stu-id="754d2-103">Arithmetic and comparison operators work as expected in the common language runtime (CLR) except as follows:</span></span>

- <span data-ttu-id="754d2-104">SQL, kayan nokta numaralarını modulus işleci desteklemez.</span><span class="sxs-lookup"><span data-stu-id="754d2-104">SQL does not support the modulus operator on floating-point numbers.</span></span>

- <span data-ttu-id="754d2-105">SQL denetlenmeyen aritmetiğini desteklemez.</span><span class="sxs-lookup"><span data-stu-id="754d2-105">SQL does not support unchecked arithmetic.</span></span>

- <span data-ttu-id="754d2-106">SQL'de çoğaltılır ve bu nedenle, desteklenmiyor ifadelerde kullandığınızda artırma ve azaltma işleçleri yan etkilere neden.</span><span class="sxs-lookup"><span data-stu-id="754d2-106">Increment and decrement operators cause side-effects when you use them in expressions that cannot be replicated in SQL and are, therefore, not supported.</span></span>

## <a name="supported-operators"></a><span data-ttu-id="754d2-107">Desteklenen işleçleri</span><span class="sxs-lookup"><span data-stu-id="754d2-107">Supported Operators</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="754d2-108">Aşağıdaki işleçleri destekler.</span><span class="sxs-lookup"><span data-stu-id="754d2-108">supports the following operators.</span></span>

- <span data-ttu-id="754d2-109">Temel aritmetik işleçler:</span><span class="sxs-lookup"><span data-stu-id="754d2-109">Basic arithmetic operators:</span></span>

  - `+`

  - <span data-ttu-id="754d2-110">`-` (çıkarma)</span><span class="sxs-lookup"><span data-stu-id="754d2-110">`-` (subtraction)</span></span>

  - `*`

  - `/`

  - <span data-ttu-id="754d2-111">Visual Basic tamsayı bölme (`\`)</span><span class="sxs-lookup"><span data-stu-id="754d2-111">Visual Basic integer division (`\`)</span></span>

  - <span data-ttu-id="754d2-112">`%` (Visual Basic `Mod`)</span><span class="sxs-lookup"><span data-stu-id="754d2-112">`%` (Visual Basic `Mod`)</span></span>

  - `<<`

  - `>>`

  - <span data-ttu-id="754d2-113">`-` (birli olumsuzlama)</span><span class="sxs-lookup"><span data-stu-id="754d2-113">`-` (unary negation)</span></span>

- <span data-ttu-id="754d2-114">Temel Karşılaştırma işleçleri:</span><span class="sxs-lookup"><span data-stu-id="754d2-114">Basic comparison operators:</span></span>

  - <span data-ttu-id="754d2-115">Visual Basic `=` ve C# `==`</span><span class="sxs-lookup"><span data-stu-id="754d2-115">Visual Basic `=` and C# `==`</span></span>

  - <span data-ttu-id="754d2-116">Visual Basic `<>` ve C# `!=`</span><span class="sxs-lookup"><span data-stu-id="754d2-116">Visual Basic `<>` and C# `!=`</span></span>

  - <span data-ttu-id="754d2-117">Visual Basic `Is/IsNot`</span><span class="sxs-lookup"><span data-stu-id="754d2-117">Visual Basic `Is/IsNot`</span></span>

  - `<`

  - `<=`

  - `>`

  - `>=`

## <a name="see-also"></a><span data-ttu-id="754d2-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="754d2-118">See also</span></span>

- [<span data-ttu-id="754d2-119">Veri Türleri ve İşlevleri</span><span class="sxs-lookup"><span data-stu-id="754d2-119">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
- [<span data-ttu-id="754d2-120">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="754d2-120">C# Operators</span></span>](../../../../../../docs/csharp/language-reference/operators/index.md)
- [<span data-ttu-id="754d2-121">İşleçler</span><span class="sxs-lookup"><span data-stu-id="754d2-121">Operators</span></span>](../../../../../visual-basic/language-reference/operators/index.md)
