---
title: C# 7.1 yenilikler nelerdir?
description: "C# 7.1 içindeki yeni özelliklere genel bakış."
keywords: "C# dil tasarımında, 7.1, Visual Studio 2017,"
author: billwagner
ms.author: wiwagn
ms.date: 08/16/2017
ms.topic: article
ms.prod: .net
ms.devlang: devlang-csharp
ms.openlocfilehash: 02f1f8fc8f0a3221e00e2a3c43ce06423ca43672
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="whats-new-in-c-71"></a><span data-ttu-id="74d32-104">C# 7.1 yenilikler nelerdir?</span><span class="sxs-lookup"><span data-stu-id="74d32-104">What's new in C# 7.1</span></span>

<span data-ttu-id="74d32-105">C# 7.1, C# dili için ilk noktası sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="74d32-105">C# 7.1 is the first point release to the C# language.</span></span> <span data-ttu-id="74d32-106">Artan sürüm tempoyla dil için işaretler.</span><span class="sxs-lookup"><span data-stu-id="74d32-106">It marks an increased release cadence for the language.</span></span> <span data-ttu-id="74d32-107">Her yeni özellik hazır olduğunda, yeni özelliklerin daha erken, ideal olarak kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="74d32-107">You can use the new features sooner, ideally when each new feature is ready.</span></span> <span data-ttu-id="74d32-108">C# 7.1 derleyici dil belirtilen sürümüyle eşleşecek şekilde yapılandırma olanağını ekler.</span><span class="sxs-lookup"><span data-stu-id="74d32-108">C# 7.1 adds the ability to configure the compiler to match a specified version of the language.</span></span> <span data-ttu-id="74d32-109">Bu, dil sürümlerini yükseltmek için karar araçları yükseltmeye karar ayırmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="74d32-109">That enables you to separate the decision to upgrade tools from the decision to upgrade language versions.</span></span>

<span data-ttu-id="74d32-110">C# 7.1 ekler [dil sürümü seçimi](#language-version-selection) yapılandırma öğesi, üç yeni dil özellikleri ve yeni derleyici davranışı.</span><span class="sxs-lookup"><span data-stu-id="74d32-110">C# 7.1 adds the [language version selection](#language-version-selection) configuration element, three new language features and new compiler behavior.</span></span>

<span data-ttu-id="74d32-111">Bu sürümdeki yeni diz özellikleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="74d32-111">The new language features in this release are:</span></span>

* [<span data-ttu-id="74d32-112">`async``Main` yöntemi</span><span class="sxs-lookup"><span data-stu-id="74d32-112">`async` `Main` method</span></span>](#async-main)
  - <span data-ttu-id="74d32-113">Bir uygulama için giriş noktası olabilir `async` değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="74d32-113">The entry point for an application can have the `async` modifier.</span></span>
* [<span data-ttu-id="74d32-114">`default`Sabit ifadeleri</span><span class="sxs-lookup"><span data-stu-id="74d32-114">`default` literal expressions</span></span>](#default-literal-expressions)
  - <span data-ttu-id="74d32-115">Hedef türü çıkarsanabileceği olduğunda, varsayılan değeri ifadelerinde varsayılan değişmez değer ifadeleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="74d32-115">You can use default literal expressions in default value expressions when the target type can be inferred.</span></span>
* [<span data-ttu-id="74d32-116">Çıkarsanan tanımlama grubu öğe adları</span><span class="sxs-lookup"><span data-stu-id="74d32-116">Inferred tuple element names</span></span>](#inferred-tuple-element-names)
  - <span data-ttu-id="74d32-117">Başlığın öğeleri adlarını, çoğu durumda tanımlama grubu başlatılmasından çıkarsanabileceği.</span><span class="sxs-lookup"><span data-stu-id="74d32-117">The names of tuple elements can be inferred from tuple initialization in many cases.</span></span>

<span data-ttu-id="74d32-118">Son olarak, derleyici iki seçenek vardır `/refout` ve `/refonly` denetleyen [başvuru derleme oluşturma](#reference-assembly-generation).</span><span class="sxs-lookup"><span data-stu-id="74d32-118">Finally, the compiler has two options `/refout` and `/refonly` that control [reference assembly generation](#reference-assembly-generation).</span></span>

## <a name="language-version-selection"></a><span data-ttu-id="74d32-119">Dil sürümü seçimi</span><span class="sxs-lookup"><span data-stu-id="74d32-119">Language version selection</span></span>

<span data-ttu-id="74d32-120">C# Derleyici C# Visual Studio 2017 sürüm 15.3 veya .NET Core SDK 2.0 ile başlayan 7.1 destekler.</span><span class="sxs-lookup"><span data-stu-id="74d32-120">The C# compiler supports C# 7.1 starting with Visual Studio 2017 version 15.3, or the .NET Core SDK 2.0.</span></span> <span data-ttu-id="74d32-121">Ancak, 7.1 özellikleri varsayılan olarak kapalıdır.</span><span class="sxs-lookup"><span data-stu-id="74d32-121">However, the 7.1 features are turned off by default.</span></span> <span data-ttu-id="74d32-122">7.1 özellikleri etkinleştirmek için projeniz için dil sürümü ayarı değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="74d32-122">To enable the 7.1 features, you need to change the language version setting for your project.</span></span>

<span data-ttu-id="74d32-123">Visual Studio'da, Çözüm Gezgini'nde proje düğümüne sağ tıklayın ve seçin **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="74d32-123">In Visual Studio, right-click on the project node in Solution Explorer and select **Properties**.</span></span> <span data-ttu-id="74d32-124">Seçin **yapı** sekmesinde ve seçin **Gelişmiş** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="74d32-124">Select the **Build** tab and select the **Advanced** button.</span></span> <span data-ttu-id="74d32-125">Açılır listede seçin **C# son alt sürüm (son)**, veya belirli bir sürümünü **C# 7.1** görüntü aşağıda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="74d32-125">In the dropdown, select **C# latest minor version (latest)**, or the specific version **C# 7.1** as shown in the image following.</span></span> <span data-ttu-id="74d32-126">`latest` Değeri, geçerli makineye en son alt sürüm kullanmak istediğiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="74d32-126">The `latest` value means you want to use the latest minor version on the current machine.</span></span> <span data-ttu-id="74d32-127">`C# 7.1` Yeni ikincil sürümleri bile sunulduktan sonra C# 7.1, kullanmak istediğiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="74d32-127">The `C# 7.1` means that you want to use C# 7.1, even after newer minor versions are released.</span></span>

![Dil sürümünü ayarlama](./media/csharp-7-1/advanced-build-settings.png)

<span data-ttu-id="74d32-129">Alternatif olarak, "csproj" dosyasını düzenleyin ve ekleyebilir veya aşağıdaki satırları değiştirin:</span><span class="sxs-lookup"><span data-stu-id="74d32-129">Alternatively, you can edit the "csproj" file and add or modify the following lines:</span></span>

```xml
<PropertyGroup>
  <LangVersion>latest</LangVersion>
</PropertyGroup>
```

> [!NOTE]
> <span data-ttu-id="74d32-130">Csproj dosyalarınızı güncelleştirmek için Visual Studio IDE kullanırsanız, IDE her yapı yapılandırması için ayrı düğüm oluşturur.</span><span class="sxs-lookup"><span data-stu-id="74d32-130">If you use the Visual Studio IDE to update your csproj files, the IDE creates separate nodes for each build configuration.</span></span> <span data-ttu-id="74d32-131">Genellikle değerini aynı tüm yapı yapılandırmalarında ayarlamanız, ancak her yapı yapılandırması için açıkça ayarlamak veya bu ayarı değiştirdikten sonra "Tüm yapılandırmaları" seçmek gerekir.</span><span class="sxs-lookup"><span data-stu-id="74d32-131">You'll typically set the value the same in all build configurations, but you need to set it explicitly for each build configuration, or select "All Configurations" when you modify this setting.</span></span> <span data-ttu-id="74d32-132">Aşağıdaki csproj dosyanızda görürsünüz:</span><span class="sxs-lookup"><span data-stu-id="74d32-132">You'll see the following in your csproj file:</span></span>

```xml
<PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|AnyCPU'">
  <LangVersion>latest</LangVersion>
</PropertyGroup>

<PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Debug|AnyCPU'">
  <LangVersion>latest</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="74d32-133">İçin geçerli ayarları `LangVersion` öğesidir:</span><span class="sxs-lookup"><span data-stu-id="74d32-133">Valid settings for the `LangVersion` element are:</span></span>

* `ISO-1`
* `ISO-2`
* `3`
* `4`
* `5`
* `6`
* `7`
* `7.1`
* `default`
* `latest`

<span data-ttu-id="74d32-134">Özel dizeler `default` ve `latest` yapı, sırasıyla makinede en son birincil ve ikincil dil sürümleri çözmek.</span><span class="sxs-lookup"><span data-stu-id="74d32-134">The special strings `default` and `latest` resolve to the latest major and minor language versions installed on the build machine, respectively.</span></span>

<span data-ttu-id="74d32-135">Bu ayar, bir projede yeni dil özellikleri içerecek şekilde seçme gelen geliştirme ortamınızı yeni sürümlerini SDK ve araçlarını yükleme ayrıştırır.</span><span class="sxs-lookup"><span data-stu-id="74d32-135">This setting decouples installing new versions of the SDK and tools in your development environment from choosing to incorporate new language features in a project.</span></span> <span data-ttu-id="74d32-136">En son SDK'yı ve araçları, yapı makinenizde yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="74d32-136">You can install the latest SDK and tools on your build machine.</span></span> <span data-ttu-id="74d32-137">Her proje, derleme için belirli bir dil sürümünü kullanacak şekilde yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="74d32-137">Each project can be configured to use a specific version of the language for its build.</span></span>

## <a name="async-main"></a><span data-ttu-id="74d32-138">Zaman uyumsuz ana</span><span class="sxs-lookup"><span data-stu-id="74d32-138">Async main</span></span>

<span data-ttu-id="74d32-139">Bir *zaman uyumsuz ana* yöntemi kullanmanıza olanak sağlayan `await` içinde `Main` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="74d32-139">An *async main* method enables you to use `await` in your `Main` method.</span></span>
<span data-ttu-id="74d32-140">Daha önce yazma gerekir:</span><span class="sxs-lookup"><span data-stu-id="74d32-140">Previously you would need to write:</span></span>

```csharp
static int Main()
{
    return DoAsyncWork().GetAwaiter().GetResult();
}
```

<span data-ttu-id="74d32-141">Şimdi yazabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="74d32-141">You can now write:</span></span>

```csharp
static async Task<int> Main()
{
    // This could also be replaced with the body
    // DoAsyncWork, including its await expressions:
    return await DoAsyncWork();
}
```

<span data-ttu-id="74d32-142">Programınızı bir çıkış kodu varsa döndürmez, bildirebilirsiniz bir `Main` döndüren yöntemi bir <xref:System.Threading.Tasks.Task>:</span><span class="sxs-lookup"><span data-stu-id="74d32-142">If your program doesn't return an exit code, you can declare a `Main` method that returns a <xref:System.Threading.Tasks.Task>:</span></span>

```csharp
static async Task Main()
{
    await SomeAsyncMethod();
}
```

<span data-ttu-id="74d32-143">Daha fazla bilgiyi ayrıntılar hakkında [zaman uyumsuz ana](../programming-guide/main-and-command-args/index.md) konusu programlama kılavuzu.</span><span class="sxs-lookup"><span data-stu-id="74d32-143">You can read more about the details in the [async main](../programming-guide/main-and-command-args/index.md) topic in the programming guide.</span></span>

## <a name="default-literal-expressions"></a><span data-ttu-id="74d32-144">Varsayılan sabit ifadeleri</span><span class="sxs-lookup"><span data-stu-id="74d32-144">Default literal expressions</span></span>

<span data-ttu-id="74d32-145">Varsayılan değişmez değer varsayılan değer ifadeleri yüklenene ifadelerini.</span><span class="sxs-lookup"><span data-stu-id="74d32-145">Default literal expressions are an enhancement to default value expressions.</span></span>
<span data-ttu-id="74d32-146">Bu ifade bir değişken varsayılan değere başlatır.</span><span class="sxs-lookup"><span data-stu-id="74d32-146">These expressions initialize a variable to the default value.</span></span> <span data-ttu-id="74d32-147">Daha önce burada yazarsınız:</span><span class="sxs-lookup"><span data-stu-id="74d32-147">Where you previously would write:</span></span>

```csharp
Func<string, bool> whereClause = default(Func<string, bool>);
```

<span data-ttu-id="74d32-148">Sağ taraftaki başlatma türü artık atlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="74d32-148">You can now omit the type on the right-hand side of the initialization:</span></span>

```csharp
Func<string, bool> whereClause = default;
```

<span data-ttu-id="74d32-149">Üzerinde C# programlama kılavuzu konusundaki bu geliştirme hakkında daha fazla bilgiyi [varsayılan değeri ifadeleri](../programming-guide/statements-expressions-operators/default-value-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="74d32-149">You can learn more about this enhancement in the C# Programming Guide topic on [default value expressions](../programming-guide/statements-expressions-operators/default-value-expressions.md).</span></span>

<span data-ttu-id="74d32-150">Bu geliştirme, ayrıca bazı ayrıştırma kurallarının değiştirir [default anahtar sözcüğü](../language-reference/keywords/default.md).</span><span class="sxs-lookup"><span data-stu-id="74d32-150">This enhancement also changes some of the parsing rules for the [default keyword](../language-reference/keywords/default.md).</span></span>

## <a name="inferred-tuple-element-names"></a><span data-ttu-id="74d32-151">Çıkarsanan tanımlama grubu öğe adları</span><span class="sxs-lookup"><span data-stu-id="74d32-151">Inferred tuple element names</span></span>

<span data-ttu-id="74d32-152">Bu özellik, C# 7. 0'sunulan diziler özellikle küçük bir yeniliktir.</span><span class="sxs-lookup"><span data-stu-id="74d32-152">This feature is a small enhancement to the tuples feature introduced in C# 7.0.</span></span> <span data-ttu-id="74d32-153">Bir tanımlama grubu başlattığınızda birçok kez atama için sağ tarafında kullanılan değişkenler tanımlama grubu öğeleri için istediğiniz adları aynıdır:</span><span class="sxs-lookup"><span data-stu-id="74d32-153">Many times when you initialize a tuple, the variables used for the right side of the assignment are the same as the names you'd like for the tuple elements:</span></span>

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count: count, label: label);
```

<span data-ttu-id="74d32-154">Başlığın öğeleri adları C# 7.1 düzeninde başlatmak için kullanılan değişkenlerden çıkarsanabileceği:</span><span class="sxs-lookup"><span data-stu-id="74d32-154">The names of tuple elements can be inferred from the variables used to initialize the tuple in C# 7.1:</span></span>

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count, label); // element names are "count" and "label"
```

<span data-ttu-id="74d32-155">Bu özellik hakkında daha fazla bilgiyi [diziler](../tuples.md) konu.</span><span class="sxs-lookup"><span data-stu-id="74d32-155">You can learn more about this feature in the [Tuples](../tuples.md) topic.</span></span>

## <a name="reference-assembly-generation"></a><span data-ttu-id="74d32-156">Başvuru derleme oluşturma</span><span class="sxs-lookup"><span data-stu-id="74d32-156">Reference assembly generation</span></span>

<span data-ttu-id="74d32-157">Üreten iki yeni derleyici seçenekleri vardır *yalnızca başvuru derlemeleri*: [/refout](../language-reference/compiler-options/refout-compiler-option.md) ve [/refonly](../language-reference/compiler-options/refonly-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="74d32-157">There are two new compiler options that generate *reference-only assemblies*: [/refout](../language-reference/compiler-options/refout-compiler-option.md) and [/refonly](../language-reference/compiler-options/refonly-compiler-option.md).</span></span>
<span data-ttu-id="74d32-158">Bağlantılı konulardan Bu seçenekler ve daha ayrıntılı başvuru derlemeleri açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="74d32-158">The linked topics explain these options and reference assemblies in more detail.</span></span>
