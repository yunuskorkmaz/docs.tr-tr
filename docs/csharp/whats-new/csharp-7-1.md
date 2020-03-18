---
title: C# 7.1 Yenilikleri
description: C# 7.1'deki yeni özelliklere genel bakış.
ms.date: 04/09/2019
ms.openlocfilehash: 5d2d6f51b6422f5b4db5c6bd275b5ffce1f695f8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399709"
---
# <a name="whats-new-in-c-71"></a><span data-ttu-id="8d5f8-103">C# 7.1 Yenilikleri</span><span class="sxs-lookup"><span data-stu-id="8d5f8-103">What's new in C# 7.1</span></span>

<span data-ttu-id="8d5f8-104">C# 7.1, C# dilinin ilk noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="8d5f8-104">C# 7.1 is the first point release to the C# language.</span></span> <span data-ttu-id="8d5f8-105">Bu dil için artan bir sürüm cadence işaretler.</span><span class="sxs-lookup"><span data-stu-id="8d5f8-105">It marks an increased release cadence for the language.</span></span> <span data-ttu-id="8d5f8-106">Yeni özellikleri, ideal olarak her yeni özellik hazır olduğunda daha erken kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d5f8-106">You can use the new features sooner, ideally when each new feature is ready.</span></span> <span data-ttu-id="8d5f8-107">C# 7.1, derleyiciyi dilin belirli bir sürümüyle eşleşecek şekilde yapılandırma olanağı ekler.</span><span class="sxs-lookup"><span data-stu-id="8d5f8-107">C# 7.1 adds the ability to configure the compiler to match a specified version of the language.</span></span> <span data-ttu-id="8d5f8-108">Bu, araçları yükseltme kararını dil sürümlerini yükseltme kararından ayırmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="8d5f8-108">That enables you to separate the decision to upgrade tools from the decision to upgrade language versions.</span></span>

<span data-ttu-id="8d5f8-109">C# 7.1 [dil sürümü seçimi](../language-reference/configure-language-version.md) yapılandırma öğesi, üç yeni dil özellikleri ve yeni derleyici davranışı ekler.</span><span class="sxs-lookup"><span data-stu-id="8d5f8-109">C# 7.1 adds the [language version selection](../language-reference/configure-language-version.md) configuration element, three new language features, and new compiler behavior.</span></span>

<span data-ttu-id="8d5f8-110">Bu sürümdeki yeni dil özellikleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="8d5f8-110">The new language features in this release are:</span></span>

- [<span data-ttu-id="8d5f8-111">`async``Main` yöntem</span><span class="sxs-lookup"><span data-stu-id="8d5f8-111">`async` `Main` method</span></span>](#async-main)
  - <span data-ttu-id="8d5f8-112">Bir uygulama için giriş noktası `async` değiştirici olabilir.</span><span class="sxs-lookup"><span data-stu-id="8d5f8-112">The entry point for an application can have the `async` modifier.</span></span>
- [<span data-ttu-id="8d5f8-113">`default`gerçek ifadeler</span><span class="sxs-lookup"><span data-stu-id="8d5f8-113">`default` literal expressions</span></span>](#default-literal-expressions)
  - <span data-ttu-id="8d5f8-114">Varsayılan değer ifadelerinde varsayılan gerçek ifadeleri, hedef türü çıkarılabilirken kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d5f8-114">You can use default literal expressions in default value expressions when the target type can be inferred.</span></span>
- [<span data-ttu-id="8d5f8-115">Çıkarılan tuple öğesi adları</span><span class="sxs-lookup"><span data-stu-id="8d5f8-115">Inferred tuple element names</span></span>](#inferred-tuple-element-names)
  - <span data-ttu-id="8d5f8-116">Tuple elemanlarının adları birçok durumda tuple başlatma çıkarılabilir.</span><span class="sxs-lookup"><span data-stu-id="8d5f8-116">The names of tuple elements can be inferred from tuple initialization in many cases.</span></span>
- [<span data-ttu-id="8d5f8-117">Genel tür parametreleri üzerinde desen eşleştirme</span><span class="sxs-lookup"><span data-stu-id="8d5f8-117">Pattern matching on generic type parameters</span></span>](#pattern-matching-on-generic-type-parameters)
  - <span data-ttu-id="8d5f8-118">Türü genel bir tür parametresi olan değişkenlerde desen eşleştirme ifadeleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d5f8-118">You can use pattern match expressions on variables whose type is a generic type parameter.</span></span>

<span data-ttu-id="8d5f8-119">Son olarak, derleyici `-refout` iki `-refonly` seçenek vardır ve bu kontrol [referans derleme nesil.](#reference-assembly-generation)</span><span class="sxs-lookup"><span data-stu-id="8d5f8-119">Finally, the compiler has two options `-refout` and `-refonly` that control [reference assembly generation](#reference-assembly-generation).</span></span>

<span data-ttu-id="8d5f8-120">Bir nokta sürümündeki en son özellikleri kullanmak için [derleyici dili sürümünü yapılandırmanız](../language-reference/configure-language-version.md) ve sürümü seçmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="8d5f8-120">To use the latest features in a point release, you need to [configure the compiler language version](../language-reference/configure-language-version.md) and select the version.</span></span>

<span data-ttu-id="8d5f8-121">Bu makalenin geri kalanı her özelliğin genel bir özetini sağlar.</span><span class="sxs-lookup"><span data-stu-id="8d5f8-121">The remainder of this article provides an overview of each feature.</span></span> <span data-ttu-id="8d5f8-122">Her özellik için, bunun arkasındaki mantığı öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="8d5f8-122">For each feature, you'll learn the reasoning behind it.</span></span> <span data-ttu-id="8d5f8-123">Sözdizimini öğreneceksin.</span><span class="sxs-lookup"><span data-stu-id="8d5f8-123">You'll learn the syntax.</span></span> <span data-ttu-id="8d5f8-124">`dotnet try` Bu özellikleri ortamınızda genel aracı kullanarak keşfedebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8d5f8-124">You can explore these features in your environment using the `dotnet try` global tool:</span></span>

1. <span data-ttu-id="8d5f8-125">[dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) global aracını yükleyin.</span><span class="sxs-lookup"><span data-stu-id="8d5f8-125">Install the [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) global tool.</span></span>
1. <span data-ttu-id="8d5f8-126">[Dotnet/try-samples](https://github.com/dotnet/try-samples) deposunu klonla.</span><span class="sxs-lookup"><span data-stu-id="8d5f8-126">Clone the [dotnet/try-samples](https://github.com/dotnet/try-samples) repository.</span></span>
1. <span data-ttu-id="8d5f8-127">*Deneme örnekleri* deposu için geçerli dizini *csharp7* alt dizinine ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="8d5f8-127">Set the current directory to the *csharp7* subdirectory for the *try-samples* repository.</span></span>
1. <span data-ttu-id="8d5f8-128">`dotnet try` öğesini çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="8d5f8-128">Run `dotnet try`.</span></span>

## <a name="async-main"></a><span data-ttu-id="8d5f8-129">Async ana</span><span class="sxs-lookup"><span data-stu-id="8d5f8-129">Async main</span></span>

<span data-ttu-id="8d5f8-130">Async *ana* yöntemi yönteminizde `await` `Main` kullanmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="8d5f8-130">An *async main* method enables you to use `await` in your `Main` method.</span></span>
<span data-ttu-id="8d5f8-131">Daha önce yazmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="8d5f8-131">Previously you would need to write:</span></span>

```csharp
static int Main()
{
    return DoAsyncWork().GetAwaiter().GetResult();
}
```

<span data-ttu-id="8d5f8-132">Şimdi yazabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8d5f8-132">You can now write:</span></span>

```csharp
static async Task<int> Main()
{
    // This could also be replaced with the body
    // DoAsyncWork, including its await expressions:
    return await DoAsyncWork();
}
```

<span data-ttu-id="8d5f8-133">Programınız bir çıkış kodu döndürmüyorsa, `Main` bir yöntem <xref:System.Threading.Tasks.Task>bildirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8d5f8-133">If your program doesn't return an exit code, you can declare a `Main` method that returns a <xref:System.Threading.Tasks.Task>:</span></span>

```csharp
static async Task Main()
{
    await SomeAsyncMethod();
}
```

<span data-ttu-id="8d5f8-134">Programlama kılavuzundaki [async ana](../programming-guide/main-and-command-args/index.md) makalesinde ayrıntılar hakkında daha fazla bilgi edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d5f8-134">You can read more about the details in the [async main](../programming-guide/main-and-command-args/index.md) article in the programming guide.</span></span>

## <a name="default-literal-expressions"></a><span data-ttu-id="8d5f8-135">Varsayılan gerçek ifadeler</span><span class="sxs-lookup"><span data-stu-id="8d5f8-135">Default literal expressions</span></span>

<span data-ttu-id="8d5f8-136">Varsayılan gerçek ifadeler varsayılan değer ifadeleri için bir geliştirme vardır.</span><span class="sxs-lookup"><span data-stu-id="8d5f8-136">Default literal expressions are an enhancement to default value expressions.</span></span>
<span data-ttu-id="8d5f8-137">Bu ifadeler varsayılan değeriçin bir değişken ilerler.</span><span class="sxs-lookup"><span data-stu-id="8d5f8-137">These expressions initialize a variable to the default value.</span></span> <span data-ttu-id="8d5f8-138">Daha önce yazacağınız yer:</span><span class="sxs-lookup"><span data-stu-id="8d5f8-138">Where you previously would write:</span></span>

```csharp
Func<string, bool> whereClause = default(Func<string, bool>);
```

<span data-ttu-id="8d5f8-139">Şimdi başbaşlatmanın sağ tarafındaki türü atlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8d5f8-139">You can now omit the type on the right-hand side of the initialization:</span></span>

```csharp
Func<string, bool> whereClause = default;
```

<span data-ttu-id="8d5f8-140">Daha fazla bilgi için varsayılan [işleç](../language-reference/operators/default.md) makalesinin [varsayılan gerçek](../language-reference/operators/default.md#default-literal) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="8d5f8-140">For more information, see the [default literal](../language-reference/operators/default.md#default-literal) section of the [default operator](../language-reference/operators/default.md) article.</span></span>

## <a name="inferred-tuple-element-names"></a><span data-ttu-id="8d5f8-141">Çıkarılan tuple öğesi adları</span><span class="sxs-lookup"><span data-stu-id="8d5f8-141">Inferred tuple element names</span></span>

<span data-ttu-id="8d5f8-142">Bu özellik, C# 7.0'da tanıtılan tuples özelliğine küçük bir geliştirmedir.</span><span class="sxs-lookup"><span data-stu-id="8d5f8-142">This feature is a small enhancement to the tuples feature introduced in C# 7.0.</span></span> <span data-ttu-id="8d5f8-143">Çoğu zaman bir tuple'ı başharflediğinizde, atamanın sağ tarafı için kullanılan değişkenler, tuple öğeleri için istediğiniz adlarla aynıdır:</span><span class="sxs-lookup"><span data-stu-id="8d5f8-143">Many times when you initialize a tuple, the variables used for the right side of the assignment are the same as the names you'd like for the tuple elements:</span></span>

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count: count, label: label);
```

<span data-ttu-id="8d5f8-144">Tuple elemanlarının adları C# 7.1'deki tuple'ı initiallaştırmak için kullanılan değişkenlerden çıkarılabilir:</span><span class="sxs-lookup"><span data-stu-id="8d5f8-144">The names of tuple elements can be inferred from the variables used to initialize the tuple in C# 7.1:</span></span>

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count, label); // element names are "count" and "label"
```

<span data-ttu-id="8d5f8-145">Bu özellik hakkında daha fazla bilgi için [Tuples](../tuples.md) makalesinde bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d5f8-145">You can learn more about this feature in the [Tuples](../tuples.md) article.</span></span>

## <a name="pattern-matching-on-generic-type-parameters"></a><span data-ttu-id="8d5f8-146">Genel tür parametreleri üzerinde desen eşleştirme</span><span class="sxs-lookup"><span data-stu-id="8d5f8-146">Pattern matching on generic type parameters</span></span>

<span data-ttu-id="8d5f8-147">C# 7.1 ile başlayarak, `is` desen `switch` ifadesi ve tür deseni genel bir tür parametresi türüne sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="8d5f8-147">Beginning with C# 7.1, the pattern expression for `is` and the `switch` type pattern may have the type of a generic type parameter.</span></span> <span data-ttu-id="8d5f8-148">Bu, ya veya `struct` `class` tür olabilir türleri denetler ve kutulama önlemek istediğiniz de en yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="8d5f8-148">This can be most useful when checking types that may be either `struct` or `class` types, and you want to avoid boxing.</span></span>

## <a name="reference-assembly-generation"></a><span data-ttu-id="8d5f8-149">Referans montaj üretimi</span><span class="sxs-lookup"><span data-stu-id="8d5f8-149">Reference assembly generation</span></span>

<span data-ttu-id="8d5f8-150">*Yalnızca referans derlemeleri*oluşturan iki yeni derleyici seçeneği vardır: [-refout](../language-reference/compiler-options/refout-compiler-option.md) ve [-refonly.](../language-reference/compiler-options/refonly-compiler-option.md)</span><span class="sxs-lookup"><span data-stu-id="8d5f8-150">There are two new compiler options that generate *reference-only assemblies*: [-refout](../language-reference/compiler-options/refout-compiler-option.md) and [-refonly](../language-reference/compiler-options/refonly-compiler-option.md).</span></span>
<span data-ttu-id="8d5f8-151">Bağlantılı makaleler bu seçenekleri ve başvuru derlemelerini daha ayrıntılı olarak açıklar.</span><span class="sxs-lookup"><span data-stu-id="8d5f8-151">The linked articles explain these options and reference assemblies in more detail.</span></span>
