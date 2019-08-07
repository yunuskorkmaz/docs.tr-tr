---
title: sizeof işleci- C# başvuru
ms.custom: seodec18
ms.date: 07/25/2019
f1_keywords:
- sizeof_CSharpKeyword
- sizeof
helpviewer_keywords:
- sizeof keyword [C#]
ms.assetid: c548592c-677c-4f40-a4ce-e613f7529141
ms.openlocfilehash: c455804923f4d0e7cc8f556bb9b9df34b6332d82
ms.sourcegitcommit: bbfcc913c275885381820be28f61efcf8e83eecc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/05/2019
ms.locfileid: "68796520"
---
# <a name="sizeof-operator-c-reference"></a><span data-ttu-id="da8ad-102">sizeof işleci (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="da8ad-102">sizeof operator (C# reference)</span></span>

<span data-ttu-id="da8ad-103">`sizeof` İşleci, verilen türdeki bir değişken tarafından bulunan bayt sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="da8ad-103">The `sizeof` operator returns the number of bytes occupied by a variable of a given type.</span></span> <span data-ttu-id="da8ad-104">`sizeof` İşlecin bağımsız değişkeni, yönetilmeyen bir [türün](../builtin-types/unmanaged-types.md) veya yönetilmeyen tür olarak [Kısıtlanmış](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) bir tür parametresinin adı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="da8ad-104">The argument to the `sizeof` operator must be the name of an [unmanaged type](../builtin-types/unmanaged-types.md) or a type parameter that is [constrained](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) to be an unmanaged type.</span></span>

<span data-ttu-id="da8ad-105">Operatör güvenli olmayan bir bağlam gerektiriyor. [](../keywords/unsafe.md) `sizeof`</span><span class="sxs-lookup"><span data-stu-id="da8ad-105">The `sizeof` operator requires an [unsafe](../keywords/unsafe.md) context.</span></span> <span data-ttu-id="da8ad-106">Ancak, aşağıdaki tabloda sunulan ifadeler derleme zamanında karşılık gelen sabit değerlere değerlendirilir ve güvenli olmayan bir bağlam gerektirmez:</span><span class="sxs-lookup"><span data-stu-id="da8ad-106">However, the expressions presented in the following table are evaluated in compile time to the corresponding constant values and don't require an unsafe context:</span></span>

|<span data-ttu-id="da8ad-107">İfade</span><span class="sxs-lookup"><span data-stu-id="da8ad-107">Expression</span></span>|<span data-ttu-id="da8ad-108">Sabit değer</span><span class="sxs-lookup"><span data-stu-id="da8ad-108">Constant value</span></span>|
|---------|---------------|
|`sizeof(sbyte)`|<span data-ttu-id="da8ad-109">1\.</span><span class="sxs-lookup"><span data-stu-id="da8ad-109">1</span></span>|
|`sizeof(byte)`|<span data-ttu-id="da8ad-110">1\.</span><span class="sxs-lookup"><span data-stu-id="da8ad-110">1</span></span>|
|`sizeof(short)`|<span data-ttu-id="da8ad-111">2</span><span class="sxs-lookup"><span data-stu-id="da8ad-111">2</span></span>|
|`sizeof(ushort)`|<span data-ttu-id="da8ad-112">2</span><span class="sxs-lookup"><span data-stu-id="da8ad-112">2</span></span>|
|`sizeof(int)`|<span data-ttu-id="da8ad-113">4</span><span class="sxs-lookup"><span data-stu-id="da8ad-113">4</span></span>|
|`sizeof(uint)`|<span data-ttu-id="da8ad-114">4</span><span class="sxs-lookup"><span data-stu-id="da8ad-114">4</span></span>|
|`sizeof(long)`|<span data-ttu-id="da8ad-115">8</span><span class="sxs-lookup"><span data-stu-id="da8ad-115">8</span></span>|
|`sizeof(ulong)`|<span data-ttu-id="da8ad-116">8</span><span class="sxs-lookup"><span data-stu-id="da8ad-116">8</span></span>|
|`sizeof(char)`|<span data-ttu-id="da8ad-117">2</span><span class="sxs-lookup"><span data-stu-id="da8ad-117">2</span></span>|
|`sizeof(float)`|<span data-ttu-id="da8ad-118">4</span><span class="sxs-lookup"><span data-stu-id="da8ad-118">4</span></span>|
|`sizeof(double)`|<span data-ttu-id="da8ad-119">8</span><span class="sxs-lookup"><span data-stu-id="da8ad-119">8</span></span>|
|`sizeof(decimal)`|<span data-ttu-id="da8ad-120">16</span><span class="sxs-lookup"><span data-stu-id="da8ad-120">16</span></span>|
|`sizeof(bool)`|<span data-ttu-id="da8ad-121">1\.</span><span class="sxs-lookup"><span data-stu-id="da8ad-121">1</span></span>|

<span data-ttu-id="da8ad-122">Ayrıca, `sizeof` işlecin işleneni bir [sabit](../keywords/enum.md) listesi türünün adı olduğunda güvenli olmayan bir bağlam kullanmanıza gerek kalmaz.</span><span class="sxs-lookup"><span data-stu-id="da8ad-122">You also don't need to use an unsafe context when the operand of the `sizeof` operator is the name of an [enum](../keywords/enum.md) type.</span></span>

<span data-ttu-id="da8ad-123">Aşağıdaki örnek `sizeof` işlecinin kullanımını gösterir:</span><span class="sxs-lookup"><span data-stu-id="da8ad-123">The following example demonstrates the usage of the `sizeof` operator:</span></span>

[!code-csharp[sizeof examples](~/samples/csharp/language-reference/operators/SizeOfOperator.cs)]

<span data-ttu-id="da8ad-124">İşleci `sizeof` , yönetilen bellekte ortak dil çalışma zamanı tarafından ayrılacak bayt sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="da8ad-124">The `sizeof` operator returns a number of bytes that would be allocated by the common language runtime in managed memory.</span></span> <span data-ttu-id="da8ad-125">[Yapı](../keywords/struct.md) türleri için bu değer, yukarıdaki örnekte gösterildiği gibi herhangi bir doldurma içerir.</span><span class="sxs-lookup"><span data-stu-id="da8ad-125">For [struct](../keywords/struct.md) types, that value includes any padding, as the preceding example demonstrates.</span></span> <span data-ttu-id="da8ad-126">`sizeof` İşlecinin sonucu, *yönetilmeyen* bellekteki bir türün boyutunu döndüren <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> yönteminin sonuçlarından farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="da8ad-126">The result of the `sizeof` operator might differ from the result of the <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> method, which returns the size of a type in *unmanaged* memory.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="da8ad-127">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="da8ad-127">C# language specification</span></span>

<span data-ttu-id="da8ad-128">Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [sizeof işleci](~/_csharplang/spec/unsafe-code.md#the-sizeof-operator) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="da8ad-128">For more information, see [The sizeof operator](~/_csharplang/spec/unsafe-code.md#the-sizeof-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="da8ad-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="da8ad-129">See also</span></span>

- [<span data-ttu-id="da8ad-130">C#başvurunun</span><span class="sxs-lookup"><span data-stu-id="da8ad-130">C# reference</span></span>](../index.md)
- [<span data-ttu-id="da8ad-131">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="da8ad-131">C# operators</span></span>](index.md)
- [<span data-ttu-id="da8ad-132">İşaretçiyle ilgili işleçler</span><span class="sxs-lookup"><span data-stu-id="da8ad-132">Pointer related operators</span></span>](pointer-related-operators.md)
- [<span data-ttu-id="da8ad-133">İşaretçi türleri</span><span class="sxs-lookup"><span data-stu-id="da8ad-133">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="da8ad-134">Bellek ve aralıkla ilgili türler</span><span class="sxs-lookup"><span data-stu-id="da8ad-134">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
