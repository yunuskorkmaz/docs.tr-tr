---
title: Yönetilmeyen türler- C# başvuru
ms.date: 09/06/2019
helpviewer_keywords:
- unmanaged type [C#]
ms.openlocfilehash: 81eef59ceb20bcae6c749dd59578ce35da253826
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204481"
---
# <a name="unmanaged-types-c-reference"></a><span data-ttu-id="b59fa-102">Yönetilmeyen türler (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="b59fa-102">Unmanaged types (C# reference)</span></span>

<span data-ttu-id="b59fa-103">Bir tür, aşağıdaki türlerden biri ise, **yönetilmeyen bir türdür** :</span><span class="sxs-lookup"><span data-stu-id="b59fa-103">A type is an **unmanaged type** if it's any of the following types:</span></span>

- <span data-ttu-id="b59fa-104">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, `double`, `decimal`veya `bool`</span><span class="sxs-lookup"><span data-stu-id="b59fa-104">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, `double`, `decimal`, or `bool`</span></span>
- <span data-ttu-id="b59fa-105">Herhangi bir [numaralandırma](../keywords/enum.md) türü</span><span class="sxs-lookup"><span data-stu-id="b59fa-105">Any [enum](../keywords/enum.md) type</span></span>
- <span data-ttu-id="b59fa-106">Herhangi bir [işaretçi](../../programming-guide/unsafe-code-pointers/pointer-types.md) türü</span><span class="sxs-lookup"><span data-stu-id="b59fa-106">Any [pointer](../../programming-guide/unsafe-code-pointers/pointer-types.md) type</span></span>
- <span data-ttu-id="b59fa-107">Yalnızca yönetilmeyen türlerin ve [](../keywords/struct.md) 7,3 ve önceki sürümlerde bulunan C# alanları içeren Kullanıcı tanımlı herhangi bir yapı türü, oluşturulmuş bir tür değildir (en az bir tür bağımsız değişkeni içeren bir tür)</span><span class="sxs-lookup"><span data-stu-id="b59fa-107">Any user-defined [struct](../keywords/struct.md) type that contains fields of unmanaged types only and, in C# 7.3 and earlier, is not a constructed type (a type that includes at least one type argument)</span></span>

<span data-ttu-id="b59fa-108">7,3 ile C# başlayarak, bir tür parametresinin işaretçi olmayan, null atanamaz yönetilmeyen bir tür olduğunu belirtmek için [`unmanaged` kısıtlamasını](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b59fa-108">Beginning with C# 7.3, you can use the [`unmanaged` constraint](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) to specify that a type parameter is a non-pointer, non-nullable unmanaged type.</span></span>

<span data-ttu-id="b59fa-109">8,0 ' C# den başlayarak, aşağıdaki örnekte gösterildiği gibi, yalnızca yönetilmeyen türlerin alanlarını içeren *oluşturulmuş* bir yapı türü de yönetilmez:</span><span class="sxs-lookup"><span data-stu-id="b59fa-109">Beginning with C# 8.0, a *constructed* struct type that contains fields of unmanaged types only is also unmanaged, as the following example shows:</span></span>

[!code-csharp[unmanaged constructed types](~/samples/csharp/language-reference/builtin-types/UnmanagedTypes.cs#ProgramExample)]

<span data-ttu-id="b59fa-110">Genel bir yapı, yönetilmeyen ve yönetilmeyen oluşturulmuş türlerin kaynağı olabilir.</span><span class="sxs-lookup"><span data-stu-id="b59fa-110">A generic struct may be the source of both unmanaged and not unmanaged constructed types.</span></span> <span data-ttu-id="b59fa-111">Yukarıdaki örnek, `Coords<T>` genel bir struct tanımlar ve yönetilmeyen oluşturulmuş türlerin örneklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b59fa-111">The preceding example defines a generic struct `Coords<T>` and presents the examples of unmanaged constructed types.</span></span> <span data-ttu-id="b59fa-112">Yönetilmeyen tür olmayan örnek `Coords<object>`.</span><span class="sxs-lookup"><span data-stu-id="b59fa-112">The example of not an unmanaged type is `Coords<object>`.</span></span> <span data-ttu-id="b59fa-113">Yönetilmeyen olmayan `object` türünde alanlar içerdiğinden, yönetilmeyen değildir.</span><span class="sxs-lookup"><span data-stu-id="b59fa-113">It's not unmanaged because it has the fields of the `object` type, which is not unmanaged.</span></span> <span data-ttu-id="b59fa-114">Oluşturulan *Tüm* türlerin yönetilmeyen türler olmasını istiyorsanız, genel bir yapının tanımındaki `unmanaged` kısıtlamasını kullanın:</span><span class="sxs-lookup"><span data-stu-id="b59fa-114">If you want *all* constructed types to be unmanaged types, use the `unmanaged` constraint in the definition of a generic struct:</span></span>

[!code-csharp[unmanaged constraint in type definition](~/samples/csharp/language-reference/builtin-types/UnmanagedTypes.cs#AlwaysUnmanaged)]

## <a name="c-language-specification"></a><span data-ttu-id="b59fa-115">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="b59fa-115">C# language specification</span></span>

<span data-ttu-id="b59fa-116">Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [işaretçi türleri](~/_csharplang/spec/unsafe-code.md#pointer-types) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="b59fa-116">For more information, see the [Pointer types](~/_csharplang/spec/unsafe-code.md#pointer-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b59fa-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b59fa-117">See also</span></span>

- [<span data-ttu-id="b59fa-118">C#başvurunun</span><span class="sxs-lookup"><span data-stu-id="b59fa-118">C# reference</span></span>](../index.md)
- [<span data-ttu-id="b59fa-119">İşaretçi türleri</span><span class="sxs-lookup"><span data-stu-id="b59fa-119">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="b59fa-120">Bellek ve aralıkla ilgili türler</span><span class="sxs-lookup"><span data-stu-id="b59fa-120">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
- [<span data-ttu-id="b59fa-121">sizeof işleci</span><span class="sxs-lookup"><span data-stu-id="b59fa-121">sizeof operator</span></span>](../operators/sizeof.md)
- [<span data-ttu-id="b59fa-122">stackalloc işleci</span><span class="sxs-lookup"><span data-stu-id="b59fa-122">stackalloc operator</span></span>](../operators/stackalloc.md)
