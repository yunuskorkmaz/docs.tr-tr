---
title: stackalloc operatörü - C# referans
ms.date: 09/20/2019
f1_keywords:
- stackalloc_CSharpKeyword
helpviewer_keywords:
- stackalloc operator [C#]
ms.openlocfilehash: 9c9767e0c9945a9589d049fa7abba192cb928ad5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846264"
---
# <a name="stackalloc-operator-c-reference"></a><span data-ttu-id="f46ca-102">stackalloc operatörü (C# referansı)</span><span class="sxs-lookup"><span data-stu-id="f46ca-102">stackalloc operator (C# reference)</span></span>

<span data-ttu-id="f46ca-103">İşleç `stackalloc` yığına bir bellek bloğu ayırır.</span><span class="sxs-lookup"><span data-stu-id="f46ca-103">The `stackalloc` operator allocates a block of memory on the stack.</span></span> <span data-ttu-id="f46ca-104">Yöntem yürütülmesi sırasında oluşturulan bir yığın ayrılmış bellek bloğu, yöntem döndüğünde otomatik olarak atılır.</span><span class="sxs-lookup"><span data-stu-id="f46ca-104">A stack allocated memory block created during the method execution is automatically discarded when that method returns.</span></span> <span data-ttu-id="f46ca-105">`stackalloc` İşleç ile ayrılan belleği açıkça boşaltamazsınız.</span><span class="sxs-lookup"><span data-stu-id="f46ca-105">You cannot explicitly free memory allocated with the `stackalloc` operator.</span></span> <span data-ttu-id="f46ca-106">Yığın ayrılmış bellek bloğu çöp [toplama](../../../standard/garbage-collection/index.md) tabi değildir ve bir [ `fixed` deyim](../keywords/fixed-statement.md)ile sabitlenmiş olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="f46ca-106">A stack allocated memory block is not subject to [garbage collection](../../../standard/garbage-collection/index.md) and doesn't have to be pinned with a [`fixed` statement](../keywords/fixed-statement.md).</span></span>

<span data-ttu-id="f46ca-107">İşleticinin `stackalloc` sonucunu aşağıdaki türlerden birinin değişkenine atayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f46ca-107">You can assign the result of the `stackalloc` operator to a variable of one of the following types:</span></span>

- <span data-ttu-id="f46ca-108">C# 7.2 <xref:System.Span%601?displayProperty=nameWithType> ile <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>başlayarak veya aşağıdaki örnekte görüldüğü gibi:</span><span class="sxs-lookup"><span data-stu-id="f46ca-108">Beginning with C# 7.2, <xref:System.Span%601?displayProperty=nameWithType> or <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, as the following example shows:</span></span>

  [!code-csharp[stackalloc span](snippets/StackallocOperator.cs#AssignToSpan)]

  <span data-ttu-id="f46ca-109">Bir yığın ayrılmış bellek [unsafe](../keywords/unsafe.md) bloğu bir <xref:System.Span%601> veya <xref:System.ReadOnlySpan%601> değişkenata atadığınızda güvenli olmayan bir bağlam kullanmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="f46ca-109">You don't have to use an [unsafe](../keywords/unsafe.md) context when you assign a stack allocated memory block to a <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> variable.</span></span>

  <span data-ttu-id="f46ca-110">Bu türlerle çalışırken, aşağıdaki örnekte görüldüğü gibi `stackalloc` [koşullu](conditional-operator.md) veya atama ifadelerinde bir ifade kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f46ca-110">When you work with those types, you can use a `stackalloc` expression in [conditional](conditional-operator.md) or assignment expressions, as the following example shows:</span></span>

  [!code-csharp[stackalloc expression](snippets/StackallocOperator.cs#AsExpression)]

  <span data-ttu-id="f46ca-111">C# 8.0 ile başlayarak, `stackalloc` aşağıdaki örnekte görüldüğü <xref:System.Span%601> gibi, bir veya <xref:System.ReadOnlySpan%601> değişkene izin verildiğinde diğer ifadelerin içinde bir ifade kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f46ca-111">Beginning with C# 8.0, you can use a `stackalloc` expression inside other expressions whenever a <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> variable is allowed, as the following example shows:</span></span>

  [!code-csharp[stackalloc in nested expressions](snippets/StackallocOperator.cs#Nested)]

  > [!NOTE]
  > <span data-ttu-id="f46ca-112">Mümkün olduğunda <xref:System.Span%601> <xref:System.ReadOnlySpan%601> yığın ayrılmış bellekle çalışmak için kullanmanızı veya türleri kullanmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="f46ca-112">We recommend using <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> types to work with stack allocated memory whenever possible.</span></span>

- <span data-ttu-id="f46ca-113">Aşağıdaki örnekte görüldüğü gibi bir [işaretçi türü:](../../programming-guide/unsafe-code-pointers/pointer-types.md)</span><span class="sxs-lookup"><span data-stu-id="f46ca-113">A [pointer type](../../programming-guide/unsafe-code-pointers/pointer-types.md), as the following example shows:</span></span>

  [!code-csharp[stackalloc pointer](snippets/StackallocOperator.cs#AssignToPointer)]

  <span data-ttu-id="f46ca-114">Önceki örnekte de görüldüğü gibi, `unsafe` işaretçi türleri ile çalışırken bir bağlam kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f46ca-114">As the preceding example shows, you must use an `unsafe` context when you work with pointer types.</span></span>

  <span data-ttu-id="f46ca-115">İşaretçi türleri söz konusu olduğunda, `stackalloc` değişkeni başlatmak için yalnızca yerel bir değişken bildiriminde bir ifade kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f46ca-115">In the case of pointer types, you can use a `stackalloc` expression only in a local variable declaration to initialize the variable.</span></span>

<span data-ttu-id="f46ca-116">Yeni ayrılan belleğin içeriği tanımsız.</span><span class="sxs-lookup"><span data-stu-id="f46ca-116">The content of the newly allocated memory is undefined.</span></span> <span data-ttu-id="f46ca-117">C# 7.3 ile başlayarak, yeni ayrılan belleğin içeriğini tanımlamak için dizi başlandırıcı sözdizimini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f46ca-117">Beginning with C# 7.3, you can use array initializer syntax to define the content of the newly allocated memory.</span></span> <span data-ttu-id="f46ca-118">Aşağıdaki örnek, bunu yapmanın çeşitli yollarını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="f46ca-118">The following example demonstrates various ways to do that:</span></span>

[!code-csharp[stackalloc initialization](snippets/StackallocOperator.cs#StackallocInit)]

<span data-ttu-id="f46ca-119">`stackalloc T[E]`İfadede, `T` [yönetilmeyen](../builtin-types/unmanaged-types.md) bir tür `E` olmalı ve yazı [int](../builtin-types/integral-numeric-types.md)bir ifadesi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f46ca-119">In expression `stackalloc T[E]`, `T` must be an [unmanaged type](../builtin-types/unmanaged-types.md) and `E` must be an expression of type [int](../builtin-types/integral-numeric-types.md).</span></span>

## <a name="security"></a><span data-ttu-id="f46ca-120">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="f46ca-120">Security</span></span>

<span data-ttu-id="f46ca-121">Otomatik `stackalloc` olarak kullanılması, ortak dil çalışma zamanında (CLR) arabellek taşma algılama özelliklerini etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="f46ca-121">The use of `stackalloc` automatically enables buffer overrun detection features in the common language runtime (CLR).</span></span> <span data-ttu-id="f46ca-122">Arabellek taşması algılanırsa, kötü amaçlı kod yürütülme olasılığını en aza indirmek için işlem mümkün olduğunca çabuk sonlandırılır.</span><span class="sxs-lookup"><span data-stu-id="f46ca-122">If a buffer overrun is detected, the process is terminated as quickly as possible to minimize the chance that malicious code is executed.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="f46ca-123">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="f46ca-123">C# language specification</span></span>

<span data-ttu-id="f46ca-124">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Yığın ayırma](~/_csharplang/spec/unsafe-code.md#stack-allocation) bölümüne ve iç içe [alınan bağlamlarda `stackalloc` İzin'e](~/_csharplang/proposals/csharp-8.0/nested-stackalloc.md) ilişkin teklif notuna bakın.</span><span class="sxs-lookup"><span data-stu-id="f46ca-124">For more information, see the [Stack allocation](~/_csharplang/spec/unsafe-code.md#stack-allocation) section of the [C# language specification](~/_csharplang/spec/introduction.md) and the [Permit `stackalloc` in nested contexts](~/_csharplang/proposals/csharp-8.0/nested-stackalloc.md) feature proposal note.</span></span>

## <a name="see-also"></a><span data-ttu-id="f46ca-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f46ca-125">See also</span></span>

- [<span data-ttu-id="f46ca-126">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="f46ca-126">C# reference</span></span>](../index.md)
- [<span data-ttu-id="f46ca-127">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="f46ca-127">C# operators</span></span>](index.md)
- [<span data-ttu-id="f46ca-128">İşaretçi bağlantılı işleçler</span><span class="sxs-lookup"><span data-stu-id="f46ca-128">Pointer related operators</span></span>](pointer-related-operators.md)
- [<span data-ttu-id="f46ca-129">İşaretçi türleri</span><span class="sxs-lookup"><span data-stu-id="f46ca-129">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="f46ca-130">Bellek ve aralıkla ilgili türler</span><span class="sxs-lookup"><span data-stu-id="f46ca-130">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
