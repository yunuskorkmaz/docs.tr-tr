---
title: stackalloc işleci- C# başvuru
ms.date: 09/20/2019
f1_keywords:
- stackalloc_CSharpKeyword
helpviewer_keywords:
- stackalloc operator [C#]
ms.openlocfilehash: 5654cae622cd94c8dad7e58fbc8a99fcf48391a9
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712630"
---
# <a name="stackalloc-operator-c-reference"></a><span data-ttu-id="95793-102">stackalloc işleci (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="95793-102">stackalloc operator (C# reference)</span></span>

<span data-ttu-id="95793-103">`stackalloc` işleci, yığında bir bellek bloğu ayırır.</span><span class="sxs-lookup"><span data-stu-id="95793-103">The `stackalloc` operator allocates a block of memory on the stack.</span></span> <span data-ttu-id="95793-104">Yöntem yürütme sırasında oluşturulan bir yığın ayrılmış bellek bloğu, bu yöntem döndüğünde otomatik olarak atılır.</span><span class="sxs-lookup"><span data-stu-id="95793-104">A stack allocated memory block created during the method execution is automatically discarded when that method returns.</span></span> <span data-ttu-id="95793-105">`stackalloc` işleçle ayrılan belleği açık olarak serbest bırakılamaz.</span><span class="sxs-lookup"><span data-stu-id="95793-105">You cannot explicitly free memory allocated with the `stackalloc` operator.</span></span> <span data-ttu-id="95793-106">Yığın tarafından ayrılan bellek bloğu [çöp toplamaya](../../../standard/garbage-collection/index.md) tabi değildir ve bir [`fixed` ifadesiyle](../keywords/fixed-statement.md)sabitlenmemelidir.</span><span class="sxs-lookup"><span data-stu-id="95793-106">A stack allocated memory block is not subject to [garbage collection](../../../standard/garbage-collection/index.md) and doesn't have to be pinned with a [`fixed` statement](../keywords/fixed-statement.md).</span></span>

<span data-ttu-id="95793-107">`stackalloc` işlecinin sonucunu aşağıdaki türlerden birinin değişkenine atayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="95793-107">You can assign the result of the `stackalloc` operator to a variable of one of the following types:</span></span>

- <span data-ttu-id="95793-108">Aşağıdaki örnekte C# gösterildiği gibi 7,2, <xref:System.Span%601?displayProperty=nameWithType> veya <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>ile başlayarak:</span><span class="sxs-lookup"><span data-stu-id="95793-108">Beginning with C# 7.2, <xref:System.Span%601?displayProperty=nameWithType> or <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, as the following example shows:</span></span>

  [!code-csharp[stackalloc span](~/samples/csharp/language-reference/operators/StackallocOperator.cs#AssignToSpan)]

  <span data-ttu-id="95793-109">Bir <xref:System.Span%601> veya <xref:System.ReadOnlySpan%601> değişkenine bir yığın ayrılmış bellek bloğu atadığınızda, [güvenli olmayan](../keywords/unsafe.md) bir bağlam kullanmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="95793-109">You don't have to use an [unsafe](../keywords/unsafe.md) context when you assign a stack allocated memory block to a <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> variable.</span></span>

  <span data-ttu-id="95793-110">Bu türlerle çalışırken, aşağıdaki örnekte gösterildiği gibi, [koşullu](conditional-operator.md) veya atama ifadelerinde `stackalloc` bir ifade kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="95793-110">When you work with those types, you can use a `stackalloc` expression in [conditional](conditional-operator.md) or assignment expressions, as the following example shows:</span></span>

  [!code-csharp[stackalloc expression](~/samples/csharp/language-reference/operators/StackallocOperator.cs#AsExpression)]

  <span data-ttu-id="95793-111">8,0 ' C# den başlayarak, aşağıdaki örnekte gösterildiği gibi, bir <xref:System.Span%601> veya <xref:System.ReadOnlySpan%601> değişkenine izin verildiğinde diğer ifadelerin içinde `stackalloc` bir ifade kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="95793-111">Beginning with C# 8.0, you can use a `stackalloc` expression inside other expressions whenever a <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> variable is allowed, as the following example shows:</span></span>

  [!code-csharp[stackalloc in nested expressions](~/samples/csharp/language-reference/operators/StackallocOperator.cs#Nested)]

  > [!NOTE]
  > <span data-ttu-id="95793-112">Mümkün olduğunda yığın tarafından ayrılan bellekle çalışmak için <xref:System.Span%601> veya <xref:System.ReadOnlySpan%601> türlerini kullanmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="95793-112">We recommend using <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> types to work with stack allocated memory whenever possible.</span></span>

- <span data-ttu-id="95793-113">Aşağıdaki örnekte gösterildiği gibi bir [işaretçi türü](../../programming-guide/unsafe-code-pointers/pointer-types.md):</span><span class="sxs-lookup"><span data-stu-id="95793-113">A [pointer type](../../programming-guide/unsafe-code-pointers/pointer-types.md), as the following example shows:</span></span>

  [!code-csharp[stackalloc pointer](~/samples/csharp/language-reference/operators/StackallocOperator.cs#AssignToPointer)]

  <span data-ttu-id="95793-114">Yukarıdaki örnekte gösterildiği gibi, işaretçi türleriyle çalışırken `unsafe` bağlamı kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="95793-114">As the preceding example shows, you must use an `unsafe` context when you work with pointer types.</span></span>

  <span data-ttu-id="95793-115">İşaretçi türleri söz konusu olduğunda, değişkeni başlatmak için yalnızca yerel değişken bildiriminde bir `stackalloc` ifadesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="95793-115">In the case of pointer types, you can use a `stackalloc` expression only in a local variable declaration to initialize the variable.</span></span>

<span data-ttu-id="95793-116">Yeni ayrılan belleğin içeriği tanımlı değil.</span><span class="sxs-lookup"><span data-stu-id="95793-116">The content of the newly allocated memory is undefined.</span></span> <span data-ttu-id="95793-117">7,3 ile C# başlayarak, yeni ayrılan belleğin içeriğini tanımlamak için dizi başlatıcısı sözdizimini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="95793-117">Beginning with C# 7.3, you can use array initializer syntax to define the content of the newly allocated memory.</span></span> <span data-ttu-id="95793-118">Aşağıdaki örnek bunu yapmak için çeşitli yollar göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="95793-118">The following example demonstrates various ways to do that:</span></span>

[!code-csharp[stackalloc initialization](~/samples/csharp/language-reference/operators/StackallocOperator.cs#StackallocInit)]

<span data-ttu-id="95793-119">İfade `stackalloc T[E]`, `T` [yönetilmeyen bir tür](../builtin-types/unmanaged-types.md) olmalıdır ve `E` [int](../builtin-types/integral-numeric-types.md)türünde bir ifade olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="95793-119">In expression `stackalloc T[E]`, `T` must be an [unmanaged type](../builtin-types/unmanaged-types.md) and `E` must be an expression of type [int](../builtin-types/integral-numeric-types.md).</span></span>

## <a name="security"></a><span data-ttu-id="95793-120">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="95793-120">Security</span></span>

<span data-ttu-id="95793-121">`stackalloc` kullanımı, ortak dil çalışma zamanında (CLR) arabellek taşması algılama özelliklerini otomatik olarak sunar.</span><span class="sxs-lookup"><span data-stu-id="95793-121">The use of `stackalloc` automatically enables buffer overrun detection features in the common language runtime (CLR).</span></span> <span data-ttu-id="95793-122">Bir arabellek taşması algılanırsa, kötü amaçlı kodun yürütülmesi olasılığını en aza indirmek için işlem mümkün olduğunca hızlı bir şekilde sonlandırılır.</span><span class="sxs-lookup"><span data-stu-id="95793-122">If a buffer overrun is detected, the process is terminated as quickly as possible to minimize the chance that malicious code is executed.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="95793-123">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="95793-123">C# language specification</span></span>

<span data-ttu-id="95793-124">Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [yığın ayırma](~/_csharplang/spec/unsafe-code.md#stack-allocation) bölümüne ve [iç içe bağlamlardaki `stackalloc` izin ver](~/_csharplang/proposals/csharp-8.0/nested-stackalloc.md) Özellik teklifi notuna bakın.</span><span class="sxs-lookup"><span data-stu-id="95793-124">For more information, see the [Stack allocation](~/_csharplang/spec/unsafe-code.md#stack-allocation) section of the [C# language specification](~/_csharplang/spec/introduction.md) and the [Permit `stackalloc` in nested contexts](~/_csharplang/proposals/csharp-8.0/nested-stackalloc.md) feature proposal note.</span></span>

## <a name="see-also"></a><span data-ttu-id="95793-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="95793-125">See also</span></span>

- [<span data-ttu-id="95793-126">C#başvurunun</span><span class="sxs-lookup"><span data-stu-id="95793-126">C# reference</span></span>](../index.md)
- [<span data-ttu-id="95793-127">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="95793-127">C# operators</span></span>](index.md)
- [<span data-ttu-id="95793-128">İşaretçiyle ilgili işleçler</span><span class="sxs-lookup"><span data-stu-id="95793-128">Pointer related operators</span></span>](pointer-related-operators.md)
- [<span data-ttu-id="95793-129">İşaretçi türleri</span><span class="sxs-lookup"><span data-stu-id="95793-129">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="95793-130">Bellek ve aralıkla ilgili türler</span><span class="sxs-lookup"><span data-stu-id="95793-130">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
