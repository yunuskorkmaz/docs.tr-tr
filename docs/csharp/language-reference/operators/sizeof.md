---
title: işleç boyutları - C# referans
ms.date: 07/25/2019
f1_keywords:
- sizeof_CSharpKeyword
- sizeof
helpviewer_keywords:
- sizeof keyword [C#]
ms.assetid: c548592c-677c-4f40-a4ce-e613f7529141
ms.openlocfilehash: a9e80ecb3288479a2ca81b43c9d088809ed5f2f0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847293"
---
# <a name="sizeof-operator-c-reference"></a><span data-ttu-id="aee66-102">işlecinin boyutları (C# referansı)</span><span class="sxs-lookup"><span data-stu-id="aee66-102">sizeof operator (C# reference)</span></span>

<span data-ttu-id="aee66-103">İşletici, `sizeof` belirli bir türdeki bir değişken tarafından işgal edilen bayt sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="aee66-103">The `sizeof` operator returns the number of bytes occupied by a variable of a given type.</span></span> <span data-ttu-id="aee66-104">`sizeof` İşleç için bağımsız değişken [yönetilmeyen](../builtin-types/unmanaged-types.md) bir tür veya yönetilmeyen bir tür olarak [sınırlandırılmış](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) bir tür parametre adı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="aee66-104">The argument to the `sizeof` operator must be the name of an [unmanaged type](../builtin-types/unmanaged-types.md) or a type parameter that is [constrained](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) to be an unmanaged type.</span></span>

<span data-ttu-id="aee66-105">İşleç `sizeof` [güvenli olmayan](../keywords/unsafe.md) bir bağlam gerektirir.</span><span class="sxs-lookup"><span data-stu-id="aee66-105">The `sizeof` operator requires an [unsafe](../keywords/unsafe.md) context.</span></span> <span data-ttu-id="aee66-106">Ancak, aşağıdaki tabloda sunulan ifadeler, ilgili sabit değerlere derleme zaman olarak değerlendirilir ve güvenli olmayan bir bağlam gerektirmez:</span><span class="sxs-lookup"><span data-stu-id="aee66-106">However, the expressions presented in the following table are evaluated in compile time to the corresponding constant values and don't require an unsafe context:</span></span>

|<span data-ttu-id="aee66-107">İfadeler</span><span class="sxs-lookup"><span data-stu-id="aee66-107">Expression</span></span>|<span data-ttu-id="aee66-108">Sabit değer</span><span class="sxs-lookup"><span data-stu-id="aee66-108">Constant value</span></span>|
|---------|---------------|
|`sizeof(sbyte)`|<span data-ttu-id="aee66-109">1</span><span class="sxs-lookup"><span data-stu-id="aee66-109">1</span></span>|
|`sizeof(byte)`|<span data-ttu-id="aee66-110">1</span><span class="sxs-lookup"><span data-stu-id="aee66-110">1</span></span>|
|`sizeof(short)`|<span data-ttu-id="aee66-111">2</span><span class="sxs-lookup"><span data-stu-id="aee66-111">2</span></span>|
|`sizeof(ushort)`|<span data-ttu-id="aee66-112">2</span><span class="sxs-lookup"><span data-stu-id="aee66-112">2</span></span>|
|`sizeof(int)`|<span data-ttu-id="aee66-113">4</span><span class="sxs-lookup"><span data-stu-id="aee66-113">4</span></span>|
|`sizeof(uint)`|<span data-ttu-id="aee66-114">4</span><span class="sxs-lookup"><span data-stu-id="aee66-114">4</span></span>|
|`sizeof(long)`|<span data-ttu-id="aee66-115">8</span><span class="sxs-lookup"><span data-stu-id="aee66-115">8</span></span>|
|`sizeof(ulong)`|<span data-ttu-id="aee66-116">8</span><span class="sxs-lookup"><span data-stu-id="aee66-116">8</span></span>|
|`sizeof(char)`|<span data-ttu-id="aee66-117">2</span><span class="sxs-lookup"><span data-stu-id="aee66-117">2</span></span>|
|`sizeof(float)`|<span data-ttu-id="aee66-118">4</span><span class="sxs-lookup"><span data-stu-id="aee66-118">4</span></span>|
|`sizeof(double)`|<span data-ttu-id="aee66-119">8</span><span class="sxs-lookup"><span data-stu-id="aee66-119">8</span></span>|
|`sizeof(decimal)`|<span data-ttu-id="aee66-120">16</span><span class="sxs-lookup"><span data-stu-id="aee66-120">16</span></span>|
|`sizeof(bool)`|<span data-ttu-id="aee66-121">1</span><span class="sxs-lookup"><span data-stu-id="aee66-121">1</span></span>|

<span data-ttu-id="aee66-122">`sizeof` Ayrıca, işleç operand [bir enum](../builtin-types/enum.md) türünün adı olduğunda güvenli olmayan bir bağlam kullanmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="aee66-122">You also don't need to use an unsafe context when the operand of the `sizeof` operator is the name of an [enum](../builtin-types/enum.md) type.</span></span>

<span data-ttu-id="aee66-123">Aşağıdaki örnek, işleç `sizeof` kullanımını gösterir:</span><span class="sxs-lookup"><span data-stu-id="aee66-123">The following example demonstrates the usage of the `sizeof` operator:</span></span>

[!code-csharp[sizeof examples](snippets/SizeOfOperator.cs)]

<span data-ttu-id="aee66-124">İşleç, `sizeof` yönetilen bellekte ortak dil çalışma süresi tarafından ayrılacak bir dizi bayt döndürür.</span><span class="sxs-lookup"><span data-stu-id="aee66-124">The `sizeof` operator returns a number of bytes that would be allocated by the common language runtime in managed memory.</span></span> <span data-ttu-id="aee66-125">[Yapı](../builtin-types/struct.md) türleri için, yukarıdaki örnekte gösterildiği gibi, bu değer herhangi bir dolgu içerir.</span><span class="sxs-lookup"><span data-stu-id="aee66-125">For [struct](../builtin-types/struct.md) types, that value includes any padding, as the preceding example demonstrates.</span></span> <span data-ttu-id="aee66-126">`sizeof` İşleç sonucu, *yönetilmeyen* bellekte bir türün boyutunu döndüren <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> yöntemin sonucundan farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="aee66-126">The result of the `sizeof` operator might differ from the result of the <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> method, which returns the size of a type in *unmanaged* memory.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="aee66-127">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="aee66-127">C# language specification</span></span>

<span data-ttu-id="aee66-128">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md)işleç bölümünün [boyutlarına](~/_csharplang/spec/unsafe-code.md#the-sizeof-operator) bakın.</span><span class="sxs-lookup"><span data-stu-id="aee66-128">For more information, see [The sizeof operator](~/_csharplang/spec/unsafe-code.md#the-sizeof-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="aee66-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aee66-129">See also</span></span>

- [<span data-ttu-id="aee66-130">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="aee66-130">C# reference</span></span>](../index.md)
- [<span data-ttu-id="aee66-131">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="aee66-131">C# operators</span></span>](index.md)
- [<span data-ttu-id="aee66-132">İşaretçi bağlantılı işleçler</span><span class="sxs-lookup"><span data-stu-id="aee66-132">Pointer related operators</span></span>](pointer-related-operators.md)
- [<span data-ttu-id="aee66-133">İşaretçi türleri</span><span class="sxs-lookup"><span data-stu-id="aee66-133">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="aee66-134">Bellek ve aralıkla ilgili türler</span><span class="sxs-lookup"><span data-stu-id="aee66-134">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
- [<span data-ttu-id="aee66-135">.NET içindeki Genel Türler</span><span class="sxs-lookup"><span data-stu-id="aee66-135">Generics in .NET</span></span>](../../../standard/generics/index.md)
