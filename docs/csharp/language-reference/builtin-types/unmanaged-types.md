---
title: Yönetilmeyen türler- C# başvuru
ms.date: 07/23/2019
helpviewer_keywords:
- unmanaged type [C#]
ms.openlocfilehash: 2b675be5dbc61006725549f4b69284326650401d
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512070"
---
# <a name="unmanaged-types-c-reference"></a><span data-ttu-id="5496b-102">Yönetilmeyen türler (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="5496b-102">Unmanaged types (C# reference)</span></span>

<span data-ttu-id="5496b-103">**Yönetilmeyen tür** , başvuru türü olmayan veya oluşturulmuş tür olmayan (en az bir tür bağımsız değişkeni içeren bir tür) bir tür ve herhangi bir iç içe geçme düzeyinde başvuru türü veya oluşturulmuş tür alanları içermez.</span><span class="sxs-lookup"><span data-stu-id="5496b-103">An **unmanaged type** is any type that isn't a reference type or constructed type (a type that includes at least one type argument), and doesn't contain reference type or constructed type fields at any level of nesting.</span></span> <span data-ttu-id="5496b-104">Diğer bir deyişle, yönetilmeyen bir tür aşağıdakilerden biridir:</span><span class="sxs-lookup"><span data-stu-id="5496b-104">In other words, an unmanaged type is one of the following:</span></span>

- <span data-ttu-id="5496b-105">`sbyte``byte` ,,`int`, ,,`uint`, ,`ulong`,,, ,`double`, veya `float` `long` `ushort` `short` `char` `decimal``bool`</span><span class="sxs-lookup"><span data-stu-id="5496b-105">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, `double`, `decimal`, or `bool`</span></span>
- <span data-ttu-id="5496b-106">Herhangi bir [numaralandırma](../keywords/enum.md) türü</span><span class="sxs-lookup"><span data-stu-id="5496b-106">Any [enum](../keywords/enum.md) type</span></span>
- <span data-ttu-id="5496b-107">Herhangi bir [işaretçi](../../programming-guide/unsafe-code-pointers/pointer-types.md) türü</span><span class="sxs-lookup"><span data-stu-id="5496b-107">Any [pointer](../../programming-guide/unsafe-code-pointers/pointer-types.md) type</span></span>
- <span data-ttu-id="5496b-108">Oluşturulmuş bir tür olmayan ve yalnızca yönetilmeyen türlerin alanlarını içeren Kullanıcı tanımlı herhangi bir [Yapı](../keywords/struct.md) türü</span><span class="sxs-lookup"><span data-stu-id="5496b-108">Any user-defined [struct](../keywords/struct.md) type that is not a constructed type and contains fields of unmanaged types only</span></span>

<span data-ttu-id="5496b-109">7,3 ile C# başlayarak, bir tür parametresinin işaretçiden yönetilmeyen bir tür olduğunu belirtmek için [ `unmanaged` kısıtlamasını](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5496b-109">Beginning with C# 7.3, you can use the [`unmanaged` constraint](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) to specify that a type parameter is a non-pointer unmanaged type.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="5496b-110">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="5496b-110">C# language specification</span></span>

<span data-ttu-id="5496b-111">Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [işaretçi türleri](~/_csharplang/spec/unsafe-code.md#pointer-types) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="5496b-111">For more information, see the [Pointer types](~/_csharplang/spec/unsafe-code.md#pointer-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5496b-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5496b-112">See also</span></span>

- [<span data-ttu-id="5496b-113">C#başvurunun</span><span class="sxs-lookup"><span data-stu-id="5496b-113">C# reference</span></span>](../index.md)
- [<span data-ttu-id="5496b-114">İşaretçi türleri</span><span class="sxs-lookup"><span data-stu-id="5496b-114">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="5496b-115">Bellek ve aralıkla ilgili türler</span><span class="sxs-lookup"><span data-stu-id="5496b-115">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
- [<span data-ttu-id="5496b-116">sizeof işleci</span><span class="sxs-lookup"><span data-stu-id="5496b-116">sizeof operator</span></span>](../operators/sizeof.md)
- [<span data-ttu-id="5496b-117">stackalloc işleci</span><span class="sxs-lookup"><span data-stu-id="5496b-117">stackalloc operator</span></span>](../operators/stackalloc.md)
