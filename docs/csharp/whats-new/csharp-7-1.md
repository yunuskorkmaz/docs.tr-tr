---
title: İçindeki yenilikler C# 7.1
description: İçinde yeni özelliklere genel bakış C# 7.1.
ms.date: 04/09/2019
ms.openlocfilehash: c79c8576f9cbbd921ebf30bd84ee5a817d6dc6e7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59480969"
---
# <a name="whats-new-in-c-71"></a><span data-ttu-id="31899-103">İçindeki yenilikler C# 7.1</span><span class="sxs-lookup"><span data-stu-id="31899-103">What's new in C# 7.1</span></span>

<span data-ttu-id="31899-104">C#ilk noktası sürüm 7.1 olan C# dili.</span><span class="sxs-lookup"><span data-stu-id="31899-104">C# 7.1 is the first point release to the C# language.</span></span> <span data-ttu-id="31899-105">Bunu bir daha yüksek bir yayın temposudur dil için işaretler.</span><span class="sxs-lookup"><span data-stu-id="31899-105">It marks an increased release cadence for the language.</span></span> <span data-ttu-id="31899-106">Her yeni özellik hazır olduğunda, yeni özellikleri daha çabuk, ideal olarak kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="31899-106">You can use the new features sooner, ideally when each new feature is ready.</span></span> <span data-ttu-id="31899-107">C#Derleyicinin, belirtilen bir dile sürümüyle eşleşecek şekilde yapılandırma becerisi 7.1 ekler.</span><span class="sxs-lookup"><span data-stu-id="31899-107">C# 7.1 adds the ability to configure the compiler to match a specified version of the language.</span></span> <span data-ttu-id="31899-108">Dil sürümleri yükseltme kararı araçları yükseltme kararı ayırmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="31899-108">That enables you to separate the decision to upgrade tools from the decision to upgrade language versions.</span></span>

<span data-ttu-id="31899-109">C#7.1 ekler [dil sürüm seçimi](../language-reference/configure-language-version.md) yapılandırma öğesi, üç yeni dil özellikleri ve yeni derleyici davranışı.</span><span class="sxs-lookup"><span data-stu-id="31899-109">C# 7.1 adds the [language version selection](../language-reference/configure-language-version.md) configuration element, three new language features, and new compiler behavior.</span></span>

<span data-ttu-id="31899-110">Bu sürümdeki yeni diz özellikleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="31899-110">The new language features in this release are:</span></span>

* [<span data-ttu-id="31899-111">`async` `Main` Yöntemi</span><span class="sxs-lookup"><span data-stu-id="31899-111">`async` `Main` method</span></span>](#async-main)
  - <span data-ttu-id="31899-112">Bir uygulama için giriş noktası `async` değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="31899-112">The entry point for an application can have the `async` modifier.</span></span>
* [<span data-ttu-id="31899-113">`default` değişmez ifadeleri</span><span class="sxs-lookup"><span data-stu-id="31899-113">`default` literal expressions</span></span>](#default-literal-expressions)
  - <span data-ttu-id="31899-114">Hedef türü çıkarımı yapılan varsayılan değer ifadeleri toplama varsayılan sabit değer ifadeleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="31899-114">You can use default literal expressions in default value expressions when the target type can be inferred.</span></span>
* [<span data-ttu-id="31899-115">Çıkarsanan demet öğesi adları</span><span class="sxs-lookup"><span data-stu-id="31899-115">Inferred tuple element names</span></span>](#inferred-tuple-element-names)
  - <span data-ttu-id="31899-116">Demet öğelerinin adlarını, çoğu durumda demet başlatma içinden gösterilen.</span><span class="sxs-lookup"><span data-stu-id="31899-116">The names of tuple elements can be inferred from tuple initialization in many cases.</span></span>
* [<span data-ttu-id="31899-117">Genel tür parametrelerinde desen</span><span class="sxs-lookup"><span data-stu-id="31899-117">Pattern matching on generic type parameters</span></span>](#pattern-matching-on-generic-type-parameters)
  - <span data-ttu-id="31899-118">Genel tür parametresi türü olan değişkenlerde deseni eşleşme ifadeleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="31899-118">You can use pattern match expressions on variables whose type is a generic type parameter.</span></span>

<span data-ttu-id="31899-119">Son olarak, derleyici iki seçeneğe sahiptir `/refout` ve `/refonly` denetleyen [başvuru bütünleştirilmiş kod oluşturmayı](#reference-assembly-generation).</span><span class="sxs-lookup"><span data-stu-id="31899-119">Finally, the compiler has two options `/refout` and `/refonly` that control [reference assembly generation](#reference-assembly-generation).</span></span>

<span data-ttu-id="31899-120">Bir nokta sürümde en son özellikleri kullanmak için yapmanız [derleyici dil sürüm yapılandırma](../language-reference/configure-language-version.md) ve sürüm seçin.</span><span class="sxs-lookup"><span data-stu-id="31899-120">To use the latest features in a point release, you need to [configure the compiler language version](../language-reference/configure-language-version.md) and select the version.</span></span>

## <a name="async-main"></a><span data-ttu-id="31899-121">Zaman uyumsuz ana</span><span class="sxs-lookup"><span data-stu-id="31899-121">Async main</span></span>

<span data-ttu-id="31899-122">Bir *async main* yöntemi kullanmanıza olanak sağlar `await` içinde `Main` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="31899-122">An *async main* method enables you to use `await` in your `Main` method.</span></span>
<span data-ttu-id="31899-123">Daha önce yazmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="31899-123">Previously you would need to write:</span></span>

```csharp
static int Main()
{
    return DoAsyncWork().GetAwaiter().GetResult();
}
```

<span data-ttu-id="31899-124">Artık yazabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="31899-124">You can now write:</span></span>

```csharp
static async Task<int> Main()
{
    // This could also be replaced with the body
    // DoAsyncWork, including its await expressions:
    return await DoAsyncWork();
}
```

<span data-ttu-id="31899-125">Programınız bir çıkış kodu, döndürmüyor, bildirebilirsiniz bir `Main` döndüren yöntem bir <xref:System.Threading.Tasks.Task>:</span><span class="sxs-lookup"><span data-stu-id="31899-125">If your program doesn't return an exit code, you can declare a `Main` method that returns a <xref:System.Threading.Tasks.Task>:</span></span>

```csharp
static async Task Main()
{
    await SomeAsyncMethod();
}
```

<span data-ttu-id="31899-126">Daha fazla bilgi edinebilirsiniz hakkında ayrıntılar [async main](../programming-guide/main-and-command-args/index.md) Programlama Kılavuzu'nda makale.</span><span class="sxs-lookup"><span data-stu-id="31899-126">You can read more about the details in the [async main](../programming-guide/main-and-command-args/index.md) article in the programming guide.</span></span>

## <a name="default-literal-expressions"></a><span data-ttu-id="31899-127">Varsayılan değişmez değer ifadeleri</span><span class="sxs-lookup"><span data-stu-id="31899-127">Default literal expressions</span></span>

<span data-ttu-id="31899-128">Varsayılan değişmez ifadelerinde bir geliştirme için varsayılan değer ifadeleri toplama var.</span><span class="sxs-lookup"><span data-stu-id="31899-128">Default literal expressions are an enhancement to default value expressions.</span></span>
<span data-ttu-id="31899-129">Bu ifadeler, varsayılan değer için bir değişken başlatın.</span><span class="sxs-lookup"><span data-stu-id="31899-129">These expressions initialize a variable to the default value.</span></span> <span data-ttu-id="31899-130">Daha önce burada yazmalısınız:</span><span class="sxs-lookup"><span data-stu-id="31899-130">Where you previously would write:</span></span>

```csharp
Func<string, bool> whereClause = default(Func<string, bool>);
```

<span data-ttu-id="31899-131">Sağ taraftaki başlatma türü artık atlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="31899-131">You can now omit the type on the right-hand side of the initialization:</span></span>

```csharp
Func<string, bool> whereClause = default;
```

<span data-ttu-id="31899-132">İçinde bu geliştirme hakkında daha fazla bilgi C# Programming Guide makale [varsayılan değer ifadeleri](../programming-guide/statements-expressions-operators/default-value-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="31899-132">You can learn more about this enhancement in the C# Programming Guide article on [default value expressions](../programming-guide/statements-expressions-operators/default-value-expressions.md).</span></span>

<span data-ttu-id="31899-133">Bu geliştirme ayrıca bazı ayrıştırma kurallarını değiştirir [default anahtar sözcüğü](../language-reference/keywords/default.md).</span><span class="sxs-lookup"><span data-stu-id="31899-133">This enhancement also changes some of the parsing rules for the [default keyword](../language-reference/keywords/default.md).</span></span>

## <a name="inferred-tuple-element-names"></a><span data-ttu-id="31899-134">Çıkarsanan demet öğesi adları</span><span class="sxs-lookup"><span data-stu-id="31899-134">Inferred tuple element names</span></span>

<span data-ttu-id="31899-135">Bu özellik de kullanıma sunulan diziler özellik için küçük bir geliştirmedir C# 7.0.</span><span class="sxs-lookup"><span data-stu-id="31899-135">This feature is a small enhancement to the tuples feature introduced in C# 7.0.</span></span> <span data-ttu-id="31899-136">Bir demet başlattığınızda birden çok kez dizi öğeleri için istediğiniz adları aynı atama için sağ tarafında kullanılan değişkenleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="31899-136">Many times when you initialize a tuple, the variables used for the right side of the assignment are the same as the names you'd like for the tuple elements:</span></span>

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count: count, label: label);
```

<span data-ttu-id="31899-137">Değişkenlerden düzeninde başlatmak için kullanılan tanımlama grubu öğelerinin adlarını çıkarılan C# 7.1:</span><span class="sxs-lookup"><span data-stu-id="31899-137">The names of tuple elements can be inferred from the variables used to initialize the tuple in C# 7.1:</span></span>

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count, label); // element names are "count" and "label"
```

<span data-ttu-id="31899-138">' Deki bu özellik hakkında daha fazla bilgi [diziler](../tuples.md) makalesi.</span><span class="sxs-lookup"><span data-stu-id="31899-138">You can learn more about this feature in the [Tuples](../tuples.md) article.</span></span>

## <a name="pattern-matching-on-generic-type-parameters"></a><span data-ttu-id="31899-139">Genel tür parametrelerinde desen</span><span class="sxs-lookup"><span data-stu-id="31899-139">Pattern matching on generic type parameters</span></span>

<span data-ttu-id="31899-140">İle başlayarak C# 7.1, desen ifadesi `is` ve `switch` türü deseni bir genel tür parametre türüne sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="31899-140">Beginning with C# 7.1, the pattern expression for `is` and the `switch` type pattern may have the type of a generic type parameter.</span></span> <span data-ttu-id="31899-141">Bu olabilir ya da denetimi türlerinden en yararlı olabilir `struct` veya `class` türleri ve kutulama önlemek istiyor.</span><span class="sxs-lookup"><span data-stu-id="31899-141">This can be most useful when checking types that may be either `struct` or `class` types, and you want to avoid boxing.</span></span>

## <a name="reference-assembly-generation"></a><span data-ttu-id="31899-142">Başvuru derleme oluşturma</span><span class="sxs-lookup"><span data-stu-id="31899-142">Reference assembly generation</span></span>

<span data-ttu-id="31899-143">Oluşturan iki yeni derleyici seçenek *yalnızca başvuru derlemeleri*: [/refout](../language-reference/compiler-options/refout-compiler-option.md) ve [/refonly](../language-reference/compiler-options/refonly-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="31899-143">There are two new compiler options that generate *reference-only assemblies*: [/refout](../language-reference/compiler-options/refout-compiler-option.md) and [/refonly](../language-reference/compiler-options/refonly-compiler-option.md).</span></span>
<span data-ttu-id="31899-144">Bağlantısı verilen makalelerden Bu seçenekler ve daha ayrıntılı başvuru bütünleştirilmiş kodları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="31899-144">The linked articles explain these options and reference assemblies in more detail.</span></span>
