---
description: "C 'deki yönetilmeyen türler hakkında bilgi edinin #"
title: Yönetilmeyen türler-C# başvurusu
ms.date: 09/06/2019
helpviewer_keywords:
- unmanaged type [C#]
ms.openlocfilehash: b5a689ca3ade36ef77da958549894f76e074986e
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89143538"
---
# <a name="unmanaged-types-c-reference"></a><span data-ttu-id="ec6c2-103">Yönetilmeyen türler (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="ec6c2-103">Unmanaged types (C# reference)</span></span>

<span data-ttu-id="ec6c2-104">Bir tür, aşağıdaki türlerden biri ise, **yönetilmeyen bir türdür** :</span><span class="sxs-lookup"><span data-stu-id="ec6c2-104">A type is an **unmanaged type** if it's any of the following types:</span></span>

- <span data-ttu-id="ec6c2-105">`sbyte`,,, `byte` `short` `ushort` , `int` , `uint` , `long` , `ulong` , `char` , `float` , `double` , `decimal` , veya `bool`</span><span class="sxs-lookup"><span data-stu-id="ec6c2-105">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, `double`, `decimal`, or `bool`</span></span>
- <span data-ttu-id="ec6c2-106">Herhangi bir [numaralandırma](enum.md) türü</span><span class="sxs-lookup"><span data-stu-id="ec6c2-106">Any [enum](enum.md) type</span></span>
- <span data-ttu-id="ec6c2-107">Herhangi bir [işaretçi](../../programming-guide/unsafe-code-pointers/pointer-types.md) türü</span><span class="sxs-lookup"><span data-stu-id="ec6c2-107">Any [pointer](../../programming-guide/unsafe-code-pointers/pointer-types.md) type</span></span>
- <span data-ttu-id="ec6c2-108">Yalnızca yönetilmeyen türlerin ve C# 7,3 ve önceki sürümlerde bulunan alanları içeren Kullanıcı tanımlı [Yapı](struct.md) türleri, oluşturulmuş bir tür değildir (en az bir tür bağımsız değişkeni içeren bir tür)</span><span class="sxs-lookup"><span data-stu-id="ec6c2-108">Any user-defined [struct](struct.md) type that contains fields of unmanaged types only and, in C# 7.3 and earlier, is not a constructed type (a type that includes at least one type argument)</span></span>

<span data-ttu-id="ec6c2-109">C# 7,3 ' den başlayarak, bir tür parametresinin işaretçi olmayan, null atanamaz yönetilmeyen bir tür olduğunu belirtmek için [ `unmanaged` kısıtlamasını](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ec6c2-109">Beginning with C# 7.3, you can use the [`unmanaged` constraint](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) to specify that a type parameter is a non-pointer, non-nullable unmanaged type.</span></span>

<span data-ttu-id="ec6c2-110">C# 8,0 ' den başlayarak, aşağıdaki örnekte gösterildiği gibi, yönetilmeyen türlerin alanlarını içeren *oluşturulmuş* bir yapı türü de yönetilmdir:</span><span class="sxs-lookup"><span data-stu-id="ec6c2-110">Beginning with C# 8.0, a *constructed* struct type that contains fields of unmanaged types only is also unmanaged, as the following example shows:</span></span>

[!code-csharp[unmanaged constructed types](snippets/UnmanagedTypes.cs#ProgramExample)]

<span data-ttu-id="ec6c2-111">Genel bir yapı, yönetilmeyen ve yönetilmeyen oluşturulmuş türlerin kaynağı olabilir.</span><span class="sxs-lookup"><span data-stu-id="ec6c2-111">A generic struct may be the source of both unmanaged and not unmanaged constructed types.</span></span> <span data-ttu-id="ec6c2-112">Yukarıdaki örnek, genel bir struct tanımlar `Coords<T>` ve yönetilmeyen oluşturulmuş türlerin örneklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ec6c2-112">The preceding example defines a generic struct `Coords<T>` and presents the examples of unmanaged constructed types.</span></span> <span data-ttu-id="ec6c2-113">Yönetilmeyen bir tür örneği `Coords<object>` .</span><span class="sxs-lookup"><span data-stu-id="ec6c2-113">The example of not an unmanaged type is `Coords<object>`.</span></span> <span data-ttu-id="ec6c2-114">Yönetilmeyen değildir çünkü türünde alanları vardır `object` , yönetilmeyen değildir.</span><span class="sxs-lookup"><span data-stu-id="ec6c2-114">It's not unmanaged because it has the fields of the `object` type, which is not unmanaged.</span></span> <span data-ttu-id="ec6c2-115">Oluşturulan *Tüm* türlerin yönetilmeyen türler olmasını istiyorsanız, `unmanaged` genel bir yapının tanımında kısıtlamayı kullanın:</span><span class="sxs-lookup"><span data-stu-id="ec6c2-115">If you want *all* constructed types to be unmanaged types, use the `unmanaged` constraint in the definition of a generic struct:</span></span>

[!code-csharp[unmanaged constraint in type definition](snippets/UnmanagedTypes.cs#AlwaysUnmanaged)]

## <a name="c-language-specification"></a><span data-ttu-id="ec6c2-116">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="ec6c2-116">C# language specification</span></span>

<span data-ttu-id="ec6c2-117">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [işaretçi türleri](~/_csharplang/spec/unsafe-code.md#pointer-types) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="ec6c2-117">For more information, see the [Pointer types](~/_csharplang/spec/unsafe-code.md#pointer-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ec6c2-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ec6c2-118">See also</span></span>

- [<span data-ttu-id="ec6c2-119">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="ec6c2-119">C# reference</span></span>](../index.md)
- [<span data-ttu-id="ec6c2-120">İşaretçi türleri</span><span class="sxs-lookup"><span data-stu-id="ec6c2-120">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="ec6c2-121">Bellek ve aralıkla ilgili türler</span><span class="sxs-lookup"><span data-stu-id="ec6c2-121">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
- [<span data-ttu-id="ec6c2-122">sizeof işleci</span><span class="sxs-lookup"><span data-stu-id="ec6c2-122">sizeof operator</span></span>](../operators/sizeof.md)
- [<span data-ttu-id="ec6c2-123">stackalloc</span><span class="sxs-lookup"><span data-stu-id="ec6c2-123">stackalloc</span></span>](../operators/stackalloc.md)
