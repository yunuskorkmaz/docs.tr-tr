---
title: C# 7.3 yenilikler nelerdir?
description: C# 7.3 içindeki yeni özelliklere genel bakış
ms.date: 05/16/2018
ms.openlocfilehash: 768070ead2b180d5f4491ac87be6c248c39e9944
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/26/2019
ms.locfileid: "67397787"
---
# <a name="whats-new-in-c-73"></a><span data-ttu-id="4e51d-103">C# 7.3 yenilikler nelerdir?</span><span class="sxs-lookup"><span data-stu-id="4e51d-103">What's new in C# 7.3</span></span>

<span data-ttu-id="4e51d-104">C# 7.3 sürüm için iki ana temaları vardır.</span><span class="sxs-lookup"><span data-stu-id="4e51d-104">There are two main themes to the C# 7.3 release.</span></span> <span data-ttu-id="4e51d-105">Bir tema güvenli kod güvenli olmayan kod olarak yüksek performanslı olmasını sağlayan özellikler sunar.</span><span class="sxs-lookup"><span data-stu-id="4e51d-105">One theme provides features that enable safe code to be as performant as unsafe code.</span></span> <span data-ttu-id="4e51d-106">İkinci temanın mevcut özelliklere yapılan artımlı iyileştirmeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="4e51d-106">The second theme provides incremental improvements to existing features.</span></span> <span data-ttu-id="4e51d-107">Ayrıca, yeni derleyici seçenekleri, bu sürümde eklendi.</span><span class="sxs-lookup"><span data-stu-id="4e51d-107">In addition, new compiler options were added in this release.</span></span>

<span data-ttu-id="4e51d-108">Aşağıdaki yeni özellikleri temayı daha iyi performans için güvenli kod desteği:</span><span class="sxs-lookup"><span data-stu-id="4e51d-108">The following new features support the theme of better performance for safe code:</span></span>

- <span data-ttu-id="4e51d-109">Sabit alanlar sabitleme olmadan erişebilir.</span><span class="sxs-lookup"><span data-stu-id="4e51d-109">You can access fixed fields without pinning.</span></span>
- <span data-ttu-id="4e51d-110">Yeniden atayabilirsiniz `ref` yerel değişkenler.</span><span class="sxs-lookup"><span data-stu-id="4e51d-110">You can reassign `ref` local variables.</span></span>
- <span data-ttu-id="4e51d-111">Başlatıcılar kullanabileceğiniz `stackalloc` dizileri.</span><span class="sxs-lookup"><span data-stu-id="4e51d-111">You can use initializers on `stackalloc` arrays.</span></span>
- <span data-ttu-id="4e51d-112">Kullanabileceğiniz `fixed` ifadelerle desen destekleyen herhangi bir türü.</span><span class="sxs-lookup"><span data-stu-id="4e51d-112">You can use `fixed` statements with any type that supports a pattern.</span></span>
- <span data-ttu-id="4e51d-113">Ek genel kısıtlamalara kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4e51d-113">You can use additional generic constraints.</span></span>

<span data-ttu-id="4e51d-114">Mevcut özellikler için aşağıdaki geliştirmeler yapılmıştır:</span><span class="sxs-lookup"><span data-stu-id="4e51d-114">The following enhancements were made to existing features:</span></span>

- <span data-ttu-id="4e51d-115">Test edebilirsiniz `==` ve `!=` tanımlama grubu türleri ile.</span><span class="sxs-lookup"><span data-stu-id="4e51d-115">You can test `==` and `!=` with tuple types.</span></span>
- <span data-ttu-id="4e51d-116">Daha fazla konumda ifade değişkenleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4e51d-116">You can use expression variables in more locations.</span></span>
- <span data-ttu-id="4e51d-117">Otomatik uygulanan özellikler için destek alanı öznitelikleri iliştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4e51d-117">You may attach attributes to the backing field of auto-implemented properties.</span></span>
- <span data-ttu-id="4e51d-118">Bağımsız değişkenleri farklı olduğunda yöntemi çözümleme `in` geliştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="4e51d-118">Method resolution when arguments differ by `in` has been improved.</span></span>
- <span data-ttu-id="4e51d-119">Aşırı yükleme çözümlemesi belirsiz daha az servis taleplerini artık sahiptir.</span><span class="sxs-lookup"><span data-stu-id="4e51d-119">Overload resolution now has fewer ambiguous cases.</span></span>

<span data-ttu-id="4e51d-120">Yeni derleyici seçenekleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="4e51d-120">The new compiler options are:</span></span>

- <span data-ttu-id="4e51d-121">`-publicsign` Açık kaynak yazılım (OSS) derlemeleri imzalamayı etkinleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="4e51d-121">`-publicsign` to enable Open Source Software (OSS) signing of assemblies.</span></span>
- <span data-ttu-id="4e51d-122">`-pathmap` Kaynak dizinleri için bir eşleme sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="4e51d-122">`-pathmap` to provide a mapping for source directories.</span></span>

<span data-ttu-id="4e51d-123">Bu makalenin geri kalanında, Ayrıntılar ve her geliştirmeleri hakkında daha fazla bilgi için bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="4e51d-123">The remainder of this article provides details and links to learn more about each of the improvements.</span></span> <span data-ttu-id="4e51d-124">Bu özellikleri kullanarak ortamınıza keşfedebilirsiniz `dotnet try` genel aracı:</span><span class="sxs-lookup"><span data-stu-id="4e51d-124">You can explore these features in your environment using the `dotnet try` global tool:</span></span>

1. <span data-ttu-id="4e51d-125">Yükleme [dotnet deneyin](https://github.com/dotnet/try/blob/master/README.md#setup) genel aracı.</span><span class="sxs-lookup"><span data-stu-id="4e51d-125">Install the [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) global tool.</span></span>
1. <span data-ttu-id="4e51d-126">Kopya [dotnet/try-samples](https://github.com/dotnet/try-samples) depo.</span><span class="sxs-lookup"><span data-stu-id="4e51d-126">Clone the [dotnet/try-samples](https://github.com/dotnet/try-samples) repository.</span></span>
1. <span data-ttu-id="4e51d-127">Geçerli dizin kümesine *csharp7* alt *deneyin-samples* depo.</span><span class="sxs-lookup"><span data-stu-id="4e51d-127">Set the current directory to the *csharp7* subdirectory for the *try-samples* repository.</span></span>
1. <span data-ttu-id="4e51d-128">`dotnet try`'i çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="4e51d-128">Run `dotnet try`.</span></span>

## <a name="enabling-more-efficient-safe-code"></a><span data-ttu-id="4e51d-129">Daha verimli bir güvenli kod etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="4e51d-129">Enabling more efficient safe code</span></span>

<span data-ttu-id="4e51d-130">Güvenli bir şekilde gerçekleştiren güvenli olmayan kod yanı sıra C# kodu yazacak olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="4e51d-130">You should be able to write C# code safely that performs as well as unsafe code.</span></span> <span data-ttu-id="4e51d-131">Güvenli kod hataları, arabellek taşmalarına parazit işaretçileri ve diğer bellek erişim hataları gibi sınıfları önler.</span><span class="sxs-lookup"><span data-stu-id="4e51d-131">Safe code avoids classes of errors, such as buffer overruns, stray pointers, and other memory access errors.</span></span> <span data-ttu-id="4e51d-132">Bu yeni özellikler doğrulanabilir bir güvenli kod yeteneklerini genişletmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="4e51d-132">These new features expand the capabilities of verifiable safe code.</span></span> <span data-ttu-id="4e51d-133">Daha fazla güvenli yapıları kullanarak kodunuzu yazmak çaba harcar.</span><span class="sxs-lookup"><span data-stu-id="4e51d-133">Strive to write more of your code using safe constructs.</span></span> <span data-ttu-id="4e51d-134">Bu özellikler, kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="4e51d-134">These features make that easier.</span></span>

### <a name="indexing-fixed-fields-does-not-require-pinning"></a><span data-ttu-id="4e51d-135">Dizin oluşturma `fixed` alanları sabitleme gerektirmez</span><span class="sxs-lookup"><span data-stu-id="4e51d-135">Indexing `fixed` fields does not require pinning</span></span>

<span data-ttu-id="4e51d-136">Bu struct göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="4e51d-136">Consider this struct:</span></span>

```csharp
unsafe struct S
{
    public fixed int myFixedField[10];
}
```

<span data-ttu-id="4e51d-137">Önceki sürümlerde, C#, erişim bir parçası olan bir tamsayı değişkene sabitlemek gereken `myFixedField`.</span><span class="sxs-lookup"><span data-stu-id="4e51d-137">In earlier versions of C#, you needed to pin a variable to access one of the integers that are part of `myFixedField`.</span></span> <span data-ttu-id="4e51d-138">Artık, aşağıdaki kod değişkeni sabitleme olmadan derler `p` içinde ayrı bir `fixed` deyimi:</span><span class="sxs-lookup"><span data-stu-id="4e51d-138">Now, the following code compiles without pinning the variable `p` inside a separate `fixed` statement:</span></span>

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

<span data-ttu-id="4e51d-139">Değişken `p` bir öğe üzerinde erişen `myFixedField`.</span><span class="sxs-lookup"><span data-stu-id="4e51d-139">The variable `p` accesses one element in `myFixedField`.</span></span> <span data-ttu-id="4e51d-140">Ayrı bir bildirmeniz gerekmez `int*` değişkeni.</span><span class="sxs-lookup"><span data-stu-id="4e51d-140">You don't need to declare a separate `int*` variable.</span></span> <span data-ttu-id="4e51d-141">Unutmayın, yine bir `unsafe` bağlamı.</span><span class="sxs-lookup"><span data-stu-id="4e51d-141">Note that you still need an `unsafe` context.</span></span> <span data-ttu-id="4e51d-142">Önceki sürümlerde, C#, ikinci sabit bir işaretçi bildirmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="4e51d-142">In earlier versions of C#, you need to declare a second fixed pointer:</span></span>

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

<span data-ttu-id="4e51d-143">Daha fazla bilgi için makaleye bakın [ `fixed` deyimi](../language-reference/keywords/fixed-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4e51d-143">For more information, see the article on the [`fixed` statement](../language-reference/keywords/fixed-statement.md).</span></span>

### <a name="ref-local-variables-may-be-reassigned"></a><span data-ttu-id="4e51d-144">`ref` yerel değişkenler atanabilir</span><span class="sxs-lookup"><span data-stu-id="4e51d-144">`ref` local variables may be reassigned</span></span>

<span data-ttu-id="4e51d-145">Şimdi, `ref` Yereller başlatıldıktan sonra farklı örneklerine başvurmak için atanabilir.</span><span class="sxs-lookup"><span data-stu-id="4e51d-145">Now, `ref` locals may be reassigned to refer to different instances after being initialized.</span></span> <span data-ttu-id="4e51d-146">Aşağıdaki kod artık derlenmemektedir:</span><span class="sxs-lookup"><span data-stu-id="4e51d-146">The following code now compiles:</span></span>

```csharp
ref VeryLargeStruct refLocal = ref veryLargeStruct; // initialization
refLocal = ref anotherVeryLargeStruct; // reassigned, refLocal refers to different storage.
```

<span data-ttu-id="4e51d-147">Daha fazla bilgi için makaleye bakın [ `ref` döndürür ve `ref` Yereller](../programming-guide/classes-and-structs/ref-returns.md)ve makale [ `foreach` ](../language-reference/keywords/foreach-in.md).</span><span class="sxs-lookup"><span data-stu-id="4e51d-147">For more information, see the article on [`ref` returns and `ref` locals](../programming-guide/classes-and-structs/ref-returns.md), and the article on [`foreach`](../language-reference/keywords/foreach-in.md).</span></span>

### <a name="stackalloc-arrays-support-initializers"></a><span data-ttu-id="4e51d-148">`stackalloc` başlatıcılar diziler desteği</span><span class="sxs-lookup"><span data-stu-id="4e51d-148">`stackalloc` arrays support initializers</span></span>

<span data-ttu-id="4e51d-149">Başlattığınızda bir dizide öğe değerlerini belirtin ettirebilmeyi başardım:</span><span class="sxs-lookup"><span data-stu-id="4e51d-149">You've been able to specify the values for elements in an array when you initialize it:</span></span>

```csharp
var arr = new int[3] {1, 2, 3};
var arr2 = new int[] {1, 2, 3};
```

<span data-ttu-id="4e51d-150">Artık, aynı söz dizimi ile bildirilen diziler için uygulanabilir `stackalloc`:</span><span class="sxs-lookup"><span data-stu-id="4e51d-150">Now, that same syntax can be applied to arrays that are declared with `stackalloc`:</span></span>

```csharp
int* pArr = stackalloc int[3] {1, 2, 3};
int* pArr2 = stackalloc int[] {1, 2, 3};
Span<int> arr = stackalloc [] {1, 2, 3};
```

<span data-ttu-id="4e51d-151">Daha fazla bilgi için [ `stackalloc` işleci](../language-reference/operators/stackalloc.md) makalesi.</span><span class="sxs-lookup"><span data-stu-id="4e51d-151">For more information, see the [`stackalloc` operator](../language-reference/operators/stackalloc.md) article.</span></span>

### <a name="more-types-support-the-fixed-statement"></a><span data-ttu-id="4e51d-152">Daha fazla türlerini destekleyen `fixed` deyimi</span><span class="sxs-lookup"><span data-stu-id="4e51d-152">More types support the `fixed` statement</span></span>

<span data-ttu-id="4e51d-153">`fixed` Deyimi sınırlı sayıda türleri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="4e51d-153">The `fixed` statement supported a limited set of types.</span></span> <span data-ttu-id="4e51d-154">C# 7.3, içeren herhangi bir türü'ile başlayan bir `GetPinnableReference()` döndüren yöntem bir `ref T` veya `ref readonly T` olabilir `fixed`.</span><span class="sxs-lookup"><span data-stu-id="4e51d-154">Starting with C# 7.3, any type that contains a `GetPinnableReference()` method that returns a `ref T` or `ref readonly T` may be `fixed`.</span></span> <span data-ttu-id="4e51d-155">Bu özellik ekleme anlamına `fixed` kullanılabilir <xref:System.Span%601?displayProperty=nameWithType> ve ilgili türler.</span><span class="sxs-lookup"><span data-stu-id="4e51d-155">Adding this feature means that `fixed` can be used with <xref:System.Span%601?displayProperty=nameWithType> and related types.</span></span>

<span data-ttu-id="4e51d-156">Daha fazla bilgi için [ `fixed` deyimi](../language-reference/keywords/fixed-statement.md) dil başvurusu makalesinde.</span><span class="sxs-lookup"><span data-stu-id="4e51d-156">For more information, see the [`fixed` statement](../language-reference/keywords/fixed-statement.md) article in the language reference.</span></span>

### <a name="enhanced-generic-constraints"></a><span data-ttu-id="4e51d-157">Gelişmiş genel kısıtlamalar</span><span class="sxs-lookup"><span data-stu-id="4e51d-157">Enhanced generic constraints</span></span>

<span data-ttu-id="4e51d-158">Türü artık belirtebilirsiniz <xref:System.Enum?displayProperty=nameWithType> veya <xref:System.Delegate?displayProperty=nameWithType> bir tür parametresi için temel sınıf kısıtlama olarak.</span><span class="sxs-lookup"><span data-stu-id="4e51d-158">You can now specify the type <xref:System.Enum?displayProperty=nameWithType> or <xref:System.Delegate?displayProperty=nameWithType> as base class constraints for a type parameter.</span></span>

<span data-ttu-id="4e51d-159">Ayrıca yeni kullanabilirsiniz `unmanaged` kısıtlaması, bir tür parametresi olması gerektiğini belirtmek için bir **yönetilmeyen tür**.</span><span class="sxs-lookup"><span data-stu-id="4e51d-159">You can also use the new `unmanaged` constraint, to specify that a type parameter must be an **unmanaged type**.</span></span> <span data-ttu-id="4e51d-160">Bir **yönetilmeyen tür** , bir başvuru türü değil ve iç içe geçme herhangi bir düzeyde herhangi bir başvuru türü içermeyen bir türdür.</span><span class="sxs-lookup"><span data-stu-id="4e51d-160">An **unmanaged type** is a type that isn't a reference type and doesn't contain any reference type at any level of nesting.</span></span>

<span data-ttu-id="4e51d-161">Daha fazla bilgi için üzerinde makalelerine bakın. [ `where` genel kısıtlamalara](../language-reference/keywords/where-generic-type-constraint.md) ve [tür parametrelerindeki kısıtlamalar](../programming-guide/generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="4e51d-161">For more information, see the articles on [`where` generic constraints](../language-reference/keywords/where-generic-type-constraint.md) and [constraints on type parameters](../programming-guide/generics/constraints-on-type-parameters.md).</span></span>

<span data-ttu-id="4e51d-162">Bu kısıtlamaları var olan türlere ekleme bir [uyumsuz değişiklik](version-update-considerations.md#incompatible-changes).</span><span class="sxs-lookup"><span data-stu-id="4e51d-162">Adding these constraints to existing types is an [incompatible change](version-update-considerations.md#incompatible-changes).</span></span> <span data-ttu-id="4e51d-163">Kapalı genel türler, artık bu yeni kısıtlamalarını karşılamıyor.</span><span class="sxs-lookup"><span data-stu-id="4e51d-163">Closed generic types may no longer meet these new constraints.</span></span>

## <a name="make-existing-features-better"></a><span data-ttu-id="4e51d-164">Mevcut özellikler daha iyi hale getirir</span><span class="sxs-lookup"><span data-stu-id="4e51d-164">Make existing features better</span></span>

<span data-ttu-id="4e51d-165">İkinci tema özelliklerinde dilde geliştirmeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="4e51d-165">The second theme provides improvements to features in the language.</span></span> <span data-ttu-id="4e51d-166">Bu özellikler, C# yazarken üretkenliği artırın.</span><span class="sxs-lookup"><span data-stu-id="4e51d-166">These features improve productivity when writing C#.</span></span>

### <a name="tuples-support--and-"></a><span data-ttu-id="4e51d-167">Diziler Destek `==` ve `!=`</span><span class="sxs-lookup"><span data-stu-id="4e51d-167">Tuples support `==` and `!=`</span></span>

<span data-ttu-id="4e51d-168">C# demet türleri artık destek `==` ve `!=`.</span><span class="sxs-lookup"><span data-stu-id="4e51d-168">The C# tuple types now support `==` and `!=`.</span></span> <span data-ttu-id="4e51d-169">Bölüm kapsayan daha fazla bilgi için bkz. [eşitlik](../tuples.md#equality-and-tuples) makalede [diziler](../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="4e51d-169">For more information, see the section covering [equality](../tuples.md#equality-and-tuples) in the article on [tuples](../tuples.md).</span></span>

### <a name="attach-attributes-to-the-backing-fields-for-auto-implemented-properties"></a><span data-ttu-id="4e51d-170">Otomatik uygulanan özellikler için yedekleme alanları öznitelikleri ekleme</span><span class="sxs-lookup"><span data-stu-id="4e51d-170">Attach attributes to the backing fields for auto-implemented properties</span></span>

<span data-ttu-id="4e51d-171">Bu sözdizimi artık desteklenmektedir:</span><span class="sxs-lookup"><span data-stu-id="4e51d-171">This syntax is now supported:</span></span>

```csharp
[field: SomeThingAboutFieldAttribute]
public int SomeProperty { get; set; }
```

<span data-ttu-id="4e51d-172">Öznitelik `SomeThingAboutFieldAttribute` derleyicinin ürettiği yedekleme alanı için uygulanan `SomeProperty`.</span><span class="sxs-lookup"><span data-stu-id="4e51d-172">The attribute `SomeThingAboutFieldAttribute` is applied to the compiler generated backing field for `SomeProperty`.</span></span> <span data-ttu-id="4e51d-173">Daha fazla bilgi için [öznitelikleri](../programming-guide/concepts/attributes/index.md) C# programlama kılavuzu.</span><span class="sxs-lookup"><span data-stu-id="4e51d-173">For more information, see [attributes](../programming-guide/concepts/attributes/index.md) in the C# programming guide.</span></span>

### <a name="in-method-overload-resolution-tiebreaker"></a><span data-ttu-id="4e51d-174">`in` yöntemi aşırı yükleme çözünürlüğü tiebreaker</span><span class="sxs-lookup"><span data-stu-id="4e51d-174">`in` method overload resolution tiebreaker</span></span>

<span data-ttu-id="4e51d-175">Zaman `in` değiştirici bağımsız değişken eklendi, bu iki yöntem belirsizliğe neden olur:</span><span class="sxs-lookup"><span data-stu-id="4e51d-175">When the `in` argument modifier was added, these two methods would cause an ambiguity:</span></span>

```csharp
static void M(S arg);
static void M(in S arg);
```

<span data-ttu-id="4e51d-176">Şimdi, (ilk olarak önceki örnek) değeriyle aşırı daha iyi salt okunur başvuru sürümüne göre.</span><span class="sxs-lookup"><span data-stu-id="4e51d-176">Now, the by value (first in the preceding example) overload is better than the by readonly reference version.</span></span> <span data-ttu-id="4e51d-177">Sürüm salt okunur başvuru bağımsız değişkeni ile çağırmak için içermelidir `in` yöntemi çağırırken değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="4e51d-177">To call the version with the readonly reference argument, you must include the `in` modifier when calling the method.</span></span>

> [!NOTE]
> <span data-ttu-id="4e51d-178">Bu, bir hata düzeltmesi uygulanmıştır.</span><span class="sxs-lookup"><span data-stu-id="4e51d-178">This was implemented as a bug fix.</span></span> <span data-ttu-id="4e51d-179">Bu artık bile "7.2 için" kümesi dil sürümü ile belirsiz.</span><span class="sxs-lookup"><span data-stu-id="4e51d-179">This no longer is ambiguous even with the language version set to "7.2".</span></span>

<span data-ttu-id="4e51d-180">Daha fazla bilgi için makaleye bakın [ `in` parametre değiştiricisi](../language-reference/keywords/in-parameter-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="4e51d-180">For more information, see the article on the [`in` parameter modifier](../language-reference/keywords/in-parameter-modifier.md).</span></span>

### <a name="extend-expression-variables-in-initializers"></a><span data-ttu-id="4e51d-181">Başlatıcılar içindeki ifade değişkenleri genişletme</span><span class="sxs-lookup"><span data-stu-id="4e51d-181">Extend expression variables in initializers</span></span>

<span data-ttu-id="4e51d-182">C# izin vermek için 7.0 eklenen söz dizimi `out` değişken bildirimlerini eklemek alan başlatıcıları, özellik başlatıcılar, oluşturucu başlatıcıları sorgu yan tümceleri için genişletilmişse.</span><span class="sxs-lookup"><span data-stu-id="4e51d-182">The syntax added in C# 7.0 to allow `out` variable declarations has been extended to include field initializers, property initializers, constructor initializers, and query clauses.</span></span> <span data-ttu-id="4e51d-183">Bu, aşağıdaki örnek gibi bir kod sağlar:</span><span class="sxs-lookup"><span data-stu-id="4e51d-183">It enables code such as the following example:</span></span>

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

### <a name="improved-overload-candidates"></a><span data-ttu-id="4e51d-184">Geliştirilmiş aşırı yükleme adayları</span><span class="sxs-lookup"><span data-stu-id="4e51d-184">Improved overload candidates</span></span>

<span data-ttu-id="4e51d-185">Her sürümde, aşırı yükleme çözünürlüğü kuralları belirsiz yöntem çağrılarını "açık" bir seçeneğin sahip olduğu durumlara yönelik olarak güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="4e51d-185">In every release, the overload resolution rules get updated to address situations where ambiguous method invocations have an "obvious" choice.</span></span> <span data-ttu-id="4e51d-186">Bu sürüm, belirgin seçim çekme derleyici yardımcı olmak için üç yeni kurallar ekler:</span><span class="sxs-lookup"><span data-stu-id="4e51d-186">This release adds three new rules to help the compiler pick the obvious choice:</span></span>

1. <span data-ttu-id="4e51d-187">Bir yöntem grubu örneği hem statik üyeler içeriyorsa, yöntem bir örnek alıcı ya da bağlam çağrıldı, derleyici örnek üyeleri atar.</span><span class="sxs-lookup"><span data-stu-id="4e51d-187">When a method group contains both instance and static members, the compiler discards the instance members if the method was invoked without an instance receiver or context.</span></span> <span data-ttu-id="4e51d-188">Yöntemi bir örnek alıcı ile çağırdığınız derleyici statik üyeleri olarak atar.</span><span class="sxs-lookup"><span data-stu-id="4e51d-188">The compiler discards the static members if the method was invoked with an instance receiver.</span></span> <span data-ttu-id="4e51d-189">Hiç alıcı olduğunda, derleyicinin yalnızca statik üyeleri statik bir bağlamda, aksi takdirde statik içerir ve örnek üyeleri.</span><span class="sxs-lookup"><span data-stu-id="4e51d-189">When there is no receiver, the compiler includes only static members in a static context, otherwise both static and instance members.</span></span> <span data-ttu-id="4e51d-190">Alıcı, muğlak örneği veya türü olduğunda, derleyici her ikisi de içerir.</span><span class="sxs-lookup"><span data-stu-id="4e51d-190">When the receiver is ambiguously an instance or type, the compiler includes both.</span></span> <span data-ttu-id="4e51d-191">Bir statik içerik, örtük burada `this` örneği alıcı kullanılamaz, üyeleri gövdesi yok burada içerir `this` statik üyeleri gibi tanımlanan yanı sıra yerlerde `this` gibi alan başlatıcıları kullanılamaz ve Oluşturucu başlatıcıları.</span><span class="sxs-lookup"><span data-stu-id="4e51d-191">A static context, where an implicit `this` instance receiver cannot be used, includes the body of members where no `this` is defined, such as static members, as well as places where `this` cannot be used, such as field initializers and constructor-initializers.</span></span>
1. <span data-ttu-id="4e51d-192">Bir yöntem grubu türü bağımsız değişkenleri kendi kısıtlamaları karşılamayan bazı genel yöntemleri içeriyorsa, bu üyeler için aday kümesinden kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="4e51d-192">When a method group contains some generic methods whose type arguments do not satisfy their constraints, these members are removed from the candidate set.</span></span>
1. <span data-ttu-id="4e51d-193">Bir yöntem grubu dönüştürme, türü, kümeden kaldırıldığına aday yöntemleri, dönüş türü temsilcinin ile eşleşmiyor döndürür.</span><span class="sxs-lookup"><span data-stu-id="4e51d-193">For a method group conversion, candidate methods whose return type doesn't match up with the delegate's return type are removed from the set.</span></span>

<span data-ttu-id="4e51d-194">Hangi daha iyi bir yöntemdir emin olduğunuzda belirsiz yöntemi aşırı yüklemeleri için daha az derleyici hataları bulabilirsiniz. çünkü bu değişiklik yalnızca fark edeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="4e51d-194">You'll only notice this change because you'll find fewer compiler errors for ambiguous method overloads when you are sure which method is better.</span></span>

## <a name="new-compiler-options"></a><span data-ttu-id="4e51d-195">Yeni derleyici seçenekleri</span><span class="sxs-lookup"><span data-stu-id="4e51d-195">New compiler options</span></span>

<span data-ttu-id="4e51d-196">Yeni derleme seçenekleri C# programları için yeni derleme ve DevOps senaryolarını destekler.</span><span class="sxs-lookup"><span data-stu-id="4e51d-196">New compiler options support new build and DevOps scenarios for C# programs.</span></span>

### <a name="public-or-open-source-signing"></a><span data-ttu-id="4e51d-197">Genel veya açık kaynak imzalama</span><span class="sxs-lookup"><span data-stu-id="4e51d-197">Public or Open Source signing</span></span>

<span data-ttu-id="4e51d-198">`-publicsign` Derleyici seçeneği, bir ortak anahtar kullanarak derlemeyi imzalamak için derleyicinin bildirir.</span><span class="sxs-lookup"><span data-stu-id="4e51d-198">The `-publicsign` compiler option instructs the compiler to sign the assembly using a public key.</span></span> <span data-ttu-id="4e51d-199">Derleme işaretli olarak işaretlenmiş, ancak imza ortak anahtardan alınır.</span><span class="sxs-lookup"><span data-stu-id="4e51d-199">The assembly is marked as signed, but the signature is taken from the public key.</span></span> <span data-ttu-id="4e51d-200">Bu seçenek, bir ortak anahtar kullanarak, açık kaynak projelerinden imzalı derlemeler oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="4e51d-200">This option enables you to build signed assemblies from open-source projects using a public key.</span></span>

<span data-ttu-id="4e51d-201">Daha fazla bilgi için [- publicsign derleyici seçeneği](../language-reference/compiler-options/publicsign-compiler-option.md) makalesi.</span><span class="sxs-lookup"><span data-stu-id="4e51d-201">For more information, see the [-publicsign compiler option](../language-reference/compiler-options/publicsign-compiler-option.md) article.</span></span>

### <a name="pathmap"></a><span data-ttu-id="4e51d-202">pathmap</span><span class="sxs-lookup"><span data-stu-id="4e51d-202">pathmap</span></span>

<span data-ttu-id="4e51d-203">`-pathmap` Derleyici seçeneği, yapı ortamı'ndan kaynak yolları ile eşlenen kaynak yolları değiştirmek için derleyicinin bildirir.</span><span class="sxs-lookup"><span data-stu-id="4e51d-203">The `-pathmap` compiler option instructs the compiler to replace source paths from the build environment with mapped source paths.</span></span> <span data-ttu-id="4e51d-204">`-pathmap` Seçeneği denetimleri veya PDB dosyaları için derleyici tarafından yazılmış kaynak yolu <xref:System.Runtime.CompilerServices.CallerFilePathAttribute>.</span><span class="sxs-lookup"><span data-stu-id="4e51d-204">The `-pathmap` option controls the source path written by the compiler to PDB files or for the <xref:System.Runtime.CompilerServices.CallerFilePathAttribute>.</span></span>

<span data-ttu-id="4e51d-205">Daha fazla bilgi için [- pathmap derleyici seçeneği](../language-reference/compiler-options/pathmap-compiler-option.md) makalesi.</span><span class="sxs-lookup"><span data-stu-id="4e51d-205">For more information, see the [-pathmap compiler option](../language-reference/compiler-options/pathmap-compiler-option.md) article.</span></span>
