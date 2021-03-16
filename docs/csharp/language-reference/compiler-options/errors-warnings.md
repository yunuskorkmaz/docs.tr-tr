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
# <a name="c-compiler-options-to-report-errors-and-warnings"></a>Hataları ve uyarıları raporlamak için C# derleyici seçenekleri

Aşağıdaki seçenekler derleyicinin hataları ve uyarıları nasıl raporluyor olduğunu denetler. Yeni MSBuild sözdizimi **kalın** olarak gösterilir. Eski *csc.exe* sözdizimi içinde gösterilir `code style` .

- **WarningLevel**  /  `-warn` : uyarı düzeyini ayarla.
- **TreatWarningsAsErrors**  /  `-warnaserror` : tüm uyarıları hata olarak değerlendir
- **WarningsAsErrors**  /  `-warnaserror` : bir veya daha fazla uyarıyı hata olarak değerlendir
- **Warninggözetimi taserrors**  /  `-warnaserror` : bir veya daha fazla uyarıyı hata olarak değerlendir
- **Disableduyarılar**  /  `-nowarn` : devre dışı bırakılan uyarıların bir listesini ayarlayın.
- **CodeAnalysisRuleSet**  /  `-ruleset` : belirli tanılamayı devre dışı bırakan bir RuleSet dosyası belirtin.
- **Hata günlüğü**  /  `-errorlog` : tüm derleyici ve çözümleyici tanılamayı günlüğe kaydetmek için bir dosya belirtin.
- **ReportAnalyzer**  /  `-reportanalyzer` : yürütme süresi gibi ek çözümleyici bilgilerini bildirin.

## <a name="warninglevel"></a>Uyarı düzeyi

**WarningLevel** seçeneği, derleyicinin görüntüleyeceği uyarı düzeyini belirtir.

```xml
<WarningLevel>3</WarningLevel>
```

Öğe değeri, derleme için görüntülenmesini istediğiniz uyarı düzeyidir: daha düşük sayılar yalnızca yüksek önem derecesine sahip uyarıları gösterir. Daha yüksek numaralar daha fazla uyarı gösterir. Değer sıfır veya pozitif bir tamsayı olmalıdır:

|Uyarı düzeyi|Anlamı|
|-------------------|-------------|
|0|Tüm uyarı iletilerinin emisyonunu kapatır.|
|1|Ciddi uyarı iletileri görüntüler.|  
|2|Düzey 1 uyarılarını ve sınıf üyelerini gizleme hakkında uyarılar gibi bazı, daha az önemli uyarıları görüntüler.|
|3|Düzey 2 uyarılarını ve her zaman veya olarak değerlendirme yapan ifadeler hakkında uyarılar gibi bazı, daha az önemli uyarıları görüntüler `true` `false` .|
|4 (varsayılan)|Tüm düzey 3 uyarılarını ve bilgilendirici uyarıları görüntüler.|
|5|4. düzey uyarıları ve C# 9,0 ile gönderilen derleyicinin [ek uyarılarını](https://github.com/dotnet/roslyn/blob/a6013f3213c902c0973b2d371c3007217d610533/docs/compilers/CSharp/Warnversion%20Warning%20Waves.md) görüntüler.|
|5 ' ten büyük|5 ' ten büyük bir değer 5 olarak kabul edilir. Derleyici yeni uyarı düzeyleriyle güncelleştirilirse her zaman tüm uyarılara sahip olduğunuzdan emin olmak için rastgele bir büyük değer (örneğin, `9999` ) koyun.

Bir hata veya uyarı hakkında bilgi almak için yardım dizinindeki hata kodunu arayabilirsiniz. Bir hata veya uyarı hakkında bilgi almanın diğer yolları için bkz. [C# derleyici hataları](../compiler-messages/index.md). Tüm uyarıları hata olarak değerlendirmek için [**TreatWarningsAsErrors**](#treatwarningsaserrors) kullanın. Bazı uyarıları devre dışı bırakmak için [**disableduyarılar**](#disabledwarnings) kullanın.  

## <a name="treatwarningsaserrors"></a>TreatWarningsAsErrors

**TreatWarningsAsErrors** seçeneği tüm uyarıları hata olarak değerlendirir. Yalnızca bazı uyarıları hata olarak ayarlamak için **TreatWarningsAsErrors** ' i de kullanabilirsiniz. **TreatWarningsAsErrors**' ı açarsanız, hata olarak değerlendirilmemesi gereken uyarıları listelemek Için **TreatWarningsAsErrors** ' yi kullanabilirsiniz.

```xml
<TreatWarningsAsErrors></TreatWarningsAsErrors>
```

Tüm uyarı iletileri hata olarak bildirilir. Derleme işlemi durduruluyor (çıktı dosyası oluşturulmadı). Varsayılan olarak, **TreatWarningsAsErrors** etkin değildir, bu da uyarıların bir çıkış dosyası oluşturulmasını engellemez anlamına gelir. İsteğe bağlı olarak, yalnızca birkaç özel uyarının hata olarak değerlendirilmesini istiyorsanız, hata olarak değerlendirilecek uyarı numaralarının virgülle ayrılmış bir listesini belirtebilirsiniz. Tüm null olabilme uyarıları kümesi [**Nullable toplu değer**](language.md#nullable) ile belirtilebilir. Derleyicinin görüntülemesini istediğiniz uyarı düzeyini belirtmek için [**WarningLevel**](#warninglevel) kullanın. Bazı uyarıları devre dışı bırakmak için [**disableduyarılar**](#disabledwarnings) kullanın.

## <a name="warningsaserrors-and-warningsnotaserrors"></a>WarningsAsErrors ve Warninggözetimi Taserrors

**WarningsAsErrors** ve **Warninggözetimi taserrors** seçenekleri bir uyarı listesi Için **TreatWarningsAsErrors** seçeneğini geçersiz kılar.

Uyarıları hata olarak 0219 ve 0168 ' i etkinleştir:

```xml
<WarningsAsErrors>0219,0168</WarningsAsErrors>
```

Aynı uyarıları hatalarla devre dışı bırak:

```xml
<WarningsNotAsErrors>0219,0168</WarningsNotAsErrors>
```

Uyarı kümesini hata olarak yapılandırmak için **WarningsAsErrors** ' i kullanırsınız. Tüm uyarıları hata olarak ayarladığınızda hata olmaması gereken bir uyarı kümesini yapılandırmak için **Warninggözetimi Taserrors** ' i kullanın.

## <a name="disabledwarnings"></a>Disableduyarılar

**Disableduyarılar** seçeneği, derleyicinin bir veya daha fazla uyarı görüntülemesini engellemenize olanak tanır. Birden çok uyarı numarasını virgülle ayırın.

```xml
<DisabledWarnings>number1, number2</DisabledWarnings>
```

`number1`, `number2` Derleyicinin görüntülenmesini istediğiniz uyarı numaraları. Uyarı tanımlayıcısının sayısal parçasını belirtirsiniz. Örneğin, *CS0028* bastırmak istiyorsanız, belirtebilirsiniz `<DisabledWarnings>28</DisabledWarnings>` . Derleyici, önceki sürümlerde geçerli olan ancak kaldırılmış olan **Disableduyarılar** 'a geçirilen uyarı numaralarını sessizce yoksayar. Örneğin, *CS0679* Visual Studio .NET 2002 derleyicisinde geçerliyse, ancak daha sonra kaldırıldı.

 Aşağıdaki uyarılar **disableduyarılar** seçeneği tarafından bastırılamaz:

- Derleyici Uyarısı (düzey 1) CS2002  
- Derleyici Uyarısı (düzey 1) CS2023
- Derleyici Uyarısı (düzey 1) CS2029

## <a name="codeanalysisruleset"></a>CodeAnalysisRuleSet

Belirli tanılamayı yapılandıran bir RuleSet dosyası belirtin.

```xml
<CodeAnalysisRuleSet>MyConfiguration.ruleset</CodeAnalysisRuleSet>
```

`MyConfiguration.ruleset`Kural kümesi dosyasının yoludur. Kural kümelerini kullanma hakkında daha fazla bilgi için bkz. [Visual Studio belgelerindeki kural kümeleri hakkındaki](/visualstudio/code-quality/using-rule-sets-to-group-code-analysis-rules)makaleye bakın.

## <a name="errorlog"></a>ErrorLog

Tüm derleyici ve çözümleyici tanılamayı günlüğe kaydetmek için bir dosya belirtin.

```xml
<ErrorLog>MyConfiguration.ruleset</ErrorLog>
```

**Hata günlüğü** seçeneği derleyicinin [statik bir çözümleme sonuçları değişim biçimi (Sarif) günlüğüne](https://github.com/microsoft/sarif-tutorials/blob/main/docs/1-Introduction.md#:~:text=What%20is%20SARIF%3F,for%20use%20by%20simpler%20tools)çıktılarına neden olur. SARIF günlükleri genellikle derleyicinin ve çözümleyici tanılamalarındaki sonuçları çözümleyen araçlar tarafından okunabilir.

## <a name="reportanalyzer"></a>ReportAnalyzer

Yürütme süresi gibi ek çözümleyici bilgilerini bildirin.

```xml
<ReportAnalyzer>true</ReportAnalyzer>
```

**ReportAnalyzer** seçeneği, derleyicinin, derlemede bulunan çözümleyiciler performans özelliklerini ayrıntılarıyla bağlayan ek MSBuild günlük bilgilerini yaymasına neden olur. Bu genellikle çözümleyici yazarları tarafından, çözümleyici 'yi doğrulamaya bir parçası olarak kullanılır.
