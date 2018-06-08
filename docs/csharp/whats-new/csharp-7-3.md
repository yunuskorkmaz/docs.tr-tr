---
title: C# 7.3 içinde yenilikler nelerdir?
description: C# 7.3 içindeki yeni özelliklere genel bakış
ms.date: 05/16/2018
ms.openlocfilehash: 1d1aca2564c26315cf8b3af60a863ea3c70fd385
ms.sourcegitcommit: d955cb4c681d68cf301d410925d83f25172ece86
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/07/2018
ms.locfileid: "34827104"
---
# <a name="whats-new-in-c-73"></a><span data-ttu-id="1276d-103">C# 7.3 içinde yenilikler nelerdir?</span><span class="sxs-lookup"><span data-stu-id="1276d-103">What's new in C# 7.3</span></span>

<span data-ttu-id="1276d-104">C# 7.3 yayın iki ana temaları vardır.</span><span class="sxs-lookup"><span data-stu-id="1276d-104">There are two main themes to the C# 7.3 release.</span></span> <span data-ttu-id="1276d-105">Bir tema güvenli kodunun güvenli olmayan kod olarak kullanıcı olarak olmasını sağlayan özellikler sağlar.</span><span class="sxs-lookup"><span data-stu-id="1276d-105">One theme provides features that enable safe code to be as performant as unsafe code.</span></span> <span data-ttu-id="1276d-106">İkinci tema artımlı iyileştirmeleri var olan özellikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="1276d-106">The second theme provides incremental improvements to existing features.</span></span> <span data-ttu-id="1276d-107">Ayrıca, yeni derleyici seçenekleri bu sürümde eklendi.</span><span class="sxs-lookup"><span data-stu-id="1276d-107">In addition, new compiler options were added in this release.</span></span>

<span data-ttu-id="1276d-108">Aşağıdaki yeni özellikleri tema daha iyi performans için güvenli kod destekler:</span><span class="sxs-lookup"><span data-stu-id="1276d-108">The following new features support the theme of better performance for safe code:</span></span>

- <span data-ttu-id="1276d-109">Sabitleme olmadan sabit alanları erişebilir.</span><span class="sxs-lookup"><span data-stu-id="1276d-109">You can access fixed fields without pinning.</span></span>
- <span data-ttu-id="1276d-110">Yeniden atama yapabilir `ref` yerel değişkenler.</span><span class="sxs-lookup"><span data-stu-id="1276d-110">You can reassign `ref` local variables.</span></span>
- <span data-ttu-id="1276d-111">Başlatıcılar kullanabileceğiniz `stackalloc` dizileri.</span><span class="sxs-lookup"><span data-stu-id="1276d-111">You can use initializers on `stackalloc` arrays.</span></span>
- <span data-ttu-id="1276d-112">Kullanabileceğiniz `fixed` deyimleri ile bir deseni destekleyen herhangi bir türü.</span><span class="sxs-lookup"><span data-stu-id="1276d-112">You can use `fixed` statements with any type that supports a pattern.</span></span>
- <span data-ttu-id="1276d-113">Ek genel kısıtlamalar kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1276d-113">You can use additional generic constraints.</span></span>

<span data-ttu-id="1276d-114">Aşağıdaki geliştirmeleri için var olan özellikleri yapıldı:</span><span class="sxs-lookup"><span data-stu-id="1276d-114">The following enhancements were made to existing features:</span></span>

- <span data-ttu-id="1276d-115">Test edebilirsiniz `==` ve `!=` tanımlama grubu türleriyle.</span><span class="sxs-lookup"><span data-stu-id="1276d-115">You can test `==` and `!=` with tuple types.</span></span>
- <span data-ttu-id="1276d-116">Daha fazla konumlarda ifade değişkenlerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1276d-116">You can use expression variables in more locations.</span></span>
- <span data-ttu-id="1276d-117">Otomatik uygulanan özellikler yedekleme alanını için öznitelikler eklemek.</span><span class="sxs-lookup"><span data-stu-id="1276d-117">You may attach attributes to the backing field of auto-implemented properties.</span></span>
- <span data-ttu-id="1276d-118">Bağımsız değişkenler tarafından farklı olduğunda yöntemi çözümleme `in` geliştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="1276d-118">Method resolution when arguments differ by `in` has been improved.</span></span>
- <span data-ttu-id="1276d-119">Aşırı yükleme çözünürlüğü artık daha az belirsiz durumda olur.</span><span class="sxs-lookup"><span data-stu-id="1276d-119">Overload resolution now has fewer ambiguous cases.</span></span>

<span data-ttu-id="1276d-120">Yeni derleyici seçenekleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="1276d-120">The new compiler options are:</span></span>

- <span data-ttu-id="1276d-121">`-publicsign` Açık kaynak yazılım (OSS) derlemelerinin imzalamayı etkinleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="1276d-121">`-publicsign` to enable Open Source Software (OSS) signing of assemblies.</span></span>
- <span data-ttu-id="1276d-122">`-pathmap` Kaynak dizin için bir eşleme sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="1276d-122">`-pathmap` to provide a mapping for source directories.</span></span>

<span data-ttu-id="1276d-123">Bu makalenin sonraki bölümlerinde, Ayrıntılar ve her iyileştirmeleri hakkında daha fazla bilgi için bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="1276d-123">The remainder of this article provides details and links to learn more about each of the improvements.</span></span>

## <a name="enabling-more-performant-safe-code"></a><span data-ttu-id="1276d-124">Daha fazla kullanıcı güvenli kod etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="1276d-124">Enabling more performant safe code</span></span>

<span data-ttu-id="1276d-125">Güvenli bir şekilde yanı sıra güvenli olmayan kod gerçekleştiren C# kod yazmanız.</span><span class="sxs-lookup"><span data-stu-id="1276d-125">You should be able to write C# code safely that performs as well as unsafe code.</span></span> <span data-ttu-id="1276d-126">Güvenli kod arabellek taşmaları, parazit işaretçileri ve diğer bellek erişim hataları gibi hataları sınıfları önler.</span><span class="sxs-lookup"><span data-stu-id="1276d-126">Safe code avoids classes of errors, such as buffer overruns, stray pointers, and other memory access errors.</span></span> <span data-ttu-id="1276d-127">Bu yeni özellikleri doğrulanabilen güvenli kod özelliklerini genişletin.</span><span class="sxs-lookup"><span data-stu-id="1276d-127">These new features expand the capabilities of verifiable safe code.</span></span> <span data-ttu-id="1276d-128">Daha fazla güvenli yapıları kullanarak kodunuzu yazma konusunda da çalışmalar yapılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1276d-128">Strive to write more of your code using safe constructs.</span></span> <span data-ttu-id="1276d-129">Bu özellikler, kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="1276d-129">These features make that easier.</span></span>

### <a name="indexing-fixed-fields-does-not-require-pinning"></a><span data-ttu-id="1276d-130">Dizin oluşturma `fixed` alanları sabitleme gerektirmez</span><span class="sxs-lookup"><span data-stu-id="1276d-130">Indexing `fixed` fields does not require pinning</span></span>

<span data-ttu-id="1276d-131">Bu yapı göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="1276d-131">Consider this struct:</span></span>

```csharp
unsafe struct S
{
    public fixed int myFixedField[10];
}
```

<span data-ttu-id="1276d-132">Bir değişken parçası olan tamsayılar birine erişmek için PIN için gereken önceki sürümlerinde C#, `myFixedField`.</span><span class="sxs-lookup"><span data-stu-id="1276d-132">In earlier versions of C#, you needed to pin a variable to access one of the integers that are part of `myFixedField`.</span></span> <span data-ttu-id="1276d-133">Şimdi, aşağıdaki kodu güvenli bir bağlamda derler:</span><span class="sxs-lookup"><span data-stu-id="1276d-133">Now, the following code compiles in a safe context:</span></span>

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

<span data-ttu-id="1276d-134">Değişkeni `p` bir öğedeki erişen `myFixedField`.</span><span class="sxs-lookup"><span data-stu-id="1276d-134">The variable `p` accesses one element in `myFixedField`.</span></span> <span data-ttu-id="1276d-135">Ayrı bir bildirmeniz gerekmez `int*` değişkeni.</span><span class="sxs-lookup"><span data-stu-id="1276d-135">You don't need to declare a separate `int*` variable.</span></span> <span data-ttu-id="1276d-136">Hala ihtiyacınız Not bir `unsafe` bağlamı.</span><span class="sxs-lookup"><span data-stu-id="1276d-136">Note that you still need an `unsafe` context.</span></span> <span data-ttu-id="1276d-137">Önceki sürümlerde, C#, ikinci bir sabit işaretçi bildirmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="1276d-137">In earlier versions of C#, you need to declare a second fixed pointer:</span></span>

```csharp
class C
{
    static S s = new S();

    public void M()
    {
        fixed (int* ptr = s.myFixedField)
        {
            int p = ptr[5];
        }
    }
}
```

<span data-ttu-id="1276d-138">Daha fazla bilgi için üzerinde makalesine bakın. [ `fixed` deyimi](../language-reference/keywords/fixed-statement.md).</span><span class="sxs-lookup"><span data-stu-id="1276d-138">Fore more information, see the article on the [`fixed` statement](../language-reference/keywords/fixed-statement.md).</span></span>

### <a name="ref-local-variables-may-be-reassigned"></a><span data-ttu-id="1276d-139">`ref` yerel değişkenler atanabilir</span><span class="sxs-lookup"><span data-stu-id="1276d-139">`ref` local variables may be reassigned</span></span>

<span data-ttu-id="1276d-140">Şimdi, `ref` Yereller yeniden atandı farklı örnekleri başlatılmış sonra başvurmak için.</span><span class="sxs-lookup"><span data-stu-id="1276d-140">Now, `ref` locals may be reassigned to refer to different instances after being initialized.</span></span> <span data-ttu-id="1276d-141">Aşağıdaki kod artık derler:</span><span class="sxs-lookup"><span data-stu-id="1276d-141">The following code now compiles:</span></span>

```csharp
ref VeryLargeStruct refLocal = ref veryLargeStruct; // initialization
refLocal = ref anotherVeryLargeStruct; // reassigned, refLocal refers to different storage.
```

<span data-ttu-id="1276d-142">Daha fazla bilgi için üzerinde makalesine bakın. [ `ref` döndürür ve `ref` Yereller](../programming-guide/classes-and-structs/ref-returns.md).</span><span class="sxs-lookup"><span data-stu-id="1276d-142">For more information, see the article on [`ref` returns and `ref` locals](../programming-guide/classes-and-structs/ref-returns.md).</span></span>

### <a name="stackalloc-arrays-support-initializers"></a><span data-ttu-id="1276d-143">`stackalloc` diziler başlatıcıları desteği</span><span class="sxs-lookup"><span data-stu-id="1276d-143">`stackalloc` arrays support initializers</span></span>

<span data-ttu-id="1276d-144">Bunu başlattığınızda bir dizide öğeler için değerleri belirtin:</span><span class="sxs-lookup"><span data-stu-id="1276d-144">You've been able to specify the values for elements in an array when you initialize it:</span></span>

```csharp
var arr = new int[3] {1, 2, 3};
var arr2 = new int[] {1, 2, 3};
```

<span data-ttu-id="1276d-145">Şimdi, o aynı sözdizimi ile bildirilen diziler uygulanabilir `stackalloc`:</span><span class="sxs-lookup"><span data-stu-id="1276d-145">Now, that same syntax can be applied to arrays that are declared with `stackalloc`:</span></span>

```csharp
int* pArr = stackalloc int[3] {1, 2, 3};
int* pArr2 = stackalloc int[] {1, 2, 3};
Span<int> arr = stackalloc [] {1, 2, 3};
```

<span data-ttu-id="1276d-146">Daha fazla bilgi için bkz: [ `stackalloc` deyimi](../language-reference/keywords/stackalloc.md) dil başvurusu makalesinde.</span><span class="sxs-lookup"><span data-stu-id="1276d-146">For more information, see the [`stackalloc` statement](../language-reference/keywords/stackalloc.md) article in the language reference.</span></span>

### <a name="more-types-support-the-fixed-statement"></a><span data-ttu-id="1276d-147">Daha fazla türlerini destekleyen `fixed` deyimi</span><span class="sxs-lookup"><span data-stu-id="1276d-147">More types support the `fixed` statement</span></span>

<span data-ttu-id="1276d-148">`fixed` Deyimi sınırlı sayıda türleri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="1276d-148">The `fixed` statement supported a limited set of types.</span></span> <span data-ttu-id="1276d-149">C# 7.3, içeren herhangi bir türü'ile başlayan bir `GetPinnableReference()` döndüren yöntemi bir `ref T` veya `ref readonly T` olabilir `fixed`.</span><span class="sxs-lookup"><span data-stu-id="1276d-149">Starting with C# 7.3, any type that contains a `GetPinnableReference()` method that returns a `ref T` or `ref readonly T` may be `fixed`.</span></span> <span data-ttu-id="1276d-150">Bu özellik ekleme anlamına `fixed` ile kullanılan <xref:System.Span%601?displayProperty=nameWithType> ve ilgili türleri.</span><span class="sxs-lookup"><span data-stu-id="1276d-150">Adding this feature means that `fixed` can be used with <xref:System.Span%601?displayProperty=nameWithType> and related types.</span></span>

<span data-ttu-id="1276d-151">Daha fazla bilgi için bkz: [ `fixed` deyimi](../language-reference/keywords/fixed-statement.md) dil başvurusu makalesinde.</span><span class="sxs-lookup"><span data-stu-id="1276d-151">For more information, see the [`fixed` statement](../language-reference/keywords/fixed-statement.md) article in the language reference.</span></span>

### <a name="enhanced-generic-constraints"></a><span data-ttu-id="1276d-152">Gelişmiş genel kısıtlamalar</span><span class="sxs-lookup"><span data-stu-id="1276d-152">Enhanced generic constraints</span></span>

<span data-ttu-id="1276d-153">Şimdi türünü belirtebilirsiniz <xref:System.Enum?displayProperty=nameWithType> veya <xref:System.Delegate?displayProperty=nameWithType> bir tür parametresi için temel sınıf kısıtlamaları olarak.</span><span class="sxs-lookup"><span data-stu-id="1276d-153">You can now specify the type <xref:System.Enum?displayProperty=nameWithType> or <xref:System.Delegate?displayProperty=nameWithType> as base class constraints for a type parameter.</span></span>

<span data-ttu-id="1276d-154">Ayrıca yeni kullanabilirsiniz `unmanaged` bir tür parametresi gerektiğini belirtmek için kısıtlaması, bir **yönetilmeyen türü**.</span><span class="sxs-lookup"><span data-stu-id="1276d-154">You can also use the new `unmanaged` constraint, to specify that a type parameter must be an **unmanaged type**.</span></span> <span data-ttu-id="1276d-155">Bir **yönetilmeyen türü** bir başvuru türü değil ve iç içe geçme herhangi bir düzeyde herhangi bir başvuru türü içermiyor. bir tür.</span><span class="sxs-lookup"><span data-stu-id="1276d-155">An **unmanaged type** is a type that isn't a reference type and doesn't contain any reference type at any level of nesting.</span></span>

<span data-ttu-id="1276d-156">Daha fazla bilgi için üzerinde makalelerine bakın [ `where` genel kısıtlamalar](../language-reference/keywords/where-generic-type-constraint.md) ve [tür parametrelerindeki kısıtlamalar](../programming-guide/generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="1276d-156">For more information, see the articles on [`where` generic constraints](../language-reference/keywords/where-generic-type-constraint.md) and [constraints on type parameters](../programming-guide/generics/constraints-on-type-parameters.md).</span></span>

## <a name="make-existing-features-better"></a><span data-ttu-id="1276d-157">Var olan özellikleri daha iyi hale</span><span class="sxs-lookup"><span data-stu-id="1276d-157">Make existing features better</span></span>

<span data-ttu-id="1276d-158">İkinci tema dilde özelliklerine yönelik geliştirmelerden sağlar.</span><span class="sxs-lookup"><span data-stu-id="1276d-158">The second theme provides improvements to features in the language.</span></span> <span data-ttu-id="1276d-159">Bu özellikler, C# yazarken üretkenliği artırma.</span><span class="sxs-lookup"><span data-stu-id="1276d-159">These features improve productivity when writing C#.</span></span>

### <a name="tuples-support--and-"></a><span data-ttu-id="1276d-160">Diziler Destek `==` ve `!=`</span><span class="sxs-lookup"><span data-stu-id="1276d-160">Tuples support `==` and `!=`</span></span>

<span data-ttu-id="1276d-161">C# tanımlama grubu türleri şimdi destek `==` ve `!=`.</span><span class="sxs-lookup"><span data-stu-id="1276d-161">The C# tuple types now support `==` and `!=`.</span></span> <span data-ttu-id="1276d-162">Bölüm kapak daha fazla bilgi için bkz: [eşitlik](../tuples.md#equality-and-tuples) makalede [diziler](../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="1276d-162">Fore more information, see the section covering [equality](../tuples.md#equality-and-tuples) in the article on [tuples](../tuples.md).</span></span>

### <a name="attach-attributes-to-the-backing-fields-for-auto-implemented-properties"></a><span data-ttu-id="1276d-163">Otomatik uygulanan özellikler için yedekleme alanların öznitelikleri ekleme</span><span class="sxs-lookup"><span data-stu-id="1276d-163">Attach attributes to the backing fields for auto-implemented properties</span></span>

<span data-ttu-id="1276d-164">Bu sözdiziminin artık desteklenmektedir:</span><span class="sxs-lookup"><span data-stu-id="1276d-164">This syntax is now supported:</span></span>

```csharp
[field: SomeThingAboutFieldAttribute]
public int SomeProperty { get; set; }
```

<span data-ttu-id="1276d-165">Öznitelik `SomeThingAboutFieldAttribute` için oluşturulan derleyici yedekleme alanına uygulanan `SomeProperty`.</span><span class="sxs-lookup"><span data-stu-id="1276d-165">The attribute `SomeThingAboutFieldAttribute` is applied to the compiler generated backing field for `SomeProperty`.</span></span> <span data-ttu-id="1276d-166">Daha fazla bilgi için bkz: [öznitelikleri](../programming-guide/concepts/attributes/index.md) C# programlama Kılavuzu'nda.</span><span class="sxs-lookup"><span data-stu-id="1276d-166">For more information, see [attributes](../programming-guide/concepts/attributes/index.md) in the C# programming guide.</span></span>

### <a name="in-method-overload-resolution-tiebreaker"></a><span data-ttu-id="1276d-167">`in` yöntemi aşırı yükleme çözümü tiebreaker</span><span class="sxs-lookup"><span data-stu-id="1276d-167">`in` method overload resolution tiebreaker</span></span>

<span data-ttu-id="1276d-168">Zaman `in` bağımsız değişkeni değiştiricisi eklenen, bu iki yöntem bir belirsizlik neden olur:</span><span class="sxs-lookup"><span data-stu-id="1276d-168">When the `in` argument modifier was added, these two methods would cause an ambiguity:</span></span>

```csharp
static void M(S arg);
static void M(in S arg);
```

<span data-ttu-id="1276d-169">Şimdi, (ilk olarak önceki örnek) değeriyle aşırı daha iyi salt okunur başvuru sürümüne göre.</span><span class="sxs-lookup"><span data-stu-id="1276d-169">Now, the by value (first in the preceding example) overload is better than the by readonly reference version.</span></span> <span data-ttu-id="1276d-170">Salt okunur başvuru bağımsız değişkeni sürümüyle çağırmak için içermelidir `in` yöntemi çağrılırken değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="1276d-170">To call the version with the readonly reference argument, you must include the `in` modifier when calling the method.</span></span>

> [!NOTE]
> <span data-ttu-id="1276d-171">Bu hata düzeltmesi uygulanmıştır.</span><span class="sxs-lookup"><span data-stu-id="1276d-171">This was implemented as a bug fix.</span></span> <span data-ttu-id="1276d-172">Bu artık bile "7.2" kümesi dil sürümü ile belirsiz.</span><span class="sxs-lookup"><span data-stu-id="1276d-172">This no longer is ambiguous even with the language version set to "7.2".</span></span>

<span data-ttu-id="1276d-173">Daha fazla bilgi için üzerinde makalesine bakın. [ `in` parametresi değiştiricisi](../language-reference/keywords/in-parameter-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="1276d-173">For more information, see the article on the [`in` parameter modifier](../language-reference/keywords/in-parameter-modifier.md).</span></span>

### <a name="extend-expression-variables-in-initializers"></a><span data-ttu-id="1276d-174">Başlatıcılar ifade değişkenlerini genişletme</span><span class="sxs-lookup"><span data-stu-id="1276d-174">Extend expression variables in initializers</span></span>

<span data-ttu-id="1276d-175">C# izin vermek için 7. 0'eklenen sözdizimi `out` değişken bildirimleri genişletilmişse eklenecek alan başlatıcıları, özellik başlatıcılar, oluşturucu başlatıcıları ya da yan tümceleri sorgu.</span><span class="sxs-lookup"><span data-stu-id="1276d-175">The syntax added in C# 7.0 to allow `out` variable declarations has been extended to include field initializers, property initializers, constructor initializers, and query clauses.</span></span> <span data-ttu-id="1276d-176">Aşağıdaki örnek gibi kodu sağlar:</span><span class="sxs-lookup"><span data-stu-id="1276d-176">It enables code such as the following example:</span></span>

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
   public D(int i) : B(i, out var j)
   {
      Console.WriteLine($"The value of 'j' is {j}");
   }
}
```

### <a name="improved-overload-candidates"></a><span data-ttu-id="1276d-177">Geliştirilmiş aşırı adayları</span><span class="sxs-lookup"><span data-stu-id="1276d-177">Improved overload candidates</span></span>

<span data-ttu-id="1276d-178">Her sürümde aşırı çözümleme kurallarını belirsiz yöntem çağrılarına "açık" bir seçim sahip olduğu durumlara yönelik olarak güncelleştirilmesi.</span><span class="sxs-lookup"><span data-stu-id="1276d-178">In every release, the overload resolution rules get updated to address situations where ambiguous method invocations have an "obvious" choice.</span></span> <span data-ttu-id="1276d-179">Bu sürüm bariz seçim çekme derleyici yardımcı olmak için üç yeni kurallar ekler:</span><span class="sxs-lookup"><span data-stu-id="1276d-179">This release adds three new rules to help the compiler pick the obvious choice:</span></span>

1. <span data-ttu-id="1276d-180">Bir yöntem grubu örneği ve statik üyeler içeriyorsa, yöntemi bir örnek alıcı veya bağlam başlatıldı, derleyici örnek üyelerin atar.</span><span class="sxs-lookup"><span data-stu-id="1276d-180">When a method group contains both instance and static members, the compiler discards the instance members if the method was invoked without an instance receiver or context.</span></span> <span data-ttu-id="1276d-181">Yöntem örneği alıcı ile çağrıldı, derleyici statik üyeleri atar.</span><span class="sxs-lookup"><span data-stu-id="1276d-181">The compiler discards the static members if the method was invoked with an instance receiver.</span></span> <span data-ttu-id="1276d-182">Alıcı yok olduğunda Derleyici yalnızca statik üyeleri bir statik bağlamında, aksi takdirde statik içerir ve üyeleri örneği.</span><span class="sxs-lookup"><span data-stu-id="1276d-182">When there is no receiver, the compiler includes only static members in a static context, otherwise both static and instance members.</span></span> <span data-ttu-id="1276d-183">Alıcı, muğlak örneği veya türü olduğunda, derleyicinin hem de içerir.</span><span class="sxs-lookup"><span data-stu-id="1276d-183">When the receiver is ambiguously an instance or type, the compiler includes both.</span></span> <span data-ttu-id="1276d-184">Statik içerik örtülü burada `this` örneği alıcı kullanılamaz, Hayır burada üyeleri gövdesini içeren `this` statik üyeler gibi tanımlanmış yanı sıra yerlerde `this` alan başlatıcıları gibi kullanılamaz ve Oluşturucu başlatıcıları.</span><span class="sxs-lookup"><span data-stu-id="1276d-184">A static context, where an implicit `this` instance receiver cannot be used, includes the body of members where no `this` is defined, such as static members, as well as places where `this` cannot be used, such as field initializers and constructor-initializers.</span></span>
1. <span data-ttu-id="1276d-185">Bir yöntem grubu, tür bağımsız değişkenleri kendi kısıtlamalarını karşılamadığı bazı genel yöntemler içeriyorsa, bu üyeler adayı kümesinden kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="1276d-185">When a method group contains some generic methods whose type arguments do not satisfy their constraints, these members are removed from the candidate set.</span></span>
1. <span data-ttu-id="1276d-186">Yöntemi Grup dönüştürme için türü kümeden kaldırılır, dönüş türü temsilcinin ile eşleşmeyen adayı yöntemleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="1276d-186">For a method group conversion, candidate methods whose return type doesn't match up with the delegate's return type are removed from the set.</span></span>

<span data-ttu-id="1276d-187">Hangi daha iyi bir yöntemdir emin olduktan sonra daha az derleyici hataları için belirsiz yöntemi aşırı bulabilirsiniz çünkü bu değişikliği yalnızca fark edeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="1276d-187">You'll only notice this change because you'll find fewer compiler errors for ambiguous method overloads when you are sure which method is better.</span></span>

## <a name="new-compiler-options"></a><span data-ttu-id="1276d-188">Yeni derleyici seçenekleri</span><span class="sxs-lookup"><span data-stu-id="1276d-188">New compiler options</span></span>

<span data-ttu-id="1276d-189">Yeni derleyici seçenekleri, C# programları için yeni derleme ve DevOps senaryoları destekler.</span><span class="sxs-lookup"><span data-stu-id="1276d-189">New compiler options support new build and DevOps scenarios for C# programs.</span></span>

### <a name="public-or-open-source-signing"></a><span data-ttu-id="1276d-190">Genel veya açık kaynak imzalama</span><span class="sxs-lookup"><span data-stu-id="1276d-190">Public or Open Source signing</span></span>

<span data-ttu-id="1276d-191">`-publicsign` Derleyici seçeneği, bir ortak anahtar kullanarak derlemeyi imzalamak için derleyici gerçekleştirilmesi talimatını verir.</span><span class="sxs-lookup"><span data-stu-id="1276d-191">The `-publicsign` compiler option instructs the compiler to sign the assembly using a public key.</span></span> <span data-ttu-id="1276d-192">Derleme imzalanmış olarak işaretlenmiş, ancak imza ortak anahtarı ile alınır.</span><span class="sxs-lookup"><span data-stu-id="1276d-192">The assembly is marked as signed, but the signature is taken from the public key.</span></span> <span data-ttu-id="1276d-193">Bu seçenek, ortak anahtar kullanarak açık kaynaklı projelerden imzalı derlemeler oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="1276d-193">This option enables you to build signed assemblies from open-source projects using a public key.</span></span>

<span data-ttu-id="1276d-194">Daha fazla bilgi için bkz: [- publicsign derleyici seçeneği](../language-reference/compiler-options/publicsign-compiler-option.md) makalesi.</span><span class="sxs-lookup"><span data-stu-id="1276d-194">For more information, see the [-publicsign compiler option](../language-reference/compiler-options/publicsign-compiler-option.md) article.</span></span>

### <a name="pathmap"></a><span data-ttu-id="1276d-195">pathmap</span><span class="sxs-lookup"><span data-stu-id="1276d-195">pathmap</span></span>

<span data-ttu-id="1276d-196">`-pathmap` Derleyici seçeneği ile eşlenen kaynak yolları yapı ortamı'ndan kaynak yolları değiştirmek için derleyici bildirir.</span><span class="sxs-lookup"><span data-stu-id="1276d-196">The `-pathmap` compiler option instructs the compiler to replace source paths from the build environment with mapped source paths.</span></span> <span data-ttu-id="1276d-197">`-pathmap` Seçeneği denetimleri PDB dosyalarını veya için derleyici tarafından yazılan kaynak yolu <xref:System.Runtime.CompilerServices.CallerFilePathAttribute>.</span><span class="sxs-lookup"><span data-stu-id="1276d-197">The `-pathmap` option controls the source path written by the compiler to PDB files or for the <xref:System.Runtime.CompilerServices.CallerFilePathAttribute>.</span></span>

<span data-ttu-id="1276d-198">Daha fazla bilgi için bkz: [- pathmap derleyici seçeneği](../language-reference/compiler-options/pathmap-compiler-option.md) makalesi.</span><span class="sxs-lookup"><span data-stu-id="1276d-198">For more information, see the [-pathmap compiler option](../language-reference/compiler-options/pathmap-compiler-option.md) article.</span></span>
