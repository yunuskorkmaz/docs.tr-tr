---
title: C#Numaralandırmalar - Turu C# dil
description: Numaralandırmalar, ayrık sabitlerle adlı hakkında bilgi edininC#
ms.date: 08/10/2016
ms.assetid: 7faba1cc-6ea9-4a19-adb9-0335e4b132e5
ms.openlocfilehash: 8c1c29c3c06829da81a9c9be8bb5bd99f1c9e395
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61706357"
---
# <a name="enums"></a><span data-ttu-id="9437f-103">Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="9437f-103">Enums</span></span>

<span data-ttu-id="9437f-104">Bir ***sabit listesi türü*** adlandırılmış sabitler kümesini içeren farklı bir değer türüdür.</span><span class="sxs-lookup"><span data-stu-id="9437f-104">An ***enum type*** is a distinct value type with a set of named constants.</span></span> <span data-ttu-id="9437f-105">Bir ayrık değerler kümesi olabilir bir tür tanımlamak, ihtiyacınız olduğunda, sabit listeleri tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9437f-105">You define enums when you need to define a type that can have a set of discrete values.</span></span> <span data-ttu-id="9437f-106">Bunlar bir integral değer türlerinin, temel alınan depolama alanı olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="9437f-106">They use one of the integral value types as their underlying storage.</span></span> <span data-ttu-id="9437f-107">Anlam ayrık değerlere sağlarlar.</span><span class="sxs-lookup"><span data-stu-id="9437f-107">They provide semantic meaning to the discrete values.</span></span>

<span data-ttu-id="9437f-108">Aşağıdaki örnek bildirir ve kullandığı bir `enum` adlı türü `Color` üç sabit değerler ile `Red`, `Green`, ve `Blue`.</span><span class="sxs-lookup"><span data-stu-id="9437f-108">The following example declares and uses an `enum` type named `Color` with three constant values, `Red`, `Green`, and `Blue`.</span></span>

[!code-csharp[EnumExample](../../../samples/snippets/csharp/tour/enums/Program.cs#L3-L36)]

<span data-ttu-id="9437f-109">Her `enum` türünde adlı karşılık gelen bir integral türü ***temel alınan türü*** , `enum` türü.</span><span class="sxs-lookup"><span data-stu-id="9437f-109">Each `enum` type has a corresponding integral type called the ***underlying type*** of the `enum` type.</span></span> <span data-ttu-id="9437f-110">Bir `enum` açıkça bir temel türü bildirmiyor türüne sahip bir temel alınan türü `int`.</span><span class="sxs-lookup"><span data-stu-id="9437f-110">An `enum` type that does not explicitly declare an underlying type has an underlying type of `int`.</span></span> <span data-ttu-id="9437f-111">Bir `enum` türün depolama biçimi ve olası değerler aralığı kendi temel türü tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="9437f-111">An `enum` type’s storage format and range of possible values are determined by its underlying type.</span></span> <span data-ttu-id="9437f-112">Dizi değerlerini bir `enum` türü alabilir on ile sınırlı değildir, `enum` üyeleri.</span><span class="sxs-lookup"><span data-stu-id="9437f-112">The set of values that an `enum` type can take on is not limited by its `enum` members.</span></span> <span data-ttu-id="9437f-113">Özellikle, temel alınan herhangi bir değer türü bir `enum` atanabilecek `enum` yazın ve bu geçerli bir benzersiz değer `enum` türü.</span><span class="sxs-lookup"><span data-stu-id="9437f-113">In particular, any value of the underlying type of an `enum` can be cast to the `enum` type and is a distinct valid value of that `enum` type.</span></span>

<span data-ttu-id="9437f-114">Aşağıdaki örnek bildirir bir `enum` adlı türü `Alignment` bir temel alınan türüyle `sbyte`.</span><span class="sxs-lookup"><span data-stu-id="9437f-114">The following example declares an `enum` type named `Alignment` with an underlying type of `sbyte`.</span></span>

[!code-csharp[EnumStorage](../../../samples/snippets/csharp/tour/enums/Program.cs#L38-L43)]

<span data-ttu-id="9437f-115">Önceki örnekte gösterildiği gibi bir `enum` üye bildirimi, üyenin değeri belirten sabit bir ifade içerebilir.</span><span class="sxs-lookup"><span data-stu-id="9437f-115">As shown by the previous example, an `enum` member declaration can include a constant expression that specifies the value of the member.</span></span> <span data-ttu-id="9437f-116">Her biri için sabit değerin `enum` üye, temel alınan türü aralığında olmalıdır `enum`.</span><span class="sxs-lookup"><span data-stu-id="9437f-116">The constant value for each `enum` member must be in the range of the underlying type of the `enum`.</span></span> <span data-ttu-id="9437f-117">Olduğunda bir `enum` üye bildirimi açıkça bir değer belirtmiyor, üyenin değeri sıfır verilir (ilk üyesiyse `enum` türü) veya metin içeriğini eklemek önceki değerini `enum` yanı sıra bir üyesi.</span><span class="sxs-lookup"><span data-stu-id="9437f-117">When an `enum` member declaration does not explicitly specify a value, the member is given the value zero (if it is the first member in the `enum` type) or the value of the textually preceding `enum` member plus one.</span></span>

<span data-ttu-id="9437f-118">`Enum` dönüştürülür tamsayı değerleri ve tersi tür atamaları kullanarak bu değerleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="9437f-118">`Enum` values can be converted to integral values and vice versa using type casts.</span></span> <span data-ttu-id="9437f-119">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="9437f-119">For example:</span></span>

[!code-csharp[EnumStorage](../../../samples/snippets/csharp/tour/enums/Program.cs#L49-L50)]

<span data-ttu-id="9437f-120">Varsayılan değer aşağıdakilerden `enum` türüdür, tamsayı değeri sıfır değerine dönüştürülüp `enum` türü.</span><span class="sxs-lookup"><span data-stu-id="9437f-120">The default value of any `enum` type is the integral value zero converted to the `enum` type.</span></span> <span data-ttu-id="9437f-121">Burada değişkenleri otomatik olarak başlatılan bir varsayılan değer durumlarda değişkenleri için verilen değer budur `enum` türleri.</span><span class="sxs-lookup"><span data-stu-id="9437f-121">In cases where variables are automatically initialized to a default value, this is the value given to variables of `enum` types.</span></span> <span data-ttu-id="9437f-122">Varsayılan değeri için sırayla bir `enum` kolayca kullanılabilmesi için tür, değişmez değer `0` örtük olarak birine dönüştürür `enum` türü.</span><span class="sxs-lookup"><span data-stu-id="9437f-122">In order for the default value of an `enum` type to be easily available, the literal `0` implicitly converts to any `enum` type.</span></span> <span data-ttu-id="9437f-123">Bu nedenle, aşağıdaki izin verilir.</span><span class="sxs-lookup"><span data-stu-id="9437f-123">Thus, the following is permitted.</span></span>

[!code-csharp[EnumZero](../../../samples/snippets/csharp/tour/enums/Program.cs#L58-L58)]

> [!div class="step-by-step"]
> <span data-ttu-id="9437f-124">[Önceki](interfaces.md)
> [İleri](delegates.md)</span><span class="sxs-lookup"><span data-stu-id="9437f-124">[Previous](interfaces.md)
[Next](delegates.md)</span></span>
