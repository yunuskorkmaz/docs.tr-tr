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
ms.openlocfilehash: 4852e1166a975b1a45c5bd905123a35fc846aa28
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/26/2019
ms.locfileid: "68513162"
---
# <a name="sizeof-operator-c-reference"></a><span data-ttu-id="7779d-102">sizeof işleci (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="7779d-102">sizeof operator (C# reference)</span></span>

<span data-ttu-id="7779d-103">`sizeof` İşleci, verilen türdeki bir değişken tarafından bulunan bayt sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="7779d-103">The `sizeof` operator returns the number of bytes occupied by a variable of a given type.</span></span> <span data-ttu-id="7779d-104">`sizeof` İşlecin bağımsız değişkeni, yönetilmeyen bir [türün](../builtin-types/unmanaged-types.md) adı veya yönetilmeyen bir tür olarak [Kısıtlanmış](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) bir tür parametresi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7779d-104">An argument of the `sizeof` operator must be the name of an [unmanaged type](../builtin-types/unmanaged-types.md) or a type parameter that is [constrained](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) to be an unmanaged type.</span></span>

<span data-ttu-id="7779d-105">Operatör güvenli olmayan bir bağlam gerektiriyor. [](../keywords/unsafe.md) `sizeof`</span><span class="sxs-lookup"><span data-stu-id="7779d-105">The `sizeof` operator requires an [unsafe](../keywords/unsafe.md) context.</span></span> <span data-ttu-id="7779d-106">Ancak, aşağıdaki tabloda sunulan ifadeler derleme zamanında karşılık gelen sabit değerlere değerlendirilir ve güvenli olmayan bir bağlam gerektirmez:</span><span class="sxs-lookup"><span data-stu-id="7779d-106">However, the expressions presented in the following table are evaluated in compile time to the corresponding constant values and don't require an unsafe context:</span></span>

|<span data-ttu-id="7779d-107">İfade</span><span class="sxs-lookup"><span data-stu-id="7779d-107">Expression</span></span>|<span data-ttu-id="7779d-108">Sabit değer</span><span class="sxs-lookup"><span data-stu-id="7779d-108">Constant value</span></span>|
|---------|---------------|
|`sizeof(sbyte)`|<span data-ttu-id="7779d-109">1\.</span><span class="sxs-lookup"><span data-stu-id="7779d-109">1</span></span>|
|`sizeof(byte)`|<span data-ttu-id="7779d-110">1\.</span><span class="sxs-lookup"><span data-stu-id="7779d-110">1</span></span>|
|`sizeof(short)`|<span data-ttu-id="7779d-111">2</span><span class="sxs-lookup"><span data-stu-id="7779d-111">2</span></span>|
|`sizeof(ushort)`|<span data-ttu-id="7779d-112">2</span><span class="sxs-lookup"><span data-stu-id="7779d-112">2</span></span>|
|`sizeof(int)`|<span data-ttu-id="7779d-113">4</span><span class="sxs-lookup"><span data-stu-id="7779d-113">4</span></span>|
|`sizeof(uint)`|<span data-ttu-id="7779d-114">4</span><span class="sxs-lookup"><span data-stu-id="7779d-114">4</span></span>|
|`sizeof(long)`|<span data-ttu-id="7779d-115">8</span><span class="sxs-lookup"><span data-stu-id="7779d-115">8</span></span>|
|`sizeof(ulong)`|<span data-ttu-id="7779d-116">8</span><span class="sxs-lookup"><span data-stu-id="7779d-116">8</span></span>|
|`sizeof(char)`|<span data-ttu-id="7779d-117">2</span><span class="sxs-lookup"><span data-stu-id="7779d-117">2</span></span>|
|`sizeof(float)`|<span data-ttu-id="7779d-118">4</span><span class="sxs-lookup"><span data-stu-id="7779d-118">4</span></span>|
|`sizeof(double)`|<span data-ttu-id="7779d-119">8</span><span class="sxs-lookup"><span data-stu-id="7779d-119">8</span></span>|
|`sizeof(decimal)`|<span data-ttu-id="7779d-120">16</span><span class="sxs-lookup"><span data-stu-id="7779d-120">16</span></span>|
|`sizeof(bool)`|<span data-ttu-id="7779d-121">1\.</span><span class="sxs-lookup"><span data-stu-id="7779d-121">1</span></span>|

<span data-ttu-id="7779d-122">Ayrıca, `sizeof` işlecin işleneni bir [sabit](../keywords/enum.md) listesi türünün adı olduğunda güvenli olmayan bir bağlam kullanmanıza gerek kalmaz.</span><span class="sxs-lookup"><span data-stu-id="7779d-122">You also don't need to use an unsafe context when the operand of the `sizeof` operator is the name of an [enum](../keywords/enum.md) type.</span></span>

<span data-ttu-id="7779d-123">Aşağıdaki örnek `sizeof` işlecinin kullanımını gösterir:</span><span class="sxs-lookup"><span data-stu-id="7779d-123">The following example demonstrates the usage of the `sizeof` operator:</span></span>

[!code-csharp[sizeof examples](~/samples/csharp/language-reference/operators/SizeOfOperator.cs)]

<span data-ttu-id="7779d-124">İşleci `sizeof` , yönetilen bellekte ortak dil çalışma zamanı tarafından ayrılacak bayt sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="7779d-124">The `sizeof` operator returns a number of bytes that would be allocated by the common language runtime in managed memory.</span></span> <span data-ttu-id="7779d-125">[Yapı](../keywords/struct.md) türleri için bu değer, yukarıdaki örnekte gösterildiği gibi herhangi bir doldurma içerir.</span><span class="sxs-lookup"><span data-stu-id="7779d-125">For [struct](../keywords/struct.md) types, that value includes any padding, as the preceding example demonstrates.</span></span> <span data-ttu-id="7779d-126">`sizeof` İşlecinin sonucu, *yönetilmeyen* bellekteki bir türün boyutunu döndüren <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> yönteminin sonuçlarından farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="7779d-126">The result of the `sizeof` operator might differ from the result of the <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> method, which returns the size of a type in *unmanaged* memory.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="7779d-127">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="7779d-127">C# language specification</span></span>

<span data-ttu-id="7779d-128">Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [sizeof işleci](~/_csharplang/spec/unsafe-code.md#the-sizeof-operator) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="7779d-128">For more information, see [The sizeof operator](~/_csharplang/spec/unsafe-code.md#the-sizeof-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7779d-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7779d-129">See also</span></span>

- [<span data-ttu-id="7779d-130">C#başvurunun</span><span class="sxs-lookup"><span data-stu-id="7779d-130">C# reference</span></span>](../index.md)
- [<span data-ttu-id="7779d-131">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="7779d-131">C# operators</span></span>](index.md)
- [<span data-ttu-id="7779d-132">İşaretçiyle ilgili işleçler</span><span class="sxs-lookup"><span data-stu-id="7779d-132">Pointer related operators</span></span>](pointer-related-operators.md)
- [<span data-ttu-id="7779d-133">İşaretçi türleri</span><span class="sxs-lookup"><span data-stu-id="7779d-133">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="7779d-134">Bellek ve aralıkla ilgili türler</span><span class="sxs-lookup"><span data-stu-id="7779d-134">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
