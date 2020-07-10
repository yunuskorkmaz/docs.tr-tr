---
title: C# 7.1 Yenilikleri
description: C# 7,1 ' deki yeni özelliklere genel bakış.
ms.date: 04/09/2019
ms.openlocfilehash: fe6e49eb01e24a27bc7970900c05150378ab194a
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174776"
---
# <a name="whats-new-in-c-71"></a><span data-ttu-id="6b776-103">C# 7.1 Yenilikleri</span><span class="sxs-lookup"><span data-stu-id="6b776-103">What's new in C# 7.1</span></span>

<span data-ttu-id="6b776-104">C# 7,1, C# dilinin ilk noktası sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="6b776-104">C# 7.1 is the first point release to the C# language.</span></span> <span data-ttu-id="6b776-105">Dil için artan bir sürüm temposunda işaretler.</span><span class="sxs-lookup"><span data-stu-id="6b776-105">It marks an increased release cadence for the language.</span></span> <span data-ttu-id="6b776-106">Yeni özellikleri daha erken kullanabilirsiniz, her yeni özellik için idealdir.</span><span class="sxs-lookup"><span data-stu-id="6b776-106">You can use the new features sooner, ideally when each new feature is ready.</span></span> <span data-ttu-id="6b776-107">C# 7,1, derleyiciyi belirtilen dilin sürümüyle eşleşecek şekilde yapılandırma yeteneğini ekler.</span><span class="sxs-lookup"><span data-stu-id="6b776-107">C# 7.1 adds the ability to configure the compiler to match a specified version of the language.</span></span> <span data-ttu-id="6b776-108">Bu sayede, dil sürümlerini yükseltme kararına araçları yükseltme kararını ayırmanızı sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6b776-108">That enables you to separate the decision to upgrade tools from the decision to upgrade language versions.</span></span>

<span data-ttu-id="6b776-109">C# 7,1, [dil sürümü seçimi](../language-reference/configure-language-version.md) yapılandırma öğesini, üç yeni dil özelliğini ve yeni derleyici davranışını ekler.</span><span class="sxs-lookup"><span data-stu-id="6b776-109">C# 7.1 adds the [language version selection](../language-reference/configure-language-version.md) configuration element, three new language features, and new compiler behavior.</span></span>

<span data-ttu-id="6b776-110">Bu sürümdeki yeni dil özellikleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="6b776-110">The new language features in this release are:</span></span>

- [<span data-ttu-id="6b776-111">`async``Main`yöntemi</span><span class="sxs-lookup"><span data-stu-id="6b776-111">`async` `Main` method</span></span>](#async-main)
  - <span data-ttu-id="6b776-112">Bir uygulama için giriş noktası değiştiriciye sahip olabilir `async` .</span><span class="sxs-lookup"><span data-stu-id="6b776-112">The entry point for an application can have the `async` modifier.</span></span>
- [<span data-ttu-id="6b776-113">`default`değişmez değer ifadeleri</span><span class="sxs-lookup"><span data-stu-id="6b776-113">`default` literal expressions</span></span>](#default-literal-expressions)
  - <span data-ttu-id="6b776-114">Hedef türü çıkarsanamıyor varsayılan değer ifadelerinde varsayılan değişmez ifadeleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6b776-114">You can use default literal expressions in default value expressions when the target type can be inferred.</span></span>
- [<span data-ttu-id="6b776-115">Gösterilen demet öğesi adları</span><span class="sxs-lookup"><span data-stu-id="6b776-115">Inferred tuple element names</span></span>](#inferred-tuple-element-names)
  - <span data-ttu-id="6b776-116">Kayıt düzeni öğelerinin adları, birçok durumda demet başlatmasıyla çıkarsanamıyor.</span><span class="sxs-lookup"><span data-stu-id="6b776-116">The names of tuple elements can be inferred from tuple initialization in many cases.</span></span>
- [<span data-ttu-id="6b776-117">Genel tür parametrelerinde model eşleştirme</span><span class="sxs-lookup"><span data-stu-id="6b776-117">Pattern matching on generic type parameters</span></span>](#pattern-matching-on-generic-type-parameters)
  - <span data-ttu-id="6b776-118">Türü genel bir tür parametresi olan değişkenlerde model eşleşme ifadeleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6b776-118">You can use pattern match expressions on variables whose type is a generic type parameter.</span></span>

<span data-ttu-id="6b776-119">Son olarak, derleyici iki seçeneğe sahiptir `-refout` ve `-refonly` Bu, [Başvuru derleme üretimini](#reference-assembly-generation)denetler.</span><span class="sxs-lookup"><span data-stu-id="6b776-119">Finally, the compiler has two options `-refout` and `-refonly` that control [reference assembly generation](#reference-assembly-generation).</span></span>

<span data-ttu-id="6b776-120">En son özellikleri bir nokta sürümünde kullanmak için, [Derleyici dil sürümünü yapılandırmanız](../language-reference/configure-language-version.md) ve sürümü seçmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="6b776-120">To use the latest features in a point release, you need to [configure the compiler language version](../language-reference/configure-language-version.md) and select the version.</span></span>

<span data-ttu-id="6b776-121">Bu makalenin geri kalanında her özelliğe bir genel bakış sunulmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6b776-121">The remainder of this article provides an overview of each feature.</span></span> <span data-ttu-id="6b776-122">Her bir özellik için, arkasında yatan bir düşünme olduğunu öğrenirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6b776-122">For each feature, you'll learn the reasoning behind it.</span></span> <span data-ttu-id="6b776-123">Söz dizimini öğrenirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6b776-123">You'll learn the syntax.</span></span> <span data-ttu-id="6b776-124">Genel aracı kullanarak ortamınızdaki bu özellikleri keşfedebilirsiniz `dotnet try` :</span><span class="sxs-lookup"><span data-stu-id="6b776-124">You can explore these features in your environment using the `dotnet try` global tool:</span></span>

1. <span data-ttu-id="6b776-125">[DotNet-TRY](https://github.com/dotnet/try/blob/master/README.md#setup) küresel aracını yükler.</span><span class="sxs-lookup"><span data-stu-id="6b776-125">Install the [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) global tool.</span></span>
1. <span data-ttu-id="6b776-126">[DotNet/TRY-Samples](https://github.com/dotnet/try-samples) deposunu kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="6b776-126">Clone the [dotnet/try-samples](https://github.com/dotnet/try-samples) repository.</span></span>
1. <span data-ttu-id="6b776-127">*TRY-Samples* deposu için geçerli dizini *csharp7* alt dizinine ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="6b776-127">Set the current directory to the *csharp7* subdirectory for the *try-samples* repository.</span></span>
1. <span data-ttu-id="6b776-128">Şu komutu çalıştırın: `dotnet try`.</span><span class="sxs-lookup"><span data-stu-id="6b776-128">Run `dotnet try`.</span></span>

## <a name="async-main"></a><span data-ttu-id="6b776-129">Zaman uyumsuz ana</span><span class="sxs-lookup"><span data-stu-id="6b776-129">Async main</span></span>

<span data-ttu-id="6b776-130">*Zaman uyumsuz Main* yöntemi, `await` yöntekinizdeki kullanmanıza olanak sağlar `Main` .</span><span class="sxs-lookup"><span data-stu-id="6b776-130">An *async main* method enables you to use `await` in your `Main` method.</span></span>
<span data-ttu-id="6b776-131">Daha önce yazmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="6b776-131">Previously you would need to write:</span></span>

```csharp
static int Main()
{
    return DoAsyncWork().GetAwaiter().GetResult();
}
```

<span data-ttu-id="6b776-132">Artık şunu yazabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6b776-132">You can now write:</span></span>

```csharp
static async Task<int> Main()
{
    // This could also be replaced with the body
    // DoAsyncWork, including its await expressions:
    return await DoAsyncWork();
}
```

<span data-ttu-id="6b776-133">Programınız çıkış kodu döndürmezse, şunu `Main` döndüren bir yöntem bildirebilirsiniz <xref:System.Threading.Tasks.Task> :</span><span class="sxs-lookup"><span data-stu-id="6b776-133">If your program doesn't return an exit code, you can declare a `Main` method that returns a <xref:System.Threading.Tasks.Task>:</span></span>

```csharp
static async Task Main()
{
    await SomeAsyncMethod();
}
```

<span data-ttu-id="6b776-134">Programlama kılavuzundaki [zaman uyumsuz ana](../programming-guide/main-and-command-args/index.md) makaledeki ayrıntılar hakkında daha fazla bilgi edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6b776-134">You can read more about the details in the [async main](../programming-guide/main-and-command-args/index.md) article in the programming guide.</span></span>

## <a name="default-literal-expressions"></a><span data-ttu-id="6b776-135">Varsayılan değişmez değer ifadeleri</span><span class="sxs-lookup"><span data-stu-id="6b776-135">Default literal expressions</span></span>

<span data-ttu-id="6b776-136">Varsayılan değişmez değer ifadeleri varsayılan değer ifadelerine yönelik bir geliştirmedir.</span><span class="sxs-lookup"><span data-stu-id="6b776-136">Default literal expressions are an enhancement to default value expressions.</span></span>
<span data-ttu-id="6b776-137">Bu ifadeler varsayılan değere bir değişken başlatır.</span><span class="sxs-lookup"><span data-stu-id="6b776-137">These expressions initialize a variable to the default value.</span></span> <span data-ttu-id="6b776-138">Daha önce yazdığınız yer:</span><span class="sxs-lookup"><span data-stu-id="6b776-138">Where you previously would write:</span></span>

```csharp
Func<string, bool> whereClause = default(Func<string, bool>);
```

<span data-ttu-id="6b776-139">Artık başlatmanın sağ tarafındaki türü atlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6b776-139">You can now omit the type on the right-hand side of the initialization:</span></span>

```csharp
Func<string, bool> whereClause = default;
```

<span data-ttu-id="6b776-140">Daha fazla bilgi için [varsayılan işleç](../language-reference/operators/default.md) makalesinin [varsayılan değişmez değeri](../language-reference/operators/default.md#default-literal) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="6b776-140">For more information, see the [default literal](../language-reference/operators/default.md#default-literal) section of the [default operator](../language-reference/operators/default.md) article.</span></span>

## <a name="inferred-tuple-element-names"></a><span data-ttu-id="6b776-141">Gösterilen demet öğesi adları</span><span class="sxs-lookup"><span data-stu-id="6b776-141">Inferred tuple element names</span></span>

<span data-ttu-id="6b776-142">Bu özellik C# 7,0 ' de tanıtılan tanımlama grupları özelliği için küçük bir geliştirmedir.</span><span class="sxs-lookup"><span data-stu-id="6b776-142">This feature is a small enhancement to the tuples feature introduced in C# 7.0.</span></span> <span data-ttu-id="6b776-143">Bir tanımlama grubunu başlattığınızda, atamanın sağ tarafında kullanılan değişkenler demet öğeleri için istediğiniz adlarla aynıdır:</span><span class="sxs-lookup"><span data-stu-id="6b776-143">Many times when you initialize a tuple, the variables used for the right side of the assignment are the same as the names you'd like for the tuple elements:</span></span>

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count: count, label: label);
```

<span data-ttu-id="6b776-144">Kayıt düzeni öğelerinin adları C# 7,1 ' de kayıt kümesini başlatmak için kullanılan değişkenlerden çıkarsanamıyor:</span><span class="sxs-lookup"><span data-stu-id="6b776-144">The names of tuple elements can be inferred from the variables used to initialize the tuple in C# 7.1:</span></span>

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count, label); // element names are "count" and "label"
```

<span data-ttu-id="6b776-145">[Demet türleri](../language-reference/builtin-types/value-tuples.md) makalesinde bu özellik hakkında daha fazla bilgi edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6b776-145">You can learn more about this feature in the [Tuple types](../language-reference/builtin-types/value-tuples.md) article.</span></span>

## <a name="pattern-matching-on-generic-type-parameters"></a><span data-ttu-id="6b776-146">Genel tür parametrelerinde model eşleştirme</span><span class="sxs-lookup"><span data-stu-id="6b776-146">Pattern matching on generic type parameters</span></span>

<span data-ttu-id="6b776-147">C# 7,1 ile başlayarak, `is` ve `switch` tür deseninin model ifadesi bir genel tür parametresinin türüne sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="6b776-147">Beginning with C# 7.1, the pattern expression for `is` and the `switch` type pattern may have the type of a generic type parameter.</span></span> <span data-ttu-id="6b776-148">Bu, ya da türünde olabilecek türler denetlenirken `struct` `class` ve kutulamayı önlemek istediğiniz durumlarda yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="6b776-148">This can be most useful when checking types that may be either `struct` or `class` types, and you want to avoid boxing.</span></span>

## <a name="reference-assembly-generation"></a><span data-ttu-id="6b776-149">Başvuru derlemesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="6b776-149">Reference assembly generation</span></span>

<span data-ttu-id="6b776-150">*Yalnızca başvuru derlemeler*üreten iki yeni derleyici seçeneği vardır: [-refout](../language-reference/compiler-options/refout-compiler-option.md) ve [-refonly](../language-reference/compiler-options/refonly-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="6b776-150">There are two new compiler options that generate *reference-only assemblies*: [-refout](../language-reference/compiler-options/refout-compiler-option.md) and [-refonly](../language-reference/compiler-options/refonly-compiler-option.md).</span></span>
<span data-ttu-id="6b776-151">Bağlantılı makaleler, bu seçenekleri ve başvuru derlemelerini daha ayrıntılı bir şekilde açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="6b776-151">The linked articles explain these options and reference assemblies in more detail.</span></span>
