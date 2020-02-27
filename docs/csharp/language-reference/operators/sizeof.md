---
title: sizeof işleci- C# başvuru
ms.date: 07/25/2019
f1_keywords:
- sizeof_CSharpKeyword
- sizeof
helpviewer_keywords:
- sizeof keyword [C#]
ms.assetid: c548592c-677c-4f40-a4ce-e613f7529141
ms.openlocfilehash: 8e4518718d0975f8b4a65870f15d8c52d692c2f5
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77625741"
---
# <a name="sizeof-operator-c-reference"></a><span data-ttu-id="e3c7e-102">sizeof işleci (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="e3c7e-102">sizeof operator (C# reference)</span></span>

<span data-ttu-id="e3c7e-103">`sizeof` işleci, verilen türdeki bir değişken tarafından bulunan bayt sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="e3c7e-103">The `sizeof` operator returns the number of bytes occupied by a variable of a given type.</span></span> <span data-ttu-id="e3c7e-104">`sizeof` işlecinin bağımsız [değişkeni yönetilmeyen bir türün veya yönetilmeyen](../builtin-types/unmanaged-types.md) tür olarak [Kısıtlanmış](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) bir tür parametresinin adı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e3c7e-104">The argument to the `sizeof` operator must be the name of an [unmanaged type](../builtin-types/unmanaged-types.md) or a type parameter that is [constrained](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) to be an unmanaged type.</span></span>

<span data-ttu-id="e3c7e-105">`sizeof` işleci [güvenli olmayan](../keywords/unsafe.md) bir bağlam gerektiriyor.</span><span class="sxs-lookup"><span data-stu-id="e3c7e-105">The `sizeof` operator requires an [unsafe](../keywords/unsafe.md) context.</span></span> <span data-ttu-id="e3c7e-106">Ancak, aşağıdaki tabloda sunulan ifadeler derleme zamanında karşılık gelen sabit değerlere değerlendirilir ve güvenli olmayan bir bağlam gerektirmez:</span><span class="sxs-lookup"><span data-stu-id="e3c7e-106">However, the expressions presented in the following table are evaluated in compile time to the corresponding constant values and don't require an unsafe context:</span></span>

|<span data-ttu-id="e3c7e-107">Expression</span><span class="sxs-lookup"><span data-stu-id="e3c7e-107">Expression</span></span>|<span data-ttu-id="e3c7e-108">Sabit değer</span><span class="sxs-lookup"><span data-stu-id="e3c7e-108">Constant value</span></span>|
|---------|---------------|
|`sizeof(sbyte)`|<span data-ttu-id="e3c7e-109">1</span><span class="sxs-lookup"><span data-stu-id="e3c7e-109">1</span></span>|
|`sizeof(byte)`|<span data-ttu-id="e3c7e-110">1</span><span class="sxs-lookup"><span data-stu-id="e3c7e-110">1</span></span>|
|`sizeof(short)`|<span data-ttu-id="e3c7e-111">2</span><span class="sxs-lookup"><span data-stu-id="e3c7e-111">2</span></span>|
|`sizeof(ushort)`|<span data-ttu-id="e3c7e-112">2</span><span class="sxs-lookup"><span data-stu-id="e3c7e-112">2</span></span>|
|`sizeof(int)`|<span data-ttu-id="e3c7e-113">4</span><span class="sxs-lookup"><span data-stu-id="e3c7e-113">4</span></span>|
|`sizeof(uint)`|<span data-ttu-id="e3c7e-114">4</span><span class="sxs-lookup"><span data-stu-id="e3c7e-114">4</span></span>|
|`sizeof(long)`|<span data-ttu-id="e3c7e-115">8</span><span class="sxs-lookup"><span data-stu-id="e3c7e-115">8</span></span>|
|`sizeof(ulong)`|<span data-ttu-id="e3c7e-116">8</span><span class="sxs-lookup"><span data-stu-id="e3c7e-116">8</span></span>|
|`sizeof(char)`|<span data-ttu-id="e3c7e-117">2</span><span class="sxs-lookup"><span data-stu-id="e3c7e-117">2</span></span>|
|`sizeof(float)`|<span data-ttu-id="e3c7e-118">4</span><span class="sxs-lookup"><span data-stu-id="e3c7e-118">4</span></span>|
|`sizeof(double)`|<span data-ttu-id="e3c7e-119">8</span><span class="sxs-lookup"><span data-stu-id="e3c7e-119">8</span></span>|
|`sizeof(decimal)`|<span data-ttu-id="e3c7e-120">16</span><span class="sxs-lookup"><span data-stu-id="e3c7e-120">16</span></span>|
|`sizeof(bool)`|<span data-ttu-id="e3c7e-121">1</span><span class="sxs-lookup"><span data-stu-id="e3c7e-121">1</span></span>|

<span data-ttu-id="e3c7e-122">Ayrıca, `sizeof` işlecinin işleneni bir [sabit listesi](../builtin-types/enum.md) türünün adı olduğunda güvenli olmayan bir bağlam kullanmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="e3c7e-122">You also don't need to use an unsafe context when the operand of the `sizeof` operator is the name of an [enum](../builtin-types/enum.md) type.</span></span>

<span data-ttu-id="e3c7e-123">Aşağıdaki örnek `sizeof` işlecinin kullanımını gösterir:</span><span class="sxs-lookup"><span data-stu-id="e3c7e-123">The following example demonstrates the usage of the `sizeof` operator:</span></span>

[!code-csharp[sizeof examples](~/samples/csharp/language-reference/operators/SizeOfOperator.cs)]

<span data-ttu-id="e3c7e-124">`sizeof` işleci, yönetilen bellekte ortak dil çalışma zamanı tarafından ayrılacak bayt sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="e3c7e-124">The `sizeof` operator returns a number of bytes that would be allocated by the common language runtime in managed memory.</span></span> <span data-ttu-id="e3c7e-125">[Yapı](../builtin-types/struct.md) türleri için bu değer, yukarıdaki örnekte gösterildiği gibi herhangi bir doldurma içerir.</span><span class="sxs-lookup"><span data-stu-id="e3c7e-125">For [struct](../builtin-types/struct.md) types, that value includes any padding, as the preceding example demonstrates.</span></span> <span data-ttu-id="e3c7e-126">`sizeof` işlecinin sonucu, *yönetilmeyen* bellekteki bir türün boyutunu döndüren <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> yönteminin sonuçlarından farklı olur.</span><span class="sxs-lookup"><span data-stu-id="e3c7e-126">The result of the `sizeof` operator might differ from the result of the <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> method, which returns the size of a type in *unmanaged* memory.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="e3c7e-127">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="e3c7e-127">C# language specification</span></span>

<span data-ttu-id="e3c7e-128">Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [sizeof işleci](~/_csharplang/spec/unsafe-code.md#the-sizeof-operator) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="e3c7e-128">For more information, see [The sizeof operator](~/_csharplang/spec/unsafe-code.md#the-sizeof-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e3c7e-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e3c7e-129">See also</span></span>

- [<span data-ttu-id="e3c7e-130">C#başvurunun</span><span class="sxs-lookup"><span data-stu-id="e3c7e-130">C# reference</span></span>](../index.md)
- [<span data-ttu-id="e3c7e-131">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="e3c7e-131">C# operators</span></span>](index.md)
- [<span data-ttu-id="e3c7e-132">İşaretçiyle ilgili işleçler</span><span class="sxs-lookup"><span data-stu-id="e3c7e-132">Pointer related operators</span></span>](pointer-related-operators.md)
- [<span data-ttu-id="e3c7e-133">İşaretçi türleri</span><span class="sxs-lookup"><span data-stu-id="e3c7e-133">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="e3c7e-134">Bellek ve aralıkla ilgili türler</span><span class="sxs-lookup"><span data-stu-id="e3c7e-134">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
- [<span data-ttu-id="e3c7e-135">.NET 'teki genel türler</span><span class="sxs-lookup"><span data-stu-id="e3c7e-135">Generics in .NET</span></span>](../../../standard/generics/index.md)
