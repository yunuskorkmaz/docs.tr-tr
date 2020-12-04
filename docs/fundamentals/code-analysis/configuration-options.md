---
title: Kod analizi kurallarını yapılandırma
description: Bir çözümleyici yapılandırma dosyasında kod analizi kurallarını yapılandırmayı öğrenin.
ms.date: 09/24/2020
ms.topic: conceptual
no-loc:
- EditorConfig
ms.openlocfilehash: af2ebb74786f0ae884ffee4636765cae43fcb23f
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2020
ms.locfileid: "96589337"
---
# <a name="configuration-options-for-code-analysis"></a><span data-ttu-id="8bcfe-103">Kod analizi için yapılandırma seçenekleri</span><span class="sxs-lookup"><span data-stu-id="8bcfe-103">Configuration options for code analysis</span></span>

<span data-ttu-id="8bcfe-104">Kod analizi kuralları çeşitli yapılandırma seçeneklerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="8bcfe-104">Code analysis rules have various configuration options.</span></span> <span data-ttu-id="8bcfe-105">Bu seçenekler, bir [çözümleyici yapılandırma dosyasında](configuration-files.md) sözdizimi kullanılarak anahtar-değer çiftleri olarak belirtilir `<option key> = <option value>` .</span><span class="sxs-lookup"><span data-stu-id="8bcfe-105">These options are specified as key-value pairs in an [analyzer configuration file](configuration-files.md) using the syntax `<option key> = <option value>`.</span></span>

<span data-ttu-id="8bcfe-106">Yapılandıracağımız en yaygın seçenek, bir kuralın önem derecesine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="8bcfe-106">The most common option you'll configure is a rule's severity.</span></span> <span data-ttu-id="8bcfe-107">[Kod kalitesi kuralları](quality-rules/index.md) ve [kod stili kuralları](style-rules/index.md)da dahil olmak üzere tüm çözümleyici kuralları için önem derecesini yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8bcfe-107">You can configure severity level for all analyzer rules, including [code quality rules](quality-rules/index.md) and [code style rules](style-rules/index.md).</span></span>

<span data-ttu-id="8bcfe-108">Kural davranışını özelleştirmek için ek seçenekler de yapılandırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8bcfe-108">You can also configure additional options to customize rule behavior:</span></span>

- <span data-ttu-id="8bcfe-109">Kod kalitesi kuralları, davranışı yapılandırmak için [ek seçeneklere](code-quality-rule-options.md) sahiptir; Örneğin, bir kuralın hangi yöntem adına uygulanacağını.</span><span class="sxs-lookup"><span data-stu-id="8bcfe-109">Code quality rules have [additional options](code-quality-rule-options.md) to configure behavior, such as which method names a rule should apply to.</span></span>
- <span data-ttu-id="8bcfe-110">Kod stili kuralları [özel kod stili seçeneklerine](code-style-rule-options.md)sahiptir.</span><span class="sxs-lookup"><span data-stu-id="8bcfe-110">Code style rules have [custom code style options](code-style-rule-options.md).</span></span>
- <span data-ttu-id="8bcfe-111">Üçüncü taraf çözümleyici kuralları, özel anahtar adları ve değer biçimleri ile kendi yapılandırma seçeneklerini tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="8bcfe-111">Third party analyzer rules can define their own configuration options, with custom key names and value formats.</span></span>

<span data-ttu-id="8bcfe-112">Bir [çözümleyici yapılandırma dosyasında](configuration-files.md) belirli bir kuralın önem derecesini yapılandırmak için sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="8bcfe-112">The syntax for configuring a specific rule's severity in an [analyzer configuration file](configuration-files.md) is as follows:</span></span>

```ini
dotnet_diagnostic.<rule ID>.severity = <severity>
```

## <a name="general-options"></a><span data-ttu-id="8bcfe-113">Genel seçenekler</span><span class="sxs-lookup"><span data-stu-id="8bcfe-113">General options</span></span>

<span data-ttu-id="8bcfe-114">Bu seçenekler bir bütün olarak kod analizi için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="8bcfe-114">These options apply to code analysis as a whole.</span></span> <span data-ttu-id="8bcfe-115">Yalnızca tek bir kurala veya kural kümesine uygulanamaz.</span><span class="sxs-lookup"><span data-stu-id="8bcfe-115">They cannot be applied only to a single rule or set of rules.</span></span>

### <a name="exclude-generated-code"></a><span data-ttu-id="8bcfe-116">Üretilen kodu hariç tut</span><span class="sxs-lookup"><span data-stu-id="8bcfe-116">Exclude generated code</span></span>

<span data-ttu-id="8bcfe-117">`generated_code = true | false` [Yapılandırma dosyanıza](configuration-files.md)bir giriş ekleyerek, oluşturulan kod olarak değerlendirilecek ek dosya ve klasörler yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8bcfe-117">You can configure additional files and folders to be treated as generated code by adding a `generated_code = true | false` entry to your [configuration file](configuration-files.md).</span></span> <span data-ttu-id="8bcfe-118">.NET Code Analyzer uyarıları, tasarımcı tarafından oluşturulan dosyalar gibi oluşturulan kod dosyalarında (kullanıcıların herhangi bir ihlali onarmak için düzenleyemeyen) yararlı değildir.</span><span class="sxs-lookup"><span data-stu-id="8bcfe-118">.NET code analyzer warnings aren't useful on generated code files, such as designer-generated files, which users can't edit to fix any violations.</span></span> <span data-ttu-id="8bcfe-119">Çoğu durumda, kod Çözümleyicileri oluşturulan kod dosyalarını atlar ve bu dosyalarda ihlal bildirmez.</span><span class="sxs-lookup"><span data-stu-id="8bcfe-119">In most cases, code analyzers skip generated code files and don't report violations on these files.</span></span>

<span data-ttu-id="8bcfe-120">Varsayılan olarak, belirli dosya uzantılarına sahip dosyalar veya otomatik olarak oluşturulan dosya üstbilgileri oluşturulan kod dosyaları olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="8bcfe-120">By default, files with certain file extensions or auto-generated file headers are treated as generated code files.</span></span> <span data-ttu-id="8bcfe-121">Örneğin, veya ile biten bir dosya adı `.designer.cs` `.generated.cs` üretilen kod olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="8bcfe-121">For example, a file name ending with `.designer.cs` or `.generated.cs` is considered generated code.</span></span> <span data-ttu-id="8bcfe-122">Bu yapılandırma seçeneği, ek adlandırma desenleri belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="8bcfe-122">This configuration option lets you specify additional naming patterns.</span></span>

<span data-ttu-id="8bcfe-123">Örneğin, adı biten tüm dosyaları `.MyGenerated.cs` oluşturulan kodla işlemek için aşağıdaki girişi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="8bcfe-123">For example, to treat all files whose name ends with `.MyGenerated.cs` as generated code, add the following entry:</span></span>

```ini
[*.MyGenerated.cs]
generated_code = true
```

## <a name="rule-specific-options"></a><span data-ttu-id="8bcfe-124">Kurala özgü seçenekler</span><span class="sxs-lookup"><span data-stu-id="8bcfe-124">Rule-specific options</span></span>

<span data-ttu-id="8bcfe-125">Kurala özgü seçenekler tek bir kurala, bir dizi kurala veya tüm kurallara uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="8bcfe-125">Rule-specific options can be applied to a single rule, a set of rules, or all rules.</span></span> <span data-ttu-id="8bcfe-126">Kurala özgü seçenekler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="8bcfe-126">The rule-specific options include:</span></span>

- [<span data-ttu-id="8bcfe-127">Kural önem derecesi düzeyi</span><span class="sxs-lookup"><span data-stu-id="8bcfe-127">Rule severity level</span></span>](#severity-level)
- [<span data-ttu-id="8bcfe-128">*Kod kalitesi* kurallarına özgü seçenekler</span><span class="sxs-lookup"><span data-stu-id="8bcfe-128">Options specific to *code-quality* rules</span></span>](code-quality-rule-options.md)

### <a name="severity-level"></a><span data-ttu-id="8bcfe-129">Önem derecesi</span><span class="sxs-lookup"><span data-stu-id="8bcfe-129">Severity level</span></span>

<span data-ttu-id="8bcfe-130">Aşağıdaki tabloda, [kod kalitesi](quality-rules/index.md) ve [kod stili](style-rules/index.md) kuralları da dahil olmak üzere tüm çözümleyici kuralları için yapılandırabileceğiniz farklı kural önem dereceleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8bcfe-130">The following table shows the different rule severities that you can configure for all analyzer rules, including [code quality](quality-rules/index.md) and [code style](style-rules/index.md) rules.</span></span>

| <span data-ttu-id="8bcfe-131">Önem derecesi</span><span class="sxs-lookup"><span data-stu-id="8bcfe-131">Severity</span></span> | <span data-ttu-id="8bcfe-132">Derleme zamanı davranışı</span><span class="sxs-lookup"><span data-stu-id="8bcfe-132">Build-time behavior</span></span> |
|-|-|
| `error` | <span data-ttu-id="8bcfe-133">İhlaller derleme *hataları* olarak görünür ve yapıların başarısız olmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="8bcfe-133">Violations appear as build *errors* and cause builds to fail.</span></span>|
| `warning` | <span data-ttu-id="8bcfe-134">İhlaller derleme *uyarıları* olarak görünür, ancak yapıların başarısız olmasına neden olmaz (uyarıları hata olarak değerlendirmek için bir seçeneğe sahip olmadığınız sürece).</span><span class="sxs-lookup"><span data-stu-id="8bcfe-134">Violations appear as build *warnings* but do not cause builds to fail (unless you have an option set to treat warnings as errors).</span></span> |
| `suggestion` | <span data-ttu-id="8bcfe-135">İhlaller derleme *iletileri* olarak ve VISUAL Studio IDE 'de öneri olarak görünür.</span><span class="sxs-lookup"><span data-stu-id="8bcfe-135">Violations appear as build *messages* and as suggestions in the Visual Studio IDE.</span></span> |
| `silent` | <span data-ttu-id="8bcfe-136">İhlaller kullanıcıya görünür değil.</span><span class="sxs-lookup"><span data-stu-id="8bcfe-136">Violations aren't visible to the user.</span></span> |
| `none` | <span data-ttu-id="8bcfe-137">Kural tamamen bastırılır.</span><span class="sxs-lookup"><span data-stu-id="8bcfe-137">Rule is suppressed completely.</span></span> |
| `default` | <span data-ttu-id="8bcfe-138">Kuralın varsayılan önem derecesi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8bcfe-138">The default severity of the rule is used.</span></span> |

> [!TIP]
> <span data-ttu-id="8bcfe-139">Visual Studio 'da kural oluşturma işlemlerinin nasıl yapılacağı hakkında bilgi için bkz. [önem düzeyleri](/visualstudio/ide/editorconfig-language-conventions#severity-levels).</span><span class="sxs-lookup"><span data-stu-id="8bcfe-139">For information about how rule severities surface in Visual Studio, see [Severity levels](/visualstudio/ide/editorconfig-language-conventions#severity-levels).</span></span>

#### <a name="scope"></a><span data-ttu-id="8bcfe-140">Kapsam</span><span class="sxs-lookup"><span data-stu-id="8bcfe-140">Scope</span></span>

<span data-ttu-id="8bcfe-141">Tek bir kural için kural önem derecesini ayarlamak için aşağıdaki sözdizimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="8bcfe-141">To set the rule severity for a single rule, use the following syntax.</span></span>

```ini
dotnet_diagnostic.<rule ID>.severity = <severity value>
```

<span data-ttu-id="8bcfe-142">Bir çözümleyici kuralları kategorisinin varsayılan kural önem derecesini ayarlamak için aşağıdaki sözdizimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="8bcfe-142">To set the default rule severity for a category of analyzer rules, use the following syntax.</span></span>

```ini
dotnet_analyzer_diagnostic.category-<rule category>.severity = <severity value>
```

<span data-ttu-id="8bcfe-143">Tüm çözümleyici kuralları için varsayılan kural önem derecesini ayarlamak için aşağıdaki sözdizimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="8bcfe-143">To set the default rule severity for all analyzer rules, use the following syntax.</span></span>

```ini
dotnet_analyzer_diagnostic.severity = <severity value>
```

#### <a name="precedence"></a><span data-ttu-id="8bcfe-144">Önceliği</span><span class="sxs-lookup"><span data-stu-id="8bcfe-144">Precedence</span></span>

<span data-ttu-id="8bcfe-145">Aynı kural KIMLIĞINE uygulanabilecek birden fazla önem derecesi yapılandırma girişi varsa, öncelik aşağıdaki sırada seçilir:</span><span class="sxs-lookup"><span data-stu-id="8bcfe-145">If you have multiple severity configuration entries that can be applied to the same rule ID, precedence is chosen in the following order:</span></span>

- <span data-ttu-id="8bcfe-146">KIMLIĞE göre tek bir kural için bir giriş, bir kategorinin girdisinden önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="8bcfe-146">An entry for an individual rule by ID takes precedence over an entry for a category.</span></span>
- <span data-ttu-id="8bcfe-147">Kategori için bir giriş, tüm çözümleyici kuralları için bir girdiden önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="8bcfe-147">An entry for a category takes precedence over an entry for all analyzer rules.</span></span>

<span data-ttu-id="8bcfe-148">Aşağıdaki örneği göz önünde bulundurun; burada [CA1822](/visualstudio/code-quality/ca1822) "Performance" kategorisine sahiptir:</span><span class="sxs-lookup"><span data-stu-id="8bcfe-148">Consider the following example, where [CA1822](/visualstudio/code-quality/ca1822) has the category "Performance":</span></span>

```ini
[*.cs]
dotnet_diagnostic.CA1822.severity = error
dotnet_analyzer_diagnostic.category-performance.severity = warning
dotnet_analyzer_diagnostic.severity = suggestion
```

<span data-ttu-id="8bcfe-149">Yukarıdaki örnekte, üç önem derecesine sahip olan tüm girişler CA1822 için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="8bcfe-149">In the preceding example, all three severity entries are applicable to CA1822.</span></span> <span data-ttu-id="8bcfe-150">Bununla birlikte, belirtilen öncelik kurallarını kullanarak, sonraki girişler üzerinde ilk kural KIMLIĞI tabanlı giriş kazanır.</span><span class="sxs-lookup"><span data-stu-id="8bcfe-150">However, using the specified precedence rules, the first rule ID-based entry wins over the next entries.</span></span> <span data-ttu-id="8bcfe-151">Bu örnekte, CA1822 etkili bir önem derecesine sahip olur `error` .</span><span class="sxs-lookup"><span data-stu-id="8bcfe-151">In this example, CA1822 will have an effective severity of `error`.</span></span> <span data-ttu-id="8bcfe-152">"Performans" kategorisindeki tüm diğer kuralların önem derecesi olacaktır `warning` .</span><span class="sxs-lookup"><span data-stu-id="8bcfe-152">All other rules within the "Performance" category will have a severity of `warning`.</span></span>

<span data-ttu-id="8bcfe-153">Dosya içi önceliğe nasıl karar verdiği hakkında daha fazla bilgi için [yapılandırma dosyaları makalesinin öncelik bölümüne](configuration-files.md#precedence)bakın.</span><span class="sxs-lookup"><span data-stu-id="8bcfe-153">For information about how inter-file precedence is decided, see the [Precedence section of the Configuration files article](configuration-files.md#precedence).</span></span>
