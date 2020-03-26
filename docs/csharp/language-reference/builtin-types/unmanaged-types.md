---
title: Yönetilmeyen türler - C# başvurusu
ms.date: 09/06/2019
helpviewer_keywords:
- unmanaged type [C#]
ms.openlocfilehash: 9dd2ab4e044b8a86bfe72a6fcf2481b8e1e80bf4
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79507236"
---
# <a name="unmanaged-types-c-reference"></a><span data-ttu-id="c76b2-102">Yönetilmeyen türler (C# başvurusu)</span><span class="sxs-lookup"><span data-stu-id="c76b2-102">Unmanaged types (C# reference)</span></span>

<span data-ttu-id="c76b2-103">Bir tür, aşağıdaki türlerden herhangi biri yse **yönetilmeyen** bir türdür:</span><span class="sxs-lookup"><span data-stu-id="c76b2-103">A type is an **unmanaged type** if it's any of the following types:</span></span>

- <span data-ttu-id="c76b2-104">`sbyte`, `byte` `short`, `ushort` `int`, `uint` `long`, `ulong` `char`, `float` `double`, `decimal`, , , , veya`bool`</span><span class="sxs-lookup"><span data-stu-id="c76b2-104">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, `double`, `decimal`, or `bool`</span></span>
- <span data-ttu-id="c76b2-105">Herhangi bir [enum](enum.md) türü</span><span class="sxs-lookup"><span data-stu-id="c76b2-105">Any [enum](enum.md) type</span></span>
- <span data-ttu-id="c76b2-106">Herhangi bir [işaretçi](../../programming-guide/unsafe-code-pointers/pointer-types.md) türü</span><span class="sxs-lookup"><span data-stu-id="c76b2-106">Any [pointer](../../programming-guide/unsafe-code-pointers/pointer-types.md) type</span></span>
- <span data-ttu-id="c76b2-107">Yalnızca yönetilmeyen türlerdeki alanları içeren ve C# 7.3 ve daha önce kullanıcı [tarafından](struct.md) tanımlanan yapıt türü yapılı bir tür değildir (en az bir tür bağımsız değişkeniçeren bir tür)</span><span class="sxs-lookup"><span data-stu-id="c76b2-107">Any user-defined [struct](struct.md) type that contains fields of unmanaged types only and, in C# 7.3 and earlier, is not a constructed type (a type that includes at least one type argument)</span></span>

<span data-ttu-id="c76b2-108">C# 7.3 ile başlayarak, [ `unmanaged` bir](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) tür parametresi işaretçi olmayan, nullable yönetilemez bir tür olduğunu belirtmek için kısıtlama kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c76b2-108">Beginning with C# 7.3, you can use the [`unmanaged` constraint](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) to specify that a type parameter is a non-pointer, non-nullable unmanaged type.</span></span>

<span data-ttu-id="c76b2-109">C# 8.0 ile başlayarak, aşağıdaki örnekte görüldüğü gibi, yalnızca yönetilmeyen türlerde alanlar içeren *yapılı* bir yapı türü de yönetilemez:</span><span class="sxs-lookup"><span data-stu-id="c76b2-109">Beginning with C# 8.0, a *constructed* struct type that contains fields of unmanaged types only is also unmanaged, as the following example shows:</span></span>

[!code-csharp[unmanaged constructed types](snippets/UnmanagedTypes.cs#ProgramExample)]

<span data-ttu-id="c76b2-110">Genel bir yapı hem yönetilmeyen hem de yönetilmeyen yapılandırılan türlerin kaynağı olabilir.</span><span class="sxs-lookup"><span data-stu-id="c76b2-110">A generic struct may be the source of both unmanaged and not unmanaged constructed types.</span></span> <span data-ttu-id="c76b2-111">Önceki örnek, genel bir yapı `Coords<T>` tanımlar ve yönetilmeyen yapılandırılan türlere örnekler sunar.</span><span class="sxs-lookup"><span data-stu-id="c76b2-111">The preceding example defines a generic struct `Coords<T>` and presents the examples of unmanaged constructed types.</span></span> <span data-ttu-id="c76b2-112">Yönetilmeyen bir tür değil `Coords<object>`örneğidir.</span><span class="sxs-lookup"><span data-stu-id="c76b2-112">The example of not an unmanaged type is `Coords<object>`.</span></span> <span data-ttu-id="c76b2-113">Yönetilmeyen `object` türdeki alanlara sahip olduğu için yönetilmez.</span><span class="sxs-lookup"><span data-stu-id="c76b2-113">It's not unmanaged because it has the fields of the `object` type, which is not unmanaged.</span></span> <span data-ttu-id="c76b2-114">*Tüm* yapılandırılan türlerin yönetilmeyen türler olmasını `unmanaged` istiyorsanız, genel bir yapının tanımındaki kısıtlamayı kullanın:</span><span class="sxs-lookup"><span data-stu-id="c76b2-114">If you want *all* constructed types to be unmanaged types, use the `unmanaged` constraint in the definition of a generic struct:</span></span>

[!code-csharp[unmanaged constraint in type definition](snippets/UnmanagedTypes.cs#AlwaysUnmanaged)]

## <a name="c-language-specification"></a><span data-ttu-id="c76b2-115">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="c76b2-115">C# language specification</span></span>

<span data-ttu-id="c76b2-116">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Pointer türleri](~/_csharplang/spec/unsafe-code.md#pointer-types) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="c76b2-116">For more information, see the [Pointer types](~/_csharplang/spec/unsafe-code.md#pointer-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c76b2-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c76b2-117">See also</span></span>

- [<span data-ttu-id="c76b2-118">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="c76b2-118">C# reference</span></span>](../index.md)
- [<span data-ttu-id="c76b2-119">İşaretçi türleri</span><span class="sxs-lookup"><span data-stu-id="c76b2-119">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="c76b2-120">Bellek ve aralıkla ilgili türler</span><span class="sxs-lookup"><span data-stu-id="c76b2-120">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
- [<span data-ttu-id="c76b2-121">sizeof işleci</span><span class="sxs-lookup"><span data-stu-id="c76b2-121">sizeof operator</span></span>](../operators/sizeof.md)
- [<span data-ttu-id="c76b2-122">stackalloc</span><span class="sxs-lookup"><span data-stu-id="c76b2-122">stackalloc</span></span>](../operators/stackalloc.md)
