---
title: Kod analizi kuralları için yapılandırma dosyaları
description: Kod analizi kurallarını yapılandırmak için farklı yapılandırma dosyaları hakkında bilgi edinin.
ms.date: 09/24/2020
ms.topic: conceptual
no-loc:
- EditorConfig
ms.openlocfilehash: b98fdd48f2373bd23fcd3273834860a60c682969
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2021
ms.locfileid: "99216388"
---
# <a name="configuration-files-for-code-analysis-rules"></a><span data-ttu-id="57f27-103">Kod analizi kuralları için yapılandırma dosyaları</span><span class="sxs-lookup"><span data-stu-id="57f27-103">Configuration files for code analysis rules</span></span>

<span data-ttu-id="57f27-104">Kod analizi kuralları çeşitli [yapılandırma seçeneklerine](configuration-options.md)sahiptir.</span><span class="sxs-lookup"><span data-stu-id="57f27-104">Code analysis rules have various [configuration options](configuration-options.md).</span></span> <span data-ttu-id="57f27-105">Bu seçenekleri aşağıdaki çözümleyici yapılandırma dosyalarından birinde anahtar-değer çiftleri olarak belirtirsiniz:</span><span class="sxs-lookup"><span data-stu-id="57f27-105">You specify these options as key-value pairs in one of the following analyzer configuration files:</span></span>

- <span data-ttu-id="57f27-106">[EditorConfig](#editorconfig) Dosya: dosya tabanlı veya klasör tabanlı yapılandırma seçenekleri.</span><span class="sxs-lookup"><span data-stu-id="57f27-106">[EditorConfig](#editorconfig) file: File-based or folder-based configuration options.</span></span>
- <span data-ttu-id="57f27-107">[Global analiz Zerconfig](#global-analyzerconfig) dosyası: proje düzeyi yapılandırma seçenekleri.</span><span class="sxs-lookup"><span data-stu-id="57f27-107">[Global AnalyzerConfig](#global-analyzerconfig) file: Project-level configuration options.</span></span> <span data-ttu-id="57f27-108">Bazı proje dosyaları proje klasörü dışında olduğunda faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="57f27-108">Useful when some project files reside outside the project folder.</span></span>

## EditorConfig

<span data-ttu-id="57f27-109">[EditorConfig](/visualstudio/ide/create-portable-custom-editor-options) dosyalar, **belirli kaynak dosyalara veya klasörlere uygulanan seçenekleri** sağlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="57f27-109">[EditorConfig](/visualstudio/ide/create-portable-custom-editor-options) files are used to provide **options that apply to specific source files or folders**.</span></span> <span data-ttu-id="57f27-110">Seçenekler, uygulanabilir dosya ve klasörleri tanımlamak için bölüm üstbilgileri altına yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="57f27-110">Options are placed under section headers to identify the applicable files and folders.</span></span> <span data-ttu-id="57f27-111">Yapılandırmak istediğiniz her kural için bir giriş ekleyin ve bunu karşılık gelen dosya uzantısı bölümüne yerleştirin, örneğin, `[*.cs]` .</span><span class="sxs-lookup"><span data-stu-id="57f27-111">Add an entry for each rule you want to configure, and place it under the corresponding file extension section, for example, `[*.cs]`.</span></span>

```ini
[*.cs]
<option_name> = <option_value>
```

<span data-ttu-id="57f27-112">Yukarıdaki örnekte, `[*.cs]` `.cs` alt klasörler dahil olmak üzere geçerli klasörde dosya uzantısına sahip tüm C# dosyalarını seçmek için bir editorconfig bölüm üst bilgisi vardır.</span><span class="sxs-lookup"><span data-stu-id="57f27-112">In the above example, `[*.cs]` is an editorconfig section header to select all C# files with `.cs` file extension within the current folder, including subfolders.</span></span> <span data-ttu-id="57f27-113">Sonraki giriş, `<option_name> = <option_value>` tüm C# dosyalarına uygulanacak bir çözümleyici seçeneğidir.</span><span class="sxs-lookup"><span data-stu-id="57f27-113">The subsequent entry, `<option_name> = <option_value>`, is an analyzer option that will be applied to all the C# files.</span></span>

<span data-ttu-id="57f27-114">Dosyayı EditorConfig ilgili dizine yerleştirerek bir klasöre, projeye veya tüm depoya dosya kuralları uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="57f27-114">You can apply EditorConfig file conventions to a folder, a project, or an entire repo by placing the file in the corresponding directory.</span></span> <span data-ttu-id="57f27-115">Bu seçenekler, derleme zamanında analiz yürütülürken ve Visual Studio 'da kodu düzenlerken uygulanır.</span><span class="sxs-lookup"><span data-stu-id="57f27-115">These options are applied when executing the analysis at build time and while you edit code in Visual Studio.</span></span>

<span data-ttu-id="57f27-116">Eğer girinti boyutu gibi düzenleyici ayarları için mevcut bir *. editorconfig* dosyanız varsa veya sondaki boşluğu kırpıp kırpmak için, kod analizi yapılandırma seçeneklerinizi aynı dosyaya yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="57f27-116">If you have an existing *.editorconfig* file for editor settings such as indent size or whether to trim trailing whitespace, you can place your code analysis configuration options in the same file.</span></span>

> [!TIP]
> <span data-ttu-id="57f27-117">Visual Studio, bu dosyalardan birini projenize eklemenin kolay hale getiren bir *. editorconfig* öğesi şablonu sağlar.</span><span class="sxs-lookup"><span data-stu-id="57f27-117">Visual Studio provides an *.editorconfig* item template that makes is easy to add one of these files to your project.</span></span> <span data-ttu-id="57f27-118">Daha fazla bilgi için bkz. [ EditorConfig bir projeye dosya ekleme](/visualstudio/ide/create-portable-custom-editor-options#add-an-editorconfig-file-to-a-project).</span><span class="sxs-lookup"><span data-stu-id="57f27-118">For more information, see [Add an EditorConfig file to a project](/visualstudio/ide/create-portable-custom-editor-options#add-an-editorconfig-file-to-a-project).</span></span>

### <a name="example"></a><span data-ttu-id="57f27-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="57f27-119">Example</span></span>

<span data-ttu-id="57f27-120">Aşağıda, EditorConfig seçenekleri ve kural önem derecesini yapılandırmak için örnek bir dosya verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="57f27-120">Following is an example EditorConfig file to configure options and rule severity:</span></span>

```ini
# Remove the line below if you want to inherit .editorconfig settings from higher directories
root = true

# C# files
[*.cs]

#### Core EditorConfig Options ####

# Indentation and spacing
indent_size = 4
indent_style = space
tab_width = 4

#### .NET Coding Conventions ####

# this. and Me. preferences
dotnet_style_qualification_for_method = true

#### Diagnostic configuration ####

# CA1000: Do not declare static members on generic types
dotnet_diagnostic.CA1000.severity = warning
```

## <a name="global-analyzerconfig"></a><span data-ttu-id="57f27-121">Küresel analiz Zerconfig</span><span class="sxs-lookup"><span data-stu-id="57f27-121">Global AnalyzerConfig</span></span>

<span data-ttu-id="57f27-122">.NET 5 SDK ile başlayarak (Visual Studio 2019 sürüm 16,8 ve üzeri sürümlerde desteklenir), çözümleyici seçeneklerini genel _analiz Zericonfig_ dosyaları ile de yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="57f27-122">Starting with the .NET 5 SDK (which is supported in Visual Studio 2019 version 16.8 and later), you can also configure analyzer options with global _AnalyzerConfig_ files.</span></span> <span data-ttu-id="57f27-123">Bu dosyalar, dosya adlarından veya dosya yollarından bağımsız olarak **bir projedeki tüm kaynak dosyalara uygulanan seçenekleri** sağlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="57f27-123">These files are used to provide **options that apply to all the source files in a project**, regardless of their file names or file paths.</span></span>

<span data-ttu-id="57f27-124">[EditorConfig](#editorconfig)Dosyaların aksine, genel yapılandırma dosyaları, girinti boyutu ya da sondaki boşluğu kırpıp kırpılıp Kırpılanmayacağı gibi, IDEs için düzenleyici stil ayarlarını yapılandırmak için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="57f27-124">Unlike [EditorConfig](#editorconfig) files, global config files can't be used to configure editor style settings for IDEs, such as indent size or whether to trim trailing whitespace.</span></span> <span data-ttu-id="57f27-125">Bunun yerine, yalnızca proje düzeyi çözümleyici yapılandırma seçeneklerini belirtmek için tasarlanırlar.</span><span class="sxs-lookup"><span data-stu-id="57f27-125">Instead, they are designed purely for specifying project-level analyzer configuration options.</span></span>

### <a name="format"></a><span data-ttu-id="57f27-126">Biçimlendir</span><span class="sxs-lookup"><span data-stu-id="57f27-126">Format</span></span>

<span data-ttu-id="57f27-127">EditorConfigİlgili dosya ve klasörleri tanımlamak için gibi bölüm üst bilgileri olması gereken dosyaların aksine, `[*.cs]` genel analiz zerconfig dosyaları bölüm üst bilgilerine sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="57f27-127">Unlike EditorConfig files, which must have section headers, such as `[*.cs]`, to identify the applicable files and folders, global AnalyzerConfig files don't have section headers.</span></span> <span data-ttu-id="57f27-128">Bunun yerine, `is_global = true` normal dosyalardan ayırt edilebilmesi için formun en üst düzey bir girişi gerekir EditorConfig .</span><span class="sxs-lookup"><span data-stu-id="57f27-128">Instead, they require a top level entry of the form `is_global = true` to differentiate them from regular EditorConfig files.</span></span> <span data-ttu-id="57f27-129">Bu, dosyadaki tüm seçeneklerin Projenin tamamına uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="57f27-129">This indicates that all the options in the file apply to the entire project.</span></span> <span data-ttu-id="57f27-130">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="57f27-130">For example:</span></span>

```ini
is_global = true
<option_name> = <option_value>
```

### <a name="naming"></a><span data-ttu-id="57f27-131">Adlandırma</span><span class="sxs-lookup"><span data-stu-id="57f27-131">Naming</span></span>

<span data-ttu-id="57f27-132">EditorConfigAdlandırılmış olması gereken dosyaların aksine `.editorconfig` , genel yapılandırma dosyalarının belirli bir ad veya uzantıya sahip olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="57f27-132">Unlike EditorConfig files, which must be named `.editorconfig`, global config files do not need to have a specific name or extension.</span></span> <span data-ttu-id="57f27-133">Ancak, bu dosyaları olarak ayarlarsanız, `.globalconfig` alt klasörler dahil olmak üzere geçerli klasör içindeki tüm C# ve Visual Basic projelerine örtülü olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="57f27-133">However, if you name these files as `.globalconfig` then they will be implicitly applied to all the C# and Visual Basic projects within the current folder, including subfolders.</span></span> <span data-ttu-id="57f27-134">Aksi takdirde, `GlobalAnalyzerConfigFiles` öğeyi MSBuild proje dosyanıza açıkça eklemeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="57f27-134">Otherwise, you must explicitly add the `GlobalAnalyzerConfigFiles` item to your MSBuild project file:</span></span>

```xml
<ItemGroup>
  <GlobalAnalyzerConfigFiles Include="<path_to_global_analyzer_config>" />
</ItemGroup>
```

> [!NOTE]
> <span data-ttu-id="57f27-135">`is_global = true`Dosya adlandırılsa bile en üst düzey giriş gereklidir `.globalconfig` .</span><span class="sxs-lookup"><span data-stu-id="57f27-135">The top-level entry `is_global = true` is required even when the file is named `.globalconfig`.</span></span>

### <a name="example"></a><span data-ttu-id="57f27-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="57f27-136">Example</span></span>

<span data-ttu-id="57f27-137">Aşağıda, proje düzeyinde seçenekleri ve kural önem derecesini yapılandırmak için örnek bir genel analiz Zerconfig dosyası verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="57f27-137">Following is an example global AnalyzerConfig file to configure options and rule severity at the project level:</span></span>

```ini
# Top level entry required to mark this as a global AnalyzerConfig file
is_global = true

# NOTE: No section headers for configuration entries

#### .NET Coding Conventions ####

# this. and Me. preferences
dotnet_style_qualification_for_method = true:warning

#### Diagnostic configuration ####

# CA1000: Do not declare static members on generic types
dotnet_diagnostic.CA1000.severity = warning
```

## <a name="precedence"></a><span data-ttu-id="57f27-138">Önceliği</span><span class="sxs-lookup"><span data-stu-id="57f27-138">Precedence</span></span>

<span data-ttu-id="57f27-139">Hem EditorConfig dosyalar hem de Global analist yapılandırma dosyaları her seçenek için bir anahtar-değer çifti belirtir.</span><span class="sxs-lookup"><span data-stu-id="57f27-139">Both EditorConfig files and global AnalyzerConfig files specify a key-value pair for each option.</span></span> <span data-ttu-id="57f27-140">Aynı anahtara ancak farklı değerlere sahip birden fazla giriş olduğunda çakışmalar oluşur.</span><span class="sxs-lookup"><span data-stu-id="57f27-140">Conflicts arise when there are multiple entries with the same key but different values.</span></span>

### <a name="general-options"></a><span data-ttu-id="57f27-141">Genel seçenekler</span><span class="sxs-lookup"><span data-stu-id="57f27-141">General options</span></span>

<span data-ttu-id="57f27-142">Seçenekler arasında çakışmalar meydana geldiğinde, çakışmaları çözmek için aşağıdaki öncelik kuralları kullanılır:</span><span class="sxs-lookup"><span data-stu-id="57f27-142">When conflicts arise between options, the following precedence rules are used to resolve the conflicts:</span></span>

- <span data-ttu-id="57f27-143">Aynı yapılandırma dosyasındaki çakışan girişler: dosyanın daha sonra WINS olarak görünen giriş.</span><span class="sxs-lookup"><span data-stu-id="57f27-143">Conflicting entries in the same configuration file: The entry that appears later in the file wins.</span></span> <span data-ttu-id="57f27-144">Bu, tek bir EditorConfig dosyadaki ve aynı zamanda tek bir genel analiz Zeri yapılandırma dosyasında bulunan çakışan girişler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="57f27-144">This is true for conflicting entries within a single EditorConfig file and also within a single global AnalyzerConfig file.</span></span>

- <span data-ttu-id="57f27-145">İki dosyada çakışan girişler EditorConfig : dosya EditorConfig sisteminde daha derin olan ve dolayısıyla daha uzun bir dosya yoluna sahip olan giriş.</span><span class="sxs-lookup"><span data-stu-id="57f27-145">Conflicting entries in two EditorConfig files: The entry in the EditorConfig file that's deeper in the file system, and hence has a longer file path, wins.</span></span>

- <span data-ttu-id="57f27-146">İki genel analiz Zeri yapılandırma dosyasında çakışan girişler: bir derleyici uyarısı bildirilir ve her iki giriş de yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="57f27-146">Conflicting entries in two global AnalyzerConfig files: A compiler warning is reported and both entries are ignored.</span></span>

- <span data-ttu-id="57f27-147">Bir EditorConfig dosyadaki ve genel analiz Zeri yapılandırma dosyasında çakışan girişler: EditorConfig dosyadaki giriş kazanır.</span><span class="sxs-lookup"><span data-stu-id="57f27-147">Conflicting entries in an EditorConfig file and a Global AnalyzerConfig file: The entry in the EditorConfig file wins.</span></span>

### <a name="severity-options"></a><span data-ttu-id="57f27-148">Önem derecesi seçenekleri</span><span class="sxs-lookup"><span data-stu-id="57f27-148">Severity options</span></span>

<span data-ttu-id="57f27-149">Önceki [genel öncelik kuralları](#general-options) yapılandırma dosyalarında belirtilen tüm seçenekler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="57f27-149">The previous [general precedence rules](#general-options) apply for all options specified in configuration files.</span></span> <span data-ttu-id="57f27-150">[Önem derecesi yapılandırma](configuration-options.md#severity-level) seçenekleri için aşağıdaki ek öncelik kuralları geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="57f27-150">For [severity configuration](configuration-options.md#severity-level) options, the following additional precedence rules apply:</span></span>

- <span data-ttu-id="57f27-151">Komut satırında, derleyici seçenekleri (veya) olarak belirtilen önem derecesi seçenekleri, `/nowarn` `/warnaserror` ve genel analiz Zeri yapılandırma dosyalarında belirtilen [önem derecesi yapılandırma](configuration-options.md#severity-level) seçeneklerini her zaman geçersiz kılar EditorConfig .</span><span class="sxs-lookup"><span data-stu-id="57f27-151">Severity options specified at the command line as compiler options (`/nowarn` or `/warnaserror`) always override [severity configuration](configuration-options.md#severity-level) options specified in EditorConfig and global AnalyzerConfig files.</span></span>

- <span data-ttu-id="57f27-152">Önem derecesi seçenekleri bir [RuleSet](/visualstudio/code-quality/using-rule-sets-to-group-code-analysis-rules) dosyası ile de belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="57f27-152">Severity options can also be specified with a [Ruleset](/visualstudio/code-quality/using-rule-sets-to-group-code-analysis-rules) file.</span></span> <span data-ttu-id="57f27-153">Ancak, RuleSets dosyaları EditorConfig ve genel analiz Zeri yapılandırma dosyalarında kullanım dışı bırakılmıştır.</span><span class="sxs-lookup"><span data-stu-id="57f27-153">However, rulesets files are deprecated in favor of EditorConfig and global AnalyzerConfig files.</span></span> <span data-ttu-id="57f27-154">[RuleSet dosyalarını eşdeğer bir EditorConfig dosyaya dönüştürmeniz](/visualstudio/code-quality/use-roslyn-analyzers#convert-an-existing-ruleset-file-to-editorconfig-file)önerilir.</span><span class="sxs-lookup"><span data-stu-id="57f27-154">It's recommended that you [convert ruleset files to an equivalent EditorConfig file](/visualstudio/code-quality/use-roslyn-analyzers#convert-an-existing-ruleset-file-to-editorconfig-file).</span></span> <span data-ttu-id="57f27-155">Bir RuleSet dosyası ve EditorConfig ya da Global analist yapılandırma dosyalarından çakışan önem derecesine yönelik öncelik _tanımsızdır_.</span><span class="sxs-lookup"><span data-stu-id="57f27-155">Precedence for conflicting severity entries from a ruleset file and EditorConfig or global AnalyzerConfig files is _undefined_.</span></span>

- <span data-ttu-id="57f27-156">Farklı anahtarlarla ilgili önem derecesi seçeneklerinin öncelik kuralları hakkında bilgi için, örneğin, tek bir kural için farklı önem dereceleri belirtildiğinde ve kuralın altında bulunduğu kategori için, bkz. [Kod Analizi Için yapılandırma seçenekleri](configuration-options.md#precedence).</span><span class="sxs-lookup"><span data-stu-id="57f27-156">For information about precedence rules for related severity options with different keys, for example, when different severities are specified for a single rule and for the category that rule falls under, see [Configuration options for code analysis](configuration-options.md#precedence).</span></span>

## <a name="see-also"></a><span data-ttu-id="57f27-157">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="57f27-157">See also</span></span>

- [<span data-ttu-id="57f27-158">EditorConfig vs genel analiz Zerconfig tasarım sorunu</span><span class="sxs-lookup"><span data-stu-id="57f27-158">EditorConfig vs global AnalyzerConfig design issue</span></span>](https://github.com/dotnet/roslyn/issues/47707)
