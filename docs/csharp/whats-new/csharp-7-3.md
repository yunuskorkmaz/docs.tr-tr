---
title: C# 7.3'teki yenilikler
description: C# 7.3'teki yeni özelliklere genel bakış
ms.date: 05/16/2018
ms.openlocfilehash: ba4cea302d91b395e88940d087fcaed306920840
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74204553"
---
# <a name="whats-new-in-c-73"></a><span data-ttu-id="21282-103">C# 7.3'teki yenilikler</span><span class="sxs-lookup"><span data-stu-id="21282-103">What's new in C# 7.3</span></span>

<span data-ttu-id="21282-104">C# 7.3 sürümü için iki ana tema vardır.</span><span class="sxs-lookup"><span data-stu-id="21282-104">There are two main themes to the C# 7.3 release.</span></span> <span data-ttu-id="21282-105">Bir tema, güvenli kodun güvenli olmayan kod kadar performant olmasını sağlayan özellikler sağlar.</span><span class="sxs-lookup"><span data-stu-id="21282-105">One theme provides features that enable safe code to be as performant as unsafe code.</span></span> <span data-ttu-id="21282-106">İkinci tema, varolan özellikler için artımlı iyileştirmeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="21282-106">The second theme provides incremental improvements to existing features.</span></span> <span data-ttu-id="21282-107">Buna ek olarak, bu sürümde yeni derleyici seçenekleri eklendi.</span><span class="sxs-lookup"><span data-stu-id="21282-107">In addition, new compiler options were added in this release.</span></span>

<span data-ttu-id="21282-108">Aşağıdaki yeni özellikler, güvenli kod için daha iyi performans tesini destekler:</span><span class="sxs-lookup"><span data-stu-id="21282-108">The following new features support the theme of better performance for safe code:</span></span>

- <span data-ttu-id="21282-109">Sabit alanlara sabitleme den erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="21282-109">You can access fixed fields without pinning.</span></span>
- <span data-ttu-id="21282-110">Yerel değişkenleri `ref` yeniden atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="21282-110">You can reassign `ref` local variables.</span></span>
- <span data-ttu-id="21282-111">Diziler üzerinde `stackalloc` baş harflerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="21282-111">You can use initializers on `stackalloc` arrays.</span></span>
- <span data-ttu-id="21282-112">Bir deseni destekleyen herhangi bir türe sahip ifadeler kullanabilirsiniz. `fixed`</span><span class="sxs-lookup"><span data-stu-id="21282-112">You can use `fixed` statements with any type that supports a pattern.</span></span>
- <span data-ttu-id="21282-113">Ek genel kısıtlamalar kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="21282-113">You can use additional generic constraints.</span></span>

<span data-ttu-id="21282-114">Aşağıdaki geliştirmeler varolan özellikler için yapılmıştır:</span><span class="sxs-lookup"><span data-stu-id="21282-114">The following enhancements were made to existing features:</span></span>

- <span data-ttu-id="21282-115">Test `==` edebilirsiniz `!=` ve tuple türleri ile.</span><span class="sxs-lookup"><span data-stu-id="21282-115">You can test `==` and `!=` with tuple types.</span></span>
- <span data-ttu-id="21282-116">İfade değişkenlerini daha fazla konumda kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="21282-116">You can use expression variables in more locations.</span></span>
- <span data-ttu-id="21282-117">Otomatik olarak uygulanan özelliklerin destek alanına öznitelikleri ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="21282-117">You may attach attributes to the backing field of auto-implemented properties.</span></span>
- <span data-ttu-id="21282-118">Bağımsız değişkenler farklı `in` olduğunda yöntem çözümlemesi geliştirildi.</span><span class="sxs-lookup"><span data-stu-id="21282-118">Method resolution when arguments differ by `in` has been improved.</span></span>
- <span data-ttu-id="21282-119">Aşırı yükleme çözünürlüğü artık daha az belirsiz servis talepleri ne kadar azdır.</span><span class="sxs-lookup"><span data-stu-id="21282-119">Overload resolution now has fewer ambiguous cases.</span></span>

<span data-ttu-id="21282-120">Yeni derleyici seçenekleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="21282-120">The new compiler options are:</span></span>

- <span data-ttu-id="21282-121">`-publicsign`derlemelerin Açık Kaynak Yazılım (OSS) imzalanmasını etkinleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="21282-121">`-publicsign` to enable Open Source Software (OSS) signing of assemblies.</span></span>
- <span data-ttu-id="21282-122">`-pathmap`kaynak dizinler için bir eşleme sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="21282-122">`-pathmap` to provide a mapping for source directories.</span></span>

<span data-ttu-id="21282-123">Bu makalenin geri kalanı, her bir geliştirme hakkında daha fazla bilgi edinmek için ayrıntılar ve bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="21282-123">The remainder of this article provides details and links to learn more about each of the improvements.</span></span> <span data-ttu-id="21282-124">`dotnet try` Bu özellikleri ortamınızda genel aracı kullanarak keşfedebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="21282-124">You can explore these features in your environment using the `dotnet try` global tool:</span></span>

1. <span data-ttu-id="21282-125">[dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) global aracını yükleyin.</span><span class="sxs-lookup"><span data-stu-id="21282-125">Install the [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) global tool.</span></span>
1. <span data-ttu-id="21282-126">[Dotnet/try-samples](https://github.com/dotnet/try-samples) deposunu klonla.</span><span class="sxs-lookup"><span data-stu-id="21282-126">Clone the [dotnet/try-samples](https://github.com/dotnet/try-samples) repository.</span></span>
1. <span data-ttu-id="21282-127">*Deneme örnekleri* deposu için geçerli dizini *csharp7* alt dizinine ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="21282-127">Set the current directory to the *csharp7* subdirectory for the *try-samples* repository.</span></span>
1. <span data-ttu-id="21282-128">`dotnet try` öğesini çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="21282-128">Run `dotnet try`.</span></span>

## <a name="enabling-more-efficient-safe-code"></a><span data-ttu-id="21282-129">Daha verimli güvenli kod etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="21282-129">Enabling more efficient safe code</span></span>

<span data-ttu-id="21282-130">C# kodunu güvenli bir şekilde yazabilmelisin.</span><span class="sxs-lookup"><span data-stu-id="21282-130">You should be able to write C# code safely that performs as well as unsafe code.</span></span> <span data-ttu-id="21282-131">Güvenli kod arabellek taşmaları, başıboş işaretçiler ve diğer bellek erişim hataları gibi hata sınıfları önler.</span><span class="sxs-lookup"><span data-stu-id="21282-131">Safe code avoids classes of errors, such as buffer overruns, stray pointers, and other memory access errors.</span></span> <span data-ttu-id="21282-132">Bu yeni özellikler doğrulanabilir güvenli kodun yeteneklerini genişletir.</span><span class="sxs-lookup"><span data-stu-id="21282-132">These new features expand the capabilities of verifiable safe code.</span></span> <span data-ttu-id="21282-133">Güvenli yapılar kullanarak kodunuzu daha fazla yazmak için çalışıyoruz.</span><span class="sxs-lookup"><span data-stu-id="21282-133">Strive to write more of your code using safe constructs.</span></span> <span data-ttu-id="21282-134">Bu özellikler bunu kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="21282-134">These features make that easier.</span></span>

### <a name="indexing-fixed-fields-does-not-require-pinning"></a><span data-ttu-id="21282-135">Dizin `fixed` oluşturma alanları sabitleme gerektirmez</span><span class="sxs-lookup"><span data-stu-id="21282-135">Indexing `fixed` fields does not require pinning</span></span>

<span data-ttu-id="21282-136">Bu yapıyı göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="21282-136">Consider this struct:</span></span>

```csharp
unsafe struct S
{
    public fixed int myFixedField[10];
}
```

<span data-ttu-id="21282-137">C#'ın önceki sürümlerinde, bir değişkenin parçası olan tamsayılardan birine `myFixedField`erişmek için bir değişkeni sabitlemeniz gerekiyordu.</span><span class="sxs-lookup"><span data-stu-id="21282-137">In earlier versions of C#, you needed to pin a variable to access one of the integers that are part of `myFixedField`.</span></span> <span data-ttu-id="21282-138">Şimdi, aşağıdaki kod ayrı `p` `fixed` bir ifade içinde değişken sabitleme olmadan derler:</span><span class="sxs-lookup"><span data-stu-id="21282-138">Now, the following code compiles without pinning the variable `p` inside a separate `fixed` statement:</span></span>

```csharp
class C
{
    static S s = new S();

    unsafe public void M()
    {
        int p = s.myFixedField[5];
    }
}
```

<span data-ttu-id="21282-139">Değişken `p` bir öğeye `myFixedField`erişer.</span><span class="sxs-lookup"><span data-stu-id="21282-139">The variable `p` accesses one element in `myFixedField`.</span></span> <span data-ttu-id="21282-140">Ayrı `int*` bir değişken bildirmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="21282-140">You don't need to declare a separate `int*` variable.</span></span> <span data-ttu-id="21282-141">Yine de bir `unsafe` içeriğe ihtiyacınız olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="21282-141">Note that you still need an `unsafe` context.</span></span> <span data-ttu-id="21282-142">C#'ın önceki sürümlerinde, ikinci bir sabit işaretçi bildirmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="21282-142">In earlier versions of C#, you need to declare a second fixed pointer:</span></span>

```csharp
class C
{
    static S s = new S();

    unsafe public void M()
    {
        fixed (int* ptr = s.myFixedField)
        {
            int p = ptr[5];
        }
    }
}
```

<span data-ttu-id="21282-143">Daha fazla bilgi için [ `fixed` deyimdeki](../language-reference/keywords/fixed-statement.md)makaleye bakın.</span><span class="sxs-lookup"><span data-stu-id="21282-143">For more information, see the article on the [`fixed` statement](../language-reference/keywords/fixed-statement.md).</span></span>

### <a name="ref-local-variables-may-be-reassigned"></a><span data-ttu-id="21282-144">`ref`yerel değişkenler yeniden atanabilir</span><span class="sxs-lookup"><span data-stu-id="21282-144">`ref` local variables may be reassigned</span></span>

<span data-ttu-id="21282-145">Şimdi, `ref` yerel halk, para'ya para batandıktan sonra farklı örneklere başvurmak üzere yeniden atanabilir.</span><span class="sxs-lookup"><span data-stu-id="21282-145">Now, `ref` locals may be reassigned to refer to different instances after being initialized.</span></span> <span data-ttu-id="21282-146">Aşağıdaki kod şimdi derler:</span><span class="sxs-lookup"><span data-stu-id="21282-146">The following code now compiles:</span></span>

```csharp
ref VeryLargeStruct refLocal = ref veryLargeStruct; // initialization
refLocal = ref anotherVeryLargeStruct; // reassigned, refLocal refers to different storage.
```

<span data-ttu-id="21282-147">Daha fazla bilgi [ `ref` için, döner `ref` ve yerel halklar](../programming-guide/classes-and-structs/ref-returns.md)ile ilgili makaleye ve . [`foreach`](../language-reference/keywords/foreach-in.md)</span><span class="sxs-lookup"><span data-stu-id="21282-147">For more information, see the article on [`ref` returns and `ref` locals](../programming-guide/classes-and-structs/ref-returns.md), and the article on [`foreach`](../language-reference/keywords/foreach-in.md).</span></span>

### <a name="stackalloc-arrays-support-initializers"></a><span data-ttu-id="21282-148">`stackalloc`diziler baş harflerini destekler</span><span class="sxs-lookup"><span data-stu-id="21282-148">`stackalloc` arrays support initializers</span></span>

<span data-ttu-id="21282-149">Bir dizideki öğelerin değerlerini, bir diziyi ilk olarak aranız:</span><span class="sxs-lookup"><span data-stu-id="21282-149">You've been able to specify the values for elements in an array when you initialize it:</span></span>

```csharp
var arr = new int[3] {1, 2, 3};
var arr2 = new int[] {1, 2, 3};
```

<span data-ttu-id="21282-150">Şimdi, aynı sözdizimi ile `stackalloc`bildirilen diziler için uygulanabilir:</span><span class="sxs-lookup"><span data-stu-id="21282-150">Now, that same syntax can be applied to arrays that are declared with `stackalloc`:</span></span>

```csharp
int* pArr = stackalloc int[3] {1, 2, 3};
int* pArr2 = stackalloc int[] {1, 2, 3};
Span<int> arr = stackalloc [] {1, 2, 3};
```

<span data-ttu-id="21282-151">Daha fazla bilgi için [ `stackalloc` operatör](../language-reference/operators/stackalloc.md) makalesine bakın.</span><span class="sxs-lookup"><span data-stu-id="21282-151">For more information, see the [`stackalloc` operator](../language-reference/operators/stackalloc.md) article.</span></span>

### <a name="more-types-support-the-fixed-statement"></a><span data-ttu-id="21282-152">Diğer türler `fixed` deyimi destekler</span><span class="sxs-lookup"><span data-stu-id="21282-152">More types support the `fixed` statement</span></span>

<span data-ttu-id="21282-153">Bildirim, `fixed` sınırlı sayıda türü destekledi.</span><span class="sxs-lookup"><span data-stu-id="21282-153">The `fixed` statement supported a limited set of types.</span></span> <span data-ttu-id="21282-154">C# 7.3 ile başlayarak, `GetPinnableReference()` bir veya `ref T` `ref readonly T` olabilir döndürür bir yöntem içeren herhangi bir tür `fixed`.</span><span class="sxs-lookup"><span data-stu-id="21282-154">Starting with C# 7.3, any type that contains a `GetPinnableReference()` method that returns a `ref T` or `ref readonly T` may be `fixed`.</span></span> <span data-ttu-id="21282-155">Bu özelliğin `fixed` eklenmesi, ilgili <xref:System.Span%601?displayProperty=nameWithType> türlerle ve ilgili türlerle kullanılabileceğini zedilen anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="21282-155">Adding this feature means that `fixed` can be used with <xref:System.Span%601?displayProperty=nameWithType> and related types.</span></span>

<span data-ttu-id="21282-156">Daha fazla bilgi [ `fixed` ](../language-reference/keywords/fixed-statement.md) için, dil başvurusundaki deyim makalesine bakın.</span><span class="sxs-lookup"><span data-stu-id="21282-156">For more information, see the [`fixed` statement](../language-reference/keywords/fixed-statement.md) article in the language reference.</span></span>

### <a name="enhanced-generic-constraints"></a><span data-ttu-id="21282-157">Geliştirilmiş genel kısıtlamalar</span><span class="sxs-lookup"><span data-stu-id="21282-157">Enhanced generic constraints</span></span>

<span data-ttu-id="21282-158">Artık bir tür <xref:System.Enum?displayProperty=nameWithType> parametresi için türü veya <xref:System.Delegate?displayProperty=nameWithType> taban sınıf kısıtlamaları olarak belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="21282-158">You can now specify the type <xref:System.Enum?displayProperty=nameWithType> or <xref:System.Delegate?displayProperty=nameWithType> as base class constraints for a type parameter.</span></span>

<span data-ttu-id="21282-159">Bir tür parametrenin geçersiz olmayan `unmanaged` [yönetilmeyen](../language-reference/builtin-types/unmanaged-types.md)bir tür olması gerektiğini belirtmek için yeni kısıtlamayı da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="21282-159">You can also use the new `unmanaged` constraint, to specify that a type parameter must be a non-nullable [unmanaged type](../language-reference/builtin-types/unmanaged-types.md).</span></span>

<span data-ttu-id="21282-160">Daha fazla bilgi [ `where` için, genel kısıtlamalar](../language-reference/keywords/where-generic-type-constraint.md) ve [tür parametreleri üzerindeki kısıtlamalar hakkındaki](../programming-guide/generics/constraints-on-type-parameters.md)makalelere bakın.</span><span class="sxs-lookup"><span data-stu-id="21282-160">For more information, see the articles on [`where` generic constraints](../language-reference/keywords/where-generic-type-constraint.md) and [constraints on type parameters](../programming-guide/generics/constraints-on-type-parameters.md).</span></span>

<span data-ttu-id="21282-161">Varolan türlere bu kısıtlamaları eklemek uyumsuz bir [değişikliktir.](version-update-considerations.md#incompatible-changes)</span><span class="sxs-lookup"><span data-stu-id="21282-161">Adding these constraints to existing types is an [incompatible change](version-update-considerations.md#incompatible-changes).</span></span> <span data-ttu-id="21282-162">Kapalı genel türleri artık bu yeni kısıtlamaları karşılamayabilir.</span><span class="sxs-lookup"><span data-stu-id="21282-162">Closed generic types may no longer meet these new constraints.</span></span>

## <a name="make-existing-features-better"></a><span data-ttu-id="21282-163">Varolan özellikleri daha iyi hale getirin</span><span class="sxs-lookup"><span data-stu-id="21282-163">Make existing features better</span></span>

<span data-ttu-id="21282-164">İkinci tema, dildeki özellikleriçin iyileştirmeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="21282-164">The second theme provides improvements to features in the language.</span></span> <span data-ttu-id="21282-165">Bu özellikler C# yazarken üretkenliği artırır.</span><span class="sxs-lookup"><span data-stu-id="21282-165">These features improve productivity when writing C#.</span></span>

### <a name="tuples-support--and-"></a><span data-ttu-id="21282-166">Tuples `==` destek ve`!=`</span><span class="sxs-lookup"><span data-stu-id="21282-166">Tuples support `==` and `!=`</span></span>

<span data-ttu-id="21282-167">C# tuple türleri `==` şimdi `!=`destek ve .</span><span class="sxs-lookup"><span data-stu-id="21282-167">The C# tuple types now support `==` and `!=`.</span></span> <span data-ttu-id="21282-168">Daha fazla bilgi için, [tuples](../tuples.md)makalede [eşitliği](../tuples.md#equality-and-tuples) kapsayan bölüme bakın.</span><span class="sxs-lookup"><span data-stu-id="21282-168">For more information, see the section covering [equality](../tuples.md#equality-and-tuples) in the article on [tuples](../tuples.md).</span></span>

### <a name="attach-attributes-to-the-backing-fields-for-auto-implemented-properties"></a><span data-ttu-id="21282-169">Otomatik olarak uygulanan özellikler için destek alanlarına öznitelikleri ekleme</span><span class="sxs-lookup"><span data-stu-id="21282-169">Attach attributes to the backing fields for auto-implemented properties</span></span>

<span data-ttu-id="21282-170">Bu sözdizimi şimdi desteklenir:</span><span class="sxs-lookup"><span data-stu-id="21282-170">This syntax is now supported:</span></span>

```csharp
[field: SomeThingAboutFieldAttribute]
public int SomeProperty { get; set; }
```

<span data-ttu-id="21282-171">Öznitelik `SomeThingAboutFieldAttribute` için derleyici oluşturulan destek alanına `SomeProperty`uygulanır.</span><span class="sxs-lookup"><span data-stu-id="21282-171">The attribute `SomeThingAboutFieldAttribute` is applied to the compiler generated backing field for `SomeProperty`.</span></span> <span data-ttu-id="21282-172">Daha fazla bilgi için C# programlama kılavuzundaki [özniteliklere](../programming-guide/concepts/attributes/index.md) bakın.</span><span class="sxs-lookup"><span data-stu-id="21282-172">For more information, see [attributes](../programming-guide/concepts/attributes/index.md) in the C# programming guide.</span></span>

### <a name="in-method-overload-resolution-tiebreaker"></a><span data-ttu-id="21282-173">`in`yöntem aşırı yük çözünürlüğü tiebreaker</span><span class="sxs-lookup"><span data-stu-id="21282-173">`in` method overload resolution tiebreaker</span></span>

<span data-ttu-id="21282-174">`in` Bağımsız değişken değiştirici eklendiğinde, bu iki yöntem bir belirsizliğe neden olur:</span><span class="sxs-lookup"><span data-stu-id="21282-174">When the `in` argument modifier was added, these two methods would cause an ambiguity:</span></span>

```csharp
static void M(S arg);
static void M(in S arg);
```

<span data-ttu-id="21282-175">Şimdi, değeri (önceki örnekte ilk) aşırı okuma yalnızca başvuru sürümü daha iyidir.</span><span class="sxs-lookup"><span data-stu-id="21282-175">Now, the by value (first in the preceding example) overload is better than the by readonly reference version.</span></span> <span data-ttu-id="21282-176">Yalnızca başvuru bağımsız değişkenini içeren sürümü çağırmak `in` için, yöntemi ararken değiştiricieklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="21282-176">To call the version with the readonly reference argument, you must include the `in` modifier when calling the method.</span></span>

> [!NOTE]
> <span data-ttu-id="21282-177">Bu bir hata düzeltmesi olarak uygulandı.</span><span class="sxs-lookup"><span data-stu-id="21282-177">This was implemented as a bug fix.</span></span> <span data-ttu-id="21282-178">Bu artık dil sürümü "7.2" olarak ayarlanmış olsa bile belirsizdir.</span><span class="sxs-lookup"><span data-stu-id="21282-178">This no longer is ambiguous even with the language version set to "7.2".</span></span>

<span data-ttu-id="21282-179">Daha fazla bilgi için [ `in` parametre değiştirici](../language-reference/keywords/in-parameter-modifier.md)makalesine bakın.</span><span class="sxs-lookup"><span data-stu-id="21282-179">For more information, see the article on the [`in` parameter modifier](../language-reference/keywords/in-parameter-modifier.md).</span></span>

### <a name="extend-expression-variables-in-initializers"></a><span data-ttu-id="21282-180">Baş harflerdeki ifade değişkenlerini genişletme</span><span class="sxs-lookup"><span data-stu-id="21282-180">Extend expression variables in initializers</span></span>

<span data-ttu-id="21282-181">Değişken bildirimlere izin `out` vermek için C# 7.0'a eklenen sözdizimi alan başharflerini, özellik baş harflerini, oluşturucu baş harflerini ve sorgu yan tümcelerini içerecek şekilde genişletilmiştir.</span><span class="sxs-lookup"><span data-stu-id="21282-181">The syntax added in C# 7.0 to allow `out` variable declarations has been extended to include field initializers, property initializers, constructor initializers, and query clauses.</span></span> <span data-ttu-id="21282-182">Aşağıdaki örnek gibi bir kod sağlar:</span><span class="sxs-lookup"><span data-stu-id="21282-182">It enables code such as the following example:</span></span>

```csharp
public class B
{
   public B(int i, out int j)
   {
      j = i;
   }
}

public class D : B
{
   public D(int i) : base(i, out var j)
   {
      Console.WriteLine($"The value of 'j' is {j}");
   }
}
```

### <a name="improved-overload-candidates"></a><span data-ttu-id="21282-183">Geliştirilmiş aşırı yükleme adayları</span><span class="sxs-lookup"><span data-stu-id="21282-183">Improved overload candidates</span></span>

<span data-ttu-id="21282-184">Her sürümde, aşırı yük çözümleme kuralları, belirsiz yöntem çağrılarının "bariz" bir seçeneği olduğu durumları ele almak için güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="21282-184">In every release, the overload resolution rules get updated to address situations where ambiguous method invocations have an "obvious" choice.</span></span> <span data-ttu-id="21282-185">Bu sürüm, derleyicinin bariz seçimi seçmesine yardımcı olmak için üç yeni kural ekler:</span><span class="sxs-lookup"><span data-stu-id="21282-185">This release adds three new rules to help the compiler pick the obvious choice:</span></span>

1. <span data-ttu-id="21282-186">Bir yöntem grubu hem örnek hem de statik üye içeriyorsa, yöntem bir örnek alıcısı veya bağlam ı olmadan çağrıldıysa derleyici örnek üyeleri atar.</span><span class="sxs-lookup"><span data-stu-id="21282-186">When a method group contains both instance and static members, the compiler discards the instance members if the method was invoked without an instance receiver or context.</span></span> <span data-ttu-id="21282-187">Yöntem bir örnek alıcıile çağrıldıysa derleyici statik üyeleri atar.</span><span class="sxs-lookup"><span data-stu-id="21282-187">The compiler discards the static members if the method was invoked with an instance receiver.</span></span> <span data-ttu-id="21282-188">Alıcı olmadığında, derleyici statik bağlamda yalnızca statik üyeler içerir, aksi takdirde hem statik hem de örnek üyeler.</span><span class="sxs-lookup"><span data-stu-id="21282-188">When there is no receiver, the compiler includes only static members in a static context, otherwise both static and instance members.</span></span> <span data-ttu-id="21282-189">Alıcı belirsiz bir örnek veya tür olduğunda, derleyici her ikisini de içerir.</span><span class="sxs-lookup"><span data-stu-id="21282-189">When the receiver is ambiguously an instance or type, the compiler includes both.</span></span> <span data-ttu-id="21282-190">Örtük `this` bir örnek alıcının kullanılamadığı statik bağlam, statik `this` üyeler gibi tanımlanmamış üyelerin gövdesini ve `this` alan başharfleri ve yapıcı-başharfler gibi kullanılamayacak yerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="21282-190">A static context, where an implicit `this` instance receiver cannot be used, includes the body of members where no `this` is defined, such as static members, as well as places where `this` cannot be used, such as field initializers and constructor-initializers.</span></span>
1. <span data-ttu-id="21282-191">Bir yöntem grubu, tür bağımsız değişkenleri kısıtlamalarını karşılamayan bazı genel yöntemler içeriyorsa, bu üyeler aday kümesinden kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="21282-191">When a method group contains some generic methods whose type arguments do not satisfy their constraints, these members are removed from the candidate set.</span></span>
1. <span data-ttu-id="21282-192">Yöntem grubu dönüştürmesi için, dönüş türü temsilcinin dönüş türüyle eşleşmeyen aday yöntemler kümeden kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="21282-192">For a method group conversion, candidate methods whose return type doesn't match up with the delegate's return type are removed from the set.</span></span>

<span data-ttu-id="21282-193">Hangi yöntemin daha iyi olduğundan emin olduğunuzda, belirsiz yöntem aşırı yüklemeleri için daha az derleyici hatası bulacağınız için bu değişikliği fark eedeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="21282-193">You'll only notice this change because you'll find fewer compiler errors for ambiguous method overloads when you are sure which method is better.</span></span>

## <a name="new-compiler-options"></a><span data-ttu-id="21282-194">Yeni derleyici seçenekleri</span><span class="sxs-lookup"><span data-stu-id="21282-194">New compiler options</span></span>

<span data-ttu-id="21282-195">Yeni derleyici seçenekleri, C# programları için yeni yapı ve DevOps senaryolarını destekler.</span><span class="sxs-lookup"><span data-stu-id="21282-195">New compiler options support new build and DevOps scenarios for C# programs.</span></span>

### <a name="public-or-open-source-signing"></a><span data-ttu-id="21282-196">Genel veya Açık Kaynak imzalama</span><span class="sxs-lookup"><span data-stu-id="21282-196">Public or Open Source signing</span></span>

<span data-ttu-id="21282-197">Derleyici seçeneği derleyiciye `-publicsign` ortak bir anahtar kullanarak derlemeyi imzalamasını bildirir.</span><span class="sxs-lookup"><span data-stu-id="21282-197">The `-publicsign` compiler option instructs the compiler to sign the assembly using a public key.</span></span> <span data-ttu-id="21282-198">Derleme imzalı olarak işaretlenir, ancak imza ortak anahtardan alınır.</span><span class="sxs-lookup"><span data-stu-id="21282-198">The assembly is marked as signed, but the signature is taken from the public key.</span></span> <span data-ttu-id="21282-199">Bu seçenek, ortak bir anahtar kullanarak açık kaynak projelerinden imzalı derlemeler oluşturmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="21282-199">This option enables you to build signed assemblies from open-source projects using a public key.</span></span>

<span data-ttu-id="21282-200">Daha fazla bilgi için [-publicsign derleyici seçeneği](../language-reference/compiler-options/publicsign-compiler-option.md) makalesine bakın.</span><span class="sxs-lookup"><span data-stu-id="21282-200">For more information, see the [-publicsign compiler option](../language-reference/compiler-options/publicsign-compiler-option.md) article.</span></span>

### <a name="pathmap"></a><span data-ttu-id="21282-201">yol haritası</span><span class="sxs-lookup"><span data-stu-id="21282-201">pathmap</span></span>

<span data-ttu-id="21282-202">Derleyici seçeneği, `-pathmap` derleyiciye yapı ortamından gelen kaynak yollarını eşlenen kaynak yolları ile değiştirmesini bildirir.</span><span class="sxs-lookup"><span data-stu-id="21282-202">The `-pathmap` compiler option instructs the compiler to replace source paths from the build environment with mapped source paths.</span></span> <span data-ttu-id="21282-203">Seçenek, `-pathmap` derleyici tarafından PDB dosyalarına veya <xref:System.Runtime.CompilerServices.CallerFilePathAttribute>.</span><span class="sxs-lookup"><span data-stu-id="21282-203">The `-pathmap` option controls the source path written by the compiler to PDB files or for the <xref:System.Runtime.CompilerServices.CallerFilePathAttribute>.</span></span>

<span data-ttu-id="21282-204">Daha fazla bilgi için [-pathmap derleyicisi seçeneği](../language-reference/compiler-options/pathmap-compiler-option.md) makalesine bakın.</span><span class="sxs-lookup"><span data-stu-id="21282-204">For more information, see the [-pathmap compiler option](../language-reference/compiler-options/pathmap-compiler-option.md) article.</span></span>
