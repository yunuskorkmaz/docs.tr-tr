---
title: stackalloc işleci- C# başvuru
ms.custom: seodec18
ms.date: 09/20/2019
f1_keywords:
- stackalloc_CSharpKeyword
helpviewer_keywords:
- stackalloc operator [C#]
ms.openlocfilehash: 9ef5f98f2b4973c5873417ecc9a71c187e7299b9
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182424"
---
# <a name="stackalloc-operator-c-reference"></a><span data-ttu-id="2c4e8-102">stackalloc işleci (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="2c4e8-102">stackalloc operator (C# reference)</span></span>

<span data-ttu-id="2c4e8-103">`stackalloc` İşleci, yığında bir bellek bloğu ayırır.</span><span class="sxs-lookup"><span data-stu-id="2c4e8-103">The `stackalloc` operator allocates a block of memory on the stack.</span></span> <span data-ttu-id="2c4e8-104">Yöntem yürütme sırasında oluşturulan bir yığın ayrılmış bellek bloğu, bu yöntem döndüğünde otomatik olarak atılır.</span><span class="sxs-lookup"><span data-stu-id="2c4e8-104">A stack allocated memory block created during the method execution is automatically discarded when that method returns.</span></span> <span data-ttu-id="2c4e8-105">`stackalloc` İşleçle ayrılan belleği açık olarak serbest bırakılamaz.</span><span class="sxs-lookup"><span data-stu-id="2c4e8-105">You cannot explicitly free memory allocated with the `stackalloc` operator.</span></span> <span data-ttu-id="2c4e8-106">Yığın tarafından ayrılan bir bellek bloğu [çöp toplamaya](../../../standard/garbage-collection/index.md) tabi değildir ve [ `fixed` ifadesiyle](../keywords/fixed-statement.md)sabitlenmiş olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="2c4e8-106">A stack allocated memory block is not subject to [garbage collection](../../../standard/garbage-collection/index.md) and doesn't have to be pinned with the [`fixed` statement](../keywords/fixed-statement.md).</span></span>

<span data-ttu-id="2c4e8-107">İfadesinde `stackalloc T[E]` `E` `int`, `T` [yönetilmeyen bir tür](../builtin-types/unmanaged-types.md) olmalıdır ve türünde bir ifade olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2c4e8-107">In expression `stackalloc T[E]`, `T` must be an [unmanaged type](../builtin-types/unmanaged-types.md) and `E` must be an expression of type `int`.</span></span>

<span data-ttu-id="2c4e8-108">`stackalloc` İşlecin sonucunu aşağıdaki türlerden birinin değişkenine atayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="2c4e8-108">You can assign the result of the `stackalloc` operator to a variable of one of the following types:</span></span>

- <span data-ttu-id="2c4e8-109">Aşağıdaki örnekte C# gösterildiği gibi <xref:System.Span%601?displayProperty=nameWithType> 7,2 <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>veya sonraki bir sürümünden itibaren:</span><span class="sxs-lookup"><span data-stu-id="2c4e8-109">Starting with C# 7.2, <xref:System.Span%601?displayProperty=nameWithType> or <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, as the following example shows:</span></span>

  [!code-csharp[stackalloc span](~/samples/csharp/language-reference/operators/StackallocOperator.cs#AssignToSpan)]

  <span data-ttu-id="2c4e8-110">Bir<xref:System.Span%601> veya<xref:System.ReadOnlySpan%601> değişkenine bir yığın ayrılmış bellek bloğu atadığınızda, [güvenli olmayan](../keywords/unsafe.md) bir bağlam kullanmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="2c4e8-110">You don't have to use an [unsafe](../keywords/unsafe.md) context when you assign a stack allocated memory block to a <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> variable.</span></span>

  <span data-ttu-id="2c4e8-111">Bu türlerle çalıştığınızda, aşağıdaki örnekte gösterildiği gibi [koşullu](conditional-operator.md) veya atama `stackalloc` ifadelerinde bir ifade kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="2c4e8-111">When you work with those types, you can use a `stackalloc` expression in [conditional](conditional-operator.md) or assignment expressions, as the following example shows:</span></span>

  [!code-csharp[stackalloc expression](~/samples/csharp/language-reference/operators/StackallocOperator.cs#AsExpression)]

  <span data-ttu-id="2c4e8-112">Aşağıdaki örnekte C# gösterildiği gibi, 8,0 ile başlayarak `stackalloc` , bir <xref:System.Span%601> veya <xref:System.ReadOnlySpan%601> değişkenine izin verildiğinde, diğer ifadelerin içindeki bir ifadeyi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2c4e8-112">Starting with C# 8.0, you can use a `stackalloc` expression inside other expressions whenever a <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> variable is allowed, as the following example shows:</span></span>

  [!code-csharp[stackalloc in nested expressions](~/samples/csharp/language-reference/operators/StackallocOperator.cs#Nested)]

  > [!NOTE]
  > <span data-ttu-id="2c4e8-113">Mümkün olduğunda yığın <xref:System.Span%601> tarafından <xref:System.ReadOnlySpan%601> ayrılan bellekle çalışmak için veya türlerini kullanmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="2c4e8-113">We recommend using <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> types to work with stack allocated memory whenever possible.</span></span>

- <span data-ttu-id="2c4e8-114">Aşağıdaki örnekte gösterildiği gibi bir [işaretçi türü](../../programming-guide/unsafe-code-pointers/pointer-types.md):</span><span class="sxs-lookup"><span data-stu-id="2c4e8-114">A [pointer type](../../programming-guide/unsafe-code-pointers/pointer-types.md), as the following example shows:</span></span>

  [!code-csharp[stackalloc pointer](~/samples/csharp/language-reference/operators/StackallocOperator.cs#AssignToPointer)]

  <span data-ttu-id="2c4e8-115">Yukarıdaki örnekte gösterildiği gibi, işaretçi türleriyle çalışırken bir `unsafe` bağlam kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2c4e8-115">As the preceding example shows, you must use an `unsafe` context when you work with pointer types.</span></span>

  <span data-ttu-id="2c4e8-116">İşaretçi türleri söz konusu olduğunda, değişkeni başlatmak için yalnızca yerel `stackalloc` değişken bildiriminde bir ifade kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2c4e8-116">In the case of pointer types, you can use a `stackalloc` expression only in a local variable declaration to initialize the variable.</span></span>

<span data-ttu-id="2c4e8-117">Yeni ayrılan belleğin içeriği tanımlı değil.</span><span class="sxs-lookup"><span data-stu-id="2c4e8-117">The content of the newly allocated memory is undefined.</span></span> <span data-ttu-id="2c4e8-118">7,3 ile C# başlayarak, yeni ayrılan belleğin içeriğini tanımlamak için dizi başlatıcısı sözdizimini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2c4e8-118">Starting with C# 7.3, you can use array initializer syntax to define the content of the newly allocated memory.</span></span> <span data-ttu-id="2c4e8-119">Aşağıdaki örnek bunu yapmak için çeşitli yollar göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="2c4e8-119">The following example demonstrates various ways to do that:</span></span>

[!code-csharp[stackalloc initialization](~/samples/csharp/language-reference/operators/StackallocOperator.cs#StackallocInit)]

## <a name="security"></a><span data-ttu-id="2c4e8-120">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="2c4e8-120">Security</span></span>

<span data-ttu-id="2c4e8-121">Kullanımı, ortak `stackalloc` dil çalışma zamanında (CLR) arabellek taşması algılama özelliklerini otomatik olarak etkinleştirmektedir.</span><span class="sxs-lookup"><span data-stu-id="2c4e8-121">The use of `stackalloc` automatically enables buffer overrun detection features in the common language runtime (CLR).</span></span> <span data-ttu-id="2c4e8-122">Bir arabellek taşması algılanırsa, kötü amaçlı kodun yürütülmesi olasılığını en aza indirmek için işlem mümkün olduğunca hızlı bir şekilde sonlandırılır.</span><span class="sxs-lookup"><span data-stu-id="2c4e8-122">If a buffer overrun is detected, the process is terminated as quickly as possible to minimize the chance that malicious code is executed.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="2c4e8-123">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="2c4e8-123">C# language specification</span></span>

<span data-ttu-id="2c4e8-124">Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [yığın ayırma](~/_csharplang/spec/unsafe-code.md#stack-allocation) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="2c4e8-124">For more information, see the [Stack allocation](~/_csharplang/spec/unsafe-code.md#stack-allocation) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2c4e8-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2c4e8-125">See also</span></span>

- [<span data-ttu-id="2c4e8-126">C#başvurunun</span><span class="sxs-lookup"><span data-stu-id="2c4e8-126">C# reference</span></span>](../index.md)
- [<span data-ttu-id="2c4e8-127">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="2c4e8-127">C# operators</span></span>](index.md)
- [<span data-ttu-id="2c4e8-128">İşaretçiyle ilgili işleçler</span><span class="sxs-lookup"><span data-stu-id="2c4e8-128">Pointer related operators</span></span>](pointer-related-operators.md)
- [<span data-ttu-id="2c4e8-129">İşaretçi türleri</span><span class="sxs-lookup"><span data-stu-id="2c4e8-129">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="2c4e8-130">Bellek ve aralıkla ilgili türler</span><span class="sxs-lookup"><span data-stu-id="2c4e8-130">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
