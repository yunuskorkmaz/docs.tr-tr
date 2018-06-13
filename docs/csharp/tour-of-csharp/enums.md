---
title: C# numaralandırmaları - C# dili turu
description: C# sabitleri adlı numaralandırmalar, ayrık hakkında bilgi edinin
ms.date: 08/10/2016
ms.assetid: 7faba1cc-6ea9-4a19-adb9-0335e4b132e5
ms.openlocfilehash: 7fe2626381cb90e55842e3be17dd450eb73d5a5b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33353360"
---
# <a name="enums"></a><span data-ttu-id="2f8ef-103">Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="2f8ef-103">Enums</span></span>

<span data-ttu-id="2f8ef-104">Bir ***enum türü*** adlandırılmış sabitler kümesiyle ayrı değer türüdür.</span><span class="sxs-lookup"><span data-stu-id="2f8ef-104">An ***enum type*** is a distinct value type with a set of named constants.</span></span> <span data-ttu-id="2f8ef-105">Ayrık değerler kümesi olan tür tanımlama gerektiğinde numaralandırmaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2f8ef-105">You define enums when you need to define a type that can have a set of discrete values.</span></span> <span data-ttu-id="2f8ef-106">Tam sayı değeri türlerinden biri, temel alınan depolama alanı olarak kullanırlar.</span><span class="sxs-lookup"><span data-stu-id="2f8ef-106">They use one of the integral value types as their underlying storage.</span></span> <span data-ttu-id="2f8ef-107">Ayrık değerler için anlamsal anlamı sağlarlar.</span><span class="sxs-lookup"><span data-stu-id="2f8ef-107">They provide semantic meaning to the discrete values.</span></span>

<span data-ttu-id="2f8ef-108">Aşağıdaki örnek bildirir ve kullandığı bir `enum` adlı türü `Color` üç sabit değerleri ile `Red`, `Green`, ve `Blue`.</span><span class="sxs-lookup"><span data-stu-id="2f8ef-108">The following example declares and uses an `enum` type named `Color` with three constant values, `Red`, `Green`, and `Blue`.</span></span>

[!code-csharp[EnumExample](../../../samples/snippets/csharp/tour/enums/Program.cs#L3-L36)]

<span data-ttu-id="2f8ef-109">Her `enum` türüne sahip adlı karşılık gelen bir tam sayı türü ***temel alınan tür*** , `enum` türü.</span><span class="sxs-lookup"><span data-stu-id="2f8ef-109">Each `enum` type has a corresponding integral type called the ***underlying type*** of the `enum` type.</span></span> <span data-ttu-id="2f8ef-110">Bir `enum` açıkça bir temel alınan tür bildirmiyor türüne sahip bir temel alınan türü `int`.</span><span class="sxs-lookup"><span data-stu-id="2f8ef-110">An `enum` type that does not explicitly declare an underlying type has an underlying type of `int`.</span></span> <span data-ttu-id="2f8ef-111">Bir `enum` tür depolama biçimi ve olası değerleri aralığı, temel alınan türü tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="2f8ef-111">An `enum` type’s storage format and range of possible values are determined by its underlying type.</span></span> <span data-ttu-id="2f8ef-112">Kümesini değerlerinden oluşan bir `enum` türü alabilir üzerinde tarafından sınırlı değildir, `enum` üyeleri.</span><span class="sxs-lookup"><span data-stu-id="2f8ef-112">The set of values that an `enum` type can take on is not limited by its `enum` members.</span></span> <span data-ttu-id="2f8ef-113">Özellikle, arka plandaki herhangi bir değer türü bir `enum` için cast `enum` yazın ve o ayrı geçerli bir değer `enum` türü.</span><span class="sxs-lookup"><span data-stu-id="2f8ef-113">In particular, any value of the underlying type of an `enum` can be cast to the `enum` type and is a distinct valid value of that `enum` type.</span></span>

<span data-ttu-id="2f8ef-114">Aşağıdaki örnek bildiren bir `enum` adlı türü `Alignment` bir temel alınan türü ile `sbyte`.</span><span class="sxs-lookup"><span data-stu-id="2f8ef-114">The following example declares an `enum` type named `Alignment` with an underlying type of `sbyte`.</span></span>

[!code-csharp[EnumStorage](../../../samples/snippets/csharp/tour/enums/Program.cs#L38-L43)]

<span data-ttu-id="2f8ef-115">Önceki örnekte gösterildiği gibi bir `enum` üye bildirimi üyesinin değerini belirten bir sabit ifadesine içerebilir.</span><span class="sxs-lookup"><span data-stu-id="2f8ef-115">As shown by the previous example, an `enum` member declaration can include a constant expression that specifies the value of the member.</span></span> <span data-ttu-id="2f8ef-116">Her sabit değer `enum` üye, temel alınan türü aralığında olmalıdır `enum`.</span><span class="sxs-lookup"><span data-stu-id="2f8ef-116">The constant value for each `enum` member must be in the range of the underlying type of the `enum`.</span></span> <span data-ttu-id="2f8ef-117">Zaman bir `enum` üye bildirimi açıkça bir değer belirtmiyor, üye sıfır değeri verilir (ilk üyesiyse `enum` türü) veya textually önceki değeri `enum` yanı sıra bir üyesi.</span><span class="sxs-lookup"><span data-stu-id="2f8ef-117">When an `enum` member declaration does not explicitly specify a value, the member is given the value zero (if it is the first member in the `enum` type) or the value of the textually preceding `enum` member plus one.</span></span>

<span data-ttu-id="2f8ef-118">`Enum` değerler dönüştürülür tam sayı değerleri ve tersi tür atamaları kullanarak olabilir.</span><span class="sxs-lookup"><span data-stu-id="2f8ef-118">`Enum` values can be converted to integral values and vice versa using type casts.</span></span> <span data-ttu-id="2f8ef-119">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="2f8ef-119">For example:</span></span>

[!code-csharp[EnumStorage](../../../samples/snippets/csharp/tour/enums/Program.cs#L49-L50)]

<span data-ttu-id="2f8ef-120">Varsayılan değer herhangi `enum` türüdür tam sayı değeri sıfır değerine dönüştürülüp `enum` türü.</span><span class="sxs-lookup"><span data-stu-id="2f8ef-120">The default value of any `enum` type is the integral value zero converted to the `enum` type.</span></span> <span data-ttu-id="2f8ef-121">Burada değişkenleri otomatik olarak başlatılır için varsayılan bir değer durumlarda, bu değişkenleri için verilen değerdir `enum` türleri.</span><span class="sxs-lookup"><span data-stu-id="2f8ef-121">In cases where variables are automatically initialized to a default value, this is the value given to variables of `enum` types.</span></span> <span data-ttu-id="2f8ef-122">Varsayılan değer olan sırada bir `enum` kolayca kullanılabilir olması için türü, sabit `0` örtük olarak hiçbirine dönüştürür `enum` türü.</span><span class="sxs-lookup"><span data-stu-id="2f8ef-122">In order for the default value of an `enum` type to be easily available, the literal `0` implicitly converts to any `enum` type.</span></span> <span data-ttu-id="2f8ef-123">Bu nedenle, aşağıdaki izin verilir.</span><span class="sxs-lookup"><span data-stu-id="2f8ef-123">Thus, the following is permitted.</span></span>

[!code-csharp[EnumZero](../../../samples/snippets/csharp/tour/enums/Program.cs#L58-L58)]

>[!div class="step-by-step"]
<span data-ttu-id="2f8ef-124">[Önceki](interfaces.md)
[sonraki](delegates.md)</span><span class="sxs-lookup"><span data-stu-id="2f8ef-124">[Previous](interfaces.md)
[Next](delegates.md)</span></span>
