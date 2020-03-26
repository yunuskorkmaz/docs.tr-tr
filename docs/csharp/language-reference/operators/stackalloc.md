---
title: stackalloc ifade - C# referans
ms.date: 03/13/2020
f1_keywords:
- stackalloc_CSharpKeyword
helpviewer_keywords:
- stackalloc expression [C#]
ms.openlocfilehash: 2e99ce8b1e44dfa040c1acac799a3a55b375bd91
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/19/2020
ms.locfileid: "79546607"
---
# <a name="stackalloc-expression-c-reference"></a><span data-ttu-id="c5c05-102">stackalloc ifadesi (C# başvurusu)</span><span class="sxs-lookup"><span data-stu-id="c5c05-102">stackalloc expression (C# reference)</span></span>

<span data-ttu-id="c5c05-103">İfade, `stackalloc` yığında bellek bloğunu ayırır.</span><span class="sxs-lookup"><span data-stu-id="c5c05-103">A `stackalloc` expression allocates a block of memory on the stack.</span></span> <span data-ttu-id="c5c05-104">Yöntem yürütülmesi sırasında oluşturulan bir yığın ayrılmış bellek bloğu, yöntem döndüğünde otomatik olarak atılır.</span><span class="sxs-lookup"><span data-stu-id="c5c05-104">A stack allocated memory block created during the method execution is automatically discarded when that method returns.</span></span> <span data-ttu-id="c5c05-105">'ile ayrılan belleği açıkça `stackalloc`serbest kalamazsınız.</span><span class="sxs-lookup"><span data-stu-id="c5c05-105">You cannot explicitly free the memory allocated with `stackalloc`.</span></span> <span data-ttu-id="c5c05-106">Yığın ayrılmış bellek bloğu çöp [toplama](../../../standard/garbage-collection/index.md) tabi değildir ve bir [ `fixed` deyim](../keywords/fixed-statement.md)ile sabitlenmiş olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="c5c05-106">A stack allocated memory block is not subject to [garbage collection](../../../standard/garbage-collection/index.md) and doesn't have to be pinned with a [`fixed` statement](../keywords/fixed-statement.md).</span></span>

<span data-ttu-id="c5c05-107">Bir `stackalloc` ifadenin sonucunu aşağıdaki türlerden birinin değişkenine atayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c5c05-107">You can assign the result of a `stackalloc` expression to a variable of one of the following types:</span></span>

- <span data-ttu-id="c5c05-108">C# 7.2 <xref:System.Span%601?displayProperty=nameWithType> ile <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>başlayarak veya aşağıdaki örnekte görüldüğü gibi:</span><span class="sxs-lookup"><span data-stu-id="c5c05-108">Beginning with C# 7.2, <xref:System.Span%601?displayProperty=nameWithType> or <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, as the following example shows:</span></span>

  [!code-csharp[stackalloc span](snippets/StackallocOperator.cs#AssignToSpan)]

  <span data-ttu-id="c5c05-109">Bir yığın ayrılmış bellek [unsafe](../keywords/unsafe.md) bloğu bir <xref:System.Span%601> veya <xref:System.ReadOnlySpan%601> değişkenata atadığınızda güvenli olmayan bir bağlam kullanmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="c5c05-109">You don't have to use an [unsafe](../keywords/unsafe.md) context when you assign a stack allocated memory block to a <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> variable.</span></span>

  <span data-ttu-id="c5c05-110">Bu türlerle çalışırken, aşağıdaki örnekte görüldüğü gibi `stackalloc` [koşullu](conditional-operator.md) veya atama ifadelerinde bir ifade kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c5c05-110">When you work with those types, you can use a `stackalloc` expression in [conditional](conditional-operator.md) or assignment expressions, as the following example shows:</span></span>

  [!code-csharp[stackalloc expression](snippets/StackallocOperator.cs#AsExpression)]

  <span data-ttu-id="c5c05-111">C# 8.0 ile başlayarak, `stackalloc` aşağıdaki örnekte görüldüğü <xref:System.Span%601> gibi, bir veya <xref:System.ReadOnlySpan%601> değişkene izin verildiğinde diğer ifadelerin içinde bir ifade kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c5c05-111">Beginning with C# 8.0, you can use a `stackalloc` expression inside other expressions whenever a <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> variable is allowed, as the following example shows:</span></span>

  [!code-csharp[stackalloc in nested expressions](snippets/StackallocOperator.cs#Nested)]

  > [!NOTE]
  > <span data-ttu-id="c5c05-112">Mümkün olduğunda <xref:System.Span%601> <xref:System.ReadOnlySpan%601> yığın ayrılmış bellekle çalışmak için kullanmanızı veya türleri kullanmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="c5c05-112">We recommend using <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> types to work with stack allocated memory whenever possible.</span></span>

- <span data-ttu-id="c5c05-113">Aşağıdaki örnekte görüldüğü gibi bir [işaretçi türü:](../../programming-guide/unsafe-code-pointers/pointer-types.md)</span><span class="sxs-lookup"><span data-stu-id="c5c05-113">A [pointer type](../../programming-guide/unsafe-code-pointers/pointer-types.md), as the following example shows:</span></span>

  [!code-csharp[stackalloc pointer](snippets/StackallocOperator.cs#AssignToPointer)]

  <span data-ttu-id="c5c05-114">Önceki örnekte de görüldüğü gibi, `unsafe` işaretçi türleri ile çalışırken bir bağlam kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c5c05-114">As the preceding example shows, you must use an `unsafe` context when you work with pointer types.</span></span>

  <span data-ttu-id="c5c05-115">İşaretçi türleri söz konusu olduğunda, `stackalloc` değişkeni başlatmak için yalnızca yerel bir değişken bildiriminde bir ifade kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c5c05-115">In the case of pointer types, you can use a `stackalloc` expression only in a local variable declaration to initialize the variable.</span></span>

<span data-ttu-id="c5c05-116">Yığında bulunan bellek miktarı sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="c5c05-116">The amount of memory available on the stack is limited.</span></span> <span data-ttu-id="c5c05-117">Yığına çok fazla bellek ayırırsanız, <xref:System.StackOverflowException> bir atılır.</span><span class="sxs-lookup"><span data-stu-id="c5c05-117">If you allocate too much memory on the stack, a <xref:System.StackOverflowException> is thrown.</span></span> <span data-ttu-id="c5c05-118">Bunu önlemek için aşağıdaki kurallara uyun:</span><span class="sxs-lookup"><span data-stu-id="c5c05-118">To avoid that, follow the rules below:</span></span>

- <span data-ttu-id="c5c05-119">Ayırdığınız bellek miktarını `stackalloc`sınırlandırın:</span><span class="sxs-lookup"><span data-stu-id="c5c05-119">Limit the amount of memory you allocate with `stackalloc`:</span></span>

  [!code-csharp[limit stackalloc](snippets/StackallocOperator.cs#LimitStackalloc)]

  <span data-ttu-id="c5c05-120">Yığında kullanılabilir bellek miktarı kodun yürütüldürün bulunduğu ortama bağlı olduğundan, gerçek sınır değerini tanımlarken tutucu olun.</span><span class="sxs-lookup"><span data-stu-id="c5c05-120">Because the amount of memory available on the stack depends on the environment in which the code is executed, be conservative when you define the actual limit value.</span></span>

- <span data-ttu-id="c5c05-121">İç `stackalloc` döngüleri kullanmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="c5c05-121">Avoid using `stackalloc` inside loops.</span></span> <span data-ttu-id="c5c05-122">Bellek bloğunu bir döngünün dışına ayırın ve döngü içinde yeniden kullanın.</span><span class="sxs-lookup"><span data-stu-id="c5c05-122">Allocate the memory block outside a loop and reuse it inside the loop.</span></span>

<span data-ttu-id="c5c05-123">Yeni ayrılan belleğin içeriği tanımsız.</span><span class="sxs-lookup"><span data-stu-id="c5c05-123">The content of the newly allocated memory is undefined.</span></span> <span data-ttu-id="c5c05-124">Kullanmadan önce paranızı almalısınız.</span><span class="sxs-lookup"><span data-stu-id="c5c05-124">You should initialize it before the use.</span></span> <span data-ttu-id="c5c05-125">Örneğin, tüm öğeleri <xref:System.Span%601.Clear%2A?displayProperty=nameWithType> varsayılan değer türüne `T`ayarlayan yöntemi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c5c05-125">For example, you can use the <xref:System.Span%601.Clear%2A?displayProperty=nameWithType> method that sets all the items to the default value of type `T`.</span></span>

<span data-ttu-id="c5c05-126">C# 7.3 ile başlayarak, yeni ayrılan belleğin içeriğini tanımlamak için dizi başlandırıcı sözdizimini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c5c05-126">Beginning with C# 7.3, you can use array initializer syntax to define the content of the newly allocated memory.</span></span> <span data-ttu-id="c5c05-127">Aşağıdaki örnek, bunu yapmanın çeşitli yollarını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="c5c05-127">The following example demonstrates various ways to do that:</span></span>

[!code-csharp[stackalloc initialization](snippets/StackallocOperator.cs#StackallocInit)]

<span data-ttu-id="c5c05-128">`stackalloc T[E]`İfadede, `T` [yönetilmeyen](../builtin-types/unmanaged-types.md) bir tür `E` olmalı ve negatif olmayan bir [int](../builtin-types/integral-numeric-types.md) değerine değer vermelidir.</span><span class="sxs-lookup"><span data-stu-id="c5c05-128">In expression `stackalloc T[E]`, `T` must be an [unmanaged type](../builtin-types/unmanaged-types.md) and `E` must evaluate to a non-negative [int](../builtin-types/integral-numeric-types.md) value.</span></span>

## <a name="security"></a><span data-ttu-id="c5c05-129">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="c5c05-129">Security</span></span>

<span data-ttu-id="c5c05-130">Otomatik `stackalloc` olarak kullanılması, ortak dil çalışma zamanında (CLR) arabellek taşma algılama özelliklerini etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="c5c05-130">The use of `stackalloc` automatically enables buffer overrun detection features in the common language runtime (CLR).</span></span> <span data-ttu-id="c5c05-131">Arabellek taşması algılanırsa, kötü amaçlı kod yürütülme olasılığını en aza indirmek için işlem mümkün olduğunca çabuk sonlandırılır.</span><span class="sxs-lookup"><span data-stu-id="c5c05-131">If a buffer overrun is detected, the process is terminated as quickly as possible to minimize the chance that malicious code is executed.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="c5c05-132">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="c5c05-132">C# language specification</span></span>

<span data-ttu-id="c5c05-133">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Yığın ayırma](~/_csharplang/spec/unsafe-code.md#stack-allocation) bölümüne ve iç içe [alınan bağlamlarda `stackalloc` İzin'e](~/_csharplang/proposals/csharp-8.0/nested-stackalloc.md) ilişkin teklif notuna bakın.</span><span class="sxs-lookup"><span data-stu-id="c5c05-133">For more information, see the [Stack allocation](~/_csharplang/spec/unsafe-code.md#stack-allocation) section of the [C# language specification](~/_csharplang/spec/introduction.md) and the [Permit `stackalloc` in nested contexts](~/_csharplang/proposals/csharp-8.0/nested-stackalloc.md) feature proposal note.</span></span>

## <a name="see-also"></a><span data-ttu-id="c5c05-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c5c05-134">See also</span></span>

- [<span data-ttu-id="c5c05-135">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="c5c05-135">C# reference</span></span>](../index.md)
- [<span data-ttu-id="c5c05-136">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="c5c05-136">C# operators</span></span>](index.md)
- [<span data-ttu-id="c5c05-137">İşaretçi bağlantılı işleçler</span><span class="sxs-lookup"><span data-stu-id="c5c05-137">Pointer related operators</span></span>](pointer-related-operators.md)
- [<span data-ttu-id="c5c05-138">İşaretçi türleri</span><span class="sxs-lookup"><span data-stu-id="c5c05-138">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="c5c05-139">Bellek ve aralıkla ilgili türler</span><span class="sxs-lookup"><span data-stu-id="c5c05-139">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
- [<span data-ttu-id="c5c05-140">Stackalloc Dos ve Don'ts</span><span class="sxs-lookup"><span data-stu-id="c5c05-140">Dos and Don'ts of stackalloc</span></span>](https://vcsjones.dev/2020/02/24/stackalloc/)
