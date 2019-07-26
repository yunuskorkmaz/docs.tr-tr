---
title: C# 7,3 sürümündeki yenilikler
description: C# 7,3 sürümündeki yeni özelliklere genel bakış
ms.date: 05/16/2018
ms.openlocfilehash: ca53073db1b61300186a483001f79bf0caa79169
ms.sourcegitcommit: 1e7ac70be1b4d89708c0d9552897515f2cbf52c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68433518"
---
# <a name="whats-new-in-c-73"></a><span data-ttu-id="2cd8c-103">C# 7,3 sürümündeki yenilikler</span><span class="sxs-lookup"><span data-stu-id="2cd8c-103">What's new in C# 7.3</span></span>

<span data-ttu-id="2cd8c-104">C# 7,3 sürümünün iki ana teması vardır.</span><span class="sxs-lookup"><span data-stu-id="2cd8c-104">There are two main themes to the C# 7.3 release.</span></span> <span data-ttu-id="2cd8c-105">Bir tema, güvenli kodun güvenli olmayan kod olarak performans sağlamak için gereken özellikler sağlar.</span><span class="sxs-lookup"><span data-stu-id="2cd8c-105">One theme provides features that enable safe code to be as performant as unsafe code.</span></span> <span data-ttu-id="2cd8c-106">İkinci tema, mevcut özelliklerle artımlı iyileştirmeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="2cd8c-106">The second theme provides incremental improvements to existing features.</span></span> <span data-ttu-id="2cd8c-107">Ayrıca, bu yayına yeni derleyici seçenekleri eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="2cd8c-107">In addition, new compiler options were added in this release.</span></span>

<span data-ttu-id="2cd8c-108">Aşağıdaki yeni özellikler, güvenli kod için daha iyi performans temasını destekler:</span><span class="sxs-lookup"><span data-stu-id="2cd8c-108">The following new features support the theme of better performance for safe code:</span></span>

- <span data-ttu-id="2cd8c-109">Sabitlemeden sabit alanlara erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2cd8c-109">You can access fixed fields without pinning.</span></span>
- <span data-ttu-id="2cd8c-110">Yerel değişkenleri yeniden `ref` atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2cd8c-110">You can reassign `ref` local variables.</span></span>
- <span data-ttu-id="2cd8c-111">`stackalloc` Dizilerde başlatıcıları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2cd8c-111">You can use initializers on `stackalloc` arrays.</span></span>
- <span data-ttu-id="2cd8c-112">Deyimlerini, bir `fixed` kalıbı destekleyen herhangi bir türle birlikte kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2cd8c-112">You can use `fixed` statements with any type that supports a pattern.</span></span>
- <span data-ttu-id="2cd8c-113">Ek genel kısıtlamalar kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2cd8c-113">You can use additional generic constraints.</span></span>

<span data-ttu-id="2cd8c-114">Mevcut özelliklerde aşağıdaki geliştirmeler yapılmıştır:</span><span class="sxs-lookup"><span data-stu-id="2cd8c-114">The following enhancements were made to existing features:</span></span>

- <span data-ttu-id="2cd8c-115">Kayıt düzeni türlerini `==` test `!=` edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2cd8c-115">You can test `==` and `!=` with tuple types.</span></span>
- <span data-ttu-id="2cd8c-116">İfade değişkenlerini daha fazla konumda kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2cd8c-116">You can use expression variables in more locations.</span></span>
- <span data-ttu-id="2cd8c-117">Otomatik uygulanan özelliklerin yedekleme alanına öznitelikler iliştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2cd8c-117">You may attach attributes to the backing field of auto-implemented properties.</span></span>
- <span data-ttu-id="2cd8c-118">Bağımsız değişkenler farklı `in` olduğunda yöntem çözümlemesi geliştirildi.</span><span class="sxs-lookup"><span data-stu-id="2cd8c-118">Method resolution when arguments differ by `in` has been improved.</span></span>
- <span data-ttu-id="2cd8c-119">Aşırı yükleme çözümlemesi artık daha az belirsiz durum içeriyor.</span><span class="sxs-lookup"><span data-stu-id="2cd8c-119">Overload resolution now has fewer ambiguous cases.</span></span>

<span data-ttu-id="2cd8c-120">Yeni derleyici seçenekleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="2cd8c-120">The new compiler options are:</span></span>

- <span data-ttu-id="2cd8c-121">`-publicsign`Açık kaynak yazılım (OSS) derlemelerinin imzalanmasını etkinleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="2cd8c-121">`-publicsign` to enable Open Source Software (OSS) signing of assemblies.</span></span>
- <span data-ttu-id="2cd8c-122">`-pathmap`Kaynak dizinlere eşleme sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="2cd8c-122">`-pathmap` to provide a mapping for source directories.</span></span>

<span data-ttu-id="2cd8c-123">Bu makalenin geri kalanında, geliştirmelerin her biri hakkında daha fazla bilgi edinmek için Ayrıntılar ve bağlantılar sağlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2cd8c-123">The remainder of this article provides details and links to learn more about each of the improvements.</span></span> <span data-ttu-id="2cd8c-124">`dotnet try` Genel aracı kullanarak ortamınızdaki bu özellikleri keşfedebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="2cd8c-124">You can explore these features in your environment using the `dotnet try` global tool:</span></span>

1. <span data-ttu-id="2cd8c-125">[DotNet-TRY](https://github.com/dotnet/try/blob/master/README.md#setup) küresel aracını yükler.</span><span class="sxs-lookup"><span data-stu-id="2cd8c-125">Install the [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) global tool.</span></span>
1. <span data-ttu-id="2cd8c-126">[DotNet/TRY-Samples](https://github.com/dotnet/try-samples) deposunu kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="2cd8c-126">Clone the [dotnet/try-samples](https://github.com/dotnet/try-samples) repository.</span></span>
1. <span data-ttu-id="2cd8c-127">*TRY-Samples* deposu için geçerli dizini *csharp7* alt dizinine ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="2cd8c-127">Set the current directory to the *csharp7* subdirectory for the *try-samples* repository.</span></span>
1. <span data-ttu-id="2cd8c-128">`dotnet try` öğesini çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="2cd8c-128">Run `dotnet try`.</span></span>

## <a name="enabling-more-efficient-safe-code"></a><span data-ttu-id="2cd8c-129">Daha verimli güvenli kod etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="2cd8c-129">Enabling more efficient safe code</span></span>

<span data-ttu-id="2cd8c-130">Güvenli olmayan kod ve güvenli kod C# yazmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2cd8c-130">You should be able to write C# code safely that performs as well as unsafe code.</span></span> <span data-ttu-id="2cd8c-131">Güvenli kod, arabellek taşmaları, başıya işaretçileri ve diğer bellek erişim hataları gibi hata sınıflarını önler.</span><span class="sxs-lookup"><span data-stu-id="2cd8c-131">Safe code avoids classes of errors, such as buffer overruns, stray pointers, and other memory access errors.</span></span> <span data-ttu-id="2cd8c-132">Bu yeni özellikler, doğrulanabilir güvenli kod yeteneklerini genişletir.</span><span class="sxs-lookup"><span data-stu-id="2cd8c-132">These new features expand the capabilities of verifiable safe code.</span></span> <span data-ttu-id="2cd8c-133">Güvenli yapılar kullanarak kodunuzun daha fazlasını yazmak için çaba harcar.</span><span class="sxs-lookup"><span data-stu-id="2cd8c-133">Strive to write more of your code using safe constructs.</span></span> <span data-ttu-id="2cd8c-134">Bu özellikler daha kolay hale getirir.</span><span class="sxs-lookup"><span data-stu-id="2cd8c-134">These features make that easier.</span></span>

### <a name="indexing-fixed-fields-does-not-require-pinning"></a><span data-ttu-id="2cd8c-135">Dizin `fixed` oluşturma alanları sabitleme gerektirmez</span><span class="sxs-lookup"><span data-stu-id="2cd8c-135">Indexing `fixed` fields does not require pinning</span></span>

<span data-ttu-id="2cd8c-136">Bu yapıyı göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="2cd8c-136">Consider this struct:</span></span>

```csharp
unsafe struct S
{
    public fixed int myFixedField[10];
}
```

<span data-ttu-id="2cd8c-137">Önceki sürümlerinde C#, öğesinin `myFixedField`parçası olan tamsayıların birine erişmek için bir değişkeni sabitlemeyi gerekiyordu.</span><span class="sxs-lookup"><span data-stu-id="2cd8c-137">In earlier versions of C#, you needed to pin a variable to access one of the integers that are part of `myFixedField`.</span></span> <span data-ttu-id="2cd8c-138">Şimdi, aşağıdaki kod değişkeni `p` ayrı `fixed` bir ifadeye sabitlemeden derler:</span><span class="sxs-lookup"><span data-stu-id="2cd8c-138">Now, the following code compiles without pinning the variable `p` inside a separate `fixed` statement:</span></span>

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

<span data-ttu-id="2cd8c-139">Değişkeni `p` içindeki`myFixedField`bir öğeye erişir.</span><span class="sxs-lookup"><span data-stu-id="2cd8c-139">The variable `p` accesses one element in `myFixedField`.</span></span> <span data-ttu-id="2cd8c-140">Ayrı `int*` bir değişken bildirmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="2cd8c-140">You don't need to declare a separate `int*` variable.</span></span> <span data-ttu-id="2cd8c-141">Hala bir `unsafe` bağlam gerekeceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="2cd8c-141">Note that you still need an `unsafe` context.</span></span> <span data-ttu-id="2cd8c-142">Önceki sürümlerinde C#ikinci bir sabit işaretçi bildirmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="2cd8c-142">In earlier versions of C#, you need to declare a second fixed pointer:</span></span>

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

<span data-ttu-id="2cd8c-143">Daha fazla bilgi için, [ `fixed` deyimindeki](../language-reference/keywords/fixed-statement.md)makaleye bakın.</span><span class="sxs-lookup"><span data-stu-id="2cd8c-143">For more information, see the article on the [`fixed` statement](../language-reference/keywords/fixed-statement.md).</span></span>

### <a name="ref-local-variables-may-be-reassigned"></a><span data-ttu-id="2cd8c-144">`ref`Yerel değişkenler yeniden atanabilir</span><span class="sxs-lookup"><span data-stu-id="2cd8c-144">`ref` local variables may be reassigned</span></span>

<span data-ttu-id="2cd8c-145">Şimdi Yereller, başlatıldıktan sonra farklı örneklere başvuracak şekilde yeniden `ref` atanabilir.</span><span class="sxs-lookup"><span data-stu-id="2cd8c-145">Now, `ref` locals may be reassigned to refer to different instances after being initialized.</span></span> <span data-ttu-id="2cd8c-146">Aşağıdaki kod artık derlenir:</span><span class="sxs-lookup"><span data-stu-id="2cd8c-146">The following code now compiles:</span></span>

```csharp
ref VeryLargeStruct refLocal = ref veryLargeStruct; // initialization
refLocal = ref anotherVeryLargeStruct; // reassigned, refLocal refers to different storage.
```

<span data-ttu-id="2cd8c-147">Daha fazla bilgi için bkz [`foreach`](../language-reference/keywords/foreach-in.md) [ `ref` . dönüşler ve `ref` yerel öğeler](../programming-guide/classes-and-structs/ref-returns.md)ve hakkındaki makale.</span><span class="sxs-lookup"><span data-stu-id="2cd8c-147">For more information, see the article on [`ref` returns and `ref` locals](../programming-guide/classes-and-structs/ref-returns.md), and the article on [`foreach`](../language-reference/keywords/foreach-in.md).</span></span>

### <a name="stackalloc-arrays-support-initializers"></a><span data-ttu-id="2cd8c-148">`stackalloc`diziler, başlatıcıları destekler</span><span class="sxs-lookup"><span data-stu-id="2cd8c-148">`stackalloc` arrays support initializers</span></span>

<span data-ttu-id="2cd8c-149">Bir dizideki öğeler için değerleri, başlatma sırasında belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="2cd8c-149">You've been able to specify the values for elements in an array when you initialize it:</span></span>

```csharp
var arr = new int[3] {1, 2, 3};
var arr2 = new int[] {1, 2, 3};
```

<span data-ttu-id="2cd8c-150">Artık, ile `stackalloc`belirtilen dizilere aynı söz dizimi uygulanabilir:</span><span class="sxs-lookup"><span data-stu-id="2cd8c-150">Now, that same syntax can be applied to arrays that are declared with `stackalloc`:</span></span>

```csharp
int* pArr = stackalloc int[3] {1, 2, 3};
int* pArr2 = stackalloc int[] {1, 2, 3};
Span<int> arr = stackalloc [] {1, 2, 3};
```

<span data-ttu-id="2cd8c-151">Daha fazla bilgi için bkz [ `stackalloc` . operatör](../language-reference/operators/stackalloc.md) makalesi.</span><span class="sxs-lookup"><span data-stu-id="2cd8c-151">For more information, see the [`stackalloc` operator](../language-reference/operators/stackalloc.md) article.</span></span>

### <a name="more-types-support-the-fixed-statement"></a><span data-ttu-id="2cd8c-152">Daha fazla tür, `fixed` ifadeyi destekler</span><span class="sxs-lookup"><span data-stu-id="2cd8c-152">More types support the `fixed` statement</span></span>

<span data-ttu-id="2cd8c-153">`fixed` İfade sınırlı bir tür kümesi destekliyordu.</span><span class="sxs-lookup"><span data-stu-id="2cd8c-153">The `fixed` statement supported a limited set of types.</span></span> <span data-ttu-id="2cd8c-154">7,3 ' C# den `GetPinnableReference()` başlayarak, `ref T` `ref readonly T` veya`fixed`döndüren bir yöntemi içeren herhangi bir tür olabilir.</span><span class="sxs-lookup"><span data-stu-id="2cd8c-154">Starting with C# 7.3, any type that contains a `GetPinnableReference()` method that returns a `ref T` or `ref readonly T` may be `fixed`.</span></span> <span data-ttu-id="2cd8c-155">Bu özelliği eklemek, ve `fixed` ilgili türlerle birlikte <xref:System.Span%601?displayProperty=nameWithType> kullanılabilecek anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="2cd8c-155">Adding this feature means that `fixed` can be used with <xref:System.Span%601?displayProperty=nameWithType> and related types.</span></span>

<span data-ttu-id="2cd8c-156">Daha fazla bilgi için bkz [ `fixed` ](../language-reference/keywords/fixed-statement.md) . dil başvurusu içindeki ifade makalesi.</span><span class="sxs-lookup"><span data-stu-id="2cd8c-156">For more information, see the [`fixed` statement](../language-reference/keywords/fixed-statement.md) article in the language reference.</span></span>

### <a name="enhanced-generic-constraints"></a><span data-ttu-id="2cd8c-157">Gelişmiş genel kısıtlamalar</span><span class="sxs-lookup"><span data-stu-id="2cd8c-157">Enhanced generic constraints</span></span>

<span data-ttu-id="2cd8c-158">Artık tür parametresi için türü <xref:System.Enum?displayProperty=nameWithType> veya <xref:System.Delegate?displayProperty=nameWithType> temel sınıf kısıtlamalarını belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2cd8c-158">You can now specify the type <xref:System.Enum?displayProperty=nameWithType> or <xref:System.Delegate?displayProperty=nameWithType> as base class constraints for a type parameter.</span></span>

<span data-ttu-id="2cd8c-159">Yeni `unmanaged` kısıtlamayı, bir tür parametresinin [yönetilmeyen bir tür](../language-reference/builtin-types/unmanaged-types.md)olması gerektiğini belirtmek için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2cd8c-159">You can also use the new `unmanaged` constraint, to specify that a type parameter must be an [unmanaged type](../language-reference/builtin-types/unmanaged-types.md).</span></span>

<span data-ttu-id="2cd8c-160">Daha fazla bilgi için bkz. tür parametrelerinde [ `where` genel kısıtlamalar](../language-reference/keywords/where-generic-type-constraint.md) ve [kısıtlamalar](../programming-guide/generics/constraints-on-type-parameters.md)hakkında makaleler.</span><span class="sxs-lookup"><span data-stu-id="2cd8c-160">For more information, see the articles on [`where` generic constraints](../language-reference/keywords/where-generic-type-constraint.md) and [constraints on type parameters](../programming-guide/generics/constraints-on-type-parameters.md).</span></span>

<span data-ttu-id="2cd8c-161">Bu kısıtlamaları var olan türlere eklemek uyumsuz bir [değişiklik](version-update-considerations.md#incompatible-changes).</span><span class="sxs-lookup"><span data-stu-id="2cd8c-161">Adding these constraints to existing types is an [incompatible change](version-update-considerations.md#incompatible-changes).</span></span> <span data-ttu-id="2cd8c-162">Kapalı genel türler artık bu yeni kısıtlamaları karşılamayabilir.</span><span class="sxs-lookup"><span data-stu-id="2cd8c-162">Closed generic types may no longer meet these new constraints.</span></span>

## <a name="make-existing-features-better"></a><span data-ttu-id="2cd8c-163">Mevcut özellikleri daha iyi yapın</span><span class="sxs-lookup"><span data-stu-id="2cd8c-163">Make existing features better</span></span>

<span data-ttu-id="2cd8c-164">İkinci tema, dildeki özelliklere yönelik iyileştirmeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="2cd8c-164">The second theme provides improvements to features in the language.</span></span> <span data-ttu-id="2cd8c-165">Bu özellikler yazarken C#üretkenliği geliştirir.</span><span class="sxs-lookup"><span data-stu-id="2cd8c-165">These features improve productivity when writing C#.</span></span>

### <a name="tuples-support--and-"></a><span data-ttu-id="2cd8c-166">Tanımlama grubu `==` desteği ve`!=`</span><span class="sxs-lookup"><span data-stu-id="2cd8c-166">Tuples support `==` and `!=`</span></span>

<span data-ttu-id="2cd8c-167">C# Demet türleri artık ve `==` `!=`destekler.</span><span class="sxs-lookup"><span data-stu-id="2cd8c-167">The C# tuple types now support `==` and `!=`.</span></span> <span data-ttu-id="2cd8c-168">Daha fazla bilgi için bkz. [tanımlama](../tuples.md)bilgileri hakkındaki [makaleleri kapsayan bölüm](../tuples.md#equality-and-tuples) .</span><span class="sxs-lookup"><span data-stu-id="2cd8c-168">For more information, see the section covering [equality](../tuples.md#equality-and-tuples) in the article on [tuples](../tuples.md).</span></span>

### <a name="attach-attributes-to-the-backing-fields-for-auto-implemented-properties"></a><span data-ttu-id="2cd8c-169">Otomatik uygulanan özellikler için yedekleme alanlarına öznitelikler iliştirme</span><span class="sxs-lookup"><span data-stu-id="2cd8c-169">Attach attributes to the backing fields for auto-implemented properties</span></span>

<span data-ttu-id="2cd8c-170">Bu sözdizimi artık desteklenmektedir:</span><span class="sxs-lookup"><span data-stu-id="2cd8c-170">This syntax is now supported:</span></span>

```csharp
[field: SomeThingAboutFieldAttribute]
public int SomeProperty { get; set; }
```

<span data-ttu-id="2cd8c-171">Özniteliği `SomeThingAboutFieldAttribute` , için `SomeProperty`derleyicinin oluşturduğu yedekleme alanına uygulanır.</span><span class="sxs-lookup"><span data-stu-id="2cd8c-171">The attribute `SomeThingAboutFieldAttribute` is applied to the compiler generated backing field for `SomeProperty`.</span></span> <span data-ttu-id="2cd8c-172">Daha fazla bilgi için bkz [](../programming-guide/concepts/attributes/index.md) . C# programlama kılavuzundaki öznitelikler.</span><span class="sxs-lookup"><span data-stu-id="2cd8c-172">For more information, see [attributes](../programming-guide/concepts/attributes/index.md) in the C# programming guide.</span></span>

### <a name="in-method-overload-resolution-tiebreaker"></a><span data-ttu-id="2cd8c-173">`in`yöntem aşırı yükleme çözünürlüğü tiekesici</span><span class="sxs-lookup"><span data-stu-id="2cd8c-173">`in` method overload resolution tiebreaker</span></span>

<span data-ttu-id="2cd8c-174">`in` Bağımsız değişken değiştiricisi eklendiğinde, bu iki yöntem bir belirsizliğe neden olur:</span><span class="sxs-lookup"><span data-stu-id="2cd8c-174">When the `in` argument modifier was added, these two methods would cause an ambiguity:</span></span>

```csharp
static void M(S arg);
static void M(in S arg);
```

<span data-ttu-id="2cd8c-175">Artık, by değeri (önceki örnekte ilk olarak) aşırı yüklemesi, salt okunur başvuru sürümünden daha iyidir.</span><span class="sxs-lookup"><span data-stu-id="2cd8c-175">Now, the by value (first in the preceding example) overload is better than the by readonly reference version.</span></span> <span data-ttu-id="2cd8c-176">Salt okunur başvuru bağımsız değişkeniyle sürümü çağırmak için, yöntemini çağırırken `in` değiştiricisini dahil etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="2cd8c-176">To call the version with the readonly reference argument, you must include the `in` modifier when calling the method.</span></span>

> [!NOTE]
> <span data-ttu-id="2cd8c-177">Bu bir hata düzeltilme olarak uygulandı.</span><span class="sxs-lookup"><span data-stu-id="2cd8c-177">This was implemented as a bug fix.</span></span> <span data-ttu-id="2cd8c-178">Dil sürümü "7,2" olarak ayarlanmış olsa bile bu artık belirsizdir.</span><span class="sxs-lookup"><span data-stu-id="2cd8c-178">This no longer is ambiguous even with the language version set to "7.2".</span></span>

<span data-ttu-id="2cd8c-179">Daha fazla bilgi için, [ `in` parametre değiştiricisiyle](../language-reference/keywords/in-parameter-modifier.md)ilgili makaleye bakın.</span><span class="sxs-lookup"><span data-stu-id="2cd8c-179">For more information, see the article on the [`in` parameter modifier](../language-reference/keywords/in-parameter-modifier.md).</span></span>

### <a name="extend-expression-variables-in-initializers"></a><span data-ttu-id="2cd8c-180">Başlatıcılarda ifade değişkenlerini genişletme</span><span class="sxs-lookup"><span data-stu-id="2cd8c-180">Extend expression variables in initializers</span></span>

<span data-ttu-id="2cd8c-181">Değişken bildirimlerine izin `out` vermek C# için 7,0 'e eklenen sözdizimi, alan başlatıcıları, özellik başlatıcıları, Oluşturucu başlatıcıları ve sorgu yan tümcelerini kapsayacak şekilde genişletilmiştir.</span><span class="sxs-lookup"><span data-stu-id="2cd8c-181">The syntax added in C# 7.0 to allow `out` variable declarations has been extended to include field initializers, property initializers, constructor initializers, and query clauses.</span></span> <span data-ttu-id="2cd8c-182">Aşağıdaki örnek gibi kodu sunar:</span><span class="sxs-lookup"><span data-stu-id="2cd8c-182">It enables code such as the following example:</span></span>

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

### <a name="improved-overload-candidates"></a><span data-ttu-id="2cd8c-183">Geliştirilmiş aşırı yükleme adayları</span><span class="sxs-lookup"><span data-stu-id="2cd8c-183">Improved overload candidates</span></span>

<span data-ttu-id="2cd8c-184">Her sürümde, aşırı yükleme çözümleme kuralları belirsiz Yöntem etkinleştirmeleri "belirgin" bir seçeneğe sahip olduğu durumlara göre güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="2cd8c-184">In every release, the overload resolution rules get updated to address situations where ambiguous method invocations have an "obvious" choice.</span></span> <span data-ttu-id="2cd8c-185">Bu sürüm, derleyicinin açık seçimi seçmesini sağlamaya yardımcı olmak için üç yeni kural ekler:</span><span class="sxs-lookup"><span data-stu-id="2cd8c-185">This release adds three new rules to help the compiler pick the obvious choice:</span></span>

1. <span data-ttu-id="2cd8c-186">Bir yöntem grubu hem örnek hem de statik üye içerdiğinde, yöntem bir örnek alıcısı veya bağlamı olmadan çağrılırsa, derleyici örnek üyelerini atar.</span><span class="sxs-lookup"><span data-stu-id="2cd8c-186">When a method group contains both instance and static members, the compiler discards the instance members if the method was invoked without an instance receiver or context.</span></span> <span data-ttu-id="2cd8c-187">Yöntem bir örnek alıcısıyla çağrılırsa derleyici statik üyeleri atar.</span><span class="sxs-lookup"><span data-stu-id="2cd8c-187">The compiler discards the static members if the method was invoked with an instance receiver.</span></span> <span data-ttu-id="2cd8c-188">Alıcı olmadığında, derleyici statik bir bağlamda yalnızca statik üyeleri ve statik ve örnek üyelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="2cd8c-188">When there is no receiver, the compiler includes only static members in a static context, otherwise both static and instance members.</span></span> <span data-ttu-id="2cd8c-189">Alıcı bir örnek veya tür ındexattributes, derleyici her ikisini de içerir.</span><span class="sxs-lookup"><span data-stu-id="2cd8c-189">When the receiver is ambiguously an instance or type, the compiler includes both.</span></span> <span data-ttu-id="2cd8c-190">Örtük `this` bir örnek alıcısının kullanıldığı statik bir bağlam, statik üyeler gibi, hiçbir `this` üyenin, örneğin, alan başlatıcıları ve bu gibi kullanılamayan yerleri `this` de içerir. Oluşturucu başlatıcıları.</span><span class="sxs-lookup"><span data-stu-id="2cd8c-190">A static context, where an implicit `this` instance receiver cannot be used, includes the body of members where no `this` is defined, such as static members, as well as places where `this` cannot be used, such as field initializers and constructor-initializers.</span></span>
1. <span data-ttu-id="2cd8c-191">Bir yöntem grubu, tür bağımsız değişkenleri kısıtlamalarını karşılamadığı bazı genel yöntemler içerdiğinde, bu üyeler aday kümesinden kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="2cd8c-191">When a method group contains some generic methods whose type arguments do not satisfy their constraints, these members are removed from the candidate set.</span></span>
1. <span data-ttu-id="2cd8c-192">Bir yöntem grubu dönüştürmesi için, dönüş türü, temsilcinin dönüş türüyle eşleşmeyen aday Yöntemler kümeden kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="2cd8c-192">For a method group conversion, candidate methods whose return type doesn't match up with the delegate's return type are removed from the set.</span></span>

<span data-ttu-id="2cd8c-193">Bu değişikliği yalnızca, hangi yöntemin daha iyi olduğundan emin olduğunuzda belirsiz yöntem aşırı yüklemeleri için daha az derleyici hatası bulacağınız için fark edeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="2cd8c-193">You'll only notice this change because you'll find fewer compiler errors for ambiguous method overloads when you are sure which method is better.</span></span>

## <a name="new-compiler-options"></a><span data-ttu-id="2cd8c-194">Yeni derleyici seçenekleri</span><span class="sxs-lookup"><span data-stu-id="2cd8c-194">New compiler options</span></span>

<span data-ttu-id="2cd8c-195">Yeni derleyici seçenekleri, programlar için C# yeni derlemeyi ve DevOps senaryolarını destekler.</span><span class="sxs-lookup"><span data-stu-id="2cd8c-195">New compiler options support new build and DevOps scenarios for C# programs.</span></span>

### <a name="public-or-open-source-signing"></a><span data-ttu-id="2cd8c-196">Ortak veya açık kaynak imzalama</span><span class="sxs-lookup"><span data-stu-id="2cd8c-196">Public or Open Source signing</span></span>

<span data-ttu-id="2cd8c-197">`-publicsign` Derleyici seçeneği derleyiciye ortak anahtar kullanarak derlemeyi imzalamasını söyler.</span><span class="sxs-lookup"><span data-stu-id="2cd8c-197">The `-publicsign` compiler option instructs the compiler to sign the assembly using a public key.</span></span> <span data-ttu-id="2cd8c-198">Derleme imzalanmış olarak işaretlenir, ancak imza ortak anahtardan alınır.</span><span class="sxs-lookup"><span data-stu-id="2cd8c-198">The assembly is marked as signed, but the signature is taken from the public key.</span></span> <span data-ttu-id="2cd8c-199">Bu seçenek, açık kaynaklı projelerden ortak anahtar kullanarak imzalı derlemeler oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="2cd8c-199">This option enables you to build signed assemblies from open-source projects using a public key.</span></span>

<span data-ttu-id="2cd8c-200">Daha fazla bilgi için bkz. [-publicsign derleyici seçeneği](../language-reference/compiler-options/publicsign-compiler-option.md) makalesi.</span><span class="sxs-lookup"><span data-stu-id="2cd8c-200">For more information, see the [-publicsign compiler option](../language-reference/compiler-options/publicsign-compiler-option.md) article.</span></span>

### <a name="pathmap"></a><span data-ttu-id="2cd8c-201">pathmap</span><span class="sxs-lookup"><span data-stu-id="2cd8c-201">pathmap</span></span>

<span data-ttu-id="2cd8c-202">`-pathmap` Derleyici seçeneği, derleyicinin kaynak yollarını eşlenen kaynak yollarla derleme ortamından değiştirmesini söyler.</span><span class="sxs-lookup"><span data-stu-id="2cd8c-202">The `-pathmap` compiler option instructs the compiler to replace source paths from the build environment with mapped source paths.</span></span> <span data-ttu-id="2cd8c-203">Seçeneği, derleyici tarafından pdb dosyalarına veya <xref:System.Runtime.CompilerServices.CallerFilePathAttribute>için yazılan kaynak yolunu denetler. `-pathmap`</span><span class="sxs-lookup"><span data-stu-id="2cd8c-203">The `-pathmap` option controls the source path written by the compiler to PDB files or for the <xref:System.Runtime.CompilerServices.CallerFilePathAttribute>.</span></span>

<span data-ttu-id="2cd8c-204">Daha fazla bilgi için bkz. [-pathmap derleyici seçeneği](../language-reference/compiler-options/pathmap-compiler-option.md) makalesi.</span><span class="sxs-lookup"><span data-stu-id="2cd8c-204">For more information, see the [-pathmap compiler option](../language-reference/compiler-options/pathmap-compiler-option.md) article.</span></span>
