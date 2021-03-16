---
description: Hatalar ve uyarılar için C# derleyici seçenekleri. Bu seçenekler, uyarıları hata olarak denetler veya etkinleştirir.
title: C# derleyici seçenekleri-hatalar ve uyarılar
ms.date: 03/12/2021
f1_keywords:
- cs.build.options
helpviewer_keywords:
- WarningLevel compiler option [C#]
- TreatWarningsAsErrors compiler option [C#]
- WarningsAsErrors compiler option [C#]
- WarningsNotAsErrors compiler option [C#]
- DisabledWarnings compiler option [C#]
- CodeAnalysisRuleSet compiler option [C#]
- ErrorLog compiler option [C#]
- ReportAnalyzer compiler option [C#]
ms.openlocfilehash: 2bdda13d6b8b2b75d80c228da678a5b7fbcb8892
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2021
ms.locfileid: "103482941"
---
# <a name="c-compiler-options-to-report-errors-and-warnings"></a><span data-ttu-id="2a6cc-104">Hataları ve uyarıları raporlamak için C# derleyici seçenekleri</span><span class="sxs-lookup"><span data-stu-id="2a6cc-104">C# Compiler Options to report errors and warnings</span></span>

<span data-ttu-id="2a6cc-105">Aşağıdaki seçenekler derleyicinin hataları ve uyarıları nasıl raporluyor olduğunu denetler.</span><span class="sxs-lookup"><span data-stu-id="2a6cc-105">The following options control how the compiler reports errors and warnings.</span></span> <span data-ttu-id="2a6cc-106">Yeni MSBuild sözdizimi **kalın** olarak gösterilir.</span><span class="sxs-lookup"><span data-stu-id="2a6cc-106">The new MSBuild syntax is shown in **Bold**.</span></span> <span data-ttu-id="2a6cc-107">Eski *csc.exe* sözdizimi içinde gösterilir `code style` .</span><span class="sxs-lookup"><span data-stu-id="2a6cc-107">The older *csc.exe* syntax is shown in `code style`.</span></span>

- <span data-ttu-id="2a6cc-108">**WarningLevel**  /  `-warn` : uyarı düzeyini ayarla.</span><span class="sxs-lookup"><span data-stu-id="2a6cc-108">**WarningLevel** / `-warn`: Set warning level.</span></span>
- <span data-ttu-id="2a6cc-109">**TreatWarningsAsErrors**  /  `-warnaserror` : tüm uyarıları hata olarak değerlendir</span><span class="sxs-lookup"><span data-stu-id="2a6cc-109">**TreatWarningsAsErrors** / `-warnaserror`: Treat all warnings as errors</span></span>
- <span data-ttu-id="2a6cc-110">**WarningsAsErrors**  /  `-warnaserror` : bir veya daha fazla uyarıyı hata olarak değerlendir</span><span class="sxs-lookup"><span data-stu-id="2a6cc-110">**WarningsAsErrors** / `-warnaserror`: Treat one or more warnings as errors</span></span>
- <span data-ttu-id="2a6cc-111">**Warninggözetimi taserrors**  /  `-warnaserror` : bir veya daha fazla uyarıyı hata olarak değerlendir</span><span class="sxs-lookup"><span data-stu-id="2a6cc-111">**WarningsNotAsErrors** / `-warnaserror`: Treat one or more warnings not as errors</span></span>
- <span data-ttu-id="2a6cc-112">**Disableduyarılar**  /  `-nowarn` : devre dışı bırakılan uyarıların bir listesini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="2a6cc-112">**DisabledWarnings** / `-nowarn`: Set a list of disabled warnings.</span></span>
- <span data-ttu-id="2a6cc-113">**CodeAnalysisRuleSet**  /  `-ruleset` : belirli tanılamayı devre dışı bırakan bir RuleSet dosyası belirtin.</span><span class="sxs-lookup"><span data-stu-id="2a6cc-113">**CodeAnalysisRuleSet** / `-ruleset`: Specify a ruleset file that disables specific diagnostics.</span></span>
- <span data-ttu-id="2a6cc-114">**Hata günlüğü**  /  `-errorlog` : tüm derleyici ve çözümleyici tanılamayı günlüğe kaydetmek için bir dosya belirtin.</span><span class="sxs-lookup"><span data-stu-id="2a6cc-114">**ErrorLog** / `-errorlog`: Specify a file to log all compiler and analyzer diagnostics.</span></span>
- <span data-ttu-id="2a6cc-115">**ReportAnalyzer**  /  `-reportanalyzer` : yürütme süresi gibi ek çözümleyici bilgilerini bildirin.</span><span class="sxs-lookup"><span data-stu-id="2a6cc-115">**ReportAnalyzer** / `-reportanalyzer`:  Report additional analyzer information, such as execution time.</span></span>

## <a name="warninglevel"></a><span data-ttu-id="2a6cc-116">Uyarı düzeyi</span><span class="sxs-lookup"><span data-stu-id="2a6cc-116">WarningLevel</span></span>

<span data-ttu-id="2a6cc-117">**WarningLevel** seçeneği, derleyicinin görüntüleyeceği uyarı düzeyini belirtir.</span><span class="sxs-lookup"><span data-stu-id="2a6cc-117">The **WarningLevel** option specifies the warning level for the compiler to display.</span></span>

```xml
<WarningLevel>3</WarningLevel>
```

<span data-ttu-id="2a6cc-118">Öğe değeri, derleme için görüntülenmesini istediğiniz uyarı düzeyidir: daha düşük sayılar yalnızca yüksek önem derecesine sahip uyarıları gösterir.</span><span class="sxs-lookup"><span data-stu-id="2a6cc-118">The element value is the warning level you want displayed for the compilation: Lower numbers show only high severity warnings.</span></span> <span data-ttu-id="2a6cc-119">Daha yüksek numaralar daha fazla uyarı gösterir.</span><span class="sxs-lookup"><span data-stu-id="2a6cc-119">Higher numbers show more warnings.</span></span> <span data-ttu-id="2a6cc-120">Değer sıfır veya pozitif bir tamsayı olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="2a6cc-120">The value must be zero or a positive integer:</span></span>

|<span data-ttu-id="2a6cc-121">Uyarı düzeyi</span><span class="sxs-lookup"><span data-stu-id="2a6cc-121">Warning level</span></span>|<span data-ttu-id="2a6cc-122">Anlamı</span><span class="sxs-lookup"><span data-stu-id="2a6cc-122">Meaning</span></span>|
|-------------------|-------------|
|<span data-ttu-id="2a6cc-123">0</span><span class="sxs-lookup"><span data-stu-id="2a6cc-123">0</span></span>|<span data-ttu-id="2a6cc-124">Tüm uyarı iletilerinin emisyonunu kapatır.</span><span class="sxs-lookup"><span data-stu-id="2a6cc-124">Turns off emission of all warning messages.</span></span>|
|<span data-ttu-id="2a6cc-125">1</span><span class="sxs-lookup"><span data-stu-id="2a6cc-125">1</span></span>|<span data-ttu-id="2a6cc-126">Ciddi uyarı iletileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="2a6cc-126">Displays severe warning messages.</span></span>|  
|<span data-ttu-id="2a6cc-127">2</span><span class="sxs-lookup"><span data-stu-id="2a6cc-127">2</span></span>|<span data-ttu-id="2a6cc-128">Düzey 1 uyarılarını ve sınıf üyelerini gizleme hakkında uyarılar gibi bazı, daha az önemli uyarıları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="2a6cc-128">Displays level 1 warnings plus certain, less-severe warnings, such as warnings about hiding class members.</span></span>|
|<span data-ttu-id="2a6cc-129">3</span><span class="sxs-lookup"><span data-stu-id="2a6cc-129">3</span></span>|<span data-ttu-id="2a6cc-130">Düzey 2 uyarılarını ve her zaman veya olarak değerlendirme yapan ifadeler hakkında uyarılar gibi bazı, daha az önemli uyarıları görüntüler `true` `false` .</span><span class="sxs-lookup"><span data-stu-id="2a6cc-130">Displays level 2 warnings plus certain, less-severe warnings, such as warnings about expressions that always evaluate to `true` or `false`.</span></span>|
|<span data-ttu-id="2a6cc-131">4 (varsayılan)</span><span class="sxs-lookup"><span data-stu-id="2a6cc-131">4 (the default)</span></span>|<span data-ttu-id="2a6cc-132">Tüm düzey 3 uyarılarını ve bilgilendirici uyarıları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="2a6cc-132">Displays all level 3 warnings plus informational warnings.</span></span>|
|<span data-ttu-id="2a6cc-133">5</span><span class="sxs-lookup"><span data-stu-id="2a6cc-133">5</span></span>|<span data-ttu-id="2a6cc-134">4. düzey uyarıları ve C# 9,0 ile gönderilen derleyicinin [ek uyarılarını](https://github.com/dotnet/roslyn/blob/a6013f3213c902c0973b2d371c3007217d610533/docs/compilers/CSharp/Warnversion%20Warning%20Waves.md) görüntüler.</span><span class="sxs-lookup"><span data-stu-id="2a6cc-134">Displays level 4 warnings plus [additional warnings](https://github.com/dotnet/roslyn/blob/a6013f3213c902c0973b2d371c3007217d610533/docs/compilers/CSharp/Warnversion%20Warning%20Waves.md) from the compiler shipped with C# 9.0.</span></span>|
|<span data-ttu-id="2a6cc-135">5 ' ten büyük</span><span class="sxs-lookup"><span data-stu-id="2a6cc-135">Greater than 5</span></span>|<span data-ttu-id="2a6cc-136">5 ' ten büyük bir değer 5 olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="2a6cc-136">Any value greater than 5 will be treated as 5.</span></span> <span data-ttu-id="2a6cc-137">Derleyici yeni uyarı düzeyleriyle güncelleştirilirse her zaman tüm uyarılara sahip olduğunuzdan emin olmak için rastgele bir büyük değer (örneğin, `9999` ) koyun.</span><span class="sxs-lookup"><span data-stu-id="2a6cc-137">To make sure you always have all warnings if the compiler is updated with new warning levels, put an arbitrary large value (for example, `9999`).</span></span>

<span data-ttu-id="2a6cc-138">Bir hata veya uyarı hakkında bilgi almak için yardım dizinindeki hata kodunu arayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2a6cc-138">To get information about an error or warning, you can look up the error code in the Help Index.</span></span> <span data-ttu-id="2a6cc-139">Bir hata veya uyarı hakkında bilgi almanın diğer yolları için bkz. [C# derleyici hataları](../compiler-messages/index.md).</span><span class="sxs-lookup"><span data-stu-id="2a6cc-139">For other ways to get information about an error or warning, see [C# Compiler Errors](../compiler-messages/index.md).</span></span> <span data-ttu-id="2a6cc-140">Tüm uyarıları hata olarak değerlendirmek için [**TreatWarningsAsErrors**](#treatwarningsaserrors) kullanın.</span><span class="sxs-lookup"><span data-stu-id="2a6cc-140">Use [**TreatWarningsAsErrors**](#treatwarningsaserrors) to treat all warnings as errors.</span></span> <span data-ttu-id="2a6cc-141">Bazı uyarıları devre dışı bırakmak için [**disableduyarılar**](#disabledwarnings) kullanın.</span><span class="sxs-lookup"><span data-stu-id="2a6cc-141">Use [**DisabledWarnings**](#disabledwarnings) to disable certain warnings.</span></span>  

## <a name="treatwarningsaserrors"></a><span data-ttu-id="2a6cc-142">TreatWarningsAsErrors</span><span class="sxs-lookup"><span data-stu-id="2a6cc-142">TreatWarningsAsErrors</span></span>

<span data-ttu-id="2a6cc-143">**TreatWarningsAsErrors** seçeneği tüm uyarıları hata olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="2a6cc-143">The **TreatWarningsAsErrors** option treats all warnings as errors.</span></span> <span data-ttu-id="2a6cc-144">Yalnızca bazı uyarıları hata olarak ayarlamak için **TreatWarningsAsErrors** ' i de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2a6cc-144">You can also use the **TreatWarningsAsErrors** to set only some warnings as errors.</span></span> <span data-ttu-id="2a6cc-145">**TreatWarningsAsErrors**' ı açarsanız, hata olarak değerlendirilmemesi gereken uyarıları listelemek Için **TreatWarningsAsErrors** ' yi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2a6cc-145">If you turn on **TreatWarningsAsErrors**, you can use **TreatWarningsAsErrors** to list warnings that shouldn't be treated as errors.</span></span>

```xml
<TreatWarningsAsErrors></TreatWarningsAsErrors>
```

<span data-ttu-id="2a6cc-146">Tüm uyarı iletileri hata olarak bildirilir.</span><span class="sxs-lookup"><span data-stu-id="2a6cc-146">All warning messages are instead reported as errors.</span></span> <span data-ttu-id="2a6cc-147">Derleme işlemi durduruluyor (çıktı dosyası oluşturulmadı).</span><span class="sxs-lookup"><span data-stu-id="2a6cc-147">The build process halts (no output files are built).</span></span> <span data-ttu-id="2a6cc-148">Varsayılan olarak, **TreatWarningsAsErrors** etkin değildir, bu da uyarıların bir çıkış dosyası oluşturulmasını engellemez anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="2a6cc-148">By default, **TreatWarningsAsErrors** isn't in effect, which means warnings don't prevent the generation of an output file.</span></span> <span data-ttu-id="2a6cc-149">İsteğe bağlı olarak, yalnızca birkaç özel uyarının hata olarak değerlendirilmesini istiyorsanız, hata olarak değerlendirilecek uyarı numaralarının virgülle ayrılmış bir listesini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2a6cc-149">Optionally, if you want only a few specific warnings to be treated as errors, you may specify a comma-separated list of warning numbers to treat as errors.</span></span> <span data-ttu-id="2a6cc-150">Tüm null olabilme uyarıları kümesi [**Nullable toplu değer**](language.md#nullable) ile belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="2a6cc-150">The set of all nullability warnings can be specified with the [**Nullable**](language.md#nullable) shorthand.</span></span> <span data-ttu-id="2a6cc-151">Derleyicinin görüntülemesini istediğiniz uyarı düzeyini belirtmek için [**WarningLevel**](#warninglevel) kullanın.</span><span class="sxs-lookup"><span data-stu-id="2a6cc-151">Use [**WarningLevel**](#warninglevel) to specify the level of warnings that you want the compiler to display.</span></span> <span data-ttu-id="2a6cc-152">Bazı uyarıları devre dışı bırakmak için [**disableduyarılar**](#disabledwarnings) kullanın.</span><span class="sxs-lookup"><span data-stu-id="2a6cc-152">Use [**DisabledWarnings**](#disabledwarnings) to disable certain warnings.</span></span>

## <a name="warningsaserrors-and-warningsnotaserrors"></a><span data-ttu-id="2a6cc-153">WarningsAsErrors ve Warninggözetimi Taserrors</span><span class="sxs-lookup"><span data-stu-id="2a6cc-153">WarningsAsErrors and WarningsNotAsErrors</span></span>

<span data-ttu-id="2a6cc-154">**WarningsAsErrors** ve **Warninggözetimi taserrors** seçenekleri bir uyarı listesi Için **TreatWarningsAsErrors** seçeneğini geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="2a6cc-154">The **WarningsAsErrors** and **WarningsNotAsErrors** options override the **TreatWarningsAsErrors** option for a list of warnings.</span></span>

<span data-ttu-id="2a6cc-155">Uyarıları hata olarak 0219 ve 0168 ' i etkinleştir:</span><span class="sxs-lookup"><span data-stu-id="2a6cc-155">Enable warnings 0219 and 0168 as errors:</span></span>

```xml
<WarningsAsErrors>0219,0168</WarningsAsErrors>
```

<span data-ttu-id="2a6cc-156">Aynı uyarıları hatalarla devre dışı bırak:</span><span class="sxs-lookup"><span data-stu-id="2a6cc-156">Disable the same warnings as errors:</span></span>

```xml
<WarningsNotAsErrors>0219,0168</WarningsNotAsErrors>
```

<span data-ttu-id="2a6cc-157">Uyarı kümesini hata olarak yapılandırmak için **WarningsAsErrors** ' i kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="2a6cc-157">You use **WarningsAsErrors** to configure a set of warnings as errors.</span></span> <span data-ttu-id="2a6cc-158">Tüm uyarıları hata olarak ayarladığınızda hata olmaması gereken bir uyarı kümesini yapılandırmak için **Warninggözetimi Taserrors** ' i kullanın.</span><span class="sxs-lookup"><span data-stu-id="2a6cc-158">Use **WarningsNotAsErrors** to configure a set of warnings that should not be errors when you've set all warnings as errors.</span></span>

## <a name="disabledwarnings"></a><span data-ttu-id="2a6cc-159">Disableduyarılar</span><span class="sxs-lookup"><span data-stu-id="2a6cc-159">DisabledWarnings</span></span>

<span data-ttu-id="2a6cc-160">**Disableduyarılar** seçeneği, derleyicinin bir veya daha fazla uyarı görüntülemesini engellemenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="2a6cc-160">The **DisabledWarnings** option lets you suppress the compiler from displaying one or more warnings.</span></span> <span data-ttu-id="2a6cc-161">Birden çok uyarı numarasını virgülle ayırın.</span><span class="sxs-lookup"><span data-stu-id="2a6cc-161">Separate multiple warning numbers with a comma.</span></span>

```xml
<DisabledWarnings>number1, number2</DisabledWarnings>
```

<span data-ttu-id="2a6cc-162">`number1`, `number2` Derleyicinin görüntülenmesini istediğiniz uyarı numaraları.</span><span class="sxs-lookup"><span data-stu-id="2a6cc-162">`number1`, `number2` Warning number(s) that you want the compiler to suppress.</span></span> <span data-ttu-id="2a6cc-163">Uyarı tanımlayıcısının sayısal parçasını belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2a6cc-163">You specify the numeric part of the warning identifier.</span></span> <span data-ttu-id="2a6cc-164">Örneğin, *CS0028* bastırmak istiyorsanız, belirtebilirsiniz `<DisabledWarnings>28</DisabledWarnings>` .</span><span class="sxs-lookup"><span data-stu-id="2a6cc-164">For example, if you want to suppress *CS0028*, you could specify `<DisabledWarnings>28</DisabledWarnings>`.</span></span> <span data-ttu-id="2a6cc-165">Derleyici, önceki sürümlerde geçerli olan ancak kaldırılmış olan **Disableduyarılar** 'a geçirilen uyarı numaralarını sessizce yoksayar.</span><span class="sxs-lookup"><span data-stu-id="2a6cc-165">The compiler silently ignores warning numbers passed to **DisabledWarnings** that were valid in previous releases, but that have been removed.</span></span> <span data-ttu-id="2a6cc-166">Örneğin, *CS0679* Visual Studio .NET 2002 derleyicisinde geçerliyse, ancak daha sonra kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="2a6cc-166">For example, *CS0679* was valid in the compiler in Visual Studio .NET 2002 but was removed later.</span></span>

 <span data-ttu-id="2a6cc-167">Aşağıdaki uyarılar **disableduyarılar** seçeneği tarafından bastırılamaz:</span><span class="sxs-lookup"><span data-stu-id="2a6cc-167">The following warnings cannot be suppressed by the **DisabledWarnings** option:</span></span>

- <span data-ttu-id="2a6cc-168">Derleyici Uyarısı (düzey 1) CS2002</span><span class="sxs-lookup"><span data-stu-id="2a6cc-168">Compiler Warning (level 1) CS2002</span></span>  
- <span data-ttu-id="2a6cc-169">Derleyici Uyarısı (düzey 1) CS2023</span><span class="sxs-lookup"><span data-stu-id="2a6cc-169">Compiler Warning (level 1) CS2023</span></span>
- <span data-ttu-id="2a6cc-170">Derleyici Uyarısı (düzey 1) CS2029</span><span class="sxs-lookup"><span data-stu-id="2a6cc-170">Compiler Warning (level 1) CS2029</span></span>

## <a name="codeanalysisruleset"></a><span data-ttu-id="2a6cc-171">CodeAnalysisRuleSet</span><span class="sxs-lookup"><span data-stu-id="2a6cc-171">CodeAnalysisRuleSet</span></span>

<span data-ttu-id="2a6cc-172">Belirli tanılamayı yapılandıran bir RuleSet dosyası belirtin.</span><span class="sxs-lookup"><span data-stu-id="2a6cc-172">Specify a ruleset file that configures specific diagnostics.</span></span>

```xml
<CodeAnalysisRuleSet>MyConfiguration.ruleset</CodeAnalysisRuleSet>
```

<span data-ttu-id="2a6cc-173">`MyConfiguration.ruleset`Kural kümesi dosyasının yoludur.</span><span class="sxs-lookup"><span data-stu-id="2a6cc-173">Where `MyConfiguration.ruleset` is the path to the ruleset file.</span></span> <span data-ttu-id="2a6cc-174">Kural kümelerini kullanma hakkında daha fazla bilgi için bkz. [Visual Studio belgelerindeki kural kümeleri hakkındaki](/visualstudio/code-quality/using-rule-sets-to-group-code-analysis-rules)makaleye bakın.</span><span class="sxs-lookup"><span data-stu-id="2a6cc-174">For more information on using rule sets, see the article in the [Visual Studio documentation on Rule sets](/visualstudio/code-quality/using-rule-sets-to-group-code-analysis-rules).</span></span>

## <a name="errorlog"></a><span data-ttu-id="2a6cc-175">ErrorLog</span><span class="sxs-lookup"><span data-stu-id="2a6cc-175">ErrorLog</span></span>

<span data-ttu-id="2a6cc-176">Tüm derleyici ve çözümleyici tanılamayı günlüğe kaydetmek için bir dosya belirtin.</span><span class="sxs-lookup"><span data-stu-id="2a6cc-176">Specify a file to log all compiler and analyzer diagnostics.</span></span>

```xml
<ErrorLog>MyConfiguration.ruleset</ErrorLog>
```

<span data-ttu-id="2a6cc-177">**Hata günlüğü** seçeneği derleyicinin [statik bir çözümleme sonuçları değişim biçimi (Sarif) günlüğüne](https://github.com/microsoft/sarif-tutorials/blob/main/docs/1-Introduction.md#:~:text=What%20is%20SARIF%3F,for%20use%20by%20simpler%20tools)çıktılarına neden olur.</span><span class="sxs-lookup"><span data-stu-id="2a6cc-177">The **ErrorLog** option causes the compiler to output a [Static Analysis Results Interchange Format (SARIF) log](https://github.com/microsoft/sarif-tutorials/blob/main/docs/1-Introduction.md#:~:text=What%20is%20SARIF%3F,for%20use%20by%20simpler%20tools).</span></span> <span data-ttu-id="2a6cc-178">SARIF günlükleri genellikle derleyicinin ve çözümleyici tanılamalarındaki sonuçları çözümleyen araçlar tarafından okunabilir.</span><span class="sxs-lookup"><span data-stu-id="2a6cc-178">SARIF logs are typically read by tools that analyze the results from compiler and analyzer diagnostics.</span></span>

## <a name="reportanalyzer"></a><span data-ttu-id="2a6cc-179">ReportAnalyzer</span><span class="sxs-lookup"><span data-stu-id="2a6cc-179">ReportAnalyzer</span></span>

<span data-ttu-id="2a6cc-180">Yürütme süresi gibi ek çözümleyici bilgilerini bildirin.</span><span class="sxs-lookup"><span data-stu-id="2a6cc-180">Report additional analyzer information, such as execution time.</span></span>

```xml
<ReportAnalyzer>true</ReportAnalyzer>
```

<span data-ttu-id="2a6cc-181">**ReportAnalyzer** seçeneği, derleyicinin, derlemede bulunan çözümleyiciler performans özelliklerini ayrıntılarıyla bağlayan ek MSBuild günlük bilgilerini yaymasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="2a6cc-181">The **ReportAnalyzer** option causes the compiler to emit extra MSBuild log information that details the performance characteristics of analyzers in the build.</span></span> <span data-ttu-id="2a6cc-182">Bu genellikle çözümleyici yazarları tarafından, çözümleyici 'yi doğrulamaya bir parçası olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2a6cc-182">It's typically used by analyzer authors as part of validating the analyzer.</span></span>
