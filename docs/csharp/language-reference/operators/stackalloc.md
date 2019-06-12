---
title: stackalloc işleci - C# başvurusu
ms.custom: seodec18
ms.date: 06/10/2019
f1_keywords:
- stackalloc_CSharpKeyword
helpviewer_keywords:
- stackalloc operator [C#]
ms.openlocfilehash: 3be4e827e75e4e26a34d9ed70423af5aa317e7fb
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025008"
---
# <a name="stackalloc-operator-c-reference"></a><span data-ttu-id="9874d-102">stackalloc işleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="9874d-102">stackalloc operator (C# reference)</span></span>

<span data-ttu-id="9874d-103">`stackalloc` İşleci bir yığında bellek bloğu ayırır.</span><span class="sxs-lookup"><span data-stu-id="9874d-103">The `stackalloc` operator allocates a block of memory on the stack.</span></span> <span data-ttu-id="9874d-104">Bu yöntem döndürüldüğünde ayrılmış bellek bloğu yöntem yürütme işlemi sırasında oluşturulan bir yığın otomatik olarak atılır.</span><span class="sxs-lookup"><span data-stu-id="9874d-104">A stack allocated memory block created during the method execution is automatically discarded when that method returns.</span></span> <span data-ttu-id="9874d-105">Açıkça atanan bellek bırakılamıyor `stackalloc` işleci.</span><span class="sxs-lookup"><span data-stu-id="9874d-105">You cannot explicitly free memory allocated with the `stackalloc` operator.</span></span> <span data-ttu-id="9874d-106">Bir yığın ayrılmış bellek bloğu konusu değil [çöp toplama](../../../standard/garbage-collection/index.md) ve sabitlenmiş olmak zorunda değildir [ `fixed` deyimi](../keywords/fixed-statement.md).</span><span class="sxs-lookup"><span data-stu-id="9874d-106">A stack allocated memory block is not subject to [garbage collection](../../../standard/garbage-collection/index.md) and doesn't have to be pinned with the [`fixed` statement](../keywords/fixed-statement.md).</span></span>

<span data-ttu-id="9874d-107">Sonucu atayabilirsiniz `stackalloc` şu türlerden birinde bir değişkene işleci:</span><span class="sxs-lookup"><span data-stu-id="9874d-107">You can assign the result of the `stackalloc` operator to a variable of one of the following types:</span></span>

- <span data-ttu-id="9874d-108">İle başlayarak C# 7.2, <xref:System.Span%601?displayProperty=nameWithType> veya <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>aşağıdaki örnekte gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="9874d-108">Starting with C# 7.2, <xref:System.Span%601?displayProperty=nameWithType> or <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, as the following example shows:</span></span>

  [!code-csharp[stackalloc span](~/samples/csharp/language-reference/operators/StackallocOperator.cs#AssignToSpan)]

  <span data-ttu-id="9874d-109">Kullanmak zorunda değilsiniz bir [güvenli olmayan](../keywords/unsafe.md) yığın atadığınızda içerik ayrılan bellek bloğu için bir <xref:System.Span%601> veya <xref:System.ReadOnlySpan%601> değişkeni.</span><span class="sxs-lookup"><span data-stu-id="9874d-109">You don't have to use an [unsafe](../keywords/unsafe.md) context when you assign a stack allocated memory block to a <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> variable.</span></span>

  <span data-ttu-id="9874d-110">Bu türler ile çalışırken kullanabileceğiniz bir `stackalloc` ifadesinde [koşullu](conditional-operator.md) veya atama ifadeleri, aşağıdaki örnekte gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="9874d-110">When you work with those types, you can use a `stackalloc` expression in [conditional](conditional-operator.md) or assignment expressions, as the following example shows:</span></span>

  [!code-csharp[stackalloc expression](~/samples/csharp/language-reference/operators/StackallocOperator.cs#AsExpression)]

  > [!NOTE]
  > <span data-ttu-id="9874d-111">Kullanmanızı öneririz <xref:System.Span%601> veya <xref:System.ReadOnlySpan%601> ayrılan bellek mümkün olduğunda yığın ile çalışmak için türleri.</span><span class="sxs-lookup"><span data-stu-id="9874d-111">We recommend using <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> types to work with stack allocated memory whenever possible.</span></span>

- <span data-ttu-id="9874d-112">A [işaretçi türü](../../programming-guide/unsafe-code-pointers/pointer-types.md)aşağıdaki örnekte gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="9874d-112">A [pointer type](../../programming-guide/unsafe-code-pointers/pointer-types.md), as the following example shows:</span></span>

  [!code-csharp[stackalloc pointer](~/samples/csharp/language-reference/operators/StackallocOperator.cs#AssignToPointer)]

  <span data-ttu-id="9874d-113">Yukarıdaki örnekte gösterildiği gibi kullanmalısınız bir `unsafe` işaretçi türleri ile çalışırken bağlamı.</span><span class="sxs-lookup"><span data-stu-id="9874d-113">As the preceding example shows, you must use an `unsafe` context when you work with pointer types.</span></span>

<span data-ttu-id="9874d-114">Yeni ayrılan bellek içeriğini tanımsızdır.</span><span class="sxs-lookup"><span data-stu-id="9874d-114">The content of the newly allocated memory is undefined.</span></span> <span data-ttu-id="9874d-115">İle başlayarak C# 7.3, yeni ayrılan bellek içeriğini tanımlamasını dizi Başlatıcısı sözdizimi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9874d-115">Starting with C# 7.3, you can use array initializer syntax to define the content of the newly allocated memory.</span></span> <span data-ttu-id="9874d-116">Aşağıdaki örnek, bunu yapmak için çeşitli yollar gösterir:</span><span class="sxs-lookup"><span data-stu-id="9874d-116">The following example demonstrates various ways to do that:</span></span>

[!code-csharp[stackalloc initialization](~/samples/csharp/language-reference/operators/StackallocOperator.cs#StackallocInit)]

## <a name="security"></a><span data-ttu-id="9874d-117">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="9874d-117">Security</span></span>

<span data-ttu-id="9874d-118">Kullanımını `stackalloc` otomatik olarak ortak dil çalışma zamanı (CLR) arabellek taşması algılama özelliklerini etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="9874d-118">The use of `stackalloc` automatically enables buffer overrun detection features in the common language runtime (CLR).</span></span> <span data-ttu-id="9874d-119">İşlem, bir arabellek taşması algılanırsa, kötü amaçlı kod yürütülür olasılığını en aza indirmek için mümkün olan en kısa sürede sonlandırılır.</span><span class="sxs-lookup"><span data-stu-id="9874d-119">If a buffer overrun is detected, the process is terminated as quickly as possible to minimize the chance that malicious code is executed.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="9874d-120">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="9874d-120">C# language specification</span></span>

<span data-ttu-id="9874d-121">Daha fazla bilgi için [yığın ayırma](~/_csharplang/spec/unsafe-code.md#stack-allocation) bölümünü [ C# dil belirtimi](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="9874d-121">For more information, see the [Stack allocation](~/_csharplang/spec/unsafe-code.md#stack-allocation) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9874d-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9874d-122">See also</span></span>

- [<span data-ttu-id="9874d-123">C#başvuru</span><span class="sxs-lookup"><span data-stu-id="9874d-123">C# reference</span></span>](../index.md)
- [<span data-ttu-id="9874d-124">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="9874d-124">C# operators</span></span>](index.md)
- [<span data-ttu-id="9874d-125">İşaretçi bağlantılı işleçleri</span><span class="sxs-lookup"><span data-stu-id="9874d-125">Pointer related operators</span></span>](pointer-related-operators.md)
- [<span data-ttu-id="9874d-126">İşaretçi türleri</span><span class="sxs-lookup"><span data-stu-id="9874d-126">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="9874d-127">Bellek ve aralıkla ilgili türler</span><span class="sxs-lookup"><span data-stu-id="9874d-127">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
