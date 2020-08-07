---
title: stackalloc ifadesi-C# başvurusu
ms.date: 03/13/2020
f1_keywords:
- stackalloc_CSharpKeyword
helpviewer_keywords:
- stackalloc expression [C#]
ms.openlocfilehash: 4f20f3262b77cc2fe16480e53d13960e68d230b5
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916670"
---
# <a name="stackalloc-expression-c-reference"></a><span data-ttu-id="9a783-102">stackalloc ifadesi (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="9a783-102">stackalloc expression (C# reference)</span></span>

<span data-ttu-id="9a783-103">Bir `stackalloc` ifade, yığında bir bellek bloğunu ayırır.</span><span class="sxs-lookup"><span data-stu-id="9a783-103">A `stackalloc` expression allocates a block of memory on the stack.</span></span> <span data-ttu-id="9a783-104">Yöntem yürütme sırasında oluşturulan bir yığın ayrılmış bellek bloğu, bu yöntem döndüğünde otomatik olarak atılır.</span><span class="sxs-lookup"><span data-stu-id="9a783-104">A stack allocated memory block created during the method execution is automatically discarded when that method returns.</span></span> <span data-ttu-id="9a783-105">İle ayrılmış belleği açık bir şekilde serbest bırakılamaz `stackalloc` .</span><span class="sxs-lookup"><span data-stu-id="9a783-105">You cannot explicitly free the memory allocated with `stackalloc`.</span></span> <span data-ttu-id="9a783-106">Yığın tarafından ayrılan bellek bloğu [çöp toplamaya](../../../standard/garbage-collection/index.md) tabi değildir ve bir [ `fixed` ifadesiyle](../keywords/fixed-statement.md)sabitlenemez.</span><span class="sxs-lookup"><span data-stu-id="9a783-106">A stack allocated memory block is not subject to [garbage collection](../../../standard/garbage-collection/index.md) and doesn't have to be pinned with a [`fixed` statement](../keywords/fixed-statement.md).</span></span>

<span data-ttu-id="9a783-107">Bir `stackalloc` ifadenin sonucunu aşağıdaki türlerden birinin değişkenine atayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9a783-107">You can assign the result of a `stackalloc` expression to a variable of one of the following types:</span></span>

- <span data-ttu-id="9a783-108"><xref:System.Span%601?displayProperty=nameWithType>Aşağıdaki örnekte gösterildiği gibi C# 7,2 veya sonraki bir sürümünden itibaren <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> :</span><span class="sxs-lookup"><span data-stu-id="9a783-108">Beginning with C# 7.2, <xref:System.Span%601?displayProperty=nameWithType> or <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, as the following example shows:</span></span>

  [!code-csharp[stackalloc span](snippets/shared/StackallocOperator.cs#AssignToSpan)]

  <span data-ttu-id="9a783-109">Bir veya değişkenine bir yığın ayrılmış bellek bloğu atadığınızda, [güvenli olmayan](../keywords/unsafe.md) bir bağlam kullanmanız gerekmez <xref:System.Span%601> <xref:System.ReadOnlySpan%601> .</span><span class="sxs-lookup"><span data-stu-id="9a783-109">You don't have to use an [unsafe](../keywords/unsafe.md) context when you assign a stack allocated memory block to a <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> variable.</span></span>

  <span data-ttu-id="9a783-110">Bu türlerle çalıştığınızda, `stackalloc` Aşağıdaki örnekte gösterildiği gibi [koşullu](conditional-operator.md) veya atama ifadelerinde bir ifade kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9a783-110">When you work with those types, you can use a `stackalloc` expression in [conditional](conditional-operator.md) or assignment expressions, as the following example shows:</span></span>

  [!code-csharp[stackalloc expression](snippets/shared/StackallocOperator.cs#AsExpression)]

  <span data-ttu-id="9a783-111">C# 8,0 ' den başlayarak, `stackalloc` <xref:System.Span%601> <xref:System.ReadOnlySpan%601> Aşağıdaki örnekte gösterildiği gibi, bir veya değişkenine izin verildiğinde, diğer ifadelerin içindeki bir ifadeyi kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9a783-111">Beginning with C# 8.0, you can use a `stackalloc` expression inside other expressions whenever a <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> variable is allowed, as the following example shows:</span></span>

  [!code-csharp[stackalloc in nested expressions](snippets/shared/StackallocOperator.cs#Nested)]

  > [!NOTE]
  > <span data-ttu-id="9a783-112"><xref:System.Span%601> <xref:System.ReadOnlySpan%601> Mümkün olduğunda yığın tarafından ayrılan bellekle çalışmak için veya türlerini kullanmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="9a783-112">We recommend using <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> types to work with stack allocated memory whenever possible.</span></span>

- <span data-ttu-id="9a783-113">Aşağıdaki örnekte gösterildiği gibi bir [işaretçi türü](../../programming-guide/unsafe-code-pointers/pointer-types.md):</span><span class="sxs-lookup"><span data-stu-id="9a783-113">A [pointer type](../../programming-guide/unsafe-code-pointers/pointer-types.md), as the following example shows:</span></span>

  [!code-csharp[stackalloc pointer](snippets/shared/StackallocOperator.cs#AssignToPointer)]

  <span data-ttu-id="9a783-114">Yukarıdaki örnekte gösterildiği gibi, `unsafe` işaretçi türleriyle çalışırken bir bağlam kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="9a783-114">As the preceding example shows, you must use an `unsafe` context when you work with pointer types.</span></span>

  <span data-ttu-id="9a783-115">İşaretçi türleri söz konusu olduğunda, `stackalloc` değişkeni başlatmak için yalnızca yerel değişken bildiriminde bir ifade kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9a783-115">In the case of pointer types, you can use a `stackalloc` expression only in a local variable declaration to initialize the variable.</span></span>

<span data-ttu-id="9a783-116">Yığındaki kullanılabilir bellek miktarı sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="9a783-116">The amount of memory available on the stack is limited.</span></span> <span data-ttu-id="9a783-117">Yığında çok fazla bellek ayırırsanız, bir oluşturulur <xref:System.StackOverflowException> .</span><span class="sxs-lookup"><span data-stu-id="9a783-117">If you allocate too much memory on the stack, a <xref:System.StackOverflowException> is thrown.</span></span> <span data-ttu-id="9a783-118">Bundan kaçınmak için aşağıdaki kuralları izleyin:</span><span class="sxs-lookup"><span data-stu-id="9a783-118">To avoid that, follow the rules below:</span></span>

- <span data-ttu-id="9a783-119">Tahsis ettiğiniz bellek miktarını sınırlayın `stackalloc` :</span><span class="sxs-lookup"><span data-stu-id="9a783-119">Limit the amount of memory you allocate with `stackalloc`:</span></span>

  [!code-csharp[limit stackalloc](snippets/shared/StackallocOperator.cs#LimitStackalloc)]

  <span data-ttu-id="9a783-120">Yığında kullanılabilir bellek miktarı kodun yürütüldüğü ortama bağlı olduğundan, gerçek sınır değerini tanımlarken koruyucu olun.</span><span class="sxs-lookup"><span data-stu-id="9a783-120">Because the amount of memory available on the stack depends on the environment in which the code is executed, be conservative when you define the actual limit value.</span></span>

- <span data-ttu-id="9a783-121">`stackalloc`İçindeki döngüleri kullanmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="9a783-121">Avoid using `stackalloc` inside loops.</span></span> <span data-ttu-id="9a783-122">Bellek bloğunu bir döngü dışında ayırın ve döngü içinde yeniden kullanın.</span><span class="sxs-lookup"><span data-stu-id="9a783-122">Allocate the memory block outside a loop and reuse it inside the loop.</span></span>

<span data-ttu-id="9a783-123">Yeni ayrılan belleğin içeriği tanımlı değil.</span><span class="sxs-lookup"><span data-stu-id="9a783-123">The content of the newly allocated memory is undefined.</span></span> <span data-ttu-id="9a783-124">Kullanmadan önce onu başlatmalısınız.</span><span class="sxs-lookup"><span data-stu-id="9a783-124">You should initialize it before the use.</span></span> <span data-ttu-id="9a783-125">Örneğin, <xref:System.Span%601.Clear%2A?displayProperty=nameWithType> tüm öğeleri türünün varsayılan değerine ayarlayan yöntemini kullanabilirsiniz `T` .</span><span class="sxs-lookup"><span data-stu-id="9a783-125">For example, you can use the <xref:System.Span%601.Clear%2A?displayProperty=nameWithType> method that sets all the items to the default value of type `T`.</span></span>

<span data-ttu-id="9a783-126">C# 7,3 ' den başlayarak, dizi başlatıcısı sözdizimini kullanarak yeni ayrılan belleğin içeriğini tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9a783-126">Beginning with C# 7.3, you can use array initializer syntax to define the content of the newly allocated memory.</span></span> <span data-ttu-id="9a783-127">Aşağıdaki örnek bunu yapmak için çeşitli yollar göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="9a783-127">The following example demonstrates various ways to do that:</span></span>

[!code-csharp[stackalloc initialization](snippets/shared/StackallocOperator.cs#StackallocInit)]

<span data-ttu-id="9a783-128">İfadesinde `stackalloc T[E]` , `T` yönetilmeyen bir [tür](../builtin-types/unmanaged-types.md) olmalıdır ve `E` negatif olmayan bir [tamsayı](../builtin-types/integral-numeric-types.md) değeri olarak değerlendirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="9a783-128">In expression `stackalloc T[E]`, `T` must be an [unmanaged type](../builtin-types/unmanaged-types.md) and `E` must evaluate to a non-negative [int](../builtin-types/integral-numeric-types.md) value.</span></span>

## <a name="security"></a><span data-ttu-id="9a783-129">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="9a783-129">Security</span></span>

<span data-ttu-id="9a783-130">Kullanımı, `stackalloc` ortak dil çalışma zamanında (CLR) arabellek taşması algılama özelliklerini otomatik olarak etkinleştirmektedir.</span><span class="sxs-lookup"><span data-stu-id="9a783-130">The use of `stackalloc` automatically enables buffer overrun detection features in the common language runtime (CLR).</span></span> <span data-ttu-id="9a783-131">Bir arabellek taşması algılanırsa, kötü amaçlı kodun yürütülmesi olasılığını en aza indirmek için işlem mümkün olduğunca hızlı bir şekilde sonlandırılır.</span><span class="sxs-lookup"><span data-stu-id="9a783-131">If a buffer overrun is detected, the process is terminated as quickly as possible to minimize the chance that malicious code is executed.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="9a783-132">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="9a783-132">C# language specification</span></span>

<span data-ttu-id="9a783-133">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [yığın ayırma](~/_csharplang/spec/unsafe-code.md#stack-allocation) bölümüne ve [ `stackalloc` iç içe bağlamlarda izin ver](~/_csharplang/proposals/csharp-8.0/nested-stackalloc.md) Özellik teklifi notuna bakın.</span><span class="sxs-lookup"><span data-stu-id="9a783-133">For more information, see the [Stack allocation](~/_csharplang/spec/unsafe-code.md#stack-allocation) section of the [C# language specification](~/_csharplang/spec/introduction.md) and the [Permit `stackalloc` in nested contexts](~/_csharplang/proposals/csharp-8.0/nested-stackalloc.md) feature proposal note.</span></span>

## <a name="see-also"></a><span data-ttu-id="9a783-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9a783-134">See also</span></span>

- [<span data-ttu-id="9a783-135">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="9a783-135">C# reference</span></span>](../index.md)
- [<span data-ttu-id="9a783-136">C# işleçleri ve ifadeleri</span><span class="sxs-lookup"><span data-stu-id="9a783-136">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="9a783-137">İşaretçi bağlantılı işleçler</span><span class="sxs-lookup"><span data-stu-id="9a783-137">Pointer related operators</span></span>](pointer-related-operators.md)
- [<span data-ttu-id="9a783-138">İşaretçi türleri</span><span class="sxs-lookup"><span data-stu-id="9a783-138">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="9a783-139">Bellek ve aralıkla ilgili türler</span><span class="sxs-lookup"><span data-stu-id="9a783-139">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
- [<span data-ttu-id="9a783-140">Stackalloc 'un DOS ve yapılmaması</span><span class="sxs-lookup"><span data-stu-id="9a783-140">Dos and Don'ts of stackalloc</span></span>](https://vcsjones.dev/2020/02/24/stackalloc/)
