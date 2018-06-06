---
title: C# 7.1 yenilikler nelerdir?
description: C# 7.1 içindeki yeni özelliklere genel bakış.
ms.date: 08/16/2017
ms.openlocfilehash: 565db102284424f9d8f6fa04ec9c74b52c9da0e6
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34728660"
---
# <a name="whats-new-in-c-71"></a><span data-ttu-id="5b65e-103">C# 7.1 yenilikler nelerdir?</span><span class="sxs-lookup"><span data-stu-id="5b65e-103">What's new in C# 7.1</span></span>

<span data-ttu-id="5b65e-104">C# 7.1, C# dili için ilk noktası sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="5b65e-104">C# 7.1 is the first point release to the C# language.</span></span> <span data-ttu-id="5b65e-105">Artan sürüm tempoyla dil için işaretler.</span><span class="sxs-lookup"><span data-stu-id="5b65e-105">It marks an increased release cadence for the language.</span></span> <span data-ttu-id="5b65e-106">Her yeni özellik hazır olduğunda, yeni özelliklerin daha erken, ideal olarak kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5b65e-106">You can use the new features sooner, ideally when each new feature is ready.</span></span> <span data-ttu-id="5b65e-107">C# 7.1 derleyici dil belirtilen sürümüyle eşleşecek şekilde yapılandırma olanağını ekler.</span><span class="sxs-lookup"><span data-stu-id="5b65e-107">C# 7.1 adds the ability to configure the compiler to match a specified version of the language.</span></span> <span data-ttu-id="5b65e-108">Bu, dil sürümlerini yükseltmek için karar araçları yükseltmeye karar ayırmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="5b65e-108">That enables you to separate the decision to upgrade tools from the decision to upgrade language versions.</span></span>

<span data-ttu-id="5b65e-109">C# 7.1 ekler [dil sürümü seçimi](../language-reference/configure-language-version.md) yapılandırma öğesi, üç yeni dil özellikleri ve yeni derleyici davranışı.</span><span class="sxs-lookup"><span data-stu-id="5b65e-109">C# 7.1 adds the [language version selection](../language-reference/configure-language-version.md) configuration element, three new language features and new compiler behavior.</span></span>

<span data-ttu-id="5b65e-110">Bu sürümdeki yeni diz özellikleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="5b65e-110">The new language features in this release are:</span></span>

* [<span data-ttu-id="5b65e-111">`async` `Main` Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5b65e-111">`async` `Main` method</span></span>](#async-main)
  - <span data-ttu-id="5b65e-112">Bir uygulama için giriş noktası olabilir `async` değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="5b65e-112">The entry point for an application can have the `async` modifier.</span></span>
* [<span data-ttu-id="5b65e-113">`default` Sabit ifadeleri</span><span class="sxs-lookup"><span data-stu-id="5b65e-113">`default` literal expressions</span></span>](#default-literal-expressions)
  - <span data-ttu-id="5b65e-114">Hedef türü çıkarsanabileceği olduğunda, varsayılan değeri ifadelerinde varsayılan değişmez değer ifadeleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5b65e-114">You can use default literal expressions in default value expressions when the target type can be inferred.</span></span>
* [<span data-ttu-id="5b65e-115">Çıkarsanan tanımlama grubu öğe adları</span><span class="sxs-lookup"><span data-stu-id="5b65e-115">Inferred tuple element names</span></span>](#inferred-tuple-element-names)
  - <span data-ttu-id="5b65e-116">Başlığın öğeleri adlarını, çoğu durumda tanımlama grubu başlatılmasından çıkarsanabileceği.</span><span class="sxs-lookup"><span data-stu-id="5b65e-116">The names of tuple elements can be inferred from tuple initialization in many cases.</span></span>

<span data-ttu-id="5b65e-117">Son olarak, derleyici iki seçenek vardır `/refout` ve `/refonly` denetleyen [başvuru derleme oluşturma](#reference-assembly-generation).</span><span class="sxs-lookup"><span data-stu-id="5b65e-117">Finally, the compiler has two options `/refout` and `/refonly` that control [reference assembly generation](#reference-assembly-generation).</span></span>

<span data-ttu-id="5b65e-118">Noktası sürümündeki yeni özellikleri kullanmak için yapmanız [derleyici dil sürümünü yapılandırmanız](../language-reference/configure-language-version.md) ve sürümü seçin.</span><span class="sxs-lookup"><span data-stu-id="5b65e-118">To use the latest features in a point release, you need to [configure the compiler language version](../language-reference/configure-language-version.md) and select the version.</span></span>

## <a name="async-main"></a><span data-ttu-id="5b65e-119">Zaman uyumsuz ana</span><span class="sxs-lookup"><span data-stu-id="5b65e-119">Async main</span></span>

<span data-ttu-id="5b65e-120">Bir *zaman uyumsuz ana* yöntemi kullanmanıza olanak sağlayan `await` içinde `Main` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5b65e-120">An *async main* method enables you to use `await` in your `Main` method.</span></span>
<span data-ttu-id="5b65e-121">Daha önce yazma gerekir:</span><span class="sxs-lookup"><span data-stu-id="5b65e-121">Previously you would need to write:</span></span>

```csharp
static int Main()
{
    return DoAsyncWork().GetAwaiter().GetResult();
}
```

<span data-ttu-id="5b65e-122">Şimdi yazabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5b65e-122">You can now write:</span></span>

```csharp
static async Task<int> Main()
{
    // This could also be replaced with the body
    // DoAsyncWork, including its await expressions:
    return await DoAsyncWork();
}
```

<span data-ttu-id="5b65e-123">Programınızı bir çıkış kodu varsa döndürmez, bildirebilirsiniz bir `Main` döndüren yöntemi bir <xref:System.Threading.Tasks.Task>:</span><span class="sxs-lookup"><span data-stu-id="5b65e-123">If your program doesn't return an exit code, you can declare a `Main` method that returns a <xref:System.Threading.Tasks.Task>:</span></span>

```csharp
static async Task Main()
{
    await SomeAsyncMethod();
}
```

<span data-ttu-id="5b65e-124">Daha fazla bilgiyi ayrıntılar hakkında [zaman uyumsuz ana](../programming-guide/main-and-command-args/index.md) konusu programlama kılavuzu.</span><span class="sxs-lookup"><span data-stu-id="5b65e-124">You can read more about the details in the [async main](../programming-guide/main-and-command-args/index.md) topic in the programming guide.</span></span>

## <a name="default-literal-expressions"></a><span data-ttu-id="5b65e-125">Varsayılan sabit ifadeleri</span><span class="sxs-lookup"><span data-stu-id="5b65e-125">Default literal expressions</span></span>

<span data-ttu-id="5b65e-126">Varsayılan değişmez değer varsayılan değer ifadeleri yüklenene ifadelerini.</span><span class="sxs-lookup"><span data-stu-id="5b65e-126">Default literal expressions are an enhancement to default value expressions.</span></span>
<span data-ttu-id="5b65e-127">Bu ifade bir değişken varsayılan değere başlatır.</span><span class="sxs-lookup"><span data-stu-id="5b65e-127">These expressions initialize a variable to the default value.</span></span> <span data-ttu-id="5b65e-128">Daha önce burada yazarsınız:</span><span class="sxs-lookup"><span data-stu-id="5b65e-128">Where you previously would write:</span></span>

```csharp
Func<string, bool> whereClause = default(Func<string, bool>);
```

<span data-ttu-id="5b65e-129">Sağ taraftaki başlatma türü artık atlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5b65e-129">You can now omit the type on the right-hand side of the initialization:</span></span>

```csharp
Func<string, bool> whereClause = default;
```

<span data-ttu-id="5b65e-130">Üzerinde C# programlama kılavuzu konusundaki bu geliştirme hakkında daha fazla bilgiyi [varsayılan değeri ifadeleri](../programming-guide/statements-expressions-operators/default-value-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="5b65e-130">You can learn more about this enhancement in the C# Programming Guide topic on [default value expressions](../programming-guide/statements-expressions-operators/default-value-expressions.md).</span></span>

<span data-ttu-id="5b65e-131">Bu geliştirme, ayrıca bazı ayrıştırma kurallarının değiştirir [default anahtar sözcüğü](../language-reference/keywords/default.md).</span><span class="sxs-lookup"><span data-stu-id="5b65e-131">This enhancement also changes some of the parsing rules for the [default keyword](../language-reference/keywords/default.md).</span></span>

## <a name="inferred-tuple-element-names"></a><span data-ttu-id="5b65e-132">Çıkarsanan tanımlama grubu öğe adları</span><span class="sxs-lookup"><span data-stu-id="5b65e-132">Inferred tuple element names</span></span>

<span data-ttu-id="5b65e-133">Bu özellik, C# 7. 0'sunulan diziler özellikle küçük bir yeniliktir.</span><span class="sxs-lookup"><span data-stu-id="5b65e-133">This feature is a small enhancement to the tuples feature introduced in C# 7.0.</span></span> <span data-ttu-id="5b65e-134">Bir tanımlama grubu başlattığınızda birçok kez atama için sağ tarafında kullanılan değişkenler tanımlama grubu öğeleri için istediğiniz adları aynıdır:</span><span class="sxs-lookup"><span data-stu-id="5b65e-134">Many times when you initialize a tuple, the variables used for the right side of the assignment are the same as the names you'd like for the tuple elements:</span></span>

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count: count, label: label);
```

<span data-ttu-id="5b65e-135">Başlığın öğeleri adları C# 7.1 düzeninde başlatmak için kullanılan değişkenlerden çıkarsanabileceği:</span><span class="sxs-lookup"><span data-stu-id="5b65e-135">The names of tuple elements can be inferred from the variables used to initialize the tuple in C# 7.1:</span></span>

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count, label); // element names are "count" and "label"
```

<span data-ttu-id="5b65e-136">Bu özellik hakkında daha fazla bilgiyi [diziler](../tuples.md) konu.</span><span class="sxs-lookup"><span data-stu-id="5b65e-136">You can learn more about this feature in the [Tuples](../tuples.md) topic.</span></span>

## <a name="reference-assembly-generation"></a><span data-ttu-id="5b65e-137">Başvuru derleme oluşturma</span><span class="sxs-lookup"><span data-stu-id="5b65e-137">Reference assembly generation</span></span>

<span data-ttu-id="5b65e-138">Üreten iki yeni derleyici seçenekleri vardır *yalnızca başvuru derlemeleri*: [/refout](../language-reference/compiler-options/refout-compiler-option.md) ve [/refonly](../language-reference/compiler-options/refonly-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="5b65e-138">There are two new compiler options that generate *reference-only assemblies*: [/refout](../language-reference/compiler-options/refout-compiler-option.md) and [/refonly](../language-reference/compiler-options/refonly-compiler-option.md).</span></span>
<span data-ttu-id="5b65e-139">Bağlantılı konulardan Bu seçenekler ve daha ayrıntılı başvuru derlemeleri açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="5b65e-139">The linked topics explain these options and reference assemblies in more detail.</span></span>
